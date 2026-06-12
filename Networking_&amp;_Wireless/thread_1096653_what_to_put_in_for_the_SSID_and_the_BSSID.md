---
title: "what to put in for the SSID and the BSSID"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by wstay on 2009-03-15
I am using an USB Wireless adapter.
But I don't know what to put in for the SSID and the BSSID in the Network Connections Configuration.
Can someone please show me the way?

---

### Post by ajmorris on 2009-03-16
> **wstay said:**
> I am using an USB Wireless adapter.
But I don't know what to put in for the SSID and the BSSID in the Network Connections Configuration.
Can someone please show me the way?

hi there,
your SSID is just the broadcast name of your wireless network. (i.e the name of the network that is listed when you scan for avaliable networks)
and the BSSID is the MAC address of your router.

if you run:
```
sudo iwlist scanning
```
in a terminal, you can see both of them for your wireless network. the SSID is called 'ESSID' and the BSSID is just 'Address'

You should not have to manually specify your BSSID however, as this should be detected automagically from the SSID. However, if it doesn't automagically detect it, then specify the BSSID also. :)

AJ

---

### Post by wstay on 2009-03-16
> **ajmorris said:**
> hi there,
your SSID is just the broadcast name of your wireless network. (i.e the name of the network that is listed when you scan for avaliable networks)
and the BSSID is the MAC address of your router.

if you run:
```
sudo iwlist scanning
```
in a terminal, you can see both of them for your wireless network. the SSID is called 'ESSID' and the BSSID is just 'Address'

You should not have to manually specify your BSSID however, as this should be detected automagically from the SSID. However, if it doesn't automagically detect it, then specify the BSSID also. :)

AJ

Thanks for your reply.
My computer automatically detects the SSID (ESSID) of my wireless network as ZyXEL which is my wireless router ADSL modem. When I go to edit in the Network Connections Configuration, both the BSSID and the MAC address are blank. Does this mean that it is not detecting the BSSID and MAC address or it has detected the BSSID and MAC address but is just not showing them.
When I post 'sudo iwlist scanning' in the terminal, it gives me the following output:
wstay@ubuntu8:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:30:0A:C2:C5:DA
                    ESSID:"aztech"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/100  Signal level:-76 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000037d28d69c
                    Extra: Last beacon: 1048ms ago
          Cell 02 - Address: 00:13:49:A8:77:4F
                    ESSID:"ZyXEL"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/100  Signal level:-52 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 54 Mb/s
                    Extra:tsf=00000001acff6ed3
                    Extra: Last beacon: 1044ms ago

wstay@ubuntu8:~$ 

So, do I have to manually fill in the BSSID and MAC Address, and how can I obtain these information?

---

### Post by ajmorris on 2009-03-18
which network configuration tool are you using? You shouldn't have to fill in that information for your network (unless you're not using dhcp) - when you choose to connect to the network, if you are using dhcp, all the info such as the BSSID is there automagically. If however this is not working, and you have the need to configure your network manually, the bssid from your output is where it says: > Cell 02 - Address: 00:13:49:A8:77:4F
the bssid is the actual MAC address from this; 00:13:49:A8:77:4F


AJ

---

### Post by mayer213 on 2009-03-18
I think you can find out the SSID and BSSID in the configuration of your wireless router. You know to access your router right? when you did look for the SSID on the wireless configuration. One you got you can input the name in the SSID bar in the computer to connect. Important take down on a note OK? you'll need the exact spelling and capital letter of the SSID or BSSID.

---

### Post by tonytraductor on 2009-05-11
I don't understand why I would have to feed the network manager values for the router.
Shouldn't it automatically find the router?

What am I supposed to do when I go to a coffee shop, and don't know the values for their router?

---

### Post by LandisTwo on 2011-04-21
> **ajmorris said:**
> hi there,
your SSID is just the broadcast name of your wireless network. (i.e the name of the network that is listed when you scan for avaliable networks)
and the BSSID is the MAC address of your router.....

Thanks

Landis

---

### Post by ekpg on 2013-02-02
Just wanted to put this out there. I was not having any luck to fill out the BSSID and other encryption etc, either. 
I was wanting to use a usb connected wireless adapter...but when I did that is when I was asked to put these in. 
Also I was a bit bothered that I could not connect to internet wirelessly. It recognized the device but that is it. 
I spent days and many hours trying to change setting in Wireless network and other means.
Finally I called my internet provider and they tole me to look up my Username / Passphrase and all in the website with a spacific IP address number he gave me. This took me to all my setup information and everything else.
That is where I found out that I had chosen WPA/WPA2 security my own created password/passphrase. 
The Adapter did not have this. Only WEP so it won't work unless I change the setting from WPA to WEP. 
So I will have to purchase a wirelessN adapter that will work on WPA/WPA2 like the Cisco usb wireless adapter or the internal TP-LinkTL-WN951N .  Then I will not have to enter all this stuff. 

So, problem solved if you can just get the right wireless adapter for you computer or have you internet provider help you change the settings to the WEP and then all the right info you put in for that will just be the same.

---

### Post by howefield on 2013-02-02
Old thread closed.

---

