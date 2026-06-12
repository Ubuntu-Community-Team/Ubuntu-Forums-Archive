---
title: "wierd issue networking xBox to ubuntu"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by kirk ammon on 2009-01-26
I am trying to set up my modded xbox so I can stream music from my computer to the xbox.

I am in a college dorm room with no access to the router. I have my computer connected wirelessly to the internet and I have an ethernet cable running to the xbox. I followed a guide that uses Firestarter to bridge the connections so that the xbox can see the internet. It all worked great. XBMC connects through to the internet (the RSS feed at the bottom loads, and I can look at the weather updates). However, the xbox cant see anything on the local network, including my computer which it is connected through to get to the internet! How can it connect to the internet without seeing my computer?

Anybody know how to fix this? Thanks!

---

### Post by nixscripter on 2009-01-26
If you wanted to do that, you would have to bridge the two networks together. This should help: [https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

---

### Post by kirk ammon on 2009-01-26
Thanks for the reply, but I am a bit confused. I was under the impression that Firestarter does the bridging for me...does this process do anything that Firestarter isn't? Also, I followed the instructions from the article but this does not seem to change anything. no "br0" interface appears in ifconfig. Could you give me some more information on how this is supposed to work?

Thanks for your help.

---

### Post by nixscripter on 2009-01-28
The article I used to point people to disappeared, unfortunately. That was the next best thing, so if it didn't work, let me see what I can do myself.

I don't know much about firestarter, except that what it does is operate on top of a system utility called **iptables**. This utility tells the kernel what to do with packets when it recives them, using a long set of rules. When you "bridge" with firestarter, it probably just wrote a rule something like: when I get a packet from the wireless card, send it to the ethernet card if its final destination is one I don't know about. That is Network Address Translation.

Bridging, in Linux at least, operates at a different level. It takes the two network interfaces (wireless and wired) and creates a "fake" interface which chains them together. Whenever it recieves a packet, it sends it down the other one, under all circumstances, no translation (at the IP address level anyway).

Hopefully that should clear things up. I typed this sort of fast, so if it doesn't let me know.

Now, as for the practical way to do this, there are four steps:

1. Install **bridge-utils** package, either from Synaptic Package Manager, or the **apt-get** utility.

2. Open a terminal, and create a bridge with the command: ```
sudo brctl addbr br0
```

3. Bring both interfaces down and then up, so they don't have addresses: ```
for iface in eth0 wlan0 do; sudo ifconfig $iface 0.0.0.0 up; done
``` This step will disconnect you, but don't worry; if this doesn't work, reboot and you'll have your old settings back.

4. Add the interfaces to br0, raise it, and ask **it** for an address from DHCP (assuming you have it configured that way): ```
sudo brctl addif br0 wlan0
sudo brctl addif br0 eth0
sudo ifconfig br0 up # <-- If this doesn't work, the bridge isn't set up right
sudo dhclient br0

```

Hopefully, this will work. If it doesn't, let me know.

---

