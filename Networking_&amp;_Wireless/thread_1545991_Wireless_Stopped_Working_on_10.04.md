---
title: "Wireless Stopped Working on 10.04"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by Debian1 on 2010-08-04
Hello my Ubuntu friends...I have a wireless issue that I need some help with.
 

 Issue:
 Just recently the wireless stopped working on Ubuntu 10.04. The machine is AcerOne AOA-150.
 I did notice recently the wireless would stop working, and I would need to either 1) reboot 2) switch the wireless off by moving the switch from left to right in front of the laptop.
 

 However, this time nothing is working. I've provided some detail and if more information is needed, let me know.
 

 LSPCI:
 

 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) 
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 
 00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) 
 00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) 
 00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02) 
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 
 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
 03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
 

 IWCONFIG:
 

 wlan0     IEEE 802.11bg  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Encryption key:off 
           Power Management:off 
            
 

 MESSAGE Log File:
 

 I see multiple messages referring to WLAN0
 Aug  4 11:52:56 laptop kernel: [   26.763965] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by Shompol on 2010-08-04
Try this, worked like magic for both of my computers with Atheros cards:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2404068.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2404068.html)

---

### Post by Debian1 on 2010-08-04
> **Shompol said:**
> Try this, worked like magic for both of my computers with Atheros cards:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2404068.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2404068.html)

  Thanks for replying I have checked router configuration and the encryption is set to ONLY AES.

---

### Post by Debian1 on 2010-08-05
> **Debian1 said:**
> Thanks for replying I have checked router configuration and the encryption is set to ONLY AES.


My router is already configured Correctly. All other machines that are wireless are working as designed to.

I really don't feel like reinstalling the OS to fix a wireless issue.

Any help would be much appreciated.

---

### Post by Debian1 on 2010-08-13
OK...I'm back online (wireless) with Ubuntu 10.04 and Acer AOA-150. I think Network Manager some how got corrupted and caused the internal wireless chip set from working properly.

Anyways...If you remove Network Manager from the GUI (Ubuntu Software Center), this seems to not remove all the dependencies. So, I had to manually remove the program via command line.

1) sudo aptitude remove network-manager (you will be prompted for your password)
2) After successfully removing network-manager DO NOT reboot your machine. Shut it down. I tried re-booting and I still had problems.
3) Next, After logging back into Ubuntu search for the following wireless management tool called WICD. This program can be found within Ubuntu Software Center
4) After successfully installing WICD I setup my WPA encryption and network configuration and now I"M BACK!

FYI...During the setup if you receive an error message about "Bad Password" don't panic. This has nothing to do with a password, but with your ESSID. Open WICD and click the NETWORK Button and select Find Hidden Network. Enter your ESSID and you should be good to go.

I love finding the root cause of my own problems. I hope this helps others.

---

