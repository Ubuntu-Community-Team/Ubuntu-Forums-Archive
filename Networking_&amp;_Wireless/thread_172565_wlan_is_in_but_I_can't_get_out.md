---
title: "wlan is in but I can't get out"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by gwpritch on 2006-05-08
](*,)    This says it all!!!

I have been working my way through setting up my linksys wpc54g notebook adapter and wrt54g router.

I installed the windows driver lsbcmnds.inf via ndiswrapper and it worked fine the  
module was loaded and wlan0 showed up in iwconfig

```
IEEE 802.11g  ESSID:off/any Nickname:"gwpritch"
Mode:Managed  Frequency:2.412 GHz Access Point 00:00:00:00:00:00
Bit Rate=54 MB/s  Tx-Power: 25 dBm
RTS thr=2347 B  Fragment thr=2346 dBm
Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0   Invalid misc:0  Missed beacon:0

```
ifconfig gives:

```
lo     etc  etc

wlan0

Link encap:Ethernet  HWaddr 00:14:BF:CA:3E:72
inet addr:192.168.1.110  Bcast:192.168.1.255 Mask 255:255:255:0
inet6 addr: fe80::214:bfff:feca:3e72/64  Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
Rx bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
Memory:ac00000-ac01fff
```

/etc/network/interfaces reads

```
auto lo
iface lo inet loopback

mapping hotplug
script grep
map wlan0

iface wlan0 inet static
     wireless_mode Managed
     wireless_essid linksys
     wireless_nick gwpritch
     address 192.168.1.110
     netmask 255.255.255.0
     network 192.168.1.0
     broadcast 192.168.1.255
     gateway 192.168.1.1

auto wlan0

```
Network Settings shows the Interface wlan0 is active

yet I get nothing. Can't even ping the router.

Can anyone help. In a weak moment I found myself longing for windoze and I've been a linux devotee for the better part of 8 years.

---

### Post by Azrael on 2006-05-08
What I'd do first in a situation like this, is to use ethereal to see if there are *any* packets going in or out.

edit: "Access Point 00:00:00:00:00:00" probably means you are not associated with your AP. Check your syslog for hints.

---

### Post by gwpritch on 2006-05-09
There appears to be no traffic at all :( 
Googling around I found a reference to suggest using the NT driver instead of the 9x driver from the install CD with ndiswrapper. I'm going to try that and see what happens.

Does my interfaces file look ok. Some examples I have seen have both an eth0 and wlan0 entry. Is this just in the case of two separate nic for lan and internet?

BTW this card is wpc54g version 3. Is that a problem? The linksys site doesn't even have a driver available for version 3, only 1,2 and 4.

---

### Post by dickohead on 2006-05-09
disable security on the router, broadcast the SSID and run the following commands:

sudo ifdown wlan0
sudo ifup wlan0

see if that helps.

---

### Post by jml on 2006-05-09
To be quite frank, I have never been able to get a Linksys PCMCIA card to work with Linux.  The wireless base station works fine.  If you can, I would suggest selling the card and get either a Netgear WG511T card, or a Cisco Aironet 802.11 a/b/g card.  The Aironet is more expensive, but its more linux compatible.  Cisco even offers Linux drivers on their web site.  If you can live with 802.11b connectivity then you may want to try and find an Orinoco Gold Classic card.  They are no longer manufactured, but you may find one on e-Bay.  Another good 802.11b card is the Cisco Aironet 350.  Its still available from the Cisco website.  Hope this helps.

Joe

---

### Post by gwpritch on 2006-05-10
dickohead: thanks...tried all that...no joy

jml:  I'm just about at that point. Thanks for the suggestions.


My forehead is getting pretty flat and sore. Still got to try the NT driver but I'm not holding out much hope. Still accepting any 11th hour suggestions though. 

Have a good one. Cheers y'all!

---

### Post by deathbyswiftwind on 2006-05-11
have you tried the win xp driver? the only drivers ive ever had really work and work well were xp ones some nt ones and sometimes not all the time mind you xp and nt are the same

---

### Post by gwpritch on 2006-05-11
The box the card came in claims it was designed for winXP ( which should have scared the hell out of me from the start) but in the Driver folder there is only 9x and NT folders so I assume NT an XP use the same driver. The same is true for the file I downloaded from the list on the wiki site.
I am going to try this out tonight.
I think I will also compile the latest ndiswrapper rather than the supplied v1.1.
Here's hopin'

---

### Post by gwpritch on 2006-05-14
After fiddling around and wasting another couple of nights I finally said  'sc##' and returned the blasted thing to Future Shop. Went to Staples and bought a D-Link DWL-G650....WORKED RIGHT OUT OF THE BOX!!!!!!

:)  :D 8) 

Thanks for the help all.

---

### Post by john_van_v on 2006-05-14
I have a D-Link G630, not quite the G650, but...

It the on-light turns on, the communication light blinks as I am booting up.

The configuration tool shows the name of the wireless router correctly, but the configuration tool fails to make a DHCP connection.

ifconfig produces output for it, but shows no IPv4 address, of course.

Does anyone have any suggestions ??

---

