---
title: "Wireless connects but no internet -- Ubuntu 9.04, Realtek 8187B, Gateway Laptop"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by blackwoodarsenal on 2009-09-28
Hey there folks. I'm a complete newbie to Ubuntu, having installed it onto a partition of my Gateway laptop last night, and everything works great except the wireless connection. Right out of the installation I was able to connect to my wireless signal, no issue. However, once I attempt to actually go to a website, it might connect at first, but then nothing. I'll type in "www.facebook.com", and perhaps a few images or text will load, then nothing at all. When I restart, I can get the same thing to happen--a couple things load and then silence. All the while, my connection still reports as strong. On the Windows side of things, my connection runs perfectly.

I tried a few of the fixes online, as well as with the built in help files, such as disabling ipv6. I can't be sure if any of these things really applies exactly to my issue. I imported my drivers from the Windows side, installed ndiswrapper, installed the drivers using the graphical interface, and it says the hardware is detected. Still the same thing. It feels like nothing I do has any effect!

Anyway, here's some of the readouts from the terminal--maybe you guys can help me.

```
trev@bomber-mk3:~$ lsusb
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 002: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
```
trev@bomber-mk3:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"G-House"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:82:0C:FC   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=60/100  Signal level:-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

``````
trev@bomber-mk3:~$ dmesg | grep "wlan0"
[   40.717587] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.720838] wlan0: direct probe to AP 00:1b:11:f0:91:b4 try 1
[   44.921053] wlan0: direct probe to AP 00:1b:11:f0:91:b4 try 2
[   45.120070] wlan0: direct probe to AP 00:1b:11:f0:91:b4 try 3
[   45.320065] wlan0: direct probe to AP 00:1b:11:f0:91:b4 timed out
[   62.241337] wlan0: authenticate with AP 00:0f:66:82:0c:fc
[   62.243086] wlan0: authenticated
[   62.243092] wlan0: associate with AP 00:0f:66:82:0c:fc
[   62.245315] wlan0: RX AssocResp from 00:0f:66:82:0c:fc (capab=0x431 status=0 aid=1)
[   62.245319] wlan0: associated
[   62.248869] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   72.776063] wlan0: no IPv6 routers present
[   94.600943] wlan0 direct probe responded
[   94.600955] wlan0: authenticate with AP 00:0f:66:82:0c:fc
[   94.604073] wlan0: authenticated
[   94.604082] wlan0: associate with AP 00:0f:66:82:0c:fc
[   94.606550] wlan0: RX ReassocResp from 00:0f:66:82:0c:fc (capab=0x431 status=0 aid=1)
[   94.606557] wlan0: associated
```
```
trev@bomber-mk3:~$ sudo lshw -C network
[sudo] password for trev: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:df:e5:19
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:10:c0:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.3.102 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: da:34:01:05:07:24
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
```
trev@bomber-mk3:~$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:82:0C:FC
                    ESSID:"G-House"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/100  Signal level:-41 dBm  
                    Encryption key:on
                    IE: Unknown: 0007472D486F757365
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001f3bec0e17e
                    Extra: Last beacon: 68ms ago

```

I'm running Ubuntu 9.04.

Kernel/architecture: 2.6.28-11-generic i686

Restarting the network:
```
trev@bomber-mk3:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                      
 Ignoring unknown interface wlan0=wlan0.
```

Please help, I've been pulling my hair out trying to get this simple internet thing to work. It would be one thing if it didn't connect at all, or if it didn't find any networks, or if my computer just exploded into flames (then I'd be *certain* what was wrong with it!). No, it actually connects, and then nothing happens after a few seconds.

](*,)

---

### Post by blackwoodarsenal on 2009-09-28
*bump*

I hate to do this, but I'm watching this very carefully all day for help, and I don't want my topic to go unnoticed--I know you guys get a billion of these per day. I'm trying to get this up and running, and I think I've provided some [hopefully] good preliminary information. :)

---

### Post by blackwoodarsenal on 2009-09-30
Still waiting on a reply. I don't want to get lost in the shuffle here--I need this working asap. If I don't have enough information provided to help you guys determine the issue, please let me know.

Help please! :confused:

---

### Post by fidelandche on 2009-09-30
Had the same sort of problem with my Gateway, I used this code and with a reboot it worked fine,
 
sudo apt-get install linux-backports-modules-jaunty

---

### Post by blackwoodarsenal on 2009-09-30
Thanks for the reply. :) I'll give it a try and let you guys know if it worked.

It's irritating that I don't have access to a computer on the side to help troubleshoot (I have to continuously reboot to get back to Ubuntu). I should probably head down to the University library and use one of their computers for the internet.

---

### Post by blackwoodarsenal on 2009-09-30
> **fidelandche said:**
> sudo apt-get install linux-backports-modules-jaunty

This is supposed to download and install something, correct? I have no internet access at all on my Ubuntu partition. I can download things and transfer them from my Vista partition, however. I have a little flash drive I've been using to move crap back and forth.

---

### Post by blackwoodarsenal on 2009-09-30
I guess I'm confused as to what this command does exactly. Does it install something from my Ubuntu CD or does it attempt to download it online? Either way, it can't find the file.

---

### Post by Cuba71 on 2009-09-30
Go to System > Administration > Synaptic Package Manager and do a search for linux-backports-modules-jaunty, and if you find it then install it

---

