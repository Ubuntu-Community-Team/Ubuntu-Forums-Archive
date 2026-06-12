---
title: "Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250"
date: 2009-12-07
forum: Multimedia Software
---

### Post by uhappo on 2009-12-07
lspci
```

05:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04)
```

How do I make it work?

---

### Post by erixoltan on 2010-01-03
I have the same card.  I also need to understand how to make it work.  Any ideas?

---

### Post by uhappo on 2010-01-04
Apparently it's so new card that drivers are missing, but I'm still hunting the web for more info

---

### Post by HappyFeet on 2010-01-04
If it is a relatively new card, you will have a very hard time getting it going (if at all). It ususally takes at least 2 years for drivers to appear for tv tuners. Some never get supported properly. If you don't feel like waiting, get a HVR-1600. That's probably the best tv tuner that is supported.

---

### Post by uhappo on 2010-01-04
> **HappyFeet said:**
> If it is a relatively new card, you will have a very hard time getting it going (if at all). It ususally takes at least 2 years for drivers to appear for tv tuners. Some never get supported properly. If you don't feel like waiting, get a HVR-1600. That's probably the best tv tuner that is supported.

I don't have the actual need for it, it came bundled in my HP-desktop PC so I'm just checking and looking if it would work. Always "fun" to solve these things...

---

### Post by uhappo on 2010-01-21
Bumpty bump?

---

### Post by sports.car.guy on 2010-01-21
One thing some Hauppauge cards have issue with is being an OEM version, and it won't work. Not all of their "white box" OEM cards are like that too. You can have an OEM card that goes to say HP like you. it gets one set of numbers, and one for general OEM's get's another. If you look at NewEgg's site they will sometimes have 3 or 4 versions of the same card between the retail and OEM versions.

I am not sure if yours suffers the OEM problem. I know that an OEM version of the 1800 has some major issues and won't work right if at all. I know with MythTV not at all.

If it is a supported one here is the page at linuxtv.org

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250)

I hope this is of help you you.

---

### Post by carlexpc on 2010-01-21
If you know how to compile a customized kernel, please try to do it. The device you are talking about is supported in kernel 2.6.32.x.

Location:
 -> Device Drivers
  -> Multimedia support (MEDIA_SUPPORT [=y])
    -> Video capture adapters (VIDEO_CAPTURE_DRIVERS [=y])
      -> V4L USB devices (V4L_USB_DRIVERS [=Y])

---

### Post by uhappo on 2010-01-21
> **carlexpc said:**
> If you know how to compile a customized kernel, please try to do it. The device you are talking about is supported in kernel 2.6.32.x.

Location:
 -> Device Drivers
  -> Multimedia support (MEDIA_SUPPORT [=y])
    -> Video capture adapters (VIDEO_CAPTURE_DRIVERS [=y])
      -> V4L USB devices (V4L_USB_DRIVERS [=Y])

WHAAAAT!?

I guess my card is sort of an OEM-version, so this is lottery for sure...

I don't know how to compile a customized kernel, never done that. Hmm, V4L USB? This is pci-e card, I'm sure of that. But I just really don't know about compiling, so enlighten me a bit, would you?

But this is amazing if my card is supported in the near future, no windows for me! (Well, for audio/studio work it's a must...)

Yeah!

---

### Post by uhappo on 2010-01-31
It's called AVerMedia H789. Check this out:
[HP Support]("http://h30434.www3.hp.com/t5/Hardware/AVerMedia-H789-PCI-E-Hybrid-DVB-T-TV-tuner/m-p/81781")

---

### Post by uhappo on 2010-02-25
Bumpty bump?

---

### Post by erixoltan on 2010-02-25
My card still doesn't work, although I'm certainly not sure I'm doing the right thing.

---

### Post by uhappo on 2010-02-25
> **erixoltan said:**
> My card still doesn't work, although I'm certainly not sure I'm doing the right thing.

So what exactly are you doing, or trying to do to it?

---

### Post by erixoltan on 2010-02-26
At this point, I'm just waiting.  I've read that the basic card is supported by Linux, but this proprietary variant doesn't work.  I get updates applied to my system every night, so from time to time I try the card to see if it works.  

I don't personally know of anything better to do.

---

### Post by uhappo on 2010-03-07
I bet you have to wait for loooooooong time...

There's no driver for it at the moment IIRC, so we have to wait for something special to happen. I know it's possible, let's be patient!

---

### Post by joachimp on 2010-10-28
I have a 02:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 0f) 

Using cx23885 module it works kinda, though sound is often broken, and jerky when viewing highdef content. Note, I'm using a ppa kernel from
 
[http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu/](http://ppa.launchpad.net/kernel-ppa/pre-proposed/ubuntu/)
2.6.36-020636rc8-generic
card was nonfunctional using the ubuntu shipped 2.6.35 kernels. Card previously worked great in Debian 2.6.32 kernels...

---

### Post by technoboi on 2010-11-08
> **erixoltan said:**
> My card still doesn't work, although I'm certainly not sure I'm doing the right thing.

In the case of my Satellite tuner, the firmware already installed was duff.
What you need to do is find & download the appropriate firmware. In the directory where the firmware is stored (/var/lib) you may find some firmware with a similar name but a different build (or version number).
What you need to do is disable that firmware by changing its name  to something else (rather than deleting it). 
Then create a symbolic link with the generic name of the firmware pointing to your new, target, firmware.
Here is an example:
Syntax: ln -s  newfirmwareTARGET.fw genericName.fw
e.g     ln -s  dvb-fe-cx24116-1.26.90.0.fw dvb-fe-cx24116.fw

Also, when you set up MythTV backend you'll need to make it connect to the LNB if it is a satellite tuner. Do that via the capture cards settings. It's a menu within a menu - can't remember which one - the one involved with LNB switching.

---

### Post by erixoltan on 2010-11-18
Well, I don't understand how to use the Conexant cx23885 module.  I don't want to recompile my kernel because I don't want to get out of synch or have it stop working in future updates.  I don't have firmware and am not sure exactly how to get that.  

I am not able to configure it to work in any of my video applications.  So I am still in waiting mode.  It works in Windows and I can use a dual boot if I want to record an important show in high def.  

Hopefully it will work soon, because it's one of the last things keeping me tied to a dual boot system.  

Thanks,
Erik

---

