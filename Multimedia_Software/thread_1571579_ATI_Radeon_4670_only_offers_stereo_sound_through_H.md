---
title: "ATI Radeon 4670 only offers stereo sound through HDMI, missing 5.1 or 7.1"
date: 2010-09-09
forum: Multimedia Software
---

### Post by notbitmonk on 2010-09-09
I bought this Radeon 4670 ([http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-4000/hd-4770/Pages/ati-radeon-hd-4770-specifications.aspxref=oss_product](http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-4000/hd-4770/Pages/ati-radeon-hd-4770-specifications.aspxref=oss_product)) to improve my video. Although the description on ATI-AMD webpage ([http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-4000/hd-4600/Pages/ati-radeon-hd-4600-specifications.aspx](http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-4000/hd-4600/Pages/ati-radeon-hd-4600-specifications.aspx)) specifies that this card can output up to 7.1 audio through HDMI, Sound Controls only shows the stereo and off option.  ATI Catalyst does not have any controls for audio. Is there a way to get 5.1 audio enabled? Using 10.04.

---

### Post by hfdragon on 2010-10-28
Hi !

I have the same problem with another ATI card (ATI Mobility Radeon HD 4670)  and ubuntu 10.10... have you found a solution about this ?

---

### Post by navait on 2010-11-11
Similar issues with a ATI Radeon 4350 in my HTPC, if anybody has any ideas.

---

### Post by hfdragon on 2010-11-12
Hi !

I finally managed to get 5.1 sound through HDMI.

You need to use and configure vlc to play your files.

To configure vlc : 

Tools -> Preferences -> Audio

In output module, choose Alsa, and then just below choose your ATI HDMI card.

You might need to choose "yes" for dolby surround.

Close and restart vlc.... it should work :)

---

### Post by navait on 2010-11-12
Haha wow, well done. I could hug you. I was *this* close to crawling back to Windows just for the surround sound. Seriously, I almost done prepping the flash drive.

Now I just need to get that to work in XBMC...

Thanks for the help!

---

### Post by notbitmonk on 2010-11-19
Still no luck. Did a fresh reinstall and skipped the hardware drivers but that did not function. hfdragon thanks for your tip however, I am trying to have it work from any application in Ubuntu because I try to keep my system as lean as possible (although I tinker with several pieces of software, I usually end up doing a clean install).

---

### Post by hfdragon on 2010-11-19
As far as I know, every application in Ubuntu can't send sound via hdmi.

It is a (known) limitation of pulseaudio; so if you absolutely need that, maybe you should remove pulseaudio and use only alsa for sound... but I don't know what other problem it could cause to your installation and if it will work at all !!!

---

### Post by notbitmonk on 2010-12-01
I never checked if there was audio output. I only concentrated on the 5.1 or 7.1 output (wanted to connect to my home theater) option in sound controls.

---

### Post by Noread on 2011-03-15
I don't know if you're still looking to solve this problem. But I've recently had the same problem and found a working solution for xbmc.

I uninstalled pulseaudio and then used the following settings in xbmc, you need 10.1 to make several of the options available:


Audio output: HDMI
Speaker configuration: 5.1
Dolby Digital (AC#) capable receiver: check
DTS capable receiver: check (only use these 2 if you indeed have a receiver capable of these codecs.
Audio output device: hdmi
Audio passthrough device: Custom
Custom passthrough device: hdmi:CARD=Generic,DEV=0

The right passthrough device can be different in your setup, you can find it using ```
aplay -L
```

Do note, the menu sounds and other sounds outside xbmc will most likely no longer work out of the box. But who needs those on a htpc?

---

### Post by notbitmonk on 2011-12-17
To have audio output you need ATI's closed source drivers. Still output to stereo though.

---

### Post by notbitmonk on 2012-01-12
Just found this page [http://www.avsforum.com/avs-vb/showthread.php?t=1029603](http://www.avsforum.com/avs-vb/showthread.php?t=1029603) that pointed to Realtek website at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2). In there is a file for audio drivers. I just downloaded it. I will let you know how it goes.

---

### Post by notbitmonk on 2012-05-13
It did not work. :(

---

### Post by BicyclerBoy on 2012-05-13
The HDA-intel HDMI audio codec support is provided by alsa, the AMD video driver is required to expose the devices.
The open source driver does support HDMI audio for a couple of models..

Install/run pavucontrol

Are you now using 12.04 ? 
And the AMD proprietary fglx driver ?

You are recommended to alsa 1.0.25 or 1.0.24 at least..

---

