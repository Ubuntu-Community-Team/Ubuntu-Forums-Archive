---
title: "How do I install this ATI graphics driver?"
date: 2010-01-01
forum: Multimedia Software
---

### Post by Cityscape on 2010-01-01
I downloaded my Proprietary ATI Linux Driver (for my Radeon Xpress 200) from [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English). But I cannot figure out how to install it!

I followed the instructions [here]("http://www2.ati.com/drivers/linux/linux_8.16.20.html#176980") but Terminal told me "command not found". I also tried double-clicking the file but it opened with gedit and gave me an error.

I need to know how to install this driver, please help!

---

### Post by Revolutionary101 on 2010-01-01
Make sure that the .run file is in your home folder then just copy and paste the command that is in step two of the instructions.

After you go through the setup just follow step 7

---

### Post by Cityscape on 2010-01-01
> family@FamilyPC:~$ sudo ./ati-driver-installer-9-3-x86.x86_64.run
[sudo] password for family: 
sudo: ./ati-driver-installer-9-3-x86.x86_64.run: command not found
family@FamilyPC:~$ 

I still get "command not found".
What do i need to do?

---

### Post by Revolutionary101 on 2010-01-01
Enter this command first

```
sudo su
```

Then enter this

```
./ati-driver-installer-9-3-x86.x86_64.run
```

---

### Post by Cityscape on 2010-01-01
family@FamilyPC:~$ sudo su
[sudo] password for family: 
root@FamilyPC:/home/family# ./ati-driver-installer-9-3-x86.x86_64.run
bash: ./ati-driver-installer-9-3-x86.x86_64.run: Permission denied
root@FamilyPC:/home/family#

Now i get this?

---

### Post by Revolutionary101 on 2010-01-01
Right click on the .run file and click on Properties. Once the properties window opens up go to the Permissions tab. After that check the box that says "Allow executing file as program". Then you should be able to run it with the commands I told you to use earlier.

---

### Post by Cityscape on 2010-01-01
Well it now did execute correctly but now I get the following error.

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-17-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.dnhAzv

---

### Post by Revolutionary101 on 2010-01-01
I think you are trying to install a graphics driver that does not support the 2.6.28-17-generic linux kernel. I would suggest upgrading to Ubuntu 9.10 to fix this or you could possibly compile your own linux kernel to update.

---

### Post by Cityscape on 2010-01-01
This driver was released on March 26 2009.
I would think that since Jaunty (9.04) was only a month or so away from being released that ATI would support it.

Would upgrading to Karmic really help? I'm using Ubuntu CE, and the latest stable release of that is 9.04

---

### Post by Revolutionary101 on 2010-01-01
I looked on the AMD/ATI website and I think you may be trying to install the wrong driver. If you go to the website [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English") you should be able to get the right driver. Try that one and see how it works. There should also be a .pdf file that will help you with installing it. (don't forget to use the instructions that I told you about before)

---

### Post by charon2112 on 2010-01-02
> **Revolutionary101 said:**
> I looked on the AMD/ATI website and I think you may be trying to install the wrong driver. If you go to the website [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English) you should be able to get the right driver. Try that one and see how it works. There should also be a .pdf file that will help you with installing it. (don't forget to use the instructions that I told you about before)

Hi, I'm also trying to install an ATI driver.  It's the current version, 9.3.  I'm running Karmic, and I also get the below error:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-17-generic; make sure that the version is being
correctly set by --iscurrentdistro

Can anyone help?

---

### Post by Yellow Pasque on 2010-01-02
You can't install Catalyst 9.3 on Jaunty/Karmic. Catalyst 9.3 does not support the more recent X server versions found in those releases. Just use the pre-installed open-source radeon/ati driver.

---

### Post by igotswings on 2010-02-22
> **Temüjin said:**
> You can't install Catalyst 9.3 on Jaunty/Karmic. Catalyst 9.3 does not support the more recent X server versions found in those releases. Just use the pre-installed open-source radeon/ati driver.

Those with Xpress 200 are out of luck?

---

### Post by Yellow Pasque on 2010-02-22
> **igotswings said:**
> Those with Xpress 200 are out of luck?
For the moment, yes. A Gallium3D driver for that gen of chips is under development along with improvements in the kernel. [http://www.phoronix.com/forums/showthread.php?t=22096](http://www.phoronix.com/forums/showthread.php?t=22096)

---

### Post by igotswings on 2010-02-22
> **Temüjin said:**
> For the moment, yes. A Gallium3D driver for that gen of chips is under development along with improvements in the kernel. [http://www.phoronix.com/forums/showthread.php?t=22096](http://www.phoronix.com/forums/showthread.php?t=22096)

You said earlier to "Just use the pre-installed open-source radeon/ati driver." How do I do that O.o

---

### Post by Yellow Pasque on 2010-02-22
It's pre-installed. If you want to try a newer version, see the xorg-edgers PPA. It may give you a bit better 3D experience, but it still won't be as good as the proprietary driver or the forthcoming Gallium3D "r300g" driver.

---

