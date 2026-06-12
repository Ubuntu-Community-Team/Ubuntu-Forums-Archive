---
title: "Extremely slow wireless Internet"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by itsjareds on 2009-08-01
[SIZE="4"]Problem solved: [See this post.]("http://ubuntuforums.org/showthread.php?p=7733217#post7733217")[/SIZE]

------------
Hi, I just bought a Rosewill RNX-EasyN1 USB wireless adapter since my old one was very buggy with Linux, and my new one for the most part has no connection issues. My only problem is that when I am connected, I'm getting really, really slow Internet. It takes at least a minute to fully display a Google search, and there's still a loading bar for a longer time. I know that the adapter itself is fine because I also run Windows 7 on this machine, and it runs at a normal speed (ping ~120ms). Now I'm getting pings of around 300-1000ms, and I have no idea why.

I've tried disabling IPv6 by adding these lines in /etc/modprobe.d/aliases:
```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
```

Rebooted, and still slow Internet. My old adapter gets normal speeds on Ubuntu, but I can't use it because it'll drop the connection randomly. Does anybody know a reason that this RNX-EasyN1 won't get normal speeds?

I'm not sure what commands to run to show you my speeds, but here's my ping using the adapter:
```
jared@jared-desktop:~$ ping google.com
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=43 time=1931 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=43 time=929 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=43 time=302 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=4 ttl=43 time=273 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=5 ttl=43 time=215 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=6 ttl=43 time=189 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=7 ttl=43 time=275 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=8 ttl=43 time=258 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=9 ttl=43 time=200 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=10 ttl=43 time=307 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=12 ttl=43 time=199 ms
```

There really isn't a consistent time, but it's averaging around 250ms if you ignore the first two outliers. This is much slower than what it should be, and webpages seem to take much longer than this to load.

Thanks**

---

### Post by itsjareds on 2009-08-01
Bump

---

### Post by Raider007 on 2009-08-01
quick question:
in your Network Tools > Wireless dropdown
what's your Link Speed listed at?

---

### Post by itsjareds on 2009-08-01
I've got 65 Mbps.

edit: Here's two of the tabs on my Network Tools window:

[IMG]http://i30.tinypic.com/2eobp8m.png[/IMG]

[IMG]http://i30.tinypic.com/160o7x5.png[/IMG]

---

### Post by itsjareds on 2009-08-02
bump

---

### Post by w_1_n_d on 2009-08-02
Did you try disconecting you wireless  and reconnecting it? Or maybe it needs a certain driver or a patch. so search google for information about your wireless device. :P

---

### Post by itsjareds on 2009-08-02
> Did you try disconecting you wireless and reconnecting it?

Do you mean from the router? I don't have any access to the router, so I can't change anything.

I downloaded the driver for my chipset, and Rosewill released a linux driver for the RNX-EasyN1. It says "Linux is not supported now" on their product page, though. There has also been another confirmed case of using this adapter with WPA2 security, which is exactly what I need.

[http://ubuntuforums.org/showthread.php?t=1016108]("http://ubuntuforums.org/showthread.php?t=1016108")

---

### Post by itsjareds on 2009-08-03
Bump :(

---

### Post by itsjareds on 2009-08-04
bump

I'd really like to get this figured out!

---

### Post by itsjareds on 2009-08-04
Woooooo I found the fix by myself :D

After reading through the source of the driver, I edited RT2870STA.dat and changed these lines for my specific network:

```

SSID=Tegan
AuthMode=WPA2
EncrypType=AES
WPAPSK=<my psk>

```

I reinstalled the driver and, like magic, my speeds are back to normal! Yay, 40 ms average ping :).

Thanks for the help, those who offered it.

---

### Post by SlySammy on 2009-12-21
How do you install the driver? I'm an Ubuntu noob and I can't figure out how to set it up.

---

