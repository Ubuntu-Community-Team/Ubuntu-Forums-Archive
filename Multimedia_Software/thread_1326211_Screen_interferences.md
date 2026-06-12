---
title: "Screen interferences"
date: 2009-11-14
forum: Multimedia Software
---

### Post by -Ziggy- on 2009-11-14
Hello.
My problem is that I have annoying screen interferences such as moving parallel lines, similar to the ones you have when a TV program is codified. I don't know why did this happened, I've been using Ubuntu for a week or so for the first time, and this problem appeared two or three days ago, without having made nothing but the usual things in my computer (internet, email, messanger, openoffice, torrents, etc.).

My monitor is a BenQ FP222WH, 22 inches, and my video card is an ATI HD 3870. I've chcked the screen resolution and so with ATI Catayst Control Center and I have 1680x1050 and 60Hz. I tried to change the refresh rate with Catalyst but I couldn't, it just leaves me to set it at 60Hz, although my monitor's maximum is 75Hz. 

I've checked my xorg.conf file and it looks like this:

> 
Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
    Option        "SHMConfig" "true"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSectionWhat can I do to solve this problem? I'd really thank you if you explained it in an easy way, as I'm a newbie in Ubuntu.
Thanks in advance.

---

### Post by -Ziggy- on 2009-11-14
I forgot to say that I also have another video card that I don't use now, it's a nVidia 8400GS, will it be wise to change it?

---

### Post by -Ziggy- on 2009-11-14
> **-Ziggy- said:**
> I forgot to say that I also have another video card that I don't use now, it's a nVidia 8400GS, will it be wise to change it?

Forget what I've said because I can't find the damn video card.
Can anybody help me please?

---

