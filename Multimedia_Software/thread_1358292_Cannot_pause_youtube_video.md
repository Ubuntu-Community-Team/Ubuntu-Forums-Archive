---
title: "Cannot pause youtube video ??"
date: 2009-12-18
forum: Multimedia Software
---

### Post by annasarp on 2009-12-18
Hi all
I am unable to pause the youtube video while using ubuntu 9.1
In windows i am able to pause.
I am using ubuntu 9.1 and latest version of Firfox..
any suggestions??:(

---

### Post by saltmore on 2009-12-18
I am guessing 64 bit os?

Edit /usr/lib/nspluginwrapper/i386/linux/npviewer
add the following line BEFORE the last line of text
export GDK_NATIVE_WINDOWS=1
Save.
Restart any applications using flash.

---

### Post by Ylon on 2009-12-18
> **annasarp said:**
> Hi all
I am unable to pause the youtube video while using ubuntu 9.1
In windows i am able to pause.
I am using ubuntu 9.1 and latest version of Firfox..
any suggestions??:(

The problem is Compiz+Flash, if you disable desktop effect your click will be back work perfectly.

Another trurn-around is to: press and hold righ-mouse-button (appear flash's popup menu) > now while RMB is pressed (and the cursor is still in the flash's field) the click (with the other button) should also.

Anyway, there's also a 64bit version of Flash for linux
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html) (tar.gz to install btw)

---

### Post by saltmore on 2009-12-18
> **Ylon said:**
> The problem is Compiz+Flash, if you disable desktop effect your click will be back work perfectly.

Another trurn-around is to: press and hold righ-mouse-button (appear flash's popup menu) > now while RMB is pressed (and the cursor is still in the flash's field) the click (with the other button) should also.

Anyway, there's also a 64bit version of Flash for linux
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html) (tar.gz to install btw)

Did they finally get around to fixing the 64 bit flash?

---

### Post by smo0th on 2009-12-18
Try by using the space bar to pause/play and <- -> arrows to rwd and ffwd

---

### Post by Ylon on 2009-12-18
> **saltmore said:**
> Did they finally get around to fixing the 64 bit flash?

that's the alpha dev (not for public release) version of Adobe Flash for Linux64bit. It deal with some performance problem that can be experienced, but not the final fix.

Anway, I am testing youtube videos right now with the "video" plugin disabled: also seem to work.
To disable the video plugin of compiz you need the complete backend configurator of compiz:

in a terminal:
**sudo apt-get install compizconfig-settings-manager**

then run: **ccsm** and disable "Video Playback" plugin.

---

### Post by DJ_Cripple on 2010-02-26
> **Ylon said:**
> Anway, I am testing youtube videos right now with the "video" plugin disabled (...)
run: **ccsm** and disable "Video Playback" plugin.

Weirdly enough, I disabled the video playback plugin, and it still didn't work.  then we i re-*enabled* the video plugin flash did start working.

Mind you, I also tried saltmore's suggested fix, which didn't work at first, and I haven't changed that back to the way it was, so maybe it's a combination of the two...

> Edit /usr/lib/nspluginwrapper/i386/linux/npviewer
add the following line BEFORE the last line of text
export GDK_NATIVE_WINDOWS=1

---

