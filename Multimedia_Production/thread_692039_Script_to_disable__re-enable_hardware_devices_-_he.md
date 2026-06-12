---
title: "Script to disable / re-enable hardware devices - help needed"
date: 2008-02-09
forum: Multimedia Production
---

### Post by GingerAlex on 2008-02-09
The short of it:

I would like to write a script that disables certain devices, namely my audio record and playback, and obviously a script that re-enables them again. I'm guess modprobe is involved but to be honest I have no idea.

The long of it:

[LIST]
[*]I have a Presonus FP10 (formerly Firepod) which I would like to use for some home recording. I have a mutliple boot machine, with Ubuntu 7.10 (the default), a realtime kernel version, and Windows Vista for when times are hard. 
[*]I found that when I first started to use the Firepod, my laptop would hang within moments of switching it on, regardless of which operating system I used.
[*]I investigated this problem in Windows, where I am a little more certain of my facts, and found that to get it to work I had to disable my other audio devices. So I'm pretty sure it's just a hardware conflict between devices. However I'd rather use Ubuntu, and I use the laptop for general use outside of music so I don't want to just keep it as a 'clean music machine'. So a script to switch unwanted devices off when doing music, and back for general purpose is what I want.
[*]My laptop is an Acer Aspire 5612 (1gb ram, 2x intel 1.6Ghz), not sure of the exact sound hardware, but it shows up as Realtek audio manager in Windows, so lets assume its a Realtek..
[/LIST]

Any tips welcome - I'd quite like to use this to educate myself to Ubuntu workings so any background info welcome as well.

---

### Post by Stochastic on 2008-02-10
hmm that seems really strange.  I have a firepod and don't get any such issues, but it sounds like it has more to do with your laptop's bios than anything else.  I can't write a script for you but I can help a little (I think).  First post the results of ```
sudo lspci
``` as this will show the exact address of both your onboard soundcard and your firewire controller.

Out of curiosity, what process did you use to install the firepod (or FP10) in ubuntu?  for me, I just use jack to grab the freebob driver and this presents no conflict issue.

---

### Post by GingerAlex on 2008-02-11
```
alex@alex-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
07:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

```

I did manage to get this a bit further than this yesterday, using

```
modprobe -r snd-hda-intel
``` 

to disable the existing sound, I managed to get as far as recording a simple track in Audacity, and multi tracking another track over it to give the 'duplex' recording a little test.  However after I'd listened to my creation a couple of times, the system froze again (and I mean frozen, mouse not responding, caps lock light not responding..). 

The recording set up is as you expect, based on information in these forums:
-install jack and freebob
-add permissions for IEEE394 
how do you mean 'use jack to grab the freebob'? I think I just installed it via package manager as per usual.

I also have both OSS and ALSA installed as far as I can tell, this might mean something although I suspect you're correct this is down to a hardware issue somewhere.

thanks.

---

### Post by Stochastic on 2008-02-11
what I meant by use jack to grab freebob is that until I start jack via qjackctl or with  'jackd -R -d freebob' my firepod is entirely dormant.  Once jack starts and boots- so to speak - the freebob drivers then jack is the audio process that handles the firepod and nothing else.  Jack isn't attempting to look for other hardware etc.. and therefore I was worried that you having conflicts may have resulted from alsa wanting to run freebob or something like that (I don't know if this is possible).  Until Jack is started the firepod really shouldn't be interacting with the audio chain at any point.

---

### Post by GingerAlex on 2008-02-11
Hi - I don't think this is what is happening, I switch the firepod on, but the light stays red until I start Jack up. I'll have another play with it soon, experiment with lower sample rates, since it now works for a bit I'll see if I can get it to stay upright for a bit longer..

cheers!

---

### Post by Stochastic on 2008-02-12
so do you mean that as soon as you start jack, then your laptop hangs? or as soon as you turn on your os?

---

### Post by GingerAlex on 2008-02-13
Hi,

what I do is:
- switch on the firepod
- start up the jack controller
- launch freebob from that

I then get an indeterminate amount of time to play with my firepod - varying from seconds to minutes ( if I do the modprobe -r... thing ).

I think my next step is to do some more checking of this in Windows to ensure I can definitely get it running smoothly there before I try more experiments in Linux, unless you have a cunning plan?

cheers.

---

### Post by Stochastic on 2008-02-13
are you able to see what happens in the messages window of qjackctl right before it hangs?  what are your settings in jack like?

first step would be to make sure that verbose mode is on, then it's easier to troubleshoot.

---

### Post by GingerAlex on 2008-03-21
ok - I'm back on the case with this, after a uni project deadline led to music (and in fact most other forms of enjoyment!)  being left on the back burner for a while. Hope you are still around Stochastic!

Just had a play in vista - disabled the realtek sound devices ran with Cubase VST for a bit. Performance very similar to as described - normally get as far as recording a 2nd short track, then freeze during playback. The sound whilst I am playing along to track 1 had occasional pops and crackles on.

This leads me to think the problems are related to hardware, and I am as well off trying to fix them in Ubuntu as in Vista. I will try out your above suggestion and report back with further news.

---

### Post by GingerAlex on 2008-03-21
well, I've not got very far. I've installed the studio applications, which as far as I can tell is neither here nor there, and tried some safer settings to no avail.

In fact, on today's performance, the track and a half I did manage to record was something of a miracle!

I can see some posts around concerning the setting of IRQ priorities  - however I've not really made sense of them , and couldn't find out which priorities I need to set. Will look into this further, and any suggestions are welcome!

I've also renamed this thread to reflect the true problem.

---

