---
title: "Kaffeine and HDTV movies"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by dumas33 on 2007-07-10
I downloaded HDTV movie, just want to try how good quality it is. 

Unfortunately I can not play it. Kaffeine shows blue screen sound seems OK. 

Anyone knows how to watch HDTV movie in ubunu. (I use Kubuntu 7.04, video Intel 915, resolution 1280x800

Waiting for comments.

Dumas

---

### Post by hyrule_man on 2007-07-10
Well before anything, I'd reccomend updating to Kubuntu 7.04. That's been out for a while now, and frankly it makes Edgy and Dapper obsolete. Not too sure about your problem though.... Sorry.

---

### Post by dumas33 on 2007-07-10
it was mistake i'm using kubuntu 7,04

---

### Post by dumas33 on 2007-07-13
so, nobody knows how to play hdtv video on ubuntu?

---

### Post by xc3RnbFO8P on 2007-07-13
Have install all codec, and have you tried VLC player?

---

### Post by Contrast on 2007-08-18
You most likely just need to add this line to the device section of your xorg.conf:
VideoRam 65536
That will allot 64MB of your RAM to the video card.

---

### Post by stoeptegel on 2007-08-18
I watch HDTV with kmplayer and w32dcodecs.  W32codecs does also work with kaffeine, though mplayer seems be able to crash less than xine here for some reason.

---

### Post by mtron on 2007-10-24
i managed to get European HDTV (h264 codec) in kaffeine. It works quite well if you grab xine-lib 1.1.8 from source.

Xine keeps also it's own ffmpeg snapshot which does the HDTV stuff, but it's quite old so you will also need a fresh ffmpeg svn checkout, and pass the switch --with-external-ffmpeg to the others when running ./configure in xine-lib.

So you'll get the real  bleeding edge xine-lib & HDTV working

---

### Post by zak123 on 2008-06-23
Using Hardy with kaffeine 8.6 this tool me ages to work on my laptop using intel 945 chip set.
Problem was HDTV would blues screen SD channels could view ok.
insert the following lines in xorg.conf and rebooted PC.

Viewing HD Material

    * Add a LinearAlloc option line to your xorg.conf. E.g. : 

/etc/X11/xorg.conf

 Section "Device"
       Identifier      "IntelIntegrated"
       Driver          "i810"
       BusID           "PCI:0:2:0"
       Option          "LinearAlloc"   "16384"
 EndSection

16mb of memory seems to be enough for my setup, yours may vary.

---

