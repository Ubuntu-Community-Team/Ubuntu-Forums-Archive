---
title: "Still having problems with XFree86-DRI"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by erikcw on 2006-08-25
Hi all,

I followed the Wiki article about setting up the binary driver for my video card. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I tried the ATI driver download first, but that seemed to cause problems, so I over-wrote it with the apt-get version.

> 
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 PRO Generic
OpenGL version string: 2.0.6011 (8.28.8)


I followed the directions for fixing the "Xlib:  extension "XFree86-DRI" missing on display ":1.0"" error on the wiki page, but load "dri" is already in the Module section of xorg.conf.

What else could be causing this error??

Thanks for your help!

Erik

---

### Post by Ziox on 2006-08-25
what do you get from this:

glxinfo | grep direct

?

---

### Post by erikcw on 2006-08-25
> 
$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
direct rendering: No


I'm running Compiz/XGL if that makes a difference.

Thanks!

---

### Post by Ziox on 2006-08-25
> **erikcw said:**
> I'm running Compiz/XGL if that makes a difference.

Thanks!

Yeah I believe it does make a difference, here's an explaination that some one else has given me: [http://www.ubuntuforums.org/showpost.php?p=1405280&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1405280&postcount=5)

---

### Post by rodrigo666 on 2006-08-30
I am getting the same problem here.

If I go to a normal Gnome session, then I get direct rendering from the "glxinfo | grep direct" command and no "Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0"" from fglxinfo.

But when I go for XGL + Compiz, I get that.

---

### Post by Ziox on 2006-08-30
> **rodrigo666 said:**
> I am getting the same problem here.

If I go to a normal Gnome session, then I get direct rendering from the "glxinfo | grep direct" command and no "Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0"" from fglxinfo.

But when I go for XGL + Compiz, I get that.

refer to the link in my previous post

---

### Post by rodrigo666 on 2006-09-01
> **Ziox said:**
> refer to the link in my previous post

The one who I can't reply and say just this?

"Code:
name of display: :1.0

Trust me, under xgl it will tell you that direct rendering isn't enabled. I'll bet $10 that if the user logs into a non-Xgl session glxinfo will say direct rendering: yes. You don't understand how Xgl works. It's basically one big Window that's running ontop of display :0. Display :0 has direct rendering which is what xgl uses. Display :1 doesn't because it's Xgl's internal display surface."

Okay, I got that. I understand that I am all right then.

---

