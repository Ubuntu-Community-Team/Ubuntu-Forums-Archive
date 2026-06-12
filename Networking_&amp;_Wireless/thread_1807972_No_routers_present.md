---
title: "No routers present"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by moonsal on 2011-07-19
Just installed 10.04 and can't seem to connect to my router... What gives?? my nic card is read and all good but I can't connect to the router via wireless bridge...

dmesg | gre -e eth0 -e bcm

[ #s] eth0: RealTek RTL8139 at 0x3000, 00:00:c5:c1:73:e4, irq
[ #s] eth0: link up. 100mbps, yada
[ #s] eth0: no IPv6 routers present

Any thoughts??? I'm on a Win7 system a the moment so copy and paste is kinda not possible..lol I can type in whatever info ya'll need though... Just need to get this thing online and i'll be good to go... Thanks for the help in advance...

Under the -Moon

---

### Post by jmoorse on 2011-07-19
> 
 my nic card is read and all good but I can't connect to the router via wireless bridge...


To clarify: are you having issues with wired, wireless, or both?

---

### Post by wildmanne39 on 2011-07-19
> **moonsal said:**
> Just installed 10.04 and can't seem to connect to my router... What gives?? my nic card is read and all good but I can't connect to the router via wireless bridge...

dmesg | gre -e eth0 -e bcm

[ #s] eth0: RealTek RTL8139 at 0x3000, 00:00:c5:c1:73:e4, irq
[ #s] eth0: link up. 100mbps, yada
[ #s] eth0: no IPv6 routers present

Any thoughts??? I'm on a Win7 system a the moment so copy and paste is kinda not possible..lol I can type in whatever info ya'll need though... Just need to get this thing online and i'll be good to go... Thanks for the help in advance...

Under the -MoonHi, from what I read your problem is just the wireless card correct? if that is the case please run these commands in a termial
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list All
```
and post the results back here.
Thank you

---

### Post by moonsal on 2011-07-20
It's a wired card that goes to a wireless bridge.. My wireless router is about 40ft from the wireless bridge... I can't get xubuntu to find the router (or bridge maybe??)...


lspci -nn | grep 0280
```
NOTHING, just went back to prompt
```

iwconfig
```

lo           no wireless extensions.

eth0         no wireless extensions.
```


rfkill list all
```
Nothing, just back to prompt
```

---

### Post by smurphy_it on 2011-07-20
Then how about posting these commands ?
```
lspci
```
```
ifconfig -a
```

Do you have internet access ?  Can you ping your wireless router, or is it configured to automatically forward it to your main router ?

---

### Post by moonsal on 2011-07-20
Here ya go...

lspci
```

******************
******************
01:0e.0 Ethernet controller. Realtek Semiconductor Co., Ltd. RTL-8139/8139c/8139c+ (rev 10)
```

ifconfig -a
```

eth0     Link encap:Ethernet  HWaddr 00:00:c5:c1:73:34
         inet6 addr: fe80::200::fecl::73e4/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B) TX bytes: 1836 (1.8KB)
         Interrupt:10 Base address:0x3000


lo       Link encap: Local loopback
         inet addr:127.0.0.0 MASK 255.0.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436 Metric:1
         RX packets:148 errors:0 dropped:0 overruns:0 frame:0
         TX packets:148 errors:0 dropped:0 overruns:0 carrier:0        
         collisions:0 txqueuelen:0
         RX bytes:11728 (11.7 KB)  TX bytes:11728 (11.7 KB) 
         
```

---

### Post by moonsal on 2011-07-20
Also, do I need to take my wireless bridge and physically connect it into my router first??

---

### Post by smurphy_it on 2011-07-20
Not sure of your wireless bridging setup.  I haven't done it myself, but did look at doing it at one point between two dd-wrt routers.  From my understanding the wireless bridge would connect wirelessly to your main router, and all traffic would go on that same vlan (or an alternate).  Additionally, you would only have 1 dhcp server setup on the routers (unless the wireless bridge has LAN ports which you wish to use).

If dealing with the same vlan, then one would have to deal with subnetting.  If two seperate vlans, you'd have to setup routes so that both vlans would see each other.

Perhaps you can explain your specific setup in more detail.

PS.  I noticed that eth0 doesn't have an IP address assigned.  That could point to part of your problem.

---

### Post by moonsal on 2011-07-20
Thanks for the reply. I just moved this(ubuntu) system in the other room and hooked it straight into the router and it works flawlessly!! So I know it&#347; not the nic card.... My setup is pretty much how you described...  NIC -> Wireless bridge -> wireless router.... I have another system runnin Win7 with just a wireless cardand it too works great so it&#347; this bridge (i&#7743; figuring)... Dunno what sort of detail I can explain to you but feel free to ask any questions and I&#314;l do my best to answer them... 

How do I configure the bridge in linux?

Again thanks..

---

### Post by smurphy_it on 2011-07-20
Why don't you start with the hardware.  What kind of "wireless bridge" is it ?  Is it some kind of wireless router etc... Make and model would be beneficial.

Second is the router, what kind of router is it... model / make too.

---

### Post by moonsal on 2011-07-20
Ok.... I'm re-installing xubuntu 10.04 (almost done) but this time I set up the network (manually) during setup instead of skipping it... HOPEFULLY, it might work but seriously doubt it..

My NIC is Realtek 8139C
 
The bridge is just a plain wireless bridge, nothing fancy.. Linksys WET54G

The router is Linksys WRT54GS...

Anything else you need to know please don't hesitate to ask..

---

### Post by mokrates on 2011-07-20
If your router and the wireless-bridge (which, as I understand, are connected wirelessly ;) ) are like 'cheap', of the shelf, plastic thingies, you probably don't have to configure anything on your ubuntu-box.
As the output of ifconfig which you posted points out, your ubuntu-box is connected to the bridge. (That's the RUNNING Flag on the eth0 interface) but doesn't get an IP, so your ubuntu-box cannot reach the router /through/ the bridge.

Probably your bridge just doesn't work.

The bridge is, as you probably don't know, NOT a peripheral to your ubuntu-box. It's not like a wireless card, but more like a ethernet-switch. So the wireless-credentials have to be entered into the box, not into your ubuntu-configuration.
have a look into the manual of the box, how to configure it with an existing wireless-network (most likely there will be a (somehow) reachable webinterface in which you can enter a network-name ((E)SSID) and a network-password (WPA(2)-PSK most likely for home-use hardware))

the 'No routers reachable' is irrelevant to this problem, as it tells you that miredo doesn't work, which is not your problem at hand but not surprising without internet-access. :)

greetz

mo

---

### Post by moonsal on 2011-07-20
Completely understand.. :) Thing is I have 2 bridges here (1 that has never been used) and they both did not work on the U-box... I remember a while back having to set up each bridge manually for security system and another Win-box so during this (new)installation I went ahead and did that as before I just skipped it thinking I could later set it up.. I was wrong.. :(

---

### Post by moonsal on 2011-07-20
NEW ifconfig -a          I replaced my IP with 11.111.11.178

```

eth0     Link encap:Ethernet  HWaddr 00:00:c5:c1:73:34
         inet addr:11.111.11.178 Bcast:11.111.11.255 Mask:255.255.255.0
         inet6 addr: fe80::200:c5ff:fecl::73e4/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B) TX bytes: 17912 (17.9 KB)
         Interrupt:10 Base address:0x3000


lo       Link encap: Local loopback
         inet addr:127.0.0.0 MASK 255.0.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436 Metric:1
         RX packets:157 errors:0 dropped:0 overruns:0 frame:0
         TX packets:157 errors:0 dropped:0 overruns:0 carrier:0        
         collisions:0 txqueuelen:0
         RX bytes:14966 (14.9 KB)  TX bytes:14966 (14.9 KB)  
```

I still have no internet, I think I can get it if someone would tell me how to reassign the bridge without re-installing xubuntu..

---

### Post by mokrates on 2011-07-20
The IP you get there looks wrong (it's not a private LAN ip). For instructions to setup your bridge, you should consult the manual:

I found it googling for 'Linksys WET54G' on this page: [http://www.linksysbycisco.com/UK/en/products/WET54G](http://www.linksysbycisco.com/UK/en/products/WET54G)

Chapter 3 reads: 

> 
How to Access the Web-Based Utility
1.     Open your web browser, and enter the IP address
of the Wireless-G Ethernet Bridge (the default is
192.168.1.226) in the browser&#8217;s Address field. Then
press Enter.


as it seems, the default is not set on your bridge anymore. So you should try to reset the device. How to do that is probably explained in the manual, also

---

### Post by smurphy_it on 2011-07-20
Typically one would login to the wireless bridge, and give it the credentials of your main router (SSID + passphrase).  That should give the bridge the credentials it needs.  Anything that connects to that bridge should then have access.

Of course, the wireless bridge would probably just be a pass-through (extending your wifi range) and the dhcp assigned address would be gotten from your main router.

Documentation should explain that in detail though.  Or the online help within your wifi bridge.

---

### Post by moonsal on 2011-07-20
Thanks, i'll have to check into that right quick...Through ifconfig I changed my broadcast ip to that of my router, shouldn't this work now?? Since this new install I don't have the "network manager" icon on top right corner of my screen..

```

eth0     Link encap:Ethernet  HWaddr 00:00:c5:c1:73:34
         inet addr:11.111.11.178 Bcast:192.168.1.1 Mask: 255.255.255.0
         inet6 addr: fe80::200::fecl::73e4/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:684 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B) TX bytes: 45224 (45.2KB)
         Interrupt:10 Base address:0x3000


lo       Link encap: Local loopback
         inet addr:127.0.0.0 MASK 255.0.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436 Metric:1
         RX packets:148 errors:0 dropped:0 overruns:0 frame:0
         TX packets:148 errors:0 dropped:0 overruns:0 carrier:0        
         collisions:0 txqueuelen:0
         RX bytes:11728 (31.4 KB)  TX bytes:31494 (31.4 KB)

```

---

### Post by mokrates on 2011-07-20
As your ethernet-card gets an IP, it probably is configured via dhcp. entering a different broadcast-address won't work that way, you have to enter a matching ip also. AND you should check if there is a running dhcp-client (which there probably is, as you already have a (wrong) ip set), which will reset your ip-settings.
So the best option is NOT to fiddle with your ubuntu-network-settings, but to reset that bridge and step-by-stepping the manual instructions. Perhaps with your working windows box.

1. reset the bridge
2. wire it to your windows or ubuntu box
3. reboot that box
4. hopefully your box has got a matching ip, so that you can configure the bridge

---

### Post by moonsal on 2011-07-20
OK, done..... Everything is back to what it was in my first post, FRESH INSTALL (without network set up, tried and failed) and the bridge is configured and works great on my WinX systems (just plug in any system in the house and instant internet)but still no go for ubuntu??

I've searched and searched and read and read and still can't find anything about this... Any ideas??

---

### Post by jmoorse on 2011-07-20
Hello, please post the new output of:

```

cat /etc/network/interfaces
sudo dhclient
ifconfig -a

```

Please do not change the broadcast address, that will break things

---

### Post by moonsal on 2011-07-21
Interesting.... Never had the eth0:avahi before... 

```
cat /etc/network/interfaces

auto lo
iface lo inet loopback

```

```
sudo dhclient

Listening on LPF/eth0/00:00:c5:c1:73:e4
Sending on LPF/eth0/00:00:c5:c1:73:e4
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received
No working leases in persistent database - sleeping.

```

```
ifconfig -a

eth0     Link encap:Ethernet  HWaddr 00:00:c5:c1:73:34
         inet6 addr: fe80::200::fecl::73e4/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B) TX bytes: 1836 (1.8KB)
         Interrupt:10 Base address:0x3000

eth0:avahi Link encap:Ethernet  HWaddr 00:00:c5:c1:73:e4
           inet addr:169.254.11.14 Bcast:169.254.255.255 Mask:255.255.0.0
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           Interrupt:10 Base address:0x3000      
           

lo       Link encap: Local loopback
         inet addr:127.0.0.0 MASK 255.0.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436 Metric:1
         RX packets:148 errors:0 dropped:0 overruns:0 frame:0
         TX packets:148 errors:0 dropped:0 overruns:0 carrier:0        
         collisions:0 txqueuelen:0
         RX bytes:11728 (11.7 KB)  TX bytes:11728 (11.7 KB)
```

---

### Post by jmoorse on 2011-07-21
So basically you are not getting a valid IP address from your router.  What model is it?  Can you try plugging in to another port and rerunning the 'sudo dhclient' command and 'ifconfig -a'?

What we want is to see something like this in 'ifconfig' (the IPs will be different)

```

inet addr:192.168.45.7  Bcast:192.168.45.255  Mask:255.255.255.0

```

---

### Post by mokrates on 2011-07-21
Do you have hard-set IPs on your windows boxes? Do you use dhcp? If not, you would have to set up an ip manually.
OR:
Didn't you say, that your windows box has an internal wireless card? So, are you sure the bridge did work, when wired to it? If network was working, perhaps it was working through the internal card and not through the bridge?

the :avahi addresses are quite new. It's the same 'auto-address' which you probably know from windows.

---

### Post by moonsal on 2011-07-21
@mokrates

Yea, it's dhcp(made sure of it) and I disabled the wireless card before I plugged in the cat5 to the on-board nic. So the bridge does work...

@jmoorse
I understand all that except the port part.. It's been plugged in multiple systems and works and only have the one on this system unless you mean try to change the default port 80 which I really don't know how to do for both the router and nic? The router is a WRT54g..

Here's an idea maybe. Since I know my bridge works on this WinX box, you think maybe I should just hook up the bridge on it and put the wireless card(WMP54GS) in the ubuntu box??

---

### Post by mokrates on 2011-07-21
Hm. Then I don't know. If you plugged the ubuntu-box directly into the router once, and it worked, it should work over the bridge. Unless the reception is bad or sth.

---

### Post by moonsal on 2011-07-21
I agree Mo, that's whats got me miffed..lol I can take the ubuntu box and plug it in straight, just did as a matter of fact, and FLAWLESS... Even using the bridge here on this WinX box as I type... There's no reason it shouldn't work but it sure doesn't..:(:mad::mad:

---

### Post by mokrates on 2011-07-21
Prehaps you have a cross-cable, and the bridge doesn't support that? Other than that, i'm lost. sorry

---

### Post by moonsal on 2011-07-21
Nah, no cross-cable... No worries though, I appreciate the time and effort maan... One way or another this box will get up and runnin..lol

---

### Post by jmoorse on 2011-07-21
> **moonsal said:**
> @mokrates

Yea, it's dhcp(made sure of it) and I disabled the wireless card before I plugged in the cat5 to the on-board nic. So the bridge does work...

@jmoorse
I understand all that except the port part.. It's been plugged in multiple systems and works and only have the one on this system unless you mean try to change the default port 80 which I really don't know how to do for both the router and nic? The router is a WRT54g..

Here's an idea maybe. Since I know my bridge works on this WinX box, you think maybe I should just hook up the bridge on it and put the wireless card(WMP54GS) in the ubuntu box??
I meant physical port on the router/bridge that you are plugging you laptop in to.  Given the information you provided, this is note needed.  Let's check the driver installed for the nic:

```

sudo lshw -c NET

```

Please post the results, thanks

---

### Post by mokrates on 2011-07-22
if i recall correctly, the NIC was a rtl8139, which should be no problem at all, driver-wise

---

