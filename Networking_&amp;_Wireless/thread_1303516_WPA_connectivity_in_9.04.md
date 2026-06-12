---
title: "WPA connectivity in 9.04"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by a-web on 2009-10-28
I have been able to connect to WEP and non-secure wireless networks fine.  But I am unable to connect to my house mate's WPA wireless.  The password is correct, since I am on a Mac which is currently connected.

Where can I look for help?  (Just let me know what info to provide (and how to get it).)
Thanks.

---

### Post by jward3010 on 2009-10-28
How long is the WPA passphrase, and what type of router is it? The reason I say it is that some wireless routers don't stick to standards in terms of minimum phrase length. WPA passphases have to be at least 8 long, some stupid routers I've come across have accepted less and WORKED! Often a standards compliant OS like Ubuntu won't work with anything less than the 8 character amount. It's a long shot but it's one of those weird ones you have to experience to believe and worth adding to the discussion.

---

### Post by jward3010 on 2009-10-28
Way more obvious to bring up, is your wireless card compatible with WPA. Many old models are not, they don't have the hardware on board to decrypt as WPA security is hardware based. Best thing is find out what your wireless card is using:
```
sudo lshw -C network
```
And search on it.

Check this too: [http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access#Hardware_support](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access#Hardware_support)

---

### Post by a-web on 2009-10-28
The key is 10 characters long, so that isn't the problem.

And below is the outcome of "sudo lshw -C network".  How do I know if it can support WPA?

       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 20
       serial: 00:0c:41:51:36:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8180 driverversion=1.53+Realtek,10/07/2004,5.173.10 ip=192.168.0.46 latency=64 link=yes maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

---

### Post by jward3010 on 2009-10-28
One thing that stands out is "wireless=IEEE 802.11b". It's only "B" compatible and hence an old card, chances are you'll have to do a firmware upgrade or get a newer wireless card. Check this out in fact and check the second paragraph: [http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=5&Level=6&Conn=5&ProdID=37](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=5&Level=6&Conn=5&ProdID=37)

---

### Post by a-web on 2009-10-28
So a newer card should help me out.  Do you have any recommendations?  I am using a Compaq Presario 2100 (with Intel Celeron 2.4 GHz).

Like this should work:
[http://www.buy.com/retail/product.asp?sku=10392991&listingid=54439789#cRevSec](http://www.buy.com/retail/product.asp?sku=10392991&listingid=54439789#cRevSec)

---

### Post by jward3010 on 2009-10-29
I'll let someone else come in on this one. In regards wireless compatibility there's a lot of up and down, mostly up, but a little down every now and then. This may help: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by a-web on 2009-10-31
Upgraded to a WPC54GX v.2 which is supposed to support WPA.  Still no luck.  Any insight?

---

### Post by a-web on 2009-11-01
And my new output of "sudo lshw -C network":

description: Wireless interface
       product: AGN100 802.11 a/b/g True MIMO Wireless Card
       vendor: Airgo Networks Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan2
       version: 03
       serial: 00:16:b6:f2:77:ca
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netani driverversion=1.53+Linksys,02/04/2005, 1.4.4.1 latency=248 maxlatency=255 mingnt=24 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by jward3010 on 2009-11-02
What I'm thinking is more than likely the WPA security thats switched on is WPA2 and that card is not necessarily compatible with it or possibly the security type thats enabled to encapsulate the packets is incompatible, these are called AES and TKIP. So to sum up:

- Possibly you need to enable WPA1 security on the router and retry.
- Possibly you can stay with WPA2 but need to change between AES and TKIP options.

---

### Post by a-web on 2009-11-02
I think you are correct, jward3010.  What does that mean for me?  As in - what can I change on my computer to help make it work... and if nothing, what should be changed on the router?  (Best on my computer first, since it is a neighbor's router who is allowing access.)  Thanks!

Bellow is the output of: sudo iwlist scan

wlan2     Scan completed :
...
          Cell 03 - Address: 00:21:7C:E3:C1:31
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:100/100  Signal level:-17 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

---

### Post by jward3010 on 2009-11-02
Realistically you'll need to change these things on the router as it's the flexible friend at the moment and your card ain't. It will  mean a tiny amount of network disruption, as when you change options it will disconnect other connected machines, until they reconnect.

The best way to do this is leave as much security enabled as possible on the router and keep regressing until you find something that works. 

1. Stay with WPA2 and change the Cipher option to AES (if the options available - technically AES is the newest encryption and possibly leat compatible with an old card but try it anyway).

2. If no luck with this, change to WPA-Personal (or WPA1) (you might be given the option of TKIP and AES, try both). See how you get on here. 

Realistically, WPA1 is still a very safe mode of encryption so leaving it on this setting won't be a big deal in terms of the security of your network.

---

### Post by a-web on 2009-11-02
Haven't talked to the neighbor yet... but did look around on ubuntuforums for similar problems.  And let me give some info.

I edited /etc/wpa_supplicant.conf to contain the following:

ctrl_interface=/var/run/wpa_supplicant

ap_scan=2

network={
    scan_ssid=1
    ssid="2WIRE487"
    proto=WPA2
    key_mgmt=WPA-PSK
    group=TKIP
    psk=(my psk)
}



And now "sudo wpa_supplicant -iwlan2 -Dwext -c /etc/wpa_supplicant.conf" has the following result:

Trying to associate with SSID '2WIRE487'
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with SSID '2WIRE487'
Associated with 00:(correct address)
WPA: Key negotiation completed with 00:(correct address) [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:(correct address) completed (auth) [id=0 id_str=]
Associated with 00:(correct address)
WPA: Key negotiation completed with 00:(correct address) [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:(correct address) completed (reauth) [id=0 id_str=]
... and on and on...

What does this mean?  Am I actually connecting at all?

---

### Post by jward3010 on 2009-11-02
When you (seem) to be connected as above, try in a terminal:
```
ping -c 3 208.67.222.222
```
And see if you get successful replies. Test internet generally as well, through Firefox for example.

Most important, like above, while you're (supposedly) connected above give us the output of:
```
ifconfig -a
```

I recommend you put that above info in "code" tags, it get rids of those unintentional smilies.

---

### Post by a-web on 2009-11-03
Here's some output - hopefully in code boxes:
(Trying Firefox I get nothing.)

```
ping -c 3 208.67.222.222

PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
From 169.254.10.39 icmp_seq=1 Destination Host Unreachable
From 169.254.10.39 icmp_seq=2 Destination Host Unreachable
From 169.254.10.39 icmp_seq=3 Destination Host Unreachable

--- 208.67.222.222 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3
``````
 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:85:f5:dc  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1318 (1.3 KB)  TX bytes:1318 (1.3 KB)

wlan2     Link encap:Ethernet  HWaddr 00:16:b6:f2:77:ca  
          inet6 addr: fe80::216:b6ff:fef2:77ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5833 (5.8 KB)  TX bytes:5296 (5.2 KB)
          Interrupt:11 Memory:34000000-34080000 

wlan2:avahi Link encap:Ethernet  HWaddr 00:16:b6:f2:77:ca  
          inet addr:169.254.10.39  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:34000000-34080000
```

---

### Post by jward3010 on 2009-11-03
Ok, basically I see that you're NOT connecting. You've received an APIPA address (169.254.X.X) which means your not getting an address from the router. Next thing is that chat with the neighbour, oh, and thanks for using the code tags.

---

### Post by kiff on 2009-11-03
I have had similar problems in the past connecting via WPA. When booting my machine in Windows XP, I have been able to connect to the router using WPA, but when booting into 9.04, I have never been able to connect. 

In the end I gave up and switched the security to WEP. It means that I still can't connect to any WPA networks, but at least I can use wireless at home.

Sorry, I realise that this doesn't help to solve the problem, but at least you know you're not alone :-7

---

### Post by a-web on 2009-12-02
I am ONLINE!!!  :)  (Sort of...)  :(

After having and solving other problems ([http://ubuntuforums.org/showthread.php?t=1342185](http://ubuntuforums.org/showthread.php?t=1342185)) I decided to try one more shot at connecting to WPA2 (as my house mate has been dragging his feet on changing any router settings).  And by following this:
[http://ubuntuforums.org/showpost.php?p=8082022&postcount=4](http://ubuntuforums.org/showpost.php?p=8082022&postcount=4)
I am online.  BUT - the network keeps disconnecting and reconnecting....  and seems to like being disconnected more than connected.

So now I know that it is possible to connect to this network with my computer.  I just need to make it reliable.

Any NEW ideas?

---

### Post by a-web on 2009-12-02
Later in the morning = back to no connectivity.  What is my next step here??

---

### Post by a-web on 2009-12-04
Confusion and Frustration going hand-in-hand here... :???: :-x

After my last reboot (hibernating has been giving me issues through all of this too!) Network Manager says that I am online with the WPA2 network!!

But I can not access anything online.  What is happening here?

---

### Post by jward3010 on 2009-12-04
> **a-web said:**
> ...hibernating has been giving me issues through all of this too! 
Ubuntu is plagued with hibernation and suspend issues for reasons once again of not being able to get decent ACPI drivers from manufacturers. It has improved a lot right up to Karmic to the point that I use it a lot now, previously I was just used to shutting down.

> **a-web said:**
> Network Manager says that I am online with the WPA2 network!!
But I can not access anything online.  What is happening here?
If you're still "technically" connected, try this:
```
ping -c 3 208.67.222.222
```
Then...
```
ping -c 3 resolver1.opendns.com
```
Then post the output of both if you can, it's a long shot but even a long shot is worth shooting. Hey, people win the lotto every now and then.

---

### Post by a-web on 2009-12-04
> **jward3010 said:**
> Ubuntu is plagued with hibernation and suspend issues for reasons once again of not being able to get decent ACPI drivers from manufacturers. It has improved a lot right up to Karmic to the point that I use it a lot now, previously I was just used to shutting down.


If you're still "technically" connected, try this:
```
ping -c 3 208.67.222.222
```Then...
```
ping -c 3 resolver1.opendns.com
```Then post the output of both if you can, it's a long shot but even a long shot is worth shooting. Hey, people win the lotto every now and then.

Hibernation only became a problem after I started working on the wireless; before that it was fine.


Although NM says I am connected, here is my output:
to "ping -c 3 208.67.222.222" I get
     connect:  Network is unreachable

and "ping -c 3 resolver1.opendns.com" gives me
     ping:  unknown host resolver1.opendns.com

---

### Post by jward3010 on 2009-12-04
OK, that was just going to test whether you had a DNS issue but it's definite non-connection issue. Basically if the first ping test had worked and the second hadn't, I would have concluded a DNS issue.

Can you give us the output of "nm-tool" and "ifconfig" once more, now that your connected?

---

### Post by a-web on 2009-12-04
```
a-web@Cutter:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            natsemi
  State:             unavailable
  Default:           no
  HW Address:        00:0D:9D:85:F5:DC

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan2  [2WIRE487] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           no
  HW Address:        00:16:B6:F2:77:CA

  Capabilities:
    Speed:           108 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2WIRE487:        Ad-Hoc, 02:D5:06:00:00:00, Freq 2412 MHz, Rate 11 Mb/s, Strength 90 WEP
    Clubhouse Redux: Infra, 00:1B:11:6A:E6:6B, Freq 2427 MHz, Rate 18 Mb/s, Strength 40 WPA

  IPv4 Settings:
    Address:         10.42.43.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0
``````
a-web@Cutter:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:85:f5:dc  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan2     Link encap:Ethernet  HWaddr 00:16:b6:f2:77:ca  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:30000000-30080000
```

---

### Post by jward3010 on 2009-12-04
I meant to ask for one other thing. I actually thought it would come up in nm-tool but it didn't. 
```
route -n
```

---

### Post by xjb2003x on 2009-12-04
I had a similar issue just last week.  I was connected just fine, then all of the sudden my connection would drop.  I scanned the wireless networks in the area and noticed a new wireless network.  My neighbor decided to get herself a router.  I went into my router's configuration and changed the channel from the default 6, to channel 1.  I have been connected uninterrupted ever since.

---

### Post by a-web on 2009-12-04
```
a-web@Cutter:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan2

```

---

### Post by a-web on 2009-12-06
Update...

- I took my laptop to an unsecured network, and it still said that it was connected to the WPA network (which was miles away).  So I deleted the WPA2 network from NM and it connected fine.

- Back with the WPA2 network, no connection.  But when I do```
sudo renice +19 $(pidof wpa_supplicant)
```during a connection attempt I am online.  For about a minute.  Then NM closes, connection goes off.

- If I reboot, NM says I am "connected" to the WPA2 network, but I am not.  If I delete the WPA2 network from NM, reboot again, and reconnect to a hidden network and do```
sudo renice +19 $(pidof wpa_supplicant)
```I am online for a minute....  etc...

What does this mean?

---

### Post by a-web on 2009-12-06
But now I have been online for a number of minutes, and still going strong.  Any thoughts on how to make this reliable?  Or not having do```
sudo renice +19 $(pidof wpa_supplicant)
```every time?

---

### Post by a-web on 2009-12-09
I am marking this thread as "solved" because now I am able to get online to the WPA2 network reliably.  Only issue is that it is neither easy nor fast.  So maybe I will open a new thread for that issue.  Thanks all for the assistance.

---

