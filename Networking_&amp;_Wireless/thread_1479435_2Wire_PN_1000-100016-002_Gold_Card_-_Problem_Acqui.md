---
title: "2Wire P/N 1000-100016-002 Gold Card - Problem Acquiring IP Address"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by sacredfaith on 2010-05-10
Howdy, 

Perhaps someone could help me, I've tried quite a few routes here and  I'm near the conclusion that my card isn't going to cooperate. While  Ubuntu recognizes the card, the EESID, and even assigns a 'working'  driver...I cannot obtain an IP address. Here we go:

System:
Laptop - Dell Latitude C840
Wireless Card - 2Wire 802.11b Wireless PCMCIA Gold 1000-100016-002
Ubuntu Lucid 

System Monitor
Intel P4 Mobile 1.6 Ghz
497.3 MB RAM 


lshw
```

 *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:ad:8d:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b

```

iwconfig output:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```...okay, so then I proceeded to scan...

```

eth1      Scan completed :
          Cell 01 - Address: 00:1E:58:25:2C:33
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"The Icy Black Hand Of DeathNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003327e0a5420
                    Extra: Last beacon: 244ms ago
                    IE: Unknown:  001E5468652049637920426C61636B2048616E64204F662044656174684E6574
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

```So it can see my network "The Icy Black Hand of DeathNet" :)

...so at this point I was a bit confused - when the system would start  it would ask me for the key, I'd put it in, and....nothing. To post  this, I had to connect it through a wired connection. After a little more searching I tried disconnecting from the wired connection, and monitoring the /var/log/message output...this shows the disconnect, the ejection, and the reinsertion of the card

```

 sacredfaith@Jehova-Jireh:/etc/network$ tail -f /var/log/messages
May 10 15:56:29 Jehova-Jireh kernel: [  916.121651] orinoco_cs 1.0: Hardware identity 0001:0004:0005:0000
May 10 15:56:29 Jehova-Jireh kernel: [  916.121777] orinoco_cs 1.0: Station identity  001f:0002:0009:0030
May 10 15:56:29 Jehova-Jireh kernel: [  916.121785] orinoco_cs 1.0: Firmware determined as Lucent/Agere 9.48
May 10 15:56:29 Jehova-Jireh kernel: [  916.121790] orinoco_cs 1.0: Ad-hoc demo mode supported
May 10 15:56:29 Jehova-Jireh kernel: [  916.121795] orinoco_cs 1.0: IEEE standard IBSS ad-hoc mode supported
May 10 15:56:29 Jehova-Jireh kernel: [  916.121800] orinoco_cs 1.0: WEP supported, 104-bit key
May 10 15:56:29 Jehova-Jireh kernel: [  916.121804] orinoco_cs 1.0: WPA-PSK supported
May 10 15:56:29 Jehova-Jireh kernel: [  916.184123] ADDRCONF(NETDEV_UP): eth1: link is not ready
May 10 16:00:51 Jehova-Jireh sudo: pam_sm_authenticate: Called
May 10 16:00:51 Jehova-Jireh sudo: pam_sm_authenticate: username = [sacredfaith]
May 10 16:20:05 Jehova-Jireh kernel: [ 2332.000912] pcmcia_socket pcmcia_socket1: pccard: card ejected from slot 1
May 10 16:20:05 Jehova-Jireh kernel: [ 2332.001291] hermes @ 0001e100: Card removed while issuing command 0x0002.
May 10 16:20:05 Jehova-Jireh kernel: [ 2332.001299] eth1: Error -19 disabling MAC port
May 10 16:20:13 Jehova-Jireh kernel: [ 2339.848090] pcmcia_socket pcmcia_socket1: pccard: PCMCIA card inserted into slot 1
May 10 16:20:13 Jehova-Jireh kernel: [ 2339.848439] pcmcia 1.0: pcmcia: registering new device pcmcia1.0
May 10 16:20:13 Jehova-Jireh kernel: [ 2339.931315] orinoco_cs 1.0: Hardware identity 0001:0004:0005:0000
May 10 16:20:13 Jehova-Jireh kernel: [ 2339.931443] orinoco_cs 1.0: Station identity  001f:0001:0008:002a
May 10 16:20:13 Jehova-Jireh kernel: [ 2339.931452] orinoco_cs 1.0: Firmware determined as Lucent/Agere 8.42
May 10 16:20:13 Jehova-Jireh kernel: [ 2339.947064] orinoco_cs 1.0: firmware: requesting agere_sta_fw.bin
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051062] orinoco_cs 1.0: Hardware identity 0001:0004:0005:0000
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051188] orinoco_cs 1.0: Station identity  001f:0002:0009:0030
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051195] orinoco_cs 1.0: Firmware determined as Lucent/Agere 9.48
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051201] orinoco_cs 1.0: Ad-hoc demo mode supported
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051205] orinoco_cs 1.0: IEEE standard IBSS ad-hoc mode supported
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051210] orinoco_cs 1.0: WEP supported, 104-bit key
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051215] orinoco_cs 1.0: WPA-PSK supported
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.106257] ADDRCONF(NETDEV_UP): eth1: link is not ready

```What is perhaps more interesting is watching the error that results when I'm trying to connect to the network:

```

sacredfaith@Jehova-Jireh:/etc/network$ tail -f /var/log/messages
May 10 16:20:13 Jehova-Jireh kernel: [ 2339.947064] orinoco_cs 1.0: firmware: requesting agere_sta_fw.bin
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051062] orinoco_cs 1.0: Hardware identity 0001:0004:0005:0000
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051188] orinoco_cs 1.0: Station identity  001f:0002:0009:0030
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051195] orinoco_cs 1.0: Firmware determined as Lucent/Agere 9.48
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051201] orinoco_cs 1.0: Ad-hoc demo mode supported
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051205] orinoco_cs 1.0: IEEE standard IBSS ad-hoc mode supported
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051210] orinoco_cs 1.0: WEP supported, 104-bit key
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.051215] orinoco_cs 1.0: WPA-PSK supported
May 10 16:20:13 Jehova-Jireh kernel: [ 2340.106257] ADDRCONF(NETDEV_UP): eth1: link is not ready
May 10 16:21:53 Jehova-Jireh kernel: [ 2440.313377] eth1: Lucent/Agere firmware doesn't support manual roaming
May 10 16:21:59 Jehova-Jireh kernel: [ 2445.792059] eth1: Lucent/Agere firmware doesn't support manual roaming
May 10 16:22:04 Jehova-Jireh kernel: [ 2451.242410] eth1: Lucent/Agere firmware doesn't support manual roaming
May 10 16:22:09 Jehova-Jireh kernel: [ 2456.697408] eth1: Lucent/Agere firmware doesn't support manual roaming
May 10 16:22:15 Jehova-Jireh kernel: [ 2462.158244] eth1: Lucent/Agere firmware doesn't support manual roaming
May 10 16:22:20 Jehova-Jireh kernel: [ 2467.635211] eth1: Lucent/Agere firmware doesn't support manual roaming

```So, after doing the most brilliant thing I could (Google) I came up with running dhclient...

```

Listening on LPF/eth1/00:02:2d:ad:8d:44
Sending on   LPF/eth1/00:02:2d:ad:8d:44
Listening on LPF/eth0/00:06:5b:b8:fc:61
Sending on   LPF/eth0/00:06:5b:b8:fc:61
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.0.195 from 192.168.0.1
DHCPREQUEST of 192.168.0.195 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.195 from 192.168.0.1
bound to 192.168.0.195 -- renewal in 34294 seconds.

```Which resulted in bumpkis, to use the phrase coined by Adam on Mythbusters...*sigh*

SO then I decided that I should abandon the orinoco driver...so I downloaded the corresponding Windows XP driver and installed it successfully using ndiswrapper (which involved blacklisting the hermes, orinoco, orinoco_cs, orinoco_plx, etc). Nothing. So I have since commented out the blacklist, uninstalled the WinXP driver - and have reverted back to the orinoco driver (just because I felt a lot closer to victory). 

ANY help at all would be MUCH appreciated!!!

Kind Regards,

sf

---

### Post by chili555 on 2010-05-10
May I please see:```
sudo iwlist eth1 auth
```








hint to chili: WPA or WPA2??

---

### Post by sacredfaith on 2010-05-10
certainly

```

eth1      Authentication capabilities :
        WPA
        CIPHER-TKIP
          Current Key management :
        PSK
          Current TKIP countermeasures : no
          Current Authentication algorithm :
        open


```

---

### Post by chili555 on 2010-05-10
It looks like your access point or router is set for WPA2 but your card is only capable of WPA. If it did WPA2, it would report:> $ sudo iwlist wlan0 auth
[sudo] password for chili: 
wlan0     Authentication capabilities :
		WPA
		[COLOR="Blue"]WPA2[/COLOR]
		CIPHER-TKIP
		CIPHER-CCMPI suggest you change the encryption in the router to WPA.

---

### Post by sacredfaith on 2010-05-10
Thank you so much for the responses!! Good to know someone out there cares! 

So a router can only broadcast one type of encryption at a time? I apologize if this seems like an elementary question. I'm just a little confused by the "WPA Version 1" that appears in my iwlist eth1 scan.

---

### Post by chili555 on 2010-05-10
> So a router can only broadcast one type of encryption at a time? So I thought. I am a bit confused, too. Can you get into the administrative pages of the router and see if it's set up as WPA *OR* WPA2 or, possibly WPA *AND* WPA2? I will be fascinated to hear which it is.

For comparison, my scan says:> Scan completed :
          Cell 01 - Address: 99:24:56:88:D7:44
                    ESSID:"mylilrouter"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-51 dBm  
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2[/COLOR] Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 76ms agoAnd my auth says:> eth1      Authentication capabilities :
		WPA
		[COLOR="Red"]WPA2[/COLOR]
		CIPHER-TKIP
		CIPHER-CCMP
--- snip ---

---

### Post by sacredfaith on 2010-05-11
chili, thank you so much for your willingness to help with this!

>            I suggest you change the encryption in the router to WPA.This was a great idea. Thanks! However, I still get the "Lucent/Agere firmware..." error message. I tried this even with WPA-TKIP settings.

>  Can you get into the administrative pages of the router and see if it's set up as WPA *OR* WPA2 or, possibly WPA *AND* WPA2?Certainly. See attached. From the looks of things it does appear to have the capability to do both simultaneously. As of the first screenshot, it's only set to do WPA-TKIP (per the previous experiment). 

I suppose this helps understand the iwlist output:
```

IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

```Incidentally...
The router is a D-Link DIR-655, firmware v 1.11, hardware version A3

Kind Regards,

sf

---

### Post by chili555 on 2010-05-11
Are the hostap suite of drivers installed on your system? Are they blacklisted?```
sudo updatedb
locate hostap_cs.ko
cat /etc/modprobe.d/blacklist.conf | grep host
lsmod | grep host 
```This may be Plan B.

---

### Post by sacredfaith on 2010-05-13
Hmm....

```

sacredfaith@Jehova-Jireh:~$ sudo updatedb
[sudo] password for sacredfaith: 
sacredfaith@Jehova-Jireh:~$ locate hostap_cs.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/hostap/hostap_cs.ko
/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/hostap/hostap_cs.ko
sacredfaith@Jehova-Jireh:~$ cat /etc/modprobe.d/blacklist.conf | grep host
sacredfaith@Jehova-Jireh:~$ lsmod | grep host
sacredfaith@Jehova-Jireh:~$ 

```

---

### Post by chili555 on 2010-05-13
Let's see if we can get the hostap driver to work. This will be a temporary fix. If it works, we will tweak a few things. In a terminal, do:```
sudo rmmod -f orinoco orinoco_cs
sudo modprobe hostap_cs
iwconfig
```Was a wireless interface created? Please post:```
lspci -nn
```I would like to see the data related to your card. You can skip all the unrelated data.

---

### Post by sacredfaith on 2010-05-13
```

sacredfaith@Jehova-Jireh:~$ lspci -m
00:00.0 "Host bridge" "Intel Corporation" "82845 845 [Brookdale] Chipset Host Bridge" -r04 "" ""
00:01.0 "PCI bridge" "Intel Corporation" "82845 845 [Brookdale] Chipset AGP Bridge" -r04 "" ""
00:1e.0 "PCI bridge" "Intel Corporation" "82801 Mobile PCI Bridge" -r42 "" ""
00:1f.0 "ISA bridge" "Intel Corporation" "82801CAM ISA Bridge (LPC)" -r02 "" ""
00:1f.6 "Modem" "Intel Corporation" "82801CA/CAM AC'97 Modem Controller" -r02 "PCTel Inc" "Device 4c21"
02:00.0 "Ethernet controller" "3Com Corporation" "3c905C-TX/TX-M [Tornado]" -r78 "Dell" "Device 00d4"
02:01.0 "CardBus bridge" "Texas Instruments" "PCI4451 PC card Cardbus Controller" "Dell" "Device 00d5"
02:01.1 "CardBus bridge" "Texas Instruments" "PCI4451 PC card Cardbus Controller" "Dell" "Device 00d5"

```

Okay, I took out everything that obviously wasn't it... I think it's one of the last two, but it doesn't seem to be identifying the card itself.

Just for completeness...I checked to make sure the orinoco_cs driver was getting removed...

```
sacredfaith@Jehova-Jireh:~$ tail -f /var/log/messages
May 13 15:05:05 Jehova-Jireh kernel: [ 3230.756742] orinoco_cs 1.0: Station identity  001f:0002:0009:0030
May 13 15:05:05 Jehova-Jireh kernel: [ 3230.756753] orinoco_cs 1.0: Firmware determined as Lucent/Agere 9.48
May 13 15:05:05 Jehova-Jireh kernel: [ 3230.756760] orinoco_cs 1.0: Ad-hoc demo mode supported
May 13 15:05:05 Jehova-Jireh kernel: [ 3230.756765] orinoco_cs 1.0: IEEE standard IBSS ad-hoc mode supported
May 13 15:05:05 Jehova-Jireh kernel: [ 3230.756772] orinoco_cs 1.0: WEP supported, 104-bit key
May 13 15:05:05 Jehova-Jireh kernel: [ 3230.756777] orinoco_cs 1.0: WPA-PSK supported
May 13 15:05:05 Jehova-Jireh kernel: [ 3231.506743] ADDRCONF(NETDEV_UP): eth1: link is not ready
May 13 15:05:23 Jehova-Jireh sudo: pam_sm_authenticate: Called
May 13 15:05:23 Jehova-Jireh sudo: pam_sm_authenticate: username = [sacredfaith]
May 13 15:06:06 Jehova-Jireh kernel: [ 3292.485347] lib80211: common routines for IEEE802.11 drivers
^C
sacredfaith@Jehova-Jireh:~$ rmmod orinoco_cs
ERROR: Module orinoco_cs is in use
sacredfaith@Jehova-Jireh:~$ sudo rmmod orinoco_cs orinoco
ERROR: Module orinoco_cs is in use
ERROR: Module orinoco is in use by orinoco_cs

```

If sudo can't do it...I'm at a loss.

---

### Post by chili555 on 2010-05-13
Is it a PCMCIA card? Let's try:```
pccardctl ident
```> If sudo can't do it...I'm at a loss.Let's use the **force** argument:```
sudo rmmod [COLOR="Red"]-f[/COLOR] orinoco orinoco_cs

```Thanks.

---

### Post by sacredfaith on 2010-05-18
Sorry for taking so long to reply. You've been most helpful!!! 

So here are the results from a bit of backtracking and the bit of forward tracking that you suggested...


```

sacredfaith@Jehova-Jireh:~$ pccardctl ident
Socket 0:
  no product info available
Socket 1:
  product info: "2Wire", "Wireless PC Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)
sacredfaith@Jehova-Jireh:~$ sudo rmmod -f orinoco orinoco_cs
[sudo] password for sacredfaith: 
ERROR: Removing 'orinoco': Resource temporarily unavailable
ERROR: Removing 'orinoco_cs': Resource temporarily unavailable


```

---

