---
title: "reset sound setting?"
date: 2009-06-08
forum: Multimedia Software
---

### Post by Stoneface on 2009-06-08
I could not get Skype to work and played around with the sound settings. Now Skype works except for the dialing as other phones register everything double (2x5 instead of one single 5). Now my Acer Aspire no longer has a working sound button?! Now I can only change volume using the master control. Volume increases in programs no longer work. How can I reset or undo all this? Have had two rather bad days with Ubuntu. Desktop crashed and indexing ate up all memory. I fixed those two issues. But sound... I want Skype to work and the general volume control buttons to work.
So how can I reset sound settings?

---

### Post by Stoneface on 2009-06-09
Nobody here who has had the same problems? Volume can only be changed by using master volume on my Acer Aspore 4520G laptop now. Volume control via all programs is not working. Is there a way to reset alsamixer to settings just after installation of alsamixer or Ubuntu? Or should I uninstall and reinstall alsmixer?

---

### Post by Stoneface on 2009-06-11
When I use my Acer Aspire volume button the capture colume is increased, not the general volume. How can I adjust its function so it increases the general volume or master control volume again?

---

### Post by Stoneface on 2009-06-19
Well I found [http://ubuntuforums.org/showthread.php?t=1130384&highlight=reinstall+alsa](http://ubuntuforums.org/showthread.php?t=1130384&highlight=reinstall+alsa) and there I found some useful information. I got back control over the master volume. I did this by going to System> Preferences > Sound and there I used my preferred volume wheel which Ubuntu then recognizes as master volume button. Now I need to work on the issues with Skype.

---

### Post by Stoneface on 2009-06-19
I played around with mt newly installed Pulse Audio Applet. I think I have got Skype working properly again. Will call my sister in an hour to double check.

---

### Post by Stoneface on 2009-06-19
Well Skype is still messed up. I can hear people talk, but my voice is not transfered at all.

---

### Post by kaefert66014235 on 2009-06-24
Im using Ubuntu 9.04 and my Skype doesn't work at all.. I mean I can use it to text, but no sound out and no sound in. I tried all settings in the list skype offered me for the "Sound Out"-box:
-) Default device (default)
-) HDA Intel (hw:Intel,0)
-) HDA Intel (plughw:Intel,0)
-) HDA Intel (hw:Intel,1)
-) HDA Intel (plughw:Intel,1)
-) hdmi
-) headset
-) pulse

but none of them got skype making any sound.

---

### Post by mbn18 on 2009-06-24
I got the same thing.

My motherboard is Asus P5B Deluxe ( HDA Intel - Azalia ) and I am using Jaunty 9.04
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

When I use Skype, I can hear people but they cant hear me. I tried messing with gnome-volume-control but couldn't fix it. ( Also tried gnome recorder with no success )

Beside that, Pulse settings sound like crap, is it digital at all?

Any idea is welcomed.

---

### Post by mbn18 on 2009-06-24
To solve the sound problem I did:

1. find your model:
Run:
cat /proc/asound/card0/codec#* | grep Codec
in my case the model was AD1988B

2. Search the file for the model name:
less /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
In my case the result was: 6stack

3. Edit the file:
sudo vim /etc/modprobe.d/alsa-base.conf

4. Added the following line:
options snd-hda-intel model=6stack

5. Reboot

6. play with the options under System -> Preferences -> Sound

---

### Post by Stoneface on 2009-06-30
```
/proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC268
Codec: LSI ID 1040

```

So my soundcard is a Realtek ALC268. You're second piece of information I don't get yet. Reading it again as we speak.
I need to go through: ALSA-Configuration.txt.gz with less to find the model I have? Well I can't find ALC268 there...

Here is some more information:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
and lspci -v  | less
```
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
        Subsystem: Acer Incorporated [ALI] Device 0127
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at f2480000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```

As far as I can see I should add ```
options snd-hda-intel model=ALC268
``` or ```
options snd-hda-intel model=6stack
```to the ALSA configuration file to make it work.. This is all really high tech stuff so I don't know yet. I hope this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326") will be resolved soon.

---

### Post by Stoneface on 2009-06-30
```
options snd-hda-intel model=6stack
``` worked!!! And then I changed sound in to Hw:NVdia:0 in Skype which is analogue I believe. I will try a few others later. I am a happy camper now!

---

### Post by dedlycow on 2009-06-30
Good luck with your sound probs with skype
 I have acer aspire 5536G.
I have been trying for weeks to get the mic  working on Skype and the sound volume to work properly with no luck.
 I will watch your progress with much interest.

---

