---
title: "Lost my network connection"
date: 2010-10-23
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-10-23
My Mythbuntu (10.04) box has lost its ability to connect to the network. The cables seem to be OK, and my network switch has a little green light where it should do. If I hover my mouse over the network icon in the top right corner of the Ubuntu desktop, it says

"Wired network connection 'Auto eth0' active"

However, there is no connectivity. I can't open web pages, and I can't even ping other devices on my home network.

I believe this started last weekend, possibly after downloading and installing the latest security updates.

Any ideas what could be going on? Is it possible that the updates have set some ludicrously restrictive firewall setting somewhere or something like that? Any log files that might give a clue to what's going on?

All suggestions gratefully received.

---

### Post by LowSky on 2010-10-23
first thing to try is reboot your router

---

### Post by ian dobson on 2010-10-24
Hi,

ifconfig to see how your network card is configured/ip address.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2010-10-24
Thanks for that. I tried rebooting the router (and the network switch, for good measure), but that didn't help. I'd be surprised if it's a problem with the router, as the rest of my network is fine. I have another PC and a couple of backup devices on the network, and the other PC can happily access the backup devices and the internet.

This is what happens when I type ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:5b:9d:32  
          inet addr:172.16.100.20  Bcast:172.16.100.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe5b:9d32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5590 (5.5 KB)  TX bytes:61836 (61.8 KB)
          Interrupt:25 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17241 (17.2 KB)  TX bytes:17241 (17.2 KB)
```

The IP address 172.16.100.20 is set up as the machine's static IP address, so the fact it has an IP address doesn't necessarily mean it's talking to anything else.

---

### Post by NautiusMaximus on 2010-10-24
I should also mention that if I unplug the network cable from the back of the computer, I get a little message telling me that eth0 is now disconnected, and then when I plug it back in I'm told it's connected again. Also, the corresponding light on the network switch goes out when I unplug it and comes back on again when I plug it in.

So I don't think this is a hardware problem. It looks very much like something bad happened after last weekend's software updates, as that's when the problem started.

However, exactly what this bad thing that happened is, I have no idea.

---

### Post by ozybushwalker on 2010-10-24
There are many things that could have gone wrong so I suggest you post the output of the following shell commands.

```

# ping -c 1 a.b.c.d
# ping -c 1 x.y.z
# dig x.y.z
# arp -a

```

where you should replace a.b.c.d by the IP address of your router and replace x.y.z by the name of your router.

Maybe you have a configuration problem, a routing problem, a DNS problem ...

---

### Post by NautiusMaximus on 2010-10-25
Many thanks for the suggestions.

To the best of my knowledge, my router doesn't have a name: I only ever refer to it by its IP address. Is that important?

Anyway, here are the results of the commands you suggested:

```

adam@htpc:~$ ping -c 1 172.16.100.254
PING 172.16.100.254 (172.16.100.254) 56(84) bytes of data.
From 172.16.100.20 icmp_seq=1 Destination Host Unreachable

--- 172.16.100.254 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

adam@htpc:~$ dig 172.16.100.254

; <<>> DiG 9.7.0-P1 <<>> 172.16.100.254
;; global options: +cmd
;; connection timed out; no servers could be reached

 
adam@htpc:~$ arp -a
? (172.16.100.254) at <incomplete> on eth0
adam@htpc:~$ 

```

I should mention that I have a Windows PC on the same network, which can ping the router without any problems. So I'm pretty sure that any problem is with the Mythbuntu box, not with the router.

Any ideas what could be going on?

---

### Post by mymythtv on 2010-10-25
Hi

You wrote that the IP was set static - did you check your other network settings ?
Network, Default gateway, media speed ?
( netstat -r, ethtool eth0, 

Just a guess, but as hw seems ok ( light on, light off )..

Alternatively, try configure eth0 as dhcp and let it pick up settings..

I'm not aware of an update giving network trouble lately ?!?

---

### Post by ozybushwalker on 2010-10-25
Your network port behaves as if it is connected to something that talks back (see the counters in ifconfig output) but is on the wrong subnet (else the router would answer the arp).

Please check it is connected to the correct equipment (maybe the wrong switch or the wrong port in a VLAN capable switch or another computer instead of the switch or ...). If that seems to be OK and you still have the problem I suggest you take a packet trace and post it here. 

# tcpdump -i eth0 -c 20

will display 20 packets sent and received on interface eth0. The IP addresses in those packets might give a clue as to where the interface is connected. 

Oh, and do both ends of the cable see the link as being up and passing traffic? I have seen cases where connector problems have resulted in one end of a link not seeing traffic seemingly sent by the other end.

---

### Post by nickrout on 2010-10-25
172.16 is a fairly uinusual (although not impossible) subnet for a home network to be on.

What is the IP address of your windows machine? And gateway? (start|run|cmd then type in ipconfig /all)

---

### Post by NautiusMaximus on 2010-10-26
Many thanks for your helpful suggestions, everyone. This is a frustrating problem, as I'm sure you can imagine, but I'm confident that with you guys on the case we'll get there in the end.

@mymythtv:

Here is the output from the command you suggested:


```
adam@htpc:~$ netstat -r ethtool eth0
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.16.100.0    *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         172.16.100.254  0.0.0.0         UG        0 0          0 eth0

```

I tried setting eth0 to dhcp, but all that happened is that it was unable to connect. Have now set it back to static.

@ozybushwalker:

I only have the one switch, and it's plugged into the same place it's always been, so I don't see how any problems could have arisen there. Here's the result of the command you suggested:

```
adam@htpc:~$ sudo tcpdump -i eth0 -c 20
[sudo] password for adam: 
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
08:31:55.576786 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:31:56.578028 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:31:59.576787 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:00.576795 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:01.576791 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:05.596784 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:06.596785 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:07.596782 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:10.596787 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:11.596789 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:12.596786 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:15.606782 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:16.606798 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:17.606787 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:20.606786 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:21.606785 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:22.606787 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:25.606788 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:26.606787 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
08:32:27.606787 ARP, Request who-has 172.16.100.254 tell 172.16.100.20, length 28
20 packets captured
23 packets received by filter
0 packets dropped by kernel
```

I'm not entirely sure I've understood what you meant by "both ends of the cable", but there is a light on where the network cable goes into the back of the computer, and there is also a light on where the corresponding cable goes into the network switch. Is that what you meant or did I misunderstand?

@nickrout:

There is a good reason for the unusual IP address. I have a VPN to my office, where internal IP addresses have the more usual form 192.168.xxx.xxx. The IT guy who set the VPN up told me that it was necessary to have my home IP addresses in a different range. My windows PC is 172.16.100.52 (assigned dynamically) and my router is 172.16.100.254.

Talking of the VPN to my office, I should mention that it's currently not working. This may possibly be related, although I think it's more likely to be a coincidence for 3 reasons. First, the problem with my Mythbuntu box occurred first, and the VPN was still working at the time (although has failed since). Second, I don't see why the Mythbuntu box shouldn't at least be able to ping the router, even if there are problems beyond it. Third, I have the DNS server addresses set up to go straight to my ISP's DNS server, rather than  routing through my office, which has in the past led to my Mythbuntu box being perfectly able to connect to the internet during previous VPN failures.

So, are we any further towards figuring out what's going on?

---

### Post by mymythtv on 2010-10-26
hi

Sorry if my last post wasn't clear enough :-)
"netstat -r" and "ethtool eth0" are two commands....

Anyway - I would have guessed of an output from netstat like

> [FONT="Courier New"]root@rafiki:/tmp# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.9     0.0.0.0         UG        0 0          0 eth0
root@rafiki:/tmp# [/FONT]

or - with multiple interfaces/ip

> [FONT="Courier New"]Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
20.45.103.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         20.45.103.1     0.0.0.0         UG        0 0          0 eth0[/FONT]

Don't quite get where the "*" comes from in your gateway?

As Nickrout wrote, your 172.16 not unusual. It's a class B and normally have 255.255.0.0 as netmask ( nothing wrong in 255.255.255.0 ! )

Quick info link: [http://www.rhyshaden.com/ipadd.htm](http://www.rhyshaden.com/ipadd.htm) - somewhat tech stuff.

I don't think it's a hardware problem but more of a configuring issue with your netmask/gateway

Can you post your content from: /etc/network/interfaces
It should look like ( more or less ):

[FONT="Courier New"]> # The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.25
    netmask 255.255.255.0
    network    192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.9[/FONT]

I hope it gets you further..

---

### Post by Spr0k3t on 2010-10-26
My question, is the static IP assigned through DHCP or set up locally on the computer in question?  If it's not assigned through DHCP, I'd consider doing just that and allow the computer system to accept the IP address given.  That may eliminate one of the potential issues you are having.  Also, if you have to boot the computer system with a livecd, this would allow you to keep the assigned IP without having to configure it at all.

---

### Post by ozybushwalker on 2010-10-26
> **NautiusMaximus said:**
> 

I'm not entirely sure I've understood what you meant by "both ends of the cable", but there is a light on where the network cable goes into the back of the computer, and there is also a light on where the corresponding cable goes into the network switch. Is that what you meant or did I misunderstand?

Yes. One of the port lights normally flickers during activity. Based on the tcpdump output you displayed, if you attempt to ping the router I would expect the NIC port light on your computer to flicker briefly and the corresponding port on the switch to flicker briefly with the port light on your computer. Similarly the port light on the switch for the connection to the router and the corresponding port light on the router should flicker in sync with the port lights on the hop between the computer and switch.

The tcpdump should show an arp response from the router. Either the arp request is not getting to the router or the router isn't acting on it (perhaps a firewall rule on the router is discarding arp requests) or the arp response from the router is not getting back to the computer.

Watching the lights might suggest a hop where the arp request might be getting lost.

Have you tried connecting the computer to a different switch port? Have you tried using a different cable between switch and computer or swapping the cable ends (plug the end that used to connect to the switch into the computer and the end that used to connect to the computer into the switch)?

---

### Post by NautiusMaximus on 2010-10-27
mymythtv:

> Sorry if my last post wasn't clear enough 
"netstat -r" and "ethtool eth0" are two commands....

Ah, yes, I should have spotted the comma between them, shouldn't I?

Anyway, here is what it looks like if I run the commands separately:


```
adam@htpc:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.16.100.0    *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         172.16.100.254  0.0.0.0         UG        0 0          0 eth0


adam@htpc:~$ sudo ethtool eth0
[sudo] password for adam: 
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

```

And here is the content of /etc/network/interfaces. Interestingly,it looks nothing like what you said it should look like. 


```
auto lo
iface lo inet loopback

```

That's it. The entire contents. Nothing about eth0 at all. Could we be getting towards the cause of the problem? I should point out, however, that I checked the last modified date on the file, and it wasn't changed in the latest upgrade. It has apparently looked the same since last year sometime (I think it dates from when I installed Mythbuntu 9.10).

---

### Post by NautiusMaximus on 2010-10-27
Spr0k3t:

I've already tried allowing it to pick up an IP address via DCHP. It won't.

ozybushwalker:

Thanks for the suggestion re cables. Must dash off to work now, but will try that this evening unless there is a consensus that the problem is caused by my /etc/network/interfaces file.

---

### Post by mymythtv on 2010-10-27
Are you running 1000Mb/s on your local network ??

mii-tools says "Speed: 1000Mb/s" ?!
If your router only is running 100Mb/s then it could explain something...

What kind of router do you have (name & model)?
If it's a gigabit router then it's ok.

I wonder why you don't see anything in /etc/network/interfaces ?!?

You might have wrote it before, but you are running Myhtbuntu (10.04) ??

How did you define your ip-adress ( commandline, gui ? )

---

### Post by NautiusMaximus on 2010-10-28
Yes, my local network is indeed gigabit. I have a Netgear Prosafe GS116 as my network switch.

Yes, I am running Mythbuntu 10.04.

I set up the static ip address with a gui. I reached this gui by right clicking on the little network icon in the top right of the Ubuntu desktop and selecting "edit network connection" (or something like that).

All this worked in the past, but doesn't work any more. The only thing I think I changed to get from working to not working was installing the regular security updates via the update manager.

---

### Post by mymythtv on 2010-10-28
Weird

Right - it's called "Edit connection"
I'm at my laptop right now, running DHCP, but a guess on what it should look like could be:
```
[FONT="Courier New"]Wired -
  MAC address: <my mac>
  MTU: automatic

802.1x Security -
 <untagged>  

IPv4 Settings -
  Method: Manual
    -Addresses
     172.16.1.20 - 255.255.255.0 - 172.16.1.254
  DNS servers: <dns ip>
  Search domains: <search domainname>

IPv6 Settings:
  Method: Ignore[/FONT]
```

"Available to all users" tagged.

---

### Post by NautiusMaximus on 2010-10-29
Well, that depends on what you mean by "what it should look like".

The way it's laid out on screen looks nothing like that: it's all done through a GUI, whereas what you have looks much more text-based.

However, the information is very similar. The only thing that doesn't match what you had is that "Search domains" is blank. Other than that, all the settings, while not laid out the way you have them, have the same content.

---

### Post by mymythtv on 2010-10-29
yeah - sorry for the layout, but I thought that's the easy way of showing the content from the gui without "copy & paste"



I noticed that your "netstat -r" looked like:

```
adam@htpc:~$ netstat -r ethtool eth0
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.16.100.0    *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         172.16.100.254  0.0.0.0         UG        0 0          0 eth0
```

I noticed your "link-local" on eth0 along with the 172.16.100.0 address - are you using local-link/ZeroConfNetworking ?
[https://wiki.ubuntu.com/ZeroConfNetworking](https://wiki.ubuntu.com/ZeroConfNetworking)
[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

The "search domain" is used when you do a "nslookup", so don't think of that right now

---

### Post by NautiusMaximus on 2010-10-30
To the best of my knowledge, I'm not using ZeroConfNetworking. From the look of those links, I would have to have set it up to do so deliberately, right? Since I'd never heard of it before, I assume I'm not using it (unless I've misunderstood and it is used by default).

I've just tried a couple more things that may shed some light on it.

First, I've ruled out any network hardware problems by connecting another device to the cable that goes into the back of my Mythbuntu box, while the cable was plugged in where it normally is. It got a connection just fine.

Second, I appear to have ruled out any problems with my particular Mythbuntu setup by booting to a live CD version (9.10, but I don't suppose the version makes any difference). That should just connect to the network by default, right? It didn't.

So, if it's not a hardware problem, and it's not a software problem, the only thing I can think of is that there is some subtle problem with my network router. A bit odd, because it is happy to let other things connect. But maybe there is something that has changed in its configuration that means it sees the Mythbuntu box as a threat and won't allow it to connect.

Does that sound possible? Is there anything else that could be going wrong that I'm overlooking?

---

### Post by nickrout on 2010-10-30
what is your network hardware?

what driver is it using?

---

### Post by NautiusMaximus on 2010-10-31
The Mythbuntu box connects to the network through the network socket built into the motherboard, which is Gigabyte GA-M78SM-S2H.

I have no idea what driver it uses: until now, it has always "just worked" out of the box, with Mythbuntu recognising it automatically. Bear in mind that I had the same problem when booting to a live CD version of Mythbuntu.

Beyond the Mythbuntu box, the network switch is a Netgear Prosafe GS116, and that then connects to a Juniper NS5GT firewall & router. On the other side of the Juniper box, there is an ADSL router connecting it all to the outside world.

---

### Post by nickrout on 2010-10-31
lspci for a list of pci devices, including the network card.

lsmod gives a list of modules, including your network driver.

---

### Post by NautiusMaximus on 2010-10-31
```
adam@htpc:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:06.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:06.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2)


adam@htpc:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
vfat                   10866  1 
fat                    55350  1 vfat
nls_cp437               6351  1 
cifs                  279302  0 
snd_hda_codec_nvhdmi     4760  1 
snd_hda_codec_realtek   279040  1 
snd_hda_intel          25773  1 
snd_hda_codec          85759  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
dvb_usb_dib0700        71047  17 
dib7000p               18348  3 dvb_usb_dib0700
dib7000m               15907  1 dvb_usb_dib0700
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
fbcon                  39270  71 
tileblit                2487  1 fbcon
dib0070                 8549  3 dvb_usb_dib0700
dvb_usb                16709  1 dvb_usb_dib0700
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
xfs                   542450  1 
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
exportfs                4202  1 xfs
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dib3000mc              12997  1 dvb_usb_dib0700
dib8000                26879  1 dvb_usb_dib0700
dibx000_common          3570  4 dib7000p,dib7000m,dib3000mc,dib8000
softcursor              1565  1 bitblit
nvidia              10832442  30 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
dvb_core              103025  3 dib7000p,dvb_usb,dib8000
joydev                 11072  0 
ppdev                   6375  0 
video                  20623  0 
snd                    71187  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             29958  1 
lirc_imon              26413  0 
lirc_dev               11302  1 lirc_imon
output                  2503  1 video
serio_raw               4918  0 
shpchp                 33711  0 
edac_core              45423  0 
edac_mce_amd            9278  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_nforce2             6099  0 
it87                   24460  0 
hwmon_vid               3130  1 it87
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41084  0 
hid                    83472  1 usbhid
usb_storage            49961  1 
pata_amd               11962  0 
ahci                   37870  3 
forcedeth              55624  0 

```

We are now well beyond the limits of my competence in fiddling around with Linux computers. All of the above means nothing to me. But perhaps they contain some valuable clues to some of you experts?

---

### Post by nickrout on 2010-11-01
well i assume you can read this line from lspci:

```
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)

```

The driver is trickier, but I think it is the forcedeth one (the first in the list - well printed as the last, but thats because they are listed in the reverse order to what they were inserted in the kernel)

So you need to be googling for problems with the forcedeth driver and the nvidia mcp77 ethernet device.

---

### Post by NautiusMaximus on 2010-11-01
While it's entirely possible that some latest security fixes could have messed with the driver and caused the problems, presumably those same problems would not have been present when I booted to the live CD?

When I booted to the live CD, I also failed to get any kind of network connection. Wouldn't the live CD have come with its own drivers? That was a previous version of Mythbuntu (9.10) which never gave me any problems with network connectivity.

Doesn't the failure to connect to the network from the live CD rule out any problems with drivers or the like, and make some configuration problem with the firewall the chief suspect?

---

### Post by NautiusMaximus on 2010-11-01
Or possibly a weird hardware failure? Although the computer seems to be aware of whether a cable is plugged into the network port or not, so presumably the network port has some functionality, is it possible that it's somehow not able to communicate properly?

---

### Post by nickrout on 2010-11-01
> **NautiusMaximus said:**
> While it's entirely possible that some latest security fixes could have messed with the driver and caused the problems, presumably those same problems would not have been present when I booted to the live CD?

When I booted to the live CD, I also failed to get any kind of network connection. Wouldn't the live CD have come with its own drivers? That was a previous version of Mythbuntu (9.10) which never gave me any problems with network connectivity.

Doesn't the failure to connect to the network from the live CD rule out any problems with drivers or the like, and make some configuration problem with the firewall the chief suspect?


The livecd comes with the same drivers as it then installs to hard drive.

If 9.10 works for you, use it. If you want a later version of mythtv use autobuilds.

---

### Post by mymythtv on 2010-11-02
If I read correct, then:

> When I booted to the live CD, I also failed to get any kind of network connection. Wouldn't the live CD have come with its own drivers? **That was a previous version of Mythbuntu (9.10) which never gave me any problems with network connectivity**.

Not sure it's the same hardware, but it seems that even an previous working 9.10 cd isn't enough to bring live to the network - and that it has worked before...

---

### Post by NautiusMaximus on 2010-11-02
Yes, it's the same hardware. It's beginning to look like there must be some weird fault with the network connection on my motherboard. I really can't think what else could possibly explain it.

To be clear, booting to the live CD of Mythbuntu 9.10 also results in a failure to connect to the network. In the past, I was able to connect to the network with 9.10, but I can't now.

I have a spare network card. When I get a few spare moments (probably at the weekend) I shall try installing it and seeing what else happens.

BTW, I've just ruled out any problem with the network switch, by plugging the Mythbuntu box directly into my firewall/router. Same symptoms: I'm told there is a network connection, but I can't ping the router.

---

### Post by nickrout on 2010-11-02
I strongly recommend that you turn on dhcp on your router and allow the new network card to get all it's parameters via dhcp. It will eliminate a lot of operator error!

---

### Post by Meph1st0 on 2010-11-02
On my router there is something called Static DHCP which allows me to set an IP address that the router will always issue out to a specific computer given it's MAC address.  If you want the benefits of having a static IP address but the configuration simplicity of DHCP then I suggest looking to see if your router supports that feature.

---

### Post by NautiusMaximus on 2010-11-06
Hurrah! I've finally solved it. It was indeed a hardware problem. I have fitted a spare network card to the computer, and now everything works just fine.

What initially threw me was that the computer would say "eth0 now connected" or "eth0 now disconnected" when the network cable was either plugged in or unplugged, so I assumed that the network hardware must be working.

Seems that was wrong. Clearly it is possible for the network hardware to be working to the point where the computer knows that something is plugged in, despite not actually working.

Anyway, I got there in the end. Thanks ever so much to all of you who helped me with troubleshooting.

---

### Post by nickrout on 2010-11-06
Either that or you configured one different to the other?

---

