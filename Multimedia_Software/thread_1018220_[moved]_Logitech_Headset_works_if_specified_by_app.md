---
title: "[moved] Logitech Headset works if specified by application, but not as default"
date: 2008-12-21
forum: Multimedia Software
---

### Post by SlidingHorn on 2008-12-21
Okay, I've searched all over the forums and the net about this one, and I've found some similar situations, but none of their responses seem to be fixing the problem.

I am running Xubuntu Intreped, and am basically trying to allow myself to switch between my speakers and my Logitech USB headset (speakers & mic) as the default playback devices (so as not to disturb my girlfriend after she goes to bed with JJ Johnson blaring through the walls) 

If I am able to specify within an application (skype, vlc, etc.) to select the headset as the playback device, it works beautifully.  However, if I go to my sound settings for Ubuntu, and select the headset as default, the headset doesn't play at all. (vis a vis: [https://answers.launchpad.net/ubuntu/+question/51565](https://answers.launchpad.net/ubuntu/+question/51565))

On top of that, when I go back into my sound settings, the checkbox next to "Speaker,0" is unchecked again.

lsusb shows the headset as
```
Bus 001 Device 003: ID 046d:0a01 Logitech, Inc. USB Headset

```

cat /proc/asound/cards:
```
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 80 with ALC658D at 0xfe02a000, irq 17
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:13.0-1, full speed

```

It's a recognized device:
```
ryan@ryan-desktop:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
[B]  8: [ 1- 0]: digital audio playback
  9: [ 1- 0]: digital audio capture[/B]
 10: [ 1]   : control

```

I have been tooling around with *buntu for a while, but I'd still consider myself a noob of sorts.  This would be one of those times.  

Basically I just want to be able to easily switch between the speakers and headset so I can listen to last.fm in peace at night, lol

Any help you can provide is appreciated.

---

### Post by SlidingHorn on 2008-12-22
Bumpers? :)

---

### Post by kostkon on 2008-12-22
> **SlidingHorn said:**
> Okay, I've searched all over the forums and the net about this one, and I've found some similar situations, but none of their responses seem to be fixing the problem.

I am running Xubuntu Intreped, and am basically trying to allow myself to switch between my speakers and my Logitech USB headset (speakers & mic) as the default playback devices (so as not to disturb my girlfriend after she goes to bed with JJ Johnson blaring through the walls) 

If I am able to specify within an application (skype, vlc, etc.) to select the headset as the playback device, it works beautifully.  However, if I go to my sound settings for Ubuntu, and select the headset as default, the headset doesn't play at all. (vis a vis: [https://answers.launchpad.net/ubuntu/+question/51565](https://answers.launchpad.net/ubuntu/+question/51565))

On top of that, when I go back into my sound settings, the checkbox next to "Speaker,0" is unchecked again.

lsusb shows the headset as
```
Bus 001 Device 003: ID 046d:0a01 Logitech, Inc. USB Headset

```

cat /proc/asound/cards:
```
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 80 with ALC658D at 0xfe02a000, irq 17
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:13.0-1, full speed

```

It's a recognized device:
```
ryan@ryan-desktop:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
[B]  8: [ 1- 0]: digital audio playback
  9: [ 1- 0]: digital audio capture[/B]
 10: [ 1]   : control

```

I have been tooling around with *buntu for a while, but I'd still consider myself a noob of sorts.  This would be one of those times.  

Basically I just want to be able to easily switch between the speakers and headset so I can listen to last.fm in peace at night, lol

Any help you can provide is appreciated.
In *Ubuntu* you would normally install the *PulseAudio Device Chooser* utility to easily move the sound streams from one device to another and easily set the default device to be used.

But, I don't really know if *Xubuntu* uses *PulseAudio* or not.

---

### Post by markbuntu on 2008-12-22
Pulseaudio is definitely what you need if you want an easy way to control more than one sound device. There is probably far more information here than you need but it will help you understand. (You can skip to the Sound server setup section)


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by SlidingHorn on 2008-12-23
Thanks guys!  I'll play around with it and see what I find :)

**[COLOR="Lime"]***Mark Solved***[/COLOR]**

---

### Post by erikthedrink on 2009-09-08
In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

This should set your Logitech USB device as the general default. :confused:Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

