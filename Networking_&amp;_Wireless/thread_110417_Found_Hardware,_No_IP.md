---
title: "Found Hardware, No IP"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by Jeff12088 on 2005-12-30
After a few days of tackling, finally got Ubuntu to detect my network card and load my driver but just couldn't browse the web. I tried following the ethernet troubleshooting:

whenever I type "ifconfig" I see eth0 driver loaded but no IP address.
I'm using DHCP so I typed "dhclient eth0" and got "No DHCPOFFERS recieved."

Tried route -n and no results.

Typed "cat /etc/resolv.conf":
"search gateway.2wire.net
nameserver 172.16.0.1"

Went "mii-tool eth0"
and I get "Operation not supported" even though I did plugin the ethernet cable and the light on the card does blink.

Help?

---

### Post by fordfan753 on 2005-12-30
Is it possible for you to set a static ip?

---

### Post by Jeff12088 on 2005-12-30
Not possible, I have DSL and I don't have a static IP :( 
I got Wireless working with this same computer using DHCP and doesn't work with static

---

### Post by fordfan753 on 2005-12-30
Hmm, ok.
My first thoughts, is that if you're on DSL, then maybe your DNS servers are wrong...but that shouldn't really make a difference because DHCP is broadcast.

---

### Post by darth_vector on 2005-12-30
[QUOTE=Jeff12088]Not possible, I have DSL and I don't have a static IP :( 
I got Wireless working with this same computer using DHCP and doesn't work with static[/QUOTE]

your DSL modems internal IP is static, its just its external IP that isnt. you can do whatever you want in your internal network.

---

### Post by fordfan753 on 2005-12-30
[QUOTE=darth_vector]your DSL modems internal IP is static, its just its external IP that isnt. you can do whatever you want in your internal network.[/QUOTE]

This is the case most of the time, but not all modems support NAT

This raises a good point though...what make/model is your modem or router?

---

### Post by Jeff12088 on 2005-12-30
Well, if I try static, I don't have an static external IP so I can't fill out that spot.

I have a 2WIRE Homeportal1000HW router/gateway.

---

### Post by fordfan753 on 2005-12-30
If your modem supports NAT, then this wont be a problem

---

### Post by darth_vector on 2005-12-30
[QUOTE=fordfan753]This is the case most of the time, but not all modems support NAT[/QUOTE]

oops, really!? my mistake :oops:

---

### Post by Jeff12088 on 2005-12-30
Yes it does support NAt according to this document: [http://www.2wire.com/pages/pdfs/106.pdf](http://www.2wire.com/pages/pdfs/106.pdf)
The model number is the 1000HG

Actually.. maybe I need to restart my gateway like last time when I setup the wireless

---

### Post by fordfan753 on 2005-12-30
[QUOTE=darth_vector]oops, really!? my mistake :oops:[/QUOTE]

Not really a mistake at all...99.999% or all modems I've come across do utilise NAT quite well...

OK, one thing to realise Jeff12088, there are different types of networks, being very brief and ignoring half of what I learned in CCNA, I'll just tell you about the two that matter. They are the WAN, and the LAN. WAN is Wide Area Network, this usually refers to the internet. LAN is Local Area Network, which is common in a lot of houses. Basically you have a LAN, even if it only has one computer on it. Now, the modem is your boundry between the LAN and the WAN (internet). On one side of the modem is the WAN, on the other is the LAN. Your ISP is on the WAN side, your ISP will give **the WAN interface** or your modem an IP address, this address has nothing to do with your LAN addressing scheme. Ok, now on the other side of the modem, your side, there is another interface, this is usually ethernet, or USB, or even wireless. This interface will also have an address, but it will be independant from the address on the WAN side of the modem. It's important to think of an interface as having the IP address, not the actual device.

What it looks like, is that your modem isn't giving your computer an IP address, so you're going to have to specify one. But in order to do that we first have to find out the IP address of your modem. We can find that using ping.

try ping xxx.xxx.xxx.xxx
where xxx.xxx.xxx.xxx can be the following addresses..
10.0.0.1
10.0.0.254
10.1.1.1
10.1.1.254
192.168.0.1
192.168.0.254
192.168.1.1
192.168.1.254

The one that gives you a reply will most likely be your modem, from there I can give you a static IP to use that corresponds to the LAN interface of your modem.

---

### Post by fordfan753 on 2005-12-30
That was more long winded than I intended, but I hope it helps. It's just some people know this stuff, but some people don't, it's not neccessarily because it's hard, it's more because no one ever told them that before...

---

### Post by Jeff12088 on 2005-12-30
Thanks for your reply, I've pinged all 8 addresses you supplied and none gave me a result. All of them resulted "Network is unreachable".

On my management, 
it tells me this, just thought it might be helpful
```
Internet Address:  	 	69.107.58.236
Subnet Mask: 		255.255.255.255
Default Gateway: 		151.164.184.83
```

---

### Post by Jeff12088 on 2005-12-31
Problem solved.
All I did was restart my gateway and replugged all the lines that were used.
Typed in 
```
dhclient eth0
```
Recieved a response, boo!

---

