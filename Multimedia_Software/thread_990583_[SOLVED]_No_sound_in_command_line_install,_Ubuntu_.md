---
title: "[SOLVED] No sound in command line install, Ubuntu 8.10"
date: 2008-11-22
forum: Multimedia Software
---

### Post by BeardlessForeigner on 2008-11-22
I know there are lots of no sound in Intrepid threads, but I haven't seen my particular problem mentioned anywhere and I'm sure someone will have some insight. As the title says, I did a command line install of 8.10, and have no sound. When I run "aplay -l" normally, I get:
```
michael@lappy:~$ aplay -l
aplay: device_list:215: no soundcards found...

```
And if I run alsamixer, I get an error:
```
michael@lappy:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

But if I run these as root, instead I get:
```
michael@lappy:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
and "sudo alsamixer" in fact opens up alsamixer.

I also get:
```
michael@lappy:~$ lspci -v

(...)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: IBM Device 0567
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1c00 [size=256]
        I/O ports at 1880 [size=64]
        Memory at b0000800 (32-bit, non-prefetchable) [size=512]
        Memory at b0000400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0
(...)

```

I have tried reinstalling alsa-base, alsa-util, and linux-sound-base as suggesting in the sound guide thread, and restarted, with the same effects. Does anyone have any suggestions or advice of what I can do to get my sound working?

---

### Post by BeardlessForeigner on 2008-11-23
I got impatient and installed xubuntu-desktop, and that cleared the issue up. I guess I just don't have the time now to work out the bugs of a minimal install.

---

### Post by BeardlessForeigner on 2009-03-14
Just as an update, I figured out what the problem is after a short foray into Archlinux. It seems that the Ubuntu base install does not add the user to the audio group. Essentially what you need to do after the install finishes is set up your audio as here:

[http://wiki.archlinux.org/index.php/Beginners_Guide#Step_1:_Configure_sound_with_alsamixer](http://wiki.archlinux.org/index.php/Beginners_Guide#Step_1:_Configure_sound_with_alsamixer)

You also need to add your user account to the audio group with the command

```

sudo gpasswd -a [username] audio

```

The "groups" command lists what groups the current user is party to. I just tried another base install today, and had to reboot after these steps for audio to show up in my groups, and then everything was ok.

---

