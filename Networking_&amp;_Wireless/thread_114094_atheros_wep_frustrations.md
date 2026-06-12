---
title: "atheros wep frustrations"
date: 2006-01-07
forum: Networking &amp; Wireless
---

### Post by nrune on 2006-01-07
Sorry folks I have gone through simlar threads trying to get this to work and I just can't Please help.
```

output of lshw
  *-network:1
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: a
                bus info: pci@01:0a.0
                logical name: ath0
                version: 01
                serial: 00:11:f9:fd:XX:XX
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) ip=192.168.1.102 multicast=yes wireless=IEEE 802.11g
                resources: iomemory:cffe0000-cffeffff irq:11
```

```
output of iwconfig
ath0      IEEE 802.11g  ESSID:"brownnet"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:05:C7:XX:XX
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/94  Signal level=-45 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:7

```

i am using an ascii key all numbers. in the Key

Not sure how to proceed. I am going on a trip where the hotel has wep and a number key so I would like to fix this. Thanks in advance.

---

### Post by Lambert on 2006-01-07
How are you setting the key? through the network-admin gui?

Try this

```
sudo iwconfig ath0 essid ____ mode managed  key s:______ commit
```

In your /etc/network/interfaces file your line should look like this

wireless-key s:________

You may need to enter your key so it has a - after every 4 letters

wireless-key s:ever-y4le-tter-s

The s: is what designates it as ascii key.

Another problem that might be is if you're using shared key? If so post back and I'll give you instructions to make the adjustment.

anything else about your wep? do you have a choice to set multiple keys and if so which one?

---

### Post by nrune on 2006-01-08
thanks for your help.

config ath0 essid ____ mode managed  key s:______ commit

results in..> 
nrune@nrune:~$ sudo iwconfig ath0 essid brownnet key s:12345 commit 
commit Error for wireless request "Commit changes" (8B00) :
 SET failed on device ath0 ; Operation not supported.

Access point info: One key. authentation type set to open system. 

Thanks for the help in advance!

---

### Post by nrune on 2006-01-08
After messing with this most of this afternoon, my guess is that the key is not being registered to the card/essid. Not sure how I could go about proving that the key is assigned to the correct essid/card, but that might be helpful with a further debug.

---

### Post by nrune on 2006-01-08
Not sure if this would be helpfull > 

nrune@nrune:~$ sudo iwconfig ath0 essid brownnet key s:12345
nrune@nrune:~$ iwconfig
ath0      IEEE 802.11g  ESSID:"brownnet"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by nrune on 2006-01-11
Uh...bump help?

---

### Post by Scotland on 2006-01-11
[QUOTE=nrune]Uh...bump help?[/QUOTE]

Try,

iwconfig ath0 essid "HOME"
iwconfig ath0 key "10917061D2"
iwconfig ath0 freq 5.18G
iwconfig ath0 channel 36

I have the exact same output as your lshw and I have no problems running above script to set wireless (have 2 scripts, 1 for home, 1 for office).

Dougie.

---

### Post by marcantonio on 2006-01-11
[QUOTE=nrune]thanks for your help.

config ath0 essid ____ mode managed  key s:______ commit

results in..

nrune@nrune:~$ sudo iwconfig ath0 essid brownnet key s:12345 commit
commit Error for wireless request "Commit changes" (8B00) :
SET failed on device ath0 ; Operation not supported.

Access point info: One key. authentation type set to open system. 

Thanks for the help in advance![/QUOTE]

FWIW, I've never been able so use the commit command with any atheros cards.  I would leave the commit off the end of that command and it should set fine.

Also, what is the output of iwconfig *run as root*.  It looks like your running it as a regular user, in which case it will not display the key.

---

### Post by nrune on 2006-01-11
Okay running as root seems to have shed some light on this. 
```
root@nrune:~# iwconfig ath0 key "1234567890" open
root@nrune:~# iwconfig
ath0      IEEE 802.11g  ESSID:"brownnet"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:05:C7:98:28
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:1234-5678-90   Security mode:open
          Power Management:off
          Link Quality=52/94  Signal level=-43 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

```
```
root@nrune:~# iwconfig ath0 key s:"1234567890" open
root@nrune:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"brownnet"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:05:C7:98:28
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3132-3334-3536-3738-3930   Security mode:open
          Power Management:off
          Link Quality=52/94  Signal level=-43 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

```

Okay neither of these configurations work, however I do notice some strange behavior I am using an ascii key with the s: I get this for the key 3132-3334-3536-3738-3930 when using it without the s:1234-5678-90 which is right?  Is the without the s: a hex key?? 

Thanks in advance.

Mike

---

### Post by marcantonio on 2006-01-11
> 
Okay neither of these configurations work, however I do notice some strange behavior I am using an ascii key with the s: I get this for the key 3132-3334-3536-3738-3930 when using it without the s:1234-5678-90 which is right?  Is the without the s: a hex key?? 

Thanks in advance.

Mike

Ok, when you use s:"1234567890" it is setting the key to that string, 1234567890.  The hex you see in the output of iwconfig is the hex representation of this string, i.e. 1 = hex 0x31, 2 = hex 0x32, etc.  So it's right.

When you use "1234567890", without the s:, you are setting the key to the hex value 0x1234567890.  If you throw a non-hex character in there it won't take it.

So if you'e setting your key in ascii on the AP make sure you use s:, if it's in hex, don't.

Also, try this instead:

```
iwconfig ath0 key s:"1234567890" restricted
```

It shouldn't matter, as using open like you did above accepts both encrypted and non-encrypted traffic, but it's worth a try.  Some cards use this differently.

After you do this are you trying DHCP or static?  What happens?

---

### Post by nrune on 2006-01-12
Thanks very much for hanging in there with me. Okay here is the whole thing.

> root@nrune:~# iwconfig ath0 key s:"1234567890" restricted
root@nrune:~# iwconfig
ath0      IEEE 802.11g  ESSID:"brownnet"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:05:C7:xx:xx
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3132-3334-3536-3738-3930   Security mode:restricted
          Power Management:off
          Link Quality=51/94  Signal level=-44 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:7
root@nrune:~# dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 22471
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:11:f9:fd:59:74
Sending on   LPF/ath0/00:11:f9:fd:59:74
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.1.102
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

Running dhcp, will try a static ip and see if that helps

Thanks again
Mike

---

### Post by nrune on 2006-01-12
Okay so I did some checking on the keys  
this ascii "ABCDEFGHIJ"  produced
this Key   4142-4344-4546-4748-494A 
this ascii  ABCDEFGHIJ produced
this key   4142-4344-4546-4748-494A 
this ascii  1234567890 produced 
this key    3132-3334-3536-3738-3930 

I looked up this web page [http://www.csgnetwork.com/wepgeneratorcalc.html](http://www.csgnetwork.com/wepgeneratorcalc.html) and from what I can see the keys are right on the money for what they should be. so then the mystery is why will it not connect? I used a manual ip address   and it still won't work. I am begning to wonder if it is the router that is causing the problems. 

I have usb adapter that I will try with my windows machine to see if I can isolate the router as the problem. 

Thanks!

---

### Post by nrune on 2006-01-12
usb wireless adapter crashed both 98 and xp, so much for that Idea. Found a card with an old prism chipset and ubuntu installed it like a champ, same issues as the atheros card. Wish I had another router to test out. Begining to think that the router is the problem.

Router is a Di 614+

---

### Post by Lambert on 2006-01-12
Can you post the output of this command here. I'm not sure it's your router as it's broadcasting a signal and you can associate with the router it looks like. But it's not authenticating your data transfer so maybe the algorithm is not being sent properly.

```
sudo iwpriv ath0
``` 
This is just to see what options are available, once I see that there will be more output I'll ask for depending on what you post from this command.

---

### Post by nrune on 2006-01-13
here ya go
ath0      Available private ioctls :
          setoptie         (8BE8) : set 256 byte  & get   0
          getoptie         (8BE9) : set   0       & get 256 byte
          setkey           (8BE2) : set  60 byte  & get   0
          delkey           (8BE4) : set   7 byte  & get   0
          setmlme          (8BE6) : set  42 byte  & get   0
          addmac           (8BEA) : set   1 addr  & get   0
          delmac           (8BEC) : set   1 addr  & get   0
          chanlist         (8BEE) : set  32 byte  & get   0
          setparam         (8BE0) : set   2 int   & get   0
          getparam         (8BE1) : set   1 int   & get   1 int
          turbo            (0001) : set   1 int   & get   0
          get_turbo        (0001) : set   0       & get   1 int
          mode             (0002) : set   1 int   & get   0
          get_mode         (0002) : set   0       & get   1 int
          authmode         (0003) : set   1 int   & get   0
          get_authmode     (0003) : set   0       & get   1 int
          protmode         (0004) : set   1 int   & get   0
          get_protmode     (0004) : set   0       & get   1 int
          mcastcipher      (0005) : set   1 int   & get   0
          get_mcastcipher  (0005) : set   0       & get   1 int
          mcastkeylen      (0006) : set   1 int   & get   0
          get_mcastkeylen  (0006) : set   0       & get   1 int
          ucastciphers     (0007) : set   1 int   & get   0
          get_uciphers     (0007) : set   0       & get   1 int
          ucastcipher      (0008) : set   1 int   & get   0
          get_ucastcipher  (0008) : set   0       & get   1 int
          ucastkeylen      (0009) : set   1 int   & get   0
          get_ucastkeylen  (0009) : set   0       & get   1 int
          keymgtalgs       (0015) : set   1 int   & get   0
          get_keymgtalgs   (0015) : set   0       & get   1 int
          rsncaps          (0016) : set   1 int   & get   0
          get_rsncaps      (0016) : set   0       & get   1 int
          roaming          (000C) : set   1 int   & get   0
          get_roaming      (000C) : set   0       & get   1 int
          privacy          (000D) : set   1 int   & get   0
          get_privacy      (000D) : set   0       & get   1 int
          countermeasures  (000E) : set   1 int   & get   0
          get_countermeas  (000E) : set   0       & get   1 int
          dropunencrypted  (000F) : set   1 int   & get   0
          get_dropunencry  (000F) : set   0       & get   1 int
          wpa              (000A) : set   1 int   & get   0
          get_wpa          (000A) : set   0       & get   1 int
          driver_caps      (0010) : set   1 int   & get   0
          get_driver_caps  (0010) : set   0       & get   1 int
          maccmd           (0011) : set   1 int   & get   0
          wme              (0012) : set   1 int   & get   0
          get_wme          (0012) : set   0       & get   1 int
          hide_ssid        (0013) : set   1 int   & get   0
          get_hide_ssid    (0013) : set   0       & get   1 int
          ap_bridge        (0014) : set   1 int   & get   0
          get_ap_bridge    (0014) : set   0       & get   1 int
          inact            (0017) : set   1 int   & get   0
          get_inact        (0017) : set   0       & get   1 int
          inact_auth       (0018) : set   1 int   & get   0
          get_inact_auth   (0018) : set   0       & get   1 int
          inact_init       (0019) : set   1 int   & get   0
          get_inact_init   (0019) : set   0       & get   1 int
          ibss             (001A) : set   1 int   & get   0
          get_ibss         (001A) : set   0       & get   1 int
          pureg            (001B) : set   1 int   & get   0
          get_pureg        (001B) : set   0       & get   1 int
          reset            (0063) : set   1 int   & get   0

---

### Post by Lambert on 2006-01-13
run these and post output

```
 sudo -s
```
enter password then

```
iwpriv ath0 get_authmode
iwpriv ath0 getparam
```

---

### Post by nrune on 2006-01-13
root@nrune:~# iwpriv ath0 get_authmode
ath0      get_authmode:1

root@nrune:~# iwpriv ath0 getparam
The command getparam needs exactly 1 argument(s)...

putting the ath0 last results in
root@nrune:~# iwpriv getparam ath0
getparam  no private ioctls.

Thanks again

---

### Post by Lambert on 2006-01-13
Have you tried  turning off wep or using a hex key instead or using a static ip just to get a connection with the router and verify it can work.

Currently I believe everything is working on the device driver side, what looks to be happening is the router is not authenticating your datagrams and sending you a dhcpoffer.

Have you also tried to reboot the router as sometimes it helps but I will say in doing this, depending on model etc... sometimes settings are lost and router needs to be reconfigured.

---

### Post by nrune on 2006-01-13
I am able to connect with out any wep. In fact I am writting on the unencrypted connection as we talk. I have tried to get it to accept a hex key, but I have never been able to get it to accept a hex key, i allways get an error of some kind. Will try a router reboot, It is an old DI614+ in need of an excuse to replace any way. thanks for everyone's efforts and help.

---

