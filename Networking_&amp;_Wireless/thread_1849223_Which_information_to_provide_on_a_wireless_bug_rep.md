---
title: "Which information to provide on a wireless bug report?"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by Xavi López on 2011-09-24
I own a Belkin wireless USB adapter. It seems to be supported  by the rtl8192cu driver in 11.10 betas, which is great, because in  11.04 the driver had to be compiled/installed manually. But, nobody is  perfect, and I seem to have some driver-related problems with the  dongle. 
  It seems that it is able to connect only after several retries  (taking the dongle out and plugging it in another port), or after a  reboot, or sometimes at the first boot.
  I don't know how to diagnose this wireless things from the command  line, so I'll tell you what I see in Kubuntu's network manager: When it  can't connect, it says "Configuring interface" for a loong time, and  then sometimes "Waiting for authorization". Nothing else. 
  What I'm asking is: 
  
[LIST=1]
[*]What type of information (logs, traces, etc), and
[*]How do I exactly get it (where is it, is there a special command like *dmesg*),
[/LIST]
  in order to
  
[LIST=1]
[*]try to troubleshoot the problem myself (or with some help form some of you =),
[*]Have better chances to spot a duplicate bug report.
[*]Provide that information in a new bug report.
[/LIST]
  I'd appreciate as much information as possible regarding this matter,  because I've never done it but I've already needed it in the past.

---

### Post by praseodym on 2011-09-24
Hi,

please show:

```
lsusb
lsmod
iwconfig
rfkill list
dmesg | egrep 'rtl8|r8'
sudo iwlist scan
iwlist chan
```
Did you install the package **linux-firmware**?

---

### Post by Xavi López on 2011-09-24
Hi, praseodym, here is the info you required: [http://tinypaste.com/5b30b6. ]("http://tinypaste.com/5b30b6")It's been extracted now, when the dongle is working, but in this session it didn't work at first. You can see that in *dmesg* i think, but there's no tip there. I'll try to reboot now and provide this information when the dongle is not working.

Also, I can tell you that I've got linux-firmware installed and up to date. I don't have linux-firmware-non-free, but I don't think it's necessary.

---

### Post by praseodym on 2011-09-24
1. ) Try wicd instead of the network-manager:

```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver.

2.) and/or change to WPA2-AES (CCMP) encryption.

---

### Post by Xavi López on 2011-09-24
Here is the same information, with the dongle **not** working. [http://tinypaste.com/f8f269. ]("http://tinypaste.com/f8f269")

Thanks for the wicd tip! I'll tell back how it worked. I'll also try to switch to WPA-AES encryption, I just hope my other devices that access the wlan support it.

---

### Post by Xavi López on 2011-09-27
I've tried wicd. The connection doesn't seem to improve, on the contrary, now it seems impossible to connect. It might have something to do with WPA encryption, I see this repeating alot of times on the wicd.log, and it's the thing it prints on the log while it is 'hanged up': 
```
WPA_CLI RESULT IS INACTIVE
```
(followed by ifconfigs).

I'll try changing encryption to wpa2-AES.

---

### Post by Xavi López on 2011-10-01
Finally, after trying with wpa2 psk, wicd, and a fresh install of 11.10 beta2, the issue is still there. wicd.log shows WPA_CLI STATUS IS ASSOCIATING and shortly after, WPA_CLI STATUS IS SCANNING. 

There seems to be an issue with rtl8192cu and wpa/wpa2 psk (at least with my belkin surf n150 usb nic), so I've created this bug report with apport: 

```
https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/862684
```

Everyone having this same issue, please reflect it in the bug with 'also affects me'. And if you have the time, feel free to improve the information on the report, it's my first one and don't know if it has been reported correctly :)

---

