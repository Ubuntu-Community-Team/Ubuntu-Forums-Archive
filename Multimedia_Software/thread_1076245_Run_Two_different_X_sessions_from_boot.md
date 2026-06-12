---
title: "Run Two different X sessions from boot?"
date: 2009-02-21
forum: Multimedia Software
---

### Post by Reeman on 2009-02-21
I am currently running the flgrx on a generic kernel. The reason for this is that I just can't seem to get a 64bit RT Kernel config for the ati drivers cooking. I there a way to have grub load different /etc/X11/xorg.conf files? Or is this something that grub cannot yet pass to the kernel at boot?  One realtime with vesa and the other with the ati driver.

The reason is I do like to run two different monitors for things like GoogleEarth on the big screen in my living room. But need the RT for serious audio work.

---

### Post by markbuntu on 2009-02-21
Yoou can try the xforcevesa option on the grub kernel boot line for the rt kernel but that may not work past the login screen. If you get to the login screen but not all the way to the desktop you can try to login to gnome-safe mode. That should load the VESA driver. 

Here is an example from one of my /boot/grub/menu.lst where you would put the xforcevesa option

title		Ubuntu jaunty (development branch), kernel 2.6.28-8-generic uuid=534a3674-8af0-4fee-8c22-ac3bccc38909
kernel		/boot/vmlinuz-2.6.28-8-generic root=UUID=534a3674-8af0-4fee-8c22-ac3bccc38909 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-8-generic
quiet

You should also add it to the recovery mode section for the rt kernel in case you need to use it.

If you want to run two different x sessions with different drivers on the same card I am pretty sure that is impossible but I guess you are not really looking for that.

For some reason the latest ati driver builds for Ubuntu have left out a patch for the rt kernel. Hopefully that will be fixed in the 9.2 release.

---

