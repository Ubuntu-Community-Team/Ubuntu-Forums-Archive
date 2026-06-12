---
title: "Disconnected, packet loss, any network card"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by Fujk on 2012-01-24
Ok after 6 months of not being able to use Ubuntu on my desktop I gave it another try.

Here is my story.

It begins with the crappy Realtek driver r8169 which does not work properly with my Gigabyte motherboard. I get frequent disconnections and packet loss. This problem has consisted for over 6 months, and I have tried every possible solution out there, from changing drivers, blacklisting the old ones etc. etc.

I do not want to try another Realtek related "solution".

**Nothing works.**

The Realtek card is:

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

Ok so, lets forget about the crappy network card for a minute and continue.

---

I get fed up working this issue for 6 months so I go and buy an Intel PRO PCI card. I am being told this will work 100%.

What happends? SAME CRAP!

I am not joking.

The intel card is:
06:01.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)

Using driver: e1000


**Everything works 100% in Windows 7. It is NOT a hardware failure.**

My packet loss tests consists of 30 minutes of pinging my router and being connected to IRC. In Windows 7 NOTHING happends.

In Ubuntu, regular disconnects and packet loss of 4-7% on the pings.

How the hell is this possible? I'm so pissed off at Ubuntu right now I am about to permanently uninstall this garbage if I can't find a solution.

Please. I need expert help. WTF is going on? How can TWO different cards fail with different brands!

There must be something else going on, like crappy software.

Current installation:
2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 x86_64 GNU/Linux

Ubuntu 10.04 LTS

---

