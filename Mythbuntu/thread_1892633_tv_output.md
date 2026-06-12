---
title: "tv output"
date: 2011-12-08
forum: Mythbuntu
---

### Post by dkag7 on 2011-12-08
hi all,
i can not find where the settings are to enable tv output.
my system is a p1-ph1 asus. on the system, i can view live tv and recordings fine through the computer monitor. what i want to do is get the tv output on the system to display video on the tv.

i checked with lspci -k and got this:

[I]VGA compatible controller: ATI Technologies Inc RS400 [Radeon Xpress 200]
	Subsystem: ASUSTeK Computer Inc. Device 81c8
	Kernel driver in use: radeon
	Kernel modules: radeon
[/I]

so it looks to me like the drivers are loaded.?
are they?
if so, what bone-headed thing am i not doing to get the display on the tv?

thanks
<kurt

---

### Post by lswartz on 2011-12-08
Did you enable it in the ATI Catalyst Control Center?

---

### Post by dkag7 on 2011-12-08
i doubt it... can you tell me where it is?
I went through all settings that i could find

thanks
kurt

---

### Post by dkag7 on 2011-12-08
going to the ati site, it looks like i need this driver [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

in the driver install, it tells me to do this for auto install:
Enter the command sh ./ati-driver-installer-9.2-x86.x86_64.run to launch the
ATI Proprietary Linux driver installer

it also tells me that i need super user privileges.
 so from the download directory i typed 'sudo su'
it asks me for my password, and i enter it.
Then i type sh ./ati-driver-installer-9.2-x86.x86_64.run 
I then get:
sh: cant open  ./ati-driver-installer-9.2-x86.x86_64.run 

Can someone tell me what i am doing wrong?
Do i need to have ubuntu installed as well?
(i just installed mythbuntu alone)

thanks
Kurt

---

### Post by dkag7 on 2011-12-08
ok, i have another video driver that came with the system that i am trying to install.

i can get the install to run now, but the install stops at a message:
X server: unable to detect

what does that mean?

Also, on the ATI sight, it says "[FONT=verdana][SIZE=2]Currently, this driver is available in rpm  format only. Packages are available for XFree86 versions 4.1, 4.2, and  4.3, as well as X.org 6.8. One of these four versions must be installed  before installing the ATI Proprietary Linux driver."

Can someone please tell me what this is? my guess is that this is what is stopping the video card driver install, but i have know idea what it is or what to do about it..
any help would be gratefully appreciated ! :confused:

thanks again
kurt
[/SIZE][/FONT]

---

