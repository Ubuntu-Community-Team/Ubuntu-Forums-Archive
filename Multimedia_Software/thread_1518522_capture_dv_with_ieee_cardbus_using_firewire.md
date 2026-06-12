---
title: "capture dv with ieee cardbus using firewire"
date: 2010-06-26
forum: Multimedia Software
---

### Post by JaneDoe23 on 2010-06-26
Im less then a week old on ubuntu and i need some serious help 
Ive read some help and not really to sure how to use the termainal i dont really want to have to use the terminal if not needed but if have to then thats fine

Can anyone help me with this error "raw1394 kernal module not loaded or failure"
thanks in advance greatly appreciated

---

### Post by JaneDoe23 on 2010-06-29
i changed the title not sure if anyone will see that. help please

---

### Post by simonmoon42 on 2010-07-02
I banged my head against this for 20 minutes before I thought to check my bios to make sure ieee1394 is enabled. It wasn't... enabled it and viola! Also, you may want to run through these instructions from Kino...

> In a Terminal, enter 'gksu gedit /etc/modprobe.d/blacklist-firewire.conf'. 
Uncomment (remove the #-character at the beginning of the line) ohci1394, sbp2, dv1394, raw1394, and video1394. Then, comment (add a #-character to the beginning of the line) out the firewire-ohci and firewire-sbp2 lines. Save and Quit gedit. 
Next, run 'sudo update-initramfs -k all -u' and finally reboot. 

Now, when you plugin your camcorder, it should have permission by default (unlike in the past). Vote for this to become the default by indicating that this bug affects you. 

---

