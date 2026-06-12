---
title: "Lenovo g560 eth0 no wireless extensions"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by petre.tudor on 2012-11-07
After some updates that required restart, the wireless stopped working.
My wireless card: is Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)


Can someone please point me to the right direction into solving this?

Thanks!
Petre

---

### Post by chili555 on 2012-11-07
You posted details about your wired ethernet card. Please run and post:```
lspci -nn | grep 0280
rfkill list all
```

---

### Post by petre.tudor on 2012-11-07
Sure

```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```AND

```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```This part was: 
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes

```But I run this: rfkill unblock all and now is:  Soft blocked: no


Thanks for your reply!
Petre

---

### Post by chili555 on 2012-11-07
Your Broadcom works best with the STA driver. Let's try to re-install it and see if we can get it going.```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
iwconfig
```

---

### Post by petre.tudor on 2012-11-07
After the first command I got lots of data, but something went wrong:

```
FATAL: Module wl not found.
```

Second:
```
FATAL: Module wl not found.
```

Still: 

```

eth0      no wireless extensions.
lo        no wireless extensions.

```

:(

---

### Post by chili555 on 2012-11-07
> After the first command I got lots of data, but something went wrong:It will be helpful to see the exact errors. Can you please run it again and copy and paste the terminal output here? May we see:```
lsb_release -d
```

---

### Post by petre.tudor on 2012-11-07
```
sudo apt-get install --reinstall bcmwl-kernel-source


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,181 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 173150 files and directories currently installed.)
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
```

I was under the impression that I've mentioned ubuntu version, sorry: Ubuntu 12.10

---

### Post by chili555 on 2012-11-07
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.Feel that little itch right there? That's known as a bug! You lucky Ubuntu person!

Ideally, if the kernel source were not installed, apt would...do what?...*install it!* Let's help it along:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
iwconfig
```*Now* do we have wireless?

---

### Post by petre.tudor on 2012-11-07
It works!

Thank you for your time!
This is all to much for me :)


Have a nice day/week/year/life!!!

---

### Post by chili555 on 2012-11-07
Thanks for your kind comments! I am very glad it's working. Have fun!

---

### Post by thewump on 2012-11-07
I OWE YOU A BEER TOO!!

Sniffing around the net today many people are having this issue. Seems like a bit of a nightmare impacting Dell / Lenovo / Macbook and all the other Broadcom laptops.

Thanks

Keith

---

### Post by mlorcam on 2012-11-11
Thank you very, very much Chili555. I spent 2 days trying to explain to myself what happened with the wireless card in my **HP ProBook 6360b** and finally reached your post which solved this damned problem :P
Thanks a lot again.

---

### Post by chili555 on 2012-11-11
You are very welcome! Thanks for the kind words and the beers. I'm glad it's working.

---

### Post by Maksat on 2012-11-11
Registered on purpose to thank you, chili555! :)

P.S: for noobs like me, also works on eMachines e525

---

### Post by PlayStationTiger on 2012-12-05
> **chili555 said:**
> You are very welcome! Thanks for the kind words and the beers. I'm glad it's working.

Hi,

I only registered to say that I found this thread via Google and it seems to work.

You are the man, many thanks!

---

### Post by janekapmann on 2013-03-25
Hello all,

It doesn't work for me. After I install linux-header-generic , then "sudo apt-get install --reinstall bcmwl-kernel-source" .  I still get error :
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-27-generic/updates/dkms/


depmod....


DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Error inserting wl (/lib/modules/3.5.0-27-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-27-generic


Any others clue please ?

---

### Post by chili555 on 2013-03-25
> FATAL: Error inserting wl (/lib/modules/3.5.0-27-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)Do you have linux-backports-modules-cw installed?```
sudo dpkg -s linux-backports-modules-cw-3.6-quantal-generic
```If it is installed, remove it and try again:```
sudo apt-get remove --purge linux-backports-modules-cw-3.6-quantal-generic
sudo apt-get remove --purge linux-backports-modules-cw-3.6-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by BorisFindell on 2013-03-29
> **chili555 said:**
> Feel that little itch right there? That's known as a bug! You lucky Ubuntu person!

Ideally, if the kernel source were not installed, apt would...do what?...*install it!* Let's help it along:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
iwconfig
```*Now* do we have wireless?


Excelente! Me anduvo a la perfección! Gracias!!

Boris

---

### Post by oletorp on 2013-05-07
> 
sudo apt-get install linux-headers-generic  
sudo apt-get install --reinstall bcmwl-kernel-source

Re-installing  following these guidelines helped me out as well after experiencing a similar problem after upgrading to UBUNTO 13.04. 

Cheers!
Otl

---

### Post by praveenmg on 2013-05-21
Hi I am using Toshiba PORTEGE R930
I am very new to UBUNTU and I followed steps in this post but I couldn't solve the problem

Any help will be greatly appreciated............

Thank You in advance

for this command 
[B]
lspci -nn | grep 0280[/B]

I got this output

**04:00.0 Network controller [0280]: Intel Corporation Device [8086:088e] (rev 24)**

For this command
 
[B]rfkill list all
[/B]
I got the following output

[B]0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no[/B]

---

### Post by chili555 on 2013-05-21
> **praveenmg said:**
> Hi I am using Toshiba PORTEGE R930
I am very new to UBUNTU and I followed steps in this post but I couldn't solve the problem

Any help will be greatly appreciated............

Thank You in advance

for this command 
[B]
lspci -nn | grep 0280[/B]

I got this output

**04:00.0 Network controller [0280]: Intel Corporation Device [8086:088e] (rev 24)**

For this command
 
[B]rfkill list all
[/B]
I got the following output

[B]0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no[/B]You don't have a Broadcom wireless device, so none of this helps you. Please start a new thread and tell us what is not working and what you tried that we may have to undo.

---

