---
title: "Installed drivers - blue screen"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by Sprut on 2007-06-30
Hi,

I've installed all possible codecs, still when I try to play movies (in Totem, VLC, whatever) all I can see is a blue area. My movies won't show.

Edit; I can hear the sound.

What might be the problem ?

---

### Post by eggdeng on 2007-06-30
See if you can play the .ogg file in your /home/Examples folder. If so, you probably just need to install the codecs. See [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Sprut on 2007-06-30
> **eggdeng said:**
> See if you can play the .ogg file in your /home/Examples folder. If so, you probably just need to install the codecs. See [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

As I said before - I have installed the codecs. Tried using APT and Automatix, I get the same problem either way. Installing codecs twice wont work...

I can't see the .ogg example, same thing happens there, all that is rendered is blue.

---

### Post by eggdeng on 2007-06-30
Drivers != codecs. Are you using XGL? Compiz/Beryl? Can you start a session without them? Have you tried reverting to the bundled driver by editing your /etc/X11/xorg.conf & changing the line ```
Driver 'nvidia'
``` to ```
Driver 'nv'
``` (Nvidia cards), or ```
Driver 'flgrx'
``` to ```
Driver 'ati'
``` (Ati cards).

---

### Post by Sprut on 2007-06-30
> **eggdeng said:**
> Drivers != codecs. Are you using XGL? Compiz/Beryl? Can you start a session without them? Have you tried reverting to the bundled driver by editing your /etc/X11/xorg.conf & changing the line ```
Driver 'nvidia'
``` to ```
Driver 'nv'
``` (Nvidia cards), or ```
Driver 'flgrx'
``` to ```
Driver 'ati'
``` (Ati cards).

Well, I don't use compiz/beryl. And, Im on a laptop using an Unichrome Pro IGP graphics card so my driver is set to "via". Maybe thats the problem then?

---

### Post by eggdeng on 2007-07-01
Try replacing ```
Driver 'via' 
```with ```
Driver 'vesa'
``` If you can play video with that, then that would appear to narrow it down to the VIA driver.

---

### Post by Sprut on 2007-07-01
> **eggdeng said:**
> Try replacing ```
Driver 'via' 
```with ```
Driver 'vesa'
``` If you can play video with that, then that would appear to narrow it down to the VIA driver.

Thanks that did work, I can now watch the videos. The only thing is that I no longer have direct rendering. glxinfo gives several errors.

Any fix? :P

---

### Post by eggdeng on 2007-07-01
The vesa driver is very limited and not a long term solution, so you need to get the via driver working properly.
If you haven't done so already, check out the how-to at [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome). In particular, this section may be of interest.
> I do not have any picture when playing videos
This mostly happens when using a laptop and is caused by openChrome not supporting Xv correctly on some models. You can try to change the video driver in Xine to "gl" or "x11" and see if that helps. This problem does not appear when not using the integrated LCD and using an external monitor instead. The OpenChrome ticket for that is located here: [WWW] [http://www.openchrome.org/trac/ticket/40](http://www.openchrome.org/trac/ticket/40) If you do a forum search for Unichrome Pro IGP, you will find more suggestions.

---

### Post by Sprut on 2007-07-01
> **eggdeng said:**
> The vesa driver is very limited and not a long term solution, so you need to get the via driver working properly.
If you haven't done so already, check out the how-to at [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome). In particular, this section may be of interest.
 If you do a forum search for Unichrome Pro IGP, you will find more suggestions.

Did not work at all for me, and now using Via driver makes the whole screen flicker.

For some reason the sound is also missing now.

If only things actually worked with ubuntu....

---

### Post by eggdeng on 2007-07-01
Understand your getting pissed off & sorry I can't offer solutions. With a bit of patience, or even a reinstall, you will get everything else to work, but the bug with the open source driver for the Unichrome card looks like a bit of a show-stopper. :(

---

### Post by Sprut on 2007-07-01
> **eggdeng said:**
> Understand your getting pissed off & sorry I can't offer solutions. With a bit of patience, or even a reinstall, you will get everything else to work, but the bug with the open source driver for the Unichrome card looks like a bit of a show-stopper. :(

I appreciate the help, Linux has always been, and probably will always be hard to handle, sadly. Seems like I need to reinstall then, think I'll try with Dapper, thats what I used earlier, didn't have problems with that.

Btw, will installing KDE desktop do anything? The kernel is the same either way so I was wondering what good it would do, if anything :p

---

### Post by eggdeng on 2007-07-01
I still use Dapper on my laptop, always found it elegant, versatile & stable to a fault. Never been a fan of all those toothy KDE soviet art cogs but no harm in trying though.

---

