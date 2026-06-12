---
title: "Suddenly can't access Google on wireless"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by JudeOsborn on 2011-01-04
I've been using Ubuntu 10.04 for a couple of months now, but I booted in to Widows for a week over the Christmas break. When I booted back in to Ubuntu I was suddenly unable to access Google sites when on Wireless. I can access any other site so far, except for Google. I don't recall playing with the network settings or doing any kind of funny business.

If I plug my network cable back in I can access Google fine, so the problem is only with Wireless. However, I've tried 3 different wireless connections and I get the same results -- no Google.

I have a dual boot system and when I boot in to Windows 7 I can access Google sites just fine on Wireless. I also had someone else nearby who uses exactly the same Dual boot Ubuntu 10.04 set up I use, and this person can access Google fine on wireless. He has no problems. So the problem does not seem to be with my ISP or router, but with my Ubuntu configuration.

So I really don't know what to do. I'm fairly new to Ubuntu, though I'm a web developer with a high degree of technical knowledge. Can anyone at least give me some ideas for how to fix this problem? I'm pretty stumped.

---

### Post by PatchesTheCaveman on 2011-01-04
Go to Applications > Accessories > Terminal.  In the black box that appears, type the following and press Enter:
```
ping google.com
```
Wait about 30 seconds, then press CTRL+C.  Now, copy and paste what it output into a reply to this thread.

Then, run this command:
```
dig google.com
```
and copy/paste its output here too.

With that information, we might be able to figure out what's going on.  Thank you!

---

### Post by JudeOsborn on 2011-01-06
Thanks very much for your assistance. Here's the info you asked for.

When I ping google.com I get this:

```
PING google.com (66.102.7.99) 56(84) bytes of data.
```

Then it just sits there doing nothing. I let it go for a couple of minutes, but nothing else every happens, and I have to hit Control C to get back to the prompt. This does not happen to me in Windows. In Windows google.com pings fine.

Of course, pinging other sites, like yahoo.com works fine. I get the usual ping information that continues until I press Control C.

This is what I get when I try "dig google.com":

```

; <<>> DiG 9.7.0-P1 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65141
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		81	IN	A	66.102.7.99
google.com.		81	IN	A	66.102.7.104

;; Query time: 5 msec
;; SERVER: 172.27.2.3#53(172.27.2.3)
;; WHEN: Thu Jan  6 11:16:11 2011
;; MSG SIZE  rcvd: 60


```

This is information. I'm not super familiar with.

---

### Post by PatchesTheCaveman on 2011-01-06
That means your computer can figure out Google's IP address, but can't reach it for some reason.

Next, run this command which might explain why:
```
ip route
```
and copy/paste what appears.

---

### Post by thefix0r on 2011-01-06
sounds to me like your router is having a brain fart over two hosts with the same mac, I know it shouldnt happen, but still Ive seen stranger **** happen.

Id give your router/modem a nice health reboot, and if that doesnt kick it into shape, 

U might try apt-get install macchanger and change your mac address on your network adapter, it just might work.

---

### Post by JudeOsborn on 2011-01-07
Here's the info from ip route:

```

172.27.5.0/24 dev eth0  proto kernel  scope link  src 172.27.5.167  metric 1 
172.27.5.0/24 dev wlan0  proto kernel  scope link  src 172.27.5.148  metric 2 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 172.27.5.1 dev eth0  proto static 

```

thefix0r, I don't think anythings wrong with my router. I've tried more than one router and I get the same results. Also, everything works perfectly fine in Windows on the same routers and the same machine. I'll try changing my mac address as you suggested and see what happens. Thanks for the info.

---

### Post by JudeOsborn on 2011-01-07
Changed my mac address, but no change. Still can't access Google sites.

---

### Post by PatchesTheCaveman on 2011-01-07
It looks like your system might be getting confused between the wired and wireless connections (which is strange because they usually coexist peacefully).

Disconnect from Ethernet and run these commands to force everything to go through wireless properly:
```
sudo ip route del default
sudo ip route add default via 172.27.5.1 dev wlan0 proto static
```

Then try pinging/visiting Google again and see if it works.

---

### Post by JudeOsborn on 2011-01-10
Unfortunately that didn't make any difference. I still can't access Google sites, but I can access other sites via wireless. :-(

---

### Post by PatchesTheCaveman on 2011-01-11
Run:
```
mtr --report -c 10 google.com
```
and copy/paste the output.

---

### Post by JudeOsborn on 2011-01-11
Thanks for your help. I'm learning a lot here. Here's the output:

```


HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. eaglecrest-gate.ws.local      0.0%    10    0.7   0.8   0.7   1.5   0.2
  2. ???                          100.0    10    0.0   0.0   0.0   0.0   0.0
  3. 192.168.1.254                 0.0%    10    4.1   4.3   4.1   4.4   0.1
  4. dsl-servicio-l200.uninet.net 40.0%    10   62.7  73.7  11.3 187.4  68.3
  5. bb-la-grand-4-pos0-15-2-0.un 10.0%    10   43.9 162.3  29.5 1054. 335.0
  6. dsl-servicio-l200.uninet.net 90.0%    10  1795. 1795. 1795. 1795.   0.0
  7. bb-la-grand-4-pos0-15-2-0.un 90.0%    10  2956. 2956. 2956. 2956.   0.0
  8. ???                          100.0    10    0.0   0.0   0.0   0.0   0.0
  9. ???                          100.0    10    0.0   0.0   0.0   0.0   0.0
 10. dsl-servicio-l200.uninet.net 80.0%    10  614.3 584.1 553.8 614.3  42.8
 11. ???                          100.0    10    0.0   0.0   0.0   0.0   0.0

```

---

### Post by JudeOsborn on 2011-01-17
Well, after all that, the problem is gone as mysteriously as it came. After a weekend of using Windows 7 only, I booted into Ubuntu this morning and I can now access Google sites. Very strange. Thanks to everyone who provided me help with this odd problem. I did learn a fair bit about networking in the process, if it's any comfort.

---

