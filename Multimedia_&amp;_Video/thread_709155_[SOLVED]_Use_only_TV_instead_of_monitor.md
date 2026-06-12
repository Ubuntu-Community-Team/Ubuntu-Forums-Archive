---
title: "[SOLVED] Use only TV instead of monitor"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by prshah on 2008-02-27
Hello all,

I have a couple of old machines which I want to connect to the TV. One runs Xubuntu (P3550/384Mb/8Gb/ATI8Mb Rage) and the other Kubuntu (P3500/320Mb/20+10Gb/SiS 6326 8mb)

In both machines, I have connected only TV to the composite tv out of the display card (no monitor). 

When booting, both machines display bios screen, grub select screen etc on the TV. But the display goes blank when the startup graphic appears (with status bar). However, I can switch to virtual console 1 (ctrl+alt+f1) and continue working, but no X interface.

What to I have to do in either/both to get X to display on the TV?

Many many howtos and guides exist for Nvidia TV out, but cannot find anything for SiS.

Also these are usually dual-head (multi-display) configs, I want only TV (no monitor).

My ultimate long term aim is to turn these two into super-set-top-type multimedia boxes.

Advise, tips, pointers and useful insults (haven't you come across "atitvout" in your braindead existence?) welcome.

Cheers,
PRShah

---

### Post by Sam Lars on 2008-02-27
If you do a
```
sudo dpkg-reconfigure xserver-xorg
```
with the TV hooked up, does it get you a configuration that works?

---

### Post by prshah on 2008-03-01
Been there, done that. Problem is I dont know what settings to choose for refresh rates for television. I tried Simple->14" monitor and Medium->800x600@60Hz but no ice. Apparently, for TV out, I have to add certain TV settings lines to the Xorg.conf... still researching that issue.

Cheers,
PRShah

---

### Post by steefjeqv on 2008-03-02
Hi,

If you've got a bit of soldering skills, then you can make your own vga to scart (rgb) cable.

Simplest version is the ATI vga to scart  (rgb) cable.

[http://www.idiots.org.uk/vga_rgb_scart/]("http://www.idiots.org.uk/vga_rgb_scart/")

[http://www.avforums.com/forums/showthread.php?t=136811&page=1&pp=15]("http://www.avforums.com/forums/showthread.php?t=136811&page=1&pp=15")

Greetings,
Steven

---

### Post by prshah on 2008-03-03
OK Got it!

I made the changes as recommended in [http://www.winischhofer.eu/linuxsispart1.shtml#23](http://www.winischhofer.eu/linuxsispart1.shtml#23) .

For quick reference:

    * for PAL: PAL800x600, PAL800x600U, PAL720x540 and PAL640x480
    * for NTSC: NTSC640x480, NTSC640x480U and NTSC640x400

Just place these modes in the Screen section of your XF86Config(-4)/xorg.conf, for example as follows:

  Section "Screen"
  ...
    SubSection "Display"
      Modes ... "PAL800x600" "PAL720x540" ...
  ...

I removed everything else in the Modes line and replaced it with "PAL800x600".

The I tried restarting the X server by pressing Ctrl+Alt+BkSp in relevant terminal. The screen flickered for a few seconds, and then the system shutdown! No idea why, but everything was OK when restarted, including X.

Thanks to above link.

Cheers,
PRShah


> **prshah said:**
> Hello all,

I have a couple of old machines which I want to connect to the TV. One runs Xubuntu (P3550/384Mb/8Gb/ATI8Mb Rage) and the other Kubuntu (P3500/320Mb/20+10Gb/SiS 6326 8mb)

In both machines, I have connected only TV to the composite tv out of the display card (no monitor). 

When booting, both machines display bios screen, grub select screen etc on the TV. But the display goes blank when the startup graphic appears (with status bar). However, I can switch to virtual console 1 (ctrl+alt+f1) and continue working, but no X interface.

What to I have to do in either/both to get X to display on the TV?

Many many howtos and guides exist for Nvidia TV out, but cannot find anything for SiS.

Also these are usually dual-head (multi-display) configs, I want only TV (no monitor).

My ultimate long term aim is to turn these two into super-set-top-type multimedia boxes.

Advise, tips, pointers and useful insults (haven't you come across "atitvout" in your braindead existence?) welcome.

Cheers,
PRShah

---

