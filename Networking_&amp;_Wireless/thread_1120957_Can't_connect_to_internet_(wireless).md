---
title: "Can't connect to internet (wireless)"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Gollum999 on 2009-04-09
Hey, I've got a bit of a problem.

Ubuntu will not connect to the internet.

I've checked google, but nothing seems to help.

Now let me elaborate:
I've got my laptop set up to multi-boot Vista, Ubuntu, and Windows 7 Beta.  Internet connects flawlessly on Windows, but Ubuntu can't connect.

My router isn't listed in the list of connections, but that makes sense, since it is normally hidden.  So if I enter my information manually, it will just sit there for about a minute, then ask me to re-input my WEP code, and continue this cycle a few times before disconnecting.

Could it be a driver thing?  Or something else, perhaps?

I'm pretty new to Ubuntu, so maybe there's just something I'm missing...

Thanks for any help. :)

---

### Post by StuartN on 2009-04-09
In Ubuntu 8.10 there is a new menu item on the wireless manager to "Connect to hidden wireless network". In earlier versions you might manage to use the "Create new wireless network" option - the network manager is supposed to connect if you type in the SSID.

Neither worked for me, but switching on the SSID broadcast on the router allows connection. Then switch it back to hidden and network manager still connects. In 8.10 though it seems a hidden network will not work using WPA but will with WEP.

---

### Post by Michael.Godawski on 2009-04-09
hi Gollum999,

yep wireless can be a challenge. Have you tried to Connect to Hidden Wireless Network as StuartN suggested?

For a deeper insight into your network status please open up the terminal and post the outputs of these terminal commands here:

```
iwconfig
sudo iwlist scan
sudo lshw -C network
cat /etc/network/interfaces
```

---

### Post by Gollum999 on 2009-04-09
Wow, thanks for the fast response.  Most other forums take days before someone tries to help.

I tried using Connect to Hidden Wireless Network, but it does the same thing.  I haven't tried broadcasting the SSID yet, I'll see if I can try that in a bit.

I tried those console commands:

"iwconfig" returned:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.
```

-----

"sudo iwlist scan" returned:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:22:A4:1F:CE:69
                    ESSID:""
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:5/5  Signal level:-47 dBm  Noise level:-24 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:0F:66:47:CB:E0
                    ESSID:"linksysRPL"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-19 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:22:A4:1F:CE:69
                    ESSID:" "
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:5/5  Signal level:-48 dBm  Noise level:-24 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:21:29:92:54:8F
                    ESSID:"Lawler"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-84 dBm  Noise level:-19 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 05 - Address: 00:18:39:58:D0:BB
                    ESSID:"linksys"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-87 dBm  Noise level:2 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 00:22:A4:81:39:69
                    ESSID:"2WIRE009"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

pan0      Interface doesn't support scanning.

```
-----

"sudo lshw -C network" returned:

```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:d3:ff:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:07:d0:00
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:09:2c:3f:7f:27
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

-----

and "cat /etc/network/interfaces" returned:

```
auto lo
iface lo inet loopback
```

-----

So.... now what?

---

### Post by superprash2003 on 2009-04-10
dont you see a list of networks when you click on the network symbol ( two computer monitors ) at the top bar to the right? .. and when you select WEP.. try various combinations for the 64bit,128 bit etc..

---

### Post by Gollum999 on 2009-04-17
Okay, I got it working.  I turned on SSID broadcast, and Ubuntu connected almost immediately. :p

Thanks for the help, guys!

Now I'm just wondering... am I going to have to leave SSID broadcast on?  I mean, I turned it back off, and it stayed connected, but if I restart the computer will it lose the connection again?

---

