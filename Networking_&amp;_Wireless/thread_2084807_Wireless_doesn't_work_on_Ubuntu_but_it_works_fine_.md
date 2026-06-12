---
title: "Wireless doesn't work on Ubuntu but it works fine on Windows 7"
date: 2012-11-16
forum: Networking &amp; Wireless
---

### Post by M123 on 2012-11-16
Hi Everyone,
 
 I used to have Windows 7 as a single OS on my laptop, and now I installed Ubuntu. But I have a problem with the wireless connection. It works fine on Windows 7 though, and the wired connection works fine on both. And If I run Ubuntu from the CD as a trial version the wireless works fine. I will appreciate any help as I am new to Ubuntu and I don't know how to start the troubleshooting.

Regards,

---

### Post by ajgreeny on 2012-11-16
Have you done an update with the cable connection?  That may solve the problem for you.

---

### Post by wildmanne39 on 2012-11-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by M123 on 2012-11-16
Hey Guys,

Thanks for your replies :smile: 

Wild Man...Kindly find the attached file.

---

### Post by wildmanne39 on 2012-11-16
Hi, please do:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
```
sudo modprobe b43
```
or reboot.
Thanks

---

### Post by M123 on 2012-11-16
still doesn't work

---

### Post by wildmanne39 on 2012-11-16
Hi, delete the infotext file and run the script again and attach the results so we can see where your wireless is at now.
Thanks

---

### Post by M123 on 2012-11-17
Here you go man :)

---

### Post by wildmanne39 on 2012-11-17
Hi, ok we will just use the other driver then.

```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Then:
```
sudo modprobe wl
```
Thanks

---

### Post by M123 on 2012-11-17
still nothing...this is what I got 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,181 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 151491 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-18-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-18-generic
mahmoud@mahmoud-Aspire-5741G:~$ sudo modprobe wl
FATAL: Module wl not found.

---

### Post by wildmanne39 on 2012-11-17
Hi, please do:
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
```
Then:
```
sudo modprobe wl
```
Thanks

---

### Post by flash63 on 2012-11-17
Hello,
brcmsmac with the latest firmware might work directly. Give it a try before you install the Broadcom Station-Driver ;)
[http://www.linuxwireless.org/en/users/Drivers/brcm80211](http://www.linuxwireless.org/en/users/Drivers/brcm80211)

Install the latest Broadcom Firmware from [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree)

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware
sudo modprobe bcma brcmsmac
iwconfig
iwlist chan
sudo iwlist scan
```

Reference: [http://forum.ubuntuusers.de/topic/lenovo-s206-nach-installation-kein-wlan-discon/2/#post-5007272](http://forum.ubuntuusers.de/topic/lenovo-s206-nach-installation-kein-wlan-discon/2/#post-5007272)

---

### Post by M123 on 2012-11-19
WildMan Thanks sooooooooo much...you saved my life man :D :D 
I really appreciate your help :)
but can you just briefly explain to me what was it cause I hate that I don't understand :) 
Thanks again :)

---

### Post by M123 on 2012-11-19
Thanks Flash63 but Wild Man's commands made it work :)

---

### Post by wildmanne39 on 2012-11-19
Hi, there are two drivers that can be used for your device I like the b43 better then the wl myself.

The reason it would not work to build the driver you have to have linux-headers installed and they are not installed be default in 12.10 so the driver will not build.
Thanks

---

