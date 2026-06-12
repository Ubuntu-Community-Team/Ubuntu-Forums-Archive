---
title: "I'm unable to ping my external ip"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by Abvgz on 2013-04-05
I might be wrong but as far as I remember this has been an issue ever since I started using Linux (not just in Xubuntu - Ubuntu and other distros too). At present my PC has a dual boot with Windows 7 and Xubuntu 13.04 and in Windows I don't face such problems. Whether I ping the IP address itself or a host resolving to it in Windows I don't have any problems.

I'm able to ping 192.168.1.1 (default gateway/router) and other PCs in my LAN as well as 127.0.0.1 and other sites from the WWW in Linux, though.

I looked for a solution but it seemed that no one had the same issue as I do and I couldn't resolve it. It definitely isn't a router or firewall (iptables) problem.

Any kind of help is appreciated!

---

### Post by ahallubuntu on 2013-04-05
~

---

### Post by Abvgz on 2013-04-05
[FONT=Verdana]OK, so I made the following tests and am so frustrated:[/FONT]

[FONT=Verdana]1. Connected my laptop to my neighbour's Wi-Fi (same ISP, different router brands) and booted a Live USB with my current OS (Xubuntu 13.04) - everything worked, pings to the external IP were successful.[/FONT]

[FONT=Verdana]2. Enabled my own Wi-Fi and connected to it (same OS). Tried pinging the IP and the host resolving to it and it worked.[/FONT]

[FONT=Verdana]So it appears that the problem is in my Xubuntu, but where exactly? I don't know what to look for...[/FONT]

[FONT=Verdana]@ahallubuntu, Sadly, it appears that there are some issues. It might work for some people but if I didn't have any problems with it I wouldn't be posting a thread about it, would I? As for the second part of your reply, if pinging was disabled by default I suppose I wouldn't be able to ping anything or be pinged at all. Moreover, it is a problem I face only in linux.[/FONT]

[FONT=Verdana]Edit: Tried the Live USB on my PC and the ping was unsuccessful so I guess it's a driver problem, perhaps? I have an integrated Atheros GbE LAN chip and use the default kernel drivers. Tomorrow I'll test with a PCI LAN card to see if the drivers are the problem. Until then I'm looking forward to more replies.[/FONT]

[FONT=Verdana]Edit2: Yesterday I tried with an external PCI LAN card (Realtek but I'm not sure about the model) and in both PC and Live USB there was no ping to my external IP. I didn't mention that earlier but the strangest thing is that when I start pinging the IP it doesn't show anything like 'Host Unreachable' or a timeout, nothing, there are no further lines. It looks like this:[/FONT]

> [FONT=Verdana]username@username:~$ ping X.X.X.X
[/FONT][FONT=Verdana]PING X.X.X.X (X.X.X.X) 56(84) bytes of data.[/FONT]

[FONT=Verdana]Where might the problem be?[/FONT]

---

### Post by Abvgz on 2013-04-07
[SIZE=2]I researched a bit more and found another tool for pinging (fping) and when issued it shows "X.X.X.X is unreachable" (where X.X.X.X is my external IP) :mad: . Does anybody have any idea where the problem might be? :confused:

Edit: I'm marking this thread SOLVED because it the problem seems to be coming from DMZ enabled for my PC's internal IP, because I'm hosting a game server. My last router (Canyon CN-BR1) seems to have had a 'NAT Loopback' feature and I could ping the external IP even when DMZ was enabled for the internal IP of the PC. My current one is Canyon CNP-WF514 and perhaps it lacks this feature and that's the case. As for the ping available in Linux, they told me in another forum that it was due to Windows somehow determines the IPv4 external address and just pings the gateway on the LAN side (my router).[/SIZE]

---

