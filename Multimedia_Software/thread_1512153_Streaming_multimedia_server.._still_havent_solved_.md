---
title: "Streaming multimedia server.. still havent solved it"
date: 2010-06-17
forum: Multimedia Software
---

### Post by DJYoshaBYD on 2010-06-17
ok.. so here is my current set up for my server..

Ubunutu Hardy
3.2 P4 HT
1gb ddr2 800
Nvidia based Chipset; Foxconn board.. cant remember which one
1tb HD/sata

it does run a gui, and the following apps

samba - sharing media throughout the house
vsftpd
SSH server
VNC
Virtualbox running Windows XP Pro SP3
XP software - Pimpstreamer, Tversity, multiple codecs for all different formats.. all the basics

Now, the issue I am having, as you can see, is the fact that I do not have enough ram to run a virtual machine with XP, and serve, and encode that stuff on the fly.. in my house, it will run fine, but I remote access this stuff from outside with my PSP using pimpstreamer, and stream media from a browser with Tversity..

Now.. here is the kicker.. With vbox running and NOT encoding, it peaks my server out to about 900+mb of ram usage, and almost all my CPU, peaking out at 100% all the time

Without the VM, it sits at 125mb at idle, and up to 300mb at the most at full load, streaming to my laptop, gaming, and music pc, all while torrenting at full tilt.. 

The MAIN reason I want to NOT use a VM, is because its a very bulky solution to a simple problem:

Tversity has a very intuitive GUI, that I can access from outside of my network through a port forward, and stream WITHIN the browser.. 

I have not yet found a program for ubuntu/linux that has this feature, as that is a biggy..

Pimpstreamer i can live without, although its very slick.. its just doesnt run in wine :(

sooooooo

I would like a program that has the GUI that I can access through a web browser, that streams media, like Tversity has.. i have tried VLC, and other solutions, but none are as clean as Tversity..

Anyone got any ideas??

---

### Post by xzero1 on 2010-06-18
Mediatomb is a dlna server that has a web gui.

---

### Post by DJYoshaBYD on 2010-06-18
it has a web gui for management.. NOT streaming media like Tversity does..

Any other ideas?

---

### Post by DJYoshaBYD on 2010-06-18
bump :)

---

### Post by DJYoshaBYD on 2010-06-18
sooo.. i found gnump3d.. this will work for now.. now i just need to find a way to stream to my PSP, as PimpStreamer doesnt work in Wine.. (although, im going to try it again later)

Anyone stream video/audio to PSP?

---

### Post by DJYoshaBYD on 2010-06-18
I just got PimpStreamer working.. Im using the newest version of PimpStreamer, and I got the newest version of Wine for ubuntu 8.04.. I think it was 1.3.8 or something like that.. 

Everything streams to the gui now from outside of my network, but I have yet to test it on my psp.. Im sure it will work, as it works great on a computer.. 

Thanks for help? HOPEFULLY this solution will help someone else in my position..

:lolflag:

---

### Post by ghammar on 2010-07-07
I'm not using this for a PSP, but are you able to FF/Rewind the media file or does it just stream? I'm using minidlna and it streams to my Samsung BluRay player just fine, but it won't allow me any control other than start and stop.

---

### Post by DJYoshaBYD on 2010-07-09
no.. pimpstreamer just streams.. you cannot ff/rw with it, sadly..

---

