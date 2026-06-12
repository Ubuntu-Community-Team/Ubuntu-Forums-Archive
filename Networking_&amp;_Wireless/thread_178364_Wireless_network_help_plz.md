---
title: "Wireless network help plz"
date: 2006-05-17
forum: Networking &amp; Wireless
---

### Post by Ashez25 on 2006-05-17
Hi 
  I have installed ubuntu 5.10 a week ago and are still having trouble with my Netgear wirless usb adaptor WG111v2
  I have installed ndiswrapper and ndisgtk and they worked so i installed the drivers aswell.
  I have also installed wifi-radar given it all the wep,ch,ip and it can find the network but i can not connect to the internet.:( 
  If any1 can help please as this is my first use of linux.

Thanks
Ashley

---

### Post by mjm115 on 2006-05-17
it found the network, but are you able to get an IP adderess?  What are the results of 'ifconfig' when you type it in a terminal?

---

### Post by Ashez25 on 2006-05-18
Heya when i used ifconfig i got the following:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28541 (27.8 KiB)  TX bytes:28541 (27.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:B9:61:29
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:feb9:6129/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I gave wifi-radar an IP if thats what you mean?

Thanks
Ashley

---

### Post by Doghouse on 2006-05-18
Recheck your wep key and that the ssid, which you should rename to something specif to you.... like your last name or something, is identical to what your broadcasting from your access point.  Also; is that the ip-range that your broadcasting in your dhcp table??.  Make sure that your not picking up your neighbors access point.  I mac filter and static enter the ip... that way I know that I'm getting on the right access point.  Plus is will give you at least the front line of security.

I mean it looks like your getting an address.


-K

---

### Post by Ashez25 on 2006-05-19
I checked my WEP key and the ssid (if thats the network name)
I have given it a static IP which is the same as the router.
I can not find how to give it a mac filter with wifi-radar do i have to do something different.

Thanks
Ashley

---

### Post by Ashez25 on 2006-05-22
I can ping the network now but it wont let me connect to the net. Has any1 got any help plz.

Thanks
Ashley

---

### Post by avirnig on 2006-05-22
first off, have you disabled your wired ethernet adapter? sometimes having both enabled can freak out ubuntu networking. , secondly, if you can ping the AP, then it should be able to connect to the internet. do you have any DNS server addresses set up in your conf files? (not exactly sure which file that is- someone else will have to help you there) if you can ping the AP , AND are on the exact same subnet mask AND do NOT have the exact same IP as the AP itself set for your card, then it must be a DNS problem.

---

### Post by Ashez25 on 2006-05-23
Sorry but umm.. wat does DNS starnd for???

---

### Post by popkid on 2006-05-23
[QUOTE=Ashez25]Sorry but umm.. wat does DNS starnd for???[/QUOTE]

Domain Name System (or Service or Server depending on who you ask!)

It is the system by which your computer knows where you want to go when you type in a web address into your browser, it converts the name to the ip address of the name.

If you aren't accessing a DNS server properly then you could be connected to the internet, but typing in a web address wouldn't do any good, because your computer couldn't convert it into the IP address of the site.

pK

---

### Post by gitargr8 on 2006-05-23
Try this and post the results:

```


sudo dhclient wlan0
```
If it is hanging, try to do this:

```


sudo iwconfig wlan0 essid YourEssid
sudo iwconfig wlan0 key restricted YOURWEPKEY
sudo dhclient wlan0

```
If it doesn't hang, try to:

```


ping www.yahoo.com -c 4
```
If you get a reply that means you have Internet.

---

### Post by Ashez25 on 2006-05-23
heya tried what you said and the got this
[U]
For sudo dhclient wlan0[/U]
sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 8494
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:b9:61:29
Sending on   LPF/wlan0/00:0f:b5:b9:61:29
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[U]
[U]For sudo iwconfigs they did nothing when i typed them in the terminal
when i did sudo dhclient wlan0 again i g[/U]ot
sudo dhclient wlan0[/U]
There is already a pid file /var/run/dhclient.pid with pid 8756
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:b9:61:29
Sending on   LPF/wlan0/00:0f:b5:b9:61:29
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping


_And final for ping i got_
ping: unknown host [www.yahoo.com](www.yahoo.com)

Hope this means something to someone because it doesnt for me.

Thanks Ashley

---

### Post by ingo on 2006-05-23
Hi Ashley,

I take it your router is a dhcp server and set up as such. If so, try the following,. I'm pretty confident it'll work:

sudo bash
(type in your password to get a root shell)
ifdown wlan0
iwconfig wlan0 essid "YOUR NETWORK NAME" key s:YOUR PASSWORD PHRASE
ifup wlan0

You should be in now. If it worked for you have a look at 
[http://ubuntuforums.org/showthread.php?t=177059&page=2&highlight=ip+address](http://ubuntuforums.org/showthread.php?t=177059&page=2&highlight=ip+address)
to write yourself a script and save typing all that every time you want to get in.

HTH 

Ingo

---

### Post by jml on 2006-05-23
If you are still having problems connecting, temporarily disable WEP encryption on both your laptop and the wireless access point.  If you can connect to the internet now, then you know its not a hardware problem, but a configuration problem.  

Check out this link, its the Ubuntu Wireless Troubleshooting guide and may be of some help.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by stock99 on 2006-05-27
hi,

 i got similar problem with my wg311v2 card too. It drops off very now and then, so i try to run `dhclient wlan0` every 30 min in crontab to allow me to access this computer remotely.  But i realize after a while, dhclient stop working and come out with the same error message as [Ashez25] .   I try the command [Ingo] suggest but still the error message.

---

