---
title: "vmware, winxp, and firewire audio mixers"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by tedrampart on 2006-11-25
hello, 

I've just converted my laptop to Edgy, and the intent was to have a free opensource mobile recording station.

what I would like to do (but don't have it yet) is attach a FireWire Mixer to the laptop and run it similar to how CubaseSX would work with it in windows.

I've searched google, and this forum for connecting a firewire device like this to linux, and it didn't turn up promising results (either not possible, or a lot of trouble, since I am somewhat a newb.).

so I'm wondering what a good solution would be.. I thought about running VMware, but then I'd have to use windows anyhow (still better than straight windows as its hosted in linux).. would the firewire device have to be compatible with linux, or just windows?

I used my old laptop with Audacity with a regular analog mixer plugged into the mic-input, but it was terrible quality sound, so we're thinking about upgrading to a more clear/digital way of recording.. hence the firewire mixer..

I would really like some help, as I really don't want to have to resort to using winblows again.. but so far its looking that way...
thanks in advance... I'll keep searching too..

---

### Post by Mike'sHardLinux on 2006-11-26
I would expect performance issues if you use VMware in that way. It is good for running normal applications, but games and recording software require more resources, especially if you're going to use DX effects. Also, recording applications access the hardware on a lower level that may not work properly in VMware, although this is kind of a guess. Also, latency will likely be a BIG problem running windows in VMware.

Be sure and do lots of research on the interface. I have a $1300 firewire interface(Fireface 800) that won't work in Linux, and RME says they won't make drivers for Linux....ever. This means I'm stuck with Windows for recording, unless I get rid of the Fireface and get something else (no chance of that happening.)

---

### Post by tedrampart on 2006-11-27
hmm thanks for the tip.. latency would be a major problem now that I think of it.  

it looks like for now, the option is to have a dual boot.. which kinda sucks.. though my bass player said he found a tascam fw1804 write up saying it worked in linux.  though I'm guesing it won't be easy..

plus there's this page I found..
[http://freebob.sourceforge.net/index.php/List_of_Supported_Devices](http://freebob.sourceforge.net/index.php/List_of_Supported_Devices)

---

### Post by Mike'sHardLinux on 2006-11-27
:( That page further confirms RME will never support the Fireface in Linux.

Just in case, I thought I'd mention there is a whole forum on Ubuntu Forums for recording: "Ubuntu Studio" [http://www.ubuntuforums.org/forumdisplay.php?f=128]("http://www.ubuntuforums.org/forumdisplay.php?f=128")

---

