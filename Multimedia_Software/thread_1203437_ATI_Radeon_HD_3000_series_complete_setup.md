---
title: "ATI Radeon HD 3000 series complete setup"
date: 2009-07-03
forum: Multimedia Software
---

### Post by grizlo42 on 2009-07-03
Here is what I did to get my ATI Radeon HD working.

[LIST]
[*]downloaded the ATI Catalyst driver from: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)
[*]chmod +x ati-driver-installer-*.run
[*]fresh install of ubuntu (9.04)
[*]install updates
[*]at this point, i mounted my /home directory which i kept through the install where i kept the driver, but any way of copying the driver installer works.
[*]sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms ia32-libs <== ia32-libs only for 64 bit install
[*]cp to directory containing the driver
[*]sh ati-driver-installer-9-6-x86.x86_64.run --buildpkg Ubuntu/jaunty
[*]sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
[*]sudo apt-get install displayconfig-gtk <== This may not be necessary, but its what i did, and mine is working well so, I put it anyway
[*]sudo gedit /etc/X11/xorg.conf
[*]add this to the driver device section
[/LIST]
```

Section "Device"
	.........[B]
	Identifier	"SOME IDENTIFIER"
	Driver		"fglrx"[/B]
        .........
EndSection

```
[LIST]
[*]sudo aticonfig --initial -f
[*]sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
[*]sudo shutdown -r
[/LIST]

glxgears should be running fine. compiz should be working, and compiz plus opengl programs work :).  Don't enable the restricted module at this point. Hope this helps.

---

### Post by jonshaft1 on 2009-07-29
Thanks for the post, this worked like a charm for me.

I appreciate you taking the time to put this up here...

---

### Post by markbuntu on 2009-07-30
A little more FYI.

If you have a fresh install of ubuntu and have not enabled the restricted driver offered from hardware manager you can just make the install script executable by right clicking on it and choosing properties/permissions and checking the executable box and then cd the whever you downloaded it to  and run it as root

cd /Desktop
sudo sh ./ati-driver-installler-9-7-x86.x86_64.run

and after it finishes

sudo aticonfig --initial
This will automatically configure the etc/X11/xorg.conf file.
reboot so the kernel modules and the driver become active.

It is not necessary to build the packages unless the installer does not work, like if you are using the rt kernel or something. The automatic installer has worked for me for more than a year now with Hardy and Intrepid and Jaunty both 32 and 64 bit versions with my HD3650 and HD3450. If you have an integrated 3200 or 3300 then you should use the latest driver. 

If you want to use more than one gpu then you should use the latest driver. If you have a new 4xxx series esppecially the 45xx and the x2 series, many of these are not supported by the driver in the repos so you should use the latest driver from ati.

If you are already using the driver from hardware manager then you need to remove fglrx and the fglrx kernel modules which you can do with the Synaptic package manager.

If you are using a driver from envy then use envy to remove it completely before installing the new driver from ati.

If you are using a driver from the ati site then you need to run the script usr/share/ati/fglrx-uninstall.sh to remove the old driver before installing a new one.

If you fail to remove an old driver and its kernel modules then there is a good chance that a kernel update will fail to build the fglrx kernel modules and you will boot into a black screen or something as bad.

---

### Post by Krews on 2009-08-14
Thx markbuntu, works great on my hp dv2-1110eo :D

---

### Post by Peter Gtam on 2009-11-26
Thanks for the post!!! :p

---

### Post by chopp3r on 2010-04-07
Thank-you Markbuntu. 

Your simple and straightforward setup worked just fine for me using the following hardware and software: 

[LIST]
[*]Linux distribution - Ubuntu 9.10 karmic koala
[*]Graphics card - ATI Mobility Radeon HD 3650
[*]Display driver - ATI Catalyst display driver version 10.3
[/LIST]
The only thing that I would add is that I read the [installation instructions [PDF, 546 KB]]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat102-inst.pdf") for the driver, which were available on the [ATI Catalyst display driver download page]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.25&lang=English"), and ensured that I had all the required packages installed before I ran the driver installer.

---

### Post by surficity on 2013-04-26
Thanks

---

### Post by surficity on 2013-04-26
Thanks

---

### Post by QIII on 2013-04-26
Back to bed, dear old thread.

---

