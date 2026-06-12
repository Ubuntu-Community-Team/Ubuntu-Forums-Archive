---
title: "Port Forwarding Madness"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by 23aka23 on 2013-07-09
I'm totally flummoxed trying to set up port forwarding in Ubuntu 12.04.2 so I can upload my share of files in qBittorrent. I've read everything I can find here, and on the net. Tried every guide, every suggestion, everything that seemed relevant, and I'm still at a loss. I'm using a VPN (privateinternetaccess.com) which may be part of the problem. I connect through the VPN well, but then lose that connection fairly often after a few minutes, sending me back to my normal connection. The Ubuntu network icon I click on often flashes on the screen for a half-second, and then disappears like it's had enough of all this, and just wants to run away and hide. Not that I blame it.
 

 Between a static ip address from the ISP, and the static ip from the VPN, opening ports on my modem through my ISP's web site, running commands I don't get yet like ufw enable/disable, setting min and max connections... aeiiii! My download speeds with qBittorrent are great. Right at the speed limit I pay my ISP for, but the uploads are horrendous. About 800kps down/10kps up. One of the things I like about Linux is the sharing, and I'm not able to do so with qBittorrent because, I guess, I can't open a port.
 

 I just switched to Ubuntu (64bitAMD) from Windows, nothing's going to make me go back, and I just can't figure this out. I'd gladly re-install Ubuntu, and start from scratch if that's a good idea. I've been at this for two days now, my dog thinks I've abandoned him, my girlfriend's taken up with a battery-operated companion, and I'm so wired from espresso and nicotine that I feel like Don Knotts on *Adderall*. If there's anyone who knows how to make this work, I'd really appreciate some help.

---

### Post by Cheesehead on 2013-07-09
> **23aka23 said:**
> I'd gladly re-install Ubuntu, and start from scratch if that's a good idea.
Port forwarding is done by the router, not by your desktop, so reinstalling would not solve your problem.

You set up the ROUTER for port forwarding. Log into the router's web interface.
1) Your desktop must be assigned the address that the router forwards to. Else the connection will go somewhere else.

You set up your DESKTOP to simply accept the connection.
2) Firewall set to ACCEPT connections on that port (this is already the default in Ubuntu)
3) An application must be listening on that port, or the connection will be ignored.

Do those in order.

---

### Post by 23aka23 on 2013-07-09
Thanks so much for your reply. It does sound so easy, and I've been trying to do those very things. I've changed my router to accept requests from a slew of ports, some by instructions in guides are random between a certain range lie 49153. I'm guess I'm still unclear on how to assign my desktop an address the router can forward to. Or any address, really. I've tried firestarter, and others, some command line instructions that I think are meant to open a port to my desktop. I've tested port 80, and it does seems to be open, but my uploads remain dismal. The app I'm using to listen is qbittorrent.

I'm sure this can be done, and I'll keep at it till I get it right. Thanks for the definitive statement that re-installing Ubuntu is not a practical approach. If you have any further suggestions, I'm very open to them.

---

### Post by Cheesehead on 2013-07-10
> **23aka23 said:**
> I'm sure this can be done, and I'll keep at it till I get it right.

Do the three steps from my last post *in order*. Don't jump around.

What is the result of Step #1?
Do you know how to configure your ROUTER (not desktop) using it's web pages?
Are you able to configure your ROUTER to issue the same IP address to your desktop every time?

---

