---
title: "X can't load nvidia kernel module"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by sopordave on 2006-07-07
I tried installing the nvidia-glx as per the HOTWO's in the forums and wiki, but without success.  Nvidia-glx is installed on my system, but whenever my xorg.conf uses "nvidia" as the display driver, X always refuses to start saying that it can't find the nvidia kernel module.  When I change it back to "nv", it starts up, but I want the nvidia driver...

Does anybody have any ideas?  I've tried depmod, and that didn't change anything.

---

### Post by Dr. Nick on 2006-07-07
Were you sure to get the correct Restricted modules package for your kernel?

---

### Post by sopordave on 2006-07-08
Thanks, your response sort of fixed my problem.  I did have the restricted modules installed (amd64-generic), but they weren't working with my amd64-server kernel which boots by default.  once i selected the amd64-generic kernel, it worked.

which brings up more questions: why arent there restricted packages for the -server kernel?  whats the advantage to the -server kernel?  i had to do a server install because teh graphical one on the desktop cd kept freezing so i tossed in the server cd and did a apt-get install ubuntu-desktop.

---

### Post by Dr. Nick on 2006-07-08
Havent played with the server version myself so this may not be totally accurate, but I would imagine that the servers running on the server version do not need the 3d accererated video cards, wireless cards etc.. that are included in the restricted modules.

If you are going to use the gui daily then I would probably stick to the amd64-generic (non server) kernel as it has most likely been more thourghly tested for the average desktop machine.

---

### Post by tseliot on 2006-07-08
> **sopordave said:**
> Thanks, your response sort of fixed my problem.  I did have the restricted modules installed (amd64-generic), but they weren't working with my amd64-server kernel which boots by default.  once i selected the amd64-generic kernel, it worked.

which brings up more questions: why arent there restricted packages for the -server kernel?  whats the advantage to the -server kernel?  i had to do a server install because teh graphical one on the desktop cd kept freezing so i tossed in the server cd and did a apt-get install ubuntu-desktop.
You could have installed Ubuntu in this way:

> 1) you install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

