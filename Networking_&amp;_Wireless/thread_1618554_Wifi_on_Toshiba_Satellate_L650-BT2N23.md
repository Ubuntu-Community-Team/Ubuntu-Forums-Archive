---
title: "Wifi on Toshiba Satellate L650-BT2N23"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by harris.sw on 2010-11-10
**Ubuntu on Toshiba Satellite L650-BT2N23** 			
 			 			 		   		 		 		I am new to  Ubuntu and was given a Toshiba Satellite L650-BT2N23 that I was hoping  to use Ubuntu on.  I installed 10.10 but wifi, the integrated intel  graphics, and the SD card reader don't seem to work.  

First I need to get wifi working; from looking around the forums I tried  booting from a livecd, but no wifi card seen.  I tried proprietary  drivers but none were found. I did an lspci -nn and got the following:

:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5  Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath  Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

How do I find the right driver?  
Thanks for any help!

---

### Post by chili555 on 2010-11-10
> 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [[COLOR="Red"]10ec:8176[/COLOR]] (rev 01)Please see here:  [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)

Especially see the last three posts.

Post back if you get stuck.

---

### Post by harris.sw on 2010-11-11
Worked like a charm!! Thank you so much...I am replying with a wifi connection.  It came up easily on the restart.

---

### Post by chili555 on 2010-11-11
Great job. Glad it's working for you. Have fun!

---

### Post by agbarthel on 2011-02-28
Thank you so much for the help. This fix worked perfectly for my Toshiba NB505 as well.

---

### Post by olamina on 2011-04-11
This worked great for my Toshiba NB505. Thanks so much. I love Ubuntu precisely because of this fabulous community!

EDIT: And then it stopped working after reboot...gotta figure out what's wrong. As much as I hate Windows, I am glad I am duel booting otherwise I'd be internet-less. What a frickin bummer.

---

### Post by altometer on 2011-07-21
I can confirm this also worked for a Toshiba Satellite L775D-S7222 THANKS!

---

### Post by msrk on 2011-09-21
Hi,
I have a Toshiba NB505 Netbook/Ubuntu Natty with the Rtl8192ce net card.  I use it on Columbia University campus a lot.  However, the network connection drops a lot, very annoying.  A MS Windows friend of mine suggested switching the net card mode from N to G.  He claims to have lots of flaky problems with N.

I'd like to try this.  How can I configure my netcard to use G-Mode only?

Thank you.

---

### Post by chili555 on 2011-09-21
> **msrk said:**
> Hi,
I have a Toshiba NB505 Netbook/Ubuntu Natty with the Rtl8192ce net card.  I use it on Columbia University campus a lot.  However, the network connection drops a lot, very annoying.  A MS Windows friend of mine suggested switching the net card mode from N to G.  He claims to have lots of flaky problems with N.

I'd like to try this.  How can I configure my netcard to use G-Mode only?

Thank you.You might try:```
sudo iwconfig wlan0 rate 54M auto
```If it is helpful, make it persistent with:```
sudo gedit /etc/rc.local
```Add a line above exit 0:```
iwconfig wlan0 rate 54M auto
```

---

### Post by msrk on 2011-09-22
Hi,

Thank you for the reply. I just had a chance to try it but it did not help.  The wireless connections continue to drop.  This is frustrating.  This computer and netcard work well with a g-router in my house but not in the Columbia libraries.  I expect the Columbia equipment should be good.

Please advise.

Thank you.

---

### Post by chili555 on 2011-09-22
Would you please also try:```
sudo iwconfig wlan0 modu 11g
```

---

### Post by msrk on 2011-09-22
Thank you again.   This is what happened:

ms@BlueBook:~$ sudo iwconfig wlan0 modu 11g
[sudo] password for ms: 
Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan0 ; Operation not supported.
ms@BlueBook:~$ 

ms@BlueBook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
ms@BlueBook:~$ 

Any other ideas would be appreciated.

---

### Post by chili555 on 2011-09-22
I am sorry, I have no more ideas. You might start a new thread and refer to G speeds in the thread title in case someone has a better idea.

---

