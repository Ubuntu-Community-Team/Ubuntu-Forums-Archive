---
title: "No sound on SiS SI7012"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by ddado on 2008-03-20
Hi!

I am running an Ubuntu 7.10 on Asus a9t (a laptop) with a SiS SI7012 soundcard. Pretty much everything works fine apart from the sound, which isn't working at all. I have tried several solutions mentioned here, reinstalled alsa drivers, reconfigured them, set the alsa-mixer etc.... nothing worked. Does anybody have any other solutions? Or, have I done something wrong? This might be possible, as I am pretty new to Linux, so please, if you have any idea what I might do, I would be very grateful if you posted them - just be precise about what i should do. 

Thanx in advance!

---

### Post by wolfen69 on 2008-03-20
this page [http://ubuntuforums.org/showthread.php?t=384945](http://ubuntuforums.org/showthread.php?t=384945)  *seems* to have an answer.

---

### Post by ddado on 2008-03-20
Tried that....

I did what hants told:

> a)
I) open console
II) su to root
III) run alsamixer
go right with the arrow keys and
1) <Master_S> (Master Surround):
unmute (press m), increase volume (up-arrow key)
2) <PCM>:
unmute (press m), increase volume (up-arrow key)
3) <Channel> (Channel Mode):
set to 4 or 6 (up-arrow key)
4)<Exchange> (Exchange Front/Surround)
unmute (press m)
5)exit
press Esc
But it didn't help.

I'd like to try Francois Rigault's suggestionin the same thread:
> The SiS7012 sound card (the one on the A9T laptop) will work by removing Alsa modules and enabling the corresponding DSP driver (i810_audio). You need to configure XMMS to use the DSP (in XMMS options).
But I don't know how to do it.... Help anybody???

---

### Post by Yellow Pasque on 2008-03-21
Before you give up, make sure to try OSS4 (see link in my sig).

---

### Post by ddado on 2008-03-21
> **Temüjin said:**
> Before you give up, make sure to try OSS4 (see link in my sig).
Okay, I tried that, followed it step-by-step and even got some clicking in my speakers when I set up the sound in the failsafe terminal, but that was it. I made a launcher with the command ossxmix -d<1>, launched it, and nothing worked - i.e. no sound.

ossdetect -v brought me this:

> neverone@wasteland:~$ sudo ossdetect -v
Detected SiS 7012 
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture

and ossinfo this:

> neverone@wasteland:~$ sudo ossinfo 
Version info: OSS 4.0 (b1014/200802280648) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 (wasteland)

Number of audio devices:        1
Number of audio engines:        10
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: ich0 SiS 7012 interrupts=14388 (14388)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: ICH AC97 Mixer (AD1888) (Mixer 0 of device object 1)

Audio devices
SiS 7012                          /dev/oss/ich0/pcm0  (device index 0)

Plus, now, after reboot, I get the dialogue: "The pannel encountered a problem while loading  "OAFIID:Deskbar_Applet". Do you want to delete the applet from your configuration?" Whats wrong with that???

---

### Post by Yellow Pasque on 2008-03-22
I'm sorry that OSS4 didn't work for you. If you'd like to uninstall:
```
sudo soundoff
sudo dpkg -r oss-linux
```

---

### Post by ddado on 2008-03-22
Hmmm.... so is that it??? Am I ever gonna have the chance of playing the sound on my machine??? Anybody els have any ideas? Please help!!!

---

### Post by ddado on 2008-03-23
Anybody??? Puh-leeeeaaaasee.... :)

---

