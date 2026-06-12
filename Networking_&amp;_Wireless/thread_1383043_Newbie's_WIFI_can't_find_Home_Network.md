---
title: "Newbie's WIFI can't find Home Network"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by JeffSC on 2010-01-16
I'm new to Linux and Ubuntu 9.10.  I have installed Ubuntu 9.10 on an older Compaq Presario 6100.  Initially my built in wireless was not working.  I searched the forum and was able to get my wireless working (I think) by installing the BCM43XX driver.  I assume that works on my computer since I believe the BCM4306 driver is needed.  Anyway, assuming my wireless is working, my home network does not show up in the pick list when I go to network<wireless.  

I've spent a couple of hours already researching this and up someone can help me out.  I would really like to give this new system a try.

Thanks,
Jeff

---

### Post by gordintoronto on 2010-01-16
Right-click the network manager icon, select "edit connections," open the wireless tab, click on "add."  You will need to enter your router's ID, the type of encryption and the router's password.

To confirm that you have a BCM 43xx, open accessories/terminal, and enter the command:
lspci

Welcome aboard!

---

### Post by MarkC502 on 2010-01-16
Also try the command iwconfig in a terminal and it will list all your network devices and whether they are wifi devices or not, if it says no wifi then you have no wifi so check that command as well.

---

### Post by JeffSC on 2010-01-17
Thanks.  My wireless is working.  I connect to my router but FireFox can not make a connection.  It tells me to check my fiewall or network proxy.  Any suggestions?

---

### Post by JeffSC on 2010-01-17
When I run iwconfig I get the below-

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Keadle's Belkin54g"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 16:04:39:80:E6:4E   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by JeffSC on 2010-01-17
See resutlsfor lspci-

 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by gordintoronto on 2010-01-17
> **JeffSC said:**
> Thanks.  My wireless is working.  I connect to my router but FireFox can not make a connection.  It tells me to check my fiewall or network proxy.  Any suggestions?

I assume you are using DHCP, where the router gives you DNS server addresses?  You can check this with the command:
cat /etc/resolv.conf

If you use a static IP address, you will need to specify DNS servers in Network Manager.

---

