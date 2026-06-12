---
title: "Realtek RTL8192e on 802.11n?"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by tonyps on 2011-01-25
Afternoon,

Anyone out here had any success with getting this wireless nic to work on wireless n networks?
It goes all day on 802.11/bg, so long as I use the ndiswrapper method with the XP driver. I have never been successful, as far as I can remember, getting it to work with linux drivers...???
Is there anyone successful in getting a linux driver set (and can get me to it, or it to me??) to work on Ubuntu 10.10,32bit??
Thanks in advance for any assistance.

Tony ...
Toshiba A505D-S6958

---

### Post by eldergs on 2011-02-23
Hi. I have the same problem and notebook. But, readying so many forum and post, I resolved the problem.

Sorry for my bad english.

First, open your terminal.

Run the code:

**lsmod | grep 819**

I think will show:

r8192e_pci
r8192se_pci

This is the conflicting drivers.

Now, run this code (to add r8192se_pci in blacklist):

[B]sudo su
echo "blacklist r8192se_pci" >> /etc/modprobe.d/blacklist.conf
exit[/B]

**Reboot**

Now, Download the newest driver from realtek, they mail me with instructions and file (I post in some servers)

[http://eldergs.4shared.com](http://eldergs.4shared.com)
[http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html](http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html)
[http://www.megaupload.com/?d=F2R0S36T](http://www.megaupload.com/?d=F2R0S36T)

Now do what the support from realtek say:

[B]Hi Sir,               
 
Thanks for your email.
 
Please find the attached for latest RTL8192E 32bit and 64bit Linux driver which is the updated one different from the one you used.
 
Just kindly remind, please install by the below steps.
The following is the installing steps:
1. Change to the driver directory
2. sudo su
3. make
4. make install
5.reboot
6. ./wlan0up or ./wlan1up
 
     Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
           2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).
 
If your OS is 64bit, maybe there is kernel self driver for RTL8192E, you should delet it first before install:
 
 
    1) cd /lib/modules/2.6.3x.xx.xx/
    2) find -name "r8192e_pci.ko"
    3) delet all the r8192e_pci.ko
    4) install our RTL8192E driver
    5) reboot.
 
 
if there’s still any other problem, please let us know.
   Thanks a lot
 
Regards,
Kidman[/B]

Reboot

Now, You can use your Wireless and have fun.

:)

---

