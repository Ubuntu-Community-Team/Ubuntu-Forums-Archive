---
title: "SSH, VNC, No-IP and port forwarding(!)"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by freshtoast on 2011-03-26
Edited after rethink!

I'm looking for some advice as to the best way forward.

I currently use a commercial VPN when working overseas for secure internet access.

I now also need to VNC to a home ubuntu desktop (which runs software 24/7 that I need to periodically check).

When overseas, I use a Ubuntu laptop and an Android tablet. 

For the VNC I intend to use an SSH tunnel. So my question is: should I ALSO set up openVPN on the home computer (so I can stop paying for a commercial provider which routes all my traffic twice across the Atlantic...) or is it easier/better to use the SSH tunnel for the secure webbrowsing too? Something like a SOCKS proxy?

I am quite new to much of this, so any advice would be appreciated.

Many thanks :)

---

### Post by freshtoast on 2011-03-27
Bump for a complete change of question!

---

### Post by fela on 2011-03-27
This is the way I'd do it: skip the VPN. You don't need it.

Firstly, setup a VNC server on the Ubuntu box you want to control. I assume you know how to do this, but if not just go to System > Preferences > Remote Desktop (ignore message about local-only access).

Then, setup an SSH server on the same box. Edit the sshd_config file (/etc/ssh/sshd_config), and where it says 'Port 22', change it to some other port that you'll remember (of course, if the line's commented, uncomment, if it doesn't exist, add it :D).

This is because people often scan computers on the internet looking for port 22 (the default SSH port), so they can try to hack them. In other words, a non-standard port gives you more security.

After you've done this (and restarted SSH with sudo /etc/init.d/ssh restart), you need to forward the port you chose for SSH using your modem/router, to your Ubuntu box. I assume you know how to do this, but if not then it's just a matter of going to your router's settings page (enter something like 192.168.0.1 in your browser), and it should be easy from there. Obviously, if you're on a shared network, or for some other reason you can't forward ports, this whole plan won't work and you'll have to use a VPN or something :P

After you've got the port forwarded, and noted down your **public IP** (whatismyip.com to check), run this from a remote machine:

```
ssh -p **port_number** -L 59100:localhost:5900 **username**@**public_ip**
```

Then, you should be able to control the Ubuntu box by using any VNC client (such as TightVNC) and connecting to localhost:59100.

---

### Post by freshtoast on 2011-03-27
Thank you for the reply - it's very much appreciated!

The plan for the VNC is to do as you said, although I will need to use No-IP for dynamic DNS.

With regards to secure browsing on the laptop overseas (on the occasions when VNC is not needed), is using the remote desktop the easiest/best way to do simple browsing? Or should I use the SSH tunnel to set up a secure proxy or something similar? Or does ```
ssh -p port_number -L 59100:localhost:5900 username@public_ipp
``` already send everything through the SSH tunnel (not just VNC)?

---

### Post by fela on 2011-03-27
> **freshtoast said:**
> Thank you for the reply - it's very much appreciated!

The plan for the VNC is to do as you said, although I will need to use No-IP for dynamic DNS.

With regards to secure browsing on the laptop overseas (on the occasions when VNC is not needed), is using the remote desktop the easiest/best way to do simple browsing? Or should I use the SSH tunnel to set up a secure proxy or something similar? Or does ```
ssh -p port_number -L 59100:localhost:5900 username@public_ipp
``` already send everything through the SSH tunnel (not just VNC)?

Well with something like secure web browsing, I'm not sure how to set it up using the Ubuntu box as a proxy server. I don't think you'd need an SSH tunnel if the proxy server did the encrypting, but I guess you could use one if it didn't. I guess you could setup a basic unsecure proxy server on the Ubuntu box, and make an SSH tunnel from some random local port (like 59101), to the proxie's port on the ubuntu box. So, as far as the websites' servers that you access are concerned, you're browsing from the Ubuntu box.

One question, seeing as the ISP for your Ubuntu box can see all the traffic going to that, why do you want a secure proxy through it (or did I get that wrong)? Also, unless you have a *very* fast internet connection on your Ubuntu box, browsing is going to be á la 90s ;)

---

### Post by freshtoast on 2011-03-27
Thanks again for the reply.

When I'm overseas I have 2 issues:
1. Normal security concerns when using public hot spots
2. Having 'normal' access to the internet (certain countries have very heavy censorship - things as simple as skype being blocked)

I have no problem with my home ISP or need to hide things from them.

To date, a VPN has satisfied both those requirements. But if possible, I'd like to do it myself rather than using a commercial solution.

My initial thoughts were to run an openVPN server on the Ubuntu box at home seeing as it'll be running 24/7 anyway for the VNC/SSH tunnel.

I'm just not sure if openVPN on the Ubuntu box is the best way to go, or if I can achieve the same results through the existing SSH tunnel? Perhaps a Socks Proxy is totally unsuitable which is what is causing the confusion

---

### Post by fela on 2011-03-27
Hmm, okay, oh yeah come to think of it, BBC iPlayer is blocked outside of the UK and someone I know wanted to do something like this from Israel a while ago, but that's a different story...

I've only ever tried to use a VPN once, and that was to VNC (for fun) my friend's PC, however that never worked. I think the cause for it not working was because I was behind a shared network, and other things, but anyway if you want to go with a VPN I can't give any advice on that :P

As for a proxy server through an SSH tunnel, I've never done that before either :D but it should be quite easy if you've already got an SSH connection working. Just setup a proxy server as per something like [this guide]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html"), and (assuming you've used the port 3128 ), do the tunnel:

```
ssh -p port_number -L 3128:localhost:3128 user@public_ip
```

Then you go to your browser/network settings on your laptop/whatever from overseas, and hit 'proxy server' and point it to localhost:3128 :popcorn:

As I said, I've never done any of this before, but the point I'm illustrating is that if you can get an SSH tunnel and a Proxy server running, putting them together is a piece of cake. So I wouldn't worry about VPNs just yet.

EDIT: oh yeah, forgot to mention, Squid is a good proxy server, the one that's featured in the guide I linked to.

---

### Post by freshtoast on 2011-03-28
That's great - thanks once again for the help.

I'll give things a go and see how I get on

---

### Post by fela on 2011-03-28
Cool, no problem glad to help :D

---

