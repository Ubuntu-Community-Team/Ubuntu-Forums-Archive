---
title: "Xbmc"
date: 2008-11-18
forum: Multimedia Software
---

### Post by orela on 2008-11-18
Hello

I have Ubuntu 8.1.
I installed the XBMC.

I installed this program according to its web site instruction.
I have some problems with it:
 - The mouse pointer some times disappears and the GUI stuck...
 - The movies something plays in high speed and i can not  
   change it to play normal speed.
I changed the the visual effects (in the appearance menu)to none.

Please advice.

Thanks

---

### Post by Havel on 2008-11-19
Intrepid is not stable enough. I tried XBMC with it and had to many issues. Went back to hardy. Works flawlessly.

---

### Post by kamitsukai on 2008-11-29
> **orela said:**
> Hello

I have Ubuntu 8.1.
I installed the XBMC.

I installed this program according to its web site instruction.
I have some problems with it:
 - The mouse pointer some times disappears and the GUI stuck...
 - The movies something plays in high speed and i can not  
   change it to play normal speed.
I changed the the visual effects (in the appearance menu)to none.

Please advice.

Thanks

I had this problem with mine if you take a look at the XBMC forums theres a sticky about pulseaudio and such on intrepid...and theres one matty who  posted a couple commands which seem the fix the problem

```
pulseaudio -k
sleep 2
xbmc
pulseaudio -D
```

If you create a new text file on your desktop and paste that into it and then rename it to something Like  "xbmc.sh" without the quotes, then right click -->Properties and then the Permissions tab and then select "allow _e_xecuting of this file as a program" then every time you want to use XBMC click on it and select run from the pop up menu:guitar:

if you google around a bit you could also add this to you menu as well

---

