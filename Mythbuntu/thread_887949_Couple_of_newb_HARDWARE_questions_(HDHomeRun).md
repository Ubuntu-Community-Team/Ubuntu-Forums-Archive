---
title: "Couple of newb HARDWARE questions (HDHomeRun)"
date: 2008-08-12
forum: Mythbuntu
---

### Post by BassKozz on 2008-08-12
_Ok here is my (soon to be setup) setup:_

**Server**: P4 3Ghz 4Gb RAM (Ubuntu Desktop 8.04 + Mythbuntu Primary Backend)
**Client 1**: PIII 900mhz 768Mb RAM (Mythbuntu Frontend)
**Client 2**: PIII 900mhz 768Mb RAM (Mythbuntu Frontend)
I plan on buying a [HDHomeRun]("http://www.silicondust.com/") to stream content to my Backend (Server).

_on to my questions:_
[LIST=1]
[*]Both of my Clients have on-board video (VGA-out) only, what video card(s) should I get so that I can watch HD & h.264 streams from these on my TV's (using Component, S-Video, & Composite cables)? Or am I better off getting [one of these]("http://sewelldirect.com/pc-to-tv.asp")?
[*]I currently have Comcast Cable, but I might soon switch to Verizon FiOS. Do I need to have a cablebox connected to the HDHomeRun in order to stream to "extended basic" channels (i.e. MTV) to the Backend?
[*]Do I need to have anything hooked-up (in addition to an Antenna) to the HDHomeRun in order to get 'Digital' TV on the HDHomeRun, or is it already built to convert digital signals? Also any recommendations on a good antenna/digital converter box for this setup?
[/LIST]

Man I need alot of help.  The setup shouldn't be that difficult as I am fairly savvy with Ubuntu and General Networking knowledge, but I just need to get the hardware figured out.
Thanks in advance,
-BassKozz

---

### Post by newlinux on 2008-08-12
1. I don't be able to do HD with those frontends (CPUs too weak). I don't think linux drivers for most graphic cards take advantage of a lot of the hardware acceleration yet, outside of xvmc for mpeg-2 acceleration. your backend machine has enough CPU to display HD.

2. The only stations you'll get from cable via the HDHomerun are unencrypted QAm stations, which usually are just you locals in SD/HD and a smattering of other stations. The stations you can get are depend on your provider and location - they vary a lot.I don't think the hdhomerun captures directly from cable boxes. You'd need a card with S-video/composite in like a pvr-150 to capture from a cable box and then you would need to setup an external channel changer. 

3. Provider your antenna can pick up the stations it is all you need for digital OTA stations.

---

### Post by BassKozz on 2008-08-12
> **newlinux said:**
> 1. I don't be able to do HD with those frontends (CPUs too weak). I don't think linux drivers for most graphic cards take advantage of a lot of the hardware acceleration yet, outside of xvmc for mpeg-2 acceleration. your backend machine has enough CPU to display HD.
Really, that's a bummer :(... What's the Min CPU needed to play HD streams?
Would it help or hurt if I had the backend transcode the streams first?
There aren't any video cards that I can buy that will allow Mythbuntu take advantage of a GPU to be able to play HD, to take the load off the CPU?
> **newlinux said:**
> 
I don't think the hdhomerun captures directly from cable boxes.
Another bummer :(
> **newlinux said:**
> 
3. Provider your antenna can pick up the stations it is all you need for digital OTA stations.
Any suggestions for an antenna?
Or should I [make my own]("http://www.youtube.com/watch?v=EWQhlmJTMzw") ;)

---

