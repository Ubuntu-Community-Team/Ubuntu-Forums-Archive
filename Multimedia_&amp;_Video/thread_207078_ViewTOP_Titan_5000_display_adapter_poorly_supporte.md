---
title: "ViewTOP Titan 5000 display adapter poorly supported"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by jis on 2006-07-01
I get poor resolution with ViewTOP Titan 5000 display adapter; the desktop does not even have space to show all of its content. Even if I choose 800x600 in display settings, I do not get any better resolution. Also content does not update correctly..

---

### Post by jis on 2006-09-17
I have got better results with display modes, if I boot S-video not connteced. (No more only part of desktop screen visible.) Is this normal with graphics cards that have TV-out? I have also rewritten xorg.conf by running
```
sudo dpkg-reconfigure xserver-xorg
```
(I use a savage driver instead of vesa one, now.)

I installed s3switch from universe, to be able to control S-video output. If I connect S-video later and run 'sudo s3switch crt tv pal' (It's PAL since I am in Finland.) I can get the output to both CRT and TV, but this time it only uses a small part of both screens and that section shows only small portion of the desktop. (Quality of picture in the TV is not as good as it coud be.) When I try to return to normal display state by 'sudo s3switch crt', the TV goes blank, but the CRT gets totally corrupted, displaying some gray characters (most of them blinking); luckily Ctrl+Alt+Backspace helps to get out.

lspci -v shows this for the graphics card:
> 
0000:01:01.0 VGA compatible controller: S3 Inc. 86c794 [Savage 3D] (rev 01) (prog-if 00 [VGA])
        Subsystem: S3 Inc. 86C391 Savage3D
        Flags: bus master, 66MHz, medium devsel, latency 80, IRQ 11
        Memory at d8000000 (32-bit, non-prefetchable) [size=128M]
        Expansion ROM at e0000000 [disabled] [size=64K]
        Capabilities: <available only to root>


I wonder, if the old card has 128M of memory, like the previous output suggests.

xorg.conf Device section is like this: 
```

Section "Device"
        Identifier      "S3 Inc. 86c794 [Savage 3D]"
        Driver          "savage"
        BusID           "PCI:1:1:0"
EndSection
```

Do you have any ideas how to use the TV-out feature better in this system?

---

### Post by jis on 2006-09-17
I have to add that the mode in the login screen of Xubuntu is not good; it shows only part of the screen, but I can scroll the screen by mouse. This happens even if S-video is not connected during boot and when 1024x768 mode is selected for the login screen. There are these modes in x.org screen section:
```

SubSection "Display"
 Depth     24
 Modes     "1024x768" "800x600" "640x480" "1400×1050" "1600x1200" "1152x864"
EndSubSection

```
(for each bit depth).

---

