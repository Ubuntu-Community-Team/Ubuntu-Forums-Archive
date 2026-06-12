---
title: "Slow wireless in Ubuntu..but not Windows"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by secretservgy on 2006-06-27
I used to use windows and connect to my wireless network...but now 'm using  ubuntu but it is so much slower,,anyone help?

---

### Post by Oblong_Cheese on 2006-06-27
I know for a fact that the Broadcom drivers under Ubuntu default to 802.11b (maximum of 10Mbps) operation.

Perhaps under Windows your wireless card is operating within 802.11g (54Mbps) and under Ubuntu is at 802.11b?

---

### Post by secretservgy on 2006-06-27
i suppose that may be true. But here from iwconfig it shows it at 24mb/s:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"linksys"  Nickname:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:8F:F9:FA
          Bit Rate=24 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-86 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Is there any reason for this and a way to fix it?

---

### Post by secretservgy on 2006-06-27
i suppose that may be true. But here from iwconfig it shows it at 24mb/s:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"linksys"  Nickname:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:8F:F9:FA
          Bit Rate=24 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-86 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Is there any reason for this and a way to fix it?

---

### Post by secretservgy on 2006-06-27
i suppose that may be true. But here from iwconfig it shows it at 24mb/s:

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"linksys"  Nickname:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:8F:F9:FA
          Bit Rate=24 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-86 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


Is there any reason for this and a way to fix it?

---

### Post by Oblong_Cheese on 2006-06-27
What dimension of your wireless is slow? Response times to websites (ping), or bandwidth (ability to download quickly)?

From your iwconfig output it says the 'bitrate' is 24Mb/sec which I can only assume actually means around 24Mbit/sec. Meaning that your maxmum throughput will be around 24/8 = 3 megabytes per second.

---

### Post by secretservgy on 2006-06-27
i think it might be ping...since i can download files at a normal fast speed....it just takes forever for a site to be found and load.

---

### Post by secretservgy on 2006-06-27
it takes so long when it says on bottom of browser Looking up ....
and it also takes long hwen downloaed the actual site after it has "found" it

---

### Post by secretservgy on 2006-06-28
I attempted to disble ipv6 but i dont think it worked.

---

### Post by secretservgy on 2006-06-28
well..i actually figured out the problem....i needed to disable ipv6..its still kinda slow...but better then before.

---

### Post by Lawke on 2007-11-06
Hi,

I have the same problem, i'm using the bcm43xx drivers and I only get 24mbit/sec.
If I go to the upper floor I don't even have a connection.
This was no problem in windows,
Any way to tell me how you fixed this?

Greets

---

