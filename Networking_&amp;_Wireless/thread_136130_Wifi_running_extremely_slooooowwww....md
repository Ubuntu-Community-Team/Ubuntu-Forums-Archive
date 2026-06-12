---
title: "Wifi running extremely slooooowwww..."
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by chopsbuntu on 2006-02-25
I have Ubuntu 5.10 running KDE 3.5.1 on my HP Pavilion ze4600us laptop with an Orinoco Proxim Silver (802.11 b/g). I just replaced my Linksys WRT54G wireless router for the new WRT54GX4 which has the SRX400 technology.

Anyway, ever since I switched over to Ubuntu on the laptop, the wifi runs extremely slow. I have a 10Mbs cable business line, so I know that's not the problem. In fact, my wifi connection used to fly while I was running Windows XP Pro. And my signal strength is maxed out even two rooms away, so that isn't the problem either. And yes, everything is configured correctly with the router and wifi card.

So what is my problem? 

I'm thinking it has something to do with Ubuntu and the card itself. Either it has the wrong drivers or something because I am not getting anywhere near the speed I should be. The only drivers for the card are whatever ones got loaded while installing Ubuntu.

Are there better drivers or something that can be installed?

This is starting to really piss me off because I just spent $115 on this router which isn't improving anything at the moment, and I know this router works. My friend has the lower model and my laptop flies all the way on the other end of his house!

Please help me with this. :confused: :confused:

---

### Post by jamesr on 2006-02-25
You state
> My friend has the lower model and my laptop flies all the way on the other end of his house!


If I am reading your comments correctly, if your laptop works well with another system surely that puts the problem in the router or the router/card connection protocol.

---

### Post by chopsbuntu on 2006-02-25
[QUOTE=jamesr]You state


If I am reading your comments correctly, if your laptop works well with another system surely that puts the problem in the router or the router/card connection protocol.[/QUOTE]

Yes and no. You did read it correctly, but I just didn't say it right.

What I meant to say was that while I had WinXP on my laptop, I had a fast connection at my house and his. He brought his laptop over to my house and his flies, even more so with my new router.

The problem IS with Ubuntu and my wifi card, not my network, router, or connection protocol. Everything is configured as it should be hardware wise. I put WinXP back on my laptop yesterday just to prove I configured the new router properly, and it is. My laptop was acting like it was wired into the network. Transfer speeds from my server's HD to the laptop was pegged out to the max, as well as internet browsing.

The problem is somewhere within Ubuntu and the drivers/software for my wifi card. So now what?

---

### Post by chopsbuntu on 2006-02-25
Any other suggestions anyone?

---

### Post by Lambert on 2006-02-25
After running for a few minutes and browsing the web, post the output of:

iwconfig
ifconfig

tracepath [www.google.com](www.google.com)

ping -c 3 ______

with the ping command you're going to run this three times. after -c 3 use these

1. 127.0.0.1
2. ip of your nic
3. ip of your router

What kind of settings are you using? Also what device and driver is being used?

---

### Post by chopsbuntu on 2006-02-25
Hello again Lambert! Here's the info you requested...

**iwconfig:**
> charles@chops:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"House Of P****"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:C4:AC:43
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:3

sit0      no wireless extensions.


**ifconfig:**
> charles@chops:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:20:A6:50:64:67
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:a6ff:fe50:6467/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32102 errors:928955 dropped:0 overruns:0 frame:928955
          TX packets:17635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:44002939 (41.9 MiB)  TX bytes:1301016 (1.2 MiB)
          Interrupt:11 Memory:ecfa0000-ecfb0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1364 (1.3 KiB)  TX bytes:1364 (1.3 KiB)


**tracepath:**
> charles@chops:~$ tracepath [www.google.com](www.google.com)
 1:  192.168.1.122 (192.168.1.122)                          1.081ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            610.211ms
 2:  10.97.16.1 (10.97.16.1)                               99.907ms
 3:  gig1-0.tampflerl-rtr1.tampabay.rr.com (65.32.14.1)   214.060ms
 4:  pos6-0-OC-192.tampflerl-rtr3.tampabay.rr.com (65.32.8.133) 274.720ms
 5:  pop1-tby-P3-0.atdn.net (66.185.136.57)               477.108ms
 6:  bb1-tby-P0-2.atdn.net (66.185.136.164)               256.415ms
 7:  bb2-atm-P7-0.atdn.net (66.185.152.245)               293.957ms
 8:  pop2-atm-P1-0.atdn.net (66.185.147.211)              362.663ms
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply 
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500                                                       

---

### Post by Jova on 2006-02-25
ath0 IEEE 802.11g ESSID:"House Of P****"
Mode:Managed Frequency:2.462 GHz Access Point: 00:13:10:C4:AC:43
Bit Rate:36 Mb/s Tx-Power:18 dBm Sensitivity=0/3
Retry:off RTS thr:off Fragment thr:off
Power Management:off
Link Quality=38/94 Signal level=-57 dBm Noise level=-95 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:3

I think that's your link Quolity for -57dBm is to low...  hhmm eay don't you just try to connect wirh lower rate 11m or 1m

iwconfig ath0 rate 1M

And slow down your router to b mode

---

### Post by chopsbuntu on 2006-02-25
And now for the second half...

**ping -c 3_____ :**
> charles@chops:~$ ping -c 3 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.167 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.159 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.108 ms

--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.108/0.144/0.167/0.029 ms

> charles@chops:~$ ping -c 3 192.168.1.122
PING 192.168.1.122 (192.168.1.122) 56(84) bytes of data.
64 bytes from 192.168.1.122: icmp_seq=1 ttl=64 time=0.052 ms
64 bytes from 192.168.1.122: icmp_seq=2 ttl=64 time=0.101 ms
64 bytes from 192.168.1.122: icmp_seq=3 ttl=64 time=0.080 ms

--- 192.168.1.122 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.052/0.077/0.101/0.022 ms

> charles@chops:~$ ping -c 3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=950 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=151 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=174 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 151.478/425.698/950.734/371.379 ms

---

### Post by chopsbuntu on 2006-02-25
[QUOTE=Jova]

I think that's your link Quolity for -57dBm is to low...  hhmm eay don't you just try to connect wirh lower rate 11m or 1m

iwconfig ath0 rate 1M

And slow down your router to b mode[/QUOTE]

That pretty much defeats the whole purpose. I want to go faster, NOT slower. :???:

---

### Post by Lambert on 2006-02-25
From a glance this is what I'm seeing and right now can't offer a whole lot but maybe this will help your search.

Your ifconfig shows no tx errors but a bunch of rx errors. 

You can see your ping and tracepath are really fast to the device but extends way to long to the router.

So this is how I see it.

Your pc can send packets to the router ok and the router receives them. But the rx errors on the pc tells me that your pc is not receiving packets ok from the router. A network is pretty smart as far as errors. The router knows the pc is not getting the packets so it makes adjustments until the packet gets to the pc. 

What causes this? not sure but I would check your mask on the router to make sure it is 255.255.255.0

If I see something else I can post I'll come back to this

---

### Post by jamesr on 2006-02-25
I agree with Lambert that the time to the router is too long. If the poblem is signal strength just as a test try next to the PC nest to the router. I know that you said that it was OK with Windows but note if the signal strength has increased significantly and a possible reduction in the ping time to the router.

Have you googled for the new SRX400 technology and also for the wifi card to see if anybody else is having a problem

---

### Post by Lambert on 2006-02-25
One other thought, this is a 802.11g router but has a type of MIMO technology that can reach 108mbps. Are you runing in this mode? And if so what device/driver are you using?

---

### Post by chopsbuntu on 2006-02-26
Well I solved part of the problem by uninstalling that WRT54GX4 and reinstalling my old and trusted WRT54G last night. That new router obviously has something wrong with it. Every time I would log into its web-based setup menu, I would be able to view one or two pages, then it would just lock up and not let me save any changes or view anymore pages. And I have read online about the firmware being screwed up or something, so...

Anyway, when I reinstalled the old router, I placed on top of my Linux box which sits on top of tall book case in my room, so now the router is about 18" below my 8' ceiling. This has helped some as far as getting a stronger signal out in the other room, but it's still not running as fast as it should be.

Here are the "iwconfig" and "ifconfig" readings again for a comparison... Again, these are with my old router.

> charles@chops:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Tits McGee"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:41:D4:50:57
          Bit Rate:12 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/94  Signal level=-58 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:4   Missed beacon:8

sit0      no wireless extensions.

> charles@chops:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:20:A6:50:64:67
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:a6ff:fe50:6467/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14641 errors:394349 dropped:0 overruns:0 frame:394349
          TX packets:10652 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:17527557 (16.7 MiB)  TX bytes:1013265 (989.5 KiB)
          Interrupt:11 Memory:ecfa0000-ecfb0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1411 (1.3 KiB)  TX bytes:1411 (1.3 KiB)


Any better or worse or what?!?!

---

