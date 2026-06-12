---
title: "hauppauge 1600, HDHR net tuner, ATI HDTV wonder pci on 3 ghz pentium 4 geforce 6200"
date: 2014-03-03
forum: Mythbuntu
---

### Post by sdowney717 on 2014-03-03
Assuming good signal strength, will these HDTV tuners work equally without stuttering playing HDTV?

On the hardware encoding, I know Haupage has it and ATI HDTV wonder does not. 

Does that only matter if encoding and not watching HDTV ATSC streams?

I figure the ATI and Haupage can also function as capture cards so hardware encoding would be better.

But if your just watching HDTV, is hardware encoding-decoding doing something on these tuners?

This pentium 4 3 ghz PC can play a 1080 video file recorded off the air from another WMC PC ok.

---

### Post by newlinux on 2014-03-03
The tuners don't have much to do with playback for digital streams like ATSC. Digital streams are simply captured and no hardware encoding is needed. The differences I've seen in digital tuners has to do with their tuning sensitivity, so assuming good signal strength they should capture ATSC signals equally. For capture the hardware encoding would come into play, but encoding standard definition analog streams isn't all that processor intensive with even older hardware. I used to use a P4 3.0 and 2.8Ghz computer to play back HD mpeg2 content without any problem (and without hardware acceleration via the GPU).

---

### Post by aelfric55 on 2014-03-03
Hardware vs. software encoding refers to how tuner cards (like the Hauppauge 1600 or the older pcHDTV 5500 card) handle analog streams --old-fashioned analog TV broadcasts, analog feeds from STBs, etc. For HD digital there is no encoding involved at all, hardware or software, with the simple recording of and the display of the embedded and already-encoded MPEG2 (or similar) streams of these broadcasts. All digital cards are (in theory) equal on this front. For HD watching on a Mythtv frontend, it's all about display and IO speed for large files. CPU speed, hardware-accelerated video adapters (PCI-e or AGP), fast SATA drives on the backend, and zippy fast-ethernet networking or the equivalent (where the backends and frontends are separated) are the essential features.

---

### Post by sdowney717 on 2014-03-03
Thanks, I went ahead and bought the cheaper ATI HDTV wonder pci card since hardware mpeg encoding will not be in play with HDTV. ($11.99)

Idea is use it with mythtv.

The PC is on a gigabit network.
I have the PC overclocked on its system bus to 220 vs 200, and it is stable.
I can put in a faster CPU which would make it run at 3.4 ghz with this overclock.
Base cpu is a 2.8 ghz now running at 3.06 ghz.

the board has sata ports, but I only have IDE drives on this, currently a wd800.
I think this board has those transitional early sata 1.5 connection.

This here is that board
[http://us.msi.com/product/mb/PM8MV.html](http://us.msi.com/product/mb/PM8MV.html)

---

### Post by aelfric55 on 2014-03-03
I have used a very similar MSI board for several years as a dedicated backend in my basement.  I also occasionally run a frontend on it when I want to watch a ballgame or some such while doing shop work.

I use an IDE hard disk on it for the OS only (where disk speed is unimportant).  I do recording storage on this machine on two 3TB sata drives, mounted under /var/lib/mythtv/.  Graphics is an older NVidia 8600GT, while recording is done from a couple of Hauppauge 1600s. The CPU is an old 2.8-ish Ghz  Celeron. Overclocking isn't necessary, and I'm always concerned with its long-term adverse affects on motherboards and components. No problems with HD LiveTV while simultaneously recording a second HD stream.

---

