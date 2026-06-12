---
title: "How to reinstall fglrx Driver (9.10) via terminal?"
date: 2010-03-14
forum: Multimedia Software
---

### Post by zzyzx1 on 2010-03-14
Hello,

Well, i was having issues with xscreensaver, desktop background and VLC all cutting out at same or different times and narrowed it down to "possibly" compiz or the FGLXR ATI driver that was recommended for my ATI HD3200 card. So, without knowing better, i went into hardware settings and removed the proprietary driver and did a reboot thinking the system would come back up and default back to a vanilla driver. No dice. Hello white screen of death! So, i am assuming that I can just reinstall via terminal and life will be good again? 

So, looking for CLI commands via terminal for reinstall.. (if possible) Otherwise some better advise!

Cheers!

---

### Post by RedSingularity on 2010-03-14
So you want a command to install the driver?

How about.....

sudo apt-get install xorg-driver-fglrx

---

### Post by zzyzx1 on 2010-03-14
Thanks, I found this thread and thought i would try my luck with the ATI drivers instead... i feel a complete system reload coming up... ;)

[http://ubuntuforums.org/showthread.php?t=1409467&highlight=reinstall+fglrx+Driver+terminal](http://ubuntuforums.org/showthread.php?t=1409467&highlight=reinstall+fglrx+Driver+terminal)

---

### Post by RedSingularity on 2010-03-14
Can you even get to your xorg.conf file?

---

### Post by Yellow Pasque on 2010-03-14
Just get rid of all the proprietary stuff you installed and start clean: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by zzyzx1 on 2010-03-14
sure, i can navigate so-so via term (ctl-alt-F1) but dont know how to get an editor, and i can even use sys disk to get in and mount the hd.

---

### Post by zzyzx1 on 2010-03-14
[QUOTE=Temüjin;8968404]Just get rid of all the proprietary stuff you installed and start clean:

Yes, did that (i think it took)

---

### Post by Yellow Pasque on 2010-03-14
Huh? So what's your current status?

---

### Post by zzyzx1 on 2010-03-14
Sorry, i followed dome threads that basically cleaned out/removed any residue from the proprietary drivers and basically sets you up for a clean install of the ATI Linux flavor of the HD3xxx driver. I have it on the Desktop now, I'm in terminal, getting ready to launch the installer....

---

### Post by zzyzx1 on 2010-03-15
Problem solved. The above link worked and the ATI drivers loaded perfectly. Now I will move on to see if I still have the other issues that I was having in a post I did called "memory leak?" in the Newb section.

It would be nice, though, if the Ubuntu folks added a (WARNING) disclaimer next to uninstall proprietary driver button! 

Thanks!

---

