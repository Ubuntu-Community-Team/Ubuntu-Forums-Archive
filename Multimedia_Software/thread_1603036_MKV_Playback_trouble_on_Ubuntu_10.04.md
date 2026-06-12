---
title: "MKV Playback trouble on Ubuntu 10.04"
date: 2010-10-22
forum: Multimedia Software
---

### Post by Gan_HOPE326 on 2010-10-22
Hi,
I have some trouble in playing mkv files (both 720p and 400p) on Ubuntu. I had no problem whatsoever playing the same files when I still had Windows, so I'm assuming this is not an hardware problem. I have an HP Pavillion laptop, an nVidia graphic card with proprietary drivers for Ubuntu, dual core AMD processor, and Ubuntu 10.04 64bit installed. Many other applications are actually way faster, now, than with Windows, as that was just a 32bit version. Nevertheless, I have problems. Totem is usually slow, and generates lags between video and audio. I used MPlayer (with Gnome GUI), and it was ok with some files, but with some others (can't find any particular logic, maybe it's due to different encoding methods) it will just start, not show anything, NOT CLOSE, and enter in some kind of stall. The CPU overheats and I'm forced to reboot to stop it.
(It's not due to folders too crowded with mkv files... I've tried to take the files out of their folders, they still give trouble).
Finally, VLC kinda works, but still won't allow me to jump in between the file. With some files it just doesn't jump. With a file I acquired recently, it jumps to exactly HALF of the time I actually asked for the jump (Like, I ask to jump at 42 min., it jumps at 21 min.). Chapter selection won't work either.
Please help me... I'm confident there must be some way to overcome this, maybe it's just some wrong setting. Thank you!

---

### Post by kerry_s on 2010-10-22
i use gnome-mplayer with some settings.

```
-lavdopts skiploopfilter=all -nodouble -vf scale=640:480
```

---

### Post by Gan_HOPE326 on 2010-10-22
> **kerry_s said:**
> i use gnome-mplayer with some settings.

```
-lavdopts skiploopfilter=all -nodouble -vf scale=640:480
```

Thanks... but not working :(.

---

### Post by coskierken on 2010-10-22
I play mkv (720p) on my Asus a8JP (C2D/1.5G ram/ATIx1700) laptop without a problem in VLC.  Make sure you have all the codecs loaded.  If you install VLC, it does load most codecs.  What type of machine are you trying to run it on.  I have run it on laptops with only the intel chipsets.

---

### Post by Gan_HOPE326 on 2010-10-22
> **coskierken said:**
> I play mkv (720p) on my Asus a8JP (C2D/1.5G ram/ATIx1700) laptop without a problem in VLC.  Make sure you have all the codecs loaded.  If you install VLC, it does load most codecs.  What type of machine are you trying to run it on.  I have run it on laptops with only the intel chipsets.

Machine: HP Pavillion DV6000.
[http://www.mobilewhack.com/reviews/hp_pavilion_dv6000_new_notebook.html](http://www.mobilewhack.com/reviews/hp_pavilion_dv6000_new_notebook.html)
Check the specs. It's AMD DualCore, as I said, and it always ran smoothly under Windows. Also, I don't think there's a problem with codecs, if there weren't codecs I wouldn't see a thing. But maybe there are codec packs other than the ones I can find in the common Ubuntu repository, if that was the case I'd like to try them too.

---

### Post by kerry_s on 2010-10-22
it's got nvidia, have you set up vdpau ?
[http://www.google.com/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=vdpau#hl=en&sa=X&ei=vfDBTP7aJIG-sAOi7fXnCw&ved=0CBIQvwUoAQ&q=ubuntu+nvidia+vdpau&spell=1&fp=7bc4deae06aba4f2](http://www.google.com/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=vdpau#hl=en&sa=X&ei=vfDBTP7aJIG-sAOi7fXnCw&ved=0CBIQvwUoAQ&q=ubuntu+nvidia+vdpau&spell=1&fp=7bc4deae06aba4f2)

---

### Post by Gan_HOPE326 on 2010-10-22
> **kerry_s said:**
> it's got nvidia, have you set up vdpau ?
[http://www.google.com/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=vdpau#hl=en&sa=X&ei=vfDBTP7aJIG-sAOi7fXnCw&ved=0CBIQvwUoAQ&q=ubuntu+nvidia+vdpau&spell=1&fp=7bc4deae06aba4f2](http://www.google.com/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=vdpau#hl=en&sa=X&ei=vfDBTP7aJIG-sAOi7fXnCw&ved=0CBIQvwUoAQ&q=ubuntu+nvidia+vdpau&spell=1&fp=7bc4deae06aba4f2)

Sorry, I made a mistake, it's actually an ATI Radeon. I got confused with my previous computer :P... Anyway, I installed the analogous ATI packages (xvba). Basically, though, nothing changed. I'd be ok with VLC if it wasn't for the skipping trouble, that doesn't allow me to jump to a position in the middle of the file.

---

