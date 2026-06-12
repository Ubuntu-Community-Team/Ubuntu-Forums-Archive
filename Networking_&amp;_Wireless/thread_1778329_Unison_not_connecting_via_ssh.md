---
title: "Unison not connecting via ssh"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by gantww on 2011-06-08
I'm having a little trouble getting unison to work on Kubuntu and  can't figure out why.I have two machines. One is a dinky little box that I'm using for version control and as a file server. It has an IP address of 192.168.1.5.

My other machine is a laptop with an ip address assigned via DHCP. I can ssh from the laptop to the dinky box with no problems. However, in unison, I've set up a profile to sync /home/will with ssh://will@192.168.1.5/WillHomeSync. However, when I try to connect, it just hangs on the "Contacting Server..." window and does nothing. How do I even go about starting to troubleshoot this?

---

### Post by Ordes on 2011-07-18
it seems to be a bug..

solution 1: 
use ssh key authentication instead of password. here is a short and straight way to it
[http://linuxphilia.blogspot.com/2011/01/setting-up-public-key-authentication.html](http://linuxphilia.blogspot.com/2011/01/setting-up-public-key-authentication.html)
>> in case you using different ports for ssh, the copy-id will only work when adding "" ( > XXXX = your port);
$ ssh-copy-id "username@host -p XXXX"

solution 2:
people are claiming that the debian release is fixed and works fine.
[https://bugs.launchpad.net/ubuntu/+source/unison/+bug/696706](https://bugs.launchpad.net/ubuntu/+source/unison/+bug/696706)

here you get the deb
[http://packages.debian.org/wheezy/unison-gtk](http://packages.debian.org/wheezy/unison-gtk)

---

