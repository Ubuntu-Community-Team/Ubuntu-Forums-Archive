---
title: "Strange WiFi speed problem with RTL8187"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by strixx on 2009-06-17
Hi,
 
First post here. I have tried getting help in a Swedish Ubuntu forum with no luck on this problem.
 
Tanx to a great thread here I have managed to get my Netgear wg111v3 to connect to my wireless router that's secured with WPA2/AES. And without any network manager. Im running Ubuntu 9.04 with Lxde on a super old laptop so I am trying to reduce the amount of resource demanding apps.
 
My problem is that the speed after boot is only 1Mbit/s.
I can't get it to speed up with iwconfig.
But if I restart the network with ".../networking restart" iwconfig reports 54Mbit/s.
In ".../interfaces" I have the line "wireless-rate 54M".
It's the same thing every time i reboot, tried at least 20 times now!

---

### Post by pytheas22 on 2009-06-17
So typing:
```

sudo iwconfig wlan0 rate 54M
```

doesn't do anything?  But:
```

sudo /etc/init.d/networking restart
```

fixes it until the next reboot?  If that's the case, I'm not sure what's wrong, but a work around would probably be to write a boot script that would just restart networking automatically.  To create that script, run these commands:
```

sudo -s
echo -e '#/bin/bash\n/etc/init.d/networking restart' > /etc/init.d/networking-fix.sh
cd /etc/init.d
chmod +x networking-fix.sh
update-rc.d networking-fix.sh start 99 2 3 4 5
```

With this script in place, does you problem go away?

---

### Post by dnairb on 2009-06-17
I don't think this is actually a problem (unless you only get 1Mb/s when actually using the network (e.g.downloading emails, browsing the 'net).

My network behaves in the same way: it seems when the wireless network is idle, the speed drops to 1Mb/s to keep the connection alive, and when actually in use, it jumps to 54Mb/s.

---

### Post by strixx on 2009-06-18
> **pytheas22 said:**
> So typing:
```

sudo iwconfig wlan0 rate 54M
```
 
doesn't do anything? But:
```

sudo /etc/init.d/networking restart
```
 
fixes it until the next reboot? 
 
That is correct!!!
 
Of course I could make a script, but i rather find out what's wrong... :(
And it takes some time to restart the network, at least 1 minute.

---

### Post by strixx on 2009-06-18
> **dnairb said:**
> I don't think this is actually a problem (unless you only get 1Mb/s when actually using the network (e.g.downloading emails, browsing the 'net).
 
So what your saing is that I should get some king of tool to se the actual dowload speed?

---

### Post by pytheas22 on 2009-06-18
> That is correct!!!

Of course I could make a script, but i rather find out what's wrong...
And it takes some time to restart the network, at least 1 minute. 

That's strange.  It should only take a few seconds to restart networking.  Does it tell you what's taking so long when you run '/etc/init.d/networking restart' in the terminal?

> 
So what your saing is that I should get some king of tool to se the actual dowload speed?

Yes, as dnairb points out, having 1M transfer rates listed in iwconfig is not unusual.  You should try downloading a file to see if the rate is really limited to 1 megabit per second (which is equal to 125 kilobytes/second).  If your Internet connection to the outside world is slower than 125 kilobytes/second, you should try transferring a file on the local network (i.e., from another computer in your house) to see how fast that goes, since a local file transfer should be much faster than downloading from the Internet, unless you have a very high-bandwidth Internet connection.

---

### Post by strixx on 2009-06-18
Nope, doesn't tell me what it's doing.
It stops after telleing me that it's realesed the IP, and "thinks" for about 20 sek.
Then it stops again after requesting new IP also for about 20 sek.
 
I will start the computer where the problem is (not this one) and do some copy, paste actions to show you. But it will have to be later. I'm working right now (its 10 am here).
 
I will also test the actual speed.

---

### Post by dnairb on 2009-06-18
In Gnome, if that is what you are using, right-click the network icon thingy in the panel (normally top right-ish) and select "Connection Information"
This gives you IP address, DNS address, etc, and the current speed.

---

### Post by strixx on 2009-06-18
Here is som more info:

This is my "/etc/network/interfaces":
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

#WiFi
auto wlan0
iface wlan0 inet dhcp
wirless-rate 54M
wpa-driver wext
wpa-ssid Inet@Simens
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 9a3470870b83629fcbe53d8ae5a05902e791a92e5e7b69c0ecb9bb5cf5631b23

```

This is what "iwconfig" tells me after a reboot:
```
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Inet@Simens"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:02:20:24:B8   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=66/100  Signal level:-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

This is what hapens when I run "sudo /etc/init.d/networking restart":
```
* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 2315
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1e:2a:cd:d3:0c
Sending on   LPF/wlan0/00:1e:2a:cd:d3:0c
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon
   ...done.
```
[COLOR="Red"]Here it stops and wait for 63 seconds[/COLOR]
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1e:2a:cd:d3:0c
Sending on   LPF/wlan0/00:1e:2a:cd:d3:0c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPOFFER of 192.168.2.14 from 192.168.2.1
DHCPREQUEST of 192.168.2.14 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.14 from 192.168.2.1
bound to 192.168.2.14 -- renewal in 86079 seconds.
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon
   ...done.
```

And this is what "iwconfig wlan0" after the network restart says:
```
wlan0     IEEE 802.11bg  ESSID:"Inet@Simens"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:02:20:24:B8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=60/100  Signal level:-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I will know test the actual speed, and will as soon as possible get back to you with the result.

---

### Post by strixx on 2009-06-18
Now I have tested the speed by downloading a file with Filezilla from my Ubuntserver at home.
 
But here is a funny result.
 
First time after reboot with "iwconfig" reporting 1Mb/s a 18Mb file took 1.5 minutes to download with max speed 310KB/s, wich indicates about 1-2Mbit.
 
Then I tryied the same file again without doing anything else and then it took 52sek with max speed 470KB/s. Wich only is about 3Mbit but its faster than the first time. I theh whent out in terminal an checked iwconfig and it then reported 54Mb/s.
 
It hade by it self went up in speed. This has never happend befor by just browsing the webb.
 
So no mather what iwconfig reports I only have about 2Mbit!!!
I have found a page that indicates that sometimes speed issues can be fixed with changing the MTU vale can help.
I don't know how to do this without any manager, but if i find out I will try this.

---

### Post by strixx on 2009-06-18
Just realised one thing. This superold computer only has USB 1.0, wich have a maximum transferrate of 12Mbit.
And the interface is connected to the computer through a hub, where the mouse also is connected.
 
Could this be the cause of the low transferspeed?

---

### Post by pytheas22 on 2009-06-18
I don't know if changing the mtu does anything on a wireless interface; I've only heard of that for ethernet.

Anyway, 460 kilobytes/second is pretty reasonable for a residential Internet connection.  Is that substantially slower than the download speeds you see on other computers/operating systems in your house?

The speed difference between the first and second download attempts could be due to any number of factors: other computers in your house using some of the bandwidth, your neighbors using bandwidth, bottlenecks upstream, etc.  It's not necessarily a problem with your wireless card.

---

### Post by strixx on 2009-06-19
On my other laptop the same file takes 6 sekonds, and max speed is 4 MByte/s wich is about 30 Mbit/s.
 
My internet connection is for the moment a 2 Mbit/s, so if I don´t get more speed it is not a disaster, but it would be fun to know why it does like it does.
 
Could it be a bug in the rtl8187 module? As I understand that module has had some problems in the past. And it not so long ago it started to support the version B of the 8187 chip, wich i have.

---

### Post by pytheas22 on 2009-06-19
You could try using the Windows driver in ndiswrapper instead of the native Linux rtl8187 module.  If it's a problem with the Linux driver, this should fix it.

---

### Post by strixx on 2009-06-20
> **pytheas22 said:**
> You could try using the Windows driver in ndiswrapper
 
This i've tried before on both Puppy and DSL, without any luck. It could never keep the connection for more than a couple of minutes.

---

### Post by pytheas22 on 2009-06-20
> Just realised one thing. This superold computer only has USB 1.0, wich have a maximum transferrate of 12Mbit.
And the interface is connected to the computer through a hub, where the mouse also is connected.

Could this be the cause of the low transferspeed? 

Ah, I didn't see this post until just now--you must have written it while I was in the middle of writing another one, and after I refreshed the page your post was no longer at the bottom.

This is very likely the problem.  USB 1.1 maximum transfer speed is only 1.5 megabits/second (pretty similar to the speeds you were seeing), compared with 12 for USB 2.  Unless you get faster transfer speeds on the same computer under Windows, then I think this explains it.

---

### Post by strixx on 2009-06-20
> **pytheas22 said:**
> Unless you get faster transfer speeds on the same computer under Windows, then I think this explains it.
 
Don´t know, and don't want to know... ;) I don't use Windows unless I'm forced to do so... 
 
But I think I have to mark this as solved, beacuse I'm pretty sure my self that it is the USB-port that's the problem...

---

