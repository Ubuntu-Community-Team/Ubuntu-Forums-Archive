---
title: "pppoe problem after update to from 5.10 to 6.06"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Michal77 on 2006-06-04
Hi every one,
I updated today ubuntu 5.10 to 6.06. I did it by update manager. Everything gone well, but after restart system I lost my connection via pppoe.
I reconfigured pppoe and check it by plog command:

Jun  4 13:14:18 localhost pppd[5523]: pppd 2.4.4b1 started by root, uid 0
Jun  4 13:14:53 localhost pppd[5523]: Timeout waiting for PADS packets
Jun  4 13:14:53 localhost pppd[5523]: Unable to complete PPPoE Discovery
Jun  4 13:15:58 localhost pppd[5523]: Timeout waiting for PADS packets
Jun  4 13:15:58 localhost pppd[5523]: Unable to complete PPPoE Discovery
Jun  4 13:17:03 localhost pppd[5523]: Timeout waiting for PADS packets
Jun  4 13:17:03 localhost pppd[5523]: Unable to complete PPPoE Discovery
Jun  4 13:17:56 localhost pppd[5772]: Plugin rp-pppoe.so loaded.
Jun  4 13:17:56 localhost pppd[5774]: pppd 2.4.4b1 started by root, uid 0

After check it by ifconfig ppp0 I’ve this:

ppp0      Link encap:Point-to-Point Protocol
          inet addr:61.51.178.57  P-t-P:61.149.8.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:489 (489.0 b)  TX bytes:377 (377.0 b)


What to do? I was working in 5.10 brilliant and now… ](*,) 
M.

---

### Post by Michal77 on 2006-06-04
Strange. It's just started working when i restarted comp to install rm-pppoeconf...
First show info about siolgifflags. I clicked ok and started working...
:confused:

---

### Post by Michal77 on 2006-06-05
[QUOTE=Michal77]Strange. It's just started working when i restarted comp to install rm-pppoeconf...
First show info about siolgifflags. I clicked ok and started working...
:confused:[/QUOTE]

And today stop working again. Why it one time works other doesn't? I change nothing. I'm fresh in Linux. Somone can explain me what's wrong? I didn't had this problem in 5.10 it started after up-date to 6.06... ](*,) 
M.

---

### Post by ojacquem on 2006-06-06
Hi Michal,

Just a short message to let you know that I'm experiencing the very same problem. No solution yet.
I had a quick look at the bug tracker system: bug
[40741]("https://launchpad.net/distros/ubuntu/+bug/40741") seems close to our problem.  For me the internet connection is OK until I stop using it for a few minutes.

Did you try posting a bug report on your own?

_Olivier_

---

### Post by Michal77 on 2006-06-11
[QUOTE=ojacquem]Hi Michal,

Just a short message to let you know that I'm experiencing the very same problem. No solution yet.
I had a quick look at the bug tracker system: bug
[40741]("https://launchpad.net/distros/ubuntu/+bug/40741") seems close to our problem.  For me the internet connection is OK until I stop using it for a few minutes.

Did you try posting a bug report on your own?

_Olivier_[/QUOTE]

Hi,
I think our problem is similar to this bug:
[https://launchpad.net/distros/ubuntu/+source/rp-pppoe/+bug/34277](https://launchpad.net/distros/ubuntu/+source/rp-pppoe/+bug/34277)
I didn't try this solution yet. Be honest I given up. I check Aurox, Mandriva and Suse there are not problems with pppoe and for now I’m going to stick to Suse. 
Pity! I really liked Breezy but I need comp to work and keep windows for be able to work with Linux... pointless. Maybe I’ll try next Ubuntu.
I don’t expect miracles but new edition shouldn’t be worst like previous. Especial internet connection should be well done cause how I can get help without Internet? windows? But them where is point to switch to Linux if I’ll need windows in case new update f… up my internet connection? etc)…
:-?

---

### Post by erbuc on 2006-06-11
Hi,
I am having similar problems, but this happens to my connection no matter if it is idle for 5 minutes or not. After 5 minutes, I get a little warning triangle up near the network icon at the top of the screen. The the red circle with a line thru it.

If I wait a minute or two, the connection is restored and the red circle goes away.

I am using a Broadcom Giabit ethernet card on a Dell Latitude D400. The NIC is connected via an Ethernet cable to a Billion ADSL modem. No dual boot or anything strange, just a straight install of 6.06. I do also have a WLAN card and a modem, but I have not tried connecting using either of these methods as yet.

I have also noticed that when I look at the Network interfaces, I see PPP0, PPP1 and PPP2. These tend to come and go over time and a PPP3 shows up. At one point, only PPP0 and PPP1 were present and I could browse the Internet, etc. Both had IP addresses assigned to them. This doesn't sound right to me.

Newbie,
Eric

---

### Post by Michal77 on 2006-06-11
Hi everyone,
My curiosity won and I tried again. I made fresh installation of Drapper. No problems with set pppoe and it works but after restar no connection at all. Even after new reconfiguration by pppoeconf the same story like in my first post. I tried all tricks from forums and still nothing.
So I deleted Drapper and installed Breezy and&#8230; no problems. Internet still works after few restarts and you can read this message&#8230;
Michal

---

### Post by Michal77 on 2006-06-14
Hi,
I made update from Brezzy to Dapper... again but this time by alternative CD.  Of course no network after. Reconfiguration by pppoeconf or pon dsl-provider doesn't change nothing. Anyway i found that if I restart machine with ADSL router (D-Link 500) switch off and swith on when machine already run and them pon dsl-provider I've network. Of course during next restart I've to keep ADSL router switch off again and start conection by pon dsl-provider.
Maybe it'll help someone...

---

