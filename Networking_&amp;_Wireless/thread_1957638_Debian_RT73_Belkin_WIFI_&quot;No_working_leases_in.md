---
title: "Debian RT73 Belkin WIFI &quot;No working leases in persistent database - sleeping&quot;"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by cmschuster on 2012-04-12
i am using debian squeeze (2.6.32-5-686) on a via mini itx.  i am trying to get the wifi up and working with a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2571W].  i am using the rt73 driver because that is what the chipset indicates i should use.

i am cross posting this because debian is "the rock upon which Ubuntu is built", and there are probably some smarter people out there than me, and the similar issue i saw here: [http://ubuntuforums.org/showthread.php?t=1637914](http://ubuntuforums.org/showthread.php?t=1637914) who knows, perhaps we can all make the world less stupid.

i followed [http://wiki.debian.org/WiFi/rt73](http://wiki.debian.org/WiFi/rt73) to get the wifi usb working.  however, i cannot connect to the wireless router.  i use rausb0.

the symptoms:

everything seems to be working ok but for a couple of key things.  i did the install using the debian wifi wiki, so i think that the driver is properly installed and deconflicted.  i updated the vi etc/network/interfaces just as is indicated, but when i iwconfig it does not show the essid that i put into the etc/network/interfaces, nor that i have WPA (it says Security mode:open).  not only that, but when i ifconfig, it does not even list an inet address.  further indication, cat /var/log/syslog indicates no IPv6 routers present.  using iwlist scan, i can see the router, and ifconfig indicates packets are going up and down.  when i ifdown and ifup, it just sits there and says "DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12" until it tells me it received no DHCPOFFERS and is going to sleep.  also, the little LED on the Belkin device is intermittently blinking like its browsing reddit or something.

What am i missing? help?

here are the outputs from some key commands.  i have info from lsusb, lsmod, dmesg, cat /var/log/syslog, ifconfig, iwconfig, iwlist scan, and vi etc/network/interfaces.

lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2571W]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsmod

```
usbcore             99329  5 rt73,usbhid,uhci_hcd,ehci_hcd
```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:off/any
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=54 Mb/s 
          RTS thr:off   Fragment thr:off
          Encryption key:0123-4567-89 Security mode:open
          Link Quality:0/100  Signal level:-121dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ifconfig

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

rausb0    Link encap:Ethernet  HWaddr "mac address"
          inet6 addr: fe80::222:75ff:feb1:87bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:641052 (626.0 KiB)  TX bytes:177624 (173.4 KiB)
```

cat /var/log/syslog | grep rausb | tail -n20

```
kernel:  [   20.864006] rausb0: no IPv6 routers present
dhclient: DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
```

iwlist scan

```
rausb0     Scan completed:
           Cell 01 - Address: "mac address"
           Mode:Managed
           ESSID:"goodbar1"
           Channel:1
           Encryption key:on
           Bit Rates:130 Mb/s
```

vi etc/network/interfaces

```
auto lo
iface lo inet loopback

iface rausb0 inet dhcp
pre-up ip link set dev rausb0 up
wireless-essid MY_ESSID
wireless-key s:"my wireless string"
auto rausb0
```

uname -r
```
2.6.32-5-686
```

dmesg | grep rt73
```
[    6.419406] usbcore: registered new interface driver rt73
```

ifup rausb0

```
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by chili555 on 2012-04-12
Is Network Manager running here? Usually, NM and manual configuration; i.e. /etc/network/interfaces, don't play well together.```
ps aux | grep etwork
```> Encryption key:0123-4567-89 Security mode:openUsually a ten character key is hex and not ascii. Ascii requires the s: prefix, not hex.

---

### Post by cmschuster on 2012-04-12
> **chili555 said:**
> Is Network Manager running here? Usually, NM and manual configuration; i.e. /etc/network/interfaces, don't play well together.```
ps aux | grep etwork
```Usually a ten character key is hex and not ascii. Ascii requires the s: prefix, not hex.

i have heard that they do not.  i will look at my processes with ps and get back to you with the code results.

thank you for the response! ive been hitting my head against the terminal on this one...

---

### Post by chili555 on 2012-04-12
I noticed this:> usbcore             99329  5 [COLOR="Red"]rt73[/COLOR],usbhid,uhci_hcd,ehci_hcdFrom the wiki you linked:> rt73 (Legacy driver)

    Released by Ralink under the GPL.
    Not generally recommended for use. 

rt73 (Enhanced legacy driver)

    Previously maintained by the rt2x00 project.

    Source previously packaged in rt73-source, removed from Debian to resolve bug 563432. And then...> rt73usb (Next-generation driver)

    The recommended driver to use.

    Source previously packaged in rt2x00-source, removed from Debian to resolve bug 474189.
    Introduced in Linux 2.6.24. Isn't the preferred driver rt73**usb** included in Squeeze?

---

