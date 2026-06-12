---
title: "ssh problems"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by gdonwallace on 2009-11-30
So I come in this morning to a problem with a nightly download that is performed on another machine and emailed to one of the people I work with.  The same thing happened last week, so I did what I always do, I tried to ssh into the machine and run the download manually.  However; today I get a message I have not seen before.

ssh -v 192.168.1.166
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.166 [192.168.1.166] port 22.
debug1: Connection established.
debug1: identity file /home/mingw/.ssh/identity type -1
debug1: identity file /home/mingw/.ssh/id_rsa type -1
debug1: identity file /home/mingw/.ssh/id_dsa type -1
**ssh_exchange_identification: Connection closed by remote host**

I have done searches on this forum and through google and have come across many people posting something that is supposed to fix it, but nothing seems to be working.  

Some background: Nothing on either machine has changed.  Except for patches that are applied from Ubuntu, I have not made any changes to my machine.  The same for the target machine; except for patches from Fedora, nothing has changed on it as well.  I have check both the /etc/host.allow and /etc/host.deny; nothing is in either file.  I checked the sshd.config file to ensure that *maxstartups* was not set to low, and that line is remarked out, so it is not being used.  

I moved the known_hosts file to a tmp backup, hoping that it would recreate the file and create a new "key" for the machine I was attempting to connect to, no help there either.  

I also rebooted my machine, thinking that something with SSH may be hung up.  Didn't change anything.

So, does anyone have any ideas on what may be happening?

---

