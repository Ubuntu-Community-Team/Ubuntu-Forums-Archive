---
title: "Router Admin Page...or Not."
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by rob150588 on 2011-04-16
Hi there.

I'm having a problem accessing the Admin Page of my router (Netgear).

I key in the IP of the router in Firefox which is http:\\192.168.0.1 and Firefox reports it cannot find the server. I can ping the router OK and am connected to the internet.

I also have a machine running 9.10 and another with Vista. The other Ubuntu machine cannot view the admin page, but the Vista one can (both in IE and Firefox). Below is the output from ifconfig if it helps:

```
eth1      Link encap:Ethernet  HWaddr 00:1b:b1:8d:d0:fe  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b1ff:fe8d:d0fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5652 errors:1 dropped:0 overruns:0 frame:36865
          TX packets:5637 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3669547 (3.6 MB)  TX bytes:993729 (993.7 KB)
          Interrupt:16 
```

Does anyone know why I can't access it from Ubuntu ? Hopefully it's just something stupid I'm missing.

Cheers.

---

### Post by Enigmapond on 2011-04-16
With Netgear you can also just type:
Routerlogin.net and that should do it. It will ask for a password and if you haven't changed it, the default is "admin" & "password" but I suggest you change that once there.

---

### Post by rob150588 on 2011-04-16
Thanks for your reply Enigmapond.

That address only redirects to the Netgear customer support page. Any other suggestions ?

BTW, I already changed my pass ages ago...these things are so easy to break into otherwise !

Cheers.

---

### Post by Enigmapond on 2011-04-16
Ooops...Sorry but I have Netgear as well and that's all I do to get into the smart wizard web interface. Maybe the complete address??

[http://routerlogin.net/start.htm](http://routerlogin.net/start.htm)

Sorry if this doesn't help.

Cheers though.. :)

---

### Post by rob150588 on 2011-04-16
Nope, nada. Same problem.

It's as though to Ubuntu the http just doesn't exist...although I know full well it does.

---

### Post by chili555 on 2011-04-16
> I key in the IP of the router in Firefox which is http:\\192.168.0.1I hope you really meant http:[COLOR="Red"]//[/COLOR]192.168.0.1. Yes??

---

### Post by josephmills on 2011-04-16
you could reset you router also and try again plug into you cat5 cable and right click on your network managers icon then go to connection info. did you default route change? try in opera or chrome well hope that this helps

---

### Post by rob150588 on 2011-04-17
> **chili555 said:**
> I hope you really meant http:[COLOR="Red"]//[/COLOR]192.168.0.1. Yes??

Sorry, ex-Windows user, force of habit, you know ? Yes I meant that and it still didn't want to know.

> **josephmills said:**
> you could reset you router also and try again plug into you cat5 cable and right click on your network managers icon then go to connection info. did you default route change? try in opera or chrome well hope that this helps

Didn't work with the CAT5 either...but I reset the router last night and input all my settings again (which was a right pain) and it works fine now. It seems odd to me that that was the issue as nothing has changed on it at all. Meh, job's good anyway.

Thanks for all your help guys, as always much appreciated.

Rob.

---

