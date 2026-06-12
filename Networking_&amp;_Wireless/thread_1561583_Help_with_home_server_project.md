---
title: "Help with home server project"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by drumknott on 2010-08-26
Hello everybody!

I'm totally new to Linux and networking and I really need some help with my home server project.

I have just built myself a mini-ITX PC to use as home server:
[LIST]
[*]Foxconn 45CTP Mainboard with onboard Intel Atom processor
[*]2 GB RAM
[*]1 x 32 GB SSD for the operating system
[*]1 x 2 TB HDD for file storage
[*]LAN onboard (10/100) + PCI LAN card (10/100/1000)
[/LIST]

My main requirements for this server are as follows (not necessarily in this order):

[LIST]
[*]print server: I want to be able to connect my USB printer (HP 1005P) to the home server and print wirelessly from any computer in the house (2 PC's and one Mac)

[*]file sharing server: storing files on the 2 TB HDD

[*]Internet gateway: at first I thought it would be nice but now I'm not so sure I need this. Especially if it complicates things.
[/LIST]

Could I use Ubuntu as operating system for the home server? How do I configure it? I don't even know where to start looking for information. I think Ubuntu Server might be better suited for the job but I fear it may be too much for me as a Linux beginner. And as I probably won't have Internet access while I'm setting everything up so I want to know what I have to do before actually starting.

I have an idea for how the network could look (see image below) but I have no idea how to put this into practice. This is why I would greatly appreciate any suggestion or advice.

[IMG]http://dl.dropbox.com/u/5258708/network.jpg[/IMG]

---

### Post by SlugSlug on 2010-08-26
With you being new - I'd go for the Ubuntu Desktop 1st

you then want to look at samba for the file/print server and maybe squid / iptables for the internet gateway..

loads of how to's about so I'd start of install Ubuntu Desktop get on the net with that and take it from there maybe starting with samba as that would be the easiest of the two...

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

