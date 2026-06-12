---
title: "Hotplug usb headphones"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by Joe_CoT on 2006-10-02
I recently bought [these]("http://www.woot.com/Blog/BlogEntry.aspx?BlogEntryId=1476") from w00t.com, since I already had the mp3 version and they worked great. The usb one sounds much better than using the mp3 version through my analog sound card.

I have two issues with it, though. One's already been posted about in [this thread]("http://ubuntuforums.org/showthread.php?t=249026"). The other, though, is much more annoying: I can't seem to be able to hotplug the headphones.

If I start the computer with the usb reciever plugged in, it's recognized as a sound device, and is set as the first audio output in alsa. Perfect. But if I plug in the usb reciever while i'm in gnome ... nothing happens. Not detected at all. If I unplug it (after it was detected on startup), my normal sound card is still set as the second device in alsa. If I plug it back in, it does not work; not detected at all, even though alsa saved the 0 spot for it.

I've tried restarting alsa, i've tried restarting udev. Doesn't seem to redetect the usb or audio devices. While I could just restart the computer every time I want to switch, that would seriously cut down on my protein folding efficiency :-D Thoughts?

---

### Post by DoctorMO on 2007-01-16
Does it appear in `lsusb` when you plug them in?

I think it's likly to be an alsa problem, config for alsa is arcane at the best of times.

---

