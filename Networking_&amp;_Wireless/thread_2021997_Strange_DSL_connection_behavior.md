---
title: "Strange DSL connection behavior"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by SOIMiMozO on 2012-07-10
Hi, I have an interesting DSL connection issue here, which looks like a  bug. Or maybe I'm just doing something in a wrong way.  So, let me  describe it.
I'm connected to Internet through a DSL wired  connection. Started to use it under 11.04, and it was working without  any glitches, until I switched to 12.04. 
It still worked well, I  could get access to almost everything without problems, BUT some  particular pages just refused to load completely. For example a Firefox  themes page, or [www.speedtest.net]("http://www.speedtest.net") just wouldn't load no matter how long I  wait. At first I blamed Open JDK for it, and switched to Oracle Java,  but nothing changed. I was completely lost, thinking maybe I've messed  something up, with Java installation, and system still uses the OpenJDK  one somehow. But at the same time I got a wireless router with PPPoE  interface onboard. And the problem was gone... When I use router's PPPoE  interface to connect to internet it works properly, but using Ubuntu's  DSL, with direct cable connection brings the problem back.

Maybe someone can explain me, how the PPPoE interface can be related to some particular pages access. 

P.S.  And yeah, tried it on two different machines, with different network  cards and found that problem doesn't exist on livecd or fresh  installation. But shows up after some package upgrades.

upd: Mint 13 has the same problem.

---

### Post by SOIMiMozO on 2012-07-20
Come on, no ideas?

---

### Post by ammofreak on 2012-07-21
Hi ):P
The only thing I can think of right now is the MTU setting. Try lowering it from its' present setting....:)

PS: if I remember right, the maximum MTU for PPPOE is 1492. Please do not quote me on this...

---

### Post by SOIMiMozO on 2012-07-27
> **ammofreak said:**
> Hi ):P
The only thing I can think of right now is the MTU setting. Try lowering it from its' present setting....:)

PS: if I remember right, the maximum MTU for PPPOE is 1492. Please do not quote me on this...

Lowered it to 1492 but no changes so far. Still can't get to firefox themes page. And, considering all other pages go without a glitch I guess it has to be somewhere else.
But thanks for the idea though. It is appreciated.

---

### Post by robert shearer on 2012-07-27
Could be lots of things so I guess you are open to any and all suggestions...:)

My own Firefox page loading strangness was driving me mad.... would load part of a page then hang...usually on something google related...google analytics etc.
Then, when I clicked to another page the original page would load for an instant before Firefox opened the new page.

Thought it was 12.04 but it happened on 11.10 too so thought it was Firefox and replaced the Ffox profile.
That worked for about, oh, a search or two...:(

Then saw a thread for a similar problem solved by installing the Firefox extension Ghostery and configuring it to block trackers.

This has worked for my page load problem and I have since kept adding blocks for just about everything else and not noticed any slow down (that I can't live with...:D ) all pages still load.

You can always disable the plug-in if it does not solve your problem.

---

### Post by SOIMiMozO on 2012-07-31
Thanks for suggestion, but the problem persist on Opera as well. So I guess it isn't browser related.

upd.: Tried to ping those resources. No problems with it. And still Opera an Firefox just stuck on "waiting for response".

---

