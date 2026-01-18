# Shell in a GitHub Action

This repository demonstrates **how to obtain a reverse shell from a GitHub Actions runner** by setting up a listener on an external machine and configuring the workflow to connect back to it.

### Requirements

To test this setup, you'll need **an internet-accessible machine** that can act as a listener (e.g., an EC2 instance).
If you don’t have one, you can use a free tunneling service such as: [https://pinggy.io/](https://pinggy.io/)

### Setup Steps

#### 1. Install Netcat on the Listener Machine

On Ubuntu:

```bash
sudo apt install netcat-traditional
```

#### 2. Start a Listener

On the external machine, open a port and wait for incoming connections:

```bash
nc -lvnp 9001
```

#### 3. Trigger the GitHub Action

In your GitHub repository:

* Go to **Actions**
* Select the workflow
* Click **Run workflow**

When the runner executes the reverse-shell command, you should see a connection appear in your listener terminal.

#### Upgrade to an Interactive TTY (Optional)

Once the reverse shell connects, you can upgrade it to a fully interactive Bash session with:

```bash
python3 -c 'import pty, os; pty.spawn("/bin/bash")'
```


⚠️ **Educational and debugging purposes only. Use responsibly!**
