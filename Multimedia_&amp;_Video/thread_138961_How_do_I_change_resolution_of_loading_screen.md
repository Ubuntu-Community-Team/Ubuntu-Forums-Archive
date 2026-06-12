---
title: "How do I change resolution of loading screen"
date: 2006-03-02
forum: Multimedia &amp; Video
---

### Post by BiggerBadderBen on 2006-03-02
I just installed Breezy on a brand new Dell Dimension 5150 with an ATI X300 PCIE card and a Dell 1907 LCD.  Ubuntu detected the video card, and chose the the 'ati' driver for X.  Using either VGA or DVI inputs to the monitor, I wasn't able to get X started.  Changing the driver to 'radeon' did the trick, and now X starts up fine.  There may be a better driver to use, but I haven't had any 3D needs yet and probably won't any time soon.  Anyway...  here's the problem:  When using the DVI input, the Dell BIOS displays fine, and the login and X screens come up OK.  The part in between, though, when Linux is loading and verbosely stating its status, uses screen settings that this monitor doesn't support (a message on the screen states that this is an unsupported resolution).  Everything displays when I use the VGA input, but I have other plans for that one.  Does anyone know how to configure the resolution and refresh rates of the loading screen, or is it hard-coded?  Not a big issue, as long as there are no problems loading, but life doesn't alwasy work out that way!

---

### Post by quonsar on 2006-03-03
you can change this by adding a vga=xxx to the kernel line in /boot/grub/menu.lst. 

```
sudo gedit /boot/grub/menu.lst
```

scroll down until you see some lines like this:

```
title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot
```

on the end of the line that starts with 'kernel', add the parameter 'vga=xxx' (get the value of xxx from [this table]("http://www.ubuntuforums.org/showpost.php?p=670508&postcount=2"). i use 792 to get 1024x768 in 24-bit color, you may require something else. find your resolution in the table and use that number.

now the line will look similar to this:

```
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash vga=792
``` 

save the menu.lst file. next time you boot your loading screen should be at the resolution you chose.

---

### Post by Parkotron on 2006-03-03
The usplash screen that you're refering to normally runs at a very low resolution with a very low number of colours. I've never heard of a monitor not supporting settings that are too low, but I guess that might be what's happening.

Anyway, to run that screen at a different resolution you'll need to edit Grub's menu file. I don't know how familiar you are with Linux so I'll assume nothing:
[list=1][*]Open the grub configuration file for editing as root by typingthe following on the command line.```
sudo gedit /boot/grub/menu.lst
```

[*]Find the main kernel entry. It should probably look something like following, but the kernel version and hard drive used will probably be different.```
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
```

[*]Add **vga=###** to the end of the kernel line, where **###** is taken from the table below. 792 seems to be a popular choice.```
 Colours  Depth  | 640x480  800x600 1024x768 1280x1024
---------------------------------------------------------
     256   8bit  |   769      771      773      775
   32768  15bit  |   784      787      790      793
   65536  16bit  |   785      788      791      794
16777216  24bit  |   786      789      792      795
```

[*]Save and close the file, then reboot your computer.
[/list]

I have no idea if this will actually fix your problem, but it's the only thing I can think of. Good luck.

---

### Post by Parkotron on 2006-03-03
quonsar, you beat me to it. I guess that's what I get for not replying right away. I started a reply got up and made some hot chocolate and came back to finish it. That'll teach me to dilly-dally.

---

### Post by quonsar on 2006-03-03
hahaha! i was wondering... i just said that! :-k

---

### Post by BiggerBadderBen on 2006-03-03
Thanks guys!  Works like a charm!

Ben:)

---

