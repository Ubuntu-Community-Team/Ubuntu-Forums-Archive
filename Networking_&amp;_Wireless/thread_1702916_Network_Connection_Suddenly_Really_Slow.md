---
title: "Network Connection Suddenly Really Slow"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by fogNL on 2011-03-08
I'm pretty much out of ideas, been searching around a lot, and can't quite find anyone else with the same issue.

I have a Zotac MAG HTPC machine running Ubuntu 10.10.  I've had it installed for about a month or 2 without much issue with networking (audio over hdmi is another thing).

Some time last week, a set of updates came down, and since then, my networking performance has been terrible.  Transferring a file across my local network or downloading from the internet tops out at around 40-50kb/s.  When prior to these updates, internet download was 800kb/s and across the network could be 2-3mb/s.

The network connection is Wireless N, using a Zonet USB adapter:

> Bus 002 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter


As far as I can tell, it uses module **r8712u**.

Other information:

ifconfig
> wlan0     Link encap:Ethernet  HWaddr 08:10:74:78:71:0c
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:422402 errors:0 dropped:25377 overruns:0 frame:0
          TX packets:293505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:575183473 (575.1 MB)  TX bytes:27590312 (27.5 MB)


iwconfig
> wlan0     IEEE 802.11bgn  ESSID:"caprica"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: E0:CB:4E:A5:7D:C8
          Bit Rate:150 Mb/s   Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=68/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Other wireless devices on my network work without issue.

I've read around and tried some other suggestions like disabling ipv6, but it made no difference.  I really don't want to have to re-install everything, but I will if I got to (i do have an old clonezilla image i could use).

Looking at dmesg and /var/log/messages  doesn't give me any indication of issue.  Also, if I do a download to the system, and ssh in using putty, the putty session is extremely lagged.

Can anyone point me in any direction on how I can diagnose this issue?  Thanks.

**Update**:  one more thing.  I tried to upload a file from the HTPC to another computer.  It started out at 3.0Mb/s, but got slower and slower as time went on, down to about 700Kb/s, but is now hovering around 700-800 kb/s.  

Using the same two systems, transfering the same file back the other way starts out at 3.0mb/s, but slows down fairly quickly down to 40kb/s to 50kb/s.

So, it appears the issue is only one way, on the downstream.

---

### Post by chili555 on 2011-03-08
Let's see what driver it is using. Please run and post:```
lsmod | grep r8
```Thanks.

---

