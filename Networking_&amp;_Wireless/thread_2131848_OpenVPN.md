---
title: "OpenVPN"
date: 2013-04-03
forum: Networking &amp; Wireless
---

### Post by igwt007 on 2013-04-03
I downloaded OpenVPN the other day and I can't get the software center to install it. So how do manually install it.

---

### Post by ahallubuntu on 2013-04-03
Open a terminal and type:

sudo apt-get update
sudp apt-get install openvpn

If you are using Network Manager in Ubuntu desktop (most people do) and you are trying to connect as a client to an existing OpenVPN server, you might also wish to install the Network Manager plug-in to allow you to connect via Network Manager to the other VPN:

sudo apt-get install network-manager-openvpn

---

### Post by igwt007 on 2013-04-03
Can I connect to the internet by doing that? I'm using my phones internet connection. Thank you for replying.

---

### Post by ahallubuntu on 2013-04-03
A VPN is a Virtual Private Network.  It's a way to connect to another network securely over an unsecure network.  Like: you're at a coffee shop on your laptop, and you want to connect to your home network to access files on your home computer.  If you setup a VPN at home (with say OpenVPN), you connect to it from the coffee shop, and it would be secure from hackers monitoring your activity.

So, no, you don't use a VPN to connect TO the internet.  You can use connection OVER the internet to connect to a VPN.

---

### Post by igwt007 on 2013-04-03
I understand what your saying I can use it to connect to a network. But can I use it to connect to my phones internet connection. Like you can with USB Tether or PDAnet? And the reason why I'm not using them is I can't seem to install the driver for them but I read their might be a way with OpenVPN. Sorry for all the questions I'm very new to Ubuntu. And so far I like it.

---

### Post by ahallubuntu on 2013-04-03
No, OpenVPN is not a way to make an internet connection or tether to another device.

You may be able to tether with Ubuntu to your phone to get on the internet, but you would need either a USB cable or bluetooth or a working WiFi card, depending on what kind of phone it is.  OpenVPN has nothing to do with it.

---

### Post by igwt007 on 2013-04-03
Okay thank you.

---

### Post by staylowproduction on 2013-06-19
Hello. I'm having a lot problems with trying to accomplish what I would like. Maybe there is a better way of going about it, but I'll just post my thinking for now. Please excuse the lack of knowledge as I'm new to android, linux (ubuntu), etc.. Privacy and security is the goal. I currently tether via USB my android to ubuntu to connect to the internet. I've been trying to setup a VPN server via OpenVPN. I can get the server running no problem. I don't even know how to explain this I'm so exhausted, so I'll try to simplify it more. Android tether (USB) -> Ubuntu -> Internet.....how can I get a VPN in here? I also have a DD-WRT router available I would to incorporate somwhere if possible. Android (Gingerbread btw) provides internet via easytether. Does this make any sense? lol....I apologize.

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by helaaaaaa on 2013-06-20
pleeeeeeeese i have a big problem i want to set up a vpn betwen tow local network so i decided to use openvpn but evry time i have a diferent probleme pleaaaaaaaaaaze help me pleaaase

---

