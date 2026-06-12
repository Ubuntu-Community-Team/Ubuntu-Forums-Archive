---
title: "Bumblebee not working with 3D applications"
date: 2013-05-07
forum: Multimedia Software
---

### Post by Taijitu on 2013-05-07
Hello dear Ubuntuforums

I just came back to ubuntu yesterday after some years without it on my main computer, and was pleased to find that bumblebee was working great with almost no manual setup.

However, after a few hours of minecrafting with my nvidia card, it crashed, and now it does not work any more.

When I try to run either "primusrun glxgears" or "optirun glxgears", the window appears, the gears start turning, but then stop after about one second. The command line still indicates that something is being rendered as can be seen below. This is running for 20 seconds after the animation freezes.

```
xxxx@xxxx:~$ primusrun glxgears 
307 frames in 5.0 seconds = 61.357 FPS
301 frames in 5.0 seconds = 60.067 FPS
301 frames in 5.0 seconds = 60.065 FPS
301 frames in 5.0 seconds = 60.058 FPS

```

Minecraft (Feed the beast) with primusrun just gets a black screen, but minecraft itself seems to be running fine in the background ( the console continues the usual way, but nothing is shown on screen )

glxspheres freezes seemingly in the first frame with optirun and hangs the CPU. Primusrun glxspheres open a window, but the contents of that window is just whatever was behind it when it was opened, and it's frozen and hangs the CPU.

Optirun of anything I can think of that does not require 3D seems to work fine (chromium, gedit, vlc, software center etc), and cat /proc/acpi/bbswitch even says that the Nvidia card is on.

I see no error messages whatsoever in any of the cases. According to the logfiles and console outputs, everything is working.


If you have no idea what could be wroing, I would like to get your opinion on whether this is a hardware issue and if I should contact my dealer. Here are a couple of reasons:

I actually went back to Ubuntu because the Nvidia drivers in windows suddenly started crashing and eventually causing BSODs, ending in a bootloop of system restores that didn't work, and more BSODs. So that gives me a hint that something might be wrong. I also reinstalled Win8, and it seems to be okay with the nvidia drivers for now, but who knows how long that lasts.

I have reformatted my Ubuntu partition and reinstalled completely twice since the issue arose yesterday afternoon, and it does not change anything.

The Intel card works fine for everything; glxgears, glxspheres, minecraft etc.

My laptop is a Lenovo Thinkpad Edge S430 with Nvidia Optimus (HD4000/GeForce620M)

Hope you have some input :-).

And in advance, thanks.

---

### Post by Taijitu on 2013-05-07
Alright, riddle solved: Lenovo support agrees with me that it is probably a hardware fault in the GPU...

---

### Post by marccollin on 2013-05-18
what lenovo firmware do you use? 2.51?
what kernel do you use?

can you  post your

*x**or**g*[COLOR=#444444][FONT=arial].[/FONT][/COLOR]*conf*[COLOR=#444444][FONT=arial].[/FONT][/COLOR][I]nvidia
[/I][COLOR=#333333][FONT=Consolas]bumblebee.conf

file[/FONT][/COLOR]

---

