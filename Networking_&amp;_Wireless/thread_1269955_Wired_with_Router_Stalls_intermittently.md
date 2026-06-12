---
title: "Wired with Router Stalls intermittently"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by arvin555 on 2009-09-18
Would like to request help with wired internet problem.  I am using Jaunty on a PC, I had to add a new Lan card on the PC because the internal one got damaged and didn't work (I was on WinXP then), it worked quite well on XP, and then I migrated to Jaunty, worked okay as well.  

However recently I have noticed that though I do not see any disconnection information, the Icon for network looks normal, Clicking "connection information" looks normal, ifconfig also shows a connection. But all communications with my Linksys router would stop, I wouldn't even be able to access the router setup using the browser.  

This problem comes up sometimes after 10 minutes, but sometimes after a few hours.  There is no indication that I have no connection so that gmails are unsent, forum posts will be unsent, and the only way to fix the problem (so far is to reboot the computer). 

I have tried clicking on icon, turning off and then on network connection, and turning off and on the eth0, but when I do this, the network will now show disconnected and wont' be able to reconnect at all unless I reboot.  I have tried using a terminal and doing ifconfig down and up and also network restart, all of these do not work.  

Anyone can suggest a way to reconnect or reestablish connection with my Router without having to reboot?  On winXP, I can usually just "repair" the connection, or at times I actually disable the network card and then enable it, and that usually works. Another thing is ipconfig /renew all would also work...   I can't find a way to do this in Jaunty unfortunately. :(


Here is my ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:4f:4e:07:fa:c2  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::24f:4eff:fe07:fac2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:449046 errors:1 dropped:0 overruns:0 frame:0
          TX packets:488841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:413158445 (413.1 MB)  TX bytes:83248131 (83.2 MB)
          Interrupt:19 Base address:0x9000 

eth1      Link encap:Ethernet  HWaddr 00:0d:87:ef:d1:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



Thanks in advance for your help guys.

---

### Post by arvin555 on 2009-09-19
This is my Interfaces.txt (don't know if needed)
> auto lo
iface lo inet loopback


Here is my lspci
> home@home-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78 )
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)


nmTools
>  Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             unavailable
  Default:           no
  HW Address:        00:0D:87:EF:D1:E1

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:4F:4E:07:FA:C2

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             114.108.192.31
    DNS:             114.108.192.32


These were taken while the connection is still okay.  If there is a terminal command to I need to check when the connection has stalled, so we can trouble shoot please let me know. :)

---

### Post by arvin555 on 2009-09-21
Unfortunately, no improvements, still had a "hanged" or stalled connection even though Ubuntu network manager thinks that it is still connected, no connection with the router.

I tried disabling network connecction using network manager, waiting for a long time and then enabling, still no go. :(  This problem is intermittent, I went one whole day without the problem, then just this morning 2 times in a row. :(

At least an someone confirm if what I understand is correct that my eth0 is  Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78 )?

TTFN
Arvin

---

### Post by lisati on 2009-09-21
How's your connection from the router to the internet? I occasionally experience hassles with my ADSL connection is playing up, but found that things improved recently when I rewired the connection from my ADSL modem to the the phone line. (I was using two extension leads on the phone line & moved things around so that I could unplug one of them.)

---

### Post by arvin555 on 2009-09-22
Lisati,

Thanks for your feedback,  unfortunately it is not the internet connection as the Router to Modem to Internet is okay, not great as sometimes I need to restart both to get connection, but I think I have eliminated that as possible problem because if it's the modem/internet connection, I should still be able to connect to my router configuration/setup page using my browser.  I actually do this to "remotely" reset the router DHCP and or do a restart.  

When my actual problem happens, I can't even connect to the router as well.  I have a feeling that the network card hangs or crashes and needs a "reset".  In Windows before I can uninstall it, and then reinstall and usually that will fix it.  The problem with Ubuntu is that when I disable then reanable networking, the problem still is there. Only solution that I have for now is to shut down and then turn on the PC again.

TTFN
Arvin

---

### Post by arvin555 on 2009-09-30
Just wanted to update, and I might have found the solution to my problem.

1. Unfortunately the intermittent connection (stalled connection) still happens.

2. But recently I have been experimenting by just pulling off the LAN cable from the LAN card, waiting a bit and then plugging it back in.  The connection manager will of course tell me that the wired connection is disconnected, but often after I reconnect the LAN cable, I get info that eth0 is connected again.

3. A few times this did not work, so what I did was do the same thing, unplug then plug in, then if nothing happens I disable networking by right clicking on the network icon on the toolbar, then unchecking network connection, it will disconnect, then I click again to reconnect, then it will try to search for connection and usually it does detect and eth0 will be up again.  

I still have no idea why the connection stalls, maybe it has to do with my cable or my Linksys router, but at least I don't have to always reboot when this happens again.  

TTFN
Arvin

---

