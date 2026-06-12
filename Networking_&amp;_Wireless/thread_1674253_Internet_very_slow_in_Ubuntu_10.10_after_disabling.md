---
title: "Internet very slow in Ubuntu 10.10 after disabling ipv6"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by Jomboz on 2011-01-23
Sorry if this issue has already been addressed, but here it is: I have installed Ubuntu 10.10 on my laptop, and the internet was very slow and kept dropping in and out for any web browsers and sometimes the Ubuntu software center. After searching the internet for a while I came across several article saying to disable ipv6, which I have done, but the issue persists and I have no idea how to fix it. Again, sorry if this has already been asked, but I am new to linux and need some assistance.

---

### Post by lemming465 on 2011-01-24
I'm sorry to hear you are having performance problems.  We'll need more information to help diagnose why before we can suggest workarounds or repair strategies.

Is internet access generically slow for all computers and operating systems in your vicinity, or just your ubuntu laptop?

Is your laptop network behavior slow everywhere, or just in some places like at home?

Is your network access wireless (WIFI) or cabled (ethernet)?
What is your network uplink, e.g. cable modem, DSL modem, voice modem, 3G cell data, optical fiber or what?

If you try to ping (icmp-echo test) a site numerically, are any packets lost?  Are the round trip times low and stable, or high and variable? Does it differ much with small versus big packets? E.g.```
ping -c20 144.92.9.185
ping -c20 -s1000 144.92.9.185
```

DNS configuration problems can be a cause of slow performance, and ISP DNS servers can be overloaded.
If you run```
time host -t A ipv6.he.net
time host -t AAAA ipv6.he.net
time host ipv6.he.net
```
what kind of times do you get?  If your DNS setup is working well, and your ISP isn't overloaded, the first two should be similar and less than 0.1 seconds, and the last one should be 3-4x the first two, but under .3 seconds.

Could we see the output of:```
lsmod | sort
cat /etc/resolv.conf
ip address show
```

---

### Post by Philip550c on 2011-07-28
I know this is an old post but for anyone else reading it still it might have been slow not because of ipv6 but because of the wireless card not staying at 54Mb/s, try looking at connection information and see if the speed is varying going even as low as 1Mb/s.
If so try this command: 

```
sudo iwconfig wlan0 rate 54M
```

---

