---
title: "Black Stripes On Screen"
date: 2009-12-18
forum: Multimedia Software
---

### Post by da_minci on 2009-12-18
:popcorn:
I read that some people are experiencing the same problem as me. The problem og black stripes on the Ubuntu / Kubuntu, that would be an error with the video driver. I've been trying to fix this for over one month now. But still nothing.

Preludium
I had Ubuntu version 8.10 installed on my computer, it worked fine for almost 6 months. Suddently one day, I turn on my computer and Gnome hangs, and shows black stripes on login. I got NO IDEA why this happened, I had not done any update or something. One day it worked, next day not. I have a DELL 6400 Inspirion. Using Video driver from ATI. Card ATI Mobilty Radeon X1300.


What I have learned is:
The problem has to do with the video driver, the stripes are not in Windows. Hence it is not the card. I've also run diagnosis, which tells me that the card is working!
The newest version of Ubuntu and Kubuntu has for some reason, enabled the 3D desktop effects as a default. If I am able to disable these effects I'll may be able to run the system, but it often hangs again. 
I have tried to download, and install the correct driver. But the problem is that there still does not excist a driver that suppert the version of Xserver (7.5). Only up to about 7.4. 

I tried to install Ubuntu 8. This worked fine, because the desktop effects are disabled as default. It installed the driver, but as soon as I tried to enable desktop effects, the system crash. (This has worked before, so I do not understant why the crash!). I tried to run the system but I hangs from time to time.

About 1 & 1/2 month ago, when my system was working. It was fantastic. Never problems, I had ATI driver installed, catalyst worked. Desktop effects worked, Compiz worked. Everything. But for some reason, now nothing works.

Anybody in Ubuntuworld that has experienced the same problem?

(And please do not respond by saying: 
"Have you tried to reset the xorg-conf file back to default". 

I will now try to install Kubuntu 8. I tried the newest version of Kubuntu, not even able to login. 

If this does not work, I will return to Windows and Microsoft. 
- Da minci!

---

### Post by michael37 on 2009-12-18
> **da_minci said:**
> :popcorn:
I read that some people are experiencing the same problem as me. The problem og black stripes on the Ubuntu / Kubuntu, that would be an error with the video driver. I've been trying to fix this for over one month now. But still nothing.

Preludium
I had Ubuntu version 8.10 installed on my computer, it worked fine for almost 6 months. Suddently one day, I turn on my computer and Gnome hangs, and shows black stripes on login. I got NO IDEA why this happened, I had not done any update or something. One day it worked, next day not. I have a DELL 6400 Inspirion. Using Video driver from ATI. Card ATI Mobilty Radeon X1300.


What I have learned is:
The problem has to do with the video driver, the stripes are not in Windows. Hence it is not the card. I've also run diagnosis, which tells me that the card is working!
The newest version of Ubuntu and Kubuntu has for some reason, enabled the 3D desktop effects as a default. If I am able to disable these effects I'll may be able to run the system, but it often hangs again. 
I have tried to download, and install the correct driver. But the problem is that there still does not excist a driver that suppert the version of Xserver (7.5). Only up to about 7.4. 

I tried to install Ubuntu 8. This worked fine, because the desktop effects are disabled as default. It installed the driver, but as soon as I tried to enable desktop effects, the system crash. (This has worked before, so I do not understant why the crash!). I tried to run the system but I hangs from time to time.

About 1 & 1/2 month ago, when my system was working. It was fantastic. Never problems, I had ATI driver installed, catalyst worked. Desktop effects worked, Compiz worked. Everything. But for some reason, now nothing works.

Anybody in Ubuntuworld that has experienced the same problem?

(And please do not respond by saying: 
"Have you tried to reset the xorg-conf file back to default". 

I will now try to install Kubuntu 8. I tried the newest version of Kubuntu, not even able to login. 

If this does not work, I will return to Windows and Microsoft. 
- Da minci!

First of all, install Ubuntu 9.10.  
Then, get rid of xorg.conf file.  You don't need it in new release of Ubuntu.

Owner of Dell Inspiron 6400 with Ati Mobility X1400.

---

### Post by da_minci on 2009-12-18
I know. I ain't got one either;)

---

### Post by michael37 on 2009-12-19
Another thought: you might have a hardware problem in the 3D engine.  The fact that Microsoft Windows work well (which doesn't use 3D graphics) and that Ubuntu without desktop effects work well (which doesn't use 3D graphics) simply means that 2D graphics works perfectly.  

But I would try Ubuntu 9.10 first since it has the best driver for your hardware.

---

### Post by da_minci on 2009-12-19
I have tried Ubuntu 9.10. But it does not work. Still if I disable the desktop effects, it hangs from time to time! :(

But I still have no idea what so ever, how it is possible that the system runs just fine one day, and the next day it does not work what so ever...

---

### Post by michael37 on 2009-12-19
> **da_minci said:**
> I have tried Ubuntu 9.10. But it does not work. Still if I disable the desktop effects, it hangs from time to time! :(

But I still have no idea what so ever, how it is possible that the system runs just fine one day, and the next day it does not work what so ever...

I had experience with a computer which behaved this way.  The problem was overheating.

Try to install gkrellm and [thread="1132923"]enable i8k plugin[/thread] which is a bit trickier on a 64-bit computer.  Ubuntu is notably worse than Windows in controlling temperature of Dell computers.

---

