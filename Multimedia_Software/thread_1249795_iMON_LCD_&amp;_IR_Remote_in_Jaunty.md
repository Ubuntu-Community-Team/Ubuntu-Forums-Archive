---
title: "iMON LCD &amp; IR Remote in Jaunty"
date: 2009-08-25
forum: Multimedia Software
---

### Post by Powderking on 2009-08-25
Hi everyone!

I'm running mythbuntu 9.04 AMD64 with kernel 2.6.28-15-generic.

What I'm trying to do is getting my Soundgraph iMON OEM (LCD) ([http://www.soundgraph.com/Eng_/Products/oem3.aspx](http://www.soundgraph.com/Eng_/Products/oem3.aspx)) running.
There are different versions of this hardware. I have the one with ProdID 0038

I couldn't get further than using the pad as mouse. When I try "irw" I get the message "connect: No such file or directory"


Following this guide [https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD) I stuck when I should edit "/etc/modprobe.d/options" because I cant find the correct file.

I followed as well this how to: [http://codeka.com/forums/viewtopic.php?f=3&t=22](http://codeka.com/forums/viewtopic.php?f=3&t=22)
But after "./setup.sh" I get the message: "You will have to use the lirc_imon kernel module."

The same was written here: [http://www.mythtv.org/docs/mythtv-HOWTO-8.html#ss8.3](http://www.mythtv.org/docs/mythtv-HOWTO-8.html#ss8.3)
They told me to edit "/etc/modules.conf" but I got the same problem as above.
I read that this options are now in "/boot/grub/menu.lst".

I really stuck here because I don't know which option to add:
- alias char-major-61 lirc_imon ([http://www.mythtv.org/docs/mythtv-HOWTO-8.html#ss8.3](http://www.mythtv.org/docs/mythtv-HOWTO-8.html#ss8.3))
- options lirc_imon is_lcd=1 ([https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD))



After reading this [http://www.mythtv.org/wiki/Imon](http://www.mythtv.org/wiki/Imon) I should only have "Lirc 0.8.4, configure --with-driver=imon_pad". If I understand it right, it should be enough, choosing "Soundgraph iMON IR/LCD" in the frontend setup. I let it generate dynamic button mappings. The pad works and I can control the mouse but nothing more :(

In the same wiki is written to install "LCDProc 0.5.2 with codeka patch -> configure --enable-drivers=imonlcd". This is the same guide as above. I finished the part for the LCD without error.
I as well did "modprobe lirc_imon is_lcd=1". There is a warning that I don't understand: "WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release."
I have chosen almost all options for LCDs in mythbuntu frontend Utilities / Setup > Setup > Appearance. But there is nothing on the display.
When I try "sudo echo Hello > /dev/lcd0" I get "bash: /dev/lcd0: Permission denied"


I hope someone can help me :)

---

### Post by Powderking on 2009-08-30
Is there anybody with the same configuration / prob?
Or has someone a guess or anything :confused:

---

### Post by jbruck on 2009-08-30
Same Problem
have been able to get most of mythbuntu going except the remote and lcd.  I can live without the lcd but not the remote.  I will keep an eye on this thread.

---

