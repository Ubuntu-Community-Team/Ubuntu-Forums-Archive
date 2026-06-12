---
title: "ASUS USB-N13 Still not working"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by etgcm on 2011-03-30
Hello All,
 
I am new to ubuntu and linux and have been browsing this forum for three days and still cannot get my ASUS usb-n13 to work.
 
It shows up with lsusb but not with iwconfig or ifconfig.
 
I was able to download and install v2.4.0.1 driver from ASUS. I can see it working with lsmod but nothing is using it and modinfo lists it as version 2.4.0.0.
 
I am not sure where to put the RT2870STACard.dat file. It doesn't look like "make install" put it anywhere.
 
Thanks in advance for any help with this problem.

---

### Post by etgcm on 2011-03-31
I have compiled and done a make install of the latest driver (v2.3.0.1) from ralink but when I try to do an insmod I get this.
 
root@ubuntu:/home/ubuntu/working/os/linux# insmod rt3070sta.ko
insmod: error inserting 'rt3070sta.ko': -1 Unknown symbol in module
root@ubuntu:/home/ubuntu/working/os/linux# 
 
I found some other threads with this message but none for this version of the driver and this is the only rt3070 I could get to compile.
 
This is the end of the dmesg output 
 
[11996.803033] <--- rtusb exit
[12272.506167] rt3070sta: module license 'unspecified' taints kernel.
[12272.506172] Disabling lock debugging due to kernel taint
[12272.506435] rt3070sta: Unknown symbol usb_alloc_urb (err 0)
[12272.506649] rt3070sta: Unknown symbol usb_free_urb (err 0)
[12272.507018] rt3070sta: Unknown symbol usb_alloc_coherent (err 0)
[12272.507676] rt3070sta: Unknown symbol usb_register_driver (err 0)
[12272.508507] rt3070sta: Unknown symbol usb_put_dev (err 0)
[12272.508830] rt3070sta: Unknown symbol usb_get_dev (err 0)
[12272.509381] rt3070sta: Unknown symbol usb_submit_urb (err 0)
[12272.510184] rt3070sta: Unknown symbol usb_free_coherent (err 0)
[12272.511000] rt3070sta: Unknown symbol usb_control_msg (err 0)
[12272.511733] rt3070sta: Unknown symbol usb_deregister (err 0)
[12272.512576] rt3070sta: Unknown symbol usb_kill_urb (err 0)
[12638.222245] rt3070sta: Unknown symbol usb_alloc_urb (err 0)
[12638.222460] rt3070sta: Unknown symbol usb_free_urb (err 0)
[12638.222869] rt3070sta: Unknown symbol usb_alloc_coherent (err 0)
[12638.223366] rt3070sta: Unknown symbol usb_register_driver (err 0)
[12638.223870] rt3070sta: Unknown symbol usb_put_dev (err 0)
[12638.224058] rt3070sta: Unknown symbol usb_get_dev (err 0)
[12638.224379] rt3070sta: Unknown symbol usb_submit_urb (err 0)
[12638.224847] rt3070sta: Unknown symbol usb_free_coherent (err 0)
[12638.225322] rt3070sta: Unknown symbol usb_control_msg (err 0)
[12638.225895] rt3070sta: Unknown symbol usb_deregister (err 0)
[12638.226735] rt3070sta: Unknown symbol usb_kill_urb (err 0)
[13458.097159] rt3070sta: Unknown symbol usb_alloc_urb (err 0)
[13458.097375] rt3070sta: Unknown symbol usb_free_urb (err 0)
[13458.097759] rt3070sta: Unknown symbol usb_alloc_coherent (err 0)
[13458.098243] rt3070sta: Unknown symbol usb_register_driver (err 0)
[13458.098747] rt3070sta: Unknown symbol usb_put_dev (err 0)
[13458.098936] rt3070sta: Unknown symbol usb_get_dev (err 0)
[13458.099256] rt3070sta: Unknown symbol usb_submit_urb (err 0)
[13458.099725] rt3070sta: Unknown symbol usb_free_coherent (err 0)
[13458.100199] rt3070sta: Unknown symbol usb_control_msg (err 0)
[13458.100772] rt3070sta: Unknown symbol usb_deregister (err 0)
[13458.101613] rt3070sta: Unknown symbol usb_kill_urb (err 0)
 
Does anyone have any ideas?

---

### Post by etgcm on 2011-04-03
Here is what I did, maybe someone will find it helpful.  Thank you to all of the knowledgeable people who donate their time to this and other forums.  I could not have done it without your help.

1.) Blacklist these drivers.[INDENT]blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb
blacklist rt2870sta

sudo gedit /etc/modprobe.d/blacklist.conf and add to end of file

Reboot to make sure they don't restart.  I had done something previously that would start these drivers even after they were blacklisted.  I ended up reinstalling ubuntu and starting over.
[/INDENT]2.) Download and expand the attached file.[INDENT]It is the current driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) with the following modifications
[/INDENT][INDENT]-added MODULE_LICENSE("GPL"); to /*installed location/*os/linux/usb_main_dev.c after MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");

-Changed the n's to y's for these lines in  /*installed location/*os/linux/config.mk

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
[/INDENT]3.) Compile and install[INDENT]cd /[I]installed location
[/I]make
sudo make install

If you make any mistakes and need to start over do this
sudo make uninstall
make clean
make
sudo make install
[/INDENT]You should now be able to configure a wireless connection using the icon at the top of the screen.

---

### Post by Talon2 on 2011-04-03
How about subscribing to and making a writeup on this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

The more folks, the greater the chance of this being fixed.

---

### Post by etgcm on 2011-04-04
Will rt3070 work with the rt2870 chipset?

---

