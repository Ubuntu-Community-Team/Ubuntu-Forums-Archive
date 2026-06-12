---
title: "Fresh Hardy install, sound working, but all or nothing - slider not adjustable!"
date: 2009-01-10
forum: Multimedia Software
---

### Post by heyho on 2009-01-10
As per title, gone from a fully functioning Gutsy install, to a Hardy Install with a few issues!

My sound is always at full volume when 1st booted, and is not adjustable via the volume slider - well, it is, but it can only be dragged to the bottom "mute" position.  Anywhere in between, it just bounces back up to full volume.

If I right click on the volume icon, the preference is set to "Realtek ALC861 (OSS mixer)".  If I set it to ALSA, I have control of the volume back, but It seems to default to full volume every reboot.

This is my first foray into sorting out sound problems, up until now it's just been wireless issues, so be gentle.

The machine is a Siemens-Fujitsu Amilo laptop, lspci gives the following:

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

---

### Post by markbuntu on 2009-01-10
The sound scheme in Hardy and Intrepid is very different from the one in Gutsy. They use Pulseaudio as the sound server but for some unfathomable reason Ubuntu did not include the controls for it. Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by heyho on 2009-01-11
Thanks for your pointer markbuntu.

I have tried a few different solutions already, which involved removing and installing various things, so goodness knows what I do and don't have on my system now, so I'll probably reinstall again, and follow your link.

Cheers, Heyho.

---

### Post by heyho on 2009-01-11
I've followed the link, and now have some control over the volume, but only in the pulseaudio drop down menu, the main volume control still bounces back up to full.

---

### Post by heyho on 2009-01-17
Turned out not to be a sound problem exactly, more a keyboard problem - for some reason the key release is not detected, hence the max or min volume.

Not solved, but may help someone else trying to sort this issue.  Same problem in fedora.

---

