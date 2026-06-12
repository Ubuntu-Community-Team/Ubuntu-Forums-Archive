---
title: "xDVD Shrink: Much Different from the Windows Version"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by teejay17 on 2007-01-30
I downloaded and installed DVD Shrink for Ubuntu (from Automatix), and all I have to say is "wow", but in a bad way. It is definitely not like its Windows counterpart!
Although I'm still learning Ubuntu, and don't mind a little challenge, when I went to rip a DVD the other night I found DVD Shrink pretty overwhelming and confusing, so much so that I waited to rip the DVD on a Windows box. It was all command line stuff, and things I've never heard of!
Anyway, although it says that xDVD Shrink is the "Linux counterpart of DVD Shrink," I think I'm still going to need some direction and assistance!

---

### Post by yabbadabbadont on 2007-01-30
They are two different software packages created by different people.  As far as I know, they are not related in any way other than they perform the same task.  :)

---

### Post by bruenig on 2007-01-30
Well I installed it from its website and have ripped two movies from it. It was very easy. It is graphical, so there shouldn't be any command line stuff. I don't know exactly what you are trying to do. I just ripped the main movie and then burned it which is probably the simplest thing but I would imagine the other stuff wouldn't be too hard.

---

### Post by teejay17 on 2007-01-30
For some strange reason it seems I'm missing a GUI for xDVD Shrink.

---

### Post by 3rdalbum on 2007-01-30
Well, the "x" in xDVD Shrink means that it is graphical.

I know there's  aset of instructions out there for ripping and shrinking a DVD on the command-line using MEncoder... are you maybe getting confused with that?

Also, I've had some success with k9copy (in the repositories). That's an incredibly easy program to use.

---

### Post by teejay17 on 2007-01-31
> **3rdalbum said:**
> Well, the "x" in xDVD Shrink means that it is graphical.

I know there's  aset of instructions out there for ripping and shrinking a DVD on the command-line using MEncoder... are you maybe getting confused with that?

Also, I've had some success with k9copy (in the repositories). That's an incredibly easy program to use.
Yeah, I'm not really sure what's going on; Automatix definitely tells me that I've installed xDVD Shrink. I think I'm going to uninstall the Automatix version of xDVD Shrink and perhaps I'll try installing it from the repositories instead, to see if that works better.
If I still don't get a graphical interface, then I'm going to shop around for another programme. I just want simple DVD shrinking and encoding, so I can backup store bought DVDs and play them in any region.

---

### Post by bruenig on 2007-01-31
Try running
```
/usr/bin/xdvdshrink.pl
```
That is how you start the graphical interface on my machine. xDvdshrink isn't in the repos you would need to get it from its website.

---

### Post by jackrobinson on 2007-01-31
> **teejay17 said:**
> I downloaded and installed DVD Shrink for Ubuntu (from Automatix), and all I have to say is "wow", but in a bad way. It is definitely not like its Windows counterpart!
Although I'm still learning Ubuntu, and don't mind a little challenge, when I went to rip a DVD the other night I found DVD Shrink pretty overwhelming and confusing, so much so that I waited to rip the DVD on a Windows box. It was all command line stuff, and things I've never heard of!
Anyway, although it says that xDVD Shrink is the "Linux counterpart of DVD Shrink," I think I'm still going to need some direction and assistance!

Automatix does install the right version and the right package of xdvdshrink but the menu item that it also installs points to the command line version of dvdshrink. You can run the GUI version by doing
```
/usr/bin/xdvdshrink.pl
```
You should file a bug report in the Automatix Forums to fix the menu item for dvdshrink that automatix installs so that it points to the GUI executable.

---

### Post by teejay17 on 2007-01-31
> **jackrobinson said:**
> Automatix does install the right version and the right package of xdvdshrink but the menu item that it also installs points to the command line version of dvdshrink. You can run the GUI version by doing
```
/usr/bin/xdvdshrink.pl
```You should file a bug report in the Automatix Forums to fix the menu item for dvdshrink that automatix installs so that it points to the GUI executable.
Okay, I'm going to try using that code when I get home from work tonight.
I haven't filed a bug before, so I'm not sure what the protocol is.

---

### Post by nalmeth on 2007-01-31
I've never tried xDVDShrink, but k9copy is good and native. 
DVDShrink in wine if k9copy doesn't work.

---

### Post by Uncle Spellbinder on 2007-02-01
> **jackrobinson said:**
> Automatix does install the right version and the right package of xdvdshrink but the menu item that it also installs points to the command line version of dvdshrink. You can run the GUI version by doing
```
/usr/bin/xdvdshrink.pl
```
You should file a bug report in the Automatix Forums to fix the menu item for dvdshrink that automatix installs so that it points to the GUI executable.

The code works fine.  Added a comment in the *xdxdshrink* bug thread at [**[color=#CC6600]Automatix Forums[/color]**](http://www.getautomatix.com/forum/index.php?s=&showtopic=568&view=findpost&p=2057).

---

### Post by teejay17 on 2007-02-02
[FONT=Georgia]Yes, the code works fine. Thanks everyone. Much appreciated. [/FONT]

---

