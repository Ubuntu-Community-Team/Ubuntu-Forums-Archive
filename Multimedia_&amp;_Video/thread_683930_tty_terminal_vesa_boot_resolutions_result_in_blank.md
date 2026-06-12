---
title: "tty terminal vesa boot resolutions result in blank screen (vga=xxx)"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by Peturrr on 2008-01-31
I like to work a lot on the terminal so I use the virtual terminals (tty's) often.Since the standard resolution of the tty's are very low, I decided to change that. 
I remembered that there is a vga=xxx kernel boot option that sets the appropriate resolution. 

After searching for the vesa resolutions I found them in a thread here on the forum. But whatever resolution I enter, all I get is a blank screen. The kernel is booting, and the system after that (I see the HD led working and X starts).
I have the boot splash screen disabled, but even when that one is enabled, all the tty's are blank. No login, no nothing. The splash screen shows though.

My video card is quite new ( Geforce 7600 GS AGP ), so I checked the possible vesa modes:
```
sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.utGobXAbip9
  Hardware Class: framebuffer
  Model: "NVIDIA G73 Board - p508h0  "
  Vendor: "NVIDIA Corporation"
  Device: "G73 Board - p508h0  "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 256 MB
  Memory Range: 0xc0000000-0xcfffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```The problem isn't my videocard apparently, since it does support the vesa modes. 

I also changed the monitor from rgb to dvi connector, but both video card outputs give the same result.

I am out of ideas. Somebody that knows a solution?

---

### Post by Peturrr on 2008-01-31
[Found the solution]("http://ubuntuforums.org/showthread.php?t=577457") on the forums. It appears that the Framebuffer device is not loaded with the kernel. 

To make it work I followed these steps:

  1. sudo nano -w /etc/initramfs-tools/modules and add fbcon and vesafb

  so my /etc/initramfs-tools/modules looks like:
  fbcon
  vesafb

  2. sudo update-initramfs -u -k all -v

  3. sudo nano -w /etc/modprobe.d/blacklist-framebuffer
  change the line "blacklist vesafb" to "# blacklist vesafb"

  4. reboot and everything is fine

---

### Post by H_Plow on 2008-02-03
UBUNTU Gutsy 7.10 AMD 64 Desktop
Kernel 2.6.22-14 (and 2.6.20.3-custom..)
Sapphire Radeon HD2600XT PCI-E 256MB
ATI fglrx 8.1 installed and working
Compiz installed and working

This trick works for me using "radeonhd" drivers (Tormd Volden open driver..)..."vesafb driver trick" allowed me to see tty when vga=XXX parameter is passed into kernel line (/boot/grun/menu.lst). BUT ONLY WHEN X WAS CONFIGURED TO USE "radeonhd" AND NOT "fglrx" !

When using "fglrx" it doesn't help so much....still TTY not working also with "vesafb" (or any other "frame-buffer" driver..) trick....whenever I try to access a TTY monitor goes black and I'm not able to do anything else: switch to X or to another TTY....PC is almost "hanged"...can only reboot..

Any suggestion?
Thanks

---

### Post by H_Plow on 2008-02-12
Find better solution to any fglrx/ATI problem !!!

SAY "BYE BYE ATI" !!!  :lolflag:

GOOD LUCK !!

---

### Post by analog_G on 2008-03-06
There is a great how-to about tty terminal resolution here:
[http://www.samlesher.com/ubuntu/installing-ubuntu-gutsy-on-an-asus-a7t-notebook-fix-sound-and-tty-terminal-resolution/](http://www.samlesher.com/ubuntu/installing-ubuntu-gutsy-on-an-asus-a7t-notebook-fix-sound-and-tty-terminal-resolution/)
Very similar to the procedure listed above.  This worked for me using a Dell Latitude C640 running xubuntu 7.10 (tty resolution is now 1440x1050)

---

