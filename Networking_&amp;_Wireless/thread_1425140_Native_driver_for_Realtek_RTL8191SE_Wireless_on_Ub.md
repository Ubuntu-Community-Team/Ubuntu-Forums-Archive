---
title: "Native driver for Realtek RTL8191SE Wireless on Ubuntu 9.10"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by David Bolton on 2010-03-08
Realtek RTL8191SE Wireless LAN 802.11n PCI-E NIC

Ubuntu 9.10, new user

My wireless does not work after a new (first) install of Ubuntu. I searched for my wireless card online and found a [Linux driver from the company website]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true"). Should I use this native driver or is still recommended to use an NDISWrapper? If it is possible to use the native one I think I would like to (although I would need research how to do this).

---

### Post by David Bolton on 2010-03-08
Sorry, forgot to mention computer model is Toshiba, Satellite

---

### Post by chili555 on 2010-03-08
> Realtek RTL8191SE Wireless LAN 802.11n PCI-E NICThe link you gave us is for rtl819[COLOR="Red"]2[/COLOR]se_pci. Before you proceed further, let's make sure that is exactly what you need. Please open a terminal and do:```
lspci -nn
```It's actually fairly easy to build this.

---

### Post by Dude-PWB- on 2010-03-08
From what I have come to understand, the 8191 and 8192 use the same driver.

---

### Post by David Bolton on 2010-03-08
Below is the text from the terminal for the command you mention. 

```
david@david-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0a75] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0be3] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
04:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
04:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
04:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
04:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 01)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
3f:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
3f:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
3f:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
3f:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
3f:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
3f:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
3f:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
3f:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
3f:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
3f:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
3f:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)
david@david-desktop:~$ 

```


I originally got the product information by using the command mentioned in the wireless troubleshooting section of the built-in help. Looking over it again, I'm not sure if the product number is for the wireless or for the cable
```

david@david-desktop:~$ sudo lshw -C network
[sudo] password for david: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:43:5e:3a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:35 ioport:4000(size=256) memory:d3110000-d3110fff(prefetchable) memory:d3100000-d310ffff(prefetchable) memory:d3120000-d313ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d9100000-d9103fff
david@david-desktop:~$ 
```

---

### Post by chili555 on 2010-03-08
Let's take a look:> Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [[COLOR="Blue"]10ec:8172[/COLOR]]```
modinfo r8192se_pci | grep 8172
alias:          pci:v0000[COLOR="Blue"]10EC[/COLOR]d0000[COLOR="Blue"]8172[/COLOR]sv*sd*bc*sc*i*
```So far, so good.

I am assuming you have an ethernet connection so you can download files. Please open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
```Download the file you referenced. By default, file downloads go to your desktop. Right-click the file and select 'Extract Here'. A folder will be created called rtl8192se_linux_2.6.0014.0115.2010.

You can use the Tab key to fill in the blanks in Linux. We will use it next.```
cd Desktop/rtl8
```Press Tab and then Enter.```
sudo su
make
make install
modprobe r8192se_pci
exit
iwconfig
```Do you now have a wireless interface, wlan0, perhaps? Can you click the Network Manager icon, see networks and connect?

Have you earned your Ubuntu wings?

---

### Post by David Bolton on 2010-03-08
I now see the "Wireless Networks" subheading in the Network Manager icon but I don't see any available networks. I am using a Ubuntu as dual boot. Under Windows the network is visible (plus a couple other weaker networks from the neighbors).

At the last step of your instructions (thanks for those) I got the following text:

```
david@david-desktop:~/Desktop/rtl8192se_linux_2.6.0014.0115.2010$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



Below I also included the whole terminal session in case it is needed.

```
david@david-desktop:~$ modinfo r8192se_pci | 8172
ERROR: modinfo: could not find module r8192se_pci
8172: command not found
david@david-desktop:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc
  libstdc++6-4.4-dbg libstdc++6-4.4-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,999kB of archives.
After this operation, 23.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic-updates/main libstdc++6-4.4-dev 4.4.1-4ubuntu9 [1,490kB]
Get:2 http://us.archive.ubuntu.com karmic-updates/main g++-4.4 4.4.1-4ubuntu9 [4,701kB]
Get:3 http://us.archive.ubuntu.com karmic/main g++ 4:4.4.1-1ubuntu2 [1,446B]
Get:4 http://us.archive.ubuntu.com karmic/main patch 2.5.9-5 [100kB]
Get:5 http://us.archive.ubuntu.com karmic/main dpkg-dev 1.15.4ubuntu2 [573kB]
Get:6 http://us.archive.ubuntu.com karmic/main build-essential 11.4 [7,172B]
Get:7 http://us.archive.ubuntu.com karmic/main fakeroot 1.12.4ubuntu1 [126kB]
Fetched 6,999kB in 4s (1,638kB/s)
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 156237 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.4ubuntu2_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.4ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.15.4ubuntu2) ...
Setting up fakeroot (1.12.4ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up libstdc++6-4.4-dev (4.4.1-4ubuntu9) ...
Setting up g++-4.4 (4.4.1-4ubuntu9) ...
Setting up g++ (4:4.4.1-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4) ...
david@david-desktop:~$ cd Desktop/rtl8192se_linux_2.6.0014.0115.2010/
david@david-desktop:~/Desktop/rtl8192se_linux_2.6.0014.0115.2010$ sudo su
root@david-desktop:/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_core.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_regd.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_eeprom.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_cam.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_pm.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_ps.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_dm.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_debug.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_ethtool.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_dev.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_Efuse.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_phy.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_rtl6052.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_hwimg.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_led.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_mp.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_scan.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_rx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_softmac.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_tx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_module.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_softmac_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtl819x_HTProc.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtl819x_BAProc.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/dot11d.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_crypt.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_tkip.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_ccmp.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_wep.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/wapi.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/wapi_interface.o
  LD [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/r8192se_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/r8192se_pci.mod.o
  LD [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/r8192se_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
#@make -C /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/wapi_supplicant
root@david-desktop:/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010# make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
#@make -C /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/wapi_supplicant
make[1]: Entering directory `/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192'
make -C /lib/modules/2.6.31-14-generic/build M=/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
install -p -m 644 r8192se_pci.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
depmod -a
make[1]: Leaving directory `/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192'
root@david-desktop:/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010# modprobe r8192se_pci
root@david-desktop:/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010# exit
exit
david@david-desktop:~/Desktop/rtl8192se_linux_2.6.0014.0115.2010$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-desktop:~/Desktop/rtl8192se_linux_2.6.0014.0115.2010$ 


```

---

### Post by chili555 on 2010-03-08
Network Manager will always prefer and use wired ethernet before  wireless. Please detach the ethernet cable and give NM a few moments to react to the change of state and look for wireless networks again. 

I notice it says you have 300 Mb/s speeds, wireless N! Great! I also notice no warnings and no errors in your compile. Your Ubuntu wings will be well deserved.

---

### Post by David Bolton on 2010-03-08
I unplugged and waited for a minute or two but it didn't show any available networks in the drop-down menu. Is it correct to assume that they would appear in the list automatically like do for windows?

I restarted without the cable plugged in. Still no luck. Finally I tried "Connect to Hidden Network" and "Create New Wireless Network..." on the off chance that this is what I needed to do (The attached screenshot shows the latter). But couldn't get on the web. 

In the output from iwconfig I noticed the following line:

```
Nickname:"rtl8191SEVA2"
```

I'm downloading the RTL8191SE-VA2 file from the [same page]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true") as above. I will try to adapt your instructions to build and install later this evening. Do I need to "undo" anything from the previous driver before trying this new one?

---

### Post by David Bolton on 2010-03-08
Clicking on the link for the other driver gave me the same download. I guess that's what you meant by the page only having rtl819[COLOR=Red]2[/COLOR]se_pci. I'm not sure how to proceed from here.

---

### Post by chili555 on 2010-03-08
> it didn't show any available networks in the drop-down menu.It looks to me like it shows one called NETGEAR. Is that your network?

The designation "rtl8191SEVA2" is simply a placeholder corresponding to your chipset. Your network's ESSID will take its place as soon as you connect.

---

### Post by chili555 on 2010-03-08
Isn't this it?

---

### Post by David Bolton on 2010-03-08
Thanks for sticking with me through this!

The NETGEAR item is what got added after I chose "Create New Wireless Network..." NETGEAR is the name of the network I was hoping to connect to. I'm assuming that create new wireless network is to allow other computers to connect to the Internet through me, but really I don't know (I didn't see mention of this menu item in the built-in documentation).

When I choose "NETGEAR" for the menu it says "Network connection established" but if I try to load a web page in Firefox it doesn't work (as shown in the previous screenshot).

Right now I choose "NETGEAR" again to make sure I got the wording correct. This time it said "Network connection disconnected" and the Network icon turning into a spinner that has been rotating for the past few minutes. If I click on the rotating spinner the computer becomes unresponsive for about a minute. I couldn't reconnect via wire cable, so I tried to restart but it got stuck and so I ended up holding the power button until it turned off. 

Maybe I show try NDISWrapper after all. Any other ideas?

---

### Post by chili555 on 2010-03-09
> Maybe I show try NDISWrapper after all. Any other ideas?You certainly can try ndiswrapper if you wish, however, I see no reason to believe that the Windows driver will work any better than the native Linux driver. I think you have a configuration and Network Manager issue and not a driver issue. I have seen many examples, over the years, of new users blaming the driver for many other issues and installing a different driver and having the same problems. 

Please delete any and all settings and profiles you placed in Network Manager or other network configuration tools. NM is supposed to figure all of this out for us and generally does a very good job. Restart NM:```
sudo /etc/init.d/NetworkManager restart
```On one of my systems, it's *network-manager*, so be prepared to try the other, if you get a 'command not found.'

Then restart networking:```
sudo /etc/init.d/networking restart
```Now let's see if we see networks:```
sudo iwlist wlan0 scan
```Even if we don't see networks, and I'm fairly confident we will, the resultant message will be informative.> I'm assuming that create new wireless network is to allow other computers to connect to the Internet through me, but really I don't knowIs that what you are trying to do, set up internet connection sharing? I thought we were trying to connect your computer to the router and thereby the internet.

---

### Post by David Bolton on 2010-03-09
> I thought we were trying to connect your computer to the router and thereby the internet.


You are correct. Sorry about the confusion, I was just experimenting with a couple things to see what would happen. And whether it would connect me to the internet wireless-ly.

Below is my terminal session. It says, "wlan0     No scan results":

```
david@david-desktop:~$ sudo /etc/init.d/NetworkManager restart
[sudo] password for david: 
sudo: /etc/init.d/NetworkManager: command not found
david@david-desktop:~$ sudo /etc/init.d/network-manager restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart network-manager
network-manager start/running, process 1953
david@david-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
david@david-desktop:~$ sudo iwlist wlan0 scan
wlan0     No scan results

david@david-desktop:~$ 
```

---

### Post by chili555 on 2010-03-09
I wonder what the kernel has to say about all this:```
lsmod | grep rt2
dmesg | grep -e rt2 -e wlan
```

---

### Post by David Bolton on 2010-03-09
I tried "dmesg | grep -e rt2 -e wlan" a few times (the second two were after I unplugged the cable). 

```
david@david-desktop:~$ lsmod | grep rt2
david@david-desktop:~$ dmesg | grep -e rt2 -e wlan
[   15.822030] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1224.503745] ADDRCONF(NETDEV_UP): wlan0: link is not ready
david@david-desktop:~$ dmesg | grep -e rt2 -e wlan
[   15.822030] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1224.503745] ADDRCONF(NETDEV_UP): wlan0: link is not ready
david@david-desktop:~$ dmesg | grep -e rt2 -e wlan
[   15.822030] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1224.503745] ADDRCONF(NETDEV_UP): wlan0: link is not ready
david@david-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
joydev                 10272  0 
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 

```

---

### Post by chili555 on 2010-03-09
Sorry about that!```
lsmod | grep rtl
dmesg | grep rtl
```Thanks.

---

### Post by David Bolton on 2010-03-09
```
david@david-desktop:~$ lsmod | grep rtl
david@david-desktop:~$ dmesg | grep rtl
[    9.819595] rtllib_crypt: registered algorithm 'NULL'
[    9.819598] rtllib_crypt: registered algorithm 'TKIP'
[    9.819601] rtllib_crypt: registered algorithm 'CCMP'
[    9.819602] rtllib_crypt: registered algorithm 'WEP'
[    9.819647] rtl819xSE 0000:03:00.0: PCI INT A: no GSI - using IRQ 10
[    9.819658] rtl819xSE 0000:03:00.0: setting latency timer to 64
[   15.279045] rtl819xSE 0000:03:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   15.811442] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   15.821627] ===>rtllib_start_scan()
[   22.818654] ----------->rtl8192se_check_hw_scan()
[   22.819663] <-----------rtl8192se_check_hw_scan()
[   29.934145] ----------->rtl8192se_check_hw_scan()
[   29.935147] <-----------rtl8192se_check_hw_scan()
[   29.935306] -------------->rtl8192se_cancel_hw_scan()scan abort start...
[   36.933899] ----------->rtl8192se_check_hw_scan()
[   36.934905] <-----------rtl8192se_check_hw_scan()
[   43.387107] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   50.394318] ----------->rtl8192se_check_hw_scan()
[   50.395331] <-----------rtl8192se_check_hw_scan()
[   73.388139] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   80.395589] ----------->rtl8192se_check_hw_scan()
[   80.396597] <-----------rtl8192se_check_hw_scan()

```

---

### Post by chili555 on 2010-03-09
I am studying this:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

I have not found a solution yet. I do notice that Realtek has a later version out, so it might be worthwhile to do a sudo su, make uninstall in the old directory and then download and install the later one.

Be back soon.

---

### Post by David Bolton on 2010-03-09
I uninstalled an reinstalled with the new download. It is behaving same as before. 

```
david@david-desktop:~$ cd Desktop/rtl8192se_linux_2.2.6.0014.0115.2010/
david@david-desktop:~/Desktop/rtl8192se_linux_2.2.6.0014.0115.2010$ make uninstall
rm: cannot remove `/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless//r8192se_pci.ko': Permission denied
make[1]: Entering directory `/home/david/Desktop/rtl8192se_linux_2.2.6.0014.0115.2010/HAL/rtl8192'
depmod -a
FATAL: Could not open /lib/modules/2.6.31-14-generic/modules.dep.temp for writing: Permission denied
make[1]: *** [uninstall] Error 1
make[1]: Leaving directory `/home/david/Desktop/rtl8192se_linux_2.2.6.0014.0115.2010/HAL/rtl8192'
make: *** [uninstall] Error 2
david@david-desktop:~/Desktop/rtl8192se_linux_2.2.6.0014.0115.2010$ sudo make uninstall
[sudo] password for david: 
make[1]: Entering directory `/home/david/Desktop/rtl8192se_linux_2.2.6.0014.0115.2010/HAL/rtl8192'
depmod -a
make[1]: Leaving directory `/home/david/Desktop/rtl8192se_linux_2.2.6.0014.0115.2010/HAL/rtl8192'
david@david-desktop:~/Desktop/rtl8192se_linux_2.2.6.0014.0115.2010$ cd ../
david@david-desktop:~/.local/share/Trash/files$ cd Desktop
bash: cd: Desktop: No such file or directory
david@david-desktop:~/.local/share/Trash/files$ cd ~/Desktop
david@david-desktop:~/Desktop$ cd rtl8192se_linux_2.6.0014.0115.2010/
david@david-desktop:~/Desktop/rtl8192se_linux_2.6.0014.0115.2010$ sudo su
root@david-desktop:/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_core.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_regd.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_eeprom.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_cam.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_pm.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_ps.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_dm.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_debug.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl_ethtool.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_dev.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_Efuse.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_phy.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_rtl6052.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_hwimg.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_led.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_mp.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/rtl8192s/r8192S_scan.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_rx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_softmac.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_tx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_module.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_softmac_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtl819x_HTProc.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtl819x_BAProc.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/dot11d.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_crypt.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_tkip.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_ccmp.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_wep.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/wapi.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/../../rtllib/wapi_interface.o
  LD [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/r8192se_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/r8192se_pci.mod.o
  LD [M]  /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192/r8192se_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
#@make -C /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/wapi_supplicant
root@david-desktop:/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010# make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
#@make -C /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/wapi_supplicant
make[1]: Entering directory `/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192'
make -C /lib/modules/2.6.31-14-generic/build M=/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
install -p -m 644 r8192se_pci.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
depmod -a
make[1]: Leaving directory `/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/HAL/rtl8192'
root@david-desktop:/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010# modprobe r8192se_pci
root@david-desktop:/home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010# exit
exit
david@david-desktop:~/Desktop/rtl8192se_linux_2.6.0014.0115.2010$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-desktop:~/Desktop/rtl8192se_linux_2.6.0014.0115.2010$ 


```

---

### Post by David Bolton on 2010-03-09
in case it is helpful: 

```
david@david-desktop:~$ uname -a
Linux david-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

```

On my other partition I have Windows 7 64-bit. The wireless works there. 

On the Ubuntu partition I don't have any files yet (apart from the ones related to the wireless) so I don't mind trying a reinstall if it might help, or trying the 64-bit edition.

---

### Post by chili555 on 2010-03-09
> 2.6.31-14-genericDo you have an ethernet connection available? Can you update to the latest kernel?

---

### Post by David Bolton on 2010-03-09
Sorry I'm brand new at all of this. I tried following [these instructions for upgrading the kernal]("http://www.cyberciti.biz/faq/linux-kernel-upgrade-howto/") but I didn't have much success (as you'll see below). I also marked "pre-release updates" in the package manager but I didn't see anything for kernel. 

```
david@david-desktop:~$ uname -r
2.6.31-14-generic
david@david-desktop:~$ apt-cache search linux-image
alsa-base - ALSA driver configuration files
linux-image-2.6.31-14-386 - Linux kernel image for version 2.6.31 on i386
linux-image-2.6.31-14-generic - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-14-generic-pae - Linux kernel image for version 2.6.31 on x86
linux-image-2.6.31-14-virtual - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-302-ec2 - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-9-rt - Linux kernel image for version 2.6.31 on Ingo Molnar's full real time preemption patch
linux-image-rt - Rt Linux kernel image
rt2400-source - source for rt2400 wireless network driver
rt2500-source - source for rt2500 wireless network driver
rt2570-source - source for rt2570 wireless network driver
linux-image - Generic Linux kernel image.
linux-image-2.6.31-15-386 - Linux kernel image for version 2.6.31 on i386
linux-image-2.6.31-15-generic - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-15-generic-pae - Linux kernel image for version 2.6.31 on x86
linux-image-2.6.31-15-virtual - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-16-386 - Linux kernel image for version 2.6.31 on i386
linux-image-2.6.31-16-generic - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-16-generic-pae - Linux kernel image for version 2.6.31 on x86
linux-image-2.6.31-16-virtual - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-17-386 - Linux kernel image for version 2.6.31 on i386
linux-image-2.6.31-17-generic - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-17-generic-pae - Linux kernel image for version 2.6.31 on x86
linux-image-2.6.31-17-virtual - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-19-386 - Linux kernel image for version 2.6.31 on i386
linux-image-2.6.31-19-generic - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-19-generic-pae - Linux kernel image for version 2.6.31 on x86
linux-image-2.6.31-19-virtual - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-20-386 - Linux kernel image for version 2.6.31 on i386
linux-image-2.6.31-20-generic - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-20-generic-pae - Linux kernel image for version 2.6.31 on x86
linux-image-2.6.31-20-virtual - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-2.6.31-304-ec2 - Linux kernel image for version 2.6.31 on x86/x86_64
linux-image-386 - Generic Linux kernel image
linux-image-ec2 - Linux kernel image for ec2 machines
linux-image-generic - Generic Linux kernel image
linux-image-generic-pae - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
linux-image-virtual - Linux kernel image for virtual machines
david@david-desktop:~$ apt-get install linux-image-2.6.31-20
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
david@david-desktop:~$ sudo apt-get install linux-image-2.6.31-20
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.31-20
david@david-desktop:~$ sudo apt-get install linux-image-2.6.31-20-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.31-20-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@david-desktop:~$ uname -r
2.6.31-14-generic
david@david-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
david@david-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 82.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157207 files and directories currently installed.)
Removing linux-headers-2.6.31-14-generic ...
Removing linux-headers-2.6.31-14 ...
david@david-desktop:~$ sudo apt-get install linux-image-2.6.31-20-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.31-20-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@david-desktop:~$ uname -r
2.6.31-14-generic
david@david-desktop:~$ 


```

---

### Post by chili555 on 2010-03-09
> linux-image-2.6.31-20-generic is already the newest version.
This suggests that the latest version is installed. However, this:> $ uname -r
2.6.31-14-generictells us that you are booted into an earlier version.

When you computer boots and you see a reference to GRUB, does a menu appear for you to select which version to boot into? Have you, for some reason, picked an older version, that is x-14? If we need to get to the menu, we will need to amend a simple file.

---

### Post by David Bolton on 2010-03-10
> When you computer boots and you see a reference to GRUB, does a menu  appear for you to select which version to boot into? Have you, for some  reason, picked an older version, that is x-14?

You are right. I didn't realize these were related and that they have numbers that correspond to the kernel version.

I am choosing the older entry in GRUB because the new one doesn't start up for me. If I choose x-20 it stops at the white logo on black background and never gets to the desktop. x-19 was even worse. Every time I chose x-19 it didn't start up either and it caused Windows to run chkdisk the next time I started up. 

I subscribed to the bug you referred to so that I'll be notified of any changes. I'm happy to keep testing for a few more days but it looks like there are others with more expertise than me working through the problem. Maybe I should wait and try Ubuntu again in a few months when my hardware has been around a little longer?

You have been very helpful and generous with your time. Thanks for your help so far.

---

### Post by chili555 on 2010-03-10
Please try two things for us:```
sudo iwconfig wlan0 power on
sudo iwconfi wlan0 mode auto
sudo iwlist wlan0 scan
```Do you see networks?

As to your kernel problem, I'd suggest going to System -> Administration -> Synaptic and remove linux-image-x-19 and its corresponding linux-headers -x-19 and linux-backports-x-19, if its installed. Do the same with -20. Reboot and let Update Manager add -20 and headers and backports, if you have it. Now reboot and see if you can smoothly boot into -20.

Post back and we'll decide how to proceed.

---

### Post by David Bolton on 2010-03-10
Yesterday I experimented (probably a little too much). I tried Ubuntu Karmic to see if it would address some of my hardware issues. It didn't (and it wouldn't start up). I reinstalled Ubuntu Jaunty and went through your steps from this thread. Everything went the same as before except "dmesg | grep rtl" showed an error message I hadn't seen before. Below is the dmesg output in addition iwlist output from your instructions in the previous post. I also saved a copy of the full terminal session on my computer in case we need to refer to it.

Since I reinstalled I don't have linux-image-x-19 anymore. I followed your instructions for removing linux-image-x-20 using Synaptic package manager. I noticed there was an option to "remove" and an option to "completely remove". I didn't know which to do so I chose the former (see screenshot). 

When I went to Update Manager I clicked "Check for Updates" but it said my system was up-to-date. Should I reinstall linux-image-x-20 using Synaptic package manager instead?


```

david@david-laptop:~$ lsmod | grep rtl 
david@david-laptop:~$ dmesg | grep rtl
[  540.084950] rtllib_crypt: registered algorithm 'NULL'
[  540.084955] rtllib_crypt: registered algorithm 'TKIP'
[  540.084959] rtllib_crypt: registered algorithm 'CCMP'
[  540.084963] rtllib_crypt: registered algorithm 'WEP'
[  540.085032] rtl819xSE 0000:03:00.0: PCI INT A: no GSI - using IRQ 10
[  540.085052] rtl819xSE 0000:03:00.0: setting latency timer to 64
[  540.386747] rtl819xSE 0000:03:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[  540.630207] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  540.640268] ===>rtllib_start_scan()
[  547.640217] ----------->rtl8192se_check_hw_scan()
[  547.641227] <-----------rtl8192se_check_hw_scan()
[  554.660260] ----------->rtl8192se_check_hw_scan()
[  554.661269] <-----------rtl8192se_check_hw_scan()
[  561.660214] ----------->rtl8192se_check_hw_scan()
[  561.661224] <-----------rtl8192se_check_hw_scan()
[  573.174057] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  580.184114] ----------->rtl8192se_check_hw_scan()
[  580.185124] <-----------rtl8192se_check_hw_scan()
[  603.172892] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  610.179904] ----------->rtl8192se_check_hw_scan()
[  610.180914] <-----------rtl8192se_check_hw_scan()
[  643.186575] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  650.197241] ----------->rtl8192se_check_hw_scan()
[  650.198251] <-----------rtl8192se_check_hw_scan()
[  693.211236] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  700.221810] ----------->rtl8192se_check_hw_scan()
[  700.222819] <-----------rtl8192se_check_hw_scan()
[  708.238246] rtl819xSE:ERR!!! NicIFEnableNIC(): Driver is already down!
[  708.490163] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  708.500223] ===>rtllib_start_scan()
[  715.501515] ----------->rtl8192se_check_hw_scan()
[  715.502525] <-----------rtl8192se_check_hw_scan()
[  722.524848] ----------->rtl8192se_check_hw_scan()
[  722.525855] <-----------rtl8192se_check_hw_scan()
[  729.532324] ----------->rtl8192se_check_hw_scan()
[  729.533334] <-----------rtl8192se_check_hw_scan()
[  743.230883] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  750.242573] ----------->rtl8192se_check_hw_scan()
[  750.243581] <-----------rtl8192se_check_hw_scan()
[  773.250911] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  780.261535] ----------->rtl8192se_check_hw_scan()
[  780.262544] <-----------rtl8192se_check_hw_scan()
david@david-laptop:~$ sudo iwconfig wlan0 power on
david@david-laptop:~$ sudo iwconfi wlan0 mode auto
sudo: iwconfi: command not found
david@david-laptop:~$ sudo iwconfig wlan0 mode auto
david@david-laptop:~$ sudo iwlist wlan0 scan
wlan0     No scan results

```

---

### Post by chili555 on 2010-03-10
One other thing to try:```
cd ~/Desktop/rtl8192se_linux_2.2.6.0014.0115.2010/
sudo ./wlan0up
sudo iwlist wlan0 scan
```I am about to lose all my beans! This is a tough one!

---

### Post by David Bolton on 2010-03-10
I got a "File exists" error:

```
david@david-laptop:~$ cd /home/david/Desktop/rtl8192se_linux_2.6.0014.0115.2010/david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0014.0115.2010$ sudo ./wlan0up
[sudo] password for david: 
insmod: error inserting 'r8192se_pci.ko': -1 File exists
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0014.0115.2010$ sudo iwlist wlan0 scan
wlan0     No scan results


```

---

### Post by chili555 on 2010-03-10
Please try:```
sudo rmmod -f r8192se_pci
cd ~/Desktop/rtl8192se_linux_2.6.0014.0115.2010/
sudo ./wlan0up
```Please post back while I grab a tranquilizer.

---

### Post by David Bolton on 2010-03-10
In the meantime I turned on Desktop Effects out of curiosity. I'm  learning that some of the settings in Ubuntu are actually mine fields!  My computer would no longer start up. I read through [this thread]("http://ubuntuforums.org/showthread.php?t=494947%29:"),  but none of the suggestions worked for me. I ending up reinstalling  again.

After the reinstall a few things were a little different  than my first two installs but the most significant changes was when I  updated via Update Manger and restarted GRUB showed only x-20 instead of  showing another couple line items for the old version. Is there a way  to edit GRUB from the command line to show the old x-14 item again? If  not maybe I need to reinstall again. The first two installs I set it to  log in automatically. The third time I didn't. This is the only  difference I'm aware of.

---

### Post by David Bolton on 2010-03-11
I got Ubuntu running with the latest kernel. The trick for me was to install the 64-bit version of Ubuntu. (When I originally downloaded the ISO I didn't see the option for 64-bit).

However, I still have the wireless troubles. I went through all the steps again. Here's the latest results:

```
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo rmmod -f r8192se_pci
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ cd /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo ./wlan0up
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ 
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo iwlist wlan0scan
iwlist: unknown command `wlan0scan' (check 'iwlist --help').
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ 

```

In case its necessarily below is the full terminal session:

```
david@david-laptop:~$ uname -a
Linux david-laptop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux
david@david-laptop:~$ sudo apt-get install build-essential linux-headers-generic[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc
  libstdc++6-4.4-dbg libstdc++6-4.4-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,836kB of archives.
After this operation, 25.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com karmic-security/main dpkg-dev 1.15.4ubuntu2.1 [573kB]
Get:2 http://us.archive.ubuntu.com karmic-updates/main libstdc++6-4.4-dev 4.4.1-4ubuntu9 [1,526kB]
Get:3 http://us.archive.ubuntu.com karmic-updates/main g++-4.4 4.4.1-4ubuntu9 [5,502kB]
Get:4 http://us.archive.ubuntu.com karmic/main g++ 4:4.4.1-1ubuntu2 [1,448B]   
Get:5 http://us.archive.ubuntu.com karmic/main patch 2.5.9-5 [101kB]           
Get:6 http://us.archive.ubuntu.com karmic/main build-essential 11.4 [7,170B]   
Get:7 http://us.archive.ubuntu.com karmic/main fakeroot 1.12.4ubuntu1 [126kB]  
Fetched 7,836kB in 10s (778kB/s)                                               
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 136830 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.1-4ubuntu9_amd64.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.1-4ubuntu9_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.1-1ubuntu2_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.4ubuntu2.1_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_amd64.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.4ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.15.4ubuntu2.1) ...
Setting up fakeroot (1.12.4ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up libstdc++6-4.4-dev (4.4.1-4ubuntu9) ...
Setting up g++-4.4 (4.4.1-4ubuntu9) ...
Setting up g++ (4:4.4.1-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4) ...
david@david-laptop:~$ cd Desktop/rtl8192se_linux_2.6.0015.0127.2010/
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo su
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010# make 
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_core.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_regd.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_rfkill.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_eeprom.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_cam.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_pm.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_ps.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_dm.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_debug.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl_ethtool.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_dev.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_Efuse.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_phy.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.o
/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.c: In function ‘FirmwareSetH2CCmd’:
/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_firmware.c:714: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_rtl6052.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_hwimg.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_led.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_mp.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/rtl8192s/r8192S_scan.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.o
/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.c: In function ‘rtllib_FlushRxTsPendingPkts’:
/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.c:1122: warning: the frame size of 1056 bytes is larger than 1024 bytes
/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.c: In function ‘RxReorderIndicatePacket’:
/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_rx.c:1303: warning: the frame size of 1072 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_softmac.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_tx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_module.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_softmac_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_HTProc.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.o
/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.c: In function ‘RxPktPendingTimeout’:
/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_TSProc.c:98: warning: the frame size of 1056 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtl819x_BAProc.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/dot11d.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_tkip.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_ccmp.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/rtllib_crypt_wep.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/wapi.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/../../rtllib/wapi_interface.o
  LD [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/r8192se_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/r8192se_pci.mod.o
  LD [M]  /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192/r8192se_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010# make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: Entering directory `/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
make -C /lib/modules/2.6.31-20-generic/build M=/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
install -p -m 644 r8192se_pci.ko /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/
depmod -a
make[1]: Leaving directory `/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010# modprobe r8192se_pci
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010# exit
exit
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo /etc/init.d/network-manager restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart network-manager
network-manager start/running, process 3470
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo iwlist wlan0 scan
wlan0     No scan results

david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ lsmod | grep rtl
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ dmesg | grep rtl
[  657.815199] rtllib_crypt: registered algorithm 'NULL'
[  657.815207] rtllib_crypt: registered algorithm 'TKIP'
[  657.815212] rtllib_crypt: registered algorithm 'CCMP'
[  657.815217] rtllib_crypt: registered algorithm 'WEP'
[  657.815499] rtl819xSE 0000:03:00.0: PCI INT A: no GSI - using IRQ 10
[  657.815519] rtl819xSE 0000:03:00.0: setting latency timer to 64
[  657.895850] rtl819xSE 0000:03:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[  658.033294] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  658.043445] ===>rtllib_start_scan()
[  663.874140] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  683.871262] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  713.868710] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  753.864363] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  759.830821] rtl819xSE:ERR!!! NicIFEnableNIC(): Driver is already down!
[  760.171785] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  760.181874] ===>rtllib_start_scan()
[  765.859533] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  785.871335] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  815.869847] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  855.865804] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo iwconfig wlan0 power on
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo iwconfig wlan0 mode auto
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo iwlist wlan0 scan
wlan0     No scan results

david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo rmmod -f r8192se_pci
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ cd /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo ./wlan0up
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ 
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo iwlist wlan0scan
iwlist: unknown command `wlan0scan' (check 'iwlist --help').
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ 


```

---

### Post by chili555 on 2010-03-11
Ahh! 64-bit, indeed. Please do:```
cd ~/Desktop/rtl8192se_linux_2.6.0015.0127.2010
sudo su
make uninstall
rmmod -f r8192se_pci
```Please download and install this:

[http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)

Let's see if we have better luck.

For the benefit of the searchers, this is from here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

Post #29.

---

### Post by David Bolton on 2010-03-11
No luck so far:

```
david@david-laptop:~$ cd /home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0015.0127.2010$ sudo su
[sudo] password for david: 

Sorry, try again.
[sudo] password for david: 
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010# make uninstall
make[1]: Entering directory `/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
depmod -a
make[1]: Leaving directory `/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010/HAL/rtl8192'
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010# rmmod -f r8192se_pci
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010# cd ../rtl8192se_
rtl8192se_091211.patch
rtl8192se_linux_2.6.0010.1020.2009_64bit/
rtl8192se_linux_2.6.0015.0127.2010/
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0015.0127.2010# cd ..
root@david-laptop:/home/david/Desktop# cd rtl8192se_linux_2.6.0010.1020.2009_64bit/
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit# su
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl8192se.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_eeprom.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_cam.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_pm.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_ps.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_debug.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_ethtool.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8190_rtl8256.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192S_Efuse.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192S_phy.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192S_firmware.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192E_dm.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192S_rtl6052.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192S_hwimg.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192S_led.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192S_mp.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_rx.o
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_rx.c: In function ‘RxReorderIndicatePacket’:
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_rx.c:853: warning: the frame size of 1072 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_softmac.o
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_softmac.c: In function ‘ieee80211_sta_send_associnfo’:
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_softmac.c:2350: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘size_t’
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_softmac.c:2350: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘size_t’
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_tx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_wx.o
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_gen_ie_rsl’:
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_wx.c:1292: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_wx.c:1308: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_module.o
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_module.c: In function ‘store_debug_level’:
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_module.c:429: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_HTProc.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_TSProc.o
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_TSProc.c: In function ‘RxPktPendingTimeout’:
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_TSProc.c:118: warning: the frame size of 1056 bytes is larger than 1024 bytes
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.o
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c: In function ‘ieee80211_rx_ADDBAReq’:
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c:284: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c: In function ‘ieee80211_rx_ADDBARsp’:
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c:372: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c: In function ‘ieee80211_rx_DELBA’:
/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c:481: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/dot11d.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_crypt.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/../../ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192se_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192se_pci.mod.o
  LD [M]  /home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192se_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit# make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: Entering directory `/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make -C /lib/modules/2.6.31-20-generic/build M=/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
install -p -m 644 r8192se_pci.ko /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/
depmod -a
make[1]: Leaving directory `/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
root@david-laptop:/home/david/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit#  

```

After that I restarted to see if the changes would take effect.

```
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit$ sudo /etc/init.d/network-manager restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart network-manager
network-manager start/running, process 2398
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

david@david-laptop:~/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit$ 

```

---

### Post by chili555 on 2010-03-11
Essentially the same result as before; an interface gets created, the driver and the card have associated, but it acts as if it's asleep. It won't scan, detect networks or connect. I was interested in this:```
Sorry, forgot to mention computer model is Toshiba, Satellite
```I noticed that some of the scripts in the file, *wlan0up*, for example, run processes in */etc/acpi.* I looked in */etc/acpi* and what did I find?> chili@LAPTOP60:/etc/acpi$ ls
---snip---
batterybtn.sh       playbtn.sh       [COLOR="Blue"]tosh-wireless.sh[/COLOR]
---snip---I wonder if you might do:```
cd /etc/acpi
sudo ./tosh-wireless.sh
```Take note of any messages, errors, complaints or otherwise. Then do:```
iwconfig
sudo iwlist wlan1 scan
```Any interesting news?

---

### Post by David Bolton on 2010-03-11
Not there yet.

```
david@david-laptop:~$ cd /etc/acpi
david@david-laptop:/etc/acpi$ ls
asus-brn-down.sh    lockbtn.sh       sleepbtn.sh
asus-brn-up.sh      mailbtn.sh       sleep.sh
asus-touchpad.sh    mediabtn.sh      start.d
asus-wireless-2.sh  mutebtn.sh       stopbtn.sh
asus-wireless.sh    nextbtn.sh       thinkpad-stretchortouchpad.sh
batterybtn.sh       playbtn.sh       tosh-wireless.sh
ejectbtn.sh         powerbtn.sh      videobtn.sh
events              power.sh         voldownbtn.sh
hibernate.sh        prevbtn.sh       volupbtn.sh
ibm-wireless.sh     rotatescreen.sh  webbtn.sh
lid.sh              screenblank.sh   wireless-rtl-ac-dc-power.sh
david@david-laptop:/etc/acpi$ sudo ./tosh-wireless.sh
[sudo] password for david: 
david@david-laptop:/etc/acpi$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.467 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@david-laptop:/etc/acpi$ sudo iwlist wlan1 scan
wlan1     No scan results

david@david-laptop:/etc/acpi$ 


```

---

### Post by moaoci on 2010-03-12
Verify the length of the driver compressed file rtl8192se_linux_2.6.0015.0127.2010.tar.gz . It could be 1905119 bytes long or 1860920 bytes long.

The file that is 1860920 bytes long is working only while on AC but is not working on battery. There was a problem with ACPI.

The file to use is the 1905119 bytes long one and is available from realtek at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true) 

The driver works with a simple sudo su + make + make install + reboot . Use "sudo su" then "make install" because   "sudo make install" may not work all times (so I heard).

It has to be recompiled each time the linux kernel number changes (as it sometimes does with update manager) and that,  until Linux Kernel supports it. 

This driver uses wlan0 when lspci shows DEVICE 8172 at line 02:00.0.  Your's is showing at line 03:00.0 so it should be wlan1.

The driver works well with a standard clean install of Ubuntu 9.10 Karmic 64bit on a friend's Toshiba satellite A500-19L  Intel core duo P7450...

If your file has the good length, email [EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL] to get help, they will solve the problem.

---

### Post by chili555 on 2010-03-12
> This driver uses wlan0 when lspci shows DEVICE 8172 at line 02:00.0. Your's is showing at line 03:00.0 so it should be wlan1.I believe this driver uses wlan%d, meaning the next available wlan number. If udev has a record of a previous wireless device that used wlan0, it will rename the next device as wlan1. The bus number, 03:00.0 is not relevant.

---

### Post by cbecker78 on 2010-03-14
Yeah!!!  I don't mean to but in on this post, but I have been following it with great interest as I have a brand new laptop, with the exact same wireless drivers and the exact same problem.

I am happy to say that using the download link two posts above this one, and the instructions provided very early on:

> So far, so good.

I am assuming you have an ethernet connection so you can download files. Please open a terminal and do:     Code:
     sudo apt-get install build-essential linux-headers-generic 
Download the file you referenced. By default, file downloads go to your desktop. Right-click the file and select 'Extract Here'. A folder will be created called rtl8192se_linux_2.6.0014.0115.2010.

You can use the Tab key to fill in the blanks in Linux. We will use it next.     Code:
     cd Desktop/rtl8 
Press Tab and then Enter.     Code:
     sudo su
make
make install
modprobe r8192se_pci
exit
iwconfig 
Do you now have a wireless interface, wlan0, perhaps? Can you click the Network Manager icon, see networks and connect?

Have you earned your Ubuntu wings?I finally am able to post this using my wireless internet connection.  When I originally tried, I was using the old kernel X.16, so maybe that is what the original issue is?

David, I hope you have the same luck.

If it is of any use, I have Ubuntu 9.10 installed (upgraded via the upgrage manager from my 9.04 install). and it is the 32bit version of Ubuntu that is installed, although it is a 64bit computer (Toshiba sattelite L505 with the cheap dual core pentium..  tt0555 or something..)  and 64bit wireless from what i can tell.  Ubuntu was installed as a dual boot with windows 7, though I did manage to completely screw the installation of windows 7 in the process.

---

### Post by skeetch79 on 2010-03-19
I am newbie to Ubuntu and have to say I absolutely love it so far! (I was hooked after browsing through the Live CD and taking this awesome OS for a test drive!)

I have a Toshiba Satellite A505-S6980 now running a dual boot with Ubuntu 9.10 64-bit and Windows 7 64-bit. 

For the last few days I was having a heck of a time getting my Realtek RTL8191SE wireless card to work, let alone noticed by Ubuntu, and was ready to reformat the partition Ubuntu resided on and give the HD space back to Windoze 7.

After reading many posts I finally stumbled across the following file ([http://mysite.verizon.net/skeetch79/tar-gz/Realtek_rtl8191se_linux.tar.gz](http://mysite.verizon.net/skeetch79/tar-gz/Realtek_rtl8191se_linux.tar.gz)). The file includes a readme.txt file, which after following the instructions in _Section III. Start Up Wireless, Method 2_, I am up and running beautifully. Make sure NDISWRAPPER is installed on your system before you start.

Here are the instructions beneath _Section III. Start Up Wireless, Method 2_. Good luck. Let me know if it works for you! (Extract the file and then using Terminal cd to that directory - so you now are at the parent)

[COLOR=Red]<<Method 2>>
    Not install driver But Only load the driver module to kernel and 
    start up nic.
    1. Compile the drivers from the source code
       make

        2. Copy firmware to /lib/firmware/ or /lib/firmware/(KERNEL_VERSION)/
           cp -rf firmware/RTL8192SE /lib/firmware           or
           cp -rf firmware/RTL8192SE /lib/firmware/(KERNEL_VERSION)
           Note: This depends on whether (KERNEL_VERSION) subdirectory exists 
             under /lib/firmware

    3. Load driver module to kernel.
       ./wlan0up
           Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes 
         out after run ./wlan0up, please run ./wlan0down first, then it 
         should Be ok..
       Note: If you see the message of "unkown symbol" during ./wlan0up, it
         is suggested to start up nic use <<Method 1>>.

    4. start up nic
       ifconfig wlan0 up[COLOR=Black]

As a note, per copying the firmware (#2), I logged into my root and ran the first line only ([/COLOR][/COLOR][COLOR=Red]cp -rf firmware/RTL8192SE /lib/firmware[/COLOR][COLOR=Red][COLOR=Black]) with no problem, loaded the driver (#3) ([/COLOR][/COLOR][COLOR=Red]./wlan0up[/COLOR][COLOR=Red][COLOR=Black]) again with no problem, and then the minute I struck the enter key after #4 ([/COLOR][/COLOR][COLOR=Red]ifconfig wlan0 up[/COLOR][COLOR=Red][COLOR=Black]) I saw the notification that wireless networks were available - no reboot necessary!

Another note, I extracted the attached tar.gz file to my /tmp directory and ran everything form there. Also, not sure if this mattered, but I had first downloaded the Windows 7 RTL8191SE-VA2 driver (size: 16511K) from the following page ([http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2)) and installed it using NDISWRAPPER (System->Administration->Windows Wireless Drivers) before following the instructions above.

Good luck!!! :P
[/COLOR][/COLOR]

---

### Post by skeetch79 on 2010-03-19
Addendum:
 
I found upon restarting my computer and logging back into Ubuntu that my Wireless was again not active - even after I made it active as per the above post - I had to rerun the wlan0up command
 
Digging around, I found a sure solution to the problem. 
 
(As a foot note, I unzipped the drivers for my RTL8192se into a folder called rtl8192se within /home/brett - path = /home/brett/rtl8192se. 
 
Here is how I get it to work automatically after I log in:
 
1. I log into Ubuntu
2. I open Terminal (Applications->Accessories->Terminal)
3. I log in as Superuser ("sudo su") - without quotes
4. I issue the command "sudo gedit /etc/rc.local" - without quotes
5. Above the line that says "exit 0" and below any other code (especially that which contains "#" as the first character in the line) I entered the following commands:
 
  cd /home/brett/rtl8192se
  ./wlan0up
  ifconfig wlan0 up
 
I then saved the file and then closed out of it.
 
Now everytime I log into Ubuntu those commands execute and my wireless is up, connected and running!
 
That's it!

---

### Post by brobinson319 on 2010-03-21
Chili555,
Your tutorial worked perfect for me!!  I want to say first off that I am new to Ubuntu, so my questions might be stupid.
I am running Ubuntu from a flash drive simply because I want an OS that I can take on the go and being new I didn't want to screw up my laptop.  I can load my wireless drivers just fine with your tutorial but when I reboot the drivers are gone and I have to go through the process again.  How do I install the drivers so that they load every time I boot up.  Also, everything that is in my downloads folder and on the desktop are all gone as soon as I re-boot.

Thanks for your help!!
Brian

---

### Post by chili555 on 2010-03-21
I believe you are running in a live environment, meaning it runs from the flash drive, but you cannot change anything on the Ubuntu filesystem. When you download files or make changes, they are on the computer's RAM. When you reboot, the memory is wiped clean.

[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)

This is an area that is outside my area of experience. You might post your question here:  [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

You also might see if there is space on the flash drive to drop your downloads there.

About 75 years ago, when I first started in Linux, we, the crazed super-geeks, used to remaster live CDs with our preferences, bookmarks, etc. I do not know if remastering is an option.

In any event, have fun!

---

### Post by brobinson319 on 2010-03-21
Thank you for your reply.  So if I run the OS from my local drive and load my wireless drivers they will remain after re-booting?  If this is the case, I will add a partition.

---

### Post by chili555 on 2010-03-21
Yes, indeed. Since you built the driver from source, you will need to rebuild it each time you get a new kernel, known in Ubuntu as linux-image. Eventually, since these devices are so popular, the correct driver will be built-in.

When a new linux-image comes along, for example, 2.6.31-21, maybe, you will need to:```
cd directory/where/you/downloaded
sudo su
make clean
make
make install
modprobe r8192se_pci
exit
```When you do a hard-drive install, Update Manager will offer you a few updates (300 or so, maybe) including an updated linux-image, so be ready to rebuild. Reboot into the latest kernel and build.

---

### Post by nvphung90 on 2010-03-22
> ck121mm@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:FF:C2:92
                    ESSID:"baobienmobile"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-57 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700108C476898339A5B2E172F002401FFC29210210006442D4C696E6B102300074449522D363030102400074449522D3630301042000830303030303030301054000800060050F2040001101100074449522D363030100800020086
                    Extra: Last beacon: 204ms ago
          Cell 02 - Address: 00:14:BF:83:69:65
                    ESSID:"Theu vi tinh Phuong Anh"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality=86/100  Signal level=-57 dBm  Noise level=-113 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4ms agoI followed your instructions and I could scan some Access Points, but now I dont know what to do next to get my laptop connect to them? May anyone give me a guidance ?

---

### Post by chili555 on 2010-03-22
> I dont know what to do next to get my laptop connect to them? May anyone give me a guidance ?Click the Network Manager icon at the top right, see your network, click connect and supply your WPA password. 

If you don't see the icon, right click the panel and add Notification Area and it should appear. Please see attached.

---

### Post by euriconeto on 2010-03-22
Hi All,

I don't know nothing about how to run things over the terminal, just got tired of windows a couple of years ago, so I'm not sure if I'm in the right thread. I believe I have a very similar problem though.

I bought a HP dv6 2120tx and installed karmic 64bit. After installation, the only way I could access internet was plugging the cable. Neither wireless nor my mobile key are working. Which makes my new laptop quite useless...

The network applet only shows "enable networking"; the "enable wireless" one never showed up.

My router is a NETGEAR - DG834G-v5 and my mobile key is a - huawei usb key (couldn't get more info about it)

For more details on wireless card specifications or other details, please let me know step by step how to get these info from the terminal.

Thanks for your help!
Eurico

---

### Post by chili555 on 2010-03-22
> my mobile key is a - huawei usb key (couldn't get more info about it)Please start a new thread. We're not at all sure your device is a Realtek 8192 and we suspect it's not! I will be right here to help you.

In your first post, please insert the device and open Applications > Accessories > Terminal and run:```
lsusb
```Post the result and we'll get started.

---

### Post by nvphung90 on 2010-03-22
> **chili555 said:**
> Click the Network Manager icon at the top right, see your network, click connect and supply your WPA password. 

If you don't see the icon, right click the panel and add Notification Area and it should appear. Please see attached.

I can connect with my wireless card now :D. Thanks a lot for your help :popcorn:!

---

### Post by brobinson319 on 2010-03-22
Chili555,
Thank you very much for all of your help.  I installed Ubuntu on a separate partition and everything is working great including my network printer.  Your the Man!!  Now I can start having some fun and find out what all of the buz is about.

Brian

---

### Post by BigDaveyJ on 2010-03-22
Yes! I need this for my laptop as well!

---

### Post by brobinson319 on 2010-03-23
BigDavey,
Are you having troubles getting your wireless to work?

---

### Post by Kung! on 2010-04-22
Wow...I must be one of the REALLY lucky ones.  I've also got an RTL8192SE card in my Toshiba L500D; and all I had to do was

- download the drivers from the realtek website, and then
- make/make install them.

And they work perfectly.  :D

Now I just have to get the Mobility Radeon drivers working somehow.

---

### Post by vcallas on 2010-05-01
I have recently updated to 10.04 64 bit and I no longer have internet access on my Toshiba L450 -01 with rtl8191se wireless to work. My home network is visible but there is no internet access. I had my wireless working under 9.10 using the driver from realtek as long as my laptop was plugged in though my connection would only last a short period using battery power.

---

### Post by David Bolton on 2010-05-03
As the original poster of this thread I thought I'd share an update. 

moaoci [suggested that I email realtek for support]("http://ubuntuforums.org/showpost.php?p=8957805&postcount=38"). I got a response back with a new download and similar compilation instructions to the ones I received here. However I didn't have any more luck than I had with the downloads mentioned in this thread. I emailed back for more help and to let them know that it still wasn't working. I never received a reply.

[chili555 mentioned]("http://ubuntuforums.org/showpost.php?p=8949682&postcount=34") a bug report. I have subscribed to it to follow any news[]("http://ubuntuforums.org/member.php?u=35909") and developments. A few days ago it was marked as a duplicate of a fixed bug. I decided to try 10.04. [A comment in the new bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/567016/comments/12") further clarified that the fix is in lucid-proposed so I enabled the prerelease updates. Unfortunately the wireless still does not work for me. 

10.04 only boots in recovery, fail-safe-graphics mode. I only mention this in case it is possible that booting in recovery mode might disable the wireless?

---

### Post by chili555 on 2010-05-03
> I only mention this in case it is possible that booting in recovery mode might disable the wireless?Network manager is a graphical application, so that it can't start until X, also known as the graphical desktop starts. NM is the mechanism that scans for networks, sets the EESID and encryption and starts dhclient. The net result is no graphical desktop equals no wireless. You could certainly do all the necessary work in the command line.```
sudo iwlist wlan0 scan
sudo iwconfig wlan0 essid mylilrouter
sudo iwconfig wlan0 key 0123456789
sudo dhclient wlan0
```This assumes a WEP network; WPA is only a bit more complex.

---

### Post by David Bolton on 2010-05-09
I reinstalled 10.04 and downloaded the latest updates. This time I only installed the recommended (stable) updates. I heard from the bug reports that the latest kernel updates contain the relevant fixes for my wireless card. Unfortunately it didn't seem to work for me yet. 

I no longer have to boot using fail-safe-graphics mode. In case it is relevant I still have to boot with nomodeset in order to see the desktop. 

My wireless connection is WPA

---

### Post by matey3 on 2010-06-24
this may be old thread but it is a new problem to me.
I cannot get on wireless either and I read all the posts from before.

One thing I learned is that if you dual boot with Windows, make sure you Disable the Power Save feature on the LAN Device in Windows. Sometimes Windows puts the device (RTL8191 or wlan0 etc,) to sleep and if you do not reboot back into Windows the device may never "wake up".


BTW I get this when I do ifconfig;

```

wlan0     Link encap:Ethernet  HWaddr 40:61:84:20:c1:00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:ffffc0003160000-ffffc0003160100 

wlan0:avahi Link encap:Ethernet  HWaddr 40:61:84:20:c1:00  
          inet addr:169.254.6.50  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Memory:ffffc0003160000-ffffc0003160100 





```

---

### Post by matey3 on 2010-06-30
BTW I installed the updates via Administration-Update Manager and the next time I rebooted it found my Wireless Router!

I had already used the apt-get install update before but it didnt work.

Now I am wondering why when in xdm as root I get No Sound??
I mean I can play a DVD and I have sound, but the system has no sound and the volume control does not work when playing the DVDs!?

---

### Post by phantomSponge on 2010-07-23
Hi All,

Just wanted to add my 2 pennies worth....  Tosh laptop using a realtek rtl8192se driver on ubuntu 10.04.  Problem was similar to a few mentioned in this post:  could see wireless networks but could not connect - constantly asking for WPA key.

Downloaded latest drivers for nic:

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2302](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2302)

followed instructions that came with and worked fine!

Some great help/hints/advice on this thread!

Cheers

---

### Post by David Bolton on 2010-10-09
I just tried the release candidate for Ubuntu 10.10. Wireless worked right away (no configuration necessary). This is the first time I've been able to use the wireless using Linux! USB and the restricted drivers for 3D graphics also work for the first time with this release.

Thank you for your help back in March. Is there a way to mark this thread as solved?

---

### Post by Bucky Ball on 2010-11-21
- 'Thread tools' at top right.
- 'Mark thread as solved'

---

### Post by RobCham on 2011-04-21
Just though I'd add a note to say I found this thread useful to get my Edimax PCI Express card working with Ubuntu Studio 10.10 (it appeared as RTL8191SEvB with lspci - rebranding I guess). Anyway, I installed the latest RTL8192SE driver from the Realtek website (Release date 2010-0115, ver0014 using the readme section III startup wireless method 1) but it didn't quite work. I found i needed to add the following to /etc/rc.local ...

ifconfig wlan0 down
cd /usr/local/src/RTL8192  <-or where the driver was unzipped and make done
./wlan0up
ifconfig wlan0 up

---

