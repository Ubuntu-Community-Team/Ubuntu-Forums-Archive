---
title: "Internet connection lost but email still works"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by WileyGaia on 2010-11-24
Hi
I am a non-techie, have been gratefully using Ubuntu 8.10 for a few years for the basics: email, web, documents, photos.
I have somehow lost my internet connection, but strangely my email still works...!?!? My router is showing all the correct green lights, but I cannot get to any url. I am posting this thread via work (windows) pc.
I have searched on this forum and in anticipation have done as much homework as possible, see below.
I have a Netgear wired router.
I cannot find Network manager on the menus and tried this from the terminal:
```
network-manager 
bash: network-manager: command not found 

 networkmanager 
bash: networkmanager: command not found 
```

my netgear router is pinging successfully:
```
 ping 192.168.0.1 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.81 ms 
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.814 ms 
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.804 ms 
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.809 ms 
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=0.808 ms 
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=0.740 ms 
^C 
```

i have no idea what all this is but it's what i found the gurus asking in other threads:
```
ifconfig -a

eth1      Link encap:Ethernet  HWaddr 00:30:18:a8:46:0a   
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::230:18ff:fea8:460a/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000   sudo ifup eth1 
ifup: interface eth1 already configured 
          RX bytes:302998 (302.9 KB)  TX bytes:21934 (21.9 KB) 
          Interrupt:16  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:752 (752.0 B)  TX bytes:752 (752.0 B) 
 
pan0      Link encap:Ethernet  HWaddr 42:1a:f3:f7:b1:c5   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

```
```
route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1 
0.	192.168.0.1     0.0.0.0         UG    0      0        0 eth1 

```
```
sudo lshw -C network 
  *-network                
       description: Ethernet interface 
       product: Marvell Technology Group Ltd. 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth1 
       version: 12 
       serial: 00:30:18:a8:46:0a 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 42:1a:f3:f7:b1:c5 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

```
```
sudo ifup eth0 
Ignoring unknown interface eth0=eth0.

 sudo ifup eth1 
ifup: interface eth1 already configured 

```
```
lspci 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 
01:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 12) 
```

I also have some screen shots of the "Net Tool" pls asvise if i should post them (apologies I am not at home with my ubuntu machine, I copied all the above to a doc and brought it to work with me)

---

### Post by nasul on 2010-11-24
Never heard about this strange problem, but I think it's the router.

---

### Post by mörgæs on 2010-11-24
If you are on 8.10, it is due time to install to an newer version. 

8.10 is unsupported and therefore a security threat.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by WileyGaia on 2010-11-24
whoah!
just always been scared to upgrade since everytime i go to the forums its always riddled with users having upgrade issues... 
But I guess I better heed your advice and take the plunge... or get a mac :-)

---

### Post by WileyGaia on 2010-11-24
I just realised - I can't upgrade since I do not have an internet connection.... lovely :-(

so please - can anyone help, so that I can upgrade?

---

### Post by grahammechanical on 2010-11-24
Ifconfig shows that eth1 is UP and RUNNING and you have an Internet address - inet addr:192.168.0.2. So, I guess that you should be connected to a router. When I was using 8.10 I used a dial-up modem. Now I have broadband under 9.10, 10.4 and 10.10 and the menu access to networking tools is much improved. All I can suggest is to look through the trouble shooting guide. It is what I review. Here is the link.

[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

I know it is WiFi but there is information useful of wired connection fault finding.

Is the problem with your web browser? Do you have a firewall installed? Is it blocking access? Have you changed the user permissions and removed access to the internet? I cannot guide you through the steps to check these things. I cannot now remember 8.10 and I have learned a bit more since I was using 8.10 through trying to give help on this forum.

regards.

---

### Post by mörgæs on 2010-11-24
Rather go for a clean install than a long series of upgrades
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

Just keep wired internet access while installing and you should be fine.

---

### Post by WileyGaia on 2010-11-24
Thanks people, I guess I will have to do a new install - looks like 10.04 is the preferred choice...

---

### Post by SeijiSensei on 2010-11-24
> **WileyGaia said:**
> Thanks people, I guess I will have to do a new install - looks like 10.04 is the preferred choice...

Have you rebooted your router?  Pull out the power code, wait fifteen seconds, and plug it back in.  See if your problems disappear.

Torrents in particular can knock a router offline because they establish more simultaneous connections to peers than many routers can handle.

---

### Post by pricetech on 2010-11-24
If email is working, you have an Internet connection.  More than likely you have a DNS problem.  Whatever DNS servers your router is looking to for IPs may be down or unreachable for some other reason.  Your router may have the IP of your mail server cached, so you can still get mail.

Rebooting your router won't hurt and could even clear up the problem.  I'd also look at changing the DNS servers your router looks to as a possible solution.

---

### Post by WileyGaia on 2010-11-25
I did try and reboot the router with no success... I decided to uninstall Network Manager from the Synaptic Package Manager, well that was a dumb thing to do, now everything is DOWN. If I boot from the 8.10 CD, all is well, I can connect to www fine... so I am gonna backup files and upgrade to 10.04 - I know that doesn't get to solve the problem here, but at least I will be on a supported version, I'm pretty sure the problem will go away.
Thanks for the responses...

---

### Post by pricetech on 2010-11-25
Lucid is an LTS, so it should last you a few years.  It has worked almost flawlessly for me.

---

### Post by WileyGaia on 2010-11-26
ok ok
i am a dumbass
you're not gonna believe it
so I installed 10.04 and guess what? exactly the same thing i.e. emails working, network is connected, but no internet...
so i phoned my isp... wait for it...
I have reached my monthly 1GB cap, need to top up... thanks so much for not letting me know dear ISP grrrrrr.
Well at least I now have a LTS version of Ubuntu! :-)

Apologies for leading you all down the garden path with this...

---

### Post by mörgæs on 2010-11-26
Rofl. Well, none of us answering thought of that, so I guess we all learned something. 

Have fun in 10.04.

---

### Post by pricetech on 2010-11-29
> **WileyGaia said:**
> I have reached my monthly 1GB cap, need to top up... thanks so much for not letting me know dear ISP grrrrrr.

That sucks.  Oh well.  I guess we'll make a note of that one for future reference.

You would think though that since you still have email they would let you know you'd reached your cap.

---

