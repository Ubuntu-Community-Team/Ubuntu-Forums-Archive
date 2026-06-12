---
title: "Solution to API mismatch to use latest nVidia drivers"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by rjon17469 on 2007-07-10
This thread is meant to be informative for people trying to use the latest nVidia drivers and running into an API mismatch error. I searched many forums and never found anything that worked successfully. Here is how I was able to use the latest drivers from nVidia (100.14.11 at the moment) and have it work from boot.

Notice: I do not claim to be an expert at linux, and am far from it. If I made an error, please correct me to help others out. Also, this article is written so hopefully everyone can follow it, even a beginner, so please excuse the commands.

1) Download the latest nVidia linux drivers from [www.nvidia.com](www.nvidia.com).
2) Open a terminal, browse to the download directory, and mark the package as executable (chmod a+x 'filename').
3) Switch to a different virtual terminal (ctrl+alt+F1).
4) Log in as your user name, then type 'sudo su' and enter your root password.
5) Stop gnome (/etc/init.d/gdm stop)
6) Browse to the directory which you downloaded the nVidia drivers and type ./'filename'.
7) Go through the install process, choosing to uninstall other drivers if found and do not check the nvidia ftp site for a kernel module.
8) Assuming that process was successful, open /etc/modprobe.d/lrm-video (vim /etc/modprobe.d/lrm-video)
9) Comment out the install nvidia line (in vim, hit 'i', insert a '#' at the beginning of the line to comment out, hit escape a couple times, type ':', then 'x', then enter)
10) Reboot, and hopefully everything works out!

Please let me know if this helps!

Edit 9:55 AM CT 7/11/07: Some notes on the above steps: first, it may be helpful to remove installed nvidia_glx, nvidia_glx_new, and nvidia_glx_legacy drivers from the package manager before proceeding with the installation of the new drivers. Moreover, in the file to be edited, the only line that needs to be commented out is the install nvidia line, not the nvidia_new or nvidia_legacy lines. This is assuming that you are using non-legacy drivers from nvidia, which I am. Using legacy drivers may require you to comment out other lines as well as/in place of the nvidia line. If you are unsure, you can comment out all three if present.

---

### Post by emperon on 2007-07-11
It doesn't work. I think you need to remove the old modules. So what you suggest is insufficient for some people. Also note that the file you mention contains more than 1 entries of  NVidia here

---

### Post by rjon17469 on 2007-07-11
What error did you get? Still the API mismatch? In regard to old modules, the nVidia installer should recreate symbolic links from the old modules to the new modules, so the old ones are still present but not used. I uninstalled previous drivers installed through the package manager first however, which may have helped. Also, in the file mentioned to be edited, there may be nvidia, nvidia_new, and nvidia_legacy lines. Only the nvidia line needs to be commented out. This just prevents the 'nvidia' kernel module from being loaded from the restricted modules package, which is needed because the nvidia installer uses a kernel module with the same name. The _new and _legacy install lines can be commented as well, but it should not be necessary.

I'll combine this into my original post. Thank you for your comments emperon. I found this method to be successful for me. If others do as well, please post to confirm that this works. If you encounter troubles, I'm more than willing to help however I can.

---

### Post by emperon on 2007-07-28
yes again the same api mismatch problem

---

### Post by rjon17469 on 2007-07-29
I'm sorry to hear that this did not work for you. I don't know how much further I can help without more information. I'm willing to help you further if you'd like. If so, please post the detailed output of your xserver when it fails to load.

One point of interest may be the versions we are using. Your profile lists you as using version 6.06 of ubuntu. These instructions worked for version 7.04, which I use. I don't know if they would be different or applicable to earlier versions.

---

### Post by masebase on 2007-07-31
The fix worked for me with ubuntu 7.04 when nothing else seemed to.  Thanks!

---

