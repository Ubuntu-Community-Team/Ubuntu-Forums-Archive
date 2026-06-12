---
title: "masquerade problems ubuntu 9.04"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by corl45 on 2009-09-20
Alright, I have 2 computers upstairs with a wireless router/gateway. The two computers are hooked up through the router/gateway (its both in one, by 2wire 2701 hg-d) by ethernet cables.  we have 2 laptops that connect fine to the wireless.  So I also have 2 desktops downstairs in my room, one of them has a wireless card that I get internet from and a lan card, running ubuntu 9.04 (the one I'm on right now)  and I want to get it to masquerade to the second winxp machine I have in my room so I can get internet on both of the computers.  I'm realativly new to ubuntu, but not entirely, I've tried coutnless tutorials on how to do it, none of which worked.  They all looked about the same, 10 steps involving "ifconfig eth0" and so on.  but I cannot get it to work.  I would assume the tutorials are for people connected directly to the internet, and not through a router so mabey thats why its not working, I'm not sure.  Any help would be appreciated, thanks.

---

### Post by CyberAngel on 2009-09-21
Try the following solution...

Add the following iptable rule on your ubuntu downstairs

```
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

Change wlan0 to your wireless interface whatever this might be.

Now put an ip in a different network on your ethernet interface and connect it with the second computer using a cable and use that ip as the gateway of the second computer.

---

### Post by corl45 on 2009-09-21
Alright! thanks, I'll try it out.

---

### Post by corl45 on 2009-09-21
Sorry about the double post, but I was wondering exactly what "Add the following iptable rule on your ubuntu downstairs" means? Does that mean I enter that line of code into the Terminal with either sudo or sudo su? Or is that something different?

---

### Post by CyberAngel on 2009-09-22
> **corl45 said:**
> Sorry about the double post, but I was wondering exactly what "Add the following iptable rule on your ubuntu downstairs" means? Does that mean I enter that line of code into the Terminal with either sudo or sudo su? Or is that something different?

yes, exactly :)

```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

and then check your iptables using this commands:

```
sudo iptables -v -L -n
sudo iptables -v -L -n -t nat
```

---

### Post by corl45 on 2009-09-24
No dice so far... not sure what to do

---

### Post by creeddd on 2009-09-25
have you tried pinging the router and the other addresses wlan0 eth0 from the other computers.

---

