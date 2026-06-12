---
title: "ATI driver trobles"
date: 2006-04-01
forum: Multimedia &amp; Video
---

### Post by slipk487 on 2006-04-01
It says i need to be a super user to install driver what is that and how do i do it


```
To install the ATI Proprietary Linux driver using the Automatic option, follow these steps:

   1. Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver download.
   2. Enter the command sh ./ati-driver-installer-8.23.7-i386.run to launch the 32bit version of the ATI Proprietary Linux driver installer or sh ./ati-driver-installer-8.23.7-x86_64.run to launch the 64 bit version of the ATI Proprietary Linux driver installer. The ATI Proprietary Linux Driver Setup dialog box is displayed.


	Note: 	You must be logged in with super user privileges in order to successfully install the ATI Proprietary Linux driver.

   3. Select Install Driver and click Continue. The ATI License Agreement is displayed.
   4. Read the License Agreement and Click I Agree to continue the installation, or Cancel to terminate the installation. The Mode of Installation Dialog Box is displayed.

   5. Select Automatic and click Continue. The ATI Proprietary Linux Driver is installed, and the Installation Complete Dialog box is displayed.

   6. Click View HTML Release Note for last minute driver information, or Exit to close the ATI Proprietary Linux Driver Installer.
   7. Launch the Terminal Application/Window and run /usr/X11R6/bin/aticonfig --initial to configure the driver.
   8. Reboot your system. 

You have successfully installed the ATI Proprietary Linux Driver.

```

---

### Post by vruum on 2006-04-01
superuser means administrator or "root" which means that you and any application you run has full read write access to the whole of the system, the driver needs it to write to some system directories. to execute a command as super user, prefix it with "sudo" (SuperUser DO) it'll then prompt you for your password. and execute the command as superuser. anyway, to install the ati-driver, there's a great wiki [here]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

---

