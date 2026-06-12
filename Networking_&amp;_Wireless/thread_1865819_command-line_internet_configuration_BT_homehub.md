---
title: "command-line internet configuration BT homehub"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by MG&amp;TL on 2011-10-20
Hello forum-ers. :D

I'm using a Debian no-desktop install (hey, I would be using Ubuntu server, but the installer wouldn't run...let's not go there- Debian's on my pc now.)

I have:

-a wireless usb adapter (TL-WN321G, white stick thing)

-BT home hub 2.0 with WPA2 security.

And I'd like to connect. I have the drivers (I think, I can run an iwlist scan and put wlan0 *up* )for the adapter, and I think I have configured iwconfig right:

ESSID: BTHomeHub2-KTQ2
key: XXXXXXXX

with:

```
iwconfig wlan0 essid "BTHomeHub-KTQ2" key XXXXXXXX
```
 where the ESSID's the ESSID and the key's hashed out.

Now, my problem is, when I run:
```

 dhclient wlan0
```

....absolutely nothing happens. As in, no terminal messages, not return value, not return at all (nothing happens, but it doesn't stop) and a Ctrl-C or SIGTERM kill simply returns it to the command prompt. And my network isn't already up, I can't ping anything.

I have tried dhcpcd, but I have absolutely no idea what it does, and nothing happens (akin to dhclient), apart from it pulling wlan0 down when I kill it.

Can anybody tell me what I'm doing wrong? I'm trying to setup various forms of server (ssh, telnet, ftp, LAMP) as an experiment, and obviously I need to be connected to web to access the stuff from client machine (laptop, happily running the latest and greatest ubuntu). Oh, and currently I'm downloading debian packages from the debian site manually (on my laptop, then transferring) , and resolving dependencies is a bit of a nightmare. I'd like apt working.

I can provide script results and things, but I didn't think it necessary thus far. 

Once I have connected, do I need to keep dhclient-ing (or add it to startup file) or will it auto-connect?

Running a desktop environment, every distro I have tried on it so far has connected perfectly. My bad, methinks.

---

### Post by chili555 on 2011-10-20
> iwconfig wlan0 essid "BTHomeHub-KTQ2" key XXXXXXXXSpecifying the key in iwconfig is only valid for WEP. You have WPA2. I suspect that dhclient is, indeed working away in the background and not, of course, getting an IP address.

If you are setting up a server, I'd suggest a static IP address so you can ssh into it later. The usual method is to set up /etc/network/interfaces something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
wpa-essid myrouter
wpa-psk xxxxx

```Be sure to use an IP address outside the DHCP range used in the router. Be sure to set up DNS nameservers in /etc/resolv.conf, for instance:```
nameserver 8.8.8.8
nameserver 68.94.156.1
nameserver 205.152.37.23
```After that, simply do:```
sudo ifdown wlan0 && sudo ifup wlan0
ping -c3 www.google.com
```Upon reboot, you should be automagically connected.

---

### Post by MG&amp;TL on 2011-10-20
Sorry; I'm quite new to this; I get most of what you're saying, but I don't get where you get the numbers and/or IP adresses from.

I'll go and get iwlist scan, if and iwconfig from the server to be.

Thanks a lot; I didn't think anyone would provide such a detailed answer.

---

### Post by MG&amp;TL on 2011-10-20
Hi again:

```
$ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1792 (1.7 KiB)  TX bytes:1792 (1.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 94:0c:6d:e3:98:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
$iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=4 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
```

```
$iwlist scan
#other people's internet routers and things here
wlan0     Scan completed :
          Cell 01 - Address: 00:25:56:0A:35:4A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-KQT2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007acd1c8af
                    Extra: Last beacon: 115036ms ago
                    IE: Unknown: 000F4254486F6D65487562322D4B515432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00

#more routers here
```

What am I doing?

Btw, iwlist is from the laptop client, for some reason iwlist scan wouldn't redirect to a file on the server. Never mind, not an issue, I don't think. (?)

---

### Post by chili555 on 2011-10-20
> I don't get where you get the numbers and/or IP adresses from.Log in to the configuration pages of your router and you should see the DHCP setup. It will show the starting and ending numbers. Pick a number outside the range. The other alternative is to check ipconfig /all on a Windows machine on the same network and you'll get an idea of the gateway (the router's IP address), and the IP addresses the router is using. If, for example, your Windows machine has 192.168.1.101, you'd probably be very safe using 192.168.1.175 in your server.

I specialize in detailed answers; or, as my wife says, I talk too much.

---

### Post by MG&amp;TL on 2011-10-20
I don't have a windows machine; they're both linux. :D

I shall go to the homehub config pages.

Talking too much isn't a bad thing; I talk too little, so nobody ever knows what I think.

---

### Post by MG&amp;TL on 2011-10-20
Right...I get the static IP thing now...what's with the DNS nameservers?

---

### Post by MG&amp;TL on 2011-10-20
Okay, I filled in the /etc/resolv.conf as suggested, and the /etc/network/interfaces with my own values from the router tables, and now:

```
ifdown wlan0 
device wlan0 not configured

ifup wlan0
SIOCADDRT: No such process
Failed to bring up wlan0

```

Any ideas? I need to shut down, though, so I'll try in the morning. Or maybe the afternoon, depending on what time I get up. School constraints, y'see.

---

### Post by chili555 on 2011-10-20
We may need to go back to basics. It looks like a wireless driver is not in place. Please post:```
lspci -nn | grep 0280
iwconfig
```See you tomorrow.

---

### Post by MG&amp;TL on 2011-10-21
...I think it works, iwlist works, and the 'working' lights blink.

But as requested:

```
$lspci -nn | grep 0280

```
returns nothing.

iwconfig:

lo: no interface

eth0: no interface

wlan0:IEEE 802.11bg  ESSID:"BTHomeHub2-KTQ2"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=4 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

Oh,and hello again!

---

### Post by MG&amp;TL on 2011-10-21
Well, I can call ifconfig down/up, but ifup/down fails. iwlist scan works too (when it's up).

So...my diagnosis is that my resolv.conf/other files arenot up to scratch. I shall have a bit of a dig. :)

---

### Post by chili555 on 2011-10-21
> **MG&TL said:**
> Well, I can call ifconfig down/up, but ifup/down fails. iwlist scan works too (when it's up).

So...my diagnosis is that my resolv.conf/other files arenot up to scratch. I shall have a bit of a dig. :)Let's see the result of:```
sudo ifdown wlan0 && sudo ifup wlan0
iwconfig wlan0
ifconfig wlan0
ping -c3 74.125.45.103
```I think we're close!

---

### Post by MG&amp;TL on 2011-10-21
ifdown wlan0:

```
ifdown: interface wlan0 not configured
```

ifup wlan0:

```
SIOCADDRT: No such process
Failed to bring up wlan0
```

iwconfig wlan0:

```
wlan0     IEEE 802.11bg ESSID:off/any
Mode: managed  Access point: not-associated Tx-Power=4 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Encryption key:off
Power management:on
```

(It resets itself to this on reboot. I can change the values with iwconfig, but they revert on reboot.)

ping:

```
connect: Network unreachable
```

So a general failure. I've been looking on the web about the resolv.conf and apparently I need to know my ISP's domain. 


Sorry about the newb-ness. There's nothing tangible about networking, so I don't get it. And the documentation's awful for newbies.

---

### Post by MG&amp;TL on 2011-10-21
> **chili555 said:**
> I think we're close!

I hope so! Thanks for all the help and such.

---

### Post by MG&amp;TL on 2011-10-21
Incidentally, I can change the HomeHub's security thing to WEP, rather than WPA2. Would this help in some way?

---

### Post by chili555 on 2011-10-21
> So a general failure. I've been looking on the web about the resolv.conf and apparently I need to know my ISP's domain. resolv.conf is, at this point, a red herring. That's not where your troubles lie. > SIOCADDRT: No such process
Failed to bring up wlan0If you (or /etc/network/interfaces) can't raise the interface, it will never get as far as resolv.conf. Let's see if there are any kernel messages about this. Please post:```
dmesg | grep -e wlan -e rt2
```Thanks.

---

### Post by chili555 on 2011-10-21
> **MG&TL said:**
> Incidentally, I can change the HomeHub's security thing to WEP, rather than WPA2. Would this help in some way?Not yet. Let's trace one thing at a time.

---

### Post by MG&amp;TL on 2011-10-21
```
[    8.481655] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2495.511758] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

I had to blacklist an rt2500 module that was being loaded for some reason, for it to work at all. Sorry, should have said earlier-does it matter?

---

### Post by chili555 on 2011-10-21
> I had to blacklist an rt2500 module that was being loaded for some reason, for it to work at all.That begs the question of what *_is_* driving the wireless! Please post:```
lsmod | grep -e rt2 -e ndis
cat /etc/modprobe.d/blacklist.conf | tail -n10
```Thanks.

---

### Post by MG&amp;TL on 2011-10-21
I manually downloaded the appropriate driver from the debian source package website and dpkg -i'ed it.

Although it IS working, I am also a little curious as to what's handling it.

lsmod...  ...-e ndis:

```
rt2x00usb              5713   1  rt73usb
rt2x00lib              19101  2  rt73usb,rt2x00usb
led_class              1757   1  rtx2x00lib
mac80211               123570 2  rtx2x00usb,rtx2x00lib
cfg80211               87657  2  rtx2x00lib, mac80211
usbcore                98733  6  rt73usb,rt2x00usb,usb_storage,uhci_hcd,ehcihcd
```

blacklist.conf:

```
#these watchdog drivers break some systems
blacklist iTCO_wdt

blacklist rt2500usb
```


The rt2500usb one's me. Every time I inserted the stick, I got a phy0 -> EEPROM error. The fix is apparently blacklisting that driver and getting the right one. That driver shouldn't even be loaded for my stick, apparently.

Sorry, I'm a pain in the ****, aren't I?

---

### Post by chili555 on 2011-10-21
Let's see what's going on under the hood. Please post:```
lsusb
dmesg | grep rt73
```> Sorry, I'm a pain in the ****, aren't I? Not at all. I enjoy unraveling a mystery. This is certainly one!

---

### Post by MG&amp;TL on 2011-10-22
Err, sorry, lsusb isn't installed-what package is it in? *lsusb* doesn't bring any hits on the debian packages site.

```
[5.940558] Registered led device: rt73usb-phy0::radio
[5.940579] Registered led device: rt73usb-phy0::assoc
[5.940598] Registered led device: rt73usb-phy0::quality
[5.941124] usbcore: registered new interface driver rt73usb
[7.432548] rt73usb 1-5:1.0 firmware: requesting rt73.bin
```

There is two USB ports at front of machine, 4 at the back, only one is used for the USB adapter; does this help?

Machine: Dell Dimension 2400; Pentium IV; 512Mb RAM; NVIDIA graphics card; Intel onboard graphics;TP-Link TL-WN321G wireless adapter.

---

### Post by MG&amp;TL on 2011-10-22
Un-blacklisting the rt2500usb produces on startup or on inserting stick equals:

```

[   5.663494] Error: Driver 'pcspkr' is already registered, aborting...
[   5.839460] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   5.839492] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device. 
```


...but iwlist scan still works, and the led blinks.

---

### Post by chili555 on 2011-10-22
lsusb is, I believe, part of usbutils. In Ubuntu, it's installed by default. It gives details about all USB devices so we can troubleshoot. So far, nothing in your readings indicate a problem that prevents the device from being raised and connecting. Let's dig a bit deeper. Please post:```
sudo cat /var/log/syslog | grep -e rt7 -e wlan | tail -n25
```Here is a sample of lsusb from my machine. I've highlighted a USB wireless device:> $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ***ID 1740:9801 Senao EUB9801 802.11abgn Wireless Adapter [Ralink RT3572]***


---

### Post by MG&amp;TL on 2011-10-22
syslogd:

```
Oct 21 20:27:41 debian-fileserver kernel: [ 2495.511758] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 21 21:09:07 debian-fileserver kernel: [    5.843539] Registered led device: rt73usb-phy0::radio
Oct 21 21:09:07 debian-fileserver kernel: [    5.843559] Registered led device: rt73usb-phy0::assoc
Oct 21 21:09:07 debian-fileserver kernel: [    5.843577] Registered led device: rt73usb-phy0::quality
Oct 21 21:09:07 debian-fileserver kernel: [    5.844129] usbcore: registered new interface driver rt73usb
Oct 21 21:09:07 debian-fileserver kernel: [    7.207715] rt73usb 1-5:1.0: firmware: requesting rt73.bin
Oct 21 21:09:07 debian-fileserver kernel: [    7.318915] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 22 10:45:20 debian-fileserver kernel: [    5.940558] Registered led device: rt73usb-phy0::radio
Oct 22 10:45:20 debian-fileserver kernel: [    5.940579] Registered led device: rt73usb-phy0::assoc
Oct 22 10:45:20 debian-fileserver kernel: [    5.940598] Registered led device: rt73usb-phy0::quality
Oct 22 10:45:20 debian-fileserver kernel: [    5.941124] usbcore: registered new interface driver rt73usb
Oct 22 10:45:20 debian-fileserver kernel: [    7.432548] rt73usb 1-5:1.0: firmware: requesting rt73.bin
Oct 22 10:45:20 debian-fileserver kernel: [    7.557607] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 22 12:43:27 debian-fileserver kernel: [    6.454835] Registered led device: rt73usb-phy0::radio
Oct 22 12:43:27 debian-fileserver kernel: [    6.454855] Registered led device: rt73usb-phy0::assoc
Oct 22 12:43:27 debian-fileserver kernel: [    6.454874] Registered led device: rt73usb-phy0::quality
Oct 22 12:43:27 debian-fileserver kernel: [    6.455389] usbcore: registered new interface driver rt73usb
Oct 22 12:43:27 debian-fileserver kernel: [    7.857220] rt73usb 1-5:1.0: firmware: requesting rt73.bin
Oct 22 12:43:27 debian-fileserver kernel: [    7.982518] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 22 12:44:32 debian-fileserver kernel: [    6.207978] Registered led device: rt73usb-phy1::radio
Oct 22 12:44:32 debian-fileserver kernel: [    6.208186] Registered led device: rt73usb-phy1::assoc
Oct 22 12:44:32 debian-fileserver kernel: [    6.208234] Registered led device: rt73usb-phy1::quality
Oct 22 12:44:32 debian-fileserver kernel: [    6.208782] usbcore: registered new interface driver rt73usb
Oct 22 12:44:32 debian-fileserver kernel: [    7.708153] rt73usb 1-5:1.0: firmware: requesting rt73.bin
Oct 22 12:44:32 debian-fileserver kernel: [    7.833384] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by MG&amp;TL on 2011-10-22
lsusb:

```

Bus 004 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 148f:2573 RaLink Technology, Corp. RT2501/RT2573 Wireless Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

There's mine. I guess I have USB 2 on the front of my pc and USB 1.1 on the back?

Sorry, debian is not as helpful as ubuntu. But a useful learning experience, nonetheless. DPKG'ed it from the package site.

---

### Post by chili555 on 2011-10-22
[http://wiki.debian.org/WiFi/rt73](http://wiki.debian.org/WiFi/rt73)

What are the errors or warnings with:```
sudo ifconfig wlan0 up
```Can you confirm that you have the needed firmware?```
sudo updatedb
locate rt73.bin
```updatedb will take a few moments, please be patient.

---

### Post by MG&amp;TL on 2011-10-22
wlan0 up: nothing at all. returns 0.

/lib/firmware/rt73.bin

---

### Post by chili555 on 2011-10-22
> wlan0 up: nothing at all. returns 0.That's good news. Now if you run:```
ifconfig wlan0
```Does it show as UP?> wlan0     Link encap:Ethernet  HWaddr 00:19:d2:c2:1b:8d  
          inet addr:192.168.1.108  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec2:1b8d/64 Scope:Link
          ***UP*** BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

---

### Post by MG&amp;TL on 2011-10-22
Sorry, for some reason UF didn't show the new post. :)

Yes, (and I can toggle at will)

```

UP BROADCAST MULTICAST MTU:1500 Metric:1
```

Is that a good thing?

Is stuff always this difficult?

---

### Post by chili555 on 2011-10-22
Things are sometimes difficult until we work out the snag and then frequently work perfectly ever after.

I assume you can toggle UP with ifconfig; yes? If so, toggle it up and then do:```
sudo ifdown wlan0 && sudo ifup wlan0
ifconfig wlan0
```If you do not have an IP address, show us:```
dmesg | tail -n15
cat /etc/network/interfaces
```Please obscure your WPA2 key.

---

### Post by MG&amp;TL on 2011-10-22
ifdown: as before, 'device not configured'
ifup: SIOCADDRT: No such process: failed to bring up wlan0.

ifconfig wlan0:
...
UP BROADCAST MULTICAST
...

The bit about dmesg:

```

[    7.770126] ADDRCONF(NETDEV_UP): wlan0: link is not ready


...random stuff about my usb memory stick not automounting. <sorry, need to go to bed soon, thought you'd rather have relevent information rather than all 15 dmesg's.>

```

network interfaces file:

```
auto wlan0 iface
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 213.123.107.250
wpa-essid BTHomeHub2-KTQ2
wpa-psk ###########
```

Won't be here until tuesday now, unfortunately; shall I PM when back? I'll be here briefly in morning.

---

### Post by chili555 on 2011-10-22
> auto wlan0 iface
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 213.123.107.250
wpa-essid BTHomeHub2-KTQ2
wpa-psk ###########No wonder.

For any machine with a 192.168.x.x address, the gateway is going to be 192.168.something. I suggest you revisit your settings. It ought to read more like:```
auto lo
iface lo inet loopback

auto wlan0 
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1  <<--my best guess, please check
wpa-essid BTHomeHub2-KTQ2
wpa-psk ###########
```> shall I PM when back? Yes, please.

---

### Post by MG&amp;TL on 2011-10-22
Okay. It's just that my homehub config pages (under TCP/IP) lists:

```
Default gateway	213.123.107.250
```

Sorry, when I say morning, I mean ~10 hours from now.

Never mind, netstat got it. 192.168.1.254, apparently. (from my client machine)

---

### Post by chili555 on 2011-10-22
That's the gateway for the router's public IP address. You want here the private address of the router itself. Check some other computer on the network. If Linux, do:```
route -n
```You will see the gateway is 192.168.1.something. Make that change in *interfaces* as well as auto wlan0 and I'm confident you'll connect.

---

### Post by MG&amp;TL on 2011-10-22
;) Good, good.

Thank you for all the help, I'm just a little freaked that all this stuff goes on behind the scenes on a desktop environment install.

I'll be sure to say when I connect. :)

---

### Post by MG&amp;TL on 2011-10-23
Okay...ifup wlan0 now works....but ifdown:

```
SIOCDELRT: No such process
```

And dhclient still hangs.


Any ideas?

---

### Post by MG&amp;TL on 2011-10-23
dhclient -v wlan0:

```

Listening on LPF/wlan0/94:0c:6d:e3:98:0a
Sending on LPF/wlan0/94:0c:6d:e3:98:0a
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
etc, etc. <DHCP DISCOVER 6 times>
No DHCPOFFERS received
No working leases in persistent database-sleeping.
```

---

### Post by MG&amp;TL on 2011-10-23
Changing my address in *interfaces* to something withing the DHCP range just has the same effect.

---

### Post by chili555 on 2011-10-23
If you are trying to set a static IP address, then dhclient is not needed and is counter to what you are trying to accomplish! A static address is when you the user establish a known address so that you will be able to ssh and ftp into a server to administer it, update it, add and remove content, etc.

DHCP is where the router assigns any old address it wants. If your server has an address (assigned by the router) of x.15 one day and x.47 the next and who knows what the day after that, how can you find its address easily? You probably want static: 192.168.1.108!

As a temporary trial, do:```
sudo ifdown wlan0 && sudo ifup wlan0
ifconfig
```Do you have an IP address? If so, please do:```
ping -c3 www.google.com
```Did you get ping returns? If so, you are connected and able to reach the internet. Reboot and ping again. If you get ping returns after a reboot and no other action, you are all set.

---

### Post by MG&amp;TL on 2011-10-26
ifconfig shows an IP, but ping:

```
ping -c google.com
ping: bad number of packets to transmit
```

and 

```
ping google.com

```

just hangs.

---

### Post by MG&amp;TL on 2011-10-26
OK, I worked out what the -c option was doing. Still hangs. Pinging the address from the client gives a 'destination host unreachable' error.

---

### Post by chili555 on 2011-10-26
Let's see:```
sudo cat /var/log/syslog | grep -i -e dhc -e wlan | tail -n20
```Thanks.

---

### Post by MG&amp;TL on 2011-10-26
One thing- On boot, there's a message:

```
starting MTA: exim4
```

which is normal. But now it takes ages to find whatever exim4 is. So it looks like this for up to a minute:

```
starting MTA: _
```

Anyways:

```

Oct 23 08:34:09 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
Oct 23 08:34:14 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
Oct 23 08:34:19 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
Oct 23 08:34:27 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 
Oct 23 08:34:45 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 
Oct 23 08:35:04 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 
Oct 23 08:35:10 debian-fileserver dhclient: No DHCPOFFERS received. 
Oct 23 08:35:10 debian-fileserver dhclient: No working leases in persistent database - sleeping. 
Oct 23 08:37:12 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
Oct 23 08:37:17 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
Oct 23 08:37:25 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 
Oct 23 08:37:39 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 
Oct 23 08:37:58 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
Oct 23 08:38:06 debian-fileserver dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
Oct 26 08:46:49 debian-fileserver kernel: [ 7.517232] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Oct 26 08:47:44 debian-fileserver kernel: [ 7.627182] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Oct 26 08:54:25 debian-fileserver kernel: [ 410.599857] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Oct 26 09:02:07 debian-fileserver kernel: [ 872.104947] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Oct 26 09:03:29 debian-fileserver kernel: [ 7.662494] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
Oct 26 16:14:37 debian-fileserver kernel: [ 7.826301] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by chili555 on 2011-10-26
Let's see your amended */etc/network/interfaces*. As always, please obscure your WPA2 password. Also, may we see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by MG&amp;TL on 2011-10-27
Iwlist is from laptop; I cannot get the desktop to redirect to to file with the formatting. :confused:

iwlist:

```

wlan0     Scan completed :
          Cell 01 - Address: 00:25:56:0A:35:4A
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-KQT2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000050d028c790
                    Extra: Last beacon: 42456ms ago
                    IE: Unknown: 000F4254486F6D65487562322D4B515432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00

```

And /etc/network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.238
netmask 255.255.255.0
gateway 192.168.1.254
wpa-essid BTHomeHub2-KTQ2
wpa-psk XXXXXXXX
```

---

### Post by chili555 on 2011-10-27
Can you confirm that the server scans and sees the same access point? From the scan:> wlan0     Scan completed :
          Cell 01 - Address: 00:25:56:0A:35:4A
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-[COLOR="Red"]**KQT2**[/COLOR]"From the interfaces file:> wpa-essid BTHomeHub2-[COLOR="Red"]KTQ2[/COLOR]See the transposition?

Also, many wireless drivers have an easier time with WPA2 only, not WPA and WPA2 mixed mode. Can you change your routers setup?

---

### Post by MG&amp;TL on 2011-10-27
Yeah; sorry. The smaller outputs from the server I type rather than transferring over USB. It is seeing the same router. :)

Errr...I can, but will it affect already connected computers? There's five in my household, y'see.

One thing- ping now hangs, rather than specifying "no such host". Is this significant?

---

### Post by chili555 on 2011-10-27
> Errr...I can, but will it affect already connected computers? There's five in my household, y'see.We may be misunderstanding each other. If you expect the server to connect to BTHomeHub2-[COLOR="Red"]**KQT2**[/COLOR], then it is the /etc/network/interfaces file that must specify BTHomeHub2-_KQT2_ instead of BTHomeHub2-K**TQ**2. Please change the /etc/network/interfaces file in the server to specify the ESSID you wish to connect to and don't transpose it. Then do:```
sudo ifdown wlan0 && sudo ifup wlan0
ifconfig
ping -c3 www.google.com
```

---

### Post by MG&amp;TL on 2011-10-27
> **chili555 said:**
> We may be misunderstanding each other. 

Yup. Sorry, my bad. :)

Trying it now.

---

### Post by MG&amp;TL on 2011-10-27
Still not connecting. No idea why. Should I try a dynamic IP, then maybe I can go back to a static IP when ready? (and actually have some utilities)

---

### Post by MG&amp;TL on 2011-10-29
Thanks chilli555, I got it in the end. Weird though. I put the USB in a different hole, and then it was fine. Maybe it reset itself or something. :confused: anyway, thread solved. :D 

Thanks for all the help.

---

