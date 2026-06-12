---
title: "ssh/sftp connection refused"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by phsopher on 2010-06-13
I'm trying to establish a connection between two laptops using sftp but am getting the following error message:

Connecting to <IP>...
ssh: connect to host <IP> port 22: Connection refused
Couldn't read packet: Connection reset by peer

ftp isn't working either. Both machines are running Ubuntu and connect to the internet through the same wifi router  in case that's relevant. What could be the problem?

I'm completely new to Linux so imagine you're talking to a moron (which isn't far from the truth).

---

### Post by quvil on 2010-06-13
Are you sure that sshd is running?
If you execute the following command on the machine to which you are trying to connect:

sudo lsof 2>&1 |grep 'sshd.*IPv4.*'

do you see a line similar to the following:

sshd      24257                root    3u     IPv4           10051407         0t0        TCP *:22 (LISTEN)

If not, then sshd is not running.

---

### Post by bigmojo74 on 2010-06-13
I just started playing with Ubuntu so can someone please confirm this, none of my Ubuntu installs had an ssh server setup by default - I had to sudo apt-get install openssh-server to enable (receiving) ssh on my machines. They could all open ssh to another system out of the box.

---

### Post by phsopher on 2010-06-13
I had no idea I had to have sshd. Like I said I'm a total noob. After installing sshd everything works fine. Thanks a lot for your help.

---

### Post by bigmojo74 on 2010-06-13
No worries, I'm also more of a Windows guy, and ran into the same thing - thought ssh was a default Linux thing. Though for security purposes I like that it's not installed by default in the Ubuntu install.

---

