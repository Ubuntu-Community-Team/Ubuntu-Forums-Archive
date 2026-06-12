---
title: "ATI drivers (HD3200)"
date: 2008-08-13
forum: Mythbuntu
---

### Post by makksjuh on 2008-08-13
.

---

### Post by JugeHuge on 2008-08-13
Hello..

I have Asus M3A78-EMH HDMI which have same onboard graphics.. Drivers doesn't support yet hw decoding but ATI has started to improve their linux drivers.

Sadly those aren't yet acceptable level.. :(

---

### Post by VashTheStampede on 2009-06-12
Could you make it work? I have an ASUS M3A78-EM with the ATI HD3200 and i can't make it work. Not with the propietary drivers, not with the ATI official drivers...can you help me? thanx

---

### Post by JugeHuge on 2009-06-14
I got it working.. No problems.. What kind of problems you are facing??

---

### Post by VashTheStampede on 2009-06-15
I put any driver and after the loading bar the monitor goes "out of range". I look at the xorg.conf file and no matter what i do, it doesn't change at all. It's like basic, no resolutions, no device name, no nothing. I'm loosing it here, i'm a noob and i don't know what else to do now.

I have an ASUS M3A78-EM motherboard with 2 GB RAM, an AMD Phenom 9550 X4, a ViewSonic 19'' VA902b monitor.

---

### Post by JugeHuge on 2009-06-16
So it seems that your monitor doesn't give proper EDID data to detect correct resolution for it..

You could also Google your monitor problems as there seems to be quite much treads about same problem that you are facing.

Could you post /etc/X11/xorg.conf

---

### Post by Mattaus on 2009-06-16
I can't really be much help other than to say that I am currently running an ASUS M4A78-VM with integrated 3200 graphics.

It seems to work fine except I am having a problem at the moment that I will be posting about elsewhere, but I'm pretty sure its not graphics related. But then again I don't really know much yet :p

---

