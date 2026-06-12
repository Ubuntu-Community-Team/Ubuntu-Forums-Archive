---
title: "Ubuntu desktop refused connection to a TightVNC while laptop is granted"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by varelov on 2011-07-12
A very peculiar situation: my Ubuntu desktop (10.04) is refused when trying to connect for Remote Desktop viewing to a WinXP machine while an Ubuntu laptop (10.10) is granted connection although all three are on the same network, both physically and by IP.
Router is a NetGear wired/wireless and WinXP and Ubuntu desktop are connected to it by cables. Ubuntu laptop connects to it via wireless.
WinXP runs TightVNC in order to enable remote desktop viewing from non- win machines. Rules assigned to TightVNC incorporate the range of addresses on my private network given by the router. There is already an exception in Win's firewall to allow TightVNC's port to be open.
When I try to remotely view Win's desktop from my laptop, I am allowed in and can see and work on the desktop of WinXP with no problem. But when I try the same thing from my Ubuntu desktop it says "connection closed".
I have checked all three machines for their IP addresses and they are all in the same network with same netmask.
Is it possible that connection is sorted based on whether it is wireless or wired?
How do I go about Remote Desktop viewing from my Ubuntu desktop to WinXP if it is TightVNC's fault that connections are refused?

---

### Post by varelov on 2011-07-13
When I try to connect from wired win xp to the wired ubuntu, I am also refused connection. Isit really that tight vnc prefers wireless ?

---

### Post by idlemind324 on 2011-07-13
Check if Windows Firewall or any other firewall software is enabled on either interface.

If any firewalls are turned on make sure you exclude the ports for the services you are trying to access.

RDP - 3389 (default)
VNC - 5800 and 5900 (default)

---

### Post by varelov on 2011-07-13
After a restart of ubuntu desktop, the only remote that doesn't work is towards windows. I can remote from win to ubuntu desktop and to laptop.
All ports that you named above were already open on win firewall. Even with win firewall down, ubuntu desktop still can't remote to win.

---

### Post by idlemind324 on 2011-07-14
Is their any firewall enabled on the Ubuntu box? It is possible that a configuration error could actually block traffic leaving the Ubuntu host or coming back in. It's rare but doesn't mean it can't happen. Also what programs are you using on the two linux desktops to view your windows xp desktop (both for vnc and rdp)?

Paste the output from below
```
sudo iptables -L
```

---

### Post by varelov on 2011-07-14
For remoting from ubuntu comps I used their standard built in Remote Desktop Client. By default, no firewall is enabled on both of these boxes. Although I enabled and then disabled ufw on ubuntu desktop. To make it even more odd, I can transfer files to and from shared folders on my ubuntu and win.
 Which led me to try some other vnc software and "SSL/SSH server" that was offered through Ubuntu Software Center did the job of remoting win from wired ubuntu desktop. So now I guess this topic can be marked as solved. And on one of the screens that the newly installed app presented, there was a clue: the thing with tight vnc is it is an extension of vnc so some odd outcomes like this one are totally possible. 
It looks like this vnc app treats only one client as trusted and leave others out despite given settings regarding range of ip to be allowed to connect. Also, in a related article on vnc in ubuntu online docs it is mentioned that tight vnc creates its own kinda virtual version of desktop instead of tunneling it to you.

---

