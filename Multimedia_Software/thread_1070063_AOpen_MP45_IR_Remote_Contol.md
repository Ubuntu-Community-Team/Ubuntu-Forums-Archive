---
title: "AOpen MP45 IR Remote Contol"
date: 2009-02-14
forum: Multimedia Software
---

### Post by Kewepas on 2009-02-14
Hi all,

I have spent all the day trying to configure the remote control of my AOpen MP45. At first I thought that it was a Media Center Remote Control and I tested almost all possible configurations.

I tried the classic "sudo apt-get install lirc" with the "Windows Media Center Remotes (new version Philips et al.)" option. I tried also the "Windows Media Center Remotes (old version MicroSoft USB ID)" but none of them worked. 

I tried manual instalation following these guides:
[http://ubuntuforums.org/archive/index.php/t-598506.html](http://ubuntuforums.org/archive/index.php/t-598506.html)
[http://www.gentoo-wiki.info/AOpen_MP965-DR](http://www.gentoo-wiki.info/AOpen_MP965-DR)
[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

But none of them worked. Moreover, "mode2" and "irw" simply killed the lirc process.

So, I looked to "lsusb" and I didn't see nothing. I suspected that the problem was the type of reciver.

After many test, I tested "SIR IrDA (built-in IR ports)". With this configuration "mode2" and "irw" don't kill lirc process, but when I push any key in remote control, the red light in front panel showed that the command was recived by the mother board, but "mode2" and "irw" didn't show nothing.

Anyone has MP45 remote control working with Ubuntu?
Anyone has any idea about how could I continue?

Thank you

---

### Post by patrickjlbyrne on 2009-02-15
Hi - I have the same problem.

The red receiver light on the front of the box does come on when I press buttons on the remote. I haven't investigated any more yet. I will post here again if I make any progress.

I have mythbuntu installed on top of ubuntu 9.04.

I don't suppose you might know why installing mythbuntu seems to kill spdif out? It was working under Gnome.

Also, do you have decent graphics performance? I am only getting 60fps in glxgears?

Sorry to answer your question with more questions, but perhaps we can share info if we are both trying to get ubuntu working properly on the mp45.

Regards,
Patrick

---

### Post by Kewepas on 2009-02-15
Hi Patrickjlbyrne

I haven't tested yet audio & video :(

I have installed Intrepid with a MinimalCD distribution and I'm trying to get things done step by step. At this moment, I'm with a simply console.

If I take some step ahead, I will post it here!

Regards

---

### Post by Kewepas on 2009-02-19
As I supposed, I've connected an USB Media Center Remote and LIRC works fine (both irw and mode2). The problem is to know the type of Remote Control that MP45 has.

I tried a lot of types, but none of them work. I've seen that the Remote Control has a direct connection to the mother board. So, I've supposed that it is a "SIR IrDA (built-in IR ports)" but it doesn't work... I still trying...

---

### Post by patrickjlbyrne on 2009-02-23
Hi again,

I am on Fedora 10 now, because it had the fast intel drivers for video. I can't get lirc working though! Argh.

---

### Post by patrickjlbyrne on 2009-02-23
Um, this looks promising. Seems that a fix is upstream....

[http://1n73r.net/category/linux/mythtv](http://1n73r.net/category/linux/mythtv)

---

### Post by Kewepas on 2009-02-27
> **patrickjlbyrne said:**
> Um, this looks promising. Seems that a fix is upstream....

[http://1n73r.net/category/linux/mythtv](http://1n73r.net/category/linux/mythtv)

No... it doesn't work because MP945 uses a Media Center Remote Controller (using USB) and MP45 uses a direct connected to mother board IR. 

I connected a USB Media Center Remote Control to MP45 and It worked perfect. Then problem is that the MP45 native IR type is unknown... I've tried all kind of IR types that LIRC has, but I haven't had luck :(

I still trying... but I don't know more paths :(

---

### Post by pzeigler on 2009-03-04
I have **SOLVED** this problem on my MP45-DR in 8.10.

**Install needed apps:**
```
apt-get install libtool autoconf automake linux-headers-`uname -r` cvs lirc lirc-x
```

**Get Lirc source: (Hit Enter for the password)** 
```
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
```
[B]
Install from source[/B]
```
./autogen.sh
./setup.sh
make
make install
modprobe lirc-mceusb2
```

[B]
Here is the important part! Getting the drivers in the right place.:[/B]
```
cp /lib/modules/`uname -r`/misc/lirc_dev.ko /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko
cp /lib/modules/`uname -r`/misc/lirc_mceusb2.ko /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_mceusb2/lirc_mceusb2.ko
```

**Finish up:**
```
rmmod lirc_mceusb2
rmmod lirc_dev
lsmod|grep lirc
/etc/init.d/lirc restart
```

I hope this helps. I took me two days to figure it out because I am a novice.

---

### Post by patrickjlbyrne on 2009-04-10
Working now, thanks very much Kewepas.

I feel I should add, for those slow on the uptake like myself, that most of those commands need to be prefixed with sudo, if root privileges are required.

Also, the Infrared remote control dialog in Gnome confusingly refuses to (apparently) recognise the remote control. It is however working, and the bottom part of the dialog correctly shows buttons pressed on the remote as you press them.

---

### Post by patrickjlbyrne on 2009-05-07
I have been mailed to ask what I think of the my new AOpen MP45 system. I am replying here for the benefit of 'Da Community':


Video
-----

I have had a few problems with the video drivers, but nothing major. There have been occasional stability issues which appear to be related to the rapid intel driver development which is ongoing (according to sites like Phoronix). Hi-Def video seems to play back with easily <50% load on the CPU.

I have the video out running through a VGA-composite converter to plug into my old-style non hi-def TV. I have seen a problem where the VGA connector slips slightly and the screen comes up yellow - which makes X come up in low-graphics mode, refusing to start the desktop and insisting I 'reconfigure graphics and restart'. Re-seating the VGA connector appears to fix this.

Picture quality in composite is worse than my FreeView box! That won't be a problem for most people with HDTV-DVI I am sure.

I haven't gotten DVD playback working yet, but that just seems to be DRI / Driver woes, nowt to do with the box.


Audio
-----

It has been a little fiddly to get spdif-out working, but this seems to be more of a problem with Ubuntu/Gnome/Xine etc than anything else. Xine (or is it MPlayer?) needs 'AC3 passthrough' enabled for sound to reach spdif out.

Volume control doesn't seem to work within applications that use the passthrough, so I have to use the amp to adjust volume.

I have noticed crackles at some point but not recently, perhaps the drivers improved, and anyway my amp is severely screwed - crashes quite regularly.

This thread talks about audio and the MP45:
[http://www.avsforum.com/avs-vb/showthread.php?t=1063410&page=2](http://www.avsforum.com/avs-vb/showthread.php?t=1063410&page=2)

If anyone knows of a (stereo) amp which takes spdif input and is roughly the same size as the MP45 then I would love to hear about it. I have yet to find such a beast.


DVI
---

I have a Hauppage usb DVB-T, which I had to download the firmware for to get it working. Seems to work fine. I have had issues with DVB-using apps being a little clunky - totem seems to be rather confused by it, trying to install the drivers and failing. One hopes this will get fixed eventually as the Open Source Juggernaut inches forward.

I would have liked to buy the TV adapter that AOpen show on their website, which plugs inside the box itself, but I couldn't find a supplier.


Remote
------

The Windows Media Centre remote supplied with the box works ok for basic functions - I had to recompile lirc as detailed above in this thread. Not all the keys appear to do something useful in mythtv, but play/pause/stop/change channel all work. I am sure that the extra keys can be made to do stuff, I just can't be bothered to look into it yet.

The remote also appears to control other apps like totem / xine.


Heat
----

I installed a 7200rpm drive and it runs a little hot - 43+ degrees Celsius. I am in the process of rebuilding with a 5000rpm drive, hopefully this will be much better.


Noise
-----

Yes it is very quiet! Lovely design - no wasted space at all.


BIOS
----

Annoyingly, the BIOS will not start without a keyboard plugged in.


Access
------

I have it set up so I can log in via ssh, start a detachable terminal session with screen, and start (say) mythfrontend:

  export DISPLAY=:0 && mythfrontend

This starts mythtv using the primary display.

Remote desktop login works fine too, though playing video kills the speed of course.


Summary
-------

Yes it's great. Setting it up hasn't been too distant from the 'out-of-the-box' experience I want. It looks powerful enough to handle hi-def video, spdif output sounds fine, and I just love the design of the thing - it is exactly as big as it needs to be and no more. And it is shiny.

When it comes time to replace my home desktop I fully expect to get another box like this - I don't need bleeding-edge gaming graphics. I only wish other manufacturers were making things like this - might bring the price down.


--
Patrick Byrne

---

### Post by patrickjlbyrne on 2009-05-07
This thread has quite a lot of chat about recent intel driver development:
[http://www.phoronix.com/forums/showthread.php?t=14235](http://www.phoronix.com/forums/showthread.php?t=14235)

---

### Post by pkkid on 2009-05-08
Great information, thanks for the update. :)

---

