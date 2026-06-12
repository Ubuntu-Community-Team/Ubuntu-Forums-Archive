---
title: "Colorful blinking screen instead of tty"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by Fluxid on 2007-04-22
Hi!
I have problem with swithing to any of tty (as i know, it's name is tty... i mean switching to console by pressing ctrl+alt+f1-f6)
When i switch, i get screen with colorfull blinking vertical stripes, but no text or cursor appear...

it happens on both xgl/aiglx, fglrx/radeon..
I'm running Feisty (on edgy and dapper everything was fine...)

Fluxid

---

### Post by punkinside on 2007-04-23
on edgy you could take care of that problem by adding **vga=791** at the end of the boot options in /boot/grub/menu.lst

my default looks like this (yours will be a bit different)

```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro splash vga=791
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

---

### Post by Fluxid on 2007-04-23
Thanks! It's fixed now.. But usplash looks ugly :/
I checked available modes by hwinfo, but i get only these:
```
  Mode 0x0382: 320x200 (+320), 8 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+960), 24 bits
  Mode 0x0320: 320x200 (+1280), 32 bits
  Mode 0x0392: 320x240 (+320), 8 bits
  Mode 0x0393: 320x240 (+640), 15 bits
  Mode 0x0394: 320x240 (+640), 16 bits
  Mode 0x0395: 320x240 (+960), 24 bits
  Mode 0x0396: 320x240 (+1280), 32 bits
  Mode 0x03a2: 400x300 (+400), 8 bits
  Mode 0x03a3: 400x300 (+800), 15 bits
  Mode 0x03a4: 400x300 (+800), 16 bits
  Mode 0x03a5: 400x300 (+1200), 24 bits
  Mode 0x03a6: 400x300 (+1600), 32 bits
  Mode 0x03b2: 512x384 (+512), 8 bits
  Mode 0x03b3: 512x384 (+1024), 15 bits
  Mode 0x03b4: 512x384 (+1024), 16 bits
  Mode 0x03b5: 512x384 (+1536), 24 bits
  Mode 0x03b6: 512x384 (+2048), 32 bits
  Mode 0x03c2: 640x350 (+640), 8 bits
  Mode 0x03c3: 640x350 (+1280), 15 bits
  Mode 0x03c4: 640x350 (+1280), 16 bits
  Mode 0x03c5: 640x350 (+1920), 24 bits
  Mode 0x03c6: 640x350 (+2560), 32 bits
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0383: 640x400 (+1280), 15 bits
  Mode 0x0384: 640x400 (+1280), 16 bits
  Mode 0x0385: 640x400 (+1920), 24 bits
  Mode 0x0386: 640x400 (+2560), 32 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+1920), 24 bits
  Mode 0x0321: 640x480 (+2560), 32 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+2400), 24 bits
  Mode 0x0322: 800x600 (+3200), 32 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+3072), 24 bits
  Mode 0x0323: 1024x768 (+4096), 32 bits

```
(My native resolution is 1280x800)

Is there a way to force system to suport my resolution (any others than kernel reconfiguration and compiling?)

---

### Post by punkinside on 2007-04-27
I don't know if I understood you.. the problem with the resolution is at usplash only?

you'd have to adjust the vga=791 for another number, I can't remember them all right now do a search I remember someone posting a complete list for many resolutions. None of them are widescreen though.

let me see if I can find it quickly. But you might also want to try vga=771, thats what I had when I had a laptop with that resolution back in breezy

If the resolution thing is once in ubuntu, check your xorg.conf

---

### Post by punkinside on 2007-04-27
found the table

 ```
                     
                      640x480  800x600 1024x768 1280x1024 1600x1200
-----------------+---------+--------+----------+-----*----+----------+---------
256 (8 bit)       |   769        771        773          775          796
32,768 (15 bit) |  784        787        790          793          797
65,536 (16 bit) |  785        788        791          794          798
16.8M (24 bit)  |  786        789        792          795          799

```

Play a bit with those numbers, with 1280x800 I would recommend taking them from the 800x600 column.

---

### Post by Fluxid on 2007-04-27
No, you didn't understand me this time ;)
Now it works correctly: both tty and usplash.
I found solution here: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/63558/comments/26](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/63558/comments/26)
This works perfectly.

In the last post in the code frame i pasted vga codes supported by my framebuffer. I didn't have to experiment.
As you can see in line "Mode 0x0317: 1024x768 (+2048), 16 bits" when you convert 0x0317 to decimal, you get 791 ;)
Just `hwinfo --framebuffer`

I was trying to find info about recompiling kernel with full 1280x800 framebuffer support (a hate this LCD blur on other resolutions than native). I found something on gentoo forums ( [http://forums.gentoo.org/viewtopic-t-333300.html](http://forums.gentoo.org/viewtopic-t-333300.html) ) but im too big noob to play with this... (and also commands are diffeerent than on ubuntu/debian...)

---

### Post by punkinside on 2007-04-27
Well, fair play to you then :)  When I had the problem I just started putting in numbers and restarting until I thought it looked good enough!

What vid card are you using? 

And don't be afraid to play... just make sure you back up first!  ;)

---

### Post by Fluxid on 2007-04-27
ATI Radeon Xpress 200M

I'm not afraid that something will crash or something... I don't know just what those configuration thing mean (after make config or something like this...)
I just have to read some good manual about this - on ubuntu wiki isn't much... But now i don't have enough time.

---

