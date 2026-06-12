---
title: "delete and re-add network connection"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by stevebond001 on 2013-03-18
Hi
I have discovered a very specific problem with my Ubuntu (12.10) PC.  Whilst using ethernet, when I connect to a SMB share I can copy files _**to**_ the share, but when copying **_from_** the share the copy process stops at random times (sometimes straight away - sometimes after a few seconds).

I have systematically tried to remove and change different parts of the network to fix this:
1. tried copying from a Windows PC instead - works OK
2. tried copying from my Ubuntu PC over wireless - works OK
3. replaced the switch between Ubuntu PC and SMB share - still fails to copy over ethernet
4. replaced ethernet lead - still fails to copy over ethernet
5. Run a windows Virtual machine on Ubuntu PC - copy from SMB to VM works OK.
6. Run a Linux (Mint) Virtual machine on Ubuntu PC - fails to copy over ethernet

My only conclusion from the above is that the configuration on the network card is screwed up somehow.  I have tried taking the network card down and up (ifdown & ifup) but this makes no difference.  

So my next plan is to deinstall the network adapter from my PC and reinstall it.  This is an easy process in Windows (device manager/delete the network adapter and driver /  rescan and install the adapter and driver again).  But I have absolutely no idea how to do this in Linux.

So can anyone provide the necessary commands to let me do this?  I really don't want to have to totally rebuild my PC (last resort) as I have it just the way I want, with all the applications I want.
So any assistance would be appreciated.

Thanks in advance

---

### Post by steeldriver on 2013-03-18
Well I guess the equivalent would be to use modprobe (or rmmod / insmod) to remove and reinstall the driver kernel module - however it won't really change or update anything, it's essentially no different from rebooting

It might be better to try to diagnose the issue - do you see any ethernet interface error messages in dmesg?

```
dmesg | grep eth[0-9]
```

Maybe if you post the card / driver info someone will be able to advise if there are any known issues / updates

```
sudo lshw -C network
```

---

### Post by varunendra on 2013-03-18
> **stevebond001 said:**
> So my next plan is to deinstall the network adapter from my PC and reinstall it.  This is an easy process in Windows (device manager/delete the network adapter and driver /  rescan and install the adapter and driver again).  But I have absolutely no idea how to do this in Linux.

It does nothing more than reassigning drivers with default settings, so in essence, it is just like unloading/loading driver in Linux, like steeldriver pointed out.

Apart from what he asked for, please also post outputs of -
```
ifconfig
nm-tool

```

---

### Post by stevebond001 on 2013-03-18
Thanks for the help.
I have been trying a few additional things which may or may not help.
I have booted from a Linux Mint 13 live CD and tried copying the files from the SMB share.  This worked.
I then booted from a Ubuntu 12.04 live CD and tried copying the files from the SMB share.  This also worked.

I then tried booting from a Ubuntu 12.10 live CD and copying the files from the SMB share.  This did not work (same symptoms as before).  So I guess that ther eis either a bug in the 12.10 build, or my live CD is corrupt (this is the CD I originally installed from).  SO I think I'll try and download another ISO and burn it again; then try and boot from it and copy.  I know it's a slim chance but it's worth trying.  If that doesn't work then I think I'll have to wait until 13.04 gets released and try that build.  However, if this doesn't work I think I'll need to move over to Mint.

Regarding the output requested, please find it as follows:  Not sure if it will help though, but thanks for trying to help with this.

***_dmesg | grep eth[0-9]_***
```
[    1.018779] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:19:66:d4:01:61
[   11.748620] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.090706] forcedeth 0000:00:0a.0: eth0: MSI enabled
[   16.099742] bridge-eth0: up
[   16.121194] bridge-eth0: attached
```


***_sudo lshw -C network_***
```
PCI (sysfs)  

  *-network               
       description: Wireless interface
       product: AR5212/AR5213 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: wlan0
       version: 01
       serial: 00:14:78:72:ba:24
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.5.0-25-generic firmware=N/A ip=192.168.0.7 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fcff0000-fcffffff
  *-network
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:19:66:d4:01:61
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.2 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 memory:fce7c000-fce7cfff ioport:c880(size=8) memory:fce7e400-fce7e4ff memory:fce7e000-fce7e00f
```


***_ifconfig_***
```
eth0      Link encap:Ethernet  HWaddr 00:19:66:d4:01:61  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fed4:161/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19932409 (19.9 MB)  TX bytes:2531341 (2.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:269676 (269.6 KB)  TX bytes:269676 (269.6 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.35.1  Bcast:192.168.35.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.231.1  Bcast:172.16.231.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:78:72:ba:24  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe72:ba24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162200 (162.2 KB)  TX bytes:62832 (62.8 KB)
```


***_nm-tool_***
```
State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:19:66:D4:01:61

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0  [WLAN] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           no
  HW Address:        00:14:78:72:BA:24

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    WLAN:            Infra, 80:3F:5D:9A:0D:CA, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    *WLAN:           Infra, 7C:4C:A5:22:6B:29, Freq 2437 MHz, Rate 54 Mb/s, Strength 43 WPA2

  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
```

---

### Post by varunendra on 2013-03-18
I see nothing wrong in the above outputs. Maybe the full dmesg log can shed some light if it is indeed driver related. If not, then I suspect it may not be driver kernel related at all, but perhaps how samba packages work.

If you download the iso again, I'd suggest to download via torrent to ensure integrity : [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

---

### Post by steeldriver on 2013-03-18
Does eth0 always get the IP address 192.168.0.2? do you use DHCP for everything or is it possible there's an IP address conflict on your network?

Just throwing ideas our here...

---

### Post by stevebond001 on 2013-03-19
> **steeldriver said:**
> Does eth0 always get the IP address 192.168.0.2? do you use DHCP for everything or is it possible there's an IP address conflict on your network?

Just throwing ideas our here...

eth0 always gets .2 via DHCP, as it's reserved for the MAC address of the PC.  I have tried the copy process with static IP addresses as well as .2 with the same results.

I'll get back to you when I have tried the newly downloaded ISO.

Thanks

---

### Post by stevebond001 on 2013-03-19
Right
Just tried a fresh download of the 12.10 ISO.  And guess what?  It still didn't work :(

I get the impression that there is a bug of some sort concerning the NIC on my PC, as that is the only thing which hasn't changed in this process.

The only thing I can think of now is to wait until 13.4 gets released, and try that.  If it still fails then I'll need to look for another distro which works.

Thanks to all who helped, much appreciated.

---

### Post by stevebond001 on 2013-03-19
So, here's where I've got to:

1. To recap I have problems copying relatively small files (photos, ebooks, etc) from a SMB share to my local (sata) Linux disk.  I can successfully copy large (iso) files OK.
2. I can copy the small files from the SMB share to an externally mounted drive.
3.  I have reset the BIOS and ensured it is up to date.
4. I have rebooted using a live CD (various Ubuntu / Mint distros) and have the same symptoms as above.
5. I have removed all peripherals, PCI cards, DVD drives, memory cards, etc, from my PC - same symptoms.
5. I have replaced the sata lead for my hard drive - same symptoms.
6. I have disconnected my hard drive, booted with a live CD, and copied the files onto the liveCD desktop (in effect into RAM) - same symptoms.
7. I have tried using a wireless network card instead of ethernet - success!
8. I have replaced my ethernet NIC with another card - same symptoms as above :( .
9. I have copied from a SMB share on another computer - same symptoms.
10. I have changed switches between the linux PC and the SMB share - same symptoms.
11. I don't have any of the above problems when copying from the SMB share from within a Windows 7 Virtual Machine on the same PC (running in VMWare).

The only thing I can think of that's left is if there is a setting on the NIC which is interfering with the copying of the files.  I'm assuming that the card is set to auto-negotiate its speed with the switch.  Is there any way to manually set the connection speed so I can try 100 Full Duplex, half duplex, etc?  I can do this in windows world but I don't know where to set this on my Linux box.


If anybody has any idea how to set this, or any suggestions of what else to test over and above the things I've already tried, I would be extremely grateful.  This issue is driving me mad at the moment so I'm looking for any assistance that is offered.

Thanks very much in advance

---

### Post by varunendra on 2013-03-19
> **stevebond001 said:**
> 
8. I have replaced my ethernet NIC with another card - same symptoms as above :(
What was the card (the chip it was using) and which driver it was using?

> Is there any way to manually set the connection speed so I can try 100 Full Duplex, half duplex, etc?  I can do this in windows world but I don't know where to set this on my Linux box.
**mii-tool**
See **man mii-tool** for usage details. A few examples -

To disable autonegotiation and force speed to 100 Mbit/s Full Duplex on eth0 -
```
sudo mii-tool -F 100baseTx-FD eth0
```

To restart autonegotiation -
```
sudo mii-tool -r eth0
```

To reset all mii-tool configurations to default -
```
sudo mii-tool -R eth0
```

You may also try disabling IPv6 and setting MTU to 1492 in Network Manager, which is default value for MTU in Windows.

There are also some driver parameters for the forcedeth driver, but since changing card made no difference, I think it may not be driver related (assuming the other card used a different driver).

---

### Post by stevebond001 on 2013-03-20
Thanks very much for the assistance.

I have set the IPV6 setting to "ignore" from within the network manager gui, so I'm assuming that this is now disabled.
I have changed the MTU as suggested.
Both of these suggestions made no difference.

My original NIC (onboard) is as follows (output from *lspci | grep Ethernet*):
***> 00:0a.0 Ethernet controller: NVIDIA Corporation MCP77 Ethernet (rev a2)***

My second NIC (PCI card) has now been removed, but it is a 3Com chip on the card so I'm assuming that it uses a different driver to the onboard NIC.


I have installed and run mii-tool, but get an error as follows:
***> SIOCGMIIPHY on 'eth0' failed: Operation not supported***

Additional information from ethtool:
[B][I]> Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 3
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes[/I][/B]

So I don't know why I can't change the speed / duplex of the NIC using mii-tool.

Really stumped now :(

---

### Post by varunendra on 2013-03-20
> **stevebond001 said:**
> > SIOCGMIIPHY on 'eth0' failed: Operation not supported
So I don't know why I can't change the speed / duplex of the NIC using mii-tool.
From **man mii-tool** :
> SIOCGMIIPHY on 'eth?' failed: Operation not supported
              The interface in question does not  support  MII  queries.  Most
              likely, it does not have MII transceivers, at all.

Just for reference, ethtool eth0 output for my Atheros AR8151 chip (disconnected), which does support mii queries :
```
Settings for eth0:
	Supported ports: [**[COLOR="#000080"] TP [/COLOR]**]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: **[COLOR="#000080"]Twisted Pair[/COLOR]**
	PHYAD: 0
	Transceiver: **[COLOR="#000080"]internal[/COLOR]**
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x0000003f (63)
			       drv probe link timer ifdown ifup
	Link detected: no
```
So there are some differences than yours, although not sure if they matter.
Basically, I'm stumped too.. :(

---

### Post by stevebond001 on 2013-03-21
I've also tried the same process with OpenSUSE as well.  Same result.  :confused:

I'm not sure of the forum rules - Now I know (or think I know) it's something to do with the guts of the network connection, can I create another thread with the correct title and specific problem?  I know that it's sort of a repeat of this thread, but maybe someone will see the (amended) thread title and respond.  But I don't want to break any rules on posting.

---

### Post by varunendra on 2013-03-21
> **stevebond001 said:**
> I've also tried the same process with OpenSUSE as well.  Same result.  :confused:

I'm not sure of the forum rules - Now I know (or think I know) it's something to do with the guts of the network connection, can I create another thread with the correct title and specific problem?  I know that it's sort of a repeat of this thread, but maybe someone will see the (amended) thread title and respond.  But I don't want to break any rules on posting.

Rules are meant to enhance the help people can get here. They are not so rigid. If you think the question deserves a different thread, go ahead. I'd suggest to post a link to this thread (in fact one of these last posts to be more precise) with one or two lines of justification why you needed a different thread. I'm sure anyone interested enough will understand.

Sorry I couldn't be of more help on this, and hope you will be able to get answers from someone more experienced with these issues.

Good luck! :)

---

