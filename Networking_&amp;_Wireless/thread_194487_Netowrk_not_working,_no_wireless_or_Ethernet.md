---
title: "Netowrk not working, no wireless or Ethernet"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by csshuckster on 2006-06-11
problems with the networking on my laptop [COLOR="Red"]COMPAQ Presario V5000[/COLOR]

I have a Realtek RTL8139/810x Family Fast Ethernet NIC and for the wireless, it's a Broadcom 802.11b/g WLAN

Now I've tried the Broadcom tutorial in on of the other threads, but that did no goos, and I tried a few of the other threads suggestions, but none work.

So... here's the *ifconfig*

eth0 Link encap:Ethernet  HWaddr 00:0F:B0:FE:4A:7E
       UP BROADCAST MULTICAST  MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 b)  TX bytes:0 (0.0b)
       Interrupt:217 Base address:0x6000

lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING   MTU:16436  Metric:1
       RX packets:5 errors:0 dropped:0 overruns:0 frame:0
       TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX Bytes:272 (272.0 b)   TX bytes:272 (272.0 b)

route -n comes up with nothing and cat /etc/resolv.conf has the nameserver and the search domain i need to have in them.

Nothing is working, I don't have a clue as to what the hell is going on and this is getting very frustrating. eveything else is working, so I haven't a clue as to why, this is the only thing NOT working.

any help of any kind to get me started in some sort of directino would be greatly appreciated. Thanks.

---

### Post by spd106 on 2006-06-11
You need to provide more information, what are the outputs of **iwconfig** and **iwlist eth1 scan**?

Can you see the AP? Are you using any encryption? Do you have Network Manager installed?

---

### Post by csshuckster on 2006-06-12
**iwconfig**

lo: no wireless extensions

eth1: IEEE 802.11b/g ESSID:"3Com" Nickname:"Broadcom 4318"
        Mode: Managed  Access Point: Invalid   Bit Rate=1 Mb/s
        RTS thr: off   Fragment thr: off
        Link Quality:0  Signal level:0  Noise level:0
        Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0  Missed beacon:0

eth0: no wireless extensions

sit0: no wireless extensions


**iwlist eth1 scan**

eth1: no scan results


> Can you see the AP? Are you using any encryption? Do you have Network Manager installed?No, No, and yes.

---

### Post by cameronjreed on 2007-04-23
I have the same type of computer (Compaq Presario v5000 laptop)  It is running Ubuntu 7.04
I have connectivity via the wired connection, but NOT wireless.
I have a Realtek RTL8139/810x Family Fast Ethernet NIC and for the wireless, it's a Broadcom 802.11b/g WLAN
I ran all the same commands as mentioned above and get essentially the same results...

IWCONFIG
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

IWLIST Eth1 Scan
eth1      No scan results

I have been to several other threads in an attempt to get this working.
I have installed kNetworkManager
I have installed the bcm43xx-fwcutter and updated the firmware (when prompted)

I am a totally new to Ubuntu and Linux.
Can someone PLEASE help me.  I want to get wireless internet working on this laptop.

Thanks

---

