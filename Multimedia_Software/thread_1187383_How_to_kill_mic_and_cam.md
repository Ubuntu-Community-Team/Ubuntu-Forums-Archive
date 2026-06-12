---
title: "How to kill mic and cam?"
date: 2009-06-14
forum: Multimedia Software
---

### Post by praystation on 2009-06-14
Hi forums,
(hope this does not appear twice, browser problem).

I have a problem with a laptop with mic and cam. I do not want these things. In the preinstalled windows (left for some 3d applications not working in linux) I could just remove the drivers for cam and mic.
(I also taped the cam with black tape).
In ubuntu I followed a more stupid approach. I went System->Preferences->Sound and assigned "silence" to the capture device. Also I muted and zero-volumed what I could find in the volume control. So it was all good for soundrecorder.
However in the meanwhile I assume this is foolish because the capture device I guess one can just bypass by selecting another device and also you would not even need to be root to reverse my changes.

Q1: I am a bit  paranoid so would like to know if there is a better way to permanently disable cam and mic in the ubuntu once and for all. Do not like to end on youtube.
Q2: While performing "bypass" experiments I noted that right atm I do not get mic to work at all. Alsa capture device has a red cross mic icon in the volume settings dialoge. I guess this means its logically muted. If I click the icon the red cross goes away but whenever I reopen the volume settings it is back. Any tipps why this refuses my input?

Any hint deeply appreciated. Paranoia is so stressful :)
KR,
Ben

---

### Post by cariboo on 2009-06-14
First off, drop the windows mindset. The only way that someone can control your web cam is if you let them. Ubuntu security starts with using a strong password 10 characters upper and lower case and numbers will do. Don't open any services you don't need. The most often cracked is remote desktop sharing.

To disable your microphone, right click the volume icon in the upper panel and select  open volume control nad mute the microphone.

To disable you web cam find what driver it is using and blacklist the driver. the first thing you have to do id find what make and model of webcam you are using and what driver it uses. Once you have found what driver it uses open gedit as root and add it to the bottom of the list. Press Alt-F2 and type:

```
gksu gedit /ect/modprobe.d/blacklist
```

to edit.

---

### Post by praystation on 2009-06-14
Thank you for the webcam hint.
So just the mic problem to solve.
I have attached an image of the volume controls.
Is this muted? I cannot remove the red x and have no idea why.

While you maybe right, I think it is not a windows linux question any more as we have so many abstraction levels nowadays that these problems are cross platform. For example, shockwave flash stores hidden cookies on your computer and can also access peripherals. So the term "let them access" can be understood in many ways. I find it disturbing that I cannot disable these things in the bios.

---

