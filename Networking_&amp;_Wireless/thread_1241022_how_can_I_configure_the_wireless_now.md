---
title: "how can I configure the wireless now ?"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by aneuryzma on 2009-08-15
Hi,

I've installed wireless card and I didn't receive any error in the installation process.

Now I want to use it but I can't make internet to work.

if I check my card with iwconfig I get the following message

> wlan0     IEEE 802.11g  ESSID:"Alice-34376718"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:02:85:91:C6   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=73/100  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

"Alice-34376718" is the name of my wireless indeed... it seems already selected

but          ping [www.google.com](www.google.com)         gives      "unknown" host

and          iwlist wlan0 scan               gives       No results

Is there any driven procedure to configure the wireless ?

Is maybe because I was using ppoeconfig procedure to configure windows before ?

thanks

---

### Post by ahood on 2009-08-15
Two things you might try are...

First, determine if a network interface has an IP address.

> ifconfig

Does one of the network interfaces have an assigned IP address? If so, which ones?

Second, if you have a gateway between your client machine and the Internet modem, ping the gateway and to confirm that you are connected within your local area network.

Hope this helps.

---

### Post by aneuryzma on 2009-08-15
I'm not very prepared... this is the output.. is ip address missing, right ?

> eth0      Link encap:Ethernet  HWaddr 00:0c:6e:e4:de:c9  
          inet6 addr: fe80::20c:6eff:fee4:dec9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6834 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:12564585 (11.9 MB)  Byte TX:733146 (715.9 KB)
          Interrupt:11 Indirizzo base:0xa000 

lo        Link encap:Loopback locale  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2638 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:131900 (128.8 KB)  Byte TX:131900 (128.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:a8:85:b2  
          inet6 addr: fe80::211:50ff:fea8:85b2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:576 (576.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-A8-85-B2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)


---

### Post by ahood on 2009-08-15
Yes, it appears that the machine is not connected to the home wireless network.

What version of Ubuntu (Hardy, Intrepid, Jaunty)?

What variant of Ubuntu (Ubuntu, Kubuntu, Xubuntu)?

Is Network Manager running and available from the taskbar?

I recommend using Network Manager first to connect to a wireless network.

You will know that you are connected wirelessly because the Network Manager icon will change to multiple vertical bars.

I know I have not provided a lot of how-to information; however, more information about your system is needed to give good help.

With kind regards,

---

### Post by aneuryzma on 2009-08-15
I have GOS, I hope this is not a problem.

Ya.. I have the bars near the clock, they are all gray. When I click on "connect wireless" the lights on the wireless card are switched on.

I'm sure the wireless is working because I'm using another laptop connected to it.

The name of the app near the clock is "nm-applet 0.6.6 "applet to handle interfaces and network connections".

What should I see in the ifconfig output when it is ok ?

thanks

---

### Post by ahood on 2009-08-15
What happens when you left-click on the grey bars in the taskbar?

What should happen is a list of wireless networks configured to auto broadcast appear.

I have not used GOS and do not know how it is different from Ubuntu.

Below is an example of the output of ifconfig with a configured wireless network device.
> eth0      Link encap:Ethernet  HWaddr xx : xx : xx : xx : xx : xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr xx : xx : xx : xx : xx : xx  
          inet addr:192.168. x . xx  Bcast:192.168. x . xxx  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69389 errors:0 dropped:0 overruns:0 frame:32280
          TX packets:46311 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89201733 (85.0 MB)  TX bytes:4933899 (4.7 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101117 (98.7 KB)  TX bytes:101117 (98.7 KB)

On my system, eth1 is the wireless device and assigned a 192.168.x.xx ip address.

---

### Post by aneuryzma on 2009-08-15
ok thanks,

If I click on it, I have "connect to network", "connect to wireless", "informations"

When i select / deselect "connect to wireless", the lights on the wireless card switch on / off.

I don't have the list of wireless networks. I don't know if this is normal or not.

Maybe I should focus more on terminal commands so I'm not going to suffer this GUI differences ?

---

### Post by ahood on 2009-08-15
Okay,

Here is a resource for you, [**[COLOR="Blue"]Connect to a wireless network via command line[/COLOR]**]("http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/")

I hope the above link helps.

---

### Post by aneuryzma on 2009-08-15
thanks for the link. So...

> sudo ifconfig wlan0 up
OK
 
iwlist wlan0 scan
wlan0     No scan results


sudo iwconfig wlan0 essid Alice-34376718 key "s:49lo-o794-cdda-geej-pud5-pvh6"
OK



sudo dhclient wlan0

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:a8:85:b2
Sending on   LPF/wlan0/00:11:50:a8:85:b2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

thanks

---

### Post by ahood on 2009-08-15
For this step...

> sudo iwconfig wlan0 essid Alice-34376718 key "s:49lo-o794-cdda-geej-pud5-pvh6"

Try without the quotes

> sudo iwconfig wlan0 essid Alice-34376718 key s:49lo-o794-cdda-geej-pud5-pvh6

---

### Post by aneuryzma on 2009-08-16
Hi!

I've just wake up and after restarted Gos, surprise, the wireless is working... but:

1) it works for about 2 minutes, then I've to type "dhclient wlan0" to restart it

2) for some reason internet doesn't work with firefox but only with skype and of course in the terminal "ping www.google.com". I've tried to change proxy settings but nothing.

thanks

---

