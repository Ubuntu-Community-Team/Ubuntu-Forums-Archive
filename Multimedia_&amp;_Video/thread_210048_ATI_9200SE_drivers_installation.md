---
title: "ATI 9200SE drivers installation"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by kookookachooo on 2006-07-06
Hi, I am pretty new and I only know the basics of linux; so could anyone give me a plain and simple (explained) list of directions of what to do to install my ati drivers? I've read many other threads and guides but there are always small little details that I do not understand. So if someone out there could help a 'noob' out, many thanks.:smile:

---

### Post by bikeboy on 2006-07-06
The easiest way is probably to follow the in-built documentation. Go to System > Help > System Doc > Desktop Guide > Configuring Your System > Hardware. That explains (in fairly simple terms) how to install the ATI drivers. There's lots of other useful stuff in there too.

---

### Post by ajgreeny on 2006-07-06
Do be warned, however, that the ati drivers (I assume you mean the proprietory fglrx driver) can be very difficult to install and get working properly.

It took me several attempts in Breezy, and so far I haven't managed to get it working in Dapper at all.  I have a second and separate test-bed install on a small drive on my machine and try things like that there first, before I do it on the main working system.  I have looked at just about all the tutorials and how-to's available in the wikis and on this forum, but so far no luck, so I've given up for now; frustrating, but less so than if I keep on wasting time and getting nowhere.  I just use the default ati driver that came at install, and get as much as 2500fps in glxgears, though I accept there is probably no hardware 3d acceleration.  As I don't play games that is of little consequence to me.

Best of luck if you try.

---

### Post by Craig Watson on 2006-07-06
Hi, I've got almost the same card as you (radeon 9200) and it works perfectly well with the free "radeon" driver (included in the installation), with direct acceleration, so it works great with 3D games etc.
But if you really want to install the proprietary drivers, have a look at [easy ubuntu]("http://easyubuntu.freecontrib.org/"). It installs a few programs that are very usefull, such as the ati and nvidia drivers, skype and wengo, mp3, divx etc. codecs, ms fonts, and more.. try it out.
Well, anyway, good luck.

---

### Post by pump on 2006-07-06
I have the same card with you and it was detected automatically and the radeon driver was installed. I actually have hardware acceleration.

---

### Post by ajgreeny on 2006-07-07
How can I tell if I have hardware or just software accelleration? I'm not sure which I do have following the posts by pump and Craig Watson.  glxgears gives me anything up to about 8500fps, depending on the size of the glxgears window, and whether or not it is in the foreground, or hidden by other windows.  At the start size I get about 880fps when in the foreground, but is it hardware or software accelleration?

---

### Post by pump on 2006-07-07
Try with "glxinfo" and it will show something as "Direct Rendering: Yes" (or no). There you'll know ;)

---

### Post by bikeboy on 2006-07-07
The easiest way is a slight variation on the post above.```
glxinfo | grep rendering
```

---

### Post by kookookachooo on 2006-07-23
Ok, I'm pretty sure I have my drivers installed. I typed in glxinfo and for direct rendering it reads "Direct Rendering: No" What can I do to change this to yes? Many thanks appreciated.

---

### Post by spadewarrior on 2006-09-21
I'm trying to change this in the System > Help > System Doc > Desktop Guide > Configuring Your System > Hardware for my ATI Radeon 9200se. Seeing as there appears to be varying success rates for this, what precautions should I take to ensure I don't make my system die?

---

### Post by nolove_nomarry on 2007-11-13
many thanks

---

