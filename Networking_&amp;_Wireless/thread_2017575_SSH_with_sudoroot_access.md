---
title: "SSH with sudo/root access"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by DrMike on 2012-07-05
Hello,

I want to run a script on remote computer without having to enter a password.

I've successfully ran ssh-keygen and ssh-copy-id such that if I run the command:

ssh me@remote_host "some command"

this works fine. 

however, if I run:

sudo ssh me@remote_host "some command"

I get prompted for a password for me@remote_host. I'm assuming that this is because I generated my key under me@local_host not root@local_host.

I've (obviously) so far have be unable to figure out how to fix this. Any suggestions?

---

### Post by netopalis45 on 2012-07-05
As far as I know there is no reason to run SSH as root. If you are trying to run the command you are sending over SSH, which is what I understand you are trying to do, you need to put the "sudo" in that command.

ssh me@remote_host "sudo some command"

You can also add a line to the sudoers file so you don't have to type your password

sudo visudo
username ALL=NOPASSWD: /path/to/command

Hope this helps

---

### Post by DrMike on 2012-07-05
Well, here's the thing, I'm actually python in sudo mode so that I have write access to various files to various servers on our network.

And within the python code, I'm using the subprocess module to run command line arguments of a particularly processing-intensive process to a remote host.

I just used the above example to help simply a description of the problem.

---

