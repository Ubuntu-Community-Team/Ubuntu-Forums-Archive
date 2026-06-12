---
title: "Restarting ssh after configuring"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by sideburns on 2011-11-10
I've just installed the latest version of Ubuntu on my sister's desktop.  I've set it to use the appropriate static IP and edited ssh_config to use the port I want.  (The router sends Port 22 to my box, so I had to pick a different one for hers.)  Now, how do I restart ssh?  I tried

sudo service restart sshd

and was told it didn't exist.  Also, how do I get to a terminal from Unity without going to an alternate console?

---

### Post by fyrmedic on 2011-11-10
Couldn't you just issue

sudo reboot

ctrl-alt-t will bring up a terminal window for you. Works slick.

---

### Post by papibe on 2011-11-10
You were close:
```
sudo service ssh restart
```
Regards.

---

### Post by d3v1150m471c on 2011-11-10
> **papibe said:**
> You were close:
```
sudo service ssh restart
```Regards.

 /etc/init.d/ssh not works anymore?

---

### Post by Lars Noodén on 2011-11-11
> **sideburns said:**
> ...and edited ssh_config to use the port I want. 

Shouldn't you edit [sshd_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) instead?  [ssh_config](http://manpages.ubuntu.com/manpages/oneiric/en/man5/ssh_config.5.html) is for the client not the server.


> **sideburns said:**
>  Also, how do I get to a terminal from Unity without going to an alternate console?

That would be ctrl-alt-t

---

### Post by sideburns on 2011-11-11
*Shrug!*  Typo.  Thanx for the tips.  Among other things, I need access to transfer a 14GB .tar.bz containing all of her personal files after a reinstall.

---

### Post by sideburns on 2011-11-11
I've made sure that sshd was installed and that I'd edited the correct file.  However, when I try

sudo service sshd restart

I'm told that sshd is an unknown service.  Checking the list of all known services, it's not listed.  what next?

---

### Post by papibe on 2011-11-11
Drop the 'd'. Take a closer look at post #3.

Regards.

---

### Post by sideburns on 2011-11-11
I'm not trying to configure ssh so that I can connect to other computers from my sister's box, I'm trying to configure sshd, the ssh daemon, so that I can ssh in from another computer.  Specifically, I need to run ftp over ssh to restore a backup of her home folder and I can't connect from my laptop unless sshd is running on her box.  And yes, sshd is installed.  Not only did I check for it, sshd_config wouldn't exist if it weren't.

---

### Post by papibe on 2011-11-11
A few pointers:
[LIST]
[*]There is no service or daemon for the ssh client.
[*]On the other hand, there is a service/daemon for openssh-server.
[*]Although the name of the program/daemon itself is called sshd (you can check it using 'ps'), the service (and the script in init.d) it is called just ssh.
[*]There are two ways of restarting the service. The old way:```
sudo /etc/init.d/ssh restart
```Or the new one:```
sudo service ssh restart
```.
[*]As a prerequisite the OpenSSH server package must be installed. For example:```
sudo apt-get install openssh-server
```
[/LIST]
If you still have the need for more detail information, check this [tutorial]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html") from the help Ubuntu site.

I hope this clarify some of the confusion.

Regards.

---

### Post by sideburns on 2011-11-12
I see.  Thank you.  If so, then what did I install when I installed sshd?  And, why was the file sshd_config missing until I did?  I'm not arguing, but would like to know what's happened.

---

### Post by Lars Noodén on 2011-11-12
> **sideburns said:**
> I see.  Thank you.  If so, then what did I install when I installed sshd?  And, why was the file sshd_config missing until I did?  I'm not arguing, but would like to know what's happened.

The [file /etc/ssh/sshd_config](http://packages.ubuntu.com/oneiric/amd64/openssh-server/filelist) is part of the package openssh-server.  It is the configuration file for the server and is not needed unless you actually have the server installed.

ssh_config, on the other hand, is for the client and that comes as part of the basic kit.  Most people don't know about or have much of a reason to change ssh_config.

There is a little bit of irregularity in the naming of services, so you have to type 'sudo service ssh restart' instead of 'sudo service sshd restart'  It has puzzled me before, too.

---

