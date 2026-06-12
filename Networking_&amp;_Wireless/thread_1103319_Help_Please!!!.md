---
title: "Help Please!!!"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by BillyPrefect on 2009-03-22
I have a Dell 1720 with the Dell 1505N which is really the Broadcom 4328 wireless card in it. 

After many attempted fixes, I've realized that I have a new module in /etc/modprobe.d/ called 'ndiswrappe' 

How do I get rid of that so I can start again ... everytime I try something I get an error and I believe it is related to whatever is in the mispelled ndiswrapper module.  

Side note:  I may have had a beer or two while messing with the system.

Any help would be appreciated.

---

### Post by abyssius on 2009-03-22
> **BillyPrefect said:**
> I have a Dell 1720 with the Dell 1505N which is really the Broadcom 4328 wireless card in it. 

After many attempted fixes, I've realized that I have a new module in /etc/modprobe.d/ called 'ndiswrappe' 

How do I get rid of that so I can start again ... everytime I try something I get an error and I believe it is related to whatever is in the mispelled ndiswrapper module.  

Side note:  I may have had a beer or two while messing with the system.

Any help would be appreciated.

Billy you can either rename it back to "ndiswrapper" or delete it. It's only a text file.

---

### Post by BillyPrefect on 2009-03-22
ok, that's gone... now any help with the broadcom 4328 ???

---

### Post by abyssius on 2009-03-22
> **BillyPrefect said:**
> ok, that's gone... now any help with the broadcom 4328 ???

Billy, can you tell me exactly how far you got with this?  How did you install ndiswrapper? Do you have the required Windows .sys and .inf files for your network adapter? If you've installed the driver with ndiswrapper, can you confirm that it is loaded? You can use this code:
```
sudo ndiswrapper -l[.CODE]

Also, If the driver is loaded, it would help if you posted the output of:
[CODE]sudo ifconfig -a
```
This could give hints as to where you stand.

---

### Post by BillyPrefect on 2009-03-22
root@billy-laptop:/home/billy/Desktop# lshw -C Network
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:c7:d5:64
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.199 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:c3:c5:d9:16:38
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by BillyPrefect on 2009-03-22
root@billy-laptop:/home/billy# sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:c7:d5:64  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:396961 (396.9 KB)  TX bytes:75652 (75.6 KB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:1e:4c:30:d9:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7300 (7.3 KB)  TX bytes:7300 (7.3 KB)

pan0      Link encap:Ethernet  HWaddr 4e:c3:c5:d9:16:38  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by BillyPrefect on 2009-03-22
ignore eth1 no device exists.

---

### Post by abyssius on 2009-03-22
> **BillyPrefect said:**
> ignore eth1 no device exists.

Billy it seems like you have an IP address: 192.168.0.199 on eth0 (which I'm assuming is your wireless adapter). Usually with wireless networks, the wireless adapter is identified with a logical name like wlan0, but it's not a fixed rule. It also seems like Ubuntu is loading a driver for your device. Use this command to see a history of how eth0 is set up.
```
dmesg | grep eth0
```. This should tell you if the driver has loaded successfully, or if the OS encountered a problem. If you see an error message, post it so we can see what's happening. If it seems okay, then we can proceed,. 

Try this command:
```
iwconfig eth0
```
And post the output. I'm sorry for the delay. I'll keep watching you posts from now on.

---

### Post by dodle on 2009-03-22
I got my broadcom card working with b43-fwcutter.  No Windows driver needed.

---

### Post by BillyPrefect on 2009-03-22
I got it!!!  Using a combination of many different results/posts/builds/versions I stumbled across something that fixed it... however my wired connection isn't working right now.  I'm skipping that for now, pretty sure I can get over that.

I think that ssb module thing is overriding any attempt I try to get things working.  I have to rmmod b44, then ssb - lshw -C network then shows everything unclaimed.  Then I modprobe wl then b44, and repeat lshow and get results without the ssb module.  Wireless then turns on, and by using the network icon up in the title bar I give the password and I'm on!!!

My wired connection is still dead, going to play around a bit and see what combination will get both to be able to work (one at a time) then see what I can do about getting some sort of automatic connectivity.

Oh ya... eth0 is wired, eth1 is wireless on this crappy Dell 1720.

Then my 

root@billy-laptop:/home/billy# iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"wiredlessly"  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1B:11:74:01:C0   
          Bit Rate=14 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-42 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

