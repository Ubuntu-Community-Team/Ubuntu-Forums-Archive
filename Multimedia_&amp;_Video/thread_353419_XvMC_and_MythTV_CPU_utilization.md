---
title: "XvMC and MythTV CPU utilization"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by Joshua on 2007-02-04
I just installed MythTV and my nVidia Drivers and followed the instructions for enabling XvMC in both the configuration files for X11 and in the Settings for MythTV, but I don't appear to be getting any CPU utilization benefits.  It's always 100%.  I am watching over-the-air HDTV with a pcHDTV card, but I still thought I should be able to get lower CPU utilization.

I'm using Bob deinterlacing, with an AMD64 Kernal, Athlon 64 3000+, and nVidia GeForce 6600 GT graphics card.

Anyone know what else I need to do?

---

### Post by Joshua on 2007-02-05
I thought that maybe I was using the wrong *.so.1 file.  So I changed the configuration file to try the three different ones that I found, but nothing seemed to change.

I'm only testing it by opening the System Monitor application and watching the graphs scroll by and then starting up mythfrontend.  Is there some other way to figure out if the nVidia drivers are implementing XvMC?

---

### Post by electronikjunkie on 2007-02-07
when using xvmc, your osd should be black and white scale (grey). i've been trying to get xvmc working smoothly for a long time. i'm running ubuntu 64 version with:

athlon64 3400+
1GB RAM
asus a8v-deluxe mobo
nvidia 5200 ultra
pchdtv hd-5500

without xvmc on, i get some hd channels over my cable connection with prebuffering pauses ever couple of seconds (depends on the channel, not all the channels have the pauses). with xvmc on i get a ton of prebuffering pauses ever single second on every hd channel. i'm not sure what the problem is. i've tried other graphic cards, different linux distributions, and different nvidia driver version. the only thing i havn't tried is a 32-bit os, which is my next step. i know on the xvmc page on mythtv.org there are several reports of successful xvmc usage with 64-bit os's. i'm pretty sure all of those successful reports where from the .19 version on mythtv. i'm going to try that too.

you should be using the .so file that has "nvidia" some where in the file name. i think it also has the word "dynamic" in it. that's the xvmc driver from nvidia. all you need is the file name of the driver in your XvMCConfig file, not the whole path name. make sure you have standard xvmc on in the playback settings. try watching tv, you should see a grey osd. if not, then xvmc is not working.

if you get yours working smoothly, i would love to hear exactly what you did! ;0>

---

### Post by Joshua on 2007-02-07
Hmmm... I'll go check out the XvMC stuff on the MythTV site, and double-check my computer's configuration when I get home tonight.

Two questions though - what is OSD?
And, I saw something a while ago about some workaround for a bug related to *.so.1 vs. *.so files.  Do you know anything about whether that applies here?  I've been using a file that ends with ".so.1"

I'll be sure to post something if I get it working.

---

### Post by electronikjunkie on 2007-02-08
on screen display. it the thing that shows the channel, usually it's blue.

---

### Post by Joshua on 2007-02-09
Ok, I think I got it working.  It turns out that rather than creating a new XvMCConfig file with the right *.so file in it, I just added new *.so files to the list and put a "#" in front of the ones I didn't want to use (I'm not a Linux guru or anything and most config files treat lines like that as comments, but this one seems to work differently).  When I ran mythfrontend from the command line and read the output it looked like it only used whatever I had on the first line of the XvMCConfig file (and naturally, if it started with a "#" then it couldn't find the right *.so file).  So I cleared everything except the *.so file that I wanted to use and then tried mythfrontend again - got the gray OSD and about 50% CPU usage.  Awesome!!  Interestingly, it looks like both of the *.so files that I had with "nvidia" in them somewhere worked.  i.e. one with "dynamic" and one without.  I'm not sure what the difference is.  BUT NOW - it looks like using XvMC makes the system unstable.  It takes longer to get a channel to play.  Sometimes it will show the old blue OSD and then stutter a bit and change to the gray one.  And sometimes changing channels will lock it up to the point that I have to do a hard restart.  Anyone know what is causing this?  I thought XvMC was supposed to be pretty stable with nVidia cards and drivers.

---

### Post by Joshua on 2007-02-13
So has anyone else run into instability in MythTV when using XvMC and nVidia cards?

---

