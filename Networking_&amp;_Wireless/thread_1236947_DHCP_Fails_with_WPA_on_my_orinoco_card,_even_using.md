---
title: "DHCP Fails with WPA on my orinoco card, even using wicd and updating the firmware"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by edheil on 2009-08-10
I'll try to tell the story from the beginning.  I'm trying to rehabilitate an older computer, a Toshiba Satellite 1200-S121.  Its wifi card was detected automatically, as one of these:

ed@toshi:~$ pccardctl ident
Socket 0:
  product info: "TOSHIBA", "Wireless LAN Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)


I wanted to use it with my home network which I'm required to have WPA on because I use it for work.  I read that network manager would not do the job, so I switched to wicd, using first the version in Jaunty's repositories and then the version from the wicd team's repository.  I also read that you needed updated firmware to make this wifi card work with WPA, so I downloaded the "agere_sta_fw.bin" firmware, made sure it was the correct length (not corrupted by gitweb), and put it in /lib/firmware, and dmesg told me that it had in fact loaded Lucent/Agere version 9.28 and "WPA-PSK" was suported.

I confirmed that I could connect to my home network with encryption turned off, then turned it back on again, and connected, with wicd.

And it worked!  It worked great.

And the next day it stopped working.  And I don't think I changed anything.

Specifically what stopped working was DHCP.  wicd hung on "obtaining an IP address."

Hoping to get more information I tried to suss out a way of connecting via the command line, and learned about wpa-suppliant and such.  I concocted a wpa-suppliant.conf that gave me some very encouraging looking output, talking about connecting successfully.... (now I've lost the successful wpa-suppliant.conf and can't figure out what I had.  Dang.)  Anyway, even then I would run dhclient and fail to get an IP address.

Any clues on where to start here?

I'll post all the extra debug info y'all like on request, I just thought maybe I could focus the discussion a little by describing the situation so maybe there would be specific debug info that would be useful rather than spamming you with every possible piece of info at the beginning.

---

### Post by NiteFalll on 2009-10-07
I wish I could give you a good answer for this issue. 
I have a satellite 1955-S803 with a built-in orinoco card 
and it's giving me problems as well.

So first yes, my transmit button is turned on.
I checked to make sure the driver is loaded:

```

nitefalll@toshiba:~$ lsmod | grep orinoco
orinoco_cs             21004  1 
orinoco                61716  1 orinoco_cs
hermes_dld             15232  1 orinoco
hermes                 15360  3 orinoco_cs,orinoco,hermes_dld
pcmcia                 44748  1 orinoco_cs
pcmcia_core            43540  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

```I checked it in dmesg to see if anything got twisted
```

[   15.651616] eth1: Hardware identity 0005:0004:0005:0000
[   15.651735] eth1: Station identity  001f:0001:0008:000a
[   15.651739] eth1: Firmware determined as Lucent/Agere 8.10
[   15.651746] eth1: Attempting to download firmware agere_sta_fw.bin
[   15.652779] eth1: Read PDA returned 0
[   15.694880] eth1: Cannot find firmware agere_sta_fw.bin
[   15.694945] eth1: Hardware identity 0005:0004:0005:0000
[   15.695048] eth1: Station identity  001f:0001:0008:000a
[   15.695052] eth1: Firmware determined as Lucent/Agere 8.10
[   15.695055] eth1: Ad-hoc demo mode supported
[   15.695057] eth1: IEEE standard IBSS ad-hoc mode supported
[   15.695059] eth1: WEP supported, 104-bit key
[   15.695148] eth1: MAC address 00:02:2d:6e:4c:a4
[   15.695246] eth1: Station name "HERMES I"
[   15.695809] eth1: ready
[   15.696663] eth1: orinoco_cs at 0.0, irq 5, io 0x3100-0x313f
[   15.722009] udev: renamed network interface eth1 to eth2

```Ok I'm not sure what that udev swap was about but it looked like ubuntu found it ok. I can use eth2 no problem.

```

# pccardctl ident
Socket 0:
  product info: "TOSHIBA", "Wireless LAN Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

```Almost ready to try it.
next lets find a AP

```

# iwlist eth2 scan
eth2      Interface doesn't support scanning : Network is down

# ifconfig eth2 192.168.2.10 netmask 255.255.255.0 broadcast 192.168.2.255 up

# iwlist eth2 scan
eth2      Scan completed :
          Cell 01 - Address: 00:10:10:10:10:ha #not my real mac
                    ESSID:"GreyMusic"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:-57 dBm  Noise level:-95 dBm
                    Encryption key:on
                    Extra:bcn_int=100
                    Extra:capab=0x0431
                    Extra: Last beacon: 144ms ago
          Cell 02 - Address: 00:33.44.55.66.77
                    ESSID:"Belkin 2009"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:-79 dBm  Noise level:-95 dBm
                    Encryption key:on
                    Extra:bcn_int=100
                    Extra:capab=0x0411
                    Extra: Last beacon: 144ms ago


```so I manually had to set the IP before it would scan but hey scanning is good and those are 2 cells in my area. I'm supposed to be using the GreyMusic one. Thats me so lets ping it first: I know that I know the IP of that GreyMusic is 192.168.2.1

```

# iwpriv eth2
eth2      Available private ioctls :
          force_reset      (8BE0) : set   0       & get   0      
          card_reset       (8BE1) : set   0       & get   0      
          set_port3        (8BE2) : set   1 int   & get   0      
          get_port3        (8BE3) : set   0       & get   1 int  
          set_preamble     (8BE4) : set   1 int   & get   0      
          get_preamble     (8BE5) : set   0       & get   1 int  
          set_ibssport     (8BE6) : set   1 int   & get   0      
          get_ibssport     (8BE7) : set   0       & get   1 int  
          get_rid          (8BE9) : set   0       & get 1024 byte 
# iwconfig eth2
eth2      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth2
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
# route add default gw 192.168.2.1 dev eth2
# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth2
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth2
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
# route del default gw 192.168.1.1
# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth2
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth2

```I just switched the default route to the wireless card. 
Now lets see if we can ping one hop away.
```

# ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.10 icmp_seq=2 Destination Host Unreachable
From 192.168.2.10 icmp_seq=3 Destination Host Unreachable
From 192.168.2.10 icmp_seq=5 Destination Host Unreachable
From 192.168.2.10 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.2.1 ping statistics ---
8 packets transmitted, 0 received, +4 errors, 100% packet loss, time 7040ms
, pipe 2
# ping 192.168.2.196
PING 192.168.2.196 (192.168.2.196) 56(84) bytes of data.
From 192.168.2.10 icmp_seq=1 Destination Host Unreachable
From 192.168.2.10 icmp_seq=2 Destination Host Unreachable
From 192.168.2.10 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.2.196 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4024ms
, pipe 3

```so at this point I'm stumpted. 
I don't know how to get that driver working on this Satelite 1955-S803 laptop. 
It would have made an ideal network troubleshooting box for me.

sorry I couldn't help more but this may give you a few commands to try.

---

