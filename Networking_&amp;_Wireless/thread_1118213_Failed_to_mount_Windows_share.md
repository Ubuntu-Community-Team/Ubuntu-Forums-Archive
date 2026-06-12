---
title: "Failed to mount Windows share"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by zimbot on 2009-04-06
I have ubuntu 8.04 and I can no longer mount shared folders on windows machines on my lan

This used to work under 7.04

I am certain about a proper login & password

I can "see" the machines
Places > network > windows Network
and i see wORKGROUP ( so far so good )
I can go into Workgroup - i can 'see' a given machine
and if I click on one of those - I can "see" the shares
If i clck on a share i get a login passwd challenge ( here is where things go wrong )

I enter USERNAME & Password and get a

Unable to Mount location

Failed to mount windows share

It seems like the auth is diffrent or something... dunno ( but i used to work) note i can still Mount my ( local attched NTFS , w NTFS conf tool ) win drive -- but that is a very diffrent situation.

How can I get to those windows shares?

Thanks!

---

### Post by lisati on 2009-04-06
Do you have something like samba installed? If not there's a good tutorial here: [http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting)

---

### Post by zimbot on 2009-06-09
my problem is not win machines seeing my ubuntu machine...
it is my ubuntu machine seeing
1. my local sata 2nd drive formatted ntfs , this is a dual boot machine ubuntu & xp.
my 2nd drive is all windoze.
I used to be able to mount it w ubuntu 7.04 ntfs-configuration tool.

2. my ability to get to win machines FRom my linux machine

---

### Post by Iowan on 2009-06-09
See if this [How-To]("http://ubuntuforums.org/showthread.php?t=1169149") helps.

---

### Post by superprash2003 on 2009-06-10
you could also try accessing via ip , 
[http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

