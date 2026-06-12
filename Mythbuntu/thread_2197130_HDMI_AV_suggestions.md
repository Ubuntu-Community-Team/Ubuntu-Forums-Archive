---
title: "HDMI A/V suggestions"
date: 2014-01-02
forum: Mythbuntu
---

### Post by bah1976 on 2014-01-02
Hi -
I'm not new to mythtv, but I am new to some of the newer hardware.  I currently have a DVI to HDMI adapter to get video to my receiver, and a miniplug to Red/white RCA providing stereo audio to the receiver.  The video is obviously switched through to the TV, and the audio is controlled by the receiver.
I'm going to be building a new myth FE, and I would love to be able to have one HDMI cable providing Audio & Video to the receiver to get the surround sound I'm recording off ATSC broadcast TV in chicago (HDHomeRun).  I've done some reading, and it seems that there is a mixed bag of problems with getting this to work.  I'm hesitant to buy anything unless I know it will do this.  So, I'm looking for specific hardware suggestions - intel/amd, CPU, motherboard, chipset, onboard/PCIe video, model numbers, newegg link, etc, as much detail as you want to provide - for a configuration that works the way it's supposed to.  This FE will also be a plex media server with some transcoding responsibilities, so I was initially looking at Intel.

Everything I've ever bought for my environment has been AMD & Nvidia.  Plex seems to prefer Intel, but functional Myth is more important than rocket fast transcoding so perhaps it's better to stay with AMD?

I appreciate any thoughts or direction to where this sort of suggestions may already exist.  I browsed the functional hardware thread a bit, but didn't see anything jump out at me as being the information I'm looking for.

Thanks!

---

### Post by newlinux on 2014-01-08
Is the mixed bag of problems you are referring to getting audio and video HDMI? If so you primarily want to focus on the video card. I personally have had good success doing that with Intel and Nvidia cards. There are a large universe of cards/GPUs out there and I haven't bought anything in a couple of years to know for sure about the new stuff. Perhaps you could pick out a couple of cards you are interested in and then google or ask here what people's experiences have been. Things have gotten a lot better with Audio and video via HDMI over the past few years. The first time I did it it required me to compile a new version of ALSA and set some modprobe options. The last few times it's has been pretty much plug and play (just set the right audio output in the appropriate sound settings - Myth, XBMC, OS Soundmixer). You'll get the most help and possible the the most likely to work solution with Nvidia GPUs, but AMD and Intel have come a long way and can work just as well.  

You can get an idea of my hardware from my signature, but most of my stuff is older...

---

### Post by SeijiSensei on 2014-01-08
You'll also need a receiver with HDMI ports, of course.  I can get audio and video out of my NVIDIA card, but my receiver is so old that it has no HDMI ports.  So I'm still using analog audio to the RCA jacks (which does carry the Prologic signal for surround) and the HDMI cable for video.  Occasionally I'll just crank up the audio on the TV set rather than muck with the receiver.  That works, too, but the quality is obviously inferior compared to a real audio system.

---

### Post by bah1976 on 2014-01-21
Ok - so I've gotten a video card with a Nvidia GT630 core, specifically a zotac GT630 zone edition.

Video works fine, but no audio.  It at least partially sees it:
```

bruce@mythsecond:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfea7c000 irq 19
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfebff800 irq 20
 2 [SAA7134_1      ]: SAA7134 - SAA7134
                      saa7133[1] at 0xfebff000 irq 21

```

aplay -l is empty.
alsamixer sees the card as HDA NVidia, and Chip as Nvidia ID 51.

But in the middle where volume would be, it says This sound device does not have any controls.  I kind of expect that, since it's a digital out without a volume control, but I'm not sure why I don't see it in aplay...
In frontend setup, all i see is alsa:default, alsa:pulse, pluseaudio:default, and Null.  (I've disabled the onboard jacks in BIOS to keep them from confusing things...)

Any thoughts?
Running 12.04.2, 
```
bruce@mythsecond:~$ uname -a
Linux mythsecond 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by SeijiSensei on 2014-01-21
Did you install the proprietary driver from NVIDIA?  I'm pretty sure you need that to get the audio to work.  Run "sudo apt-get install nvidia-current", reboot and see if that helps.

---

### Post by bah1976 on 2014-01-22
I did the nvidia-current, which gave me a 304 version, and if I recall my afternoon correctly, it wouldn't work.  So I downloaded directly from nvidia and got a version 331, which is working fine on the video side, just not audio.

---

### Post by EternalStudent on 2014-01-24
So I have the ASUS Nvidia 2gb GT 630.  Slightly different as it has newer technology than other GT 630s... so my default version is a bit different if I recall.  Took me some time getting stuff figured out too.  You should be able to rule out the driver pretty quickly though:

Run this first to determine details about your card:
```
aplay -l
```

your output should have a list of cards.  The NVidia card should be card 0 (from your previous post) then there may be more than one device (something like "... device 3: HDMI ...")

For each device, run this command:
```
speaker-test -Dhw:0,3 -c2
```
Replace the 0 if your card is not card 0 and the 3 if the device is something different.

This should play static through your TV Speakers one at a time over HDMI.  Ctrl-C to exit.


This link helped me a lot:[http://ubuntuforums.org/showthread.php?t=1967755](http://ubuntuforums.org/showthread.php?t=1967755)

---

### Post by bah1976 on 2014-01-27
That's my problem - aplay -l doesn't show anything about Nvidia.  All I see there is my onboard audio.  At one point I had disabled the onboard audio, and then aplay -l was just blank.  

Any thoughts on how to get the card to show in aplay?

lspci sees it:
```

02:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 630 Rev. 2] (rev a1)
02:00.1 Audio device: NVIDIA Corporation Device 0e0f (rev a1)

```

and

```

$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfcef4000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfea7c000 irq 19

```
but that's as far as it goes...

---

### Post by bah1976 on 2014-01-27
I'm getting somewhere..  I found this:
[http://jaysdesktop.blogspot.com/2011/10/enabling-hdmi-audio-out-in-ubuntu-1004.html](http://jaysdesktop.blogspot.com/2011/10/enabling-hdmi-audio-out-in-ubuntu-1004.html)
and that got me to update alsa, now aplay -l shows my card:
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

This was my primary problem, getting the card to show up.  I'll post further if I need it.  Thanks folks..

---

