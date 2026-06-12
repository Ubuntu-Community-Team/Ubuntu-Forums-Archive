---
title: "Wireless gets link-local inet6 address"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by yadeki on 2013-04-14
Hello,

I have a problem configuring my wireless. I'm using a ralink rt2800usb driver that comes as a built-in driver.
When I scan my network I get this:

```
yannick@HTPC$ iwlist wlan0 scan                                 
wlan0     Scan completed :
          Cell 01 - Address: 00:07:7D:14:80:D4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm
                    Encryption key:on
                    ESSID:"DeKinderWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000822c1f22
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 000C44654B696E64657257494649
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00


```

When I do a iwconfig I get this:

```

yannick@HTPC$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DeKinderWIFI"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:07:7D:14:80:D4
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-40 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

When I do an ifconfig I get this:

```

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:92:7a:a5
          inet6 addr: fe80::21c:dfff:fe92:7aa5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:501795 (501.7 KB)  TX bytes:744828 (744.8 KB)

```

Why is my wireless not getting a correct IPv4 address? Instead it gets a link-local address.
The wifi dongle is recognized by my machine with the correct driver, otherwise the scan would not work.

Thanks for your help!

---

### Post by Hadaka on 2013-04-14
[ATTACH=CONFIG]241337[/ATTACH]

IPv6 is set by os default, 
click system settings
network
wireless
options
Ipv6 settings
set to IGNORE

---

### Post by yadeki on 2013-04-15
> **Hadaka said:**
> [ATTACH=CONFIG]241337[/ATTACH]

IPv6 is set by os default, 
click system settings
network
wireless
options
Ipv6 settings
set to IGNORE

Hello,

Thanks for your answer. 
I only work in cli. It's a xbmcbuntu server. So I haven't got an ubuntu desktop. If I disable ipv6 I get no address at all. The link-local address is gathered from the MAC address. It means that I haven't got a connection.
The problem is that my wifi is recognized but I don't get an IP.
Anymore help please?

---

### Post by Iowan on 2013-04-15
> **yadeki said:**
>  It's a xbmcbuntu server.I'm not really familiar w/ xbmcbuntu, but no desktop suggests it uses */etc/network/interfaces*. What is in that file? I'm wondering if it has an "auto wlan0" line.

---

### Post by chili555 on 2013-04-15
FYI, these addresses [COLOR="#FF0000"]fe80[/COLOR]::21c:dfff:fe92:7aa5/64 are placeholders, not real working addresses. I suspect your system said it would like an address from the router, ideally static, and the router didn't like some of your setting and refused.

We now return you to your regularly scheduled gurus.> What is in that file?Yes, please.

---

### Post by yadeki on 2013-04-20
> I'm not really familiar w/ xbmcbuntu, but no desktop suggests it uses */etc/network/interfaces*. What is in that file? I'm wondering if it has an "auto wlan0" line.

That's right. Here's the output of this file:
```

#auto lo
#iface lo inet loopback

#WLAN config (my own adding)
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid DeKinderWIFI
wpa-psk 1f33b3cd4bd8a044ea958af749881bde774cf6a3f85d363f3f826c526ca468bf
# if your SSID is hidden, change value to 2
wpa-ap-scan 1
# type WPA for WPA1, RSN for WPA2
wpa-proto RSN
# type CCMP for AES, TKIP for TKIP
wpa-pairwise CCMP
# type CCMP for AES, TKIP for TKIP
wpa-group CCMP
# type WPA-PSK for shared key (most common), WPA-EAP for enterprise radius server
wpa-key-mgmt WPA-PSK

```

My router config:

```

Select SSID:                            DeKinderWIFI
Wireless Isolation within SSID:     Disabled
Security:                                 WPA2 Personal
Encryption:                              AES
WPA Key:                                ********

```

---

### Post by yadeki on 2013-04-20
> I'm not really familiar w/ xbmcbuntu

It's actually running on Ubuntu 11.10:

yannick@HTPC:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10 - XBMCbuntu
Release:        11.10
Codename:       oneiric

The only thing that is different is the XBMC software and the GUI.

---

### Post by steeldriver on 2013-04-20
Do you really need all that "stuff" in your wlan0 definition? for WPA personal with DHCP I've never had to do more than

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid *yourssid*
    wpa-psk *yourpassphrase*

```

---

### Post by yadeki on 2013-04-20
> **steeldriver said:**
> Do you really need all that "stuff" in your wlan0 definition? for WPA personal with DHCP I've never had to do more than

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid *yourssid*
    wpa-psk *yourpassphrase*

```

Hello and thanks for the reply.
I just changed the config to what you said, but again a "sudo dhclient wlan0" doesn't give me an IP address...
I tried a lot, but I guess I'm forgetting something.
Anything else perhaps? :)

---

### Post by steeldriver on 2013-04-20
What did you do inbetween? you may need to actually reboot (as opposed to just restarting the networking service) to flush out your explicit driver specification

If you're still not getting a valid IP then we need to start debugging that - you can try invoking dhclient with the -v switch to get verbose info

```

sudo dhclient -r

sudo dhclient -v wlan0

```

(should show you the DHCP negotiation in real time) and you can also look at the dmesg output filtered for 'wlan0'

```
dmesg | grep wlan0
```

We should probably also take a step back and check exactly what device (PCI ID) you have and what driver it's trying to use

```

lspci -nn | grep -e '\[0200\]' -e '\[0280\]'

sudo lshw -C network

```

---

### Post by chili555 on 2013-04-20
> I just changed the config to what you said, but again a "sudo dhclient wlan0" doesn't give me an IP address...Are there any clues here?```
sudo ifdown wlan0 && sudo ifup -v wlan0
cat /var/log/syslog | grep wlan0 | tail -n20
```Ideally run consecutively.

I agree with and use this configuration myself without any problems:```
auto wlan0
iface wlan0 inet dhcp
wpa-ssid yourssid
wpa-psk yourpassphrase
```

---

### Post by chili555 on 2013-04-20
> sudo dhclient -v wlan0I think this says to the system to get an IP address for wlan0. I think the following is preferred, since it asks for the details in /etc/network/interfaces to be used:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```...or am I corn-fused, steeldriver?? (Always a possibility!)

---

### Post by steeldriver on 2013-04-20
You are probably right chili - I have used dhclient -r / dhclient -v in the past but I don't know that it's the 'right' way

As you say it makes more sense to let ifup decide what to do based on the config file

---

### Post by chili555 on 2013-04-20
> **steeldriver said:**
> You are probably right chili - I have used dhclient -r / dhclient -v in the past but I don't know that it's the 'right' way

As you say it makes more sense to let ifup decide what to do based on the config file@yadeki--

Please try *BOTH* methods and give us your results. Both use the '-v' switch so that we can see informative messages.

---

### Post by yadeki on 2013-04-20
> We should probably also take a step back and check exactly what device (PCI ID) you have and what driver it's trying to use

It's an USB dongle Realtek rt2870usb (built in driver).

---

### Post by yadeki on 2013-04-20
> sudo dhclient -v wlan0

Gives me:

```
yannick@HTPC:~$ sudo dhclient -v wlan0
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1c:df:92:7a:a5
Sending on   LPF/wlan0/00:1c:df:92:7a:a5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
...

```

And so on...


> sudo ifdown wlan0 && sudo ifup -v wlan0

Gives me:

```
ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile  /var/run/wpa_suppl                                                                                                                       icant.wlan0.pid
Stopped /sbin/wpa_supplicant (pid 2164).
wpa_supplicant: removing  /lib/init/rw/sendsigs.omit.d/wpasupplicant.wpa_supplica                                                                                                                       nt.wlan0.pid
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P  /var/run/wpa_supplicant.wlan0.pid                                                                                                                        -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile:  /lib/init/rw/sendsigs.omit.d                                                                                                                       /wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "DeKinderWIFI" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK
```
Then it fails.

```
yannick@HTPC:~$ cat /var/log/syslog | grep wlan0 | tail -n20
```
Gives me:
```

Apr 20 18:12:22 HTPC kernel: [ 1409.610608] wlan0: authenticated
Apr 20 18:12:22 HTPC kernel: [ 1409.628312] wlan0: associate with 00:07:7d:14:80:d4 (try 1)
Apr 20 18:12:22 HTPC kernel: [ 1409.631486] wlan0: RX ReassocResp from 00:07:7d:14:80:d4 (capab=0x411 status=0 aid=1)
Apr 20 18:12:22 HTPC kernel: [ 1409.631496] wlan0: associated
Apr 20 18:12:24 HTPC dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 20 18:12:32 HTPC kernel: [ 1419.739880] wlan0: disassociating from 00:07:7d:14:80:d4 by local choice (reason=3)
Apr 20 18:12:32 HTPC kernel: [ 1419.787211] wlan0: deauthenticating from 00:07:7d:14:80:d4 by local choice (reason=3)
Apr 20 18:12:33 HTPC kernel: [ 1421.048896] wlan0: authenticate with 00:07:7d:14:80:d4 (try 1)
Apr 20 18:12:33 HTPC kernel: [ 1421.050564] wlan0: authenticated
Apr 20 18:12:33 HTPC kernel: [ 1421.068278] wlan0: associate with 00:07:7d:14:80:d4 (try 1)
Apr 20 18:12:33 HTPC kernel: [ 1421.071441] wlan0: RX ReassocResp from 00:07:7d:14:80:d4 (capab=0x411 status=0 aid=1)
Apr 20 18:12:33 HTPC kernel: [ 1421.071451] wlan0: associated
Apr 20 18:12:43 HTPC dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 20 18:12:43 HTPC kernel: [ 1431.119923] wlan0: disassociating from 00:07:7d:14:80:d4 by local choice (reason=3)
Apr 20 18:12:43 HTPC kernel: [ 1431.170080] wlan0: deauthenticating from 00:07:7d:14:80:d4 by local choice (reason=3)
Apr 20 18:12:44 HTPC kernel: [ 1432.428858] wlan0: authenticate with 00:07:7d:14:80:d4 (try 1)
Apr 20 18:12:44 HTPC kernel: [ 1432.430502] wlan0: authenticated
Apr 20 18:12:44 HTPC kernel: [ 1432.448371] wlan0: associate with 00:07:7d:14:80:d4 (try 1)
Apr 20 18:12:44 HTPC kernel: [ 1432.451534] wlan0: RX ReassocResp from 00:07:7d:14:80:d4 (capab=0x411 status=0 aid=1)
Apr 20 18:12:44 HTPC kernel: [ 1432.451544] wlan0: associated

```

---

### Post by Iowan on 2013-04-20
> **yadeki said:**
> That's right. Here's the output of this file:
```

#auto lo
#iface lo inet loopback
...

```
A bit off-topic at the moment, but you will eventually want to re-enable the "lo" configuration.

---

### Post by steeldriver on 2013-04-20
I'm not seeing any red flags - it looks like the device is authenticating AND associating OK - just the DHCP is failing to get a response. Are you sure the router's DHCP server is enabled/configured? Are you sure you don't have any kind of wireless MAC filtering set up on your router that might be rejecting DHCP requests from the dongle device?

---

### Post by yadeki on 2013-04-20
> **steeldriver said:**
> I'm not seeing any red flags - it looks like the device is authenticating AND associating OK - just the DHCP is failing to get a response. Are you sure the router's DHCP server is enabled/configured? Are you sure you don't have any kind of wireless MAC filtering set up on your router that might be rejecting DHCP requests from the dongle device?

I'm 100% sure that I don't have MAC filtering enabled. The DHCP service is running on the router.

I just assigned a static IP for wlan0, even then I can't ping the IP address.

interfaces config file:
```

#localhost
auto lo
iface lo inet loopback
#wired 
auto eth0
iface eth0 inet dhcp
#WLAN 
auto wlan0
iface wlan0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
wpa-ssid DeKinderWIFI
wpa-psk <MyPSK(too long for typing :))>

``` 

Am I doing something wrong here?

---

### Post by steeldriver on 2013-04-20
Actually I DO see red flags now I look at it closer - the persistent

```
wlan0: disassociating from 00:07:7d:14:80:d4 by local choice (reason=3)
```

are a problem I think - may indicate a driver bug? I will see what I can dig up (although chili555 and others on this forum know a lot more about wireless devices than I do)

---

### Post by yadeki on 2013-04-20
Oh thanks 
my knowledge of Ubuntu is too small to troubleshoot driver bugs so I hope anyone of you can help me.

---

### Post by steeldriver on 2013-04-20
Well I'm sure one of the wireless gurus will be able to help you out - in the meantime if you don't mind a quick experiment you could try

```

sudo modprobe -r rt2800usb

sudo modprobe -v rt2800usb nohwcrypt=Y

```

and let us know if that makes any difference

EDIT: please disregard my earlier suggestion about lspci - I forgot we are dealing with a USB device

---

### Post by chili555 on 2013-04-20
And you guarantee with your hand placed on my autographed copy of 'C Programmers Bible' that Network Manager nor Wicd is installed nor running? Promise?

I would absolutely change the file to:```
#localhost
auto lo
iface lo inet loopback
#wired 
[COLOR="#FF0000"]#[/COLOR]auto eth0
iface eth0 inet dhcp
#WLAN 
auto wlan0
iface wlan0 inet static
address 192.168.1.[COLOR="#FF0000"]105[/COLOR] <--a number outside the DHCP range of the router
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid DeKinderWIFI
wpa-psk <MyPSK(too long for typing :))>
[COLOR="#FF0000"]dns-nameservers 192.168.1.1 8.8.8.8[/COLOR]
```If you want a static IP, then the DHCP server isn't going to hand out DNS nameservers; it's up to you to declare them.

I suggest you comment out 'auto eth0' since you won't need wired to try to start as well as wireless.

Then try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
ifconfig
ping -c3 www.google.com
```And diagnose if needed:```
cat /var/log/syslog | grep wlan0 | tail -n20
```> Apr 20 18:12:44 HTPC kernel: [ 1432.448371] wlan0: associate with 00:07:7d:14:80:d4 (try 1)
Apr 20 18:12:44 HTPC kernel: [ 1432.451534] wlan0: RX ReassocResp from 00:07:7d:14:80:d4 (capab=0x411 status=0 aid=1)
Apr 20 18:12:44 HTPC kernel: [ 1432.451544] wlan0: associatedThat's the end (tail) of your log. What happened next? It looks like you are associated and connected. No?

---

### Post by yadeki on 2013-04-21
> And you guarantee with your hand placed on my autographed copy of 'C  Programmers Bible' that Network Manager nor Wicd is installed nor  running? Promise?

I don't know. We never talked about that ;)
I recall myself something about "wpasupplicant" but don't really remember where I found that. I think it was [here]("http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870").
I don't know how to check wether I have a network manager.


> sudo ifdown wlan0 && sudo ifup -v wlan0

Keeps hanging on "dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -If /var/lib/dhcp3/dhclient.wlan0.leases -1 wlan0", after 5min or so it says "Failed to bring up wlan0".

> If you want a static IP, then the DHCP server isn't going to hand out DNS nameservers; it's up to you to declare them.

I suggest you comment out 'auto eth0' since you won't need wired to try to start as well as wireless.

I want to go back to the basic now and work with a static IP. So we can result that it's no driver issue. Screw the DHCP. :)
I copied your modified interfaces file, and restarted the machine. It gets the 192.168.1.5 address (I didn't go for the 192.168.1.105 address because my scope is 100-120), but I can't even ping my gateway 192.168.1.1. I get an answer from my own machine "destination host unreachable". So I think it has something to do with the driver??

---

### Post by yadeki on 2013-04-21
> **steeldriver said:**
> Well I'm sure one of the wireless gurus will be able to help you out - in the meantime if you don't mind a quick experiment you could try

```

sudo modprobe -r rt2800usb

sudo modprobe -v rt2800usb nohwcrypt=Y

```

and let us know if that makes any difference

EDIT: please disregard my earlier suggestion about lspci - I forgot we are dealing with a USB device

I now work with a static IP.
I did the commands you gave me, restarted... Still "Destination host unreachable"

---

### Post by chili555 on 2013-04-21
Here is how we check for NM or Wicd:```
ps aux | grep etwork
ps aux | grep wicd
```If either, or heaven forbid, both are running, they will compete with your interfaces file for control. Sort of like having six hands on the steering wheel as we traverse the Nurburgring at 250 kph.  [http://www.youtube.com/watch?v=sMw_IbGqPo4](http://www.youtube.com/watch?v=sMw_IbGqPo4) > I recall myself something about "wpasupplicant" but don't really remember where I found that. I think it was here.Did you read this at the beginning?> This guide was written in 2009, has not been supported in years, and is not a recommended way to deal with this problem.There are 14 pages there which is very hard for me to pick through. Maybe we can figure out what you changed:```
history | grep supplicant
```>  because my scope is 100-120Meaning what? That the DHCP pool is from 100 to 120? If so, then a static IP of x.5 is correct.> Keeps hanging on "dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -If /var/lib/dhcp3/dhclient.wlan0.leases -1 wlan0", after 5min or so it says "Failed to bring up wlan0".
Studying; I'll reserve my thoughts until we learn about NM and Wicd.

---

### Post by yadeki on 2013-04-21
> ps aux | grep etwork 
ps aux | grep wicd

This is what de ps... gave me:

```

yannick@HTPC:~$ ps aux | grep etwork
yannick   4912  0.0  0.0   4196   760 pts/0    S+   15:43   0:00 grep --color=auto etwork
yannick@HTPC:~$ ps aux | grep wicd
yannick   4914  0.0  0.0   4196   760 pts/0    S+   15:43   0:00 grep --color=auto wicd

```

> history | grep supplicant

Gives me:

```

yannick@HTPC:~$ history | grep supplicant
  427  sudo apt-get install wireless-tools wpasupplicant
  435  sudo vi /etc/wpa_supplicant.conf
  438  cd  /etc/wpa_supplicant
  523  sudo aptitude install wpasupplicant
  524  sudo apt-get install wpasupplicant
  525  sudo aptitude install wpasupplicant
  526  sudo apt-get install wpasupplicant
  527  sudo vi /etc/wpa_supplicant.conf
  530  sudo vi /etc/wpa_supplicant.conf
  531  sudo vi /etc/wpa_supplicant
  532  cd /etc/wpa_supplicant/
  541  sudo apt-get install wpasupplicant
  592  wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf
  595  cd wpa_supplicant/
  602  sudo apt-get install wpasupplicant
  603  sudo apt-get remove  wpasupplicant
  604  sudo apt-get autoremove  wpasupplicant
  605  sudo apt-get remove wpasupplicant
  608  sudo apt-get install wpasupplicant
  610  cd wpa_supplicant/
  621  sudo vi /etc/wpa_supplicant.conf
  625  sudo vi /etc/wpa_supplicant.conf
  627  sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iDEVICE-NAME -Dwext
  629  sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -irt2870usb -Dwext
  630  sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -irt2800usb -Dwext
  631  sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iwlan0 -Dwext
  636  sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iwlan0 -Dwext
  644  sudo apt-get remove wpa_supplicant
  645  sudo apt-get remove  wpasupplicant
  653  sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iwlan0 -Dwext
  799  history | grep supplicant

```

I'm a real Linux newbie, so forgive me my sins if I did lots of wrong things. :)

---

### Post by chili555 on 2013-04-21
> I'm a real Linux newbie, so forgive me my sins if I did lots of wrong things.Not a problem. Everyone, including me and including Linus, was a newbie at one time.

Back in a few.

EDIT:> 645  sudo apt-get remove  wpasupplicantI think if you intend to connect to a WPA2 protected network, you need this. Please check if it's installed:```
sudo dpkg -s  wpasupplicant
```If not, please do:```
sudo apt-get install wpasupplicant
```Then try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
ping -c3 www.google.com
```Post any errors or warnings.

---

### Post by steeldriver on 2013-04-21
Well fwiw I dug out an old ASUS USB dongle that uses rt2800usb:

```
$ lsusb | grep etwork
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT3072]

$ sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
.
<snip>
.
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
.
<snip>
.
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan1
       serial: bc:ae:c5:7d:a0:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-40-generic-pae firmware=0.29 ip=192.168.1.19 link=yes multicast=yes wireless=IEEE 802.11bgn


```

I stuck it in my 12.04.2 server lappy and blacklisted the internal wireless (ath5k) and then modified my /etc/network/interfaces as follows (NB the logical name is [FONT=courier new]**wlan1 **[/FONT]in my case - as shown by [FONT=courier new]lshw -C network[/FONT])

```
~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet dhcp
dns-nameservers 192.168.1.1

auto wlan1
iface wlan1 inet dhcp
    wpa-ssid *myssid*
    wpa-psk *mypassphrase*
dns-nameservers 192.168.1.1


```

and rebooted - it *does* come up (and get a DHCP assigned address) but the link is not stable (it dropped my ssh connection after a few minutes)

```
$ ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr bc:ae:c5:7d:a0:aa
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe7d:a0aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23347 (23.3 KB)  TX bytes:35782 (35.7 KB)


```

chili please lmk if there's anything else you want me to try by way of experimentation - this is a 'play' box for me so I don't mind if things get screwed up

---

### Post by yadeki on 2013-04-21
> sudo ifdown wlan0 && sudo ifup -v wlan0

I did "sudo apt-get remove wpasupplicant" and after that "sudo apt-get instal wpasupplicant"
Then I did the line above and that gave me this answer:

```

yannick@HTPC:/$ sudo ifdown wlan0 && sudo ifup -v wlan0
ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid
Stopped /sbin/wpa_supplicant (pid 9441).
wpa_supplicant: removing /lib/init/rw/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: waiting for "/var/run/wpa_supplicant.wlan0.pid":  0 (max. 5)
wpa_supplicant: creating sendsigs omission pidfile: /lib/init/rw/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "DeKinderWIFI" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases -1 wlan0
Failed to bring up wlan0

```

---

### Post by yadeki on 2013-04-21
> **steeldriver said:**
> Well fwiw I dug out an old ASUS USB dongle that uses rt2800usb:

```
$ lsusb | grep etwork
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT3072]

$ sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
.
<snip>
.
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
.
<snip>
.
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan1
       serial: bc:ae:c5:7d:a0:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-40-generic-pae firmware=0.29 ip=192.168.1.19 link=yes multicast=yes wireless=IEEE 802.11bgn


```

I stuck it in my 12.04.2 server lappy and blacklisted the internal wireless (ath5k) and then modified my /etc/network/interfaces as follows (NB the logical name is [FONT=courier new]**wlan1 **[/FONT]in my case - as shown by [FONT=courier new]lshw -C network[/FONT])

```
~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet dhcp
dns-nameservers 192.168.1.1

auto wlan1
iface wlan1 inet dhcp
    wpa-ssid *myssid*
    wpa-psk *mypassphrase*
dns-nameservers 192.168.1.1


```

and rebooted - it *does* come up (and get a DHCP assigned address) but the link is not stable (it dropped my ssh connection after a few minutes)

```
$ ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr bc:ae:c5:7d:a0:aa
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe7d:a0aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23347 (23.3 KB)  TX bytes:35782 (35.7 KB)


```

chili please lmk if there's anything else you want me to try by way of experimentation - this is a 'play' box for me so I don't mind if things get screwed up

Is this an answer for me? Because it already goes wrong at line 1 :)
if I do "lsusb |grep etwork" it gives me nothing. I just go to the next line.
```

yannick@HTPC:/$ sudo lsusb | grep etwork
yannick@HTPC:/$

```

---

### Post by yadeki on 2013-04-21
I now reactivated the eth0 interface because of the easy copying from the ssh session and this forum.

> sudo lshw -C network

Gives me:

```
yannick@HTPC:/$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: d4:3d:7e:33:fa:89
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.106 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febe0000-febfffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:6
       logical name: wlan0
       serial: 00:1c:df:92:7a:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.0.0-31-generic-pae firmware=0.29 ip=192.168.1.5 link=yes multicast=yes wireless=IEEE 802.11bgn

```

That's how my interfaces config file looks like:

```
yannick@HTPC:/$ cat /etc/network/interfaces
#The loopback network interface (localhost)
auto lo
iface lo inet loopback

#The wired network interface
auto eth0
iface eth0 inet dhcp
dns-nameservers 192.168.1.1

#The wireless network interface
auto wlan0
iface wlan0 inet dhcp
dns-nameservers 192.168.1.1
wpa-ssid DeKinderWIFI
wpa-psk 1f33b3cd4bd8a044ea958af749881bde774cf6a3f85d363f3f826c526ca468bf

```

---

### Post by steeldriver on 2013-04-21
> **yadeki said:**
> Is this an answer for me?


It was really just meant to confirm that the rt2800usb is not completely broken, and to start to troubleshoot why it's working on my system with just a minimal /etc/network/interfaces file but not on yours

> **yadeki said:**
> Because it already goes wrong at line 1 :smile:
if I do "lsusb |grep etwork" it gives me nothing. I just go to the next line.
 

Our devices are not the same - presumably the manufacturer's descriptive name doesn't contain the word 'Network' or 'network'. You can do a plain 'lsusb' (without the pipe to grep) if you really want to know

FWIW after switching my router to Wireless-g mode only the link seems to remain stable - I scp'd a big file over to it and got sustained rates of 600+ KiB/s (i.e. basically the full 54Mb/s)

---

### Post by yadeki on 2013-04-21
> **steeldriver said:**
> It was really just meant to confirm that the rt2800usb is not completely broken, and to start to troubleshoot why it's working on my system with just a minimal /etc/network/interfaces file but not on yours

 

Our devices are not the same - presumably the manufacturer's descriptive name doesn't contain the word 'Network' or 'network'. You can do a plain 'lsusb' (without the pipe to grep) if you really want to know

FWIW after switching my router to Wireless-g mode only the link seems to remain stable - I scp'd a big file over to it and got sustained rates of 600+ KiB/s (i.e. basically the full 54Mb/s)

Ok thanks. I overlooked that. The grep is already familiar to me. :)

```
yannick@HTPC:~$ lsusb | grep Belkin
Bus 002 Device 003: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]

```

---

### Post by steeldriver on 2013-04-21
> **yadeki said:**
> 
```
yannick@HTPC:~$ lsusb | grep Belkin
Bus 002 Device 003: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink **RT2870**]

```

Hmm... well I'm not sure that rt2800usb is the correct driver for that chipset with your kernel version - you may need to install something direct from Ralink. Let's wait and see what the wireless gurus have to say.

---

### Post by yadeki on 2013-04-22
> **steeldriver said:**
> Hmm... well I'm not sure that rt2800usb is the correct driver for that chipset with your kernel version - you may need to install something direct from Ralink. Let's wait and see what the wireless gurus have to say.

Thank you. I'm looking forward to it.
I'm moving to my new home next week where I'm going to install the XBMC server. :mrgreen:
There's no place for wires, that's why I have to use the wireless.

---

### Post by chili555 on 2013-04-22
> **steeldriver said:**
> Hmm... well I'm not sure that rt2800usb is the correct driver for that chipset with your kernel version - you may need to install something direct from Ralink. Let's wait and see what the wireless gurus have to say.rt2800usb is correct. Please insert it and see what happens. 

I'd change the interfaces file to read:> 
#The loopback network interface (localhost)
auto lo
iface lo inet loopback

#The wired network interface
#auto eth0
iface eth0 inet dhcp

#The wireless network interface
auto wlan0
iface wlan0 inet dhcp
wpa-ssid DeKinderWIFI
wpa-psk 1f33b3cd4bd8a044ea958af749881bde774cf6a3f85d363f3f826c526ca468bf
dns-nameservers 192.168.1.1Why did you give up on static?

---

### Post by yadeki on 2013-04-22
> **chili555 said:**
> I'd change the interfaces file to read

If I do that I can't access my server anymore through SSH to copy output... That's why I uncommented the eth0 in first place.

> Why did you give up on static?

I thought, if steeldriver can do it with DHCP + rt2870usb than why shouldn't I? 
I will change it back to static if u want. That's the easy part :smile:
Maybe I have to start all over again? Delete everything that has to do with wireless and rebuild it?

---

### Post by chili555 on 2013-04-22
If your system gets an ethernet connection, I'm not sure it ever continues to try a simultaneous wireless connection. It can be done, usually to separate networks, but it takes some serious fiddling in the underlying configuration files to do it.

It's very hard to troubleshoot when the conditions change frequently and when we are trying to establish a connection when you already have a wired ethernet connection.> I thought, if steeldriver can do it with DHCP + rt2870usb than why shouldn't I? If the interfaces file and the driver are set up correctly, either is equally easy to do. It's pretty hard to get the file set up correctly since it changes by the minute.

I suspect this is actually an rt2800usb issue. There are plenty of posts here on the forum about rt2800usb and rt2800pci, for that matter, that complain that they can't ever connect or stay connected longer than a few seconds.

I've suggested a setup twice and I regret that my suggestions are evidently not useful.

---

### Post by yadeki on 2013-04-22
> **chili555 said:**
> If your system gets an ethernet connection, I'm not sure it ever continues to try a simultaneous wireless connection. It can be done, usually to separate networks, but it takes some serious fiddling in the underlying configuration files to do it.

It's very hard to troubleshoot when the conditions change frequently and when we are trying to establish a connection when you already have a wired ethernet connection.If the interfaces file and the driver are set up correctly, either is equally easy to do. It's pretty hard to get the file set up correctly since it changes by the minute.

I suspect this is actually an rt2800usb issue. There are plenty of posts here on the forum about rt2800usb and rt2800pci, for that matter, that complain that they can't ever connect or stay connected longer than a few seconds.

I've suggested a setup twice and I regret that my suggestions are evidently not useful.

No problem; I change the config file to this (like it was on your last post):
```

#localhost 
auto lo 
iface lo inet loopback 
#wired  
#auto eth0 
iface eth0 inet dhcp 
#WLAN  
auto wlan0 
iface wlan0 inet static 
address 192.168.1.5 
netmask 255.255.255.0 
network 192.168.1.0 
broadcast 192.168.1.255 
gateway 192.168.1.1 
dns-nameservers 192.168.1.1
wpa-ssid DeKinderWIFI 
wpa-psk <MyPSK>

```

If you want this to find a good solution, I'm at your service. :o

---

### Post by steeldriver on 2013-04-22
^^^ as I mentioned earlier, although I got a connection with 11n enabled (one step ahead of you) it wasn't stable until I disabled 11n at the router (unlike some drivers, there doesn't seem to be a modprobe option to disable 11n at the client end).

Looking at my logs today I also see a bunch of 'deauthenticating by local choice' messages - so I'd suggest trying setting your router to 11g only if you can and having another shot

```
Apr 21 17:14:07 think60p kernel: [ 5949.115906] wlan1: disassociated from 20:4e:7f:4a:8a:77 (Reason: 8)
Apr 21 17:14:07 think60p kernel: [ 5949.165351] wlan1: deauthenticating from 20:4e:7f:4a:8a:77 by local choice (reason=3)

```

I used to use this dongle all the time w/o issues but iirc that was before I upgraded my home router to an 11n-capable one

Hope this helps.

---

### Post by chili555 on 2013-04-22
> No problem; I change the config file to this (like it was on your last post):Please re-read my posts. This is not what I suggested.

---

### Post by yadeki on 2013-04-22
> **chili555 said:**
> Please re-read my posts. This is not what I suggested.

I know. :)
You're giving up, that's what I could make of your last post? I don't want to accept that. :)
But offcourse, thanks for all the effort!

---

### Post by steeldriver on 2013-04-22
OK let's take a step back and see if we can move forward again

1. IF your router supports wireless-n mode, then please disable it. While you're in the router's config pages, see if you can check what DHCP range (aka 'LAN pool') it is using so we can avoid any potential address conflicts.

2. Let's disable hardware encryption from the get go - it may not be part of the problem, but it sometimes is, and it appears to be the only configurable parameter for that driver

```
echo "options rt2800usb nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800usb.conf
```

While we're at it, let's check there are no other modprobe configs lurking there

```
grep '\<rt' /etc/modprobe.d/*
```

3. Since your original error logs were DHCP related let's start a with static IP but **making sure that the chosen IP is OUTSIDE the router's DHCP LAN pool** - chili555 suggested **192.168.1.[COLOR=#ff0000]105[/COLOR]** in an earlier post, so let's try that **unless your router's config pages indicate otherwise**.

4. Finally, make sure your wired interface isn't coming up automatically by commenting out the 'auto eth0' line. You can always bring it up manually with 'sudo ifup eth0' if wlan0 doesn't come up and you want to ssh in and pull the logs.

i.e. as per chili555's post

```

#localhost
auto lo
iface lo inet loopback
#wired 
[COLOR=#ff0000]**#**[/COLOR]auto eth0
iface eth0 inet dhcp
#WLAN 
auto wlan0
iface wlan0 inet static
address **192.168.1.[COLOR=#ff0000]105[/COLOR]**
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid DeKinderWIFI
wpa-psk <MyPSK(too long for typing :))>
dns-nameservers 192.168.1.1 8.8.8.8

```

Then reboot and we will take stock.

---

### Post by yadeki on 2013-04-22
I reinstalled my XBMCbuntu. It was my first Linux machine, so I had in mind ******* it up.
So:

> 1. IF your router supports wireless-n mode, then please disable it.  While you're in the router's config pages, see if you can check what  DHCP range (aka 'LAN pool') it is using so we can avoid any potential  address conflicts.

Set it to B/G mixed.

> 2. Let's disable hardware encryption from the get go - it may not be  part of the problem, but it sometimes is, and it appears to be the only  configurable parameter for that driver

Done.

> grep '\<rt' /etc/modprobe.d/*

```
/etc/modprobe.d/rt2800usb.conf:options rt2800usb nohwcrypt=y
```

> 3. Since your original error logs were DHCP related let's start a with static IP but **making sure that the chosen IP is OUTSIDE the router's DHCP LAN pool** - chili555 suggested **192.168.1.[COLOR=#ff0000]105[/COLOR]** in an earlier post, so let's try that **unless your router's config pages indicate otherwise**.

My pool is 100-120, so I'll take let's say **192.168.1.78**. So my interfaces config file looks like this:
```

#localhost 
auto lo 
iface lo inet loopback 
#wired  
[COLOR=#ff0000]**#**[/COLOR]auto eth0 
iface eth0 inet dhcp 
#WLAN  
auto wlan0 
iface wlan0 inet static 
address **192.168.1.[COLOR=#ff0000]78[/COLOR]** 
netmask 255.255.255.0 
gateway 192.168.1.1 
dns-nameservers 192.168.1.1
wpa-ssid DeKinderWIFI 
wpa-psk <MyPSK(too long for typing :))> 
```

> 
4. Finally, make sure your wired interface isn't coming up automatically  by commenting out the 'auto eth0' line. You can always bring it up  manually with 'sudo ifup eth0' if wlan0 doesn't come up and you want to  ssh in and pull the logs.

i.e. as per chili555's post

Done.

> sudo shutdown -r now

Testing...
Ping gateway = OK (JEEEEJ :))
Ping google.com = NOK :mad:
Ping IP address google.com = OK (JEEEEJ :smile:)

I changed the wlan0 interface to work with DHCP.
Ping google.com = OK (JEEEEJ :smile:)


I changed my router settings back to B/G/N mixed.
Ping google.com = OK (JEEEEJ :smile:)


So I guess I just ****** up the server by trying different things before contacting you guys. 


One other thing:

After changing my routers band to B/G/N mixed I noticed the pings were very slow. (1011ms)
I started ping google.com and changed it back to B/G mixed, and noticed that the speed dramaticly changed. (21ms)

Next week I'm getting my new network in my new home. 
I hope I can just change the wpa-psk and the wpa-ssid. I only have to look not to activate the N band.

THANK YOU, you guys are awesome!!

---

### Post by steeldriver on 2013-04-22
Progress! That's great.

IMHO you *will* have issues if you allow N on the router (i.e. even B/G/N mixed) - if N is available, rt2800usb seems to try to use it - and then falls on its face. Maybe later kernel modules will fix that in which case you could try one of the backports.

---

