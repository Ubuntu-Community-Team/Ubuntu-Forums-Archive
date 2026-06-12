---
title: "A plea for help with WN825GP wireless card"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by cookevillain on 2005-12-27
Hi,

Could someone please help me to get my wireless network to run. I am trying to install a Motorola's WN825GP PCMCIA notebook adapter on my Toshiba Satellite 2530CDS laptop running Ubuntu 5.10. I have read other posts about (similar?) WN825G cards and people seem to be having a lot of success with that card under ndiswrapper. Is mine that different? I know that there seems to be a working driver for Broadcom chipset now but I am not sure this card uses one or that the driver (which seems pretty raw now) would work. Anyone knows anything about that?

I have installed ndiswrapper and got to the point when the power light would come on but the link light would stay ulit. I have no WEP activated (i.e. everything is run as an open network). Please read below for more info/test output. Any help will be greatly appreciated.

-----------------------------------------------Extra info------------------------------------------------------------------
# ndiswrapper -l

says

Installed ndis drivers:
bcmwl5 driver present, hardware present.

Here is the output of ifconfig and iwconfig:

ifconfig:

wlan0 Link encap:Ethernet HWaddr 00:0C:E5:52:BF:81
inet6 addr: fe80::20c:e5ff:fe52:bf81/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Memory:6800000-6801fff

iwconfig:

wlan0 IEEE 802.11g ESSID off/any
Mode:Managed Frequency:2.462 GHz Access Point: 00:00:00:00:00:00
Bit Rate:54 Mb/s Tx-Power:25 dBm
RTS thr:2347 B Fragment thr:2346 B
Encryption keyff
Power Managementff
Link Quality:100/100 Signal level:-10 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:59112 Missed beacon:0

Then, if I try to run 'dhclient wlan0:' it says:

There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit
url here ...

sit0: unknown hardware address type 776
irda0: unknown hardware address type 783
sit0: unknown hardware address type 776
irda0: unknown hardware address type 783
Listening on LPF/wlan0/00:0c:e5:52:bf:81
Sending on LPF/wlan0/00:0c:e5:52:bf:81
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
...

Running the scan results in:

root@ubuntu:/etc# iwlist wlan0 scan
wlan0 Scan completed :
Cell 01 - Address: 00:0C:E5:53:50:B4 (my wireless router address---checked on the box)
ESSID:"motorola 0B4"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:0/100 Signal level:-39 dBm Noise level:-256 dBm
Encryption keyff
Bit Rate:1 Mb/s
Bit Rate:2 Mb/s
Bit Rate:5.5 Mb/s
Bit Rate:11 Mb/s
Extra:bcn_int=100
Extra:atim=0

... But sometimes (seconds later) it would say:

root@ubuntu:/etc# iwlist wlan0 scan
wlan0 No scan results

Needless to say I cannot connect anywhere. If it matters I use Motorola's WR850GP router with its native firmware.
Can someone please help me figure out what is going on?
Are WN825G and WN825GP different enough so that WN825GP is not supported and is not going to work under Linux? Any help will be greatly appreciated. Thanks

Alex

---

### Post by Lambert on 2005-12-27
I see your problem but not sure about an answer at this moment.

> iwconfig:

** wlan0 IEEE 802.11g **

---

Cell 01 - Address: 00:0C:E5:53:50:B4 (my wireless router address---checked on the box)
ESSID:"motorola 0B4"
** Protocol:IEEE 802.11b** 
Your router is broadcasting in protocol .11b but your card is set up to receive in protocol .11g

so need to figure how to change the driver so it runs in .11b mode.

post the output of this command here.

sudo iwpriv wlan0

You may not get anything, not sure if/how ndiswrapper handles ioctls.

edit: this is the command to change it to .11b

```
sudo iwpriv wlan0 network_type b
```

---

### Post by cookevillain on 2005-12-27
You are absolutely right: even though the protocol the card sees is 802.11b, I did set the router to broadcast in ..11g exclusively. Another strange thing: when I activate the card next to a laptop running a functioning wireless under WinXP, the WinXP machine sees the card for about half a minute and claims it is running in Ad-hoc mode (even though I set it to Auto) and then it disappears.

Here is the out put of iwpriv:

root@ubuntu:/home/alex# sudo iwpriv wlan0
wlan0     Available private ioctls :
          setwpa           (8BE1) : set   1 int   & get   0
          setkey           (8BE2) : set   1 int   & get   0
          associate        (8BE3) : set   1 int   & get   0
          disassociate     (8BE4) : set   1 int   & get   0
          drop_unencrypted (8BE5) : set   1 int   & get   0
          countermeasures  (8BE6) : set   1 int   & get   0
          deauthenticate   (8BE7) : set   1 int   & get   0
          auth_alg         (8BE8) : set   1 int   & get   0
          ndis_reset       (8BF0) : set   0       & get   0
          power_profile    (8BF1) : set   1 int   & get   0
          network_type     (8BF2) : set   1 char  & get   0

Thanks so much for your reply---I am getting pretty desperate.

I just saw your edit: I did run this command and the machine replied that `interface does not accept private ioctl' (I guess the price we pay for letting a part of XP in our pristine world ... ;] )

Alex

---

### Post by cookevillain on 2005-12-29
Ok, I am giving up. I guess the only thing left to do is to wait for the native drivers to come along or give up on wireles under Linux altogether. If anyone has any idea about how to make the card work with ndiswrapper, please let me know.

In case some poor soul has the same problem as I do, here is the info on the card:

Motorola WN825GP (not ...G, this one is the `enhanced' version), the output of various commands can be found elsewhere in this thread. I was able to get to the point where the card's `link' led would blink as dhclient searched for the router and where the iwlist wlan0 scan command outputs the correct info for the router (only when I put the card in Auto mode) but I could never actually connect to the router. If you know how to get the card to work, please post here. If you have lost hope, at least find comfort in knowing you are not alone. Motorola is on my black list from now on (I did not buy this card though, and will never buy anything with Motorola on it unless it also says `linux is supported').

Alex

---

