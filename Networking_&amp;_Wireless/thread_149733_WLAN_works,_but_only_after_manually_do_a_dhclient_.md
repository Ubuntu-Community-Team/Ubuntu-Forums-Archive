---
title: "WLAN works, but only after manually do a dhclient wlan0"
date: 2006-03-24
forum: Networking &amp; Wireless
---

### Post by broseman on 2006-03-24
Hi all,

my WLAN (Vigor 2500, DrayTek Vigor 510) is working well with this [HowTo]("http://www.mindcrime.net/~niehaus/wlan-ng-HOWTO.html") (in german), but only with a
```
sudo dhclient wlan0
```
after each boot.

My etc/network/interfaces reads
```

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid xxx
wireless_enc on
wlan_ng_authtype opensystem
wlan_ng_key0 xx:xx:...
auto wlan0
```

A dmesg lists the error

```
only dot11req_mibget allowed for non-root
```

It does not help to add the call to /etc/init.d/bootmisc.sh !

I also tried to manipulate the /etc/dhcp3/dhclient.conf , but had no luck so far.

Any Suggestions? Thanks!

Greetings

 broseman

---

### Post by mzilhao on 2006-03-24
what does your /etc/resolv.conf say?

can you ping your router before
```
sudo dhclient wlan0
```?

---

### Post by broseman on 2006-03-24
Thanks for your reply!

resolv.conf:
```
nameserver 217.11.48.200
nameserver 217.11.49.200
```

Answer to second question will follow (sorry).

---

### Post by broseman on 2006-03-25
Here we go again...

Answer is: No. A ping to the router before "dhclient wlan0" is followed by a

```
connect: Network is unreachable
```

BTW: In the output of "dhclient wlan0" I find the lines:
```
There is already a pid file /var/run/dhclient.pid with pid 6657
killed old client process, removed PID file
```

If it helps...

Thank you!

---

### Post by mzilhao on 2006-03-25
well, if you can't ping your router then it shouldn't be a dns problem... i had a similar problem, but it was a problem with dns...
does your /etc/network/interfaces or your /etc/resolv.conf change after you ```
sudo dhclient wlan0
```?

have you tried with a static ip address?

i'm not an expert, though. maybe someone else has a better idea...

---

### Post by _Groove_ on 2006-03-25
May be related... I'm finding my wired 10/100 ethernet port is brought up on boot but does not receive an address from dhcp. It requires me to do an ifup/ifdown or restart networking to get an ip address.

Perhaps a problem with dhclient?

---

### Post by broseman on 2006-03-25
Here are some news:

I found my network working in textmode, before logging into gnome!

And: Now every thing works fine! Problem solved...

Unfortunately I cannot tell you the solution. Meanwhile I had to delete the .ICEauthority due to another problem - maybe it has something to do with that?

Greetings and thanks for your help!

 broseman

---

