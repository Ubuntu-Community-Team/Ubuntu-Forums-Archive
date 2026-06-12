---
title: "Editing video without losing sync"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by gheywood on 2007-11-07
Does anyone know a program that can edit video without losing AV sync? 

I am currently capturing to AVI using VLC and that seems fine, but after editing with AVIDEMUX audio and video are no longer in sync. Apart from that it works great though.

Can anyone recommend a program or way to edit video (AVI or perhaps another format?) so I can get it in sync, and ready to burn to DVD?

Cheers

---

### Post by wjston on 2007-11-07
> **gheywood said:**
> Does anyone know a program that can edit video without losing AV sync? 

I am currently capturing to AVI using VLC and that seems fine, but after editing with AVIDEMUX audio and video are no longer in sync. Apart from that it works great though.

Can anyone recommend a program or way to edit video (AVI or perhaps another format?) so I can get it in sync, and ready to burn to DVD?

Cheers

I struggled with Avidmux for a few days before I finally found a post about ProjectX. It took a bit of tinkering to figure out how to get it to edit  but, once I got that out of the way, I've used it to edit hours of tv shows without having one audio/video sync problem. I highly recommend giving it a try.  
[http://avidemux.org/admWiki/index.php?title=Project_X#Downloading_Project_X](http://avidemux.org/admWiki/index.php?title=Project_X#Downloading_Project_X)

---

### Post by gheywood on 2007-11-24
Thanks. Looks awesome, but I have no clue how to use it.

Do you know any good help sites for Project X? i went through the online help, but it is all dutch to me.

cheers

---

### Post by vanadium on 2007-11-24
You can get away with Avidemux provided you give it the proper audio/video delay. When you loaded your original video into Avidemux, go to Audio - Main track and note the "ms shift" that is indicated there. You need to enter that shift into the "shift" box (and check the mark) for Avidemux to include the delay into the outputfile as well.

---

### Post by gheywood on 2007-11-25
So in there it says:

Audio track 0 (MP2/2 channels/192 kbit per s/607 ms shift)


So I then need to go to AUDIO/FILTERS and then in the MISC box, tick timeshift, and enter 607?

---

### Post by gheywood on 2007-11-25
Ah, -607.


Superb, thanks very much for that.

---

### Post by vanadium on 2007-11-25
No, you find the shift setting just in the main Avidemux application window.

---

### Post by gheywood on 2007-11-25
OK, that seems to work fine, and I have done some editing, but have another couple of questions if anyone can help..

1) When I play back the edited file (in different players), I cannot move forwards or backwards during playback. If I try and seek to a different location, it back to the start. Is there a setting I need to adjust while editing for this?

2) I think the output is AVI. Should I be using a different format if I want to go to DVD? 

3) Any benchmark quality settings for output to DVD? 

4) Is there an easy way to get this (and other clips) on to a DVD?

Thanks

---

### Post by gheywood on 2007-12-07
Any advice? Especially on the seeking during playback? Is there a setting that I need to add for this?

---

