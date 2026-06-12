---
title: "How to check whether ssh running ?"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by deb_untu on 2010-08-01
How to check whether ssh is running or not ? (I have install ssh)

If not how to make it run ?

---

### Post by heimo on 2010-08-01
> **deb_untu said:**
> How to check whether ssh is running or not ? (I have install ssh)

If not how to make it run ?

You could try to ssh into that computer from another computer, or even the same one (ssh localhost). If it's not installed, install package openssh-server.

---

### Post by sambarusty on 2010-08-01
Why did you need to install it.  Usually it is available. Open a terminal and ssh into blah, you should see a failure or something.

---

### Post by ajgreeny on 2010-08-01
You can just open system-monitor and see if sshd is running in the processes tab.
**ssh-agent** should be by default in 10.04, but **sshd** will not be unless you have installed **openssh-server**.

You can do it in the command line or terminal with ```
ps -aux | grep ssh

```Only lines containing **ssh** will be shown.

I use ssh occasionally to network the family machines, but stop sshd from running at boot time by adding the line ```
service ssh stop
``` to **/etc/rc.local** just above the "exit 0" line.  Then when I want to use my machine as a server and connect from the other machines, I start **sshd** with the command ```
sudo service ssh start
``` for which I have set up a simpler and quicker alias of "ssh+", and then to stop it again I have an alias of "ssh-"

---

### Post by deb_untu on 2010-08-19
> **ajgreeny said:**
> You can just open system-monitor and see if sshd is running in the processes tab.
**ssh-agent** should be by default in 10.04, but **sshd** will not be unless you have installed **openssh-server**.

You can do it in the command line or terminal with ```
ps -aux | grep ssh

```Only lines containing **ssh** will be shown.

I use ssh occasionally to network the family machines, but stop sshd from running at boot time by adding the line ```
service ssh stop
``` to **/etc/rc.local** just above the "exit 0" line.  Then when I want to use my machine as a server and connect from the other machines, I start **sshd** with the command ```
sudo service ssh start
``` for which I have set up a simpler and quicker alias of "ssh+", and then to stop it again I have an alias of "ssh-"

Thanks for the post. This is what I was expecting.

---

