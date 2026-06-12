---
title: "NVIDIA Drivers on Ubuntu 8.10 - SOLVED"
date: 2008-11-07
forum: Multimedia Software
---

### Post by churfsan on 2008-11-07
Hello all,

I am writing this with reference to an earlier post I put up regarding NVIDIA drivers on 8.04. Although I could never get it working, I installed now 8.10 on the same machine, and I am now able to run NVIDIA drivers without any problem. Just wanted to share my experience so that others may be benefit. 

My machine is MSI RS-480-IL2 motherboard, with NVIDIA XFX 8600 GT card.
This is the procedure I followed:

Just go to System -> Adminitration-> Hardware Drivers and enable NVIDIA 177 driver. It will download and install the driver. 

Here there is a small hitch. Sometimes the download progress window stops at 0% only, it is bug, but the download takes place in the background and installs the driver. You need to be patient for about 5 minutes (256 KBPS download speed). 

After that, just check under System -> Administration for a new menu entry "NVIDIA Settings", if so, the driver is installed. If you select the menu item, it will say "Looks like NVIDIA driver is not being used, Update your Xorg.conf file, just run "nvidia-xconfig" from terminal as root". 

Do that, and it will update your xorg.conf file, just restart X, using CTRL + ALT + BACKSPACE, it will logout you out and ask for login again. Just login and you have NVIDIA 3D fully working. 

Try enabling 3D effects and enjoy !!! Ubuntu 8.10 really rocks, especially with 3D enabled.

For all the persons who were kind enough to reply and comment on earlier post, I would like to thank all of you.

Anyone facing problem with Ubuntu 8.04, I suggest upgrade to Ubuntu 8.10. It will solve many problems.

Thanks once again!!!

---

