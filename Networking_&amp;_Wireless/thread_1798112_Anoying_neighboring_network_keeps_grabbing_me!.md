---
title: "Anoying neighboring network keeps grabbing me!"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by oxf on 2011-07-05
Well I have a nearby WiFi network that my PC keeps trying to connect to automatically. I don't know why since mine is closer. I tried changing the channel and have deleted the offending network under "Edit Connections"  but of course it keeps comming back. The problem is most annoying on boot up when it starts trying to connect automatically as soon as the desktop is loaded.

Is there anything Ican do to "hide" this network  from my PC's vission?

Thanks
Katya

---

### Post by SteveDee on 2011-07-06
> **oxf said:**
> Well I have a nearby WiFi network that my PC keeps trying to connect to automatically...

Have you set "Connect Automatically" for your own wifi network? This should ensure it reconnects to your network each time you boot.

---

### Post by oxf on 2011-07-06
> **SteveDee said:**
> Have you set "Connect Automatically" for your own wifi network? This should ensure it reconnects to your network each time you boot.

No I haven't simply because I don't always want it to and have chosesn to manually connect as needed. However, I suppose that might be one way around the problem..

---

### Post by SteveDee on 2011-07-06
> **oxf said:**
> ...have chosen to manually connect as needed...

...so linux is selecting the best quality local wifi access point. I don't think you can blacklist a wifi AP.

---

### Post by oxf on 2011-07-09
> **SteveDee said:**
> ...so linux is selecting the best quality local wifi access point. I don't think you can blacklist a wifi AP.

But it's not the best quality, it's half the strengh of my network. No problem I just ignore it anyway.

---

### Post by SteveDee on 2011-07-10
> **oxf said:**
> But it's not the best quality....


How odd? I expected the best quality signal to be selected if you haven't manually select an ap. But maybe it starts with the lowest frequency channel.

If you are still curious (as I am) you could try this:-
Open a terminal and type:-
```

iwconfig

```
This shows you the connection details for the wifi ap you are using. Note the interface identity (e.g. "eth1" or whatever it is). Use this interface (in place of eth0) in the next command:-
```

sudo iwlist eth0 scanning

```
This should show all local wifi access points (sometimes you have to repeat the command a couple of times by using the up arrow key, then return).
Take a look at the output for any clues.

If the system does list them in channel order, you could try changing your wifi channel to channel 1, in an attempt to make it your default.

You would normally select your wifi channel to minimise interference, probably by avoiding channels used by other local wifi. However there are many other sources of interference in the wifi band (see also: [http://ubuntuforums.org/showthread.php?t=1768125](http://ubuntuforums.org/showthread.php?t=1768125) )

---

