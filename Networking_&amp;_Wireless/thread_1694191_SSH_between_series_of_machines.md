---
title: "SSH between series of machines"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by Kaiyoti on 2011-02-24
Hi, 
I have a problem that I'm trying to solve with a lack of some network knowledge. At least I thought I knew them.

This are my machines:
1. Ubuntu Desktop - OpenSSH
2. Asus WL520 Router (with Tomato firmware) - DropBear
3. DNS323 Server - OpenSSH
4. Windows 7 Desktop - Putty

@Home
(3) DNS323 server is WAN accessible (via ssh) 
(4) Windows 7 is not WAN accessible.

@Office
(1) and (2) are both not accessible via WAN.
(1) and (2) are in the same network (192.168.1.x)

```

(192.168.1.5)                         (192.168.2.1)
[Ubuntu]----[Firewall]----[Internet]----[DNS323]----[Windows 7]
               |                                   (192.168.2.2)
[Asus WL520]---+
(192.168.1.6)

```

Windows 7 and dns323 are actually in the same network but for the sake of this problem, I'll use the diagram above.

So currently I have a persistent reverse ssh connection between (2) and (3). Reason why these two are used is because they are online 24/7, (1) Ubuntu and (4) Windows 7 gets rebooted everyday. This connects the Home with the office via (dropbear):
```
ssh -R 2210:localhost:22 -g -N -f USER@HOMEIPADDRESS
```

This allows me to use putty at home to connect to my DNS323 server (which in turn connects to ASUS WL520G. (It has remote port access available). Basically I can access office network(2) from my porn machine (4) via 
```
ssh -p 2210 USER@192.168.2.1
```

My problem is that I need to access (ssh) my Ubuntu Desktop (1) directly from my Windows 7 to the Ubuntu. 

How would I do this? I tried opening up another local port forward on the DNS323 via (making two connections, one home-bound, and one ubuntu bound)
```
ssh -L -g 5566:localhost:5566 USER@192.168.1.5
```
I'm hoping the -g allows remote connection

Then in my Windows 7 (4) with Putty, I added another forward
which is basically the same thing 
```
L5566 localhost:5566
```

Does this not allow me to connect to 5566 on my Windows 7 which will get routed to Ubuntu on port 5566? This doesn't seem to work.
Am I overthinking this? Would I be able to port forward directly from the initial reverse SSH between (1) Ubuntu and (3) DNS323 via:

```
ssh -R 2210:192.168.1.5:22 -g -N -f USER@HOMEIPADDRESS
```

Help is much appreciated.
Paul

---

### Post by Kaiyoti on 2011-02-24
Maybe I should've tried that last one before I asked it.

It works :)

---

