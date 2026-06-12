---
title: "Karmic Wireless Problems"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by stevebc on 2010-05-05
Good day,
 
Recently I have encountered Problems with my Wireless that I have not had before and I cannot fix. So I am asking for help.
 
Background:
 
6 month old Dell Insperion 1730 Laptop
Dual boot Karmic/Win 7
WUBI install.
No problems till about a week ago.
 
A week ago I upgraded to Lucid and could not get the DVD drive to mount no matter what. The OS saw it but would not mount it...... uninstall and re -install Karmic.
 
All good at this point.
 
As soon as the patches are installed from the update manager, I lose my wireless completely. Wired connection still works.
 
I have tried different things from here and other sites. Basically I need to know how to enable my wireless card. There is no switch and key combinations (ALT+ F2) don't do anything. Connectivity in Win 7 is fine. 
 
The Applet says wireless is disabled and so does the output from $sudo lshw -C network.
It sees the interface but the network is disabled. lsmod shows the driver. iw list scan says does not support scanning. Newtwork is down.
 
I know there is something in the updates that is messing the Intel WiFi Link 5100 up. On a fresh install all works till updated.
 
Any help is appreciated.
 
Thanks.
 
Steve

---

### Post by mikewhatever on 2010-05-05
Can you try brining up the interface with **sudo ifconfig wlan0 up** - I am assuming the interface name is wlan0.

---

### Post by stevebc on 2010-05-06
I tried it..... but all it did was go back to the prompt.
 
Looking in the network tools, I saw that my wireless interface (wlan0) has the same hardware address as an unknown interface (wmaster0).
 
wlan0 has Multicast enabled, MTU of 1500 and State of inactive.
wmaster0 has Multicast disabled, MTU of 0 ans State of Active.
 
lshw -C network shows *Network disabled with the info for the wireless link from Intel with a logical address of wmaster0.
 
iwcofig shows no wireless extensions under wmaster0, only wlan0.
 
I am still new to Ubuntu (only a couple of months) but everything was fine before updating and still is fine with Win 7.
 
Thanks for the reply and advice. Any suggestions that you give I will try tomorrow (late here) and save outcome as text file to cut/paste. I was not thinking earlier or I'd have done that instead of saving screenshots I can't upload.
 
Thanks.
 
Steve

---

### Post by stevebc on 2010-05-06
Here are the outputs for some things I checked out:
 
```
[steve@ubuntu:~$ sudo iwconfig
lo no wireless extensions.
 
eth0 no wireless extensions.
 
wmaster0 no wireless extensions.
 
wlan0 IEEE 802.11abgn ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
 
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
steve@ubuntu:~$ sudo iwlist scan
lo Interface doesn't support scanning.
 
eth0 Interface doesn't support scanning.
 
wmaster0 Interface doesn't support scanning.
 
wlan0 Interface doesn't support scanning : Network is down
 
steve@ubuntu:~$ sudo ifconfig wlan0 up
steve@ubuntu:~$ 
steve@ubuntu:~$ sudo ifconfig wmaster0 up
steve@ubuntu:~$ 
 

```
and
```
steve@ubuntu:~$ sudo lshw -C network
password for steve: 
 
   *-network DISABLED      
 
 description: Wireless interface
 
 product: Wireless WiFi Link 5100
 
 vendor: Intel Corporation
 
 physical id: 0
 
 bus info: pci@0000:0c:00.0
 
 logical name: wmaster0
 
 version: 00
 
 serial: 00:24:d6:2a:ed:b2
 
 width: 64 bits
 
 clock: 33MHz
 
 capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
 
 configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wirele
 ss=IEEE 802.11abgn
 
 resources: irq:31 memory:f69fe000-f69fffff
 
   *-network
 
 description: Ethernet interface
 
 product: 88E8040 PCI-E Fast Ethernet Controller
 
 vendor: Marvell Technology Group Ltd.
 
 physical id: 0
 
 bus info: pci@0000:09:00.0
 
 logical name: eth0
 
 version: 13
 
 serial: 00:25:64:65:75:02
 
 capacity: 100MB/s
 
 width: 64 bits
 
 clock: 33MHz
 
 capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 
 100bt 100bt-fd autonegotiation
 
 configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A 
 latency=0 link=no multicast=yes port=twisted pair
 
 resources: irq:30 memory:f68fc000-f68fffff ioport:de00(size=256)
 steve@ubuntu:~$ 

```
 
If someone can help please?
 
Steve

---

### Post by stevebc on 2010-05-07
Bump.

---

### Post by stevebc on 2010-05-07
Bump.

---

### Post by stevebc on 2010-05-16
After some time consuming experiments, I have found that it is a kernel problem. When I update the kernel with the Update Manager, I get the problem. I now have everything EXCEPT the kernel update installed and running.
 
Steve

---

### Post by bnuytten on 2010-07-06
> **stevebc said:**
> After some time consuming experiments, I have found that it is a kernel problem. When I update the kernel with the Update Manager, I get the problem. I now have everything EXCEPT the kernel update installed and running.
 
Steve

Not sure if this only related to the kernel. Had issues with kernel 2.6.32-22. I've set managed=true in /etc/NetworkManager/nm-system-settings.conf and restarted the network-manager daemon.

No change. When I set managed=false again, in stead of "device is disabled", I got "device not managed". Anyhow, updated to 2.6.32-23 and reboot. After reboot, nm-applet still said "device not managed".

Change /etc/NetworkManager/nm-system-settings.conf and set managed=true and sudo service network-manager restart. Now working the way it did before.

---

