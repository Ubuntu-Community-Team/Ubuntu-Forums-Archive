---
title: "Disabling bcm43xx driver?"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by Honest AMish on 2011-01-23
Hey, I'm running Maverick Meerkat Ubuntu and I'm trying to figure out how to disable this bcm43xx wifi driver, or something like that.

Personally, I have no clue what this is, but someone said that after you install NDISwrapper and its components, you have to disable bcm43xx driver, otherwise the two will conflict. 

If this is wrong, please just tell me so, but if it's correct, please show me how. 

Thanks in advance!

---

### Post by Honest AMish on 2011-01-24
Bumping this... can anyone tell me how to blacklist?

gedit couldn't handle editing the blacklist.conf :(

---

### Post by bkratz on 2011-01-24
> **Honest AMish said:**
> Bumping this... can anyone tell me how to blacklist?

gedit couldn't handle editing the blacklist.conf :(



Just tried and made sure that you can. Perhaps you are not following the right path:


```
gedit /etc/modprobe.d/blacklist.conf

```

---

### Post by Honest AMish on 2011-01-24
> **bkratz said:**
> Just tried and made sure that you can. Perhaps you are not following the right path:


```
gedit /etc/modprobe.d/blacklist.conf

```

Gah, thanks for showing me how, it worked but it didn't fix the problem.

Now I'm having a very strange problem...

Every time I log into Ubuntu, the wireless adapter works fine. Everything is connected, I can surf the internet, see the network properties, and whatever. After about a solid minute, the network just drops. Then it scans for the network once more, and then the wireless shuts down all together, not even giving me an option to turn it back on. 

This is only fixed if I keep a steady stream of internet flow, like constantly refreshing a firefox page or downloading something. Once I stop, even for a few seconds, it goes down again and I have to restart to complete the process.

Anyone know what's going on?

---

### Post by Honest AMish on 2011-01-26
Okay, now I tried to use NDISwrapper to install the .inf Windows driver for it. Installed fine, but I still don't have a stable connection. It drops in and out, reconnecting and disconnecting to the network, and is even creating a whole new network (Nameofmynetwork 2 is displayed on a different computer using wireless)

Again, any solution is appreciated. Also bump

---

### Post by Honest AMish on 2011-01-29
bumping this

---

### Post by nm_geo on 2011-01-29
> **Honest AMish said:**
> bumping this

try this Code:

```
gksudo gedit /etc/modprobe.d/blacklist.conf 
```gedit can't modify the blacklist.conf until you either sudo or gksudo.

Maybe that will help..

---

