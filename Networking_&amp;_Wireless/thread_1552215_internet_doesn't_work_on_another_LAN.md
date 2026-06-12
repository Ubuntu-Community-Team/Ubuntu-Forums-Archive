---
title: "internet doesn't work on another LAN"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by llabdeepS on 2010-08-13
I installed Ubuntu for the very first time on my old Toshiba labtop anf it worked wonders compared to windows xp.
We then moved and are using a different router and it wont connect via wired nor wireless connection and i have given up after 6 hours of no progress and endless serching through posts on the internet.
 
I never used any linux based OS before so something that might seem obvious to an advanced user, is probably latin to me :D

---

### Post by Kerubu on 2010-08-13
You say you are now using a new router, do you have any other computers working through this new router?

And when you say router, is this a wireless base/ADSL modem? (If that sounds gobbeldy-gook, post the make an model so I can look it up on the internet)

Also, if you know how to bring a terminal window up, try the command :

ifconfig

And post the results

---

### Post by kiridude on 2010-08-13
This may seem obvious, but did you set up a password and username with the new router. What errors do you get when trying to connect with the wire?

---

### Post by llabdeepS on 2010-08-13
There's several other computers on the network wired/wireless including the one i post from now. All using Windows 7/Vista/XP.
Everything worked fine before we moved and i have updated stuff via the update manager in the old apprtment.
 
The labtop model is Toshiba Satellite A100-570 model no. PSAA2E-05J02CED
 
I get no errors, it cannot see the network at all. The router doesn't see it in status. 
Yes i have tried with cables i know work.
 
Result of ifconfig:
[SIZE=3][FONT=Times New Roman]lo Link encap:Local Loopback [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]inet addr:127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]RX packets:20 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]TX packets:20 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]collisions:0 txqueuelen:0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]RX bytes:1200 (1.2 KB) TX bytes:1200 (1.2 KB)[/FONT][/SIZE]

---

### Post by kiridude on 2010-08-13
Did you set up the network?

maybe the router is set to "invisible" or maybe the security settings are set to only allow machines whose mac addresses have been entered into the router.

---

### Post by llabdeepS on 2010-08-13
> **kiridude said:**
> Did you set up the network?
 
maybe the router is set to "invisible" or maybe the security settings are set to only allow machines whose mac addresses have been entered into the router.
 
What exactly do you mean "did you set up the network" ?
The router is a D-Link DI-524 with pretty much default settings
There's no mac addr., port restritions or such.
 
It just worked back home and it wont now.

---

### Post by Kerubu on 2010-08-13
This looks as though the networking in Ubuntu has been disabled (your ethernet and wireless cards are not showing up). If you're on 10.04 this is a known bug :

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454")

To enable either right-click on the network icon on the ubuntu bar (top right) and select enable networking or follow the instructions given in the solution in the above link.

Let me know if that fixes it.

---

### Post by kiridude on 2010-08-13
1

---

### Post by llabdeepS on 2010-08-13
Sorry for the late reply but they are digging the raod up, and apparently the interet cables too, so just got the net back.
awesome Kerubu
Manually stopping/starting the network via 
service network-manager stop
service network-manager start
worked wonders. If it is a known bug i really dont know why i dnt find it during my 6 hours quest.

---

### Post by Iowan on 2010-08-13
My Internet has been up/down this afternoon, too. (storm?)
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") ? :)

---

### Post by llabdeepS on 2010-08-25
It's done it again.
This time it says i cant delete the networkmanager.state files because i am not the owner.
This is the only account on the computer, so what do i do now?

---

### Post by dineshs on 2010-08-25
try [COLOR="Blue"]sudo[/COLOR] before the commands

---

