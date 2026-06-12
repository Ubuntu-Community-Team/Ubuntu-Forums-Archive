---
title: "Problems with DVD backup (K3b/Kaffeine)."
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by myoozeman on 2008-03-06
Hello everyone.

I´ve been having some problems while trying to backup some movies with K3B and subsequently playing the .iso image I got with Kaffeine. I had done this before and I had experienced no problem what-so-ever. I have not messed with K3b, Kaffeine, or Libdvdcss2 since I last backed up a dvd in the same way (and it plays fine). I´m using Kubuntu 7.10, K3b version is 1.04 and Kaffeine version is 0.8.6

What I have experienced is that while crating the .iso image, K3b sort of stalls, meaning that the clock keeps ticking but the megabytes counter is still, then it gets a huge boost (a hundred of mbs/1GB in a few seconds). upon completion of the process I get a ¨successful¨ output dialog.

When I try to run the .iso image with Kaffeine from the terminal using 
kaffeine dvd://home/username/imagename.iso
I am able to watch those anti-piracy messages and some trailers you get before actually seeing the menu, but once I choose anything from the menu kaffeine stops playing and the console output gives me an error concerning libdvdnav and 000000 when it should be 0x000001 (since I deleted the .iso image I cannot post the error message. will do as soon as I rip it again.).
it is happening with 3 different dvds and dvds I have backed up in the past with this method play perfectly with kaffeine. anyone has any ideas?

---

### Post by jelofson on 2008-03-06
> **myoozeman said:**
> Hello everyone.

I´ve been having some problems while trying to backup some movies with K3B and subsequently playing the .iso image I got with Kaffeine. I had done this before and I had experienced no problem what-so-ever. I have not messed with K3b, Kaffeine, or Libdvdcss2 since I last backed up a dvd in the same way (and it plays fine). I´m using Kubuntu 7.10, K3b version is 1.04 and Kaffeine version is 0.8.6

What I have experienced is that while crating the .iso image, K3b sort of stalls, meaning that the clock keeps ticking but the megabytes counter is still, then it gets a huge boost (a hundred of mbs/1GB in a few seconds). upon completion of the process I get a ¨successful¨ output dialog.

When I try to run the .iso image with Kaffeine from the terminal using 
kaffeine dvd://home/username/imagename.iso
I am able to watch those anti-piracy messages and some trailers you get before actually seeing the menu, but once I choose anything from the menu kaffeine stops playing and the console output gives me an error concerning libdvdnav and 000000 when it should be 0x000001 (since I deleted the .iso image I cannot post the error message. will do as soon as I rip it again.).
it is happening with 3 different dvds and dvds I have backed up in the past with this method play perfectly with kaffeine. anyone has any ideas?

This might not be of much use to you, but have you tried K9Copy? I have used it with pretty good success, especially selecting only the chapter/title I want and shrinking the ISO to a reasonable size. 
I use this program to extract DVDs and put on my myth box. It has more options than the integrated dvd ripping in mythtv. My kids are really hard on DVDs so getting them on the hard drive is a great thing.

[http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)

I haven't used k3b so I can't really help.

---

### Post by wolfen69 on 2008-03-06
i have used K9copy in the past with no problems. have you tried it?

---

### Post by wolfen69 on 2008-03-06
> [http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)
it is also in synaptic. much easier.

---

### Post by myoozeman on 2008-03-06
Nope, I have not tried it. The reason is that I wanted full images, with menus, extra contents and everything, instead of the ¨main¨ title rip only.

Error message: libdvdnav: demux error! 00 00 00 (should be 0x000001)

could it be that it is something like this?
[http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html)

EDIT: I tried K9copy. can´t even get it to complete the iso image generation.

---

