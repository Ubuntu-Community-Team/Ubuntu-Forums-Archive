---
title: "mutil monitor setup, cannot move"
date: 2011-01-18
forum: Multimedia Software
---

### Post by qwertyjjj on 2011-01-18
I have 3 monitors from left to right:
1: dvi
2: vga
3: usb displaylink

By default, the main ubunut screen shows up on the left #1 monitor.
I tired swapping these around, ie going 213 but that messes it up. Is there a way to change the main listing|+menus to screen 2, which ius my middle screen? In Windows, this would be called the primary desktop.

Secondly, how do I get screen 3 to work. Does it need a displaylink adapter for Linux?

Thanks

---

### Post by qwertyjjj on 2011-01-20
anyone?

---

### Post by BicyclerBoy on 2011-01-20
This can be done (attempted) in the /etc/X11/xorg.conf by changing the server layout section.

Do you have this file on your system ? else you need to create it...

---

### Post by qwertyjjj on 2011-01-20
> **BicyclerBoy said:**
> This can be done (attempted) in the /etc/X11/xorg.conf by changing the server layout section.

Do you have this file on your system ? else you need to create it...

I will have a look but what do I need to change in the file?
Will it also support a USB displaylink monitor because at the moment the displaylink monitor does not show up as a screen option.

---

### Post by qwertyjjj on 2011-01-20
> **BicyclerBoy said:**
> This can be done (attempted) in the /etc/X11/xorg.conf by changing the server layout section.

Do you have this file on your system ? else you need to create it...

I will have a look but what do I need to change in the file?
Will it also support a USB displaylink monitor because at the moment the displaylink monitor does not show up as a screen option.

---

### Post by BicyclerBoy on 2011-01-20
Don't be concerned if the /etc/X11/xorg.conf does not exist.

If you are using an nvidia video card you can just run the nvidia-settings GUI & make one.
AFAIK You can create one from reconfiguring Xorg but this requires the X server to be stopped.

Could be easiest to just make a simple one but you need to know some basic facts about your hardware.

Did you ever have 2 monitors working ?
Run this configuration & then post the
/var/log/Xorg.0.log
file..

I know nothing about the USB device.

---

