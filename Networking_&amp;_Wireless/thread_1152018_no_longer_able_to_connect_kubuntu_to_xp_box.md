---
title: "no longer able to connect kubuntu to xp box"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by techphets on 2009-05-07
Hi, 

I recently installed kubuntu and out of the box I was able to connect with my xp box and transfer files between the two. 

I haven't made changes to the xp system.  I'm sure I've changed things on kubuntu, most of which I am still learning about.  The latest change was that I removed the password from the wallet so that wireless would connect without prompting me at startup. 

When I use Dolphin to view Network > Samba Shares I still see my workgroup but shortly after selecting it I am prompted "Timeout on server workgroup." 

Any tips on how to troubleshoot, configure, and fix this problem would be appreciated. 

Thanks!

---

### Post by mattgyver83 on 2009-05-07
This is what worked for me in ubuntu, i would image it will work for you as well.

1.  sudo gedit /etc/samba/smb.conf
	verify domain is correct 'workgroup = your_workgroup'
2.  sudo apt-get install winbind
3.  sudo gedit /etc/nsswitch.conf
4.  edit 'files' line to include 'wins' before dns and m4dns
	hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
this line could also read
	hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4

Just verify #1 first as it could be all thats wrong, if not continue with the rest of the procedures.

Hopefully that will get you running.

---

### Post by AlanR8 on 2009-05-07
Been using Kubuntu for almost three years now and have had similar experience.

Using Dolphin then Places to get to Samba shares should let you see your network but I think I'm correct in saying it won't mount the remote drives. I discovered smb4k about a year ago, a neat little kde program that allows you to mount your remote shares very easily. 

On first boot it will search your network for machines then display them. By clicking on the machine you want to view it will open up any shares on that machine.

The advantage of doing it this way is you can now save or open documents, such as word processing documents directly to and from the remote share.

Let me know how you get on.

---

