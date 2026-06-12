---
title: "On-board ethernet port not detected- have to use PCI card"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by Dustin2128 on 2011-07-21
I'm running an ubuntu maverick server, and I'm having a slight problem  with networking. I've only got one ethernet line running into my room,  and I've got loads of computers. The server has 2 ethernet ports, one  integrated into the motherboard, one on a PCI card that I took from my  old server. The on board ethernet never worked on my old server- but I  only tried it out post-install, it was hooked up to the card during  install (For the record, networking on linux has *never* worked for me if I installed then plugged in the networking stuff after the fact). So I just used the card instead. Transferred the hard drive  into a new machine, and lo and behold, it would only work after I  transferred in the card from the old one. What I wanted to set up is a  basic NAT system, where the network connection is routed through from my  server to my main desktop- but when I run ifconfig, my card is not  detected, just lo and eth0. How can I fix this?

---

### Post by gordintoronto on 2011-07-21
Does lspci show two Ethernet adapters?

The quick fix would be a switch and one additional short cable.

Here's a top-rated, cheap switch:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122005](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122005)

By the way, I have plugged in networking stuff after the fact numerous times, and never had a problem with it. Installation runs faster if you are not online.

---

### Post by Dustin2128 on 2011-07-21
lscpi does show the both of them. I am not buying anything- both of the ports are good (ethernet worked on an old install), so why waste the money when I know it's possible? Is there a tool I can use to automatically configure the network?

---

### Post by jmoorse on 2011-07-22
Please provide the output of:

```

sudo lshw -c NET
lspci | grep -i ether

```

Perhaps a driver issue with the onboard NIC?  +1 on the avatar too btw

---

