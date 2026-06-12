---
title: "ssh issue"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by gunter1959 on 2013-05-19
Am new to ssh, so this might be simple.

This command works:

gunter@Laptop:~$ ssh gunter@192.168.1.8
gunter@192.168.1.8's password: 
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-43-generic-pae i686)
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
0 packages can be updated.
0 updates are security updates.
Last login: Sat May 18 21:54:40 2013 from laptop.local
gunter@P4ubuntu:~$


But this one doesn't:

gunter@Laptop:~$ ssh gunter@p4ubuntu
ssh: Could not resolve hostname p4ubuntu: Name or service not known
gunter@Laptop:~$

I'm guessing some name server isn't working???
How can I get this to work?

---

### Post by Hadaka on 2013-05-19
Hi, this should give you and understanding..

[http://teamprincipia.wordpress.com/2008/05/29/beginning-ssh-on-ubuntu/](http://teamprincipia.wordpress.com/2008/05/29/beginning-ssh-on-ubuntu/)

have fun

---

### Post by gunter1959 on 2013-05-19
Not sure if fun is the right word  ;)

I went to that website, it looked like a possible answer to my problem. So I edited "config" with

Host p4ubuntu
    HostName 192.168.1.8

and now the error message changed to:

gunter@Laptop:~$ ssh gunter@p4ubuntu
Bad owner or permissions on /home/gunter/.ssh/config

Well, "gunter" is the owner, and has r/w permission.

---

### Post by gunter1959 on 2013-05-19
Anyway, even if this did work, it will just substitute a word for the IP address, so if the router decides to give "p4ubuntu" a different IP address, then the script I'm using for ssh or rsync won't work (or sync with the wrong PC)

---

### Post by d.atanasov on 2013-05-19
Well hello, 

I would suggest to fix the IP of the p4ubuntu in the router settings and then you can use the rsync and ssh without caring about the name.

---

### Post by gunter1959 on 2013-05-19
Update:

Found out that changing the file permissions of "config" so ONLY "gunter" has ANY permission made it work. (weird, ssh worked before, and I didn't play with the permissions until ssh didn't work!?!)

I think, the issue as per forum header is resolved, thanks to some fast and helpful people! Hadaka's link was particularly helpful.

---

### Post by prodigy_ on 2013-05-19
Using **~/.ssh/config** is not the right approach to setting up name resolution. It's more like last resort. In most cases you should set up some conventional name resolution scheme: **/etc/hosts**, DNS, WINS or zeroconf.

---

### Post by steeldriver on 2013-05-19
The desktop edition of 12.04 should come with avahi zeroconf out of the box, so it should be possible to address your machine on the LAN using the default '.local' suffix i.e. p4ubuntu**.local** 

You can check the service is running with

```
service avahi-daemon status
```

For the server edition you just need to install the avahi-daemon package

---

