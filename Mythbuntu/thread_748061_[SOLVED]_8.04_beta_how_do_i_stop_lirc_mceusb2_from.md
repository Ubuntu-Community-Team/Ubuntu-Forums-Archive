---
title: "[SOLVED] 8.04 beta: how do i stop lirc_mceusb2 from loading?"
date: 2008-04-07
forum: Mythbuntu
---

### Post by arjay1 on 2008-04-07
I am running mythbuntu 8.04 beta with a MS pvr150mce card, and the newer MCE remote/receiver.  All works fine except I want to try and get my remote Microsoft keyboard to work as well.  I am nearly there but have this problem:

I need to be able to stop the lirc_mceusb2 module from loading and load, instead, the lirc_mod_mce module.  I have got the second loading OK by entering it in /etc/hardware.conf.  However, I cannot seem to stop the lirc_usb2 one from loading.  This means I have to manually rmmod it at each boot, and then reload the other module.

Can someone help me with how to stop the usb2 module from loading?

Thanks

---

### Post by prshah on 2008-04-07
> **arjay1 said:**
> 
I need to be able to stop the lirc_mceusb2 module from loading and load, instead, Can someone help me with how to stop the usb2 module from loading?


Add the line ```
blacklist lirc_mceusb2
``` to your /etc/modprobe.d/blacklist file

---

### Post by arjay1 on 2008-04-07
Thnx for the quick reply.  I'll give it a go and report back

---

### Post by arjay1 on 2008-04-07
> **prshah said:**
> Add the line ```
blacklist lirc_mceusb2
``` to your /etc/modprobe.d/blacklist file

OK - tried this and it did not work but I found probably why that is.  I am using a microsoft remote which needs lirc_mceusb2.  This is loaded automatically by mythbuntu's MCC.  So I can disable this by choosing "none" for the remote.  Unfortunately this, of course, disables my remote but allows the MS remote keyboard to function when lirc_mod_mce is loaded instead of lirc_mceusb2!!

Somehow I need to have lirc_mceusb2 load at start up (that enables the remote) then have rmmod unload lirc_mceusb2 (doesn't seem to stop the remote even if I do) then have insmod lirc_mod_mce load the keyboard module again.  When I do this, everything works.

I'll need to look and see if I can write a script or something for this procedure (never done it before) but presume it is possible.

Otherwise it seems I can only have one or the other - need to look into this further.  But thanks anyway for your help.

---

### Post by prshah on 2008-04-07
> **arjay1 said:**
> 
I'll need to look and see if I can write a script or something for this procedure (never done it before) but presume it is possible.


A script is nothing more than a series of commands in a text file. In fact, if you add your modprobe / rmmod commands in the /etc/rc.local, it will execute for you automatically on startup (sort of; read the contents of the /etc/rc.local before you do anything.)

---

### Post by arjay1 on 2008-04-07
> **prshah said:**
> A script is nothing more than a series of commands in a text file. In fact, if you add your modprobe / rmmod commands in the /etc/rc.local, it will execute for you automatically on startup (sort of; read the contents of the /etc/rc.local before you do anything.)

Cool - I'll give it a go.

Thanks again - I'll mark this up as solved

---

