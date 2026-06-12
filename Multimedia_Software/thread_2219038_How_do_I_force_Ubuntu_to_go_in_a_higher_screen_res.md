---
title: "How do I force Ubuntu to go in a higher screen resolution?"
date: 2014-04-22
forum: Multimedia Software
---

### Post by st-berer on 2014-04-22
I've just installed Ubuntu, and I couldn't go higher than 1024 x 768. I've updated my Nvidea GeForce M8600GT's drivers and now he's giving me 1152 x 864 and 1360 x 768 as a extra but not 1920 x 1200.

I have tried to do the xrandr command-line, but with no success because "--addmode VGA1" isn't working for me. I think the vga port is called somthing else, but I don't know how to check...

Any ideas?

---

### Post by jbaerboc on 2014-04-22
Maybe this is a too basic of a question but have you used that monitor/vid card setup on 1920 x 1200 resolution before [on another linux setup or windows setup]? On my computer with Ubuntu and a Nvidia 9600 GT card it gives me a max resolution of 1920 x 1080 [happens to be max for my monitor and card setup so works out for me].

---

### Post by st-berer on 2014-04-23
Yes, well. I have used my computer as well as my monitor on 1920 x 1080 before (not 1920 x 1200 though), But that was on a Windows install. But even 1920 x1080 is apparently too much to ask for ):

---

### Post by PotatoHead007 on 2014-04-23
hey, this should work:
1.   Type: ```
sudo gedit /etc/default/grub
```
2. Locate the line "# GRUB_GFXMODE=800x600" (resolution may be different), then remove the "#" sign, and change the reolution to yours. It should look like this: GRUB_GFXMODE=1920 x 1200.
3. Now type: ```
sudo gedit /etc/grub.d/00_header
``` 
4. Look for the line "gfxmode=${GRUB_GFXMODE}" and add "set gfxpayload=keep" under it, to make it look liek this:
```

set gfxmode=${GRUB_GFXMODE} 
set gfxpayload=keep
```
5. enter this command: ```
sudo update-grub
```
This will generate a new grub config file to save the changes

Now reboot, and it should be fixed :)

---

