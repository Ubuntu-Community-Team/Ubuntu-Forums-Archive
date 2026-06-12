---
title: "Totem color problem"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by 67GTA on 2007-03-06
I am getting a weird color when I play movie clips in Totem. People are blue, or have green lips. I tried to change using edit>preferences>display> adjusting the color sliders, but could not get the right colors. I am using totem-gstreamer with every plugin I could find in synaptic package manager. Anyone know why this is happening?

---

### Post by gameman12 on 2007-03-15
i have the same problem...need help too

---

### Post by adrianj on 2007-03-15
Dito.

Totem renders red as blue. Playing video files in VLC pose no colour problem. Even my webcam video capture through camorama is affected.

I am using Feisty kernel 2.6.20.10 and an ATI X1600 Mobility Radeon card.

Problem with Totem codecs?

Adrian

---

### Post by wieman01 on 2007-03-15
Not sure what the exact problem is but I used to have a similar issue. For some reason Kaffeine (KDE) did the job for me and after a while the problem with Totem mysteriously disappeared. Suggest you check out Kaffeine if you have a minute.

---

### Post by db9s on 2007-03-25
didn't work, :( 
i'm using the prpreitory ati drivers, may its got its got something to do with that?

---

### Post by hanzomon4 on 2007-03-25
> **db9s said:**
> didn't work, :( 
i'm using the prpreitory ati drivers, may its got its got something to do with that?

Nope I'm have a nvidia card with the same problem, so it's a totem problem not a driver problem.

---

### Post by hanzomon4 on 2007-03-26
It's a xine issue in my case

---

### Post by Kuoi on 2007-04-06
I had the same problem , and after installing Totem-Xine (in the Synaptic repos) , the colours are OK .
You have to reboot your computer first , after installing Totem-Xine !

Hope this helps , Kuoi

---

### Post by Nikusan on 2007-05-17
**Blue hue in gstreamer fix: [http://www.mikesplanet.net/2007/05/im-so-blue/](http://www.mikesplanet.net/2007/05/im-so-blue/)**

---

### Post by apricode.net on 2008-02-27
Hi all to resolve the totem's colors problem you should first uninstall  totem-gstreamer, you do it like:
[COLOR="Green"]
sudo apt-get remove totem totem-gstreamer ubuntu desktop[/COLOR]

if you have totem-xine let it how it is, if you don't have it install from Synaptic Package Manager

So, in Synaptic Package Manager you should have this 3 items refering to totem:

[COLOR="Green"]totem[/COLOR]
[COLOR="Green"]totem-mozilla[/COLOR]
[COLOR="Green"]totem-xine[/COLOR]

Reboot the computer then i hope it works.

---

