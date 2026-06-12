---
title: "wifi fail error"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by tongsengpakronilezat on 2011-08-11
just installed ubuntu-11.04-desktop on my pc, dual booted with WVista. Everything's is ok until i tried to connect to the web. My wireless connection failed with following error message :
ERROR:root: could not find def gateway
ERROR:root: could not find info in /proc 

I already input data in the network wireless connection asf : 
IPv4 192.168.1.104
mask 255.255.255.0
gateway 192.168.1.1
connection automatically

But, still failed. I used the same configuration in my other computer ( mac, *.*.*.102 ), and it's ok. 

Please give some clue about how to overcome this problem . . . thanks.

---

### Post by lmarmisa on 2011-08-12
How did you define the network configuration?. Did you use the Network Connections menu?.

---

### Post by tongsengpakronilezat on 2011-08-12
This is the data i collect from my pc :


iwconfig :

lo        no wireless extensions	

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
sudo iwlist scan :

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


ifconfig -a :

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12480 (12.4 KB)  TX bytes:12480 (12.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:8e:54:3e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lspci -nn :

00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c3] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge [8086:27b0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
04:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]

uname -rm :

2.6.38-8-generic i686

nm-tool :

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:1C:26:8E:54:3E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

sudo lshw -C network :

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:feafc000-feafffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:26:8e:54:3e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


What should i do next ?
many thanks

---

### Post by nm_geo on 2011-08-12
Install the following firmware in terminal or go to Synaptic and get it.
If it returns that it can't be found. You need to update & upgrade see bottom command. 
 
```
 
sudo apt-get install firmware-b43-installer

```
 
```
 
sudo apt-get update && sudo apt-get upgrade

```
 
Reboot if needed.
 
I just let network manager and my wireless assign my working ip with DHCP.

---

### Post by tongsengpakronilezat on 2011-08-12
Done the 1st code, and failed with error message asf :

E:Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable )
E:Unable to lock the administration directory ( /var/lib/dpkg/ ) is another process using it ?

Run the 2nd code, with more or less the same error message.

Previously, I already tried < sudo apt-get install broadcom-sta-common > also with the same result ( E:unable to locate package broadcom-sta-common ) ...

What's up? What should I do next ?

Thanks anyway nm_geo . . . .

---

### Post by nm_geo on 2011-08-12
> **tongsengpakronilezat said:**
> Done the 1st code, and failed with error message asf :
 
E:Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable )
E:Unable to lock the administration directory ( /var/lib/dpkg/ ) is another process using it ?
 
Run the 2nd code, with more or less the same error message.
 
Previously, I already tried < sudo apt-get install broadcom-sta-common > also with the same result ( E:unable to locate package broadcom-sta-common ) ...
 
What's up? What should I do next ?
 
Thanks anyway nm_geo . . . .
 
[COLOR=red]**E:Unable to lock the administration directory ( /var/lib/dpkg/ ) is another process using it ?**[/COLOR]
 
Did you have Synaptic open while you tried the terminal commands?  Close everything that would add software then try the commands

---

### Post by tongsengpakronilezat on 2011-08-12
ok, i'll shut down the synaptic and try again . . .

---

### Post by tongsengpakronilezat on 2011-08-12
regarding broadcom-sta-common and firmware-b43-installer, it says < E:Unable to locate package >

Regarding 2nd code, ( after everything's <done>, the end result is  :
0 upgraded
0 newly installed
0 to remove
0 not upgraded

---

### Post by nm_geo on 2011-08-12
Hmmm... I have assumed again do you have ethernet connection to the computer that we are discussing here?

If you do not have any connection on the computer in question try this link message #21 by the doctor chili555.

[http://ubuntuforums.org/showthread.php?p=11075482](http://ubuntuforums.org/showthread.php?p=11075482)

---

### Post by tongsengpakronilezat on 2011-08-12
I do have connection to the internet ( i'm sending this mail through another computer via the same wi-fi router ). The said computer ( Acer Aspire L-3600 ) has adequate hardware, because formerly I have normal wi-fi access to the internet ( actually, i was upgrading from Ubuntu 9 to 11 when this problem happened ). Do you think  i should reinstall the Ubuntu 11 ?

---

### Post by nm_geo on 2011-08-12
Do you have an ethernet cable even the one that goes into the wireless access point?   It sure would make it easier to get the things you need. The firmware you need has to be downloaded or you could get it from that link on the working computer moves it to the one with wireless problem and follow chili555's instructions.  I am sure re-installing will land you right in the same spot again.

---

