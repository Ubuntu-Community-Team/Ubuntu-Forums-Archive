---
title: "getting Kworld atsc 110 and Avermedia A180 to work (tvtuners)"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by newlinux on 2006-11-15
I'm at my wits end at this point and in need of help. I have a kworld atsc 110 and Avermedia A180 tuner cards. I installed the saa7134-dvb drive per: [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110). I added saa7134-dvb to /etc/modules, and tried blacklisting saa7134 in /etc/modules. I don't know much about dmesg, but at least my cards show up in when I grep the output, so they are recognized. But when i try using tvtime (with no arguments, /dev/video0 or /dev/video1) it only lets me change the input between composit e and s-video (I assume this is from my video card, not either tuner). I'm not able to input any channels. I want to get these cards working so I can attempt to install myth. Any help is greatly appreciated. Attached is the output from dmesg. Any help is greatly appreciated in getting either of these cards to work (I think they both work with the same driver, so if I get one to work, the other should too...).

---

### Post by newlinux on 2006-11-15
Hmmm. for some reason my attachment didn't show up so I'm trying again with it gzipped...

---

### Post by newlinux on 2006-11-16
I swear I got these working on another ubuntu box without too much problem, but I can't figure out what I did differently. I followed the same instructions. Is it possible that installing myth will fix the problems :). I'm cautious cause I want to verify they are working before fooling around getting to work in myth. Any help is greatly appreciated.

---

### Post by newlinux on 2006-11-17
bump...

---

### Post by newlinux on 2006-11-18
Maybe this will end up being a log of my troubles, until someone puts me out of my misery. I've now got it to at least recognize there is a tv Input (I think it is recognizing the kworld tuner (perhaps I should just take out the Avermedia until further notice or take out the Kworld, and just start with one at a time). I did this by manually loading:
```
  modprobe saa7134 card=90 tuner=68 
```
However, although it says I have stations to change, I get nothing but a blue screen on all of the stations... I'll keep plugging along. Any help is appreciated.

---

### Post by newlinux on 2006-11-18
does it mean anything that xawtv won't run?
```

:/storage$ xawtv
This is xawtv-3.95, running on Linux/i686 (2.6.17-10-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

```

---

### Post by newlinux on 2006-11-18
replying to myself again... :)
Well, since dmesg seemed to recognize things when I simply loaded saa7134 and saa7134-dvb, I left it at that and went on to installing myth, which had no problem scanning for QAM stations with either card, so I think they are fine. I've already gotten myth to display channels through QAM with the Avermedia card, but no display yet with kworld (but it found channels when scanning, so I probably messed something up). For anyone that cares - not getting the cards to work with TVtime didn't stop them from working in myth. However, I have not gotten myth to recognize NTSC channels (not really that sure if I care), so that may be where the problem lies...

---

### Post by newlinux on 2006-11-19
probably last reply to myself... Anyone have a kworld atsc 110 card working in myth? I've gotten te QAM to work and display in the Kworld, but I don't even see an option for having the QAM and the NTSC work at the same time on the kworld... If anybody has any ideas that would be great... Cause I have another K-world on another computer that will also be a myth box...

---

### Post by newlinux on 2006-11-27
just as a quick update, in mythtvtalk forums I found only the pchdtv cards are setup to do QAM/NTSC tuning simultaneously in myth. They added Kworld ATSC 110 functionality to do this really quickly in the SVN...

---

### Post by dotnino on 2007-11-17
Hi, I'm in the process of installing Mythbuntu on top of Ubuntu Gutsy.  The Mythbuntu Tuner 
Card Support page claims that the Kworld 110 is broken.  What distro did you get your card working under?  I can't scan/tune/dispaly any channels with my Kworld under the Gutsy/Mythbuntu distro.

Any help is greatly appreciated.  Thanks!

---

### Post by Zero7 on 2007-11-19
> **dotnino said:**
> Hi, I'm in the process of installing Mythbuntu on top of Ubuntu Gutsy.  The Mythbuntu Tuner 
Card Support page claims that the Kworld 110 is broken.  What distro did you get your card working under?  I can't scan/tune/dispaly any channels with my Kworld under the Gutsy/Mythbuntu distro.

Any help is greatly appreciated.  Thanks!
I installed mythbuntu on fresh install of Gutsy Gibbon.  I  was able to tune NTSC channels with ATSC 115.  ATSC 110 and 115 are similar as per wiki. So I guess it is not broken. I have not tried tuning ATSC channels yet as I lost the small connector :(  I will try and update later. When I try changing the input (pressing Y in myth frontend Live TV, it changes from ATSC, NTSC and Satellite. I guess, now hybrid tuner is supported in mythbuntu, which is a good news.

However, I was not able to tune to Clear QAM channels. I don't know what I am missing and how to get the clear channels, which are about 12 video and >30 audio channels. I can tune them using Total Media.

---

### Post by Canezila on 2007-11-20
Hey... this response is about a year late but I just bought a KWorld 110 card and have been fighting to get ATSC to work.  Seems as though I can only pull standard signal.  I have been able to get HD from this antanna through a MSI HD card and WinXPee.  .... Now I am lost with what to do.  

I have tried using Mythubunu and it looks promising...  Just not there yet for my card I suppose.  Any works of wisdom?  

Brian:guitar:

---

### Post by newlinux on 2007-11-20
Tell us what you did (modules you loaded, mythtv-setup capture card settings, firmware load, etc.) and I can try and see what didn't work. I have these cards still working fine for QAM and ATSC in edgy and Feisty. Haven't upgraded my mythboxes to Gutsy so I can't speak to that, but I don't know why they wouldn't work...


@Zero7 - try the other input on the kworld card for QAM, and then scan. Sometimes they are like that, EVEN if it is a different input on windows. Heck, I once rebooted and the QAM input changed. No lie. What QAM scan settings did you use?

This thread details a lot about these cards:

[http://ubuntuforums.org/showthread.php?t=372635](http://ubuntuforums.org/showthread.php?t=372635)

---

