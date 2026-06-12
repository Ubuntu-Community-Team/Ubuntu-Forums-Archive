---
title: "I can't upload out of proxy chanels, but I can download &amp; open pages well ??"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by GnuKian on 2012-12-14
Unexpectedly, after migrating to Ubuntu I can't upload any thing via ADSL, also I can't send any comment in weblogs. but downloading files and openning pages are ok in ADSL line! The odd point if I use proxy/antifilter (as in Tor or FreeGate I can upload!!) I can upload normally!!
There's not any problem in windows: both download and upload are ok.
Also when I use GPRS (mobile internet) I don't have any problem!!!

My Line: ADSL (send rate: 512 Kbit/s, receive rate: 2048 Kbit/s)

My Modem: D-Link 2520U

My installed operating systems are both Ubuntu 10.04 & 12.04.
I also checked &quot;uploading&quot; on 10.10, 12.04 and 12.10 in live mode => failed!

My browsers: firefox 17.0.1, default ubnutu 10.10 firefox, Opera 10.10 on Ubuntu 10.04

What does &quot;upload&quot; mean in this case? Am I uploading a file using &quot;ftp&quot; or trying to attach a file in gmail?

I can't comment on weblogs and forum in any case! (but using proxy it is ok)
I can't upload a file to uplod-center sites in any case! Modem lamps show that there is not any traffic when I click for upload!

I can upload to images.google.com but using proxy it works a few better!
I can open all web pages!

The below picture is the result of my attempt to attaching a file to AOL using Thunderbird.
[IMG]http://i.stack.imgur.com/gO0zN.png[/IMG]

BUT my try for gmail was successful! it seems there is not any problem with gmail services!!!

FTP: I could upload a txt file (10 KB), but in next attempts for uploading a bigger file (pdf: 2MB), I couldn't! (Using filezilla)

Result of ping 4.2.2.4 is here:
naik@KIAN:~$ ping 4.2.2.4
PING 4.2.2.4 (4.2.2.4) 56(84) bytes of data.
64 bytes from 4.2.2.4: icmp_seq=1 ttl=50 time=204 ms
64 bytes from 4.2.2.4: icmp_seq=3 ttl=50 time=205 ms
64 bytes from 4.2.2.4: icmp_seq=4 ttl=50 time=204 ms
64 bytes from 4.2.2.4: icmp_seq=5 ttl=50 time=203 ms
64 bytes from 4.2.2.4: icmp_seq=6 ttl=50 time=202 ms

I installed &quot;nload&quot; and glance its output in terminal during uploading a file. the below picture was captured during upload-progress from &quot;nload&quot; output:
[IMG]http://i.stack.imgur.com/mLjbl.png[/IMG]

It shows that I have upload, but I didn't get the final link. firefox was showing me that is trying to upload and nothing. I also try to post here without proxy, nload showed me there is upload but my comment wasn't sent at last! It's weird!!!

What more information do you need around this problem?

---

### Post by acronim on 2012-12-15
Have you test connecting by pppoeconf?

---

### Post by GnuKian on 2012-12-16
> **acronim said:**
> Have you test connecting by pppoeconf?
I follow pppoedconf from terminal. it connect me to internet but the problem is still permanent!? => I can't upload at all!

---

### Post by GnuKian on 2013-01-19
I can't send long sentences (with many charecter), I can send something like this post, just!
 and I can't upload any thing at all!
 I reinstalled Ubuntu. after a few days the problem returned!

---

### Post by GnuKian on 2013-01-20
Is it possible a port has been closed?

---

### Post by GnuKian on 2013-01-22
I decreased MTU and it solved!

---

