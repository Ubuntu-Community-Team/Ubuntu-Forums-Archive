---
title: "Wireless won't work in 12.04"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by clay7 on 2012-10-24
Wireless does not work on my laptop:

Toshiba Satellite S855D-S5253
ubuntu Desktop 12.04 LTS 64-bit
Dual boots with Win7 64-bit, and wireless works on Win7.
Wireless switch: on.

**I tried these instructions but they didn't work for me:**
[http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126) 

Here's the short version of that thread:
```
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```

I've been able to use a wired connection (which is working sometimes, and sometimes it doesn't) to download the following  packages and I've tried them all, in the order listed below, and none have worked:

sudo apt-get update
sudo apt-get upgrade
(I've tried jockey but that didn't produce any results)

compat-wireless-3.5.1-1-snpc
compat-wireless-2012-05-10-p
compat-wireless-2012-10-20
compat-wireless-2012-10-21
compat-wireless-2012-10-21-p
compat-wireless-2012-02-28
compat-wireless-2012-02-28-p

Here is my information. Any help would be GREATLY appreciated!

**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:10.0.0.33  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe28:7acc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:16103 (16.1 KB)  TX bytes:16433 (16.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4369 (4.3 KB)  TX bytes:4369 (4.3 KB)
```

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.
```


**lspci -nn | grep 0200**
```
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
```

**dmesg | grep alx**
```
[   14.004347] alx 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.004352] alx 0000:01:00.0: DMA to 64-BIT addresses
[   14.004371] alx 0000:01:00.0: setting latency timer to 64
[   14.004470] alx 0000:01:00.0: (unregistered net_device): HW Flags = 0x15
[   14.004902] alx 0000:01:00.0: (unregistered net_device): reset PHY, pws = 1, az = 0, ptp = 0
[   14.006310] alx 0000:01:00.0: (unregistered net_device): speed = 0x2f, autoneg = 1
[   14.007821] alx 0000:01:00.0: irq 46 for MSI/MSI-X
[   14.008617] alx: Atheros Gigabit Network Connection
```

**sudo lshw -C network**
```

  *-network               
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: xx:xx:xx:xx:xx:xx
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full firmware=alx ip=10.0.0.33 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f0100000-f013ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0000000-f0003fff
```

**nm-tool**
```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             connected
  Default:           yes
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.33
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76
```

---

### Post by ahallubuntu on 2012-10-24
Those instructions were for a Broadcom wireless card, but your wireless card is a Realtek card.

You can look for a driver from here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I'd probably try this one:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Download it to a USB thumb drive or download it using Windows first if you can't make a wired connection temporarily.

Note that this requires you to open a terminal and run some commands.  I would extract the .gz file into your download directory, cd into it, then type:

```
sudo make
sudo make install
```

(reboot the computer if there were no errors, and cross your fingers.  If there were errors, you might have to install a few other things first.)

---

### Post by Cinnamonbun23 on 2012-10-24
I'm having the exact same problem with my toshiba. windows 7 internet works fine but with ubuntu it won't work

---

### Post by clay7 on 2012-10-24
Thanks ahallubuntu. I tried RTL8191SE-VA2 since my kernel version is 3.2.0-29-generic but it didn't work. I rebooted just to make sure.

Was I suppposed to 
```
./scripts/driver-select xxxx
```
before running sudo make, and then sudo make install? I only ran sudo make, and then sudo make install, but not the ./scripts command.

Also, do i need to modprobe? If so, which module?

Thanks!

---

### Post by clay7 on 2012-10-24
Whew. After about 10 total hours of trying to get this work, this finally did it:

```
wget -O- http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz | tar -xz

cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
sudo make
sudo make install

sudo modprobe rtl8723e
```

I didn't need to run the last line.

Thanks to all who helped! I wouldn't have known to be looking for a Realtek driver unless ahallubuntu had told me - thanks!!!

---

### Post by ahallubuntu on 2012-10-25
Cool!  And if after reboot you find it doesn't work, add the line

rtl8723e

to the end of /etc/modules.

Note that if you update the kernel (a normal Ubuntu update), you may also need to re-build this module again, in exactly the same way.

---

### Post by trueSora on 2012-10-26
Hi everyone. I am very new to Linux myself.

I am having a problem with my wireless internet connection. When I startup Ubuntu and plug in the appropriate credentials for my home internet, it tries to connect to my wireless network, but it has no success (keeps asking over some time period to re-enter the password for the network).

I recently tried this again, but this time, Linux actually stated that it got an internet connection running. So, I opened up Firefox and tried to access Google. Funny thing is that I couldn't access Google. 

I also tried the Download Centre, but could not download anything. It just keeps saying:
"waiting..." or the like.

The information that Clay7 provided seemed like the correct procedure to follow, so I have done the same for my situation. Note, I have downloaded the appropiate Linux Realtek driver (mine is also Realtek), but I am unsure on how to install it into Linux. 

So my question is, "can anyone help me get my Wireless Internet Connection Running?"
Thanks for all the help in advance.

Terminal Inputs and Outputs are as follows:

For command: ifconfig

anthony@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:22:e7:85:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7744 (7.7 KB)  TX bytes:7744 (7.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:9c:83:99:b2:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)






For command: iwconfig

anthony@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Paradise"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: F4:EC:38:DB:4B:8E   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.






For command: lspci -nn|grep 0200

anthony@ubuntu:~$ lspci -nn|grep 0200
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)





For command: dmesg|grep alx

"Nothing popped up here for some reason"





For command: sudo lshw -C network

anthony@ubuntu:~$ sudo lshw -C network
[sudo] password for anthony: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 00:25:22:e7:85:48
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:d800(size=256) memory:dffff000-dfffffff memory:dfff8000-dfffbfff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:6
       logical name: wlan0
       serial: 00:9c:83:99:b2:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-29-generic-pae firmware=N/A ip=192.168.1.100 link=yes multicast=yes wireless=IEEE 802.11bgn



For command: nm-tool

anthony@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Paradise] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        00:9C:83:99:B2:DA

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Paradise:       Infra, F4:EC:38:DB:4B:8E, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:25:22:E7:85:48

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by ahallubuntu on 2012-10-26
trueSora, you have the Realtek 8192CU chipset. To build a driver for it, try this (reply #2 and #4 by me):

[http://ubuntuforums.org/showthread.php?t=2076315](http://ubuntuforums.org/showthread.php?t=2076315)

---

### Post by trueSora on 2012-10-26
Thanks. That was quick. I will try this now.

---

### Post by trueSora on 2012-10-26
I went to the page you directed me too and did the following within the terminal:

anthony@ubuntu:~$ cd ~/Downloads/wrd
anthony@ubuntu:~/Downloads/wrd$ chmod 755 ./install.sh
anthony@ubuntu:~/Downloads/wrd$ sudo ./install.sh
[sudo] password for anthony: 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
	rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730.tar.gz
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/clean
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/Makefile
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/Kconfig
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-29-generic-pae/build M=/home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_cmd.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_security.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_debug.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_io.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ioctl_query.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ioctl_set.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_ieee80211.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mlme.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_mlme_ext.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_wlan_util.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_pwrctrl.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_rf.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_recv.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_sta_mgt.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_xmit.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_p2p.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_br_ext.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/rtw_iol.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/core/efuse/rtw_efuse.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/hal_init.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_mp.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/osdep_service.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/os_intfs.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/usb_intf.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/ioctl_linux.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/xmit_linux.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/mlme_linux.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/recv_linux.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/os_dep/linux/rtw_android.o
  LD [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/8192cu.mod.o
  LD [M]  /home/anthony/Downloads/wrd/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20120730/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
##################################################
Compile make driver ok!!
##################################################
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-29-generic-pae
##################################################
The Setup Script is completed !
#################################################

However, the internet connection problem still persists. It may be because I didn't follow onto the blacklist.... step. I am unsure of what you mean't on that step. So, what should I do next?

---

### Post by ahallubuntu on 2012-10-26
Yes, you need to edit the file

/etc/modprobe.d/blacklist.conf

and probably add three three lines to the end of it:

```
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
```

Also, add this line to the end of /etc/modules

```
8192cu
```

Then reboot and try it.  That should prevent the old driver from loading and the new one should load instead.

---

### Post by trueSora on 2012-10-27
Thank you so much. It worked perfectly. I just needed to use the gksudo gedit command to edit the read only files. You're the best. :)

---

### Post by maxfli on 2013-06-20
Having the same issue but I have Dell Insp. M6400 using Brodcom Wifi. Wired works OK. Wifi works on Win 7. I have tried just about every update I know of. Wireless info:
*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.2.0-45-generic #70-Ubuntu SMP Wed May 29 20:12:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)
    Subsystem: Dell Device [1028:0251]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Dell Wireless 1510 Wireless-N WLAN Mini-Card [1028:000d]
    Kernel modules: ssb

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card

***** iwconfig *****


***** rfkill *****

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: usb0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            usb3380
  State:             unmanaged
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.71.3.139
    Prefix:          20 (255.255.240.0)
    Gateway:         10.71.0.1

    DNS:             10.71.0.1



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

allow-hotplug usb0
iface usb0 inet static
    address 192.168.3.1
    netmask 255.255.255.0
    network 192.168.3.0
    broadcast 192.168.3.255
    post-up /etc/init.d/isc-dhcp-server restart
    down /etc/init.d/isc-dhcp-server stop

***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search hospitalitytechservices.com

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/usb3380.conf]
blacklist usb3380_stall

***** dmesg *****


****************** done ******************

---

