---
title: "Ubuntu dedicated proxy server in US for use in China."
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by endor43 on 2011-01-11
Hey all,

I have a question to pose. But first, I'll let you know what im working with:

Intel Core 2 Extreme QX6700 2.93ghz
Nvidia nforce 680i SLI Chipset (has integrated gigabit ethernet)
4Gb DDR2 RAM 800mhz
Dual 8800GTX in SLI
Desktop Maverick x64

I live in the US and have done so for most of my life. As such I am used to free and unrestricted internet access, at high speeds. I will soon be moving to China for about a year, and am aware that they are no so fortunate with regards to the above. I understand that speed is always going to be more of an issue with internet in China, but I'm more concerned about unrestricted access (New sites, facebook, youtube,torrent(all totally legal files of course)).

So here's the question:
How can I use ubuntu with my machine to set up a dedicated proxy server that I leave in the states, in order to be able to connect to its global ip with various programs (firefox[using foxyproxy etc], transmission,qtbittorrent, etc)when im in China, in order to have unrestricted access?

I would assume switching to server edition is part of this process, but im pretty much in the dark here. I'd really appreciate some help.

Thank you,
Endor

---

### Post by PatchesTheCaveman on 2011-01-11
All you need is an SSH server installed (you can do this on any version of Ubuntu) and you can create an encrypted tunnel between any computer and it for Internet access.  Just install the *ssh* package via the Ubuntu Software Center, Synaptic, or by running this command on a terminal:
```
sudo apt-get install
```

Open your firewall for Port 22 and configure your router to forward the port if necessary.  Also, if your ISP ever changes your IP address you'll want to configure Dynamic DNS so you don't lose your connection if your IP address changes.  

Then, on your faraway computer, just open a terminal and run this command to establish the tunnel:
```
ssh -N -D localhost:3128 *<IP address/dyndns domain name>*
```

Then, go to System > Preferences > Network Proxy and configure your SOCKS proxy to server *localhost* on port *3128*.  All Internet connections will now go through the tunnel until you disable it.

---

### Post by solongsoho on 2011-09-21
I'm sorry if my post will sound silly but I don't really know what this program is about. I am in China for one year, studying and I wanted to use it in order to have access to different websites.

Firstly, after I install the metapackage "secure shell client and server" what do I have to do? I'm using Ubuntu 11.04 and I don't know anything about having any kind of firewall on it. Also, can I establish my proxy server without having another computer to rely on?

---

