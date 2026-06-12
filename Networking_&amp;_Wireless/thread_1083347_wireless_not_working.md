---
title: "wireless not working"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by crotherm on 2009-02-28
Hi,

Running 8.04 with a D-link 1320.  Wireless worked once.  On reboot, I cannot get it back up.  Any help would be appreciated.

below is output of lspci and iwconfig

thanks

mark



[SIZE="2"][SIZE="1"]patrick@patrick-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0f.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:13.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
patrick@patrick-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dale's Network"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:52:7B:37:D3   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-41 dBm  Noise level=-91 dBm
          Rx invalid nwid:4417  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


[/SIZE][/SIZE]

---

### Post by sailthesea on 2009-02-28
Can you see your network in network manager?

---

### Post by Venlaar on 2009-02-28
Have you tried blacklisting ipv6? I had to do that to get mine to work. I had exactly the same problem. After blacklisting ipv6 it worked. From what I understand most routers on the currently 1pv4 networks don't know how to handle ipv6 very well. You will find it under /etc/modprobe.d/blacklist.

---

### Post by sgosnell on 2009-03-01
"can't get it back up" isn't very descriptive.  Exactly what symptoms are you having?  The log you posted shows that the network is seen, but the password may be incorrect.  Have you tried editing the connection and putting in the correct password?

---

### Post by crotherm on 2009-03-01
I see the wireless interface.  It says I connected, I have the correct WPA, but it acts like it is wrong.  His WPA is just some password type phrase and not a typical numeric key.

I will try the IPv6 suggestion next time on Sunday when I am back in touch with the machine.

Thanks for the replies....

---

### Post by tommcd on 2009-03-01
First, disable all encryption on your router. Set essid to broadcast, and try to connect. After you connect without encryption, then work on getting WPA working.

As it stands now you have no way of knowing whether it is a problem with a wireless driver, WPA, or ipv6. You need to proceed in a logical, step by step fashion to determine where the problem lies.

---

### Post by crotherm on 2009-03-01
sounds like a plan....

thanks..

---

