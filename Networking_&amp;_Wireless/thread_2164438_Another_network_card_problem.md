---
title: "Another network card problem"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2013-07-31
This is related to the Broadcom 43xx problem discussed in the sticky above. Hope this is the proper place to post.
I have a Dell Inspiron 1150 with a Broadcom 4306 card. It worked with wireless fine in previous versions but has not since I installed (clean) version 12.04.
I installed the B43 driver but when I try to install the firmware for it, the system crashes, leaving a long line of script on the screen. Something about "modprobe tainted."
I have a Belkin USB stick that I can reach the Internet with and I suspect it might be causing a conflict.
I could just continue using the USB stick but it irks me that I can't get the card to work as it did before. Have considered getting another card, since they only cost about $9, but I am doubtful that would help.
Any suggestions appreciated.

---

### Post by Hadaka on 2013-07-31
Hi, give this a try..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
*If that doesnt help..please post the output of..
```
lsmod
lspci -nn | grep 0280
rfkill list all
```
thanks.

---

### Post by Lloydb39 on 2013-07-31
Ran the first command and got this:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Ran that command and it crashed...

---

### Post by Lloydb39 on 2013-07-31
OK. Problem solved. Apparently it was a conflict. I removed the USB device, downloaded the tar file, installed it via the terminal and now I am up and running and I can put away the USB device. For anyone with a similar problem the commands are:'
tar xfvj broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o

---

### Post by Lloydb39 on 2013-08-02
Additional information: It was only solved until I rebooted. Apparently the Belkin USB adapter installs its own driver, so I had to blacklist that one, remove the adapter and reboot, then run the commands above again, and add "sudo modprobe B43." Now we seem to be up and running again, permanently I hope.

---

### Post by Lloydb39 on 2013-08-02
Silly me. This is not solved (and I don't know how to unmark it "solved". Apparently the B43 driver got blacklisted somehow and I have to redo it on every boot. The file with the blacklisting can't be edited. I tried to purge bcwml, per the wiki troubleshooting guide and got this: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Every time I try to use that command, my laptop crashes. So, can anyone tell me how to un-blacklist the B43 driver for good?
Also, some instructions say use B43 and some say use "wl." B43 works but do I need to mess with wl or ssb?

---

### Post by Hadaka on 2013-08-02
Hi, you can not use both wl and b43
as the wl driver blacklists ssb and b43
so....
*If your command sudo modprobe b43
works for you then you can do..
```
sudo su
echo b43 >> /etc/modules
exit 0
```
this will load the b43 driver on boot or restart
Also..if you have not already done so...please do..
```
sudo apt-get update
sudo apt-get upgrade
```
thanks.

---

### Post by praseodym on 2013-08-02
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
should do the trick

---

### Post by Lloydb39 on 2013-08-05
That worked, praseodym. Now this problem really is solved. Thanks, guys.

---

### Post by Lloydb39 on 2013-08-18
Help! This has now turned into a different problem that I'm certain is related. Now I can't update! update manager says something is broken. trying to sudo update in the terminal gets me the instructions do dpkg configure whatever which, as I noted above, always crashes my computer.

---

### Post by Lloydb39 on 2013-08-19
Additional info: I ran these commands, per another post:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
That seemed to help and it told me I have 47 updates. But when I tried to install them, it told me it could only do a partial install and then it tried to install the "bcmwl kernel" thing and that crashed my computer as it always does.
So I'm still stuck. Everything else is working fine and I have wireless, but any attempt to update = FAIL

---

### Post by praseodym on 2013-08-19
Try:
```

sudo apt-get -f install
sudo dpkg --configure -a
```

---

