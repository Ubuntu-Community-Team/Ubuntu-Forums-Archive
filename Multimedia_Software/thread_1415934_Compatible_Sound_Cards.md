---
title: "Compatible Sound Cards"
date: 2010-02-25
forum: Multimedia Software
---

### Post by carthmen on 2010-02-25
Compatible Sound Cards

Hello,

  I have recently become extremely upset with this whole pulseaudio, Ubuntu 9.10 thing.  I have tried removing it, stabbing it, and kicking it.  Nothing works.  Namely input at this time.

  So I will now through money at it.

  I did some searching and haven't found a good list of this yet, maybe because I'm frustrated so not searching as well as I think, or maybe there isn't one, either way.....

  What sound card do you use that works perfectly with a fresh Ubuntu 9.10 64bit install on a AMD 64 Dual Core System???

Thanks For The Info....

BTW..Cheaper is better!!

P.S.  We should have a sticky of confirmed to work with PulseAudio Cards until this mess is fixed up.

P.S.S.  It is way to upsetting to still have a copy of windows installed just to use vent for raids.

---

### Post by carthmen on 2010-02-25
More investigation....

  It is defiantly a hardware compatibility problem.  When I use my Bluetooth headset, it works fine.  Problem is the bluetooth only stays connected to pulseaudio for a few minuets, then disappears as a option in pulseaudio, even though the bluetooth is still connected.

  But this tells me it has to be a problem with the VT1708/A chip.

---

### Post by carthmen on 2010-02-25
Seems this blue-tooth thing is a really old problem.
[http://ubuntuforums.org/showthread.php?t=650586](http://ubuntuforums.org/showthread.php?t=650586)

Any known workarounds, or ways to fix this.

---

### Post by carthmen on 2010-02-25
I am starting to get the feeling that there is no card in the world that works on Ubuntu :(

---

### Post by markbuntu on 2010-02-25
I have a few that do but that is usually not the problem. if you want a cheap card that works OOB I have a SIIG Soundwave 7.1 PCI that has worked OOB on every Ubuntu since Hardy and on fedora and mandriva and debian and suse. 

In the past 3 years I have seen exactly one request for help with this card and that mysteriously resolved itself with a reboot. They are like $28. There is a 5.1 card that is even cheaper. Microcenter and Newegg usually have them in stock. They are not audiophile cards but they are better than the soundblaster cards in the same range.

---

### Post by carthmen on 2010-02-25
Thanks for the info!

 I have ordered the SIIG Sound Card, and will try it as soon as it arrives and report back, thanks.

---

### Post by markbuntu on 2010-02-25
If you have any problems just come back here, to this thread. You might need to reinstall alsa so the new hardware gets automagically set up but that is about it.

---

### Post by carthmen on 2010-02-26
I got the new sound card today.  Put it and and all seemed to pick it up just fine!

Problem however....

  Now I have the small pops in the sound that other ppl have described, and the audio just cuts out completely after about 5 mins.  Also don't know if this is right or not, but pulse audio after it cut out was taking up 168MB!!

---

### Post by carthmen on 2010-02-26
i installed the package 'libsdl1-debian-pulseaudio' and so far seems to have fixed it.

---

### Post by carthmen on 2010-02-26
Well it did fix the poping sounds, and pulse audio was only useing 1meg, but......

It still died after 5 mins of use, this time with 100% CPU load.  Once i closed all audio applications it went back down to 0 cpu load.

p.s.  The applications I am running are 'World of Warcraft' and 'Mangler'

---

### Post by markbuntu on 2010-02-26
Running WOW through wine has problems of its own, especially with sound. This has been a long running issue with wine. I don't use wine so I really have no idea how to help with that.

---

### Post by carthmen on 2010-02-26
Ok, so...

I did this to delete all the settings.

$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf as per [http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+cmedia](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+cmedia)

This helped as in the audio lasted almost 20 minuets (as compared to 3-5 minuets), but alas still cut out eventually with 99% cpu on pulseaudio.

---

### Post by carthmen on 2010-02-26
I wonder, if for a temporally workaround this if there was a way to write a script that would run in the background to refresh pulseaudio every few minuets.

I will look around and see if anyone has done this.

---

### Post by carthmen on 2010-02-26
I don't think it has anything to do with wow.  I just played a movie in the Ubuntu Native Movie Player and same thing happens with that too.

---

### Post by carthmen on 2010-02-26
Ok, one last update for the day.

I used 'gstreamer-properties' and selected pulseaudio.

This fixed the problem.

But now since it is using oss I presume, i can not have two audio applications running at the same time :(  At least i can have some sound for now till i get this figured out.  But I am pretty much right back to where I was now.

---

### Post by markbuntu on 2010-02-28
You might be missing some wrapper libs that are needed to get oss and old alsa apps to use pulse. Use the synaptic package manager and search alsa oss and pulse and get anything that seems likely. You also might try changing wine to use alsa instead of oss.

---

### Post by carthmen on 2010-03-01
To update, and finish of this thread.


   I got it all working!!!   Kinda of had to do it a backward way, and this most likely will not work for most other ppl having similar problems, but here it is anyways.

My internal VT1708 always has sound output working perfectly, the problem only came up using the mic with the VT1708 and PulseAudio.

So....

I ended up buying a CM8738.  This fixed my sound input problem instantly, however, as fate would have it I started having the common problem with pulseaudio just stopped working.

So my fix was this.  Use both cards.  To explain further, I am using the VT1708 chip for sound output, and the CM8738 card for input.  It might not be pretty but it works.

So in final proud to report Ubuntu is once again working without flaw.

Thank you for your help!.

P.S. Now since I have it working 'PulseAudio' is a excellent system, I just got a little frustrated with it there for a while.  I think It is great that Ubuntu team is sticking by it, we just need to hurry up and get the bugs worked out.

---

