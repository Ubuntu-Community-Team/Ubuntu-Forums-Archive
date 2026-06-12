---
title: "wireless/mac address issue"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by sks24 on 2010-07-09
Got a wireless connection issue with an 10.04 installation on a 32 bit HP DV2125 with a usb wireless dongle (Nubbin Nvix). 

I can get the Ubuntu partition to connect to the wireless network, but no pages will load. ifconfig shows the mac address as the same as it is on the Windows side, which will both connect to the network and load pages. I can also connect the ethernet cable directly to the laptop while in the Ubuntu partition and pages will load. The Ubuntu partition is fully updated. 

It's a long story as to why we're using mac addressing filters. Basically, all the laptops in the house will not connect to this particular router using WPA or even WEP security. 

All advice appreciated.

Thanks in advance,
Scott

---

### Post by sks24 on 2010-07-09
I meant to add that turning off all security on the router makes no difference: all other laptops can connect to the network and load pages, but not the Ubuntu partition on this DV2125.  The Windows side does fine, whether the security is on or not.

---

### Post by sks24 on 2010-07-10
this is my father's laptop, and it's the second time in as many months months that I've had to restore the Windows image I made for him awhile back due to malware.  He's all for living in Ubuntu if I can get him online with it . . . (hint, hint)

---

### Post by sks24 on 2010-07-10
If I may, let me approach the issue from a different angle: what might be some of the causes of the following problem:  you've got an installed and updated Ubuntu (in this case 10.04) installation.  The drivers for the Wi-Fi radio detect and connect to your wireless router, which, for security, is running mac address filtering.  You've told the router what your mac address is, and you know that the router "knows" this because, in the Windows partition on the same computer, the wi-fi both connects and pages will load in browsers.

But, on the Ubuntu side, while the interface shows a full internet connection, pages in browsers will not load.  There can be no doubt but that the issue is one of software, and almost certainly a software issue related to the Ubuntu wireless drivers.  (A direct ethernet connection on the Ubuntu side will allow for loading pages.)

Removing mac address filtering - making the router completely open - does not fix the problem, either.  

What's the next step w/r/t solving such a problem?  How would one go about determining its cause?

I removed and reinstalled Ubuntu from another ISO last night, and still the same problem is occurring.   

Thanks in advance for your time and consideration,
Scott

---

### Post by cavalier911 on 2010-07-11
**Copy/paste the output from the following commands**
[LIST=1][*]sudo lsusb[*]sudo ifconfig wlan0[*]sudo lshw -C network[*]sudo iwlist scanning[*]sudo iwconfig wlan0[*]sudo cat /proc/net/wireless[*]ping -c 10 wireless.router.gateway.ip[*]ping -c 10 8.8.8.8[*]ping -c 10 from.another.computer.on.lan@this computers.ip[*]
Please copy/paste the long output of:
```
sudo lsmod
```
to [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and copy the browser address of the paste into your reply.[/LIST]

---

### Post by sahilsameerac on 2010-07-11
If you have problem with wireless networkand if it is showing connection established and pages are not loded. the wireless card is not detected. you wan't to install driver. you can download windows wireless driver named software from ubuntu software centre. the put the driver cd. after installing windos wireless network, go to system/administration/ windows wireless driver. select the driver in the cd. the select install driver option. create a wireless network and restart your system. you can load pages. best of luck. enjoy

---

### Post by sks24 on 2010-07-11
Thank you both very much.  I'm home now, but later this week I'll head out that way and run the commands you suggest.  I'll go ahead and uninstall and reinstall the wireless drivers, too.    

Again, thanks,
Scott

---

