---
title: "Graphic problems: Neither Kubuntu nor Windows wil boot"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by gvendurjaki on 2007-11-12
After Windows crashed while I was testing a USB audio converter (USB 3D sound: [http://www.sourcingmap.com/usb-sound-audio-sound-controller-adapter-gray-p-2967.html](http://www.sourcingmap.com/usb-sound-audio-sound-controller-adapter-gray-p-2967.html)) in Counter Strike Source, I can't boot into my Kubuntu Feisty 7.04 or my Windows XP installations. I don't know whether the USB thingy caused the problem though. More info:

Problem:
[LIST]
[*]There is something seriously wrong with the graphics. Even while booting up and in the BIOS, letters are mangled in text mode (e.g. there are "((" (two parentheses) all over the place) and there are green lines in the dell start up screen and in the boot loader screen.
[/LIST]
[LIST]
[*]When I try to boot either into Kubuntu or Windows, both OSes start loading but then I just get a blank screen. The only way I've been able to boot is through Kubuntu's LiveCD "Safe Graphics Mode".
[/LIST]
[LIST]
[*]I'm running a Dell Inspiron XPS Gen2 with Nvidia GeForce 6800 Ultra.
[/LIST]
[LIST]
[*]I can't do any real testing or problem solving since I simply can't boot into any OS.
[/LIST]

What I've tried:
[LIST]
[*]I've looked up all the forums I know of and googled all I can. Can't seem to find anyone with the same problem.
[/LIST]
[LIST]
[*]I can boot into Kubuntu recovery mode. The display has the aforementioned problem of mangled text and "((" all over the place. Starting the GUI by typing "kdm", "kde" and "startx" from the terminal does not work.
[/LIST]
[LIST]
[*]Choosing "nv", "nvidia", "vesa", and "vga" with: ```
sudo dpkg-reconfigure xserver-xorg
```
[/LIST]
[LIST]
[*]Letting xorg pick settings with: ```
sudo dpkg-reconfigure -fnoninteractive xserver-xorg
```.
[/LIST]
My suspicion is that my Nvidia card is broken since even my Dell boot screen and BIOS come out mangled.

Anyone have any clue about what could be happening?

---

