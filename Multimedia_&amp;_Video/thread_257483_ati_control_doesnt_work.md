---
title: "ati control doesnt work"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by buckskinmike on 2006-09-14
ok i tried many different methods to get my ati drivers installed none of which worked. i finally came to a script on this forum which installed without any problems.

"mike@Mike:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.6011 (8.28.8)"

when i try to run the ati control i get an error saying 
"driver does not provide the firegl x11 extensions!
panel components will operate only partially"

then i press ok and it opens the control panel and it only lists my card info, it doesnt give me any options or any settings i can change. anyone know how i can fix this?

---

### Post by mobilehavoc on 2006-09-14
I have the same problem...I'm using Ubuntu stock ATI FGLRX drivers (8.25.18) and I get the same error. No clue what the problem is. I'm also using XGL via GDM and Compiz.

---

### Post by gfd on 2006-09-18
I have the same problem too, but it only occurred after I installed XGL/Compiz.

Now, I don't really know whether trying to fix this, will mess up everything else.
If someone could advise us as to the ways we can handle this, it'd be great.

I also found a [thread]("http://ubuntuforums.org/showthread.php?t=239229&page=3&highlight=extension+%22XFree86-DRI%22+missing+display") where Dropknee suggested unistalling the gcc-4.0 and using gcc-3.4 instead, following fitzman49's [how to]("http://ubuntuforums.org/showthread.php?t=204910&highlight=extension+%22XFree86-DRI%22+missing+display").
Will this help us too??

If someone could advise us as to the ways we can handle this, it'd be great.

fglrxinfo gives me this:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

Everything works without a problem so far, apart from the ATI control panel
which shows this:
```
driver does not provide the firegl x11 extensions!
panel components will operate only partially
```

Now, I know that the control panel doesn't provide a lot of extra features/functinality but I it was the only place where I could tweak my RGB profile - I'm on a laptop and the default is awful.

---

