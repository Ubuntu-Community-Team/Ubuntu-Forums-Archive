---
title: "D-Link DWA-125 w/10.04gets lost upon restart"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by banana jack on 2012-06-01
[http://ve3emb.wordpress.com/2010/10/03/d-link-dwa-125-on-linux-ubuntu-10-04/](http://ve3emb.wordpress.com/2010/10/03/d-link-dwa-125-on-linux-ubuntu-10-04/)
 I followed this tutorial, and even though everything I did was beyond me, I followed along with the video and googled some things... I did successfully unplug from the wired and go wireless after finishing, which got me super pumped, and then I unplugged everything and brought it back downstairs and set it up again...and now it has no idea what the internet is anymore...


i tried following the video through again, and have determined that the only important part is the insmod command at the end, and if i restart and then run that then my wireless works.


so i have to run
~$cd ~/Downloads
~/Downloads$ls
 
~/Downloads$cd DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/
 
~/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604$su
~/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604$cd os/linux
~/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux#insmod rt3070sta.ko


every time i boot up. i don't know what any of what i just ran meant, but i would rather not have to do it every time i boot up. any ideas?

---

### Post by chili555 on 2012-06-01
Please try this:```
sudo su
echo rt3070sta >> /etc/modules
exit
```The next time you reboot, see if it's working and post back to give us your report.

---

### Post by banana jack on 2012-06-03
nope. i ran it and rebooted, nothing. then i tried to run the insmod command so i could have internet and post my reply and it said that rt3070sta.ko is busy. so no more internet.

---

### Post by chili555 on 2012-06-03
Let's do some diagnostics. Please run and post:```
lsusb
modinfo rt3070sta | head -n1
iwconfig
```Thanks.

---

### Post by banana jack on 2012-06-04
samuel@samuel-desktop:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard 
Bus 002 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 008: ID 07d1:3c16 D-Link System  Bus 001 Device 004: ID 05ac:1260 Apple, Inc. iPod Nano 2.Gen 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
samuel@samuel-desktop:~$ modinfo rt3070sta | head -n1 
ERROR: modinfo: could not find module rt3070sta 
samuel@samuel-desktop:~$ iwconfig 
lo        no wireless extensions. 

 eth0      no wireless extensions.

---

### Post by chili555 on 2012-06-04
> ID 07d1:3c16 D-Link System > ERROR: modinfo: could not find module rt3070sta It appears you missed an essential step. Please do:```
cd Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/
sudo su
make
[COLOR="Red"]make install[/COLOR]
modprobe rt3070sta
exit
```Any improvement?

---

### Post by banana jack on 2012-06-05
samuel@samuel-desktop:~$ cd Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/ 
samuel@samuel-desktop:~/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604$ sudo su
[sudo] password for samuel: 
 root@samuel-desktop:/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# make make -C tools make[1]: Entering directory `/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/tools' gcc -g bin2h.c -o bin2h make[1]: Leaving directory `/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/tools' /home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/tools/bin2h cp -f os/linux/Makefile.6 /home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/Makefile make -C /lib/modules/2.6.32-122-rtai/build SUBDIRS=/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux modules make[1]: Entering directory `/usr/src/linux-headers-2.6.32-122-rtai'   CC [M]  /home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/rtmp_mcu.o   LD [M]  /home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/rt3070sta.o   Building modules, stage 2.   MODPOST 1 modules   LD [M]  /home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/rt3070sta.ko make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-122-rtai' cp -f /home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/rt3070sta.ko /tftpboot 
root@samuel-desktop:/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# make install make -C /home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux -f Makefile.6 install mkdir: cannot create directory `/etc/Wireless': File exists make[1]: Entering directory `/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux' rm -rf /etc/Wireless/RT3070STA mkdir /etc/Wireless/RT3070STA cp /home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/RT3070STA.dat /etc/Wireless/RT3070STA/. cp: cannot stat `/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/RT3070STA.dat': No such file or directory make[1]: *** [install] Error 1 make[1]: Leaving directory `/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux' make: *** [install] Error 2 
root@samuel-desktop:/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# modprobe rt3070sta 
root@samuel-desktop:/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# exit 
exit

---

### Post by chili555 on 2012-06-05
> /etc/Wireless/RT3070STA/. cp: cannot stat `/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/RT3070STA.dat': No such file or directory make[1]: *** [install] Error 1 make[1]: Leaving directory `/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux' make: *** [install] Error 2 That should be quick and easy to fix. Please show me:```
ls Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/
```Thanks.

---

### Post by banana jack on 2012-06-05
samuel@samuel-desktop:~$ ls Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/
chips             LICENSE ralink-firmware.txt  RT2870STACard.dat       tools
common            Makefile                     RT2870STA.dat
include           os                           sta
iwpriv_usage.txt  README_STA_usb               sta_ate_iwpriv_usage.txt

---

### Post by chili555 on 2012-06-05
> samuel@samuel-desktop:~$ ls Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/
chips LICENSE ralink-firmware.txt RT2870STACard.dat tools
common Makefile RT2870STA.dat
include os sta
iwpriv_usage.txt README_STA_usb sta_ate_iwpriv_usage.txtYou have RT2870STA.dat but it wants:> cp: cannot stat `/home/samuel/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/[COLOR="Red"]RT3070STA.dat[/COLOR]': No such file or directoryLet's fix it. Please do:```
cd Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604
cp RT2870STA.dat RT3070STA.dat
sudo su
make clean
make
make install
modprobe rt3070sta
exit
```Now does it make properly? Does the module load without errors? Does the wireless work? If so, you're all set.

---

### Post by banana jack on 2012-06-05
everything went fine until
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-122-rtai/kernel/drivers/net/wireless/rt3070sta.ko): Device or resource busy

---

### Post by chili555 on 2012-06-06
> **banana jack said:**
> everything went fine until
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-122-rtai/kernel/drivers/net/wireless/rt3070sta.ko): Device or resource busyThat simply meant it was already loaded. What does a new day and a reboot show us? Is it working as expected?

---

### Post by banana jack on 2012-06-06
IT WORKS!!! you're amazing. thanks a ton.

does anybody know what this is? it pops up right after my wpa box pops up to log into my home network. i can click ok as many times as i want, it keeps coming back unless i click cancel, then it just goes away and stays away. no idea what the password might be though. i've tried all the ones i know.

[[IMG]http://img191.imageshack.us/img191/7162/screenshotunlockloginke.png[/IMG]]("http://imageshack.us/photo/my-images/191/screenshotunlockloginke.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by chili555 on 2012-06-06
I think the keyring password gets set on first connection right after install. To me, it amounts to 'you have to give the password in order to be allowed to give the password.' I guess it's supposed to be more secure in some way. I clicked Cancel and it stays away forever. If yours won't stay away forever, you can probably find a solution on General Help.

Don't forget, with a compiled from source driver, you'll need to recompile whenever you get an updated kernel. It's just the same:```
cd Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604
sudo su
make clean
make
make install
modprobe rt3070sta
exit
```Have fun!

---

