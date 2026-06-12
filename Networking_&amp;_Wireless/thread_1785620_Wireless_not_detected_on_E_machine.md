---
title: "Wireless not detected on E machine"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2011-06-18
[FONT=Times New Roman][SIZE=4]Wireless not detected [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]I'm on **[COLOR=#dd4814]Ubuntu[/COLOR]** **[COLOR=#dd4814]11[/COLOR]**.04 64-bit. I am using an E machine laptop with a duel boot Win XP and **[COLOR=#dd4814]Ubuntu[/COLOR]**. Both systems work great, the XP can go on line with a touch of the Fn and F2 keys but the **[COLOR=#dd4814]Ubuntu[/COLOR]** mode will not. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I do not have a manual switch or button to activate the wireless. I don’t want to mess up the windows XP Fn, F2 connection when I boot into XP. What should I do to connect **[COLOR=#dd4814]Ubuntu[/COLOR]** to the Internet?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Are there other keys to activate wireless in **[COLOR=#dd4814]Ubuntu[/COLOR]** or the wireless (addresses) routers in my area?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Is there a directory of key combinations that work with **[COLOR=#dd4814]Ubuntu[/COLOR]**?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I used Ctrl, Alt and 6 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]rfkill list [/SIZE][/FONT][FONT=Times New Roman][SIZE=4]to find that. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Wireless Lan[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Soft blocked: no[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Hard blocked: no[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I am using a Linksys Router.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]I can connect **[COLOR=#dd4814]Ubuntu[/COLOR]** with a wired connection but not wireless. My drivers are up to date.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=4]Sorry for the rambling, just a newbie question that I cannot find an answer that fits without me worrying about messing things up.[/SIZE][/FONT]

---

### Post by chili555 on 2011-06-18
> My drivers are up to date.Let's have a look. Is it a built-in wireless device? If so, please post:```
lspci -nn
iwconfig
```If it's a USB device, post:```
lsusb
```Thanks.

---

### Post by SUPERFITTER on 2011-06-18
This is what I have:
 
dennis@dennis:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge [1106:3188] (rev 01)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:0a.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410]
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
00:13.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
 
 
dennis@dennis:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEEE 802.11bg ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
 
dennis@dennis:~$

---

### Post by chili555 on 2011-06-18
We're getting closer! Now, let's see:```
rfkill list all
dmesg | grep b43
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by SUPERFITTER on 2011-06-19
dennis@dennis:~$ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
 
dennis@dennis:~$ dmesg | grep b43
[ 1.176044] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 23.934955] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[ 24.033538] Registered led device: b43-phy0::tx
[ 24.033630] Registered led device: b43-phy0::rx
[ 24.033725] Registered led device: b43-phy0::radio
[ 24.144481] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 24.144487] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[ 24.144491] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
dennis@dennis:~$

---

### Post by chili555 on 2011-06-19
Your wireless is not working because the required firmware is not installed. Can you hook up a temporary ethernet cable and do:```
sudo apt-get install b43-fwcutter
```After it's done, detach the cable and reboot. Your wireless should be working.

---

### Post by SUPERFITTER on 2011-06-19
[SIZE=3][sudo] password for dennis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 145 not upgraded.
Need to get 14.6 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main b43-fwcutter i386 1:013-3 [14.6 kB]
Fetched 14.6 kB in 0s (30.7 kB/s) 
Selecting previously deselected package b43-fwcutter.
(Reading database ... 129532 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
dennis@dennis:~$ 

[SIZE=4]Sorry. No luck yet.[/SIZE][/SIZE]

---

### Post by chili555 on 2011-06-19
Did you reboot? Please post:```
dmesg | grep b43
```

---

### Post by SUPERFITTER on 2011-06-19
[FONT=Times New Roman][SIZE=4]Yes I rebooted three times and tried the Fn, F2 key but no responce.

dennis@dennis:~$ dmseg | grep b43
No command 'dmseg' found, did you mean:
 Command 'mmseg' from package 'sunpinyin-utils' (universe)
 Command 'dmesg' from package 'util-linux' (main)
dmseg: command not found
dennis@dennis:~$ [/SIZE][/FONT]

---

### Post by chili555 on 2011-06-20
Please try:```
sudo modprobe b43
[COLOR="Red"]dmesg[/COLOR] | grep b43
```Thanks.

---

### Post by SUPERFITTER on 2011-06-20
[SIZE=4]dennis@dennis:~$ sudo modprobe b43
[sudo] password for dennis: 


dennis@dennis:~$ dmesg | grep b43
[    1.168423] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   23.873487] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   24.001771] Registered led device: b43-phy0::tx
[   24.001861] Registered led device: b43-phy0::rx
[   24.001953] Registered led device: b43-phy0::radio
[   24.103332] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   24.103336] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   24.103339] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
dennis@dennis:~$ [/SIZE]

---

### Post by chili555 on 2011-06-20
Let's try a different approach:```
sudo apt-get install firmware-b43-installer
```Thanks.

---

### Post by SUPERFITTER on 2011-06-20
[SIZE=4]2011-06-20 23:36:05 (212 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794]

This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
dennis@dennis:~$ [/SIZE]

---

### Post by SUPERFITTER on 2011-06-20
[SIZE=4]Getting close.  

Laptop shows that my wireless connection light is on, but when I try to get on line I get 'Server not found'. I turned off and turned on the laptop three times[/SIZE] [SIZE=4]with the same results[/SIZE].:)

---

### Post by chili555 on 2011-06-21
Turn your computer on, connect to wireless, open the terminal and let me see:```
ifconfig
dmesg | grep b43
cat /etc/resolv.conf
```Thanks.

---

### Post by SUPERFITTER on 2011-06-21
[SIZE=4]eth0      Link encap:Ethernet  HWaddr 00:03:25:10:cf:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xec00 

lo        Link encap:Local Loopback  [/SIZE] [SIZE=4]
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26256 (26.2 KB)  TX bytes:26256 (26.2 KB)

dennis@dennis:~$ dmesg | grep b43[/SIZE] [SIZE=4]
[    1.171577] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.161483] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   24.252868] Registered led device: b43-phy0::tx
[   24.252958] Registered led device: b43-phy0::rx
[   24.253050] Registered led device: b43-phy0::radio
[   25.148044] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   25.236637] b43-phy0: Radio hardware status changed to DISABLED
dennis@dennis:~$ cat /etc/resolv.conf
# Generated by NetworkManager
dennis@dennis:~$

[/SIZE][SIZE=4]No wireless connection light[/SIZE] now.

---

### Post by chili555 on 2011-06-21
> Radio hardware status changed to DISABLEDI wonder what caused this? Has this changed?```
rfkill list all
```Is there a key combination or switch? Is there an LED? Is it blue, red, orange off??

---

### Post by SUPERFITTER on 2011-06-21
[SIZE=4]dennis@dennis:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
dennis@dennis:~$ 


 Key combination (Fn, F2), LED is blue and after holding them down the blue light came on, but can't connect. 

Server not found.[/SIZE]

---

### Post by chili555 on 2011-06-21
> **SUPERFITTER said:**
> [SIZE=4]dennis@dennis:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
dennis@dennis:~$ 


 Key combination (Fn, F2), LED is blue and after holding them down the blue light came on, but can't connect. 

Server not found.[/SIZE]After the blue LED comes on, does rfkill report hard blocked is no? If so, can you click the Network Manager icon and see networks? Can you see yours, click it and connect? It won't connect automagically to any old possibly insecure network. You must direct it.

---

### Post by SUPERFITTER on 2011-06-21
[SIZE=4]I went to: Home Folder>Network>Windows Network and got this: Unable to mount location. Failed to retrieve share list from server[/SIZE]
[SIZE=4]
dennis@dennis:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
dennis@dennis:~$ [/SIZE]

---

### Post by chili555 on 2011-06-21
> I went to: Home Folder>Network>Windows Network and got this: Unable to mount location. Failed to retrieve share list from serverThat's not Network Manager.

Network Manager is accessed by clicking an icon at the top right that looks like a cone when you are not connected. Click it and see a list of networks. Click your network and connect. Please see attached. In the attached example, my network is GBR1.

---

### Post by SUPERFITTER on 2011-06-22
[SIZE=4]Chili 555
Thank you for your time and patience helping me with my Ubuntu wireless connection.  Sorry I didn't know where Network Manager[/SIZE][SIZE=4] is located.  This looks like a great operating system and in the last few days I have had this system I have learned a lot. This laptop is seven years old and with a duel boot and more memory will  live on a few more years hopefully. Can you recommend any books that have the different codes for Ubuntu. I would like to learn more about this system.
Thank You
Dennis[/SIZE]

---

### Post by chili555 on 2011-06-22
Dennis. I'd love to know that you connected your wireless and you are happily surfing, downloading mp3s and grabbing those torrents. Did you?

I haven't read a Linux book in a few years, but my friends tell me this is a pretty good one.  [http://www.amazon.com/Ubuntu-Unleashed-2011-Covering-10-10/dp/0672333449/ref=sr_1_1?ie=UTF8&qid=1308775441&sr=8-1](http://www.amazon.com/Ubuntu-Unleashed-2011-Covering-10-10/dp/0672333449/ref=sr_1_1?ie=UTF8&qid=1308775441&sr=8-1)

It's a bit spendy; you might shop around.

---

### Post by SUPERFITTER on 2011-06-22
[FONT=Times New Roman][I][SIZE=4]Dennis. I'd love to know that you connected your wireless and you are  happily surfing, downloading mp3s and grabbing those torrents. Did you?

[/SIZE][/I][SIZE=4]Yes I did, I have turned it on and off about six times and no problems so far. When I change the ram from half a gig to 1 and a quarter it will fly. 

Thank you again[/SIZE][I][SIZE=4]
[/SIZE][/I][/FONT]

---

