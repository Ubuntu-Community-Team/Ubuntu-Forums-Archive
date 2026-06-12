---
title: "no good display despite of  X server working fine"
date: 2009-05-07
forum: Multimedia Software
---

### Post by bastienauneau on 2009-05-07
Hi everyone

I have a computer that run different services (ftp, smb, wiki etc...) for the lab at my job. I updated few days ago to 9.04. I found the new version's GUI pretty slow compare to 8.10 (especially when I move around windows, and open couple of them). So I checked the HW with hardinfo and understood I have ATI graphic card. I then installed the new driver from ATI website. Then I couldn't get the display to work after reboot. I followed some how to to install open drivers instead (I did that successfully on my laptop 2 weeks ago) but when trying to remove ati fglrx it says that it is not installed. I guess it's because I installed from the binaries on ATI website. Anyway I spent quit some time installing removing stuff and changing xorg.conf. Now I can connect to the PC using ssh and X fwding, that is why I assume that X is working fine. But I still see no good display on the screen. It actually looks like the start up image with strange colors compressed on the top of the screen and grey and white strips in the rest of the screen. I am pretty clues less now, and I want to avoid to have to re-install the system.

Thanks in advance

---

### Post by bastienauneau on 2009-05-11
No-one ? Maybe I did not explained my problem in a right way or in the right place ?

---

### Post by pro003 on 2009-05-11
How and what driver did you install?

if you have installed both fglrx and the driver from ati's web site then it explains the problem... you should have installed only one of them.

---

### Post by bastienauneau on 2009-05-11
I have installed first the binary from ATI. I got the problem I have now. Then I couldn't figure out how to uninstall it. So I tried with fglrx, did not work neither, then uninstalled fglrx did not work neither.

I guess X server is started properly, I see these deformed images of Ubuntu startup, but I guess it is definitely a driver problem.

---

### Post by bastienauneau on 2009-05-12
Maybe checking things step by step is better ?
_how can I check if X server is working fine ?
   -> [http://www.linuxforums.org/forum/linux-newbie/33019-how-check-if-xserver-running.html](http://www.linuxforums.org/forum/linux-newbie/33019-how-check-if-xserver-running.html)
_how X server is related to the driver ?
_how gnome and X are related (any other things in between all these pieces ?)

---

### Post by bastienauneau on 2009-05-12
I did ps -ef | grep X and no process running. sudo startx fails because of error parsing xorg.conf. So it seems that is the first (and last?) problem.

---

### Post by pro003 on 2009-05-12
> **bastienauneau said:**
> I have installed first the binary from ATI. I got the problem I have now. Then I couldn't figure out how to uninstall it. So I tried with fglrx, did not work neither, then uninstalled fglrx did not work neither.

I guess X server is started properly, I see these deformed images of Ubuntu startup, but I guess it is definitely a driver problem.

did you try this command after you have made any changes to xorg.conf

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or if you have still installed ati's driver, try to get into RECOVERY MODE and run the command in root shell:

```
aticonfig --initial -f
```

---

