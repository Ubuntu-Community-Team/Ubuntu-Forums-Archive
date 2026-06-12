---
title: "No microphone input or line in ALSA mixer"
date: 2021-03-10
forum: MINT
---

### Post by fabb12 on 2021-03-10
Hi everyone,

I can't get my microphone to work under Linux Mint. I tried quite a few workarounds with help of the mint community. I'm here cause my trouble might come from the kernell. Alsa never let a line-in or micro appear. 
The Mic works fine under Windows on the same PC.
It does not show any mic pr line-in under Alsa-Mixer.
Under the live ISO it does not work either. 
Fast boot under windows is off. 

This is the PC i use for work, I need the microphone for visiocalls. I'm used to Mint and don't want to go back to windows.

Any help please?

My setup :
Acer Swift 15[COLOR=#FF0040] [/COLOR] [COLOR=#FF0040] | [/COLOR]Linux Mint 20.1 Ulyssa  | Windows 10 [COLOR=#FF0040] |[/COLOR] MATE 1.24.0 [COLOR=#FF0040] | [/COLOR] 5.4.0-65-generic x86_64[COLOR=#FF0040] | [/COLOR] Intel Core i5-8250U[COLOR=#FF0040] | [/COLOR]8Go[COLOR=#FF0040] | [/COLOR]Intel UHD Graphics 620

---

### Post by ajgreeny on 2021-03-10
Install pulseaudio-volume-control (***pavucontrol***) if you have not already got it and open that to see the levels that are set for the mic.

What sort of mic is it, USB, 3.5mm plug, and what make/model?

---

### Post by fabb12 on 2021-03-12
Thanks ajgreeny

> **ajgreeny said:**
> Install pulseaudio-volume-control (***pavucontrol***) if you have not already got it and open that to see the levels that are set for the mic.

I didn't mentioned that I had pavucontrol already. The only hardware port available is "analog entry" and set to 100%. 

> **ajgreeny said:**
>  What sort of mic is it, USB, 3.5mm plug, and what make/model?

I use the build-in mic on the laptop (acer swift 15) and I also try with a very basic sennheiser headset that has previously worked like a charm on other PCs under ubuntu.

---

### Post by ajgreeny on 2021-03-12
What, if anything, does the volume icon on the panel show you?
Normally that has an entry for the microphone as well as the sound output, as shown in my screenshot.

---

### Post by fabb12 on 2021-03-14
> **ajgreeny said:**
> What, if anything, does the volume icon on the panel show you?
Normally that has an entry for the microphone as well as the sound output, as shown in my screenshot.


I'm Sorry but my PrintScreen Module does not work when anything on the taskbar is activated. Anyway, I only have the output button which activates only the output volume control. No entry for Mic show up besides.

[ATTACH=CONFIG]288116[/ATTACH]

Here are shots of my alsa mixer :

[ATTACH=CONFIG]288117[/ATTACH][ATTACH=CONFIG]288118[/ATTACH]

And Pavu Control :
[ATTACH=CONFIG]288119[/ATTACH]

---

### Post by ajgreeny on 2021-03-14
For future reference, to get the print screen to show activated dialogues you need to open the screenshot application, (not just press Print Screen), set a delay of a few seconds then click on the panel applet or whatever it is.

You certainly appear to have a system without a detected microphone but I'm afraid I do not know where you need to go from here.
Have you tried an external mic, either USB or 3.5mm stereo jack plug type?

---

