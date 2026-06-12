---
title: "Wireless through command line"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by cvp on 2009-04-29
Long story short, I want to learn a bit more about networking stuff from the command line, and I'm trying to connect to my school's unencrypted wireless network in the library. I can do this easily with a graphical tool (that's how I'm on here now); there is nothing special that I'm aware of about this wireless network.

So...

**lshw -C network**
```
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:4d:e5:3b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=172.22.36.92 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
```

**iwlist wlan0 scan**
```
wlan0     Scan completed :
          Cell 01 - Address: 00:0C:85:14:5D:A7
                    ESSID:"LTC-1220-01"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=95/100  Signal level:-33 dBm  Noise level=-87 dBm
                    Encryption key:off
                    IE: Unknown: 000B4C54432D313232302D3031
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 851E000084001F00FF0019004C54432D313232302D303100000000000F000007
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101890002850000238500004264BC0062736600
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000040d9774d7
                    Extra: Last beacon: 316ms ago
          Cell 02 - Address: 00:0C:85:0C:70:79
                    ESSID:"LTC-1220-02"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/100  Signal level:-82 dBm  Noise level=-87 dBm
                    Encryption key:off
                    IE: Unknown: 000B4C54432D313232302D3032
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 851E000084001F00FF0019004C54432D313232302D30320000000000A3000007
                    IE: Unknown: 9606004096001400
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101890002850000238500004264BC0062736600
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000058423d001d9
                    Extra: Last beacon: 3748ms ago
          Cell 03 - Address: 00:0C:30:5B:B1:BB
                    ESSID:"LTC-1220-01"
                    Mode:Master
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=60/100  Signal level:-55 dBm  Noise level=-79 dBm
                    Encryption key:off
                    IE: Unknown: 000B4C54432D313232302D3031
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 851E000084001F00FF0019004C54432D313232302D3031000000000002000023
                    IE: Unknown: 9606004096001000
                    IE: Unknown: DD06004096010100
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F20201018900028500002385000042645E0062732F00
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000040d79c051
                    Extra: Last beacon: 2372ms ago
```
The thing to note here is that there are two networks here: -01 is on floor 1, -02 is on floor 2. knetworkmanager only offers me -01 for whatever reason.

When I'm connected via knetworkmanager to LTC-1220-01,
**iwconfig wlan0**
```
wlan0     IEEE 802.11abg  ESSID:"LTC-1220-01"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:85:14:5D:A7   
          Bit Rate=11 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=81/100  Signal level:-53 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

So this is the one I'll be trying to connect to, since knetwork manager appears to do it just fine. I disconnect, close knetworkmanager (kill the process), and do the following:
```
root@strife:~# ifconfig wlan0 down
root@strife:~# ifconfig wlan0 up
root@strife:~# iwconfig wlan0 essid "LTC-1220-01"
root@strife:~# iwconfig wlan0 channel 6
root@strife:~# iwconfig wlan0 mode Managed
root@strife:~# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:4d:e5:3b
Sending on   LPF/wlan0/00:1f:3c:4d:e5:3b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
resolvconf: Error: /etc/resolv.conf must be a symlink
```

Heck, I can even toss in a "**iwconfig wlan0 ap 00:0C:85:14:5D:A7**" and it'll still give me the same series of messages about DHCPDISCOVER (albeit with different intervals).
And then I can pull up knetworkmanager and have it connect within a second and a half to the same network. Same **iwconfig wlan0** results as above.

I've also tried this with the other LTC-1220-01 network that's associated with channel 36 (frequency 5.18 GHz), and the same thing happens. Tried it with -02 for shits and giggles with the same results.

So knetworkmanager is doing *something* that I'm not doing. Encryption is off as you can see, and I never need to give knetworkmanager any kind of password or treat the network in any special way; it just works.

Gah.

Please let me know if you have any ideas.
Thanks!!
-cvp

---

### Post by chili555 on 2009-04-29
Is the result the same if you do:```
sudo /etc/init.d/NetworkManager stop
```

---

### Post by Ayuthia on 2009-04-29
Did you make sure that all the NetworkManager processes have been killed:
```
ps -ef|grep Network
```

chili555's method should get rid of the NetworkManager processes.

---

### Post by cvp on 2009-04-29
Ooh, almost. Does this mean we're getting closer?

```
root@strife:~# /etc/init.d/NetworkManager stop
 * Stopping network connection manager NetworkManager                                                           [ OK ] 
root@strife:~# ps -ef | grep Network
root      3013     1  0 13:13 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      8416  8378  0 15:05 pts/1    00:00:00 grep Network
root@strife:~# kill 3013
root@strife:~# ps -ef | grep Network
root      8418  8378  0 15:05 pts/1    00:00:00 grep Network
root@strife:~# ifconfig wlan0 down
root@strife:~# ifconfig wlan0 up
root@strife:~# iwconfig wlan0 essid "LTC-1220-01"
root@strife:~# iwconfig wlan0 mode Managed
root@strife:~# iwconfig wlan0 channel 6
root@strife:~# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6532
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3c:4d:e5:3b
Sending on   LPF/wlan0/00:1f:3c:4d:e5:3b
Sending on   Socket/fallback
DHCPREQUEST of 172.22.36.92 on wlan0 to 255.255.255.255 port 67
DHCPACK of 172.22.36.92 from 172.22.36.254
resolvconf: Error: /etc/resolv.conf must be a symlink
bound to 172.22.36.92 -- renewal in 5800 seconds.
root@strife:~# ping google.com
ping: unknown host google.com
root@strife:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:4d:e5:3b  
          inet addr:172.22.36.92  Bcast:172.22.36.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe4d:e53b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14781792 (14.7 MB)  TX bytes:4231867 (4.2 MB)

```

I have an IP, but I still can't talk to the outside world.
Am I also supposed to configure / detect gateway or DNS server information?

Thanks!
-cvp

---

### Post by cvp on 2009-04-29
Well, it's a DNS thing. I tried pinging my home desktop by giving the IP, and it worked.

When knetworkmanager is connected, my resolv.conf has entries in it preceded by the comment "generated by NetworkManager". But whenever I stop the NetworkManager service, the file becomes empty. For the time being, I've made a copy that I'll overwrite the empty resolv.conf with, but is there a way to get the DNS information from the wireless network? knetworkmanager did it, so there's clearly away...

Hey, thanks again, you guys. This is awesome.
-cvp

---

### Post by chili555 on 2009-04-29
Radical Ubuntu-geek solution number 1: remove Network Manager entirely and stop fighting with it for control of ***your*** computer.

Not-so-radical solution number 2: Edit /etc/dhcp3/dhclient.conf to make sure this part appears:```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, [COLOR="Red"]domain-name-servers[/COLOR], domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
```Really not rad at all solution: add this to your list of commands:```
echo "nameserver 172.22.36.254" | sudo tee /etc/resolv.conf
```172.x is the address of the gateway, that is, router or other access point.

Please post back so the searchers will find out what worked...or not.

---

### Post by cvp on 2009-04-29
1) Not gonna delete NetworkManager. :p
Maybe if I sell all of my possessions except my laptop and become a crazy old wireless-thieving hermit.

2) "domain-name-servers" is already in there.
In fact, I even tried this OpenDNS thing I found online that asked me to put a "prepend" statement with a handful of IP's. And it's turning out that the resolv.conf file is only being overwritten every now and again.

Unfortunately, unless you or someone else here knows how to fetch DNS information automatically from a network, I'll probably have to end up going with a #3 approach.

Thanks again! I really appreciate your help.

-cvp

---

### Post by chili555 on 2009-04-29
> Maybe if I sell all of my possessions except my laptop and become a crazy old wireless-thieving hermit.Hey, that's me! Except I kept two laptops. Oh, and my carbon-fiber road bicycle...oh, and an excellent Nikon DSLR. I *do* have the requisite white beard and jeans with a hole in the caboose.> unless you or someone else here knows how to fetch DNS information automatically from a network,I don't know how as long as Network Mangler is fighting for world domination of all computers. You already know how to do everything NM does: scan for networks and attach to the one you want. The only place I might give NM the prize is simplifying WPA, although dozens here complain: "I put my passphrase in and the little thingy spins and spins and never connects."

---

### Post by christer_f on 2010-03-21
Thanks guys!
I had a very similar problem and suspected that NetworkManager kept getting in the way for iwconfig. Stopping the NetworkManager (with sudo /etc/init.d/network-manager stop in my case) before configuring the connection with iwconfig then dhclient did the magic.

---

