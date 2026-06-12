---
title: "my DHCP broke yesterday from updates"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by dgw on 2010-04-11
I recently added the network-manager trunk PPA to my software sources because I was trying to connect to a VPN. I never managed to connect to the VPN, and I gave up on trying (see: [http://ubuntuforums.org/showthread.php?t=1438211](http://ubuntuforums.org/showthread.php?t=1438211)).

Yesterday-ish updates broke DHCP on my computer. I um... saw some message about it when it happened, and it kinda went in one ear and out the other. It was from the routine updates. I'm not sure how I can just sorta click OK to something like that and not realize I messed up until a day later, and feel sorta stupid for this. Anyone kind enough to point me in the right direction for how to get DHCP working again? I don't care about trying to connect to the VPN anymore.

---

### Post by dgw on 2010-04-12
Can I mark this thread as "it sorta works now"? I forced it to use old versions of network-manager-gnome and dhcp3-client in synaptic, and I seem to now be connected with DHCP. It's a little confusing because the network-manager icon is spinning endlessly and the output from ifconfig is just freaky now, and I can imagine breaking it again shortly... 

Anyway, as long as it's working, I don't want people to spend their time trying to help. Thanks.

---

### Post by Iowan on 2010-04-12
Feel free to post results of **ifconfig -a ** and contents of */etc/network/interfaces* (which ordinarily has only two lines defining "lo").

---

### Post by dgw on 2010-04-13
<snip> Removed my ifconfig and /etc/network/interfaces, because I no longer need help with this. Posting on my neighbor's wifi just so I can laugh about how DHCP is working.

I googled, and I found this: [http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/](http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/)

And now I feel a bit dumb. I re-enabled the PPA, installed ppa-purge, purged the PPA, and now everything seems to be normal again. Now how to do I make the topic [solved]?

---

### Post by Iowan on 2010-04-13
> **dgw said:**
>  Now how to do I make the topic [solved]?I see you figured that out too...=D>

---

