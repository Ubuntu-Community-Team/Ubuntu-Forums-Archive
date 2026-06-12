---
title: "VPN Disconnects when Transmission Starts Downloading"
date: 2013-04-08
forum: Networking &amp; Wireless
---

### Post by FunkMaster on 2013-04-08
Hello All,

I have just moved from a Windows environment onto xubuntu on one of my older machines. I am running xubuntu 12.10 - I am quite new to linux, but am sort of getting around.

I have configured the machine to connect to a VPN server using PPTP and this works without a problem, that is until the machine starts a Torrent download using Transmission. I can't quite work out what the reason for the disconnect is, but it only happens when Transmission starts downloading.

Any thoughts?

---

### Post by dcstar on 2013-04-08
Check that the MTU settings prevent packet fragmentation inside the PPTP tunnel.

---

### Post by FunkMaster on 2013-04-08
> **dcstar said:**
> Check that the MTU settings prevent packet fragmentation inside the PPTP tunnel.

Hi There,

Thanks for your response, excuse my ignorance but how would I check that or change it as a matter of fact and if I was to change it, what is the recommended MTU?

---

### Post by byt77 on 2013-07-08
Hi,
Today I also enabled a VPN connection on my Ubuntu 13.04 installation and experienced the exact same problem. VPN (PPTP) keeps disconnecting once Transmission starts downloading. Rather it takes 5-10 seconds until it disconnects. I see it's been a while since the original post. I was wondering if your problem was solved. Thanks.

---

### Post by FunkMaster on 2013-07-08
> **byt77 said:**
> Hi,
Today I also enabled a VPN connection on my Ubuntu 13.04 installation and experienced the exact same problem. VPN (PPTP) keeps disconnecting once Transmission starts downloading. Rather it takes 5-10 seconds until it disconnects. I see it's been a while since the original post. I was wondering if your problem was solved. Thanks.

Honestly, I gave up and couldn't figure it out ... Post back if you ever do

---

### Post by byt77 on 2013-07-19
> **FunkMaster said:**
> Honestly, I gave up and couldn't figure it out ... Post back if you ever do

I wanted to check if it has anything to do with the Transmission client. So I installed Vuze and gave it a shot with that. Unfortunately, exact same thing happens, VPN connection is lost after 5-10 seconds of downloading.

---

### Post by byt77 on 2013-07-20
This thing was really annoying me so I decided to change some variables and keep testing it with different settings.
Quick update: I figured out that the disconnection problem does not occur with an OpenVPN connection. I installed my VPN company's OpenVPN Linux client and established a connection. Now neither Vuze nor Transmission causes the VPN to disconnect and torrents keep downloading without any trouble. So at least my problem is solved for now since I don't mind using OpenVPN instead of PPTP. Now the open question is, why does it happen with PPTP VPN? Maybe it does have something to do with the MTU setting dcstar was refering to but unfortunately I don't have enough networking knowledge to modify settings and test it out. Let's see if anyone else can figure out what's wrong.

---

