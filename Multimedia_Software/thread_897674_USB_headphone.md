---
title: "USB headphone"
date: 2008-08-22
forum: Multimedia Software
---

### Post by terrordrone on 2008-08-22
Hi,

I have microsoft ( yeah... i know :( ) USB headphone ( [http://www.amazon.com/Microsoft-LifeChat-LX-3000-Headset-JUG-00001/dp/B000J4WPW8](http://www.amazon.com/Microsoft-LifeChat-LX-3000-Headset-JUG-00001/dp/B000J4WPW8) ) .. and i've been given a driver cd 

how do i get to use it in hardy ?

thanks

---

### Post by benbelly on 2008-08-22
> **terrordrone said:**
> Hi,
how do i get to use it in hardy ?


  I have a logitech headset that has been giving me trouble.  Here is what I have cobbled together through a number of searches.  At the commandline, type
```

aplay -l

```

I get the following output
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

  My onboard sound is card 0:NVidia, and my headset is card 1: Headset.  To switch to my headset, I type:

```

asoundconf set-default-card Headset

```

  You'll want to replace 'Headset' with whatever your headset is named in the list from aplay -l.  I suspect Headset is what you're looking for, but life is full of surprises.
  To switch back, I set the default card to NVidia.  That is almost certainly different than yours.  If you're not sure what to type, post the output of aplay -l while the headset is plugged in, and I'll see if I can help.

  I know this is not an ideal solution.  I'm still looking to find a better way.  However, at least I can listen to my music while I search now.  :)

-Ben

---

### Post by terrordrone on 2008-08-23
thanks..

i tried what you said above... but it didnt work..

this is what aplay -l gives : 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [Microsoft LifeChat LX-3000 ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


i did asoundconf set-default-card default :|

---

### Post by benbelly on 2008-08-23
> **terrordrone said:**
> i did asoundconf set-default-card default

hrm.  We're getting out of my depth here.  If you type
```
alsamixer -c 1
```
does anything happen?  Is the device muted?

-Ben

---

### Post by benbelly on 2008-08-23
I just discovered that the set-default-card only works for some application.  Try running using mplayer to at least see if you're getting sound.

---

### Post by terrordrone on 2008-08-24
sorry for the late reply

tried alsamixer -c 1

it still outputs through my speaker and not the headphone


...

if i plug in my headphone.. i can hear the ubuntu default boot sound play only in my headphone even while my speaker is outputting something else..

also i tried changing the sound preferences to usb audio... and could hear the beep when i clicked on test (after setting them to usb audio and the device to my headphone ) .. but i cant get my default output to be my headphone

---

### Post by markbuntu on 2008-08-24
If you are using pulseaudio you need to set the default output device in 

pavucontrol

the Pulse Audio Volume Control Output Devices Section. If you do not have it installed, you should get it with synaptic or apt-get. Is usually resides in Applications/Sound and Video and will let you change your audio streams from your headset to your speakers and visa versa anytime you want.

If you want to dial in your machine's sound system you can read my guide here ( it is rather long and windy but you will learn a lot about how sound works in Ubuntu):

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by erikthedrink on 2009-09-08
Instead of the name, use the number designation, which by your posting, is the number "1" In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

