---
title: "How to open Video file in command line!!!"
date: 2008-06-10
forum: Multimedia Software
---

### Post by d.kusummmanth@gmail.com on 2008-06-10
I heard that the power of Linux is in the Terminal!! So I wanted to know, how to **open Video file( in full screen mode of VLC player) using command line**?

---

### Post by forger on 2008-06-10
it's not vlc, but:
```
mplayer -fs your-file.avi
```

---

### Post by ad_267 on 2008-06-10
```
man vlc
```

> NAME
       vlc, wxvlc, svlc - the VLC media player

SYNOPSIS
       vlc [OPTIONS] [ITEMS]...

DESCRIPTION
       This  manual  page  documents  briefly  the  VLC  multimedia player and
       server.

OPTIONS
       VLC follows the usual GNU command line syntax, with long options start&#8208;
       ing  with  two  dashes  (&#8216;-&#8217;).   For  a precise description of options,
       please use "vlc --help".

       The complete list of VLC options depends on what plugins are  installed
       because  they  automatically  add  their  own  options. Please use "vlc
       --longhelp --advanced" for a complete list of available options.

...
...

```
vlc --help
```

> 
...
Video
  -f, --fullscreen, --no-fullscreen
                                 Fullscreen video output (default disabled)
...


---

### Post by d.kusummmanth@gmail.com on 2008-06-10
> **ad_267 said:**
> ```
man vlc
```



```
vlc --help
```
thx for reminding me about **man**. Silly me!!

---

### Post by Juzilopes on 2012-03-16
Code:
vlc --fullscreen "name of file and its extention" 

eg
vlc --fullscreen "juzicoding crack trick.mp4"

---

### Post by nothingspecial on 2012-03-16
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

