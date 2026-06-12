---
title: "ATI R6XX HDMI audio not working"
date: 2012-05-01
forum: Multimedia Software
---

### Post by arrow.69 on 2012-05-01
Hey,

So I'm running Precise Pangolin 12.04 64-bit, everything's looking good but I can't output audio through the HDMI port.  This works in Windows, so I assume it's a driver issue.  The HDMI device itself isn't visible in ubuntu's Sound Settings, but I can see the device in alsamixer.  I can also see it if I run aplay -l, lspci, or lsmod.  

However when I do go to the device's alsamixer configurations, all I can see is one box marked S/PDIF with value [00].  I can mute and unmute it, but I can't change the value.  There are no other controls for the device. 

I've also tried to output straight to the alsa device from vlc, or with aplay, but that also hasn't worked.

It's a strange problem because the driver seems to recognize the output device and the proper modules are loaded, but I can't seem to unmute the device and get the audio to work.

---

### Post by arrow.69 on 2012-05-01
Solved it.  Turns out the solution is quite simple.  You need to set a kernel flag for:

radeon.audio=1

For anyone who's encountered the same problem, you can do this by pressing 'e' in GRUB on your ubuntu boot option, and adding the above line somewhere.

Otherwise you can edit the entry in /boot/grub/grub.cfg  although I would recommend reading up on grub before you break something.

---

### Post by sikemo on 2012-11-04
Is this as simple as just adding that line anywhere in grub.cfg or is there more to it?

---

### Post by Yellow Pasque on 2012-11-04
sikemo, I put the instructions in youre thread, but I'll echo them here in case someone comes across this in a search:

For open-source HDMI audio, you'll need to add radeon.audio=1 (inside the quotes next to "quiet splash") to the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub and then run:
```
sudo update-grub
```

> Otherwise you can edit the entry in /boot/grub/grub.cfg...
DO NOT edit that file directly (as it warns you).

---

### Post by madned on 2012-11-30
Had the same problem using Ubuntu with my AMD A6-3500 APU and Asrock A55M motherboard, HDMI works but no sound.

confirmed that this fix works for me, thanks!!!

---

### Post by jskandhari on 2013-03-10
Someone should change the status of this thread to RESOLVED. ( #ADMINS PLEASE NOTE )

I would like to confirm this as working.

**Goto Launcher > Terminal**

```
SUDO NAUTILUS
```

Navigate yourself to /boot/grub/grub.cfg right click edit in Texteditor ...

Find your usual boot option usually the first entry in grub

when you find something like insert the line radeon.audio=1 as shown in bold. ( PS don't copy the full code )
```
fi
	linux	/boot/vmlinuz-3.5.0-25-generic root=UUID=xxxxxxxxxxxxxxxxxxxxx ro   quiet splash $vt_handoff [B]radeon.audio=1
[/B]	initrd	/boot/initrd.img-3.5.0-25-generic
```

f unsure use the at boot time method mentioned above....

---

### Post by webdesigncompanyla on 2013-03-29
> **jskandhari said:**
> Someone should change the status of this thread to RESOLVED. ( #ADMINS PLEASE NOTE )

I would like to confirm this as working.

**Goto Launcher > Terminal**

```
SUDO NAUTILUS
```

Navigate yourself to /boot/grub/grub.cfg right click edit in Texteditor ...

Find your usual boot option usually the first entry in grub

when you find something like insert the line radeon.audio=1 as shown in bold. ( PS don't copy the full code )
```
fi
    linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=xxxxxxxxxxxxxxxxxxxxx ro   quiet splash $vt_handoff [B]radeon.audio=1
[/B]    initrd    /boot/initrd.img-3.5.0-25-generic
```

f unsure use the at boot time method mentioned above....

there are two sets of code that are similar to your code snippet in grub.cfg, which line(s) do you edit?  just one of them or both?

---

### Post by Yellow Pasque on 2013-03-29
> **webdesigncompanyla said:**
> there are two sets of code that are similar to your code snippet in grub.cfg, which line(s) do you edit?  just one of them or both?

[http://ubuntuforums.org/showthread.php?t=1970699&p=12337464#post12337464](http://ubuntuforums.org/showthread.php?t=1970699&p=12337464#post12337464)

---

### Post by webdesigncompanyla on 2013-03-29
> **Temüjin said:**
> [http://ubuntuforums.org/showthread.php?t=1970699&p=12337464#post12337464](http://ubuntuforums.org/showthread.php?t=1970699&p=12337464#post12337464)

that didn't answer the question, try reading

---

### Post by Yellow Pasque on 2013-03-29
> **webdesigncompanyla said:**
> that didn't answer the question, try reading

Yes, it did. It tells you not to edit grub.cfg at all (use /etc/default/grub as directed instead). Sorry, but I can't make it any clearer...

---

### Post by webdesigncompanyla on 2013-03-30
> **Temüjin said:**
> Yes, it did. It tells you not to edit grub.cfg at all (use /etc/default/grub as directed instead). Sorry, but I can't make it any clearer...

both ways work perfectly and both are listed as solutions in this thread, but the editing grub.cfg method is unclear, editing grub too is also unclear and without a line # to edit and a code example, both fixes are poor examples of how to reproduce or follow, tsk tsk

i don't know how to be more clear that you are vague and incomplete in your explanations.

---

### Post by webdesigncompanyla on 2013-03-30
and why can't ubuntu itself make this simple update for people who have this hardware????

---

### Post by Yellow Pasque on 2013-03-31
> **webdesigncompanyla said:**
> both ways work perfectly

One involves editing a file that explicitly says "DO NOT EDIT". While it may work in the short term, it could cause problems later on.

> editing grub too is also unclear and without a line # to edit and a code example

Line # might vary, but there is only one GRUB_CMDLINE_LINUX_DEFAULT line

> i don't know how to be more clear that you are vague and incomplete in your explanations.

*Shrug* I learned a long time ago that I could lead a horse to water, but couldn't make it drink. Everyone has a different level of reading comprehension...

> tsk tsk
Keep your tsk tsk's to yourself.

> and why can't ubuntu itself make this simple update for people who have this hardware???? 
The decision to not enable HDMI audio by default was made upstream (because it causes instability on some cards).

---

### Post by solitaire on 2013-04-01
Thank the fix worked for me.

Oh by the way:
> **webdesigncompanyla said:**
> both ways work perfectly and both are listed as solutions in this thread, but the editing grub.cfg method is unclear, editing grub too is also unclear and without a line # to edit and a code example, both fixes are poor examples of how to reproduce or follow, tsk tsk

i don't know how to be more clear that you are vague and incomplete in your explanations.

Editing the grub.cfg is a _**TERRIBLE**_ way to fix this especially when talking to people who are not used to Linux in general!!

That file is a "Dynamic" file which means it's recreated every time you get a new kernal or grub update! [B]Any fix added to that file will be lost when it's recreated leaving the user with the initial problem again.
[/B]
If you make the change in the "grub" file located here /etc/default/ then the change will survive any update as this is a STATIC file that is used to store this type of fix.

---

### Post by FuzzyFeat on 2013-04-01
You rock!  I have been goin' nuts with all the complex methods (that did not work) of getting my HDMI sound to work.  

This works! Thanks again.

---

### Post by solitaire on 2013-04-26
ARGH!!
Just upgraded to 13.04

HDMI audio was working in 12.10 with the radeon.audio=1 flag in /etc/default/grub

Flag is still in grub but i've no audio over HDMI

anyone else had a problem with audio on 13.04? 
Or is it just my bad luck ^_^

any help is gratefully welcomed 

 ```

bill@zotac:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```
```

bill@zotac:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=SB
    HDA ATI SB, ALC892 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Hardware device with all software conversions


```

---

### Post by conreo on 2013-04-29
Same problem... Ubutnu 13.04 and no HDMI Sound :
> $ aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: Intel [HDA Intel], périphérique 0: ALC889A Analog [ALC889A Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: Intel [HDA Intel], périphérique 1: ALC889A Digital [ALC889A Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: STX [Xonar STX], périphérique 0: Multichannel [Multichannel]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: STX [Xonar STX], périphérique 1: Digital [Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 2: Generic [HD-Audio Generic], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0


> $ aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, ALC889A Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC889A Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC889A Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC889A Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC889A Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC889A Digital
    Hardware device with all software conversions
sysdefault:CARD=STX
    Xonar STX, Multichannel
    Default Audio Device
front:CARD=STX,DEV=0
    Xonar STX, Multichannel
    Front speakers
surround40:CARD=STX,DEV=0
    Xonar STX, Multichannel
    4.0 Surround output to Front and Rear speakers
surround41:CARD=STX,DEV=0
    Xonar STX, Multichannel
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=STX,DEV=0
    Xonar STX, Multichannel
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=STX,DEV=0
    Xonar STX, Multichannel
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=STX,DEV=0
    Xonar STX, Multichannel
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=STX,DEV=0
    Xonar STX, Multichannel
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=STX,DEV=0
    Xonar STX, Multichannel
    Direct sample mixing device
dmix:CARD=STX,DEV=1
    Xonar STX, Digital
    Direct sample mixing device
dsnoop:CARD=STX,DEV=0
    Xonar STX, Multichannel
    Direct sample snooping device
dsnoop:CARD=STX,DEV=1
    Xonar STX, Digital
    Direct sample snooping device
hw:CARD=STX,DEV=0
    Xonar STX, Multichannel
    Direct hardware device without any conversions
hw:CARD=STX,DEV=1
    Xonar STX, Digital
    Direct hardware device without any conversions
plughw:CARD=STX,DEV=0
    Xonar STX, Multichannel
    Hardware device with all software conversions
plughw:CARD=STX,DEV=1
    Xonar STX, Digital
    Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions


But radeon.audio=1  in brub... Maybe the same way with the nvidia card?

---

### Post by solitaire on 2013-04-29
it's a "bug" with the kernel! when it was being compiled they left out a few modules that are required for some HDMI outputs!

You need to grab a newer kernel:
This worked for me:

[http://ubuntuforums.org/showthread.php?t=2139206&p=12621480#post12621480](http://ubuntuforums.org/showthread.php?t=2139206&p=12621480#post12621480)

---

