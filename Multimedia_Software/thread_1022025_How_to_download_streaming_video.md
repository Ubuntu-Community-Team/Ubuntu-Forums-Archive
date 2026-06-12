---
title: "How to download streaming video"
date: 2008-12-26
forum: Multimedia Software
---

### Post by niceguy123 on 2008-12-26
I'd like to download this mms://msmedia.a7.org/arutz7/eng-video/08/dec/banks_interview-final.wmv 

If I left click it and hit "save link as..." it opens a window that allows me to pick viewing it on totem or vlc. and if a run it on one of them I don't see where it's being saved.

---

### Post by niklinux03 on 2008-12-26
Hi,

I would suggest that you left click the wmv video on the website from
which you want to download it. Then choose copy link location
and enter the following in a terminal
```

wget *the link*

```
To paste the link just left click your mouse and
choose "paste".
The program should start the download process in
the directory you started it.
Hope it helps.
Cheers.

---

### Post by pastalavista on 2008-12-26
*wget* won't work with mms//: servers. You can download/install [msdl]("http://sourceforge.net/projects/msdl/"). It comes in a .deb package. Just double-click to install. After installing it, open a terminal and  type (copy/paste)```
msdl mms://msmedia.a7.org/arutz7/eng-video/08/dec/banks_interview-final.wmv 
```The file will be saved in your home folder.

---

### Post by niceguy123 on 2008-12-27
> **pastalavista said:**
> *wget* won't work with mms//: servers. You can download/install [msdl]("http://sourceforge.net/projects/msdl/"). It comes in a .deb package. Just double-click to install. After installing it, open a terminal and  type (copy/paste)```
msdl mms://msmedia.a7.org/arutz7/eng-video/08/dec/banks_interview-final.wmv 
```The file will be saved in your home folder.

Thanks, that is amazing. Can you suggest a simple to use video editor.

---

### Post by DJ_Peng on 2008-12-29
> **pastalavista said:**
> *wget* won't work with mms//: servers. You can download/install [msdl]("http://sourceforge.net/projects/msdl/"). It comes in a .deb package.
Thanks for the link! I was going to have to find an app like that one of these days. You just saved me a nice bit of work.

---

### Post by niceguy123 on 2009-03-08
Now I need msdl for 64 bit. Can someone help?

---

### Post by niceguy123 on 2009-09-14
Now I can't figure out how to download this from the New York Times site:

[http://video.nytimes.com/video/2009/09/13/world/1247464561833/keeping-the-faith-in-homesh.html](http://video.nytimes.com/video/2009/09/13/world/1247464561833/keeping-the-faith-in-homesh.html)

---

### Post by samthjj67 on 2010-03-19
If you want to download streaming video, then you can use the free software "StreamTransport". This post has existed for a long time, I think you have solved the problem.

---

