---
title: "Enable networking greyed out - solution"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by InkyDinky on 2011-04-14
I have a temperamental wireless connection that will disconnect randomly and then not reconnect without some fidgeting. I shutdown last night when I had disabled the networking to prevent it from disconnecting and aggravating me.
When I rebooted today I couldn't re-enable networking from the network manager applet. Enable networking was greyed out.
My solution was to kill the applet and restart.
```

ps aux | grep nm-applet | grep -v grep

```
This will return information on the process to kill.
```

username   4690  0.4  1.7 138716 15276 pts/1    SLl+ 20:31   0:02 nm-applet --sm-disable

```
The pid of the network manager applet is 4690
so I need to kill it.
```

kill 4690

```
Alternatively you could run
```
killall nm-applet
```
Then restart the applet with 
```
nm-applet --sm-disable
```
The applet then started up without "enable networking" greyed out.


Prior to doing all this I had also edited /var/lib/NetworkManager/NetworkManager.state
so that its contents were this
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


```
whereas previously "NetworkingEnabled=false" was there.
I'm not totally sure if this was part of the problem or not but you might check the state of this file if the above solution doesn't work.

I hope this helps people!

---

