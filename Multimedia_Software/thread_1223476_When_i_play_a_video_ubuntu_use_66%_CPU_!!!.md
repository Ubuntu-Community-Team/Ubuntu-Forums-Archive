---
title: "When i play a video ubuntu use 66% CPU !!!"
date: 2009-07-26
forum: Multimedia Software
---

### Post by Vahids on 2009-07-26
i buy a new PC and Power FULL system,
but when i play any video on any player my cpu usage is up 60%
So i have some slow motion in move windows and play videos!

My system:
[LIST]
[*]CPU: AMD Phenom II X3 720 2.8
[*]RAM: 2GIG OCZ 1333
[*]M.B: MSI 790 FX GD70
[*]VGA: ATI Sapphire 4870 Toxic 1G
[*]OS: Ubuntu 9.4 32bit Updated ;)
[/LIST]

Catalys 9.6 is install (for ATI VGA )
no any setting for video codec in this driver ! :(
but i think vga not work when i play video and instead CPU work!
what you think ?
:confused:

---

### Post by martinbaselier on 2009-07-26
What I or anyone else thinks, is not really important. It would be far more interesting to know some facts.

please post the ouput of: 
**glxinfo | grep render**

and /var/log/Xorg.0.log would be interesting to view too.


**top**
will show you which processes use so much cpu.
Ccould you be so kind to provide that information.

---

### Post by Vahids on 2009-07-26
> **martinbaselier said:**
> What I or anyone else thinks, is not really important. It would be far more interesting to know some facts.

please post the ouput of: 
**glxinfo | grep render**

and /var/log/Xorg.0.log would be interesting to view too.


**top**
will show you which processes use so much cpu.
Ccould you be so kind to provide that information.


```
*kabal@kabal-pc:~$* glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Radeon HD 4800 Series 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_copy_depth_to_color,
```

---

### Post by martinbaselier on 2009-07-26
No errors there, as far I can see. I do find the messages about 256 color pallets a bit strange, but it's been a while since I used the ATI driver, so I can't really tell, why that is. 

So which processes use that much cpu when playing video?

as a comparison: I've got a 1,9 GHz centrino and if I play video (with firefox (15 tabs opened), my music player and some other programs opened in the background, it uses about 40% when running on 800Mhz.

---

### Post by Vahids on 2009-07-26
it's XORG!!! see my top output:

> 
2950 root      20   0  439m 121m  31m R   **87**  6.0   5:48.53 Xorg 


87% ~ 90% cpu usage when i play video.

---

### Post by martinbaselier on 2009-07-26
Right click on your desktop, desktop settings. I don't remember which tab. (I believe the most right one.) Try disabling all visual effects to test what difference that makes.

---

### Post by Vahids on 2009-07-26
> **martinbaselier said:**
> Right click on your desktop, desktop settings. I don't remember which tab. (I believe the most right one.) Try disabling all visual effects to test what difference that makes.
Thanks MAN,
NOW, it's working like charm!!! :)

but i like my visual effects :( i used Compiz, i it was so beutiful effects!
is any way to have compiz again ?!

---

### Post by igorzwx on 2009-07-26
When I tried to reenable my effects,
I got a message: "no proper driver was found", 
or something like this.
I can live without, however.

---

### Post by Vahids on 2009-07-26
> **igorzwx said:**
> When I tried to reenable my effects,
I got a message: "no proper driver was found", 
or something like this.
I can live without, however.
but i can Enable Extra Effect But i have Xorg cpu usage problem! ~90 % !!!

---

### Post by martinbaselier on 2009-07-26
You could try experimenting with the settings on that tab. (medium visualization.) and with the compiz effect you have enabled. 

I tend to use as little visual effects as possible. So I can't offer much help there.

---

### Post by igorzwx on 2009-07-26
I made some experiments with Ubuntu 9.10 Alpha 3

sudo killall pulseaudio

top

deinstall pulseaudio

System -> Preferences -> Startup Applications
and disable some of them

reboot

It reduced CPU useage of Xorg essentially

---

### Post by igorzwx on 2009-07-26
there is a long thread about Xorg CPU usage in this forum

---

### Post by martinbaselier on 2009-07-26
[http://ubuntuforums.org/showthread.php?t=1172875](http://ubuntuforums.org/showthread.php?t=1172875)

This seems a useful post.

---

