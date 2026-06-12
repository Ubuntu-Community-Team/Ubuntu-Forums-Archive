---
title: "Sound issues - Kubuntu Dapper"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by t0tAl_mElTd0wN on 2006-07-20
Hey, I'm having some issues with my sound that I was hoping somebody here might be able to help with. A little while ago I uninstalled Cedega (it completely didn't work whatsoever - things kept crashing), and after that, my sound no longer worked. I didn't change any mixer settings, and I have since looked back, and they are all still set correctly. What's interesting though, is that Gaim and xmms work fine, while Amarok, Juk, Totem, and KDE are all unable to play sound (but also leave no error message). I've tried setting the KDE settings to exactly what xmms and Gaim have, but still no luck. What's even weirder, is that the other account on this computer has full sound, no problems.

Hardware info:
[http://support.gateway.com/s/Mobile/Q106/MagicLC/1008831sp2.shtml](http://support.gateway.com/s/Mobile/Q106/MagicLC/1008831sp2.shtml) except for Windows

lspci:
```

0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0c.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:00:0c.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:00:0c.3 0805: Texas Instruments: Unknown device 803c
0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8185 (rev 20)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)

```
aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 2/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Need anything else, let me know. (By the way, I've been using Linux for a while now, so you can skip all the 'Ok, sir, unplug the hardware, wait 30 seconds, and plug it back in. Does it work now? Ok, sir, try reinstalling the software. Does it work now?' type stuff ;)

[edit] And yes, I've been googling it since 5:00 this afternoon when I got home, and yes, I've spent about the last 2 hours searching the forums.

---

### Post by t0tAl_mElTd0wN on 2006-07-24
Hey, sorry for the *bump*. I realize a lot of people have sound issues, but I've been looking all over the forums and Google, and I can't find anyone else who has solved these issues...

---

### Post by ltmon on 2006-07-24
Given it's working globally, but not for your account and only in KDE apps I would imagine that the hardware and drivers are all fine.

Anyway, a few questions that might help get to the bottom of it:

- How are you playing sound in KDE?  I find it useful to completely disable the KDE sound system (System Settings -> Sound and Multimedia -> Sound System -> Enable the Sound System (Checkbox)) and then work on the individual applications.

- What output engine are you using in Amarok? By default I think it's Xine.

- Is there a file ".asound" in your home directory?

Cheers,

L.

---

### Post by t0tAl_mElTd0wN on 2006-07-24
Well, I have no .asound file, but my other account doesn't either. I'll look up that file though, I seem to recall there being a .asound file there at one point.

By default I have the sound system set to Auto Detect, but I have tried Alsa, OSS, ESD, and Threaded OSS. No luck.

And yes, Amarok is using Xine. I've tried running GXine, but in the command line I get these error messages: ```
Failed to open device
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
```

---

### Post by ltmon on 2006-07-24
> **t0tAl_mElTd0wN said:**
> Well, I have no .asound file, but my other account doesn't either. I'll look up that file though, I seem to recall there being a .asound file there at one point.

You don't really need it unless you are screwing around with Alsa.  I was wondering if maybe Cedega had put one there for you which was causing the problem.

> 
I've tried running GXine, but in the command line I get these error messages: ```
Failed to open device
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
```
That's not a problem.  Mine does that also, it's just Xine trying to see if an infra-red remote control is running on your system.

Are you saying that GXine is not working either? How about just raw "xine testfile.mp3"?

Also try using the most basic alsa test I know of:
```

sudo apt-get install alsaplayer-alsa
alsaplayer testfile.mp3

```

L.

---

### Post by t0tAl_mElTd0wN on 2006-07-24
No, Gxine doesn't work, but what's interesting is that Gaim and XMMS still have sound.

And yes, Alsaplayer works fine. It seems to be just KDE and KDE-esque programs that don't work (amaroK, KDE, Kontact, juK, etc.)

...but all the settings seem correct in the control panel.

---

### Post by ltmon on 2006-07-24
Possibly it's the Xine engine that is screwed up.  Gaim probably uses ESD, xmms probably has something built in (?).  Maybe try the following:
```

rm -rf ~/.xine

```
This will delete all the settings for the Xine engine and cause them to default again.

The other possibility is that Arts is stuffed up.  This tends to be a constant thorn in the side for me and some others.

Most KDE programs, excluding the dedicated media players, use Arts which is yet another abstraction layer.  Arts probably then uses Xine behind it.  I personally disable arts, because I find arts to be both buggy and not very useful now that most hardware supports hardware mixing anyway.  You can then have all your kontact and other notifications sent by putting an external program in place of arts.

To do this go to:
"System Settings -> Sound & Multimedia -> Sound System" and then disable it. Next go to "System Settings -> Sound & Multimedia -> System Notifications".  Click on "Advanced".  In the very bottom right click on "Player Settings" and click the checkbox saying "Use an external player".  I then type "mplayer" in here, as it is fast and lightweight for this kind of job.  You will need to install mplayer first, but that's pretty easy using Adept. 

Hope this helps.

L.

---

### Post by t0tAl_mElTd0wN on 2006-07-25
HAH! Victory!

rm -rf ~/.xine did the trick. You know, I bet it was one of those times I had to improperly restart X - didn't have a chance to release configs or something.

Anyway, it works now. Thank you a ton! I have sound again ^_^

---

### Post by ltmon on 2006-07-25
It's nice when things work :)

---

### Post by NuclearPeon on 2007-05-27
Hello. 

I'm having some troubles with my sound on kubuntu. Well I tried using xmms and it's worked wonderfully, to my surprise. Amarok, Caffiene, and VLC plus the system sounds have all had sound that skipped horribly. I've tried removing ./xine but it doesn't seem to have helped.

I'm using Kubuntu 7.04 on a 1.1 ghz, 512 mb ram, avance ac97 sound card on-board computer. 

Also, is it possible to disable system sounds from the command line? Kubuntu has a different layout than ubuntu which is what I'm used to.

---

