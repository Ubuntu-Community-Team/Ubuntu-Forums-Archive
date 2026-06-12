---
title: "Broadcasting A Netbios Name without Network Manager"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by Morgans on 2010-06-28
Hi there,

I am having an interesting problem where if I don't use the network manager in GNOME to connect to the network and connect via iwconfig and ifconfig commands, then my samba server won't show up in the network browsers of my other computers.  

I've recently done a fresh install of Lucid on my PS3, however I'm sure it's a software and not a hardware issue. I've setup the machine to not load up GDM by default, and setup the rc.local with the following commands:

```

iwconfig wlan0 key 0123456789
iwconfig wlan0 essid "MYWIFI"
iwconfig mode Managed
ifconfig wlan0 up
dhclient wlan0
```What I need help with is figuring out what the Gnome Network Manager does and how it does it, and how to replicate those results in a CLI environment. For obvious reasons, I would like to have it done all at startup, but I'm sure I can tackle some commands into the rc.local file. Ideally, what I'd like to have is a server that I can access just by pointing to either \\stuffserver or smb://stuffserver.local. I under no circumstances feel like modifying the hosts files of the clients (for purely philosophical reasons)

I should state that I've got the openssh-server package installed on the stuffserver, and that from my ubuntu netbook, I can log into it by typing [EMAIL="myname@stuffserver.local"]myname@stuffserver.local[/EMAIL]. I just need to figure out a way to get it to broadcast its netbios name to the other computers.

Thank you for looking,

Morgans

---

