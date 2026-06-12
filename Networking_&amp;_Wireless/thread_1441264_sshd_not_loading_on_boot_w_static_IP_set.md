---
title: "sshd not loading on boot w/ static IP set"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by aztektum on 2010-03-28
i have my IP statically set via network-manager 

sshd_config is set to only listen on this IP

but sshd doesn't load on boot...

anyone else find it annoying /etc/networking/interfaces doesn't work w/ network-manager installed. i have Ubuntu server running too and it works there, so it makes for a disjointed experience.

of course i could remove network-manager and use wicd, but it doesn't integrate w/ the overall Ubuntu look as well.

---

### Post by 2hot6ft2 on 2010-03-28
> **aztektum said:**
> 
sshd_config is set to only listen on this IP

but sshd doesn't load on boot...
If I set the Listen IP Address in sshd_config to my adapters IP Address it doesn't work either, set it back to "0.0.0.0" and it will work again.
> **aztektum said:**
> anyone else find it annoying /etc/networking/interfaces doesn't work w/ network-manager installed. i have Ubuntu server running too and it works there, so it makes for a disjointed experience.
Yeah, me for one. But this is the first I've heard of it working on the server edition.:confused:
> **aztektum said:**
> of course i could remove network-manager and use wicd, but it doesn't integrate w/ the overall Ubuntu look as well.
It wouldn't do you any good as far as I know WICD was supposed to be able to support 2 simultaneous connections when version 1.6 came out but now they say maybe in version 2.0.
It seems you have a choice of either using a network manager or running without one all together and configuring everything yourself.
#-o

---

### Post by aztektum on 2010-03-29
... [http://instantcrickets.com](http://instantcrickets.com)

All these views and no suggestions. I've Googled this and can't seem to find anything.

To summarize:

Static IP set in networkmanager

sshd_config set to only listen on that IP

sshd does not start on boot

It works on my server box w/o networkmanager with the static IP set in /etc/network/interfaces

I've looked in /var/log/syslog, there are no messages regarding ssh

---

### Post by Iowan on 2010-03-30
Network Manager generally doesn't initiate interfaces until login. If you want network on boot, you may need to consider bypassing (or removing) NM and using */etc/network/interfaces* instead.  
There's still some debate if NM plays nicely with the "interfaces" file.

---

### Post by aztektum on 2010-03-31
I've pretty much established that it doesn't, by assigning a static IP via that method and having no connectivity at all.

I'd rather not remove it, since it has its uses and integrates with the overall look/feel. However it would be nice that attention be given to look/feel/ease of use while not breaking what's already there, what people are familiar with and already works.

I suppose, I'd been thinkin' Ubuntu was gettin' a bit too "user friendly" for me. I'm not at all intrigued by the social networking integration. Seems like a fad to me that will pass in another few years from it's current heights of popularity when the next new things comes along. Remember when IRC, USENET and BBs were the "it" way to communicate online? It just feels like the development time would be better spent in other ways.

Perhaps it's time to switch distros. Been eyeing Arch.

Though I haven't played with Slackware in a while. Perhaps I will roll up the sleeves and get a little crazy. ;)

Sorry for getting ranty. Thanks for the response. :)

---

### Post by Iowan on 2010-03-31
Network Manager seems to store files in different places on different releases. Check */etc/NetworkManager/system-connections* (if it exists) to see if you can modify something there.

---

### Post by chili555 on 2010-03-31
Some here would say that NM and Wicd are *both* a little too "user friendly."

Have you tried adding to /etc/rc.local:```
/etc/init.d/ssh start
```

---

