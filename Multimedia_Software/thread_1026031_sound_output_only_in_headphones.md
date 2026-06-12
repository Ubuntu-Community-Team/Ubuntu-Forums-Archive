---
title: "sound output only in headphones"
date: 2008-12-30
forum: Multimedia Software
---

### Post by parminides on 2008-12-30
I recently installed Ubuntu 8.10 Intrepid Ibex on an HP Touchsmart desktop. Shortly after the initial installation, the kernel was updated from 2.6.27-7-generic to 2.6.27-9-generic.

At some point, the sound was lost (except through the headphones). I've seen through the forums that I'm not the only one who's had this problem.

I'm not sure whether the kernel update had anything to do with it or not. I didn't notice that the sound was gone until today, but the kernel update was several days ago. Sound is not an issue for most of what I use.

Another possible cause of the sound loss is suggested by [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/25632](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/25632), namely, "If I use the 'AC3 passthrough' feature of a multimedia app (e.g. totem-xine), the SPDIF output will stop working with PCM (forever)." 

I don't know enough to know whether this is pertinent, but many parts of this thread seemed to be applicable. Also, I was using Miro last night with my headphones. I have no idea whether this was using the "AC3 passthrough feature of a multimedia app."

Another thread (which I neglected to bookmark) suggested that this problem (sound only in the headphones) arose for him after he rebooted with the headphones plugged in! Yikes!

Yet another possible culprit is an adaptor device I bought recently that is supposed to let the user plug headphones with a standard plug into a usb port of the computer. 

Whatever the cause, I'm not getting any sound anymore except through the headphones.

I'm not really a hardware kind of guy, but, according to [http://www.maximumpc.com/article/hp_touchsmart_iq770](http://www.maximumpc.com/article/hp_touchsmart_iq770), I have a Integrated Analog Devices SoundMAX HD soundcard.

Here's some more info about my system:

```

$ lspci -v  | more

```
      .
      .
      .

```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
 (rev 04)
	Subsystem: Hewlett-Packard Company Device 2a74
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fe8f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```
      .
      .
      .

and
```

$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I tried a few of the things suggested in this thread and others as possible workarounds, but without any luck. Below is an accounting of what I tried.

1st suggestion:

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo shutdown -r 0

```

No apparent effect on anything.

2nd suggestion:

Uninstall ld10k1 and qlo10k1 [Actually, I skipped this step since they didn't
seem to be installed on my computer.] Then,

```

sudo mv /etc/init.d/alsa-utils /etc/init.d/alsa-utils.GONE
sudo shutdown -r 0
sudo mv /etc/init.d/alsa-utils.GONE /etc/init.d/alsa-utils

```

Then, use mixer to restore volume.

3rd suggestion:

Edit .asoundrc to include the lines,

```

pcm.!default {
   type plug
   slave {
        pcm "spdif"
        rate 48000
        format S16_LE
    }
}

```

Actually, the suggestion was to create the file .asoundrc, but it already existed on my system, so I just added the lines.

Note: their following suggestion was to run...

```

speaker-test -D spdif -c 2
speaker-test -c 2

```

...presumably as a diagnostic. The first command yielded a string of error messages, such as,

```

speaker-test 1.0.17

Playback device is spdif
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card 'default'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device

```
	.
	.
	.

The second test (speaker-test -c 2) produces sound, but only through the headphones!

4th suggestion:

Open a terminal and issue the command,

```

iecset audio 1

```

For me that command returned the error message,

```

control "IEC958 Playback Default" (index -1) not found

```

5th suggestion:

Edit /etc/modprobe.d/alsa-base, adding the lines,

```

options snd-card-0 enable=1 index=0 model=basic
options snd-hda-intel enable=1 index=0 model=basic

```

No apparent effect.

6th suggestion:

I followed the steps outlined at [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506), to no avail, although, admittedly, I didn't have the nerve to dive into his 10,000 page guide!

7th suggestion:

Sections A and C at [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Nothing worked. I've changed so many audio things that I fear that my system is totally fubar now.

Can anyone set me on the path to audio righteousness?

---

### Post by robinbj on 2009-04-11
> **parminides said:**
> I recently installed Ubuntu 8.10 Intrepid Ibex on an HP Touchsmart desktop. Shortly after the initial installation, the kernel was updated from 2.6.27-7-generic to 2.6.27-9-generic.

At some point, the sound was lost (except through the headphones). I've seen through the forums that I'm not the only one who's had this problem.

I'm not sure whether the kernel update had anything to do with it or not. I didn't notice that the sound was gone until today, but the kernel update was several days ago. Sound is not an issue for most of what I use.

Another possible cause of the sound loss is suggested by [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/25632](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/25632), namely, "If I use the 'AC3 passthrough' feature of a multimedia app (e.g. totem-xine), the SPDIF output will stop working with PCM (forever)." 


Wow, sounds like youve done a lot. Has any new updates come your way? I am looking to get sound but still nothing and I even tried your ways to see if maybe I had some kind of enomoly....
I don't know enough to know whether this is pertinent, but many parts of this thread seemed to be applicable. Also, I was using Miro last night with my headphones. I have no idea whether this was using the "AC3 passthrough feature of a multimedia app."

Another thread (which I neglected to bookmark) suggested that this problem (sound only in the headphones) arose for him after he rebooted with the headphones plugged in! Yikes!

Yet another possible culprit is an adaptor device I bought recently that is supposed to let the user plug headphones with a standard plug into a usb port of the computer. 

Whatever the cause, I'm not getting any sound anymore except through the headphones.

I'm not really a hardware kind of guy, but, according to [http://www.maximumpc.com/article/hp_touchsmart_iq770](http://www.maximumpc.com/article/hp_touchsmart_iq770), I have a Integrated Analog Devices SoundMAX HD soundcard.

Here's some more info about my system:

```

$ lspci -v  | more

```
      .
      .
      .

```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
 (rev 04)
	Subsystem: Hewlett-Packard Company Device 2a74
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fe8f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```
      .
      .
      .

and
```

$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I tried a few of the things suggested in this thread and others as possible workarounds, but without any luck. Below is an accounting of what I tried.

1st suggestion:

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo shutdown -r 0

```

No apparent effect on anything.

2nd suggestion:

Uninstall ld10k1 and qlo10k1 [Actually, I skipped this step since they didn't
seem to be installed on my computer.] Then,

```

sudo mv /etc/init.d/alsa-utils /etc/init.d/alsa-utils.GONE
sudo shutdown -r 0
sudo mv /etc/init.d/alsa-utils.GONE /etc/init.d/alsa-utils

```

Then, use mixer to restore volume.

3rd suggestion:

Edit .asoundrc to include the lines,

```

pcm.!default {
   type plug
   slave {
        pcm "spdif"
        rate 48000
        format S16_LE
    }
}

```

Actually, the suggestion was to create the file .asoundrc, but it already existed on my system, so I just added the lines.

Note: their following suggestion was to run...

```

speaker-test -D spdif -c 2
speaker-test -c 2

```

...presumably as a diagnostic. The first command yielded a string of error messages, such as,

```

speaker-test 1.0.17

Playback device is spdif
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card 'default'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device

```
	.
	.
	.

The second test (speaker-test -c 2) produces sound, but only through the headphones!

4th suggestion:

Open a terminal and issue the command,

```

iecset audio 1

```

For me that command returned the error message,

```

control "IEC958 Playback Default" (index -1) not found

```

5th suggestion:

Edit /etc/modprobe.d/alsa-base, adding the lines,

```

options snd-card-0 enable=1 index=0 model=basic
options snd-hda-intel enable=1 index=0 model=basic

```

No apparent effect.

6th suggestion:

I followed the steps outlined at [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506), to no avail, although, admittedly, I didn't have the nerve to dive into his 10,000 page guide!

7th suggestion:

Sections A and C at [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Nothing worked. I've changed so many audio things that I fear that my system is totally fubar now.

Can anyone set me on the path to audio righteousness?

Im sorry to hear of your upset. I tried everything you did and same as you no go.

Have you had any revelation since?
I would love to have sound..

brad

---

### Post by parminides on 2009-04-12
> **robinbj said:**
> Im sorry to hear of your upset. I tried everything you did and same as you no go.

Have you had any revelation since?
I would love to have sound..

brad

No, only the sounds of silence (including the deafening silence of on this thread)! :(

Let me know if you have better luck than I did.

---

