---
title: "wireless not enabled 9.04"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by kimbroBranch on 2009-11-08
Dell Inspiron 1545, 9.04 clean install yesterday. Let the update manager install all updates.
I am new to this environment.
The dropdown dialog insists that both network and wireless are enabled. When I press f2 or fn-f2 the dialog continues to claim that the wireless is enabled.
However, no wireless is detected. I've tested more than one wifi location.

Before I started trying to follow the advice on the community sites, I got:

$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:25:64:4D:EB:28

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:26:5E:54:70:49

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    TRENDnet:        Infra, 00:14:D1:62:08:0F, Freq 2437 MHz, Rate 0 Mb/s, Strength 100

It appears that it was detecting my router, but not letting me know via the network icon.

Installed fwcutter and the access point went away (not good, I think).

Have tried to install the recommended Dell windows device driver.

ndisGTK declared "Unable to see if hardware is present" and in its dialog box listed bcmw16 "Hardware present".  I don't understand that contradiction.

I am going to try to give enough information so you wonderful folks may help me:
branch@lap:~$ cat /etc/modprobe.d/blacklist-bcm43.conf 
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
branch@lap:~$ ls /etc/modprobe.d/
alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  libpisock9.conf
blacklist-bcm43.conf    blacklist-modem.conf        ndiswrapper
blacklist.conf          blacklist-oss.conf
branch@lap:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:54:70:49
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:4d:eb:28
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.10.102 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ba:8f:dc:10:ed:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
branch@lap:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

branch@lap:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:4d:eb:28  
          inet addr:192.168.10.102  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe4d:eb28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91028999 (91.0 MB)  TX bytes:3572396 (3.5 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:26:5e:54:70:49  
          inet6 addr: fe80::226:5eff:fe54:7049/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:568 (568.0 B)  TX bytes:568 (568.0 B)


branch@lap:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:25:64:4D:EB:28

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.10.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1

    DNS:             192.168.10.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:26:5E:54:70:49

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



THANK YOU!

---

