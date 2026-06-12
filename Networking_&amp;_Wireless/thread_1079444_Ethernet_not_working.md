---
title: "Ethernet not working"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by kymagic on 2009-02-24
I am dual booting 8.10 with XP on a Dell Dimenstion 2400 with a Broadcom BCM4401 NIC. I was running 8.04, where I had no problems accessing the internet. I then installed 8.10 (as a new install and not as an upgrade), which installed fine, but I have no internet connection. Using the default Automatic DCHP setting in "Network Connections", my network connection is aparrently disconnected. When I use the manual setting and supply an IP address and copy the Netmask and Gateway from my Windows installations on the network, the connection is supposed to be connected, but I have no access to the internet. I can't ping anything using Network Tools, either. The computer doesn't appear to even attempt sending the Ping.

My ubuntu box is behind a network switch, which is in turn attatched to the router which is connected to the internet.

One thing I have noticed is that under Devices in Network Tools, the default Network Device on the dropdown menu is "Loopback interface (lo)", and there is IPv4 information there (but with 127.0.0.1 as the IP address and not the address I give in Network Connections) and some IPv6 information listed as well (though it appears to be dummmy information). What I thought was odd was that when I select eth0 from the dropdown list, nothing is listed under IP Information.

Any thoughts? Apart from I should have upgraded? :)

---

### Post by Miguel on 2009-02-24
The bcm4401 NIC is the one I had in my old Dell Inspiron 8600. And should work ok... except that I once hit problems in Hardy with linux-backports-modlues installed.

Anyway, what's the exact setup you are trying to connect? It seems that you want DHCP over ethernet, but just wanted to make sure. Furthermore, after trying to connect to the network, could you please post the contents of /etc/resolv.conf (DNS stuff), /etc/network/interfaces (should be minimal) and the output of the following three commands:
```

$ ifconfig
$ dmesg | grep b44
$ dmesg | tail -20

```

---

### Post by kymagic on 2009-02-24
Thanks for the quick reply.

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:0d:56:51:6d:20
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:53801 (53.8 KB)  TX bytes:1794 (1.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:32000 (32.0 KB)  TX bytes:32000 (32.0 KB)
```

**dmesg | grep b44**
```
[    4.920254] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.987188] b44.c:v2.0
[   38.816191] b44: eth0: Link is up at 100 Mbps, full duplex.
[   38.816202] b44: eth0: Flow control is off for TX and off for RX.
[   57.804641] b44: eth0: powering down PHY
[   57.816130] b44: eth0: Link is down.
[   60.816233] b44: eth0: Link is up at 100 Mbps, full duplex.
[   60.816248] b44: eth0: Flow control is off for TX and off for RX.
[  132.860241] b44: eth0: powering down PHY
[  137.816216] b44: eth0: Link is up at 100 Mbps, full duplex.
[  137.816229] b44: eth0: Flow control is off for TX and off for RX.
```

**dmesg | tail -20**
```
[ 1626.477165] usbcore: registered new interface driver libusual
[ 1626.533844] Initializing USB Mass Storage driver...
[ 1626.539420] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1626.543046] usbcore: registered new interface driver usb-storage
[ 1626.543071] USB Mass Storage support registered.
[ 1626.549349] usb-storage: device found at 4
[ 1626.549367] usb-storage: waiting for device to settle before scanning
[ 1631.548256] usb-storage: device scan complete
[ 1631.549705] scsi 2:0:0:0: Direct-Access              USB Flash Memory 1.04 PQ: 0 ANSI: 0 CCS
[ 1632.047658] sd 2:0:0:0: [sdc] 499712 512-byte hardware sectors (256 MB)
[ 1632.052156] sd 2:0:0:0: [sdc] Write Protect is off
[ 1632.052172] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1632.052176] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1632.068759] sd 2:0:0:0: [sdc] 499712 512-byte hardware sectors (256 MB)
[ 1632.074510] sd 2:0:0:0: [sdc] Write Protect is off
[ 1632.074525] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1632.074529] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1632.083483]  sdc: sdc1
[ 1632.087172] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[ 1632.090941] sd 2:0:0:0: Attached scsi generic sg3 type 0
```



I'm not sure what you mean by asking what setup I am looking for, but I want a static IP address for the computer. Does that answer your question?

---

### Post by Miguel on 2009-02-24
> **kymagic said:**
> I'm not sure what you mean by asking what setup I am looking for, but I want a static IP address for the computer. Does that answer your question?

Yes, that is what I needed to know. Could you please do the following commands? I need to see the contents of two files. Thanks in advance.

```

$ cat /etc/resolv.conf
$ cat /etc/network/interfaces

```

To set up a static IP, you can right-click on the NetworkManager icon (usually has two computers, or a signal strength if you're using WiFi). Here select "Edit connections", which will open a tabbed window.

Here, after selecting the "wired" tab, please click "Add". Here you can choose the name you want and, once you've done it, go to the "IPv4 settings" tab. Click again "Add" and, after selecting "Manual" in the dropdown menu, make sure you fill all three fields (Address, Netmask and Gateway). Netmask is either 255.255.255.0 or 255.255.0.0. If your IP is 10.20.30.XXX, your Gateway is almost surely 10.20.30.1 (i.e. identical, but the last number is "1").

If you know the DNS servers, you can also put them down there, in a comma-separated fashion. I'm attaching a screenshot with the sensible data erased, so you can see how it looks.

Anyway, once you've done this, and left-click on the network manager icon, you should be able to choose between a variety of connections. Your newly created config should be in the "wired" section, close to "auto eth0".

Does this work? If not, tell me and we'll configure it the old-fashioned way. Heck, doing it via the commandline can't be that bad in order to check this works.

---

### Post by kymagic on 2009-02-25
*Slaps self on forehead* Sorry for not posting the files - I did copy them over last time, but I forgot to attatch them :s  . Here they are though now.

**resolv.conf**
```
# Generated by NetworkManager
```

Yes, that's actually it. I've checked this twice. I'm no Linux expert, but I think that might be causing the problem :) Anyhoo, here's the next one:

[b]interfaces[/b[
```
auto loiface lo inet loopback
```



I also created a new connection, which didn't work. Again, it said that my connection was connected, but no internet :(  You didn't mention entering in the MAC address - is this necessary? The settings turned out to be the same as what I was entering when editing Auto eth0 originally. My gateway and DNS server are set to my router's IP (as they are set on the other windows computers on the network).

Thanks again for your continued help.

---

### Post by Miguel on 2009-02-25
Mmm... I don't know if this will have anything to do, but there's a missing return in your /etc/network/interfaces. Mine looks like:
```

auto lo
iface lo inet loopback

```

And is normal for a computer with the network managed by (duh!) Network Manager. By the way, are you sure you want to connect to a router via static IP? Most, if not all the routers I know are set up by default to use DHCP.

---

### Post by kymagic on 2009-02-25
My interfaces file does have the return; Something must have gone wrong with copy pasta via Windows.

With regards to the static IP: I would like a static IP, and my old installation used one. I plan on playing around with server applications (And installing from scratch, hence the dekstop edition). However, I suppose I could live with the minor inconvenience of reconfiguring my router when I want someone on the outside to access the computer. All my other computers (Windows) on the network use static IPs.


I haven't done anything to this installation yet (except curse at the lack of internet), so I'm going to try installing 8.04 and getting the internet on that, and then upgrading back to 8.10. It doesn't take too long, and it might migrate working network settings.

---

### Post by kymagic on 2009-02-28
Right. It took a bit longer then expected because I only had a 7.10 disc handy and my internet connection decided to download at 30KB/s, but I am now running 8.10 with a static IP! Horrah! Thanks for your help in trying to diagnose and solve the problem.

---

