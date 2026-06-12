---
title: "M-Audio Sonica USB problem - Gutsy"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by impalerau on 2007-12-22
I am trying to install an M-Audio Sonica USB on my laptop.  I'm new to Linux.  I plugged it in and nothing happened.  I fired up Device Manager and it didn't show up there.  I found this link [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60) and eventually got OSS installed but OSS can't see it either.  And now Device Manager won't start.

If I try running it from the command line using " $ hal-device-manager" I get:

[INDENT]Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 9, in <module>
    import gnome
  File "/var/lib/python-support/python2.5/gtk-2.0/gnome/__init__.py", line 13, in <module>
    from _gnome import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf
[/INDENT]

ossinfo gives me:

[INDENT]Version info: OSS 4.0 (b1011/200712200355) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 (gurieff-lt01)

Number of audio devices:        1
Number of audio engines:        10
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: maestro0 Maestro-2E interrupts=244708 (261776)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
Maestro2 AC97 Mixer (STAC9721) (Mixer 0 of device object 1)

Audio devices
Maestro-2E                        /dev/oss/maestro0/pcm0  (device index 0)
[/INDENT]

Now I don't know if I needed to remove alsa and install oss in the first place.  I just want to use my laptop as the primary audio/video source for my stereo and TV and have the Sonica as the default audio device.

Can someone help please?

---

### Post by impalerau on 2007-12-22
UPDATE
The sound using the default device was crackly and horrible using the oss driver so I've uninstalled it and gone back to alsa for now.  Would still love to get the Sonica to work.  Any ideas?

---

### Post by impalerau on 2007-12-22
I've made some progress but not quite there yet.  Some more googling and reading and I found this [http://ubuntuforums.org/archive/index.php/t-466667.html]("http://ubuntuforums.org/archive/index.php/t-466667.html")   I had seen it before but ignored it because the download url was dead.  Turns out it was just temporarilly offline.

It now shows up correctly in Device Manager.  I know it's working because I can hear the test tone through it via the Sound Preferences dialogue.  But everything is still using the ESS Maestro.

How do I make the Sonica the default sound device?

---

