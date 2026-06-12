---
title: "Sound in Ubuntu"
date: 2008-06-16
forum: Multimedia Software
---

### Post by mvvemden on 2008-06-16
Long story, I'm trying to be at least a bit complete in what I have and haven't done.

Can't seem to get sound to work properly, so I hope you guys/girls can help out. I'm pretty much lost in where to start, there's plenty of information, but I guess I just don't understand enough of it to figure out what to do and what not to do. 

I've had sound working before, but couldn't get quality microphone and sound out of Teamspeak both at the same time. I started from scratch after that, set up a dual boot system to test sound in Windows XP, which worked right away. I would really hate to have to go out and buy a version of Windows :( (current version is not registered)

Here's the output of aplay -l:
marco@marco-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
marco@marco-desktop:~$ 

It's an onboard soundcard on an Asus P5K SE Motherboard.

Here are some of the problems I'm experiencing:

- In System > Preferences > Sound with sound capture on ALSA, when I test sound I get: "gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing." When I set sound capture to 'test sound' and then test I get the beep.
- When I set the output plugin in Amarok to Alsa I get: "Xine was unable to initialize any audio drivers". I can play music using Autodetect or OSS as setting.
- When I boot the pc I do hear the sound when the loginname screen appears, but the sound that I used to get when the desktop appears is not there anymore.
- In World of Warcraft I used to have sound, that has gone for some reason. I wasn't able to get sound out of Wow and Amarok at the same time after I started from scratch. That did work before though. 

What have I tried: 

I installed the latest driver version from the Alsa project website (Alsa-driver-1.0.16). This version seems to give a mic boost option in the volume control that I need to be able to make myself heard in Teamspeak. However, since I have quite some trouble with sound I've tried uninstalling that version. Since I'm not sure how to completely uninstall those drivers though, I might have left some behind that is interfering with the drivers that I installed later through the next step described here.

From the Comprehensive sound problem solution guide I've tried reinstalling from a *fresh* kernel. This is pretty much where I am now. After that it says to go to the Alsamixer section. When I type Alsamixer in the terminal I get:
alsamixer: function snd_ctl_open failed for default: No such device
 
I reinstalled alsa-oss using synaptic package manager.

Well, hope someone has time to read through this and point me in the right direction. Thanks in advance.

---

### Post by mvvemden on 2008-06-17
Soooo.. Too much info? Not enough info? Noone have a clue what I could try? I could really use some advice...

---

### Post by FaizanKazi on 2008-06-17
When more experienced users like you have problems, noobs like me can't help but scratch their heads... i dont think you've actually come across someone who can help you yet.. hang in there :)

> **mvvemden said:**
> Soooo.. Too much info? Not enough info? Noone have a clue what I could try? I could really use some advice...

---

### Post by Pjotr123 on 2008-06-17
It could be this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 6 )

---

### Post by mvvemden on 2008-06-17
> **FaizanKazi said:**
> When more experienced users like you have problems, noobs like me can't help but scratch their heads... 
Hehe, you have no idea how much of a noob I am I guess. Just in case that wasn't clear: I am a very inexperienced Linux user :)

---

### Post by mvvemden on 2008-06-17
> **Pjotr123 said:**
> It could be this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 6 )
I'll check that out, though at first sight everything seems to point in a different direction. The website you're referring to seems to have to do with Ubuntu 8.04 specific trouble, and has little to do with the functioning of Alsa.

As far as my problem is concerned, it seems I can't get Alsa working. I get sound with OSS (in Amarok), but when I set either Amarok or System>Preferences>Sound to Alsa I get an error. Winecfg is also set to Alsa, I noticed, which could explain why sound doesn't work in Wow. I can't get sound through two different sources at the same time, I can't open Alsamixer....

What did I screw up when I tried to install Alsa 1.0.16 (and tried to remove it later)? How can I repair it by either going back to 1.0.14 or, even better, keeping 1.0.16?

---

### Post by Erlander on 2008-06-17
If you have installed any additional kernels they could be the problem.  I don't mean the standard kernels installed when you install Ubuntu or the automatic update ones.  If they are the only kernels on your system then I'm barking up the wrong tree!!

Sound drivers for sound cards are normally in the kernel except some of the additional kernels don't have them.

Rob

---

### Post by mvvemden on 2008-06-17
> **Erlander said:**
> If you have installed any additional kernels they could be the problem.  I don't mean the standard kernels installed when you install Ubuntu or the automatic update ones.  If they are the only kernels on your system then I'm barking up the wrong tree!!

Sound drivers for sound cards are normally in the kernel except some of the additional kernels don't have them.

Rob
Ok. I MAY have installed additional kernels, but I really don't have a clue. I guess I'll have to start by doing some studying on what a kernel exactly is :confused: Perhaps I installed another kernel by downloading and trying to install the drivers for my specific soundcard from the website of the motherboard manufacturer? 

The linux ones from this: [http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5K%20SE](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5K%20SE)

I tried to install those drivers, but never really got sound working with that. So, I went on to trying the alsa 1.0.16 driver, but I doubt if I removed these drivers the right way.  Is there an easy way to find out if this might be the problem?

---

