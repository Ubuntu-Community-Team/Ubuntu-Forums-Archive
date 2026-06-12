---
title: "GNOME Mplayer problems"
date: 2010-12-31
forum: Multimedia Software
---

### Post by jeddycakes on 2010-12-31
Hi,

Just recently, when opening a video file with GNOME Mplayer, this dialogue box has popped up without fail as the video starts:

```

Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

```

With "GNOME MPLAYER ERROR" above it. 

Any ideas? I'm running:
```

VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

```

I have previously had no issues with this. To my knowledge, I have not adjusted/changed anything to do with my graphics.

TY in advance

---

### Post by mc4man on 2010-12-31
Try opening gnome-mplayer - edit - preferences and see what the video output is set to, if vdpau then change to something else, try xv first.

(if still no go then search libvdpau in synaptic and even though you can't use it install if not already, probably seen as libvdpau1 - most mplayer builds depend on it so it should be installed

---

### Post by jeddycakes on 2010-12-31
> **mc4man said:**
> Try opening gnome-mplayer - edit - preferences and see what the video output is set to, if vdpau then change to something else, try xv first.


Thanks, man. Worked a treat. It was selected to nothing at all, but setting to xv has got rid of the annoying box so I'm happy!

TVM

---

### Post by jeddycakes on 2010-12-31
> **mc4man said:**
> Try opening gnome-mplayer - edit - preferences and see what the video output is set to, if vdpau then change to something else, try xv first.


Thanks, man. Worked a treat. It was selected to nothing at all, but setting to xv has got rid of the annoying box so I'm happy!

TVM

---

### Post by jeddycakes on 2010-12-31
> **mc4man said:**
> Try opening gnome-mplayer - edit - preferences and see what the video output is set to, if vdpau then change to something else, try xv first.


This worked for me, thanks. Initial setting was sactually set to nothing at all (?) but setting to xv has got rid of the annoying box, so I'm happy!

TVM

---

### Post by jeddycakes on 2010-12-31
> **mc4man said:**
> Try opening gnome-mplayer - edit - preferences and see what the video output is set to, if vdpau then change to something else, try xv first.


This worked for me, thanks. Initial setting was sactually set to nothing at all (?) but setting to xv has got rid of the annoying box, so I'm happy!

TVM

---

### Post by jeddycakes on 2011-01-01
Wtf????

---

### Post by mc4man on 2011-01-01
> Wtf????
Seems to be happening on occasion (the inadvertent multiple posts

While you can't remove the dups you can edit them back to a min. of 1 character
(I didn't think you were that overcome...

---

