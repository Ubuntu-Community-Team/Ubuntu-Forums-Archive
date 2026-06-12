---
title: "Unable to connect to wireless after disabling the wireless"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by prashant_shukl on 2011-09-09
I have to suspend my laptop while it was connected. Moving over to a diff network and then un-suspending it made me lose my wireless connection. So I unchecked Enable Wireless and and re-enabled it. 

Now i am not able to connect to wireless. Do not see the list of wireless connection. 

I am on Ubuntu 10.4 64 bit, using NetworkManager. 

Here is the info from iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


Prashant

---

### Post by prashant_shukl on 2011-09-09
And yes the lshw:


*-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:f7:60:bc
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:7000(size=256) memory:d8800000-d8803fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:85:00.0
       logical name: eth0
       version: 02
       serial: 1c:c1:de:9e:88:eb
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:2000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)

---

### Post by wildmanne39 on 2011-09-09
Hi, let see if we can get this working please post the results of these commands:
```
nm-tool
```
```
lspci -nn | grep 0280
```
```
rfkill list all
```
```
dmesg | grep wlan0
```
```
dmesg | egrep 'rtl|firm'
```
```
lsmod | grep rtl
```
Thank you

---

### Post by prashant_shukl on 2011-09-09
**_nm-tool_**
> NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xSE
  State:             disconnected
  Default:           no
  HW Address:        70:F1:A1:F7:60:BC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        1C:C1:DE:9E:88:EB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


**_lspci -nn | grep 0280_**
> 
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8171] (rev 10)


_**rfkill list all**_
> 
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


**_dmesg | grep wlan0_**
> 
[   24.602232] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**_dmesg | egrep 'rtl|firm'_**
> 
[   15.350303] rtllib_crypt: registered algorithm 'NULL'
[   15.350306] rtllib_crypt: registered algorithm 'TKIP'
[   15.350308] rtllib_crypt: registered algorithm 'CCMP'
[   15.350309] rtllib_crypt: registered algorithm 'WEP'
[   15.350357] rtl819xSE 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.350365] rtl819xSE 0000:02:00.0: setting latency timer to 64
[   24.458167] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   24.581422] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   24.591147] ===>rtllib_start_scan()
[   45.078336] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   75.078738] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  115.085376] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  165.080425] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  225.080387] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  285.080285] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  345.080726] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  405.081309] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  465.081151] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  525.081643] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  585.081313] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1


_**lsmod | grep rtl**_ Gives nothing

---

### Post by wildmanne39 on 2011-09-09
Hi, before we continue the first thing I see is that your signal strength is to weak to connect, you are to far away from the router,
Thank you

---

### Post by prashant_shukl on 2011-09-09
This laptop does not show any wireless connections available. Having said that, I am practically sitting next to my router and the signal strength is very good.

---

### Post by wildmanne39 on 2011-09-09
Hi, I am researching your issue but here is what I was talking about noise level high.
> Link Quality=[COLOR="Red"]10/100[/COLOR] Signal level=0 dBm Noise level=-100 dBm
Thank you

---

### Post by wildmanne39 on 2011-09-09
Hi, I believe you have the wrong driver installed it should be rtl8191seVA it is at this link
[http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

you will need to make sure you install the one for the kernel you are using, you can find out which kernel with this command.

Also you will need to remove your old driver first.
```
uname -a
```
Here is a link to help it is for a little different driver but the idea is the same.
[http://ubuntuforums.org/showthread.php?t=1834478](http://ubuntuforums.org/showthread.php?t=1834478)
Thank you

---

### Post by prashant_shukl on 2011-09-10
Thanks a million wildmanne39. I guess i have corrupted my wireless driver when I hibernated the system.

I have re-installed the  drivers and it works like a charm.

Thanks again for your help.
Prashant

---

### Post by wildmanne39 on 2011-09-10
Hi, your welcome! enjoy ubuntu and wireless, if I helped would you please click on my membership application in my signature and show your support for me becoming an ubuntu member? would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

