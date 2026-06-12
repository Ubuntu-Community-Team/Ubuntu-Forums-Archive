---
title: "setting up an /etc/network/interfaces file"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by dninja on 2005-12-19
I have a laptop with built in wired network card (eth0) and pcmcia wireless (eth1). There are a few situations where I use the laptop and need different configurations of the two cards.

[LIST]
[*]If I'm in the office and the wired cable is plugged in I want eth0 up and working as the default route.
[*]If I'm at home I may have a cable plugged in but it will probably be wireless so I want eth1 as default
[*]If I'm on the road then there is no network
[/LIST]

I use dhcp both at home and in the office and the main problem I'm having is the wired card sitting waiting for an IP even when there is no cable plugged in. Another problem is when I'm at home, if I have the cable plugged in I get two default routes, one through both cards.

Below is the /etc/network/interfaces file I'm currently using, can anyone suggest changes which would make my life easier?

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
        wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
        wireless-essid myessid
        wireless-mode managed



[edit]
can I add an extra bit on this, is there anyway to change what filesystems are mounted depending on where I am? In the office I have a number of nfs shares I need loaded, at home I want a different nfs share.
[/edit]

---

### Post by az on 2005-12-19
network-manager in universe is made for just this sort of thing.  So that you do not have to fiddle.

---

### Post by dninja on 2005-12-19
This is going to sound bad but, I've installed it, where is it? I'm running fluxbox but it installed a gnome applet so I guess if I was in gnome it would be obvious.

There are no binaries in the path which look like the right one.

Help!!!

---

### Post by az on 2005-12-19
usr/sbin/NetworkManager
I think.


How do the fluxbox menus work?  Do you need to have the menu package installed to get menus working?

---

### Post by jdong on 2005-12-19
I'll join the guessing game, but I believe it's called **nm-applet**? ;)

---

### Post by Lambert on 2005-12-19
You can run this command to find all files that were installed and where they were put. Not sure how many come with networkmanager but could be a long list. You should be able to look through this list and identify where the executable file is.

sudo dpkg --listfiles network-manager | less

---

### Post by dninja on 2005-12-23
Ok
I've got it installed it and found what to run - You were both right, there is a daemon and applet but has anyone got any good docs on actually getting it working? The homepage says things should just work but all it seems to do is to start a dhcp and dns server then give me a random IP address. What I want is for it to workout where I am and conect to the relivant network and set me up.

There are no real docs with it that help, can anyone out there?

---

### Post by mpvano on 2005-12-24
Hi:

I have a similar situation on one of my machines and I use the "auto" keyword to control WHICH interfaces come up in the following fashion.

I swap in several different versions of /etc/network/interfaces for different locations of by means of a script that

1. issues "ifdown -a" 
2. creats a soft link pointing to the desired file as /etc/network/interfaces
3. issues "ifup -a" to enable the new configuration

I use an old  X windows file selector program called "xgetfile"  in the script to select interfaces files, and I run the script via gksudo.

By specifying only "auto eth0" or "auto eth1" in a given file I can specify which of them will be enabled when the script performs the "ifup -a" command.

Of course, you want to keep the loopback interface always enabled by leaving it marked "auto" in all scripts.

So far, this is working great for me, and it also has the benefit of leaving the script configured properly to select the desired interface at boot.

You might wonder why I do NOT use some of the other proposed solutions. Some of the most common linux wireless card drivers do NOT support scanning and nearly all the slicker interface management solutions require this function or they do nothing useful!

Orinoco based cards using the kernel drivers are VERY common and they just don't work with the various network managers with the default drivers Ubuntu installs for them.

hope this idea is of some use to you

Mario

---

### Post by dninja on 2005-12-24
Mario
I like the idea, just one question, what gets setup at boot? If you start networking on boot then you will get the last interfaces file you linked which may be wrong for that situation, if you don't start networking then anything which has depenancies on networking, such as nfs shares, won't come up.

---

### Post by mpvano on 2005-12-24
That's exactly what happens, and in my case it's usually the right thing. If you need something else to happen, you'll need some fancier scripting.

The "interfaces" file syntax has a couple of more tricks available that might help you out. For example, I use the "pre-up" statement in /etc/network/interfaces to run a command or script that makes sure other network needs are satisfied.

I copy in the correct local hosts file for my different locations. This lets me use different Ip addresses (one on the LAN and one on the Open internet) for my own servers. The hostnames I use are aliases and they alias to different IP addresses in the local vs "roaming" host files.

You can use pre-up to solve many problems. There are also "post-up" and "pre-down" and "post-down" commands available.  These lines can run single shell commands or can run scripts, and you can use more than one in an interface stanza. Perhaps you can test or modify your mounts using some of these.

FYI here are two lines from one of my files that make sure resolv.conf is setup properly for my ISP and that make sure I'm using the preferred hosts file.

----------------------------------

pre-up echo -e "#home\nnameserver 209.98.98.98\nnameserver 208.42.42.42\n" > /etc/resolv.conf
pre-up cp /etc/network/vai/hosts /etc/hosts

---------------------------------

I don't use NFS shares myself at the moment on these machines, but I understand your problem - some Gnome applications get really upset if they're not always there.

Of course these are all klugey solutions, but perhaps you can come up with something you can live with until these drivers get standardized and Ubuntu adds a better solution.  One nice thing about these scripted hacks is that you can usually deal with adjusting them yourself to handle new problems....

I suggest spending a little time reading the man page for the "interfaces" file and those for ifup and ifdown. Also, studying the examples in /usr/share/doc. There's a lot of capability there, but it takes some work to exploit it.

Also, don't forget that the sleep scripts start and stop network interfaces according to their own ideas about what they think is running.

I'm sorry I can't give you a more complete solution, mine are a work in progress and I'm constantly fine tuning them or fixing unexpected problems, but they've generally worked well for me for several months on three different roaming notebooks....


Mario

---

### Post by dninja on 2005-12-24
Thanks for that, from that I reckon that I could get something working. All I need are 3 solutions, at home on wireless, in office on wired and anywhere else no network unless I specify it.

From what you are saying I could modify my fstab to include or exclude the NFS shares, the resolve.conf and IP are from DHCP in both situations so they should be ok.

I'll have a read and play and see what I can come up with.

---

