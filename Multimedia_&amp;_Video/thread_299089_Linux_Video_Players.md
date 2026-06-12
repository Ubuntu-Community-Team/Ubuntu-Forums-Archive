---
title: "Linux Video Players"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by FusionXN1 on 2006-11-13
I am looking for a Linux (Ubuntu/Kubuntu) video player that can play:

XVID, DIVX, AC3, OGM, OGG, MP3, TS, ( 2nd application for these? -- Quicktime and real)

I know theres VLC, but i dont like the small volume control on it and I wondered if anyone wouldn't mind recommending a few apps to me :)

Thanks!!

---

### Post by loell on 2006-11-13
gxine and mplayer

---

### Post by FusionXN1 on 2006-11-13
gxine looks good, wheres the download link for that? Anymore recommendations?

---

### Post by Ramses de Norre on 2006-11-13
No download links stuff, ```
sudo aptitude install gxine
``` or look for it in synaptic.

---

### Post by FusionXN1 on 2006-11-13
Ok thanks.

---

### Post by justinjstark on 2006-11-13
Totem plays all of these fine...at least totem-xine does.   Totem-gstreamer *should* be able to play all of these (if you install the proper plugins/codecs) by the time feisty fawn rolls out.

---

### Post by FusionXN1 on 2006-11-13
So what is I need to get for totem? synaptic or W/E and select totem-xine ?

---

### Post by Ramses de Norre on 2006-11-13
Everything you need to install can be done through synaptic/apt-get/aptitude, these three are all frontends for the same backend.

So yes, you can just search for the totem-xine package in synaptic, and it will probably tell you that totem-gstreamer will be removed but that's totally normal.
You'll want to check [this](http://wiki.ubuntu.com/RestrictedFormats) out too for adding support for restricted formats.

---

### Post by FusionXN1 on 2006-11-13
> **Ramses de Norre said:**
> Everything you need to install can be done through synaptic/apt-get/aptitude, these three are all frontends for the same backend.

So yes, you can just search for the totem-xine package in synaptic, and it will probably tell you that totem-gstreamer will be removed but that's totally normal.
You'll want to check [this](http://wiki.ubuntu.com/RestrictedFormats) out too for adding support for restricted formats.

Thanks! What I can see there is real and WMV/WMA which I'll need. Oh and flash i see. What about quicktime?

---

### Post by Ramses de Norre on 2006-11-13
Should be working too, I'm not sure which package has it. If you're using xine you shouldn't install all the gstreamer packages, just libxine and libxine-extracodecs.
Then add all the other formats like flash and java and libdvdcss etc. it's all described at the page.

---

### Post by FusionXN1 on 2006-11-13
Thanks a lot mate :) Appreshate the help a lot! do you know of any [Checkers & Pool Games](http://ubuntuforums.org/showthread.php?t=299102)?

---

### Post by drphilngood on 2006-11-14
Try foobilliard, it's my favorite linux game.  You can play it online, too.
Can't help you with the checkers game, though.:-k

---

### Post by FusionXN1 on 2006-11-14
Ya I noticed that one, it's great thanks!

---

### Post by rajasekharan on 2006-11-15
is there any way that i can download all the multimedia tools in a cd and then install it in ubuntu...?????, i dont have a net connection......:(

---

### Post by loell on 2006-11-15
> **rajasekharan said:**
> is there any way that i can download all the multimedia tools in a cd and then install it in ubuntu...?????, i dont have a net connection......:(

[http://www.ubuntustudio.com/]("http://www.ubuntustudio.com/")

though it hasn't been released yet

---

### Post by rajasekharan on 2006-11-15
thanks a lot...:), i have bookmarked that site...:)

---

### Post by patrick295767 on 2006-11-19
> **FusionXN1 said:**
> I am looking for a Linux (Ubuntu/Kubuntu) video player that can play:

XVID, DIVX, AC3, OGM, OGG, MP3, TS, ( 2nd application for these? -- Quicktime and real)

I know theres VLC, but i dont like the small volume control on it and I wondered if anyone wouldn't mind recommending a few apps to me :)

Thanks!!
 
You got lot of replies;
the codecs are also important to be present in : /usr/lib/win32
(there too: [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html))

---

