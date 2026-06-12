---
title: "Strange green line through gstreamer video"
date: 2008-05-06
forum: Multimedia Software
---

### Post by tim_wright on 2008-05-06
Thanks for reading this. Much appreciated. 

My problem is that when I watch videos through gstreamer I get the following output:

[ATTACH]69017[/ATTACH]

However, when I use the xine version I get the correct picture plus correct saturation of the colours.

[ATTACH]69016[/ATTACH]
If you want me to attach any logs or need any other information please ask and I would be most happy to help.

Thanks guys!

---

### Post by agim on 2008-05-06
It looks like a codec issue. Xine may come with some codecs readily available. Is there any special reason you don't like xine? My preference is VLC.

---

### Post by tim_wright on 2008-05-06
Gstreamer totem is the default so when I play media it appears first. Xine is better however because of the DVD menu support. 

I just like knowing that everything works :)

I think it just be an isolated incident as flv files play fine (this is an avi), although, if you have any suggestions as to what I could do they would be much appreciated. 

Thanks

---

### Post by KnightXsjado on 2009-03-29
Did you ever solve this, I get an .avi every once in a while and all three of the players I use. Totem and vlc have that green bar running through the video. Looks exactly like your pictures.

---

### Post by gandaran on 2009-03-29
> **KnightXsjado said:**
> Did you ever solve this, I get an .avi every once in a while and all three of the players I use. Totem and vlc have that green bar running through the video. Looks exactly like your pictures.
change the video output driver to x11 or any other that works in vlc preferences, do the same on other players, to change the totem driver open terminal and type **gstreamer-properties**

---

### Post by ukblacknight on 2009-04-05
> **gandaran said:**
> change the video output driver to x11 or any other that works in vlc preferences, do the same on other players, to change the totem driver open terminal and type **gstreamer-properties**

Thank you so much for this!  I've got rid of several videos because of this, thinking they were encoded badly!

Plus, I think the video displays straight away now in VLC - it used to be a blank screen, with audio when it first started, I'd always have to scroll back to the beginning for the video to display.

---

