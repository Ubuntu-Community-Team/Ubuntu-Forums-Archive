---
title: "Ridiculously high ping"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by gooberguy on 2010-03-11
Hello all,

I just installed Ubuntu 9.10 alongside windows 7 on my Acer Aspire 3050. I have a Belkin F5D7230-4 router, with wireless internet.

When i ping google.com in windows i get times like 30,31,29
when i ping google.com in ubuntu i get times like 3627,3404,3531

obviously making the internet very, VERY slow. Any ideas on why this may be? Manually setting the DNS servers, and disabling ipv6 in Firefox did not help at all.

---

### Post by gooberguy on 2010-03-11
note: this is only when I'm connecting via a wireless connection.

---

### Post by gooberguy on 2010-03-11
Also, when i run ifconfig, i get this...

```

eth0      Link encap:Ethernet  HWaddr 00:1b:24:0f:b4:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:33:07:91  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::114:6eff:fe33:791/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5355 (5.3 KB)  TX bytes:6981 (6.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7E-33-07-91-33-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by wirelessmonkey on 2010-03-12
1) What type of wireless card?
2) Is your DNS set up properly, i.e. resolv.conf?
3) Are pings to your gateway (or home router) high as well?

---

### Post by gooberguy on 2010-03-12
1)Atheros AR5100
2)Not sure what resolv.conf is, but it is set up in the properties of my wireless network (got there from the icon located top right)
3)Yes! I get responses in the range of 500-1000 with the very rare ~30 I feel like this is very important, as from my desktop that is wired in, the responses report as <1ms

```
--- 192.168.2.1 ping statistics ---
46 packets transmitted, 43 received, 6% packet loss, time 58126ms
rtt min/avg/max/mdev = 1416.326/9075.962/18691.777/6310.664 ms, pipe 11

```

---

### Post by wirelessmonkey on 2010-03-12
This is symptomatic of band saturation. Try changing the channel on your wireless router to 1,4,7,or 11.  Keep testing pings to check latency.  It's possible that  your Atheros antenna mght be damaged too, but not what I'd worry about first.

---

### Post by gooberguy on 2010-03-12
> **wirelessmonkey said:**
> This is symptomatic of band saturation. Try changing the channel on your wireless router to 1,4,7,or 11.  Keep testing pings to check latency.  It's possible that  your Atheros antenna mght be damaged too, but not what I'd worry about first.

I have not tried what you said yet, but to check my wireless card, i brought my laptop to my university. The internet is very speedy here, so it must be something with my router, like you have mentioned.

**Edit:**First channel i tested was 4, and the results were great! internet is back to speed. Thank you very much. I'm curious though why did this fix it? I do not know what band saturation is.

---

### Post by wirelessmonkey on 2010-03-12
It means, basically, that there is enough traffic or interference in the portion of the radio spectrum you were using, to cause problems with your connection.  Probably a bunch of Wireless routers or access points in your area running on the same channel.  Or possibly a microwave or cordless telephone that wasn't behaving itself.

---

### Post by Xjph on 2010-03-27
I had exactly the same problem with the same card and the same solution (changed from channel 1 to 4) but I am not happy with the explanation.  Channel 1 is not saturated in my area, in fact I specifically changed *to* channel 1 a couple of weeks ago specifically because it was empty.  There is a greater degree of saturation in my area in the frequency space used by channel 4 according to my site survey.
Furthermore, if band saturation was the problem, why would it work perfectly fine in Windows?

---

### Post by wirelessmonkey on 2010-03-30
I'm sorry you don't like the answer, for a much more in depth explanation, I suggest [this book.]("http://www.amazon.com/802-11-Wireless-Networks-Definitive-Second/dp/0596100523/ref=sr_1_1?ie=UTF8&s=books&qid=1269978171&sr=1-1")

If it truly worked 'perfectly fine' in Windows, it may be that the Atheros chipset drivers in Windows do better band segregation or chatter control than the linux driver. These chipsets are well supported in linux, so I'd be mildly surprised if that was the case. Perhaps network manager or some other app are at fault.

---

### Post by 98cwitr on 2010-03-30
looks like my wired connection when I have torrents running :/

---

### Post by chooseopen on 2010-06-29
I am seeing high ping times in Lucid on my wired connection when downloading torrents.

---

### Post by Clever_Username on 2010-07-25
Why are the ping times so much higher when he's using Linux as opposed to Windows? He's using the same hardware regardless of which OS he's using. Or did I miss something here?

---

