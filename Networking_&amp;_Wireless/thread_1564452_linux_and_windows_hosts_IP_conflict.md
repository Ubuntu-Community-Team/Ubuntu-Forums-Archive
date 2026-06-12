---
title: "linux and windows hosts IP conflict"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by mahmoodn on 2010-08-30
What happen if we assign a static IP address to both linux and windows host?

Consider host A is a ubuntu machine and host B is a windows machine. I first set a static IP for host A (W.X.Y.Z) and connect to it through ssh. Then I duplicate that IP for host B (W.X.Y.Z). 

The result was that I could no longer connect to the ubuntu machine!!:confused:

Any idea?

---

### Post by redmk2 on 2010-08-30
> **mahmoodn said:**
> What happen if we assign a static IP address to both linux and windows host?

Consider host A is a ubuntu machine and host B is a windows machine. I first set a static IP for host A (W.X.Y.Z) and connect to it through ssh. Then I duplicate that IP for host B (W.X.Y.Z). 

The result was that I could no longer connect to the ubuntu machine!!:confused:

Any idea?

Each machine has to have a unique IP address (in the same subnet).

---

### Post by mahmoodn on 2010-08-30
I know that.
What I meant was a test to see what happen in case of ip conflict between linux and windows machines. My result shows that windows can forcibly get linux ip address!!:-x In my network that there are windows and linux hosts, I don't to be the looser!!](*,) If that happen then I can no longer connect to my host (which I remotely connect).

---

### Post by Iowan on 2010-08-30
> **mahmoodn said:**
> Any idea?:confused:What "idea" are you looking for?  A network with two machines claiming the same IP probably won't have a "winner" - just problems.

---

### Post by pricetech on 2010-08-30
There's no way to sort such a thing out where it will work.

I get the feeling your Linux box is a rogue node on someone else's network.

If it's legitimate, you should be able to either use DHCP or obtain an available IP to assign to your Linux box.

---

### Post by v1ad on 2010-08-30
packet conflict!!!

---

### Post by uRock on 2010-08-30
I get the feeling someone is faking a Mac address and the real one is winning.

---

### Post by v1ad on 2010-08-30
> **uRock said:**
> I get the feeling someone is faking a Mac address and the real one is winning.

ooooo that would be fun!!

---

### Post by pricetech on 2010-08-30
> **uRock said:**
> I get the feeling someone is faking a Mac address and the real one is winning.

Hadn't thought about that.  You're probably right.

---

### Post by dmizer on 2010-08-30
If you manually assign IP address 192.168.1.100 to Linux machine A, then subsequently assign 192.168.1.100 to Windows machine B, the Windows machine will &#8220;steal&#8220; the IP address from the Linux machine.

If you manually assign IP address 192.168.1.100 to Windows machine B, then subsequently assign 192.168.1.100 to Linux machine A, the Linux machine will &#8220;steal&#8220; the IP address from the Windows machine.

If you have an environment where this is likely to happen, you will need to configure a MAC filter in your router/gateway so that even if another client attempts to manually assign a duplicate IP address, the router/gateway will not pass traffic to the imposter client.

---

### Post by BkkBonanza on 2010-08-31
dmizer is right here. The reason is that when any machine wants to know who has X ip it iniates an ARP broadcast to find out. It basically sends out a broadcast message saying "who has X ip". The responding machine will say "I AM" and send out it's MAC address. Which machine "wins" in this process probably depends on how quickly, how agressively/repeatedly, or even how slowly they respond. eg. maybe the last response sticks in the requesting machines ARP cache. After this exchange the IP value stays in the ARP cache and is re-used for a period of time until it once again asks the network "who has X ip".

This idea is how hackers can poison local DNS caches and take over local gateways etc. No one would normally do this on purpose and DHCP was created to prevent it happening by accident. But if you use these techniques maliciously you can take over a network, control and filter net access, manipulate DNS resolution etc. Very dangerous.

Two machines having the same MAC address is different but also going to create conflicts and problems, though of a slightly different character since they both will hear and talk as if the same machine. In an IP conflict only one machine gets to be the "active one" but here both can be "active".

---

### Post by mahmoodn on 2010-08-31
> **dmizer said:**
> If you have an environment where this is likely to happen, you will need to configure a MAC filter in your router/gateway so that even if another client attempts to manually assign a duplicate IP address, the router/gateway will not pass traffic to the imposter client.
This is the idea I was looking for. Thanks:)

> Which machine "wins" in this process probably depends on how quickly, how agressively/repeatedly, or even how slowly they respond. eg.
So there should be some parameters that can be changed. aren't they?

---

### Post by BkkBonanza on 2010-08-31
Not that I'm aware of. A MAC filter is only useful if you know the MAC of an offending machine, or the MACs of valid machines. And for potentially offending machines they can always spoof a different MAC once they know they're blocked. So a MAC filter isn't very functional against malicious intent, though it may be useful against some known network configuration that you can't otherwise avoid.

---

