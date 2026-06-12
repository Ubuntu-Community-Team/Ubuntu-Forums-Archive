---
title: "(Wireless) Network acting weird"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by boterbram on 2008-12-13
Hi

Im running ubuntu 8.10 on a hp compaq 8510w laptop with a Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61) wlan controller inside. To use this card I updated the iwlagn drivers with the ones from wireless.kernel.org (latest version running now (master-2008-12-10)). I did this to fix some problems with the drivers that came with intrepid. Those were fixed, but now I suddenly have these new ones and I just can't find much on google so I am stuck.

The problem: When downloading using my wlan (I haven't got a cable up here so can't test it sadly) at first everything runs fine. I get download speeds of 1,2 MB/s which is normal (downloading bin file from speedtest.bbned.com). But the speed is just counting down untill it reaches around 80 KB/s.

dmesg gives a lot of this:

```
[12657.350747] wlan0: associated
[12665.446253] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=70 
[12667.405831] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=70 
[12668.406008] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=70 
[12669.405845] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=70 
[12685.405914] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=70 
[12687.406549] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=70 
[12688.459488] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=70 
[12689.406840] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=90 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=70 
[12691.406402] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=198 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=178 
[12931.449299] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=198 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=178 
[13231.959017] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=198 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=178 
```

Let me explain a bit, 192.168.1.100 is a server which I have running, which I have some problems connecting to via smb (lead maybe?) and 192.168.1.6 is this laptop with the problem

What I found on google is that there might be a link with the wlan being a hidden network (which is true in my case). I will try and set it to unhidden in a moment, although this wouldn't be a permanent fix for me because I just want it to be hidden.

Anyone got any ideas/need more info?

Thanks in advance
Bram

---

### Post by boterbram on 2008-12-13
Unhiding the acces point seems to help a lot, dmesg shows no messages so far and downloading the same file keeps being at a constant speed of 1.1 MB/s, but again, why can't it be hidden?

EDIT:

I now get, with a hidden acces point, these dmesg messages (is that double?:P):

```

 wlan0: associated
[14800.428206] Unknown OutputIN= OUT=vmnet2 SRC=172.16.201.1 DST=172.16.201.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
[14800.428435] Unknown OutputIN= OUT=vmnet2 SRC=172.16.201.1 DST=172.16.201.255 LEN=236 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=216 
[14800.428565] Unknown OutputIN= OUT=vmnet1 SRC=192.168.170.1 DST=192.168.170.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
[14800.428678] Unknown OutputIN= OUT=vmnet1 SRC=192.168.170.1 DST=192.168.170.255 LEN=236 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=216 

```

And yes I have vmware server 2.0 installed
NB the download speed seems ok again now:S (again, hidden access point and 1.2MB/s down)

---

### Post by boterbram on 2008-12-13
It was back again just a while ago, got one extra line in dmesg and the speed dropping to halfway, but now they are up again, don't get this really.

dmesg:

```
[14762.674551] wlan0: associated
[14800.428206] Unknown OutputIN= OUT=vmnet2 SRC=172.16.201.1 DST=172.16.201.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
[14800.428435] Unknown OutputIN= OUT=vmnet2 SRC=172.16.201.1 DST=172.16.201.255 LEN=236 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=216 
[14800.428565] Unknown OutputIN= OUT=vmnet1 SRC=192.168.170.1 DST=192.168.170.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239 
[14800.428678] Unknown OutputIN= OUT=vmnet1 SRC=192.168.170.1 DST=192.168.170.255 LEN=236 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=216 
[15031.462710] Inbound IN=wlan0 OUT= MAC=00:1f:3b:93:ed:a9:00:a0:b0:19:ad:a7:08:00 SRC=192.168.1.100 DST=192.168.1.6 LEN=198 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=178 

```

---

### Post by boterbram on 2008-12-14
Allright it's not the access point being hidden, I now have the same problem with a visible access point.

any ideas, anyone??

---

