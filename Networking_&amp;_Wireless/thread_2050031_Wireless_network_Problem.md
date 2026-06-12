---
title: "Wireless network Problem"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by kooldude1986 on 2012-08-29
I have dell inspiron n5040 64 bit laptop.I have been working on my wifi connectivity in Ubuntu 12.04 for days now. I have tried out everything and every command posted on this site relating to wireless network problem but nothing worked. 

 Please help me out and do provide me with a solution.

---

### Post by AndyOpie150 on 2012-08-29
Hey kooldude1986 maybe you could go here: [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) and post your results of the commands. This should help others to diagnose what ails your Wireless.

---

### Post by kooldude1986 on 2012-08-29
Hi AndyOpie150,

As i'm new to ubuntu, I don't know how to figure out the network problem. I have the output of the commands, please let me know if you could help me find solution for my problem.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux ubuntu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
mandar@ubuntu:~$ 
mandar@ubuntu:~$ lspci -nnk | grep -iA2 net
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Dell Device [1028:0013]
	Kernel driver in use: brcmsmac
--
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:0505]
	Kernel modules: r8169
mandar@ubuntu:~$ 
mandar@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 0bda:58c0 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
mandar@ubuntu:~$ 
mandar@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Excalibur"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:7F:74:8D:1C:DC   
          Bit Rate=36 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:279   Missed beacon:0

mandar@ubuntu:~$ 
mandar@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by AndyOpie150 on 2012-08-30
Have you installed the drivers for your Wireless Lan controller using ndiswrapper?
 
EDIT: Be back in an hour or so if nobody else has picked this up.

---

### Post by kooldude1986 on 2012-08-30
I guess i have nt ...and my wired internet is also not working..but anyways how will i knw that....? which command..

---

### Post by kooldude1986 on 2012-08-30
I have pasted all of the output of command in my previous post. Can you find it there?

---

### Post by steeldriver on 2012-08-30
The Broadcom cards are often troublesome - can you post the outputs of these commands as well please:

```
lshw -C network

lsmod | grep -e wl -e b43

```

This will let us see info about the driver / firmware

---

### Post by nativehound on 2012-08-30
looks like your connected to the router.

post this output please 

```
ping 0
```

```
nm-tool
```

and try google's ip via firefox. some routers block ping requests.

```
firefox 74.125.224.72
```

---

### Post by Finnicella on 2012-08-30
This is the problem
> Kernel driver in use: brcmsmac
You must to put **brcmsmac** in blacklist and load **wl**
Bye

---

### Post by kooldude1986 on 2012-08-30
$ ping 0
PING 0 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.049 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.051 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.052 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.056 ms
64 bytes from 127.0.0.1: icmp_req=5 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_req=6 ttl=64 time=0.030 ms
64 bytes from 127.0.0.1: icmp_req=7 ttl=64 time=0.027 ms
64 bytes from 127.0.0.1: icmp_req=8 ttl=64 time=0.031 ms
64 bytes from 127.0.0.1: icmp_req=9 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_req=10 ttl=64 time=0.033 ms
64 bytes from 127.0.0.1: icmp_req=11 ttl=64 time=0.026 ms
64 bytes from 127.0.0.1: icmp_req=12 ttl=64 time=0.029 ms
64 bytes from 127.0.0.1: icmp_req=13 ttl=64 time=0.025 ms
64 bytes from 127.0.0.1: icmp_req=14 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_req=15 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_req=16 ttl=64 time=0.033 ms
64 bytes from 127.0.0.1: icmp_req=17 ttl=64 time=0.028 ms
^[64 bytes from 127.0.0.1: icmp_req=18 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_req=19 ttl=64 time=0.027 ms
64 bytes from 127.0.0.1: icmp_req=20 ttl=64 time=0.027 ms
64 bytes from 127.0.0.1: icmp_req=21 ttl=64 time=0.033 ms
64 bytes from 127.0.0.1: icmp_req=22 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_req=23 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_req=24 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_req=25 ttl=64 time=0.033 ms
64 bytes from 127.0.0.1: icmp_req=26 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_req=27 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_req=28 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_req=29 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_req=30 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_req=31 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_req=32 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_req=33 ttl=64 time=0.043 ms
64 bytes from 127.0.0.1: icmp_req=34 ttl=64 time=0.040 ms
64 bytes from 127.0.0.1: icmp_req=35 ttl=64 time=0.036 ms
64 bytes from 127.0.0.1: icmp_req=36 ttl=64 time=0.035 ms
64 bytes from 127.0.0.1: icmp_req=37 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_req=38 ttl=64 time=0.049 ms
64 bytes from 127.0.0.1: icmp_req=39 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_req=40 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_req=41 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_req=42 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_req=43 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_req=44 ttl=64 time=0.043 ms
64 bytes from 127.0.0.1: icmp_req=45 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_req=46 ttl=64 time=0.038 ms
64 bytes from 127.0.0.1: icmp_req=47 ttl=64 time=0.043 ms
64 bytes from 127.0.0.1: icmp_req=48 ttl=64 time=0.040 ms
64 bytes from 127.0.0.1: icmp_req=49 ttl=64 time=0.037 ms
^C
--- 0 ping statistics ---
49 packets transmitted, 49 received, 0% packet loss, time 47998ms
rtt min/avg/max/mdev = 0.025/0.037/0.056/0.010 ms

----------------------------------------------------------------------------------------------------------------


nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        E0:06:E6:2B:1B:1D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    kzt:             Infra, C4:3D:C7:55:9D:06, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    rick:            Infra, A0:21:B7:4F:87:CF, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    B0EC46:          Infra, 84:1B:5E:B0:EC:46, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    Enriquez:        Infra, A0:21:B7:C9:76:91, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    A26208:          Infra, 84:1B:5E:A2:62:08, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    NETGEAR23:       Infra, 2C:B0:5D:9C:E5:7A, Freq 2422 MHz, Rate 54 Mb/s, Strength 50 WPA2
    2WIRE724:        Infra, 64:0F:28:14:AD:C1, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Ocho:            Infra, 68:7F:74:8D:F7:19, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    sskr39:          Infra, A0:21:B7:4F:51:53, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    PENJAMO-PC_Network: Infra, A0:21:B7:B0:6C:04, Freq 2442 MHz, Rate 54 Mb/s, Strength 34 WPA
    2WIRE003:        Infra, B8:E6:25:47:7B:51, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Conquistadores:  Infra, C0:3F:0E:80:36:04, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2
    A14B3F:          Infra, 84:1B:5E:A1:4B:3F, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Cisco03773:      Infra, C0:C1:C0:9C:88:12, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    NETGEAR:         Infra, E0:46:9A:7A:09:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    2WIRE717:        Infra, B0:E7:54:D7:F6:A9, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    kot@.com:        Infra, E0:46:9A:60:26:45, Freq 2422 MHz, Rate 54 Mb/s, Strength 37 WPA2
    linksys:         Infra, 00:16:B6:04:D3:A8, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Chandra:         Infra, 84:1B:5E:A5:C3:0C, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    2WIRE543:        Infra, 00:22:A4:88:1D:31, Freq 2457 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    thegirls:        Infra, 20:4E:7F:7F:20:D4, Freq 2427 MHz, Rate 54 Mb/s, Strength 30 WPA2
    GuyInBlue:       Infra, E0:46:9A:55:D7:DD, Freq 2417 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    9FCA42:          Infra, 84:1B:5E:9F:CA:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    2WIRE863:        Infra, B8:E6:25:51:22:29, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    D3E668:          Infra, A0:21:B7:D3:E6:68, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    NGR8C:           Infra, 00:24:B2:9E:49:4A, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA
    DLNK7:           Infra, 00:15:E9:78:B2:10, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WEP
    HPN911a.BD9D1A:  Ad-Hoc, 02:27:57:1B:C7:1A, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    2WIRE089:        Infra, C0:83:0A:13:85:31, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Excalibur:       Infra, 68:7F:74:8D:1C:DC, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    INDIAN:          Infra, 74:44:01:93:8E:0B, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2

The above is the output, of the commands mentioned. "Excalibur" is the one we have a wirless internet access.

@Finnicella: how do i blacklist and load wl. Please send me the command.

---

### Post by Finnicella on 2012-08-30
Hi,
you can blacklist the brcmsmac with this command:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
In the open window add:
```
blacklist brcmsmac
```
at the end of the writing and save.
After that please give:
```
sudo lshw -C network
```
and write here what it says.
Bye

Edit: Please restart Ubuntu after you blacklisted.

---

### Post by kooldude1986 on 2012-08-30
Hi Finnicella,

I have blacklisted the brcmsmac, and rebooted as well. The below is output of the command sudo lshw -C network. But after reboot the wireless connections were not dectected was it because of blacklisting.



 *-network               
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:fbe00000-fbe03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 05
       serial: 24:b6:fd:51:2b:1c
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:e000(size=256) memory:d0b04000-d0b04fff memory:d0b00000-d0b03fff

---

### Post by Finnicella on 2012-08-30
Ok now we must install the broadcom STA driver with these commands:
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
and
```
sudo modprobe wl
```
This is all. Let me know if it works.
I must leave now because is nigth here.
See :p you tomorrow.
Bye

---

### Post by kooldude1986 on 2012-08-30
Hi Finnicella,

I don't have wired internet so i will nt be able to install STA driver. Can you tell any other way out to install driver.

---

### Post by nativehound on 2012-08-30
Download it to a usb or cd.

It's a .deb package so you should be able to just click on it.

[http://packages.ubuntu.com/precise-updates/admin/bcmwl-kernel-source]("http://packages.ubuntu.com/precise-updates/admin/bcmwl-kernel-source")

---

### Post by kooldude1986 on 2012-08-31
Hi nativehound,

There are so many of them, which one to download. And will amd64 work as my laptop is 64bit.

---

### Post by nativehound on 2012-08-31
Yes amd64 will work and choose the mirror closest to you on the download page.

---

### Post by kooldude1986 on 2012-08-31
Hey i downloaded and installed and after that it said installed, i rebooted. But no wireless networks were detected. I had turned on my wireless adapater. Previously on startup it used to detect the wireless networks.

What could be the issue.

---

### Post by nativehound on 2012-08-31
Did run the code Finnicella mentioned after the install

```
sudo modprobe wl
```

---

### Post by kooldude1986 on 2012-08-31
Yes i did ...it said no module wl found.

---

### Post by Finnicella on 2012-08-31
Sorry for the wait. I made research for the driver.
This is the link to download the driver:
[https://launchpad.net/ubuntu/precise/i386/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu6]("https://launchpad.net/ubuntu/precise/i386/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu6")
After the installing these are the commands to give:
```
sudo modprobe -r b43 ssb wl
```
```
sudo modprobe wl
```
Bye

---

### Post by kooldude1986 on 2012-08-31
Hi 

I downloaded bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_i386.deb, and dkms_2.2.0.3-1ubuntu3_all.deb. When i tried installing the bcmwl driver it said could not satisfy dependecies dkms. So i tried downloading dkms and install it. But dkms didnt install, and said install only if trusted. 

Cant't install anyone of them.

---

### Post by Finnicella on 2012-08-31
I found the link for the dkms only in italian wiki, the documentation of ubuntu italian forum.
So the link is:
[apt://dkms.deb]("apt://dkms.deb")
to directly download dkms.deb and try to install.
Sorry, but it's the first time for me to try to install without internet.
Bye and goodnight.
Finny

---

### Post by nativehound on 2012-08-31
Ok did some searching on bcm4313 14e4:4727
It looks like the 4313 is only supported by broadcom's
proprietary driver at the moment.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom")

You download the driver here:

[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

after you download it

```
sudo tar xvzf hybrid-portsrc_x86_64-v5_100_82_112.tar.gz -C /usr/local/src
```

```
cd /usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112
```

```
sudo ./configure
```

```
sudo make
```

```
sudo checkinstall
```

If checkinstall gives any crap about version number add

v5_100_82_112

gl

---

### Post by kooldude1986 on 2012-09-01
Hi NativeBound

I have tried all that you mentioned....this is the output of command. I was not able to install this driver again.

/usr/local/src$  cd  hybrid-portsrc_x86_64-v5_100_82_112

/usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112$ sudo ./configure
sudo: ./configure: command not found

/usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112$ sudo make

KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  LD      /usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112/built-in.o
  CC [M]  /usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112/src/shared/linux_osl.o
  CC [M]  /usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.o
/usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.c:388:2: error: unknown field &#8216;ndo_set_multicast_list&#8217; specified in initializer
/usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.c:388:2: warning: initialization from incompatible pointer type [enabled by default]
/usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.c:388:2: warning: (near initialization for &#8216;wl_netdev_ops.ndo_validate_addr&#8217;) [enabled by default]

make[2]: *** [/usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/usr/local/src/hybrid-portsrc_x86_64-v5_100_82_112] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [all] Error 2

---

### Post by nativehound on 2012-09-01
just reread the tread do you have do you have a 64 0r 32 bit os and
did you get any errors when you installed the amd64 .deb file?

Check if the driver is already installed.

```
dpkg --get-selections | grep wl
```

---

### Post by kooldude1986 on 2012-09-01
Hi,

I downloaded the broadcom from the link from previous theard that u gave me   and tried running the commands u gave me. Thats when i got these errors. Did i do anything wrong.

Mine is a 64bit system.

---

### Post by nativehound on 2012-09-01
No, that tar is a makefile and won't run with those commands i gave you. sorry i should have checked.
First check to see if the driver is installed from that .deb file.
output should look like this.

dpkg --get-selections | grep wl
bcmwl-kernel-source                install
libpwl5                        deinstall

---

### Post by kooldude1986 on 2012-09-01
Its not allowing me install that driver because of dkms dependency and let now allowing me install dkms.

It says "Install only if you trust the origin" and the install button is disabled.

---

### Post by kooldude1986 on 2012-09-01
I tried to install from the iso , then also it didnt work.

---

### Post by nativehound on 2012-09-02
Ok if you can't install the wl driver and dkms. lets try the b43-fcutter driver.
The b43-fcutter supports LP-PHY cards. Download the 64 bit version. 
If the gui is greyed out again. cd and sudo it.
 
[http://www.ubuntuupdates.org/package/core/precise/multiverse/base/b43-fwcutter](http://www.ubuntuupdates.org/package/core/precise/multiverse/base/b43-fwcutter)

---

### Post by 23senick on 2012-09-02
Haven't read everything you've tried, but as a fellow 4313 sufferer, I recall sometimes you need to delete the alternative drivers. This thread helped me, and my wireless works OK generally.  Proprietary drivers definitely work best.  

[http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)

Hope you manage to sort it!

---

### Post by kooldude1986 on 2012-09-02
Native bound i tried installing b43-futter it still greys out and does not install. Is there is anyway of installing b43futter and also dkms. Something like command line.

---

### Post by nativehound on 2012-09-03
Check if your username is associated with the admin group. I think that's why it's greyed out. Also check if dkms is installed already.
Then dpkg the .deb file. 

```
groups putusernamehere
```

```
dkms status -V
```

```
sudo dpkg -i thepackagename.deb
```

---

### Post by kooldude1986 on 2012-09-03
Hi Nativebound,

Finally i could install the driver and installed the driver but thats was of 32bit. Does it matter if my driver is 32bit and system is 64bit.

I xecuted the commands,

sudo modprobe -r b43 ssb wl

sudo modprobe wl

There were wifi networks detected, but could not connect.

The output of sudo lshw -C network is as follows:


sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: eth1
       version: 01
       serial: e0:06:e6:2b:1b:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fbe00000-fbe03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 05
       serial: 24:b6:fd:51:2b:1c
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:e000(size=256) memory:d0b04000-d0b04fff memory:d0b00000-d0b03fff

Let me what should be done next.

---

### Post by Finnicella on 2012-09-04
Sorry, but I have trouble with my pc.
I notice that it doesn't work.
Let see your module with:
```
lspci -k
```
Bye and forgive me.

---

### Post by nativehound on 2012-09-05
Check and make sure wl is not blacklisted.

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

wl needs these modules also.

```
sudo modprobe lib80211
```

```
sudo modprobe lib80211_crypt_tkip
```

```
sudo modprobe wl
```

if nothing changes restart nm

```
sudo /etc/init.d/network-manager restart
```

and post these please.

```
nm-tools
``` 

```
lshw -C network
```

---

