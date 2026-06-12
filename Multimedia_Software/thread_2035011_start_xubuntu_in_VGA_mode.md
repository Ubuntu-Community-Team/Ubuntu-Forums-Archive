---
title: "start xubuntu in VGA mode"
date: 2012-07-29
forum: Multimedia Software
---

### Post by linopinolino on 2012-07-29
Hi Guys
I just installed Xubuntu 12.04 on my new machine a ThinkPad a22p 12 years old (or maybe more) with a 16bits 800x600 screen.
I see the video "duplicated". I managed to solve the problem with the life version running on a CD by using the argument VGA=788, but in the installed version I do not manage to get solved.
This is what I done with no success:
Edit the boot parameters in /etc/default/grub
uncomment GRUB_GFXMODE=800x600
I also added a line VGA=788

I edited the grub command at boot adding vga=788

no results

thanks for help!

Lino

---

### Post by steeldriver on 2012-07-29
did you remember to run update-grub after? otherwise the changes to /etc/default/grub don't actually get written to the grub config

```
sudo update-grub
```

---

### Post by linopinolino on 2012-07-29
Hi Steeldriver,

thanks for thi hint I did forgot to do it but it does not solve the proble. I see correctly the sceen until the first splash screen, than is duplicated... grrr

Lino

---

### Post by linopinolino on 2012-07-31
Hi guys, at the end it was pretty easy, I just had to ad a xorg.conf file like this one> Section "Device"
        Identifier      "Configured Video Device"
	Driver           "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
SubSection "Display"
    	Viewport	0 0
    	Depth		16
    	Modes		"1024x768"
    EndSubSection
EndSection

I tried with vesa driver, nobody can suggest me a better driver for a ATI Mobility M3  (16 MB)?

Thanks

Lino

---

### Post by QIII on 2012-07-31
That chip is no longer supported by the proprietary driver, so continue to use the default driver.

---

### Post by linopinolino on 2012-08-01
Thanks

L.

---

