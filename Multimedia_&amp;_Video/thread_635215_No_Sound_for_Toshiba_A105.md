---
title: "No Sound for Toshiba A105"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by daraikenu on 2007-12-08
Hi, I'm new to Linux. About a week ago, I installed Ubuntu (Gutsy Gibbon) on my Toshiba A105-2101, and so far I've really been loving it. Only main issue I've been having is that I'm getting no sound from it none whatsoever from my speakers. I mean, Ubuntu recognized my sound card, I believe I've gotten everything unmuted, and I followed some of the advice from the forums here for my laptop (But it doesn't help most of the help is for Feisty, and not Gutsy, so problems still ensue.)

I'm at my rope's end with problem, I'd like to put my music back on my computer. Help!

P.S.>Here's a lspci of my system.

> daraikenu@rpanda:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


---

### Post by Yellow Pasque on 2007-12-08
See the link in my sig.

---

### Post by daraikenu on 2007-12-08
> **Temüjin said:**
> See the link in my sig.

I'll give it a try.

EDIT: Still no dice. Gah, this is frustrating!

---

### Post by ferdostar on 2007-12-08
Can you post the output of ```
sudo lshw -C sound
```

---

### Post by daraikenu on 2007-12-08
> **ferdostar said:**
> Can you post the output of ```
sudo lshw -C sound
```

Sure:

```
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

daraikenu@rpanda:~$ 

```

Don't know if I did it right, though.

---

### Post by ferdostar on 2007-12-08
Could you pleas check in terminalif everything is ok with the alsamixer? ```
alsamixer
```

---

### Post by daraikenu on 2007-12-08
> **ferdostar said:**
> Could you pleas check in terminalif everything is ok with the alsamixer? ```
alsamixer
```

Yeah.

I got a .png screenshot of alsamixer. It looks okay, but the Master doesn't seem to have a bar to adjust the volume. Weird.

---

### Post by ferdostar on 2007-12-08
If you try to move the bar up? :)

---

### Post by daraikenu on 2007-12-08
> **ferdostar said:**
> If you try to move the bar up? :)

No, like the Master volume doesn't seem to have a bar for it. The PCM and Microphone have  bars, though.

---

### Post by ferdostar on 2007-12-08
If you move move the up/down key at the keyboard there is no reply? :-k

---

### Post by daraikenu on 2007-12-08
> **ferdostar said:**
> If you move move the up/down key at the keyboard there is no reply? :-k

No, not for the master volume there isn't a replyl

---

### Post by ferdostar on 2007-12-08
Can you see if you right-click on the volume applet (the little speaker on the top panel) and choose "Preferences" is there the Master and if it is highlithed? If "yes" try to click on "Analog front" and close it. If not work with this go back to Master and click on it and close, and post

---

### Post by daraikenu on 2007-12-08
Yeah, I checked. Under my OSS Mixer, it has the Volume hightlighted.

---

### Post by ferdostar on 2007-12-08
I supose in System > Administration > Sound, The default Mixer Tracks is Alsa mixer? Other thing, if you test the different composits, is everything fine?

---

### Post by daraikenu on 2007-12-08
> **ferdostar said:**
> I supose in System > Administration > Sound, The default Mixer Tracks is Alsa mixer? Other thing, if you test the different composits, is everything fine?

When I get down to Audio conferencing, It has problems testing the sound.

From sound playback using ESD:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not establish connection to sound server
Anything I use with ESD...fails.

Also found this out when I was testing my sound capture--

From sound capture using everything (OSS, ALSA, ALC861 Analog, Etc.):
> gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not establish connection to sound server

---

### Post by ferdostar on 2007-12-08
```
asoundconf list
```
To see if you card is supported

---

### Post by daraikenu on 2007-12-08
> **ferdostar said:**
> ```
asoundconf list
```
To see if you card is supported
```

daraikenu@rpanda:~$ asoundconf list
Names of available sound cards:
SB

```

I guess that's a yes. :S

---

### Post by ferdostar on 2007-12-08
```
sudo apt-get install linux-backports-modules-generic
```

---

### Post by Yellow Pasque on 2007-12-08
> **daraikenu said:**
> I'll give it a try.

EDIT: Still no dice. Gah, this is frustrating!

Can you be a bit more specific? What exactly went wrong?

---

### Post by daraikenu on 2007-12-08
> **ferdostar said:**
> ```
sudo apt-get install linux-backports-modules-generic
```

```
E: Couldn't find package linux-backports-modules-generic

```

---

### Post by daraikenu on 2007-12-08
> **Temüjin said:**
> Can you be a bit more specific? What exactly went wrong?

Well, nothing went wrong. Basically, all of those things are already updated on my system, my guess is, and it's just no sound's coming out at all.

---

### Post by ferdostar on 2007-12-08
> **daraikenu said:**
> ```
E: Couldn't find package linux-backports-modules-generic

``` :confused:
Take a look of this, seems that the sound card is the same like yours [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=501422](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=501422)
Otherwise you can take a look of others similar posts to see if someone else had the same problem as you:
[http://ubuntuforums.org/showthread.php?t=616846](http://ubuntuforums.org/showthread.php?t=616846)
[http://ubuntuforums.org/showthread.php?t=604084](http://ubuntuforums.org/showthread.php?t=604084)
[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.p...light=no+sound](http://ubuntuforums.org/showthread.p...light=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php...21&postcount=5](http://ubuntuforums.org/showpost.php...21&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.p...olutions+guide](http://ubuntuforums.org/showthread.p...olutions+guide)
[https://help.ubuntu.com/community/De...gSoundProblems](https://help.ubuntu.com/community/De...gSoundProblems)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/200...work-in-gutsy/](http://linuxtechie.wordpress.com/200...work-in-gutsy/)
[http://linuxtechie.wordpress.com/200...tsy/#comment-6](http://linuxtechie.wordpress.com/200...tsy/#comment-6)
[https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469](https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469)

On the other hand you can try to
1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try to use a hammer :D

Hoppe it will help you!

---

### Post by daraikenu on 2007-12-08
> **ferdostar said:**
> :confused:
Take a look of this, seems that the sound card is the same like yours [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=501422](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=501422)
Otherwise you can take a look of others similar posts to see if someone else had the same problem as you:
[http://ubuntuforums.org/showthread.php?t=616846](http://ubuntuforums.org/showthread.php?t=616846)
[http://ubuntuforums.org/showthread.php?t=604084](http://ubuntuforums.org/showthread.php?t=604084)
[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.p...light=no+sound](http://ubuntuforums.org/showthread.p...light=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php...21&postcount=5](http://ubuntuforums.org/showpost.php...21&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.p...olutions+guide](http://ubuntuforums.org/showthread.p...olutions+guide)
[https://help.ubuntu.com/community/De...gSoundProblems](https://help.ubuntu.com/community/De...gSoundProblems)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/200...work-in-gutsy/](http://linuxtechie.wordpress.com/200...work-in-gutsy/)
[http://linuxtechie.wordpress.com/200...tsy/#comment-6](http://linuxtechie.wordpress.com/200...tsy/#comment-6)
[https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469](https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469)

On the other hand you can try to
1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try to use a hammer :D

Hoppe it will help you!

Thanks very much for your help. I appreciate you stood on for about 2 hours trying to help me. :D

Also I added you to my buddy list. :)

---

### Post by ferdostar on 2007-12-08
> **daraikenu said:**
> Thanks very much for your help. I appreciate you stood on for about 2 hours trying to help me. :D

Also I added you to my buddy list. :)

Nothing else to do, cause I have to do my homeworks [-(

---

### Post by quantumnight on 2008-02-17
I just fixed this for someone yesterday. The answer I got from google was to open /etc/modprobe.d/alsa-base and at the end of the file in the options area add this line:

options snd-HDA-Intel auto

and then reboot. At least I think that's what it was.
Good luck.

---

### Post by ferdostar on 2008-02-22
> **quantumnight said:**
> I just fixed this for someone yesterday. The answer I got from google was to open /etc/modprobe.d/alsa-base and at the end of the file in the options area add this line:

options snd-HDA-Intel auto

and then reboot. At least I think that's what it was.
Good luck.

Happy that you fix it :D just mark the tread as solved and have fun! Cheers!

---

