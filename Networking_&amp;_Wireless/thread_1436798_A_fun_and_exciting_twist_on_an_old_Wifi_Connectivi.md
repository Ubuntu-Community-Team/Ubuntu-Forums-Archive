---
title: "A fun and exciting twist on an old Wifi Connectivity problem!"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by Aped on 2010-03-23
Ha ha okay, I lied about the fun and exciting bit, but this does seem pretty novel, at least to me.

WiFi on this laptop worked fine for a few months then went out; after a reinstall of ubuntu (since 9.xx had come out since then anyway) the wireless still refused to even see networks, let alone connect to them; under Wireless Networks in the NM, I just see a greyed out 'disconnected'. This got me to thinking that it may have just been a hardware issue, but I find that hard to believe. Anyway, here's the pertinent information: 

Started off with an lshw command just to see if a network adapter is even listed as being connected: 
`lshw`
```

id:	
network:1
description: 	Wireless interface
product: 	PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: 	Intel Corporation
physical id: 	
3
bus info: 	
pci@0000:03:03.0
logical name: 	
eth1
version: 	05
serial: 	00:13:ce:62:f4:7b
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	ipw2200
driverversion	=	1.2.2kmprq
firmware	=	ABG:9.0.5.27 (Dec 12 2007)
latency	=	64
link	=	no
maxlatency	=	24
mingnt	=	3
multicast	=	yes
wireless	=	radio off
resources:	
irq	:	17
memory	:	dfdfd000-dfdfdfff

```

Well lo and behold, it's just called eth1 but according to this, it's there and seems to be maybe working, maybe? What's ifconfig say about eth1?
`ifconfig`:
```

eth1      Link encap:Ethernet  HWaddr 00:13:ce:62:f4:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x8000 Memory:dfdfd000-dfdfdfff 

```

so it thinks the adapter is an ethernet adapter? I don't get it. 

For good measure, then, `iwconfig`:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Wat? I was in the middle of a download when this STOPPED working the first time, which just boggles my mind. 

If any of you guys have ideas (or just need some more info) please do post away!


As an addendum: I found [this driver project]('http://ipw2200.sourceforge.net/index.php') but they claim to require a 2.6.8+ kernel; a quick `uname -r` shows that mine is 2.6.31, and an `apt-cache search linux-image` reveals that to be the highest available from repos; do Debian/Ubuntu distros not use more recent kernels or is this an Ubuntu-specific kernel naming scheme? If so, to what would it be comparable? I'm hesitant to try to install this and change my firmware if it's likely I'll be borking something. Thanks again for reading, I realize it's a bit long-winded.

---

### Post by chili555 on 2010-03-23
Please do not install a new driver and please do not download and install new firmware, because it won't work. Only one thing will work, find that switch or key combination that switches wireless and push it!> wireless	=	radio [COLOR="Red"]off[/COLOR]> eth1      radio [COLOR="Red"]off[/COLOR]  ESSID:off/any  
Now, perhaps the acpi or wmi implementation in your laptop doesn't allow the operating system to respond to hotkey presses appropriately, but that is not a driver or firmware issue.

The driver *ipw2200* uses eth1 as its interface, so that part is entirely correct.

What kind of laptop is it? What does this tell us:```
rfkill list
sudo rfkill unblock all
rfkill list
```

---

### Post by Aped on 2010-03-23
> **chili555 said:**
> Please do not install a new driver and please do not download and install new firmware, because it won't work. Only one thing will work, find that switch or key combination that switches wireless and push it!Now, perhaps the acpi or wmi implementation in your laptop doesn't allow the operating system to respond to hotkey presses appropriately, but that is not a driver or firmware issue.

The driver *ipw2200* uses eth1 as its interface, so that part is entirely correct.

What kind of laptop is it? What does this tell us:```
rfkill list
sudo rfkill unblock all
rfkill list
```

Thanks for the response. It's a Dell Inspiron 6000 and I just saw the solution to this as I read your post; I had NO idea that you could enable/disable a wifi card on such a level that reformatting wouldn't flip the switch back. Laptops are a relatively new thing to me... Anyway, as soon as you mentioned that, I went looking for a Function button that had a wifi symbol on it and sure enough, Fn+F2=WTF hax.

Now I feel silly, though, how many hours did I spend on this crap?

---

### Post by chili555 on 2010-03-23
I'm glad it's working for you. We all, including me, learn something new once or twice a day!

---

### Post by sarlaccpit on 2010-04-22
sadly this gives me nothing at all:
>  
rfkill list
sudo rfkill unblock all
rfkill list

 
I have a wlan switch to filck on my Sony Viao PCG-7F1M - This is in the 'on' status however i get the same output as Aped in the first thread. Is there any way i can force it on if the switch doesn't work?
It has worked before in the past but hasn't worked for a few months. [not used the laptop for a while]
 
I am on netbook remix
 
uname -r
2.6.31-19-generic

---

### Post by sarlaccpit on 2010-04-22
Some more info for you guys - I wonder if you can shed any light:
 
Ubuntu 9.10
2.6.31.19-generic i686
 
 
```
 
lsmod | grep 'ipw2200'
 
ipw2200                    140292    0
libipw                         43148    1 ipw2200
lib80211                        6432   2 ipw2200, libipw

```
 
 
```
 
iwlist scan
 
lo             Interface doesnot support scanning
eth0         Interface does not support scanning
eth1         No Scan results

```
 
 
```
 
/etc/init.d/networking restart
 
**edit to shorten the post **
 
No DHCP offers received
No Working leases in persistant database - sleeping

```
 
 
```
 
cat /etc/network/interfaces
 
auto lo
iface lo inet loopback
 
auto eth1
iface eth1 inet dhcp

```

---

### Post by chili555 on 2010-04-22
May we see:```
[COLOR="Red"]sudo[/COLOR] iwlist eth1 scan
dmesg | grep -e ipw -e eth
```Thanks.

---

### Post by sarlaccpit on 2010-04-22
Thanks :) 
 
Here is the output requested:
 
```
 
sudo iwlist eth1 scan
 
eth1      No scan results

```
 
 
and
 
```
 
 
[EMAIL="root@evil"]root@evil[/EMAIL]:~# dmesg | grep -e ipw -e eth
[    8.502925] eth0: RealTek RTL8139 at 0x2000, 00:01:4a:cb:5b:49, IRQ 17
[   27.167879] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   27.167882] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   27.167982] ipw2200 0000:06:0a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   27.248948] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   27.249048] ipw2200 0000:06:0a.0: firmware: requesting ipw2200-bss.fw
[   27.672125] ipw2200: Radio Frequency Kill Switch is On:
[   27.746289] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   27.748356] eth0: link down
[   27.748619] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.468020] eth1: no IPv6 routers present
[ 5625.354898] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6686.782646] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6935.686116] ADDRCONF(NETDEV_UP): eth1: link is not ready


```

---

### Post by chili555 on 2010-04-22
Would you please try:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 led=1
dmesg | grep -i kill
```See if there is any activity after [ 6935.686116].

You might also try:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 bt_coexist=1
```If either parameter works, we can tweak one file and make it permanent.

---

### Post by sarlaccpit on 2010-04-22
I get this now which is good [i think] 
 
```

[14678.272190] ipw2200 0000:06:0a.0: PCI INT A disabled
[14696.538627] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[14696.538635] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[14696.538754] ipw2200 0000:06:0a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[14696.538858] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[14696.538946] ipw2200 0000:06:0a.0: firmware: requesting ipw2200-bss.fw
[14696.714581] ipw2200: Radio Frequency Kill Switch is On:
[14696.715776] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
```
 
I have done an iwlist scan which has given me the same "No scan results" message on eth1. 
 
Is there anything else i can try please? I am at your mercy.
 
Thankyou
 
Sarlaccpit

---

### Post by chili555 on 2010-04-22
> [14696.714581] ipw2200: Radio Frequency Kill Switch is On:
It's really no better than it was. After you did the led=1 parameter, did the light or LED associated with the wireless switch work? Does the system recognize the switch activity at all?```
sudo tail -f /var/log/syslog
```Leave the terminal open and move the switch and see if the system recognizes any changes.

---

### Post by sarlaccpit on 2010-04-22
No light comes on to imply wireless is switched on.
 
Tailing the syslog as i move the switch in to the off position doesn't seem to do anything But when i move it in to the on position there is a delay before it seem to be looking for DHCP offers - and this starts and stops periodically:
 
```
 
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
dhclient: No DHCP offers received
dhclient:No working leases in persisent database.
 

```
 
Could be a hardware fault?

---

### Post by chili555 on 2010-04-22
> dhclient:No working leases in persisent database.When you get to this point, please do a Ctrl+C to stop the tail of syslog. Then do:```
sudo lshw -C network
```Now does it say 'radio off'?

Is Network Manager controlling networking or /etc/network/interfaces? It works best, and in most cases it only works, with one or the other, not both.

---

### Post by sarlaccpit on 2010-04-22
Yes it says "radio off"
 
NetworkManager is there and is active [according to ps -aux].
Though i did do a manual add of the eth1 interface to the /etc/network/interfaces file  yesterday... This, i must add, was out of desperation.
 
 
```

auto lo
iface lo inet loopback
 
auto eth1
iface eth1 inet dhcp

```
 
 
 :(

---

### Post by sarlaccpit on 2010-04-22
Ok, so i have now edited my interfaces file so it only has config for the loopback interface.
 
I have been in to nm-system-settings.conf and changed managed=false to managed=true
 
rebooted
 
```
 
sudo  rmmod -f ipw2200
sudo  modprobe ipw2200 bt_coexists=1

```
 
Now the syslog says:
 
```
 
NetworkManager <info> (eth1): device state change 1->2 (reason2)
NetworkManager <info> (eth1): bringing up device
NetworkManager <info> (eth1): preparing device
NetworkManager <info> (eth1): deactivating device (reason 2)
NetworkManager <info> (eth1): supplicant interface state: starting -> ready
NetworkManager <info> (eth1): device state change: 2 -> 3 (reason 42)
wpa-supplicant[754]: CTRL-EVENT-DISCONNECTED -Disconnect event - remove keys
avahi-daemon[661]: Registering new address record for fe80::213:ceff:faed:6c1a on eth1

```
 
Does this help?

---

### Post by chili555 on 2010-04-22
I doubt this is a wireless card problem; I think it is a Sony Vaio problem. If you Google 'sony vaio wireless switch,' you see many problems; not all Linux nor Ubuntu. 

I saw this: http://ipw2200.sourceforge.net/README.ipw2200[/url]> For the device level files, look in
	
	/sys/bus/pci/drivers/ipw2200/{PCI-ID}/

For example:
	/sys/bus/pci/drivers/ipw2200/0000:02:01.0

For the device level files, see /sys/bus/pci/drivers/ipw2200:

  rf_kill
	read - 
	0 = RF kill not enabled (radio on)
	1 = SW based RF kill active (radio off)
	2 = HW based RF kill active (radio off)
	3 = Both HW and SW RF kill active (radio off)
	write -
	0 = If SW based RF kill active, turn the radio back on
	1 = If radio is on, activate SW based RF kill

	NOTE: If you enable the SW based RF kill and then toggle the HW
  	based RF kill from ON -> OFF -> ON, the radio will NOT come back on
 You can find the bus ID number with:```
sudo lshw -C network
```Here is an example from my machine:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@[COLOR="Red"]0000:03:00.0[/COLOR]
       logical name: wlan0The idea is to do:```
sudo su
echo 0 > /sys/bus/pci/drivers/ipw2200/{PCI-ID}/rf_kill
exit

```You might have to fine tune this; it might be RFKILL or RFKILL0 instead of rf_kill. Look for it and please try it.

---

