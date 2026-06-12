---
title: "Network Disabled"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by cpusa on 2011-08-06
Gateway computer. New Hard drive, Ubuntu 11.04 installed. Only element on computer. Nothing else. Cannot connect to Internet. Info is:
*Network Disabled
Logical Name: wlano
Serial# 00:1a:73:05:aa:5f
Broadcast: yes
Driver: b43
Drv Version: 2.6.38-8 generic f1
rimware: N/A
Multicast: yes
Wireless: IEEE 802.11 dg

Now what? I'm brand new to ubuntu.

---

### Post by wildmanne39 on 2011-08-06
Hi, run these commands in a terminal please by hitting ctrl+alt+t then copy and paste the commands.
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod | grep b43
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by cpusa on 2011-08-06
I did your suggested list and it appears that each step was doing what it was supposed to do. But, when I called up Firefox, it didn't connect to the Internet.

I guess the next step is setting up the wireless code.

My network is 2WIRE817
Network Key: 2241419298

The wireless network serves to other computers well. I'm trying ubuntu on a third (laptop).

---

### Post by wildmanne39 on 2011-08-06
Hi, I need you to post the results here so I can see them.
Thank you

---

### Post by Basher101 on 2011-08-06
you got the wrong idea of the commands. those commands show any configuration of hardware and software related to internet connections, so you can copy and paste them here so we can look at them and see where the problem is.

edit: damn im typing slow..

---

### Post by cpusa on 2011-08-07
Sorry, didn't understand. I thought the commands were to cure the problem. Anyway, your routine says "copy and paste." I'm writing here on my HP Internet connected notebook. I can't copy from the ubuntu Gateway notebook and paste to this HP notebook. Before I start typing the results "by hand" is there some way I'm missing?

---

### Post by wildmanne39 on 2011-08-07
Hi, if you have a flash drive you can copy to it then transfer it to the computer with the internet connection then paste here.

We really need the information to help you.
Thank you

---

### Post by hakermania on 2011-08-07
> **cpusa said:**
> Sorry, didn't understand. I thought the commands were to cure the problem. Anyway, your routine says "copy and paste." I'm writing here on my HP Internet connected notebook. I can't copy from the ubuntu Gateway notebook and paste to this HP notebook. Before I start typing the results "by hand" is there some way I'm missing?
You can also connect via LAN

---

### Post by cpusa on 2011-08-07
sam@sam-ML6703:~$ lspci -nn | grep 0280 
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
sam@sam-ML6703:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
           
sam@sam-ML6703:~$ rfkill list all 
0: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
sam@sam-ML6703:~$ lsmod | grep b43 
b43                   296610  0 
mac80211              257001  1 b43 
cfg80211              156212  2 b43,mac80211 
ssb                    45942  1 b43 
sam@sam-ML6703:~$

---

### Post by wildmanne39 on 2011-08-07
Hi, all that looks good.
Please run these commands and post the results here.
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
dmesg | grep b43
```
```
nm-tool
```
Do you have a wired connection in ubuntu?
Thank you

---

### Post by cpusa on 2011-08-07
I do not have a wired connection with the laptop computer that ubuntu is on.

sam@sam-ML6703:~$ dmesg | grep wlan0  
 sam@sam-ML6703:~$ sudo iwlist scan  
 [sudo] password for sam:  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wlan0     Interface doesn't support scanning : Network is down  
 

 sam@sam-ML6703:~$ dmesg | grep b43  
 [    1.117009] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [    1.117026] b43-pci-bridge 0000:03:00.0: setting latency timer to 64  
 [   11.769426] b43-phy0: Broadcom 4311 WLAN found (core revision 10)  
 [   11.952995] Registered led device: b43-phy0::tx  
 [   11.953121] Registered led device: b43-phy0::rx  
 [   11.953237] Registered led device: b43-phy0::radio  
 [   13.633670] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found  
 [   13.633677] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found  
 [   13.633681] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.  
 [ 7088.892923] b43-pci-bridge 0000:03:00.0: PCI INT A disabled  
 [ 7089.713274] b43-pci-bridge 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)  
 [ 7089.713304] b43-pci-bridge 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd6000000)  
 [ 7089.713313] b43-pci-bridge 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)  
 [ 7089.713323] b43-pci-bridge 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)  
 [ 7089.718554] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [ 7092.754857] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found  
 [ 7092.754864] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found  
 [ 7092.754869] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.  
 sam@sam-ML6703:~$ nm-tool  
 

 NetworkManager Tool  
 

 State: disconnected  
 

 - Device: eth0 -----------------------------------------------------------------  
   Type:              Wired  
   Driver:            sky2  
   State:             unavailable  
   Default:           no  
   HW Address:        00:E0:B8:C3:2B:C5  
 

   Capabilities:  
     Carrier Detect:  yes  
 

   Wired Properties  
     Carrier:         off  
 

 

 - Device: wlan0 ----------------------------------------------------------------  
   Type:              802.11 WiFi  
   Driver:            b43  
   State:             unavailable  
   Default:           no  
   HW Address:        00:1A:73:05:AA:5F  
 

   Capabilities:  
 

   Wireless Properties  
     WEP Encryption:  yes  
     WPA Encryption:  yes  
     WPA2 Encryption: yes  
 

   Wireless Access Points  
 

 

 sam@sam-ML6703:~$

---

### Post by wildmanne39 on 2011-08-07
Hi, I am going to give you a zip file put it on your flash drive.

Down load the file to your flash drive then drag and drop the file to your ubuntu desktop. 

Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```

Just copy and paste the commands.

This should get your wireless working.
Thank you

---

### Post by cpusa on 2011-08-08
Hello and thanks. I now have wireless. I guess, in a way, Ubuntu has a few more versions to create because there was no way an average user could have found the answer you gave me without being a serious tech person.

Thanks again.

Sam

Visit us at [www.conservativepartyusa.com](www.conservativepartyusa.com)

---

### Post by wildmanne39 on 2011-08-08
Hi, your welcome! I am glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

WE can thank chili555 because everything I know I have learned from him.

---

### Post by paddydog on 2011-08-08
hi there
i also upgraded to 11.4 and had issues getting online wirelessly so followed advise on this forum and using Synaptic uninstalled b-43fwcutter then installed firmware-b43installer and here I am surfing wirelessly. Enjoy and thanks to forums

---

### Post by wildmanne39 on 2011-08-08
Hi, I am glad I could help.

---

### Post by Mikaelm on 2011-12-13
Hi, 

I've been using linux for 4 days now and i cant really figure out what ive been doing wrong, I have the exact same problem, but im using a realtek rtl-8169 wireless usb adapter and no wired connections. I have ubuntu 11.10 server edition so its only terminal and no internet.

I would really appreciate any help at all, I have the cd for drivers but no clue how to install..

---

