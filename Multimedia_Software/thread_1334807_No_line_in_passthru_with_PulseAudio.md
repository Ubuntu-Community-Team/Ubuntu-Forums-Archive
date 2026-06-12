---
title: "No line in passthru with PulseAudio?"
date: 2009-11-22
forum: Multimedia Software
---

### Post by dodongo on 2009-11-22
So PulseAudio is happily up and running.  My mic works in Skype, MythTV runs fine, all seems well.  Except -- I don't have a line input anymore!  With, e.g., ALSA or the Windows mixer I'd have gotten a mixer UI with a slider for each input and would be able to control volume and mix that way.  Is it the case that PulseAudio simply has no support for this?  Can it be *that* unusual of a request?  How can I go about enabling Line In pass-through?

Thanks in advance!

---

### Post by cbl016 on 2009-12-10
I too would like to know how to do this.

---

### Post by markbuntu on 2009-12-11
You can get the gnome-alsa mixer and that will give you controls for all your sound device inputs and outputs which are missing in the new gnome volume control in the panel. 

If you want to direct the line in to another output you need to load the pulseaudio module-loopback which is not loaded by default. There is more on that here

[http://ubuntuforums.org/showthread.php?t=1324135](http://ubuntuforums.org/showthread.php?t=1324135)

---

### Post by cbl016 on 2009-12-11
Thanks the thread about adding the pulseaudio module-loopback worked for me.

---

