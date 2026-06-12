---
title: "No sound in mplayer/vlc/etc. but flash in browser / gnome tests are fine!"
date: 2009-02-09
forum: Multimedia Software
---

### Post by tariq.khokhar on 2009-02-09
Hi All,

This feels like I'm missing something obvious.

In short, I'm not getting any sound playback from VLC / mplayer / totem but sound plays fine on youtube in a browser and the gnome sound preferences test beeps work fine too.

In particular with mplayer in the terminal, the software starts up but it seems to "block" and stop when it gets to the audio playback bit. It's like something else has a lock on the audio but nothing does and ALSA should mix properly right?

This behavior started after a reboot so it may be recent packages installed but there's nothing seemingly audio related in recent entries to dpkg.log

Any ideas appreciated!

Thanks,

tk

Some details:

- Running 8.04 with latest updates.

```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Elaztic on 2009-02-09
Hi,

Did you check your sound preferences in System -> Preferences -> Sound or/and in alsa-mixer?
Usually the PCM or Master volume is turned down or disbled.

---

### Post by laceration on 2009-02-09
Flash has always messed with my sound.  Playing flash often seems to make sound unavailable for other apps.  I have had the problem with different versions of flash incl. a newer beta.  Closing firefox and restarting mplayer or whatever usually fixes the problem, but sometimes I need to go into the volume control app and reset some very whacked out settings.

Those are the obvious answers, if you want to dial in your pulse audio here is a guide:
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

