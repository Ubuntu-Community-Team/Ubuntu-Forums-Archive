---
title: "sound occasionally stops working (no output)"
date: 2009-01-16
forum: Multimedia Software
---

### Post by formerwindowspoweruser on 2009-01-16
I am using Ubuntu 8.10 and have on-board sound. Currently my settings are

System > Preferences > Sound
Sound events = intel ICH5 with ALC658D Intel ICH5 - IEC958 (ALSA)

same for "music and movies" and "audio conferencing"

After I reboot, sound works fine for a while. Then one day I'll come in and sound doesn't work. Log off/log back on doesn't fix it, but a reboot does (for a while).

Currently the time between reboots is 3 days and it stopped working today (2 days of sound, then it stopped). I'll post again with the length of time between when I reboot and when it stops working.

In "sound preferences" dialog box, I have other options for sound playback. However, when I switch to another choice, like "Intel ICH5 with ALC658D Intel ICH5 (OSS)" and test, then I get a warning, "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application." The other, non-intel choices, like "ALSA" and "PulseAudio Sound server" allow the "testing pipeline" to open and do a test, but no audio signal is heard.

Please let me know what other information would be helpful. I searched dmesg output for the work "alsa" but found nothing. Switching to the kde interface also has no effect.

I am looking for a fix that will allow audio to remain available. 

I just switched from Windows and was hoping to avoid daily reboots.

Thanks.

**************************

after this initial post, logging off, then logging back in worked. However, the next day sound was again missing. This time logging off, then logging back in did not work. 

When I say "did not work", I mean Amarok plays but doesn't emit audio, my movies don't have sound, and youtube videos don't have sound. Thus, I don't think it's a specific player's fault.

Rebooting did work.

---

### Post by sickenmcsluggets on 2009-01-18
I'm having the same problem and its killing me. I'm currently trying to google it and search these forums. Been with Ubuntu for a while, and this is the most frustrating thing by far. Sound has always been perfect for my all the way back to Dapper.
Here are some threads:
[http://ubuntuforums.org/showthread.php?t=1015270&highlight=reboot+sound+working](http://ubuntuforums.org/showthread.php?t=1015270&highlight=reboot+sound+working)
In the above thread, this worked at least temporarily for me:
> **sarang said:**
> Try grace-killing pulseaudio and restarting it manually.
```

killall pulseaudio

```
 and then 

```

pulse-session

```

If this does not work, try force-killing it:

```

killall -9 pulseaudio

```
and then
```
pulse-session
```

Then there is this thread I went through, and I guess I'll see if my problem persists.
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by formerwindowspoweruser on 2009-01-18
Thanks for the help.

```
killall -9 pulseaudio
```

seems to work (this time).

Not sure why it worked, since in "System > Preferences > Sound" I didn't have any options set to use pulseaudio.

I previously tried
```

$ sudo apt-get update
$ sudo apt-get upgrade

```
but both came back empty.

For future reference, my hardware is
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci -v
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at d800 [size=256]
    I/O ports at dc00 [size=64]
    Memory at fc001000 (32-bit, non-prefetchable) [size=512]
    Memory at fc002000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

```

---

