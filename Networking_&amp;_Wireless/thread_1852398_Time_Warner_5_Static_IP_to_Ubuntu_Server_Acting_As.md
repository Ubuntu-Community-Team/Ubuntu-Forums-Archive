---
title: "Time Warner 5 Static IP to Ubuntu Server Acting As A Firewall"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by idlemind324 on 2011-09-30
Basic Information:

I have recently purchased a 5 usable address block from Time Warner cable. They provided me with a SMC 8014 cable modem. I am told the modem is in bridged mode.

My Current Setup:

SMC 8014 <- ETH0 -> Ubuntu Server Firewall <- ETH1 -> SWITCH <-- My other PCs -->

My Concern / Problem:

In using the Ubuntu Server Firewall I set ETH0 to the first of my 5 static IP addresses. I can from another Internet connection ping that address but none of the other 4. In order for it listen for the other 4 addresses I had to set them up as aliases on ETH0. So now I have configured all 5 addresses on ETH0 with only the first usable on ETH0 everything else on ETH0:1 through ETH0:4. The last time I did a Cisco appliance I can't recall actually having to assign each address to the interface. I thought you just had to give it one address and it would listen for all in that subnet then I could port forward what you want back into my private network.

Please tell me if I should be using aliases on my ETH0 NIC or if I am missing something along the line.

---

### Post by Dangertux on 2011-09-30
The alias won't matter so long as when you configure your iptables script you specify the destination. As far as iptables is concerned for -i they will all be eth0. 

An example would be something like this. 

```

iptables -t nat -A PREROUTING -i eth0 -d 66.65.64.63 -p tcp --dport 80 -j REDIRECT --to-destination 192.168.100.5:80

```

Where 192.168.100.5 is the webserver inside and 66.65.64.63 is eth0:0. Then say for eth0:1 you could do this. 
```

iptables -t nat -A PREROUTING -i eth0 -d 66.65.64.64 -p tcp --dport 80 -j REDIRECT --to-destination 192.168.100.6:80

```

For a webserver on the 64 ip. Hope that helps.

---

### Post by idlemind324 on 2011-09-30
I will be giving the iptables method a try shortly!

---

### Post by idlemind324 on 2011-09-30
So by using your rules Dangertux will I still need to have each of my static addresses assigned as an alias on my Internet connected interface (eth0).

Tim

---

### Post by Dangertux on 2011-09-30
EDIT : after thinking about it more , yes

---

### Post by idlemind324 on 2011-09-30
You need the alias entries so the cable modem can find mac addresses to forward the other 4 static IP addresses is that correct?

---

### Post by Dangertux on 2011-09-30
Yes this is correct.

---

### Post by idlemind324 on 2011-09-30
Also when I run your command i get an error:

iptables v1.4.4: unknown option '--to-destination'

x.x.x.x = my production external ip
y.y.y.y = my internal server ip

When I check the manpage the option is there and is said to only work in -t nat -A PREROUTING or -t nat -A OUTPUT. The command as I run it to get the error:

sudo iptables -t nat -A PREROUTING -i eth0 -d x.x.x.x -p tcp --dport 22 -j REDIRECT --to-destination y.y.y.y:22

The command that works for me is:

sudo iptables -t nat -A PREROUTING -i eth0 -d x.x.x.x -p tcp --dport 22 -j DNAT --to-destination y.y.y.y:22

I just want to make sure I should be using DNAT for the -j target.

UPDATE: I am also finding when I use DNAT with -P FORWARD DROP I need to use this rule as well

sudo iptables -A FORWARD -i eth0 -d y.y.y.y -p tcp --dport 22 -j ACCEPT

Is this the correct way to do this or should I have -P FORWARD ACCEPT set?

---

### Post by Dangertux on 2011-09-30
Wow -- I'm sorry REDIRECT is intended for redirecting to another interface on the same system yes DNAT is correct since we are using different systems. (Posting at 3am = bad things ;-))

Also you can set the policy for FORWARD if you want or just make the individual rule. I would prefer the individual rule, and a DROP policy so that anything I didn't want forwarded didn't match any rules and was dropped. That is personal preference though.

So if you wanted to forward SSH your rules would look something like this.

```

iptables -P FORWARD DROP
iptables -A FORWARD -i eth0 -d 66.65.64.63 -p tcp --dport 22 -j ACCEPT
iptables -t nat -A PREROUTING -i eth0 -d 66.65.64.63 -p tcp --dport 22 -j DNAT --to-destination 192.168.100.5:22

```or

```

iptables -P FORWARD ACCEPT
iptables -t nat -A PREROUTING -i eth0 -d 66.65.64.63 -p tcp --dport 22 -j DNAT --to-destination 192.168.1.100.5:22
iptables -A FORWARD -i eth0 -d 66.65.64.63 -p tcp --dport 22 -j ACCEPT
iptables -A FORWARD -j DROP

```It's 3 vs 4 lines either way you slice it and they do the same thing, essentially you just want to drop any traffic that doesn't match a port forwarding rule. :-/

EDIT: Upon thinking more, I think the second option might be the more "accepted" way to go, one it's easier to maintain/understand if  you're not the only one maintaining it, two ; it has less potential to bork and randomly kill packets because iptables is annoying ;-)

---

### Post by idlemind324 on 2011-09-30
Great, thanks for the tips going along I've modified my firewall script to use the slightly longer method.

---

