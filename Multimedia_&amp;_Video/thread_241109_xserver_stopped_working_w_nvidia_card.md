---
title: "xserver stopped working w/ nvidia card"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by King Big Ben on 2006-08-21
Alright i tried searching google and this forum but I didnt see anything that would be applicable...i upgraded ubuntu and installed some codecs for movies then tried a ctrl-alt-backspace but then x wouldnt start up again...it originally gave me a "failed to load /usr/lib/xorg/modules/extensions/libGLcore.so" error but after reinstalling and reconfiguring various things now I get this:

[INDENT](EE) No devices detected.

Fatal server error:
no screens found

XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests _0 known processed) with 0 events remaining."[/INDENT]

my xorg.conf seems to be configured correctly with driver set to "nvidia" (it's a geforce 4 mx). I tried setting it to vesa and a few other things but none of that worked. I'm still a relative newbie to linux so any help would be much appreciated :)

---

### Post by evilghost on 2006-08-21
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

---

### Post by evilghost on 2006-08-21
More info at [http://ubuntuforums.org/showthread.php?t=240957](http://ubuntuforums.org/showthread.php?t=240957)

---

### Post by King Big Ben on 2006-08-21
Ah thanks i feel like an idiot :)

---

### Post by evilghost on 2006-08-21
> **King Big Ben said:**
> Ah thanks i feel like an idiot :)

Hey no problem man, just glad I could help.  :)

---

