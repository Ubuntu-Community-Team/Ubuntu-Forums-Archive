---
title: "Support for the intel G43 chipset"
date: 2008-09-07
forum: Multimedia Software
---

### Post by mjcarr01 on 2008-09-07
I helped a friend put together a computer today, the motherboard has an intel G43 integrated graphics chip.  

I have searched quite a bit but do not see much information as to when this chip will be supported in the xorg "intel" driver.  Right now I am stuck using vesa defaults on 800x600.

Anyone else using the G43 or G45 chipsets?  Anyone found a workaround for at least getting some support?

Below are the relevant sections of the xorg.conf if it helps:

```
Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection

```

---

### Post by overdrank on 2008-09-07
> **mjcarr01 said:**
> I helped a friend put together a computer today, the motherboard has an intel G43 integrated graphics chip.  

I have searched quite a bit but do not see much information as to when this chip will be supported in the xorg "intel" driver.  Right now I am stuck using vesa defaults on 800x600.

Anyone else using the G43 or G45 chipsets?  Anyone found a workaround for at least getting some support?

Below are the relevant sections of the xorg.conf if it helps:

```
Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        Busid           "PCI:0:2:0"
       [COLOR="Red"] Driver          "intel"[/COLOR]
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection

```

Hi and welcome, you are using the intel driver. You may try the command ```
gksu displayconfig-gtk
``` and setup the monitor there.

---

### Post by mjcarr01 on 2008-09-08
> **overdrank said:**
> Hi and welcome, you are using the intel driver. You may try the command ```
gksu displayconfig-gtk
``` and setup the monitor there.

I tried the above command, I was able to set the resolution.  Unfortunately after I restarted X the screen scrambled.  I will have to figure how to set it back without the gui.

Also, I am not seeing any xorg log files created nor do I have any indication that the intel driver is in fact being used, the screen setup from the above command still showed vesa as the driver.

As a side note, my main pc (not the pc in this issue) is running compiz on an ATI X1300.  I can't help but chuckle that I can get that running but can't get an integrated intel to work.

---

### Post by overdrank on 2008-09-08
Ok to correct the graphics then you can try and boot into recovery mode which is usually the second choice from the grub. Then use the xfix option.

---

### Post by mjcarr01 on 2008-09-08
> **overdrank said:**
> Ok to correct the graphics then you can try and boot into recovery mode which is usually the second choice from the grub. Then use the xfix option.

Ok I will try that when I get home today.  What is the best way to see if the xorg is even being used?

---

### Post by mjcarr01 on 2008-09-09
Still no luck with this.  It seems someone may have figured it out in fedora, I will see if I can apply this to Ubuntu.

---

