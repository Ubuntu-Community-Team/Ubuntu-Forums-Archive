---
title: "openssh-server frustration"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by chee on 2012-10-10
So I tried to install ubuntu server on a 2ghz P4,  which apparently didn't work as it wouldn't boot,  saying there was an fd0 error.  So I figured I could just set up a regular ubuntu 12.04 install as a server with openssh.  My problem is that once everything is installed fine and the system is up and running when I view the sshd.config file (because I tried to connect to the computer via another computer running ubuntu, which didn't work) the file is empty.  I use "sudo gedit /etc/ssh/sshd.config" and there is nothing there.

Am I doing something wrong?  Is the computer too old?  This was supposed to be a learning project so that when I upgrade to a dual core for my server everything goes nice and smooth.

Here are the specs of the P4 server:
a7n8x-e deluxe motherboard
160 gb sata drive
160 gb ide drive
2gb ddr ram
older geforce 5700 graphics card
400w psu

Thank you for any help you can give!
Wes

---

### Post by albandy on 2012-10-10
Did you installed the ssh server?

sudo apt-get install ssh

---

### Post by Lars Noodén on 2012-10-10
Also, the file name for the configuration file is spelled differently than you have it.  It should be [ /etc/ssh/sshd_config ](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html)  It's strange, but that's how it is spelled.

---

### Post by chee on 2012-10-10
So I definitely installed ssh.  I actually installed ssh first,  then tried removing that and installing openssh-server.

The file name I am a bit embarrassed about,  cuz I don't really know when I started typing a "." instead of a "_", but that solves that.  

Now I just need to figure out why I can't connect.

Thank you,  I will post back after some reading.

---

