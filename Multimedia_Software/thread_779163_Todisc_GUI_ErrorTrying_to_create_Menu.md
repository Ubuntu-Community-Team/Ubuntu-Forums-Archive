---
title: "Todisc GUI Error:Trying to create Menu"
date: 2008-05-02
forum: Multimedia Software
---

### Post by Dark Aspect on 2008-05-02
I am trying to create a DVD menu with the todisc GUI but I am getting an strange error when I run it:

```
Running: 
sox /tmp/todisc-work.1/intro.wav /tmp/todisc-work.1/intro-processed.wav fade t         1  1
sox soxio: Failed reading `/tmp/todisc-work.1/intro.wav': unknown file type `auto'
mv: cannot stat `/tmp/todisc-work.1/intro-processed.wav': No such file or directory
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
todisc encountered an error:

Check the contents of /home/administrator/todisc.log to see what went wrong.
See the tovid website (http://www.tovid.org) for what to do next.
Sorry for the inconvenience!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
```

It appears to mess up when creating the intro but I haven't even entered a intro since I didn't want one.Can I disable the intro and make tovid go straight to the menu?

BTW:I can't use DeVeDe because it creates a 4:3 ratio menu and I was trying to create a 16:9 wide screen Menu.

---

### Post by grepster on 2008-05-18
> sox soxio: Failed reading `/tmp/todisc-work.1/intro.wav': unknown file type `auto'

Install libsox-fmt-all package.  Sox has recently been split into many sub packages.

grepster

---

### Post by grepster on 2008-05-18
> BTW:I can't use DeVeDe because it creates a 4:3 ratio menu and I was trying to create a 16:9 wide screen Menu

Same thing for todisc actually.  It may have been possible in 0.31 to create one, but it was not really by design.  For 16:9 menus it would require another set of hightlight/select pngs at different locations, which todisc has not yet implemented.  For svn todisc, it has been hard coded that menus are always 4:3.

See this thread for a possible workaround:
[http://groups.google.com/group/tovid-users/browse_thread/thread/56466cef7413793/6a5bde21e0b01c43?lnk=gst&q=widescreen#6a5bde21e0b01c43]("http://groups.google.com/group/tovid-users/browse_thread/thread/56466cef7413793/6a5bde21e0b01c43?lnk=gst&q=widescreen#6a5bde21e0b01c43")

grepper

---

