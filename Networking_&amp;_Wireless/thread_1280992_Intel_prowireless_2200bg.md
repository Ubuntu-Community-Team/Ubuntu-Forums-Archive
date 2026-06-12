---
title: "Intel pro/wireless 2200bg"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by demonic_crow on 2009-10-02
I'm wanting to put ubuntu on my laptop but the wireless card didn't work when I ran the live cd.  Is there anything I can do to get it to work.

---

### Post by kreggz on 2009-10-03
Hi,

You can use Windows drivers follow this guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I have had to use it on one of my pcs and it works a treat.

---

### Post by chili555 on 2009-10-03
You can also open a terminal and do two separate commands:```
sudo modprobe ipw2200
iwconfig
```Now do you see a wireless interface, eth1, perhaps? Can you click the Network Manager icon and see your network and connect?

---

### Post by anarchic_teapot on 2009-10-25
> **chili555 said:**
> You can also open a terminal and do two separate commands:```
sudo modprobe ipw2200
iwconfig
```Now do you see a wireless interface, eth1, perhaps? Can you click the Network Manager icon and see your network and connect?

I have a similar problem. Installing the windows drivers for ndiswrapper stopped my Dell 630M booting properly, so that option is out.

*sudo modprobe ipw2200 *

does indeed get the wireless network showing up in Network Manager. However, even though it says it's connected (and I've checked the config a zillion times), even boasting an IP address, it's impossible to use the connection.

wpagui says it " Can"t get status from wpa_supplicant". Rude word.

After much searching, finding loads of out-of-date tips, I found [this page]("http://www.thinkwiki.org/wiki/Wpa_supplicant#For_WPA2-Personal") (I use WPA/WPA2 on my Netgear 614).

Now the network shows up, but keeps disconnecting-reconnecting. So it works, but is so slow as to be unusable. What now??? I suspect something obvious to seasoned users that they forget to pass on to newbies.

*iwconfig*
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"my_network"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:14:6C:D6:9F:F0   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:[long_hex_chain]   **Security mode:open**
          Power Management:off
          Link Quality=75/100  Signal level=-54 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          **Tx excessive retries:434  Invalid misc:28 **  Missed beacon:1
```

Security mode - why "open"?

---

### Post by chili555 on 2009-10-25
These items:> Encryption key:[long_hex_chain]   Security mode:openare typical of a WEP encrypted setup, not WPA. Please check where and how you entered your WPA password in Network Manager.

---

### Post by anarchic_teapot on 2009-10-28
> **chili555 said:**
> These items:are typical of a WEP encrypted setup, not WPA. Please check where and how you entered your WPA password in Network Manager.

WPA-WPA2 (Personal) :/

Now I notice that if I want my wireless chip detected I need to run 'sudo modeprobe ipw2200' every time I boot.

Making sure NM is set to WPA followed by iwconfig gave me this:

```
eth1      IEEE 802.11bg  ESSID:"ssid"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: (MAC address)   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=76/100  Signal level=-52 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2
 
```I'd really, really like to get this damn thing working, it would mean I could have a distraction other than bloody awful repetitive TV or books I've read a thousand times next time I'll sick in bed for several days (happens often, I'm handicapped). Also it would be one in the eye for Windows.

---

### Post by chili555 on 2009-10-28
Your *iwconfig* looks like you are connected! Can you reach the internet with Firefox? Please try:```
ping -c3 www.google.com
```To load ipw200 automatically, please do:```
sudo gedit /etc/modules
```Add a new line:```
ipw2200
```Post back and let us know.

---

### Post by jrusso2 on 2009-10-28
This laptop has a 2200bg card which has open source intel drivers and should work out of the box.

I am running Mandriva 2009.1 atm since Jaunty had so many issues.

---

### Post by anarchic_teapot on 2009-11-03
> **chili555 said:**
> Your *iwconfig* looks like you are connected! 
Yep. NetworkManager seems to think so.
> Can you reach the internet with Firefox? 
Nope. 
> 
Please try:```
ping -c3 www.google.com
```
Now this is weird. Ping seems to work, but nothing else (no Firefox, no update-manager...). 

It doesn't seem to be switching on and off anymore, though.

---

