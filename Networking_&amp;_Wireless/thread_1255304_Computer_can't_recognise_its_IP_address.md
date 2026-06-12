---
title: "Computer can't recognise its IP address?"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by amanchesterman on 2009-09-01
I'm hoping that someone can help me resolve a problem I have every time I start my computer. I'm new to using Linux and I haven't found the answer to this question in these forums so far.

My computer is an old laptop, previously running Windows XP. I installed Xubuntu 9.04 (Jaunty Jackalope) because of memory restrictions, and it works fine: the machine has a new lease of life!

Like many other beginners, I had problems getting this machine to recognise the other machines running Windows XP on our Windows home network. I followed the advice in these forums (especially here: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)) and have resolved that difficulty successfully. I can now share and exchange files across the network, and can print from the Linux machine to a printer attached to a Windows PC.

However since these changes I now get a warning every time I start the Linux machine: *Could not look up internet address for linux-laptop.* [That's what I have called this machine on the network.] *This will prevent Xfce from operating correctly. It may be possible to correct the problem by adding linux-laptop to the file /etc/hosts on your system.* 

Of course, I have tried to take the advice in the message, but I don't really know what I'm doing. The Windows workgroup name is mshome, and Network Tools tells me that the IP address of the Linux machine is:

(l0)      127.0.1.1
(eth0)  192.168.2.7

The machine is connected to the network by Ethernet cable.

The content of the /etc/hosts file is as follows:-

[FONT=Arial]127.0.1.1    linux-laptop.mshome
192.168.2.7     linux-laptop.mshome
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/FONT]

Have I done something wrong, or failed to do something right? I'll be very grateful if anyone can help me solve this!

---

### Post by Brandon Williams on 2009-09-01
In your /etc/hosts file, change this:
```
127.0.1.1 linux-laptop.mshome
```
to this:
```
127.0.1.1 linux-laptop.mshome linux-laptop
```

Also, there should be a line in /etc/hosts for localhost that looks like this:
```
127.0.0.1 localhost
```

---

### Post by amanchesterman on 2009-09-01
Many thanks: I've made those changes to the file and the computer now starts with no problem. :D

---

