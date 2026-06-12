---
title: "x1300 pro OpenGL problems"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by voided3 on 2007-09-25
Hello, I recently tried the latest ATI driver release and it crashed my x server, so I reverted to the vesa driver and then renabled the ATI driver with the restricted drivers manger, which had worked before on a clean install. Now the problem is I don't have 3D acceleration and my OpenGL renderer is coming up as Mesa3D instead of fglrx even though fglrx is set as the driver in xorg.conf. Is there anyway I can restore the fglrx OpenGL libs without reformatting (even though I am using a very fresh install of Xubuntu feisty, I sincerely hope that there is an easier way of fixing this than by reformatting)? Thanks!

---

### Post by voided3 on 2007-09-29
Alrighty, I got it figured out. I guess the Envy uninstaller did not initiate these commands but this is straight from the ATI driver release notes:

> If the ATI Proprietary Linux Graphics Driver was installed using either the Automatic or Custom options, then do the following:

   1. Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
   2. With super user permissions, enter the command "sh ./fglrx-uninstall.sh" 


After that I rebooted and re-enabled the driver from the restricted drivers manager and all was as it was before. Too bad it can't be with the newer driver though... yet.

---

