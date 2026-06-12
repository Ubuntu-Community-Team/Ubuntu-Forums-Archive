---
title: "Anyone have NVIDIA 180.22 video drivers working in intrepid (Mythbutu 8.10)?"
date: 2009-02-01
forum: Mythbuntu
---

### Post by Ductilemelon on 2009-02-01
Anyone have NVIDIA 180.22 video drivers working in intrepid? 

I have an ASUS M3N78-VM Mother board with onboard NVIDIA 8200 chip and was looking for better support of the HDMI interface I tried loading the 180.22 drivers last night but now system video is messed up and I can't figure out how to revert to the 170.xx drivers. 

If anyone has a working ASUS M3N78-VM Mother board with onboard NVIDIA 8200 with the 180.22 in Mythbuntu 8.10 any ideas on how you got there would be greatly appreciated.

Otherwise does anyone know how to fix an upgrade gone bad i.e. revert to 170.xx proprietary NVIDIA drivers?

Thanks

---

### Post by bmwman on 2009-02-01
I did the same thing and I screwed my system as well. Let me know if you figure it out, this really sucks.

---

### Post by superm1 on 2009-02-02
apt-get remove --purge nvidia-glx-180 nvidia-180-kernel-source

apt-get install nvidia-glx-177

Should fix you up - unless you installed from NV's .run, then um.

---

### Post by rodercot on 2009-02-02
> **superm1 said:**
> apt-get remove --purge nvidia-glx-180 nvidia-180-kernel-source

apt-get install nvidia-glx-177

Should fix you up - unless you installed from NV's .run, then um.

 If you install via Nv's .run pkg then just run it again with the --uninstall switch at the end. 

 I am running 180.22 with kernel 2.6.28-4 on my test machine and I am running 180.22 on my main machine with an Asus P5N7A and 9300.  

 Dave

---

### Post by Ductilemelon on 2009-02-04
Ended up rebuilding the OS because everything that I tried to do to undo the 180.22 drivers was unsuccessful.

---

### Post by nicoloks on 2009-02-04
I have that exact motherboard and the 180.22 drivers worked first go for me. Mind you I installed them on a fresh system. Did you have a customised xorg.conf before installing? Perhaps that through the Nvidia install script off?

---

### Post by rodercot on 2009-02-05
if you plan on using the Nvidia install method via the .run pkg do not enable the restricted driver and do not dwnld via glx. 

 once you have the nvidia driver any version installed and you do have issues, you can run sudo nvidia-xconfig from a command line and it will overwrite your xorg.conf file with a clean one backing up your old one automagically of course.

 you can then goto your xorg.conf file and remove everything under the module section except for "glx" for some reason I have yet to figure this out, if we are installing via the .run package I cannot figure out why we still need that glx module reference in the xorg.conf file.

 you should also check out your Xorg log file and look for any lines with (EE) at the beginning these are Errors and that will give you a place to start.

 Dave

---

### Post by Mrkluky on 2009-02-11
> **Ductilemelon said:**
> Ended up rebuilding the OS because everything that I tried to do to undo the 180.22 drivers was unsuccessful.

Did you tried 'sudo dpkg-reconfigure -phigh xserver-xorg' ?

---

### Post by bxcrx on 2009-02-13
I had the same issue and went through endless amounts of troubleshooting, restoring xorg.conf files drivers.. You name it... I had to reinstall the O/S

When is this due for 8.10?

---

