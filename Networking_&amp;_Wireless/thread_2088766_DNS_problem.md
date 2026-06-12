---
title: "DNS problem"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by csshreeram on 2012-11-27
Hi all

Using 12.04.I am unable to connect to internet via Wireless and by Wired Ethernet connection from my modem.Firefox says "Server not found" and cant download any updates as well.But one ray of hope is Transmission is able to download files via torrents already there.So why dont other applications cannot connect to Internet and more importantly how to solve this.All of this was previously working.Cant stand being on Win"£$s for long.Helpppppp.


Tx
C.S.Shreeram

And on a totally different note...why cant I edit my Distro or my location. I dint have a problem all these years,so there wasnt a need to visit the forums.Is this a way of punishing irregular visitors?

---

### Post by dannyboy79 on 2012-11-27
it may be a DNS issue, can you open a terminal and ping google via it's IP address?
```
ping 74.125.224.72
```

As far as editing your profile distro and your location, are you sure you're logged in? You should be able to edit those within your profile after logging in. I doubt ubuntu forums punish non-frequent visitors.

---

### Post by wildmanne39 on 2012-11-27
As far as editing your profile distro and your location, you must have 25 posts to edit those, we had to change it because of spammers.

---

### Post by csshreeram on 2012-12-02
Yup ...its DNS issue.Am able to ping google via the IP Address.So how to resolve this?

Tx
C.S.Shreeram

---

### Post by dannyboy79 on 2012-12-03
you can add dns-nameservers to your interfaces file (/etc/network/interfaces using googles dns servers. the line would like this
```
dns-nameservers 8.8.8.8 8.8.4.4
```
put it directly after the interface your computer uses to surf the internet, like eth0 or wlan0

---

### Post by csshreeram on 2013-01-09
um...guys...tried everything...not working, was unable to login as well, so couldnt post updates...any other workaround?

-------
Shreeram

---

### Post by dpurgert on 2013-01-09
assuming you're using a wired card (and that it's eth0)

edit /etc/network/interfaces and add the following line

```

auto eth0
iface eth0 inet dhcp
dns-nameservers 8.8.8.8 8.8.8.4

```

Save, and restart your computer.  

This'll force your interface to use google's DNS servers (though, personally, I'm partial to Open DNS' nameservers -- 68.168.222.222 68.168.220.220). 

If this doesn't work, check your iptables and make sure you're not accidentally blocking DNS traffic (UDP port 53)

---

