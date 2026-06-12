---
title: "No wifi in ubuntu using DWA-131"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by ashikns on 2012-04-30
I have not been able to connect wifi ever from my desktop. I used backtrack 5 first. In it wicd showed "bad password". In ubuntu 11.10 and 12.04 wifi does not get connected at all. The router uses WPA-PSK TKIP. It does not support AES. Please help!!! Also the OS I use are 64 bit versions

---

### Post by nothingspecial on 2012-05-01
*Thread moved to **Networking & Wireless**.*

---

### Post by TBABill on 2012-05-01
Is this a USB device or PCI? Depending on which, run one of these in a terminal to see how Linux identifies the device and paste the info back so we can know what chipset you are using: ```
lsusb | Network
lspci | Network
```

---

### Post by kurt18947 on 2012-05-01
This is odd.  I have the same device, Dlink DWA-131.  I just unplugged  a Netgear WiFi adapter, plugged the Dlink in, entered the passwords and it connected. This is on 12.04.   Does your device work on other distros or other machines?  If so, you might try running a live install and see if the Dlink works there.  You need to try to figure out if it's a hardware problem or software problem.  The device has been plug -n- play in Ubuntu since 11.04 I believe so should work in a live install with no additional fussing.

Additional thought: 
 Here is my output from the "lsusb" command.
```
Bus 001 Device 006: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(**rev.A1**) [Realtek RTL8192SU]
```
I wonder if Dlink has used more than one chipset in this model.  I recall another poster having a problem with the same model adapter and don't know if he ever did solve his problem.  When I checked the chipset on wikidevi it shows "RTL-8191SU", not my "RTL-8192SU".  Somewhere in the infrequently accessed reaches of my brain I seem to recall the RTL-8191SU being difficult.

---

### Post by ashikns on 2012-05-02
> **kurt18947 said:**
> This is odd.  I have the same device, Dlink DWA-131.  I just unplugged  a Netgear WiFi adapter, plugged the Dlink in, entered the passwords and it connected. This is on 12.04.   Does your device work on other distros or other machines?  If so, you might try running a live install and see if the Dlink works there.  You need to try to figure out if it's a hardware problem or software problem.  The device has been plug -n- play in Ubuntu since 11.04 I believe so should work in a live install with no additional fussing.

Additional thought: 
 Here is my output from the "lsusb" command.
```
Bus 001 Device 006: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(**rev.A1**) [Realtek RTL8192SU]
```
I wonder if Dlink has used more than one chipset in this model.  I recall another poster having a problem with the same model adapter and don't know if he ever did solve his problem.  When I checked the chipset on wikidevi it shows "RTL-8191SU", not my "RTL-8192SU".  Somewhere in the infrequently accessed reaches of my brain I seem to recall the RTL-8191SU being difficult.

Well I haven't tested the device from another machine, but I dual boot windows on the same machine and the device works perfectly. So I doubt it's a hardware problem. And no, it didn't work on a live boot either

---

### Post by kurt18947 on 2012-05-02
> **ashikns said:**
> Well I haven't tested the device from another machine, but I dual boot windows on the same machine and the device works perfectly. So I doubt it's a hardware problem. And no, it didn't work on a live boot either

Have you run the commands that TBA Bill requested?  I'd be curious to know what 'lsusb' shows.  If it's not an RTL8192SU device, it might be worth looking on RealTek's site for a driver.  The fact your device doesn't 'just work' on distros 11.04 and later makes me think it's a different chipset than I have.  There WAS an easily fixed problem with this chipset on 10.10 and prior.

---

### Post by ashikns on 2012-05-02
Hey guys sorry for the late reply. Had exams:)
Here are the results of the commands.

diablo@diablo-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 002: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]
Bus 002 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
diablo@diablo-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Juniper HDMI Audio [Radeon HD 5700 Series]
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 SATA controller: JMicron Technology Corp. JMB362 SATA Controller (rev 10)
diablo@diablo-PC:~$

---

### Post by kurt18947 on 2012-05-03
I'm not sure what to tell you.  Yours appears identical to mine - same revision # and showing RealTek 8192SU chipset - and mine works fine.  The only thing different I notice is that you have USB3 ports.  I wonder if there's some sort of incompatibility?  This is only speculation on my part,  I've not heard of any such problem.  If you haven't done so, maybe try a different USB port?  Perhaps someone else has a thought.

---

