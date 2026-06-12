---
title: "ibex resetting display resolution on boot"
date: 2009-04-15
forum: Multimedia Software
---

### Post by mxxx on 2009-04-15
hi all


i've got an odd problem happening at the moment with my ibex install. 


i'm running a 22" monitor that natively does 1680x1050, which i can get going fine on nvidia driver 177.82.  i have 1680x1050@ set as the default resolution in my xorg.conf, but for some reason when i boot my system, it initially starts up in 1680x1050, and then switches itself to 1280x1024 just before the boot is completed. 

my xorg.0.log shows no errors putting it in full res, but the very last line of the log always shows 

*(II) NVIDIA(0): Setting mode "1280x1024"*



any ideas as to what might be causing this?  


thanks.

---

### Post by aeiah on 2009-04-15
have you tried messing with nvidia-settings? remember that changes wont be saved unless you run it as root:

```
sudo nvidia-settings
```

---

### Post by mxxx on 2009-04-17
yep, i've run it as root and saved the settings, they're all set properly in xorg.conf, and like i said, it starts with the right resolution and then switches it down again.  

i'm assuming some other process is changing the res to 1280x1024, but i can't imagine what or why.

---

### Post by inobe on 2009-04-17
maybe it has something to do with your driver, the version of ubuntu, and the video hardware.

tell us what you have.

---

### Post by mxxx on 2009-05-16
oops, sorry, forgot i'd posted this here.


i'm running ibex, nvidia drivers 180.11 and the hardware is a 6800XT.

---

### Post by theozzlives on 2009-05-16
um ok lay off the crack.

---

### Post by mxxx on 2009-05-16
probably worth noting too that originally i was using drivers 177, and since upgrading to 180 it's made no difference.

---

### Post by mxxx on 2009-05-16
> **theozzlives said:**
> um ok lay off the crack.

will do.  any suggestion regarding the other problem i'm having though?

---

