---
title: "avahi and ethernet crossover, 169.254.*"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by spazzeri on 2010-07-13
Hello,

in Ubuntu Karmic I was happily connecting my ubuntu laptop to another machine linked to it with a crossover Ethernet cable. I could connect in wicd, then on startup the connection would be established automatically, allowing me to ping ubuntu.local, ssh into it and so on. Both machines were assigned a 169.254.* address automatically.

After the upgrade to Ubuntu Lucid, this automatic behavior is lost ! 
However when one starts **avahi-autoipd eth0** manually, Bob's your uncle it seems.

Is there a way to get back the automatic behavior again ?

---

### Post by Iowan on 2010-07-13
Assuming you use Network Manager, which option did you choose under **IPv4 Settings**?

---

### Post by spazzeri on 2010-07-14
I would like to stick to **wicd**.

I booted on Ubuntu 10.04 Live CD, and chose **'Link-local'** under eth0 IPv4 settings in Network Manager. This establishes the connection as intended.

In Ubuntu 9.10 I had no problem connecting with wicd, which does not have this 'Link-local' option.

---

### Post by Iowan on 2010-07-14
:oops: You DID mention **wicd**... sorry, brain slipped a cog. The **link-local** option is the one I was gonna mention - but you've already been there. I haven't used **wicd**, so I can't be much help - sorry (but I'll give your thread a bump)  ;)

---

### Post by walle1357 on 2010-07-14
You do know that a 169.254.* means trouble, right? Stick with static IPs.

---

### Post by spazzeri on 2010-07-14
> **walle1357 said:**
> You do know that a 169.254.* means trouble, right? Stick with static IPs.

It does not always mean trouble as a matter of fact. It can also imply having so-called link-local with avahi-daemon, which is nice when you need to connect two machines with an ethernet cable.

---

### Post by spazzeri on 2010-07-14
> **Iowan said:**
> :oops: You DID mention **wicd**... sorry, brain slipped a cog. The **link-local** option is the one I was gonna mention - but you've already been there. I haven't used **wicd**, so I can't be much help - sorry (but I'll give your thread a bump)  ;)

Well, thanks. I'm back to using network-manager for the time being. It would be nice to be able to install wicd again though, since it is allegedly better at handling wireless connections.

---

### Post by Iowan on 2010-07-15
> **spazzeri said:**
> It does not always mean trouble as a matter of fact. It can also imply having so-called link-local with avahi-daemon, which is nice when you need to connect two machines with an ethernet cable.
That's kinda what it was intended for - AKA ZeroConf (no configuration) networking...

---

