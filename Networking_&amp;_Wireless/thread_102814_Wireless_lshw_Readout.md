---
title: "Wireless lshw Readout"
date: 2005-12-12
forum: Networking &amp; Wireless
---

### Post by haze03 on 2005-12-12
Having trouble with wireless like many, so went through the troubleshhoting guide.  Here is what I got on first step.  Where am I screwing up?

description: Wireless interface
product: Ralink RT2500 802.11 Cardbus Reference Card
vendor: RaLink
physical id: c
bus info: pci@00:0c.0
logical name: ra0
version: 01
serial: 00:0e:2e:5d:59:04
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2500 multicast=yes wireless=RT2500 Wireless
resources: iomemory:dc000000-dc001fff irq:11

---

### Post by Lambert on 2005-12-12
Not sure, what problems are you having? Your output shows the device is recognized and the rt2500 driver is allocated to the device. Next steps is to associate to the ap and then receive an ip address.


go here to see if you can configure the interface.

system>admin>networking

After you configure and activate iface, check iwconfig to see if you're associated with your ap. Should get a line like this.

 Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:46:1A:BC:7E

If you see all zeros after access point then you're not associating with the ap

Are you using wep or wpa encryptioin? If so give the detail on type and settings.

---

### Post by haze03 on 2005-12-12
I already configured and activated under networking.  However, I can't get on-line or access the network.  I use WEP.  I typed it in the network settings as ASCII.  After running iwconfig I get this:

lo no wireless extension

eth0 no wireless extensions.

ra0   RT2500 Wireless ESSID: “2WIRE356”
Mode- Managed Frequency- 2.437 GHz Access Point- 00:0D:72:85:8A;A1E
      Bit Rate- 11 Mb/s 
      RTS thr:off Fragment thr- off
      Link Quality=70/100 Signal level=-53 dBm Noise level=-193 dBm
      Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
      Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by Lambert on 2005-12-13
Ok, so on to next steps.

1. Do you have an ip assigned to the device. You can find this out with the command ifconfig. Should say inet addr: xxx.xxx.x.x on the second line

2. If you have an ip address then next thing to do is to ping 
try to ping router 
try to ping external address using their ip address
try to ping external address using common name ([www.google.com](www.google.com))

Post results of your pings here.

---

### Post by haze03 on 2005-12-30
ok been offline a couple weeks, bust still can't get this running.  here is my readout from ifconfig:

lo
link encap:local loopback
inet addr:127.0.0.1 Mask:2555.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436  Metric:1
RX packets:12266240 errors:0 dropped:0 overruns:0 frame:0
TX packets:12266240 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelan:0
RX bytes:918820813  (876.2 MiB) TX bytes:918820813 (876.2 MiB)

ra0
link encap:Ethernet HWaddr: 00:0E:2E:5D:59:04
inet6 addr:  fe80::20e:2eff:fe5d:5904/64 Scope:Link
UP BROADCAST RUNNING MUKTICAST MTU:1500  Metric:1
RX packets:313497 errors:0 dropped:0 overruns:0 frame:0
TX packets:180339 errors:10 dropped:0 overruns:0 carrier:0
collisions:1288 txquelan:1000
RX bytes:28312045  (27.0 MiB) TX bytes:1320563 (12.5 MiB)
Interrupt:11

---

### Post by haze03 on 2006-01-05
bump for help

---

### Post by Lambert on 2006-01-05
When I got to my linux box I'll come back to this. For now though here is something to try.

```
sudo dhclient ra0
```

if you're using dhcp on your router to assign ips. You should get something saying you're bound to an ip of xxx.xxx.x.x
If it doesn't work you might see no dhcp offers recieved or something like this.

If that doesn't work let's try to staticly get connected.

```
sudo ifconfig ra0 192.168.x.x up
```

```
sudo route add default gw xxx.xxx.x.x dev ra0
```

in first command replace the x's with numbers in your subnet range. (if your router's ip address is 192.168.0.1 then use 192.168.0.2, just make sure it's not an ip assigned to any other pc on the network)

In the second command I used 192.168.x.x, replace this with the ip address of your acces point.

NOw try to ping the router.

If your ping is succesful, you should be connected to the net, but you won't beable to surf as you you won't have a nameserver set up to resolve names. This step is just to ensure connectivity with the router.

Other information that I may need. You say you're using wep. If possible I would suggest removing wep and connecting via open signal just to make sure everything is working, then put encryption back in and figure out what needs to be configured to get it to work. You say you're using wep, what are the settings. Open or shared key? ascii or hexadecimal format? There might be a driver setting that needs to be changed. I need to dig into the doucmentation to find that.

---

### Post by Lambert on 2006-01-05
Double Post

---

### Post by haze03 on 2006-02-03
sorry, long time off dealing with crap.  anyhow, i tried checking dhcp and got No DHCOOFFERS received and No working leases in persistent database - sleeping.

the guy i rent from has som funky 2wire router/modem/switch something from the dsl company.  i don't know much about it and he is techno dunce.  he can turn a computer on and vheck fantasy football and that is about it.

---

### Post by haze03 on 2006-02-05
bump for help

---

### Post by haze03 on 2006-02-16
bump

---

### Post by haze03 on 2006-02-20
bunp for help

---

