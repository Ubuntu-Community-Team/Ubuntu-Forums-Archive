---
title: "Drake Graphics Nvidia Acceleration Fullscreen"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by digitalslave on 2006-07-30
i have the latest kernel and 686 nvidia drivers installed. games like quake 3 and enemy territory open in a window instead of fullscreen. i have read that editing the xorg file and adding a 32 bit section would fix this. it appeared to work although after a reboot fullscreen is now broken again.

cedega also fails opengl and 3d acceleration (rarely acceleration gets a pass). i do have desktop acceleration turned on xorg.

system is a p4 with nvidia 5600 256

any help would be appreciated. this problem once solved always creaps back up.

---

### Post by digitalslave on 2006-07-30
fixed by reinstalling glx although this problem (reinstalling) is getting quite old.

---

### Post by digitalslave on 2006-07-30
and once again - reboot - BROKEN!

---

### Post by digitalslave on 2006-07-30
it seems that reinstalling does nothing - if allowed to start x on startup acceleration does not start... however if i bork the xorg.conf and then start in command line and manually start x acceleration works just fine?

this is about the weirdest thing ive ever seen.

anyone have any idea?

---

### Post by tseliot on 2006-07-31
There might be a driver mismatch.

Try my Envy script:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by digitalslave on 2006-07-31
note: do not run script as root doesnt work

installed with newest drake envy script and the same problem persists although now i am getting a fail on opengl and a pass on 3d acceleration from a manual x start. if it starts itself nothing...

---

### Post by digitalslave on 2006-07-31
tried to install the other version you had there and now neither opengl or acceleration are working.

---

### Post by tseliot on 2006-08-01
1) Uninstall the driver from my script

2) **Reboot** and try to reinstall it.

sometimes a reboot helps

---

### Post by digitalslave on 2006-08-01
still nothing - nvidia screen comes up so the driver appears to work and everything but still no acceleration :(

hoping to have parts for a new amd 64bit machine soon - hopefully starting fresh will do the trick but if you have any suggestions in the meantime i would be greatful!

---

