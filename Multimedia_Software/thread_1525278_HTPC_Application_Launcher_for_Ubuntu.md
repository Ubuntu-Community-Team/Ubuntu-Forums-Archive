---
title: "HTPC Application Launcher for Ubuntu"
date: 2010-07-06
forum: Multimedia Software
---

### Post by fogNL on 2010-07-06
I'm in the process of setting up my Zotac Mag HD to be my media centre platform for my 40" hdtv.  The system is now configured for XBMC using the nice XCI script that was available over on the XBMC forums.  The problem for me now is that I would like to run more than just XBMC on the system.  I want to make the system almost fully controllable by my media center most of the time (unless i'm using web browser).

Along with XBMC, I have a need for Boxee, HuluDesktop and a web browser (more than likely Firefox).

What I'm looking for, is some sort of program launcher that will start when the HTPC boots, and it will allow me to choose between XBMC, Boxee, Hulu and Firefox, and be controllable by LIRC.  So far, I haven't been able to find anything that suits this, and am considering learning how to do it myself if I knew where to start.

So, does anyone have any ideas what I could use?

Currently, the system boots up, and it starts the xbmc-live service that starts X with XBMC running.

---

### Post by cwgtex on 2010-08-31
I am looking for a similar solution.  So far the best solution I come up with is to find a dock with large icons.  I also thought about just putting very large icons on the desktop, but I don't know if I will easily be able to scroll through them with LIRC and my remote.

I just finished building my HTPC yesterday, and I'm going to install ubuntu tonight.  Anyone have any more suggestions?

---

### Post by tripmix on 2010-08-31
I don't know if this is exactly what you want but have you tried irexec? It can be configured to launch and shutdown anything you want. I'll give a simple example showing how I start xbmc with the remote.

/home/user/.lircrc
```
begin
remote = HP_Pavilion
button = KEY_PROG2
prog = irexec
config = /home/user/.mediacenter
repeat = 0
delay = 0
end
``` 
/home/user/.mediacenter
```
#!/bin/bash
DISPLAY=:0.1 xbmc &
```
This last one I called .mediacenter is just a bash script that can be configured to do almost anything, for example
```
#!/bin/bash
killall xbmc.bin &&
exec boxee &
```

---

