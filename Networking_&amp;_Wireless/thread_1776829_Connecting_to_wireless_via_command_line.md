---
title: "Connecting to wireless via command line"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by dagoss on 2011-06-06
I want to connect to the internet using the command line. I'm 95% I have my wireless card installed correctly, since I'm using it right now. Here's what I'm doing

```

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "THOMSON 3" key "123456789"
sudo dhclient wlan0

```

dhclient takes a minute or two, then finishes. It gives no output, success or failure. Then I open up Firefox and I'm not connected to the internet. What can I do to figure out what the problem is?

---

### Post by dagoss on 2011-06-07
Is it possible that there's another network manager or something running in Kubuntu that is interfering? I tried passing the channel to iwconfig but that didn't help.

Does dhclient have a log somewhere or something? It doesn't give me ANY output, error or success, so I don't have a clue why this isn't working.

---

### Post by chili555 on 2011-06-07
> Is it possible that there's another network manager or something running in Kubuntu that is interfering? Not possible, but very probable. Is Network Manager running? I suspect so, because:> I have my wireless card installed correctly, since I'm using it right now. How are you using it? Did you click the icon, select your network and connect? Then Network Manager is installed and running. You are very unlikely to over-power NM with manual methods such as iwconfig and dhclient. It's like four hands on the steering wheel. You are unlikely to get where you are going easily or maybe at all.

Now, you might mess around with nm-settings and try to stop NM and try to connect, but the chances are still slight. In short, either use NM and be happy or remove NM altogether and populate /etc/network/interfaces and use manual methods entirely and be happy. I have two laptops, one with NM and one using manual methods; either works perfectly for me.

---

### Post by dagoss on 2011-06-07
I uninstalled network-manager-kde (I have kubuntu installed). Nothing changed; dhclient wlan0 still gives no output and I'm not connected (posting this using another device.)

Here is my /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

```

What I doing wrong? I see no reason why I shouldn't be online.

I could use a network manager, but I want to learn and understand how to do it manually; if I could just run a bash script to connect, I'd prefer that to a gui newrok manager.

---

### Post by chili555 on 2011-06-07
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
```Your interfaces file needs to declare the ESSID and any encryption details. For example:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid myrouter
wireless-key 0123456789
```WPA is a bit different. Then do:```
sudo ifdown wlan0 && sudo ifup wlan0
```Note any errors or messages and post them here.

---

### Post by dagoss on 2011-06-07
sudo ifdown wlan0 && sudo ifup wlan0

That gives me no output, just like before. It does nothing for about a minute, then returns me to a bash prompt. I ping google and get nothing. Below is my /etc/network/interfaces. I'm wondering if kubuntu had something other than network-manager-kde that begins at startup that is interfering with this that I don't know about.

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid "THOMSON 3"
wireless-key 12a345b67c

```

---

### Post by chili555 on 2011-06-08
You could do:

#Open Synaptic package manager and search for network. Remove any suspicious candidates. If in the very slightest doubt, stop and ask here.

#Open a terminal and do:```
ps aux | grep -i network
```Anything interesting?

#Open a terminal and do:```
sudo tail -f /var/log/syslog
```Leaving that terminal open, start another one and do:```
sudo ifdown -v wlan0 && sudo ifup -v wlan0
```Watch the syslog terminal for interesting clues. When you are done, close the syslog terminal with Ctrl+c.

Are you quite certain your wireless interface is wlan0 and not wlan1 or eth1 or ra0 or some such?```
iwconfig
ifconfig
```Are there any interesting messages when you do:```
sudo /etc/init.d/networking restart
```

---

### Post by dagoss on 2011-06-08
I checked in my package manager and everything network-y seems to be gone.

> #Open a terminal and do:
```

ps aux | grep -i network
```
Anything interesting?
This is what I get:
```

dagoss    5015  0.0  0.0  10552  1072 pts/2    S+   18:18   0:00 grep --color=auto -i network

```

> 
#Open a terminal and do:
Code:
sudo tail -f /var/log/syslog
Leaving that terminal open, start another one and do:
Code:
sudo ifdown -v wlan0 && sudo ifup -v wlan0
Watch the syslog terminal for interesting clues. When you are done, close the syslog terminal with Ctrl+c.

This is the output I get:

```

Jun  8 18:22:26 MAGIC-PORT dhclient: can't create /var/lib/dhcp3/dhclient.wlan0.leases: No such file or directory
Jun  8 18:22:26 MAGIC-PORT avahi-daemon[765]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun  8 18:22:26 MAGIC-PORT avahi-daemon[765]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.60.
Jun  8 18:22:26 MAGIC-PORT avahi-daemon[765]: Withdrawing address record for 169.254.7.60 on wlan0.
Jun  8 18:22:26 MAGIC-PORT avahi-autoipd(wlan0)[3923]: SIOCSIFFLAGS failed: Permission denied
Jun  8 18:22:26 MAGIC-PORT avahi-autoipd(wlan0)[3923]: Callout STOP, address 169.254.7.60 on interface wlan0
Jun  8 18:22:26 MAGIC-PORT avahi-autoipd(wlan0)[3924]: client: RTNETLINK answers: No such process
Jun  8 18:22:26 MAGIC-PORT dhclient: can't create /var/lib/dhcp3/dhclient.wlan0.leases: No such file or directory
Jun  8 18:22:26 MAGIC-PORT kernel: [ 1560.947932] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  8 18:22:26 MAGIC-PORT dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  8 18:22:41 MAGIC-PORT dhclient: last message repeated 4 times
Jun  8 18:22:41 MAGIC-PORT dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jun  8 18:22:47 MAGIC-PORT dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jun  8 18:22:58 MAGIC-PORT dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jun  8 18:23:07 MAGIC-PORT dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jun  8 18:23:15 MAGIC-PORT dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jun  8 18:23:27 MAGIC-PORT dhclient: No DHCPOFFERS received.
Jun  8 18:23:27 MAGIC-PORT dhclient: No working leases in persistent database - sleeping.
Jun  8 18:23:27 MAGIC-PORT avahi-autoipd(wlan0)[5628]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 109).
Jun  8 18:23:27 MAGIC-PORT avahi-autoipd(wlan0)[5628]: Successfully called chroot().
Jun  8 18:23:27 MAGIC-PORT avahi-autoipd(wlan0)[5628]: Successfully dropped root privileges.
Jun  8 18:23:27 MAGIC-PORT avahi-autoipd(wlan0)[5628]: Starting with address 169.254.7.60
Jun  8 18:23:32 MAGIC-PORT avahi-autoipd(wlan0)[5628]: Callout BIND, address 169.254.7.60 on interface wlan0
Jun  8 18:23:32 MAGIC-PORT avahi-daemon[765]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.60.
Jun  8 18:23:32 MAGIC-PORT avahi-daemon[765]: New relevant interface wlan0.IPv4 for mDNS.
Jun  8 18:23:32 MAGIC-PORT avahi-daemon[765]: Registering new address record for 169.254.7.60 on wlan0.IPv4.
Jun  8 18:23:36 MAGIC-PORT avahi-autoipd(wlan0)[5628]: Successfully claimed IP address 169.254.7.60
Jun  8 18:23:36 MAGIC-PORT ntpdate[5678]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jun  8 18:23:36 MAGIC-PORT ntpdate[5678]: no servers can be used, exiting

```

---

### Post by chili555 on 2011-06-08
Here are interesting messages:> dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
dhclient: No DHCPOFFERS received.
dhclient: No working leases in persistent database - sleeping.It shows that dhclient is trying to connect appropriately. It doesn't get an IP address from the router, but it tries as expected. I haven't a clue why nothing shows up in the terminal when you ifup wlan0. That would be expected if NM were running, but it appears not to be the case.

Let's check your settings. May we see:```
route -n
sudo iwlist wlan0 scan
```Thanks.

---

### Post by dagoss on 2011-06-08
Here they are. My wifi connection is THOMSON 3; the others are neighbors.

```


dagoss@MAGIC-PORT:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     1003   0        0 wlan0
dagoss@MAGIC-PORT:~$ sudo iwlist wlan0 scan
[sudo] password for dagoss: 
wlan0     Scan completed :
          Cell 01 - Address: E0:91:F5:CA:AA:C8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a012528f46
                    Extra: Last beacon: 3240ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7F0050F204104A0001101044000101103B0001031047001000000000000010000000E091F5CAAAC8102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F20400011011001B574E5232303030763328576972656C6573732041502D322E344729100800020086103C000103
          Cell 02 - Address: 00:13:46:1B:7A:B6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"TheDezRez"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007357409181
                    Extra: Last beacon: 3230ms ago
                    IE: Unknown: 000954686544657A52657A
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 03 - Address: 00:18:39:CE:7F:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e1b800518a
                    Extra: Last beacon: 3160ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:11:E3:42:9C:97
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"THOMSON 3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006d978fa07f
                    Extra: Last beacon: 3130ms ago
                    IE: Unknown: 000954484F4D534F4E2033
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020100
          Cell 05 - Address: 00:12:17:1C:6B:56
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000034270bdfe32
                    Extra: Last beacon: 3160ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000

dagoss@MAGIC-PORT:~$ 

```

By the way, thank you so much for all the help that you've given already.

---

### Post by chili555 on 2011-06-10
Sorry for the delay in replying. Sometimes a problem keeps me awake at night. Really.> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid "THOMSON 3"
wireless-key 12a345b67cI assume you disguised your WEP key; if not please change it at once so your security is not compromised.

I can only come up with a few thoughts.

Make sure the key in the router has 10 or 26 hex characters; not 9 or 22, etc. Make sure you are putting in the correct key in /etc/network/interfaces. I had better luck, when I used WEP, with capital letters, e.g. 12A345B67C. Try both. There are two modes of WEP, open and shared; shared is known in Linux-land as restricted. Off topic, but I have read the description several times and still don't really understand the difference.

If your network is set to WEP-shared as seen in the attached, your interfaces file should be:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid "THOMSON 3"
wireless-key 12a345b67c restricted
```Finally, I wonder if you'd have better luck with an ESSID without a space in the name, such as THOMPSON3.

---

### Post by dagoss on 2011-06-12
It is a shared key. I tried adding "restricted" to interfaces, but that didn't do anything. However, I used iwconfig and put restricted with me key, and when I called dhclient it worked.

Thank you so much for all your help. I mighty appreciate it!

---

### Post by chili555 on 2011-06-12
Awesome! I'm glad it's working.

---

### Post by superduperlinuxperson on 2011-06-12
try this:
iwconfig wlan0 ap (what ever your ap mac address is)
iwconfig wlan0 essid (name of your router)
iwconfig wlan0 key: passphrase
dhclient wlan0

---

### Post by chili555 on 2011-06-12
> **superduperlinuxperson said:**
> try this:
iwconfig wlan0 ap (what ever your ap mac address is)
iwconfig wlan0 essid (name of your router)
[COLOR="Red"]iwconfig wlan0 key: passphrase[/COLOR]
dhclient wlan0This is from *man iwconfig*:>  key/enc[ryption]
              Used to manipulate encryption or scrambling keys and security mode. To set the current encryption key, just enter the key in hex digits  as  XXXX-XXXX-XXXX-XXXX  or XXXXXXXX.  To set a key other than the current key, prepend or append [index] to the key itself (this won't change which is the active key). You can also enter  the  key  as an ASCII string by using the s: prefix. [COLOR="Red"]Passphrase is currently not supported.[/COLOR]I think you probably meant:```
[COLOR="Red"]sudo[/COLOR] iwconfig wlan0 key myhexkey
```

---

### Post by superduperlinuxperson on 2011-06-12
@chili555
sorry forgot about that

---

