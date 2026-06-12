---
title: "Missing &quot;hda intel (hw:intel,0)&quot; option in skype - Ubuntu Karmic"
date: 2009-10-30
forum: Multimedia Software
---

### Post by cipicip on 2009-10-30
Hi guys,

Just finished installing Ubuntu 9.10 Remix on an Aspire One netbook and after adding skype, can't find the "hda intel (hw:intel,0)" option in it's sound dropdowns (skype's). Only pulse audio - which works only partially. The output sound is working but no mic input.

The alsalib2 is installed, however if I try uninstalling pulseaudio, there is no more sound. At all.

What am I missing?


Thanks.

---

### Post by cipicip on 2009-10-30
Forgot to say it's skype version 2.1 and tried both the deb package and the static version.

---

### Post by cipicip on 2009-10-30
Bump!

---

### Post by cipicip on 2009-10-30
Solved. Installed skype version 2.0 and selected "HD Intel (hw:0)" option.
[http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb)

---

