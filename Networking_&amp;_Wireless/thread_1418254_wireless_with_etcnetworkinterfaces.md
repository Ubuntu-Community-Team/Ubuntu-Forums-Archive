---
title: "wireless with /etc/network/interfaces"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by gfuggs on 2010-02-28
After too many problems with network-manager, I uninstalled it and attempted to use /etc/network/interfaces instead.

My eth0 works great, it's just a crossover connection to another computer.  eth1, the wireless connection, doesn't hook up with the specified essid, and I can't figure out why:

Here's why I get after booting up:
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11-a/b/g  ESSID:""  

```

Here's my /etc/network/interfaces:
```
auto lo	
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.100.200.11
	netmask 255.255.255.0
	broadcast 10.100.200.255

auto eth1
iface eth1 inet dhcp
	wireless-essid xxxxx

```

I need to manually type "iwconfig eth1 essid xxxx" and "dhclient eth1" to get a connection.  As a temporary fix I stuck it in /etc/rc.local.  Any ideas why it won't take the essid from /etc/network/interfaces???

---

### Post by gfuggs on 2010-03-01
Still wondering why this works:
iwconfig eth1 essid xxxx
dhclient eth1

But putting it in /etc/network/interfaces doesnt...

---

### Post by chili555 on 2010-03-01
I wonder if your computer is confused. You have asked it to set up both eth0 and eth1 as active automatically. Let's ask eth0 to stand down. Please try:> auto lo	
iface lo inet loopback

[COLOR="Red"]#[/COLOR]auto eth0
iface eth0 inet static
	address 10.100.200.11
	netmask 255.255.255.0
	broadcast 10.100.200.255

auto eth1
iface eth1 inet dhcp
	wireless-essid xxxxxNo encryption on this network?? My laptop and I will be right over!

Restart networking:```
sudo /etc/init.d/networking restart
```Does it work as expected?

---

### Post by gfuggs on 2010-03-01
> **chili555 said:**
> I wonder if your computer is confused. You have asked it to set up both eth0 and eth1 as active automatically. Let's ask eth0 to stand down. Please try:No encryption on this network?? My laptop and I will be right over!

Restart networking:```
sudo /etc/init.d/networking restart
```Does it work as expected?

Thanks for the suggestion, but I did try it with eth0 commented out, which yields the same result.  Also, the no encryption was a temporary thing while I was trying to get it working, just trying to eliminate as many things as possible.

---

### Post by 2hot6ft2 on 2010-03-01
I'm waiting with baited breath for you to find a solution for this. I started a thread about 4 weeks ago trying to do the same thing here:
[Ubuntu 2 Ubuntu via Ethernet while still using WiFi?]("http://ubuntuforums.org/showthread.php?t=1391343")

I'm still looking for the solution. I am curious as to why you're using eth1 for wifi instead of wlan0?

I know there's a solution. I have seen posts during my searching for the answer where others have done it but they never give a clear explanation of how they did it.

I know it involves using the "route" command and shaping the traffic so that both connections can be used without conflicts. Sending some things like SSH over the crossover cable and the rest over the WiFi to the internet. Might have to make some iptables rules. Tunneling?

Like this post I found on another forum that's a few years old but the poster was doing basically the same type of thing. This is really all there was worth while there. I didn't save the url (wish I had now).
```
OK

Looks like route solved my problem.

`route`
Code:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth1
localnet        *               255.255.255.0   U     0      0        0 eth0
loopback        *               255.0.0.0       U     0      0        0 lo
default         GW              0.0.0.0         UG    0      0        0 eth1

Ran:
route del default; route add default netmask 0.0.0.0 gw GW eth0

Code:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth1
localnet        *               255.255.255.0   U     0      0        0 eth0
loopback        *               255.0.0.0       U     0      0        0 lo
default         GW              0.0.0.0         UG    0      0        0 eth0
```
I even downloaded the ["Linux Advanced Routing & Traffic Control HOWTO pdf"]("http://lartc.org/lartc.pdf") and went thru it but it seems to still be eluding me. Perhaps you'll get more from it than I did so there's the link to it.

---

### Post by chili555 on 2010-03-02
For both of you, may we please see:```
route -n
```eth1 or ra0 or others may be used for a wireless interface depending on the driver module. For example, the laptop I am typing on now uses *ipw2200*. That driver module assigns the next available eth number; in my case, eth1.

---

### Post by 2hot6ft2 on 2010-03-02
> **chili555 said:**
> For both of you, may we please see:```
route -n
```eth1 or ra0 or others may be used for a wireless interface depending on the driver module. For example, the laptop I am typing on now uses *ipw2200*. That driver module assigns the next available eth number; in my case, eth1.
What I want to do is use a crossover cable to transfer files back and forth without using the WiFi which is for the internet connection which I want to still be active. The router is in another building.

On the one that will be the client. I'm using an external usb WiFi adapter, I have a few but just 1 connected so I don't know why it chose #3 for the wlan.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan3
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan3

```
On the one that is the SSH Server
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```
And thanks chili555 for taking an interest.

---

### Post by chili555 on 2010-03-02
I might be confused. If you are using a crossover cable, aren't you using eth0? It seems that the issue is to set up different routes for wireless than ethernet.```
man route
```> I don't know why it chose #3 for the wlan.When an interface is established, it associates a MAC address with the interface number. When you detached one device and inserted another, the next higher wlan number was set up. It is correctable; that is, roll your wlan number back to 0, if you are compulsive.

I'm sure with your credit card number and some shopping, we could verify if it would roll over to wlan100!

---

### Post by 2hot6ft2 on 2010-03-02
> **chili555 said:**
> I might be confused. If you are using a crossover cable, aren't you using eth0? It seems that the issue is to set up different routes for wireless than ethernet.```
man route
```When an interface is established, it associates a MAC address with the interface number. When you detached one device and inserted another, the next higher wlan number was set up. It is correctable; that is, roll your wlan number back to 0, if you are compulsive.

I'm sure with your credit card number and some shopping, we could verify if it would roll over to wlan100!
If I plug in the crossover cable (which uses eth0) the WiFi will disconnect and sine the WiFi is how I connect to the internet plugging it in right now would be useless. No I'm not compulsive about the wlan #...:D. But now I understand that it keeps track by the MAC Address of adapters for future use. I thought it forgot and started from 0 after each boot in which case it would be wlan1 right now.

You can see what I have tried in the other thread I made a few weeks ago here:
[Ubuntu 2 Ubuntu via Ethernet while still using WiFi?]("http://ubuntuforums.org/showthread.php?t=1391343")

---

### Post by chili555 on 2010-03-02
> If I plug in the crossover cable (which uses eth0) the WiFi will disconnectNetwork Manager at work, I'm afraid. In order to set up your */etc/network/interfaces* file and have it actually work, NM must be removed completely and, ideally purged. If you have your Ubuntu installation CD, you can always get it back, although you may find that your system works perfectly well without it. Several of mine certainly do. Here is what I suggest:> auto lo
iface lo inet loopback

[COLOR="Red"]auto eth0[/COLOR]
iface eth0 inet static
address 10.10.1.1
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255

auto wlan3
iface wlan3 inet dhcp
wireless-essid yourlittlerouter
wireless-key 0123456789Then the other computer would set its ethernet address as 10.10.1.2 and try to connect.

auto eth0 is needed or else it won't start automatically, although it would start with *sudo ifconfig eth0 up*.

I have very little experience with the crossover method, so you might have to play with all this a bit. I am, however, quite confident that NM will not easily cooperate.

---

### Post by 2hot6ft2 on 2010-03-02
I agree NM is pretty limited and even WICD wont support 2 simultaneous networks until version 2.0 if then. I'll have to make sure I have the required packages downloaded before I remove the network manager just in case I end up without any connections. It's snowing pretty good right now and I would hate to have to trudge back and forth to the other building to try and fix things if it doesn't work.

The laptop wouldn't be bad but moving the desktop might be a real pain. And would that work for WPA? I mean I wouldn't need to specify that it's a WPA AES key.

Thanks for the help.

P.S. I see you're in SC. I'm in NE AL and this is the wettest snow I've seen here in 20 years. Don't know if it will make it to where you are.

---

### Post by 2hot6ft2 on 2010-03-02
Would disabling network manager from startup applications make it possible to try the settings before removing network-manager?
It would sure make it easier to try it out first.
I'm going to give it a shot.

---

### Post by chili555 on 2010-03-02
> And would that work for WPA? I mean I wouldn't need to specify that it's a WPA AES key.Certainly. Please see [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

It is supposed to snow here today, but right now it's 39 F. I have a MUST medical procedure appointment, so I hope the snow doesn't interfere.

---

### Post by 2hot6ft2 on 2010-03-02
> **chili555 said:**
> Certainly. Please see [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

It is supposed to snow here today, but right now it's 39 F. I have a MUST medical procedure appointment, so I hope the snow doesn't interfere.
I tried it and the crossover connection worked as expected but no wifi where the key was it said invalid argument. Tried it with the wlan being dhcp and static. I'll go read thru the thread you linked to.

I just checked weather.com and unless you're in the far west part of the state you should be ok for your appointment.

---

### Post by chili555 on 2010-03-02
> I tried it and the crossover connection worked as expected but no wifi where the key was it said invalid argument. Tried it with the wlan being dhcp and static. I'll go read thru the thread you linked to.If you get your WPA set up correctly in interfaces, I think you'll bet all set.

Snowing furiously now, so we are leaving early. I'll check in later.

---

### Post by 2hot6ft2 on 2010-03-02
> **chili555 said:**
> If you get your WPA set up correctly in interfaces, I think you'll bet all set.

Snowing furiously now, so we are leaving early. I'll check in later.
Ok, thanks again and have a safe trip.

---

### Post by 2hot6ft2 on 2010-03-02
OK. After following the thread you linked to I have WPA working and can connect without network manager. But when I put both eth0 and wlan3 in the interfaces file the eth0 connects but wlan doesn't.

So still unable to use both adapters at the same time.

Here's what I did.

Made the key using
```
wpa_passphrase your_ssid your_psk
```
Added it to /etc/wpa_supplicant.conf
following the instructions and changing TKIP to AES so I had this
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
	ssid="myapidhere"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP AES
        group=CCMP AES
	psk=reallylongstringoflettersandnumbershere
}

```
This works for wlan
On the client (laptop) /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto wlan3
iface wlan3 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan3 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

On the server (desktop) /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```
So the WiFi works with the setup. I can ping back and forth and connect by SSH over the WiFi.

Now if I add the LAN crossover to the configuration like this

On the client (laptop) I changed /etc/network/interfaces to
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.10.1.1
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255

auto wlan3
iface wlan3 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan3 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

On the server (desktop) I changed /etc/network/interfaces to
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.10.1.2
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255

auto wlan0
iface wlan0 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```
Here's route -n on the desktop. I didn't think to run it before starting this post on the laptop but I'm sure it would be about the same.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.1.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```
I can ping back and forth by the eth0 adapter using the 10.10.1.x addresses but not by the WiFi. I get
**Network is unreachable** when attempting to ping by wlan addresses which are assigned by the router to be static and can't reach the internet.

So I still have this.

The WiFi works.
The LAN crossover works.
They both just wont work at the same time.

I think the answer is going to be in using the route command to add the second network.

---

### Post by chili555 on 2010-03-02
> auto eth0
iface eth0 inet static
address 10.10.1.2
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255

Isn't the server (desktop) _only_ connecting to the laptop? Wouldn't that make the laptop the gateway? I wonder if it would work if the interfaces file for the server read, in part:```
auto eth0
iface eth0 inet static
address 10.10.1.2
netmask 255.255.255.0
gateway 10.10.1.[COLOR="Red"]1[/COLOR]
broadcast 10.10.1.255 
```As I said, I have little experience with crossover. I have certainly never even tried to get two interfaces, LAN and WAN, working at the same time. I am sure it can be done, but maybe not by me!

---

### Post by 2hot6ft2 on 2010-03-02
> **chili555 said:**
> Isn't the server (desktop) _only_ connecting to the laptop? Wouldn't that make the laptop the gateway? I wonder if it would work if the interfaces file for the server read, in part:```
auto eth0
iface eth0 inet static
address 10.10.1.2
netmask 255.255.255.0
gateway 10.10.1.[COLOR="Red"]1[/COLOR]
broadcast 10.10.1.255 
```As I said, I have little experience with crossover. I have certainly never even tried to get two interfaces, LAN and WAN, working at the same time. I am sure it can be done, but maybe not by me!
No the desktop is also using WiFi to connect to the Internet. I think I tried with a gateway before and it still worked the same. But I'll give it a shot.

---

### Post by 2hot6ft2 on 2010-03-02
No such luck that still brings up the eth0 but not the wlan.

Say there is someone on each pc and they are using the internet by wifi.
There should be a way to transfer files by crossover cable at the same time.

I used to do it with a usb bridge years ago in (you know what).

---

### Post by chili555 on 2010-03-02
Do both show IP addresses in ifconfig for both eth0 and wlan0? That is, do they both seem to be following the */etc/network/interfaces* directives?

---

### Post by gfuggs on 2010-03-02
Just to clarify, both my wired crossover connection and wireless internet connection work simultaneously.

My problem is that even though I have both as auto in /etc/network/interfaces, only the eth0 comes up automatically.

After booting, I need to type the following to get wireless to come up:
"iwconfig eth1 essid xxxx"
"dhclient eth1"

I can't figure out why it doesn't come up automatically based on what's in my /etc/network/interfaces:
```
auto lo	
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.100.200.11
	netmask 255.255.255.0
	broadcast 10.100.200.255

auto eth1
iface eth1 inet dhcp
	wireless-essid "xxxxx"
	


```

I don't have any issues with routing; my internal network is 10.x.x.x, and my wireless router is 192.x.x.x.  I didn't have to do anything to make this work, both nfs and ssh find their way to the right place if I direct them to a internal address.

---

### Post by 2hot6ft2 on 2010-03-02
> **chili555 said:**
> Do both show IP addresses in ifconfig for both eth0 and wlan0? That is, do they both seem to be following the */etc/network/interfaces* directives?
No just the eth0 (this is the desktop (server)) and yet wlan0:avahi has another ip address.
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:99:be:95  
          inet addr:10.10.1.2  Bcast:10.10.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:cd43:be95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3853 (3.8 KB)
          Interrupt:21 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0b:38:c8:27:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:0b:38:c8:27:67  
          inet addr:169.254.7.21  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-0D-88-C8-27-67-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.1.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```

---

### Post by gfuggs on 2010-03-02
What is your output from "iwconfig" in that situation Mr. 2?

If your essid shows up as blank, do this:
"iwconfig wlan0 essid xxxx"
"dhclient wlan0"

replacing xxxx with whatever is appropriate.

---

### Post by gfuggs on 2010-03-02
Sorry, forgot to mention that if you'll need to make necessary adjustment for encryption.  For example, for WEP, I use:
iwconfig wlan0 essid "xxxx" key f0f0f0f0f0

---

### Post by 2hot6ft2 on 2010-03-02
> **gfuggs said:**
> Just to clarify, both my wired crossover connection and wireless internet connection work simultaneously.

My problem is that even though I have both as auto in /etc/network/interfaces, only the eth0 comes up automatically.

After booting, I need to type the following to get wireless to come up:
"iwconfig eth1 essid xxxx"
"dhclient eth1"

I can't figure out why it doesn't come up automatically based on what's in my /etc/network/interfaces:
```
auto lo	
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.100.200.11
	netmask 255.255.255.0
	broadcast 10.100.200.255

auto eth1
iface eth1 inet dhcp
	wireless-essid "xxxxx"
	


```

I don't have any issues with routing; my internal network is 10.x.x.x, and my wireless router is 192.x.x.x.  I didn't have to do anything to make this work, both nfs and ssh find their way to the right place if I direct them to a internal address.
Glad to hear it. Maybe we can make some headway on it then. I can live with creating a launcher to kick it off from the panel if nothing else.

Rebooting the desktop now. Why are you using eth1 for the wifi?

---

### Post by 2hot6ft2 on 2010-03-02
> **gfuggs said:**
> What is your output from "iwconfig" in that situation Mr. 2?

If your essid shows up as blank, do this:
"iwconfig wlan0 essid xxxx"
"dhclient wlan0"

replacing xxxx with whatever is appropriate.
on the desktop
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"myapid"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by 2hot6ft2 on 2010-03-02
```
sudo dhclient wlan0
```
Gives me 
> Listening on LPF/wlan0/00:0d:88:c8:27:67
Sending on   LPF/wlan0/00:0d:88:c8:27:67
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by gfuggs on 2010-03-02
I would temporarily turn off wireless security while you troubleshoot this, if that's an option for you.

If you can't still can't get dhcp to work for your wireless, try a static ip.

---

### Post by 2hot6ft2 on 2010-03-02
> **gfuggs said:**
> I would temporarily turn off wireless security while you troubleshoot this, if that's an option for you.

If you can't still can't get dhcp to work for your wireless, try a static ip.
Well that was fun. I couldn't connect without it. Had to take the laptop to the other building and plug it into the router to turn it back on.

I have the static ip address assigned by the router and I can connect with wifi. It's just that I can't seem to get both wifi AND ethernet to work at the same time.

---

### Post by gfuggs on 2010-03-02
Heh, when I was messing with mine I accidentally turned off wireless instead of turning off security.  That involved digging an old laptop out and a trip to the basement.

---

### Post by 2hot6ft2 on 2010-03-02
I was looking at the man pages for iwconfig and found that "Passphrase is currently not supported" which is what my encryption is WPA AES. So I'm looking into the man pages for ifconfig and route but I'm about ready to call it quits for the day. So I'll check in on this tomorrow.

---

### Post by chili555 on 2010-03-02
> "Passphrase is currently not supported"It is not supported for WEP. For WPA, the easiest way is to set up /etc/wpa_supplicant.conf.

Here is a guide: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Skip the Network Manager part and skip down to about here: **[SIZE="3"]WPA Supplicant[/SIZE]**

---

### Post by 2hot6ft2 on 2010-03-03
> **chili555 said:**
> It is not supported for WEP. For WPA, the easiest way is to set up /etc/wpa_supplicant.conf.

Here is a guide: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Skip the Network Manager part and skip down to about here: **[SIZE="3"]WPA Supplicant[/SIZE]**
Ok, that was bassically the same as the how to thread you had me follow which by the way was sweet and it was how I got the WPA working.
It did have me create the file /etc/default/wpasupplicant and put in it
>   ENABLED=1
  OPTIONS="-iwlan3 -c/etc/wpa_supplicant.conf -Dwext -w"

When I tried running
```
sudo wpa_supplicant -iwlan3 -c/etc/wpa_supplicant.conf -Dwext -w
```
It gave me
wpa_supplicant: invalid option -- 'w'
so I removed the -w option and got
> $ sudo wpa_supplicant -iwlan3 -c/etc/wpa_supplicant.conf -Dwext
Line 9: invalid cipher 'AES'.
Line 9: failed to parse pairwise 'CCMP AES'.
Line 10: invalid cipher 'AES'.
Line 10: failed to parse group 'CCMP AES'.
Line 12: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
So I removed the lines
>         pairwise=CCMP AES
        group=CCMP AES
from /etc/wpa_supplicant.conf
and now running
```
sudo wpa_supplicant -iwlan3 -c/etc/wpa_supplicant.conf -Dwext
```
It tries to associate with my AP which since I'm already connected to it it fails but it tells me it's working.
I tried the commands that gfuggs posted
> **gfuggs said:**
> Sorry, forgot to mention that if you'll need to make necessary adjustment for encryption.  For example, for WEP, I use:
iwconfig wlan0 essid "xxxx" key f0f0f0f0f0
and when I add my psk that was generated earlier or my passphrase it gave a not supported error. Also tried using my passphrase instead of the psk.
I don't see why I would need to run the command anyway since it connects fine when the eth0 configuration is left out of the interfaces file, and since my SSID is displayed but I tried it anyway.
> **gfuggs said:**
> What is your output from "iwconfig" in that situation Mr. 2?

If your essid shows up as blank, do this:
"iwconfig wlan0 essid xxxx"
"dhclient wlan0"

replacing xxxx with whatever is appropriate.
I also tried putting the wlan configuration above the eth in the interfaces file with no change. No surprise there but eh worth a shot.

So here are a couple questions for gfuggs:

1) Is there any reason for using eth1 for the wifi as opposed to wlan0?

2) Have you made any other chages besides the interfaces file you posted earlier to get this to work?

---

### Post by gfuggs on 2010-03-03
1) No, no reason.

2) apt-get remove --purge network-manager

I'm also using WEP, not WPA, so the iwconfig wlan0 essid "xxxx" key f0f0f0f0f0 might be different for you.  (The only reason I have WEP is I initially had no security while I was getting everything working, and I just put WEP on because it was easier than trying to figure out WPA- that's on the list for the weekend).

To take a step back and give you a summary of what I have done....
1) turn off wireless security on the router
2) apt-get remove --purge network-manager
3) /etc/network/interfaces:
auto lo	
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.100.200.11
	netmask 255.255.255.0
	broadcast 10.100.200.255

auto eth1
iface eth1 inet dhcp
	wireless-essid "blah"

4) /etc/rc.local (still not sure why it doesn't come up automatically, so I stuck this here instead of having to type it every time I reboot)
iwconfig eth1 essid "blah"
dhclient eth1

5)  At this point, I reboot and both are working

---

### Post by 2hot6ft2 on 2010-03-03
> **gfuggs said:**
> 1) No, no reason.

2) apt-get remove --purge network-manager

I'm also using WEP, not WPA, so the iwconfig wlan0 essid "xxxx" key f0f0f0f0f0 might be different for you.  (The only reason I have WEP is I initially had no security while I was getting everything working, and I just put WEP on because it was easier than trying to figure out WPA- that's on the list for the weekend).

To take a step back and give you a summary of what I have done....
1) turn off wireless security on the router
2) apt-get remove --purge network-manager
3) /etc/network/interfaces:
auto lo	
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 10.100.200.11
	netmask 255.255.255.0
	broadcast 10.100.200.255

auto eth1
iface eth1 inet dhcp
	wireless-essid "blah"

4) /etc/rc.local (still not sure why it doesn't come up automatically, so I stuck this here instead of having to type it every time I reboot)
iwconfig eth1 essid "blah"
dhclient eth1

5)  At this point, I reboot and both are working
Thanks gfuggs for taking the time to lay all that out for me it looks like step 4) in your list must be what I'm missing as I haven't done anything with /etc/rc.local.
I'll start looking at the options for what all can be added to it now in addition to what you listed.

For the WPA the 2 links chili555 gave were very helpful. The first one made it possible to connect with WPA using the interfaces file without network manager.
Here's that link: [HowTo: WPA with wpa_supplicant]("http://ubuntuforums.org/showthread.php?t=263136")

The second one is a lot like the first except it had me add info to the /etc/default/wpasupplicant file as in post #34 above.
Here's that link: [WifiDocsWPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo")

I'll play with both computers some tomorrow. Then it will just be a matter of solving the auto start issue that you're having (which I will too once they both work together). Hopefully I'll stumble across the answer tonight.

Have you considered a startup script (thought I would ask before looking into that option)?

---

### Post by gfuggs on 2010-03-04
All rc.local is, is a script that runs at startup.

You don't need to worry about that until you figure out how to bring up your network.  If you can't make it work using a terminal, rc.local will do absolutely nothing for you.  Please ignore it for now. 

When my computer boots up, I need to type "iwconfig eth1 essid "alsdjf"" to tell it which wireless network to connect to, then I need to tell it "dhclient eth1" to get an address using dhcp.  Rather than doing that at every reboot, it goes in rc.local, where the two commands are run automatically.

---

### Post by gfuggs on 2010-03-04
Also, another resource that you might want to check out is this:
[http://www.linuxhomenetworking.com/]("http://www.linuxhomenetworking.com/")

They're a bit on the long side, but easy to read and well worth it, IMO. 

Specifically take a look at these sections:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking")
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch02_:_Introduction_to_Networking]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch02_:_Introduction_to_Networking")
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking")
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting")

---

### Post by 2hot6ft2 on 2010-03-04
> **gfuggs said:**
> All rc.local is, is a script that runs at startup.

Yeah, I found that out right after posting that. I've been reading a lot of things about [ubuntu rc local not running]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&q=ubuntu+rc+local+not+running&start=10&sa=N")

I'll go read thru the links you gave now. Thanks

---

