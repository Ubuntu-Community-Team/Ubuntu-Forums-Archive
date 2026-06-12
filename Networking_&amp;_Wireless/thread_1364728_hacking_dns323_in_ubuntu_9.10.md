---
title: "hacking dns323 in ubuntu 9.10"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by hosinfefer on 2009-12-26
Hi everyone

I am a complete noob and want to hack my dns 323 to install the better torrent program. I have a windows 7 host running vmware with an xp box and a ubuntu 9.10 box. I have seen some "how to's" on the internet but seem very confusing. Can someone help me out with hacking my nas?

Thanks

---

### Post by kerry_s on 2009-12-26
Can you be more clear, why does it have to be hacked?

---

### Post by hosinfefer on 2009-12-26
well the torrent program built into the nas from dlink is SSLLOOOWWW. I get maybe 4-8kb\s with it. I then dial into my ubuntu vm and set up the same torrent and sit at 200+kb\s. The nas box can d/l on its own. I dont have to leave my main box on all night. Would be nice to change out the torrent program to the linux one and let it run over night.

---

### Post by kerry_s on 2009-12-26
looking at this page:
[http://www.dlink.com/products/default.aspx?pid=DNS-323&tab=3](http://www.dlink.com/products/default.aspx?pid=DNS-323&tab=3)

it would mean replacing the firmware, which is very dangers & could brick the nas.

---

### Post by hosinfefer on 2009-12-27
well from my research the unit uses a linux os. Once you install a fun plug or something you can then just load the program onto the box and ssh (Not sure what that is) into the box and everything should work. 

something like this

[http://www.shadowandy.net/2008/05/transmission-for-dns-313-dns-323.htm](http://www.shadowandy.net/2008/05/transmission-for-dns-313-dns-323.htm)

---

### Post by kerry_s on 2009-12-27
:lolflag: that's a lot of work, have you tried tweaking the installed client?

---

### Post by paxmark1 on 2009-12-27
yes, the fun plug script is quite sweet.  It is pretty low risk, but risk is there.  chmod data files the wrong way, and you might think that you have lost date. If you know your way around the command line (telnet ssh chmod )and typing things like /mnt/HD_a2 instead of using a gui to get to /media does not scare you, you are ready.

I do not know if you can torrent faster from the DNS with the torrent from fun plug or the preexisting dlink version with firmware 1.07 I believe.  

I use the command line program rtorrent on my main computer and send it over to a usb hdd and then back it up onto the nas using grsync via ~/.gvfs  I use wipe -qrc for the files that were on my box that I sent over.  qvm (part of renameutils) is a fair command line editor of files and fdupes is nice for finding duplicates.

---

### Post by hosinfefer on 2009-12-28
no the client is very basic with no options for making the torrents run better. I thought there would be a ton of people on ubuntu forums hacking this thing.

---

