---
title: "Intel Network Card Up/Down on current 10.04"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by herrmoody on 2010-05-18
I am running Lucid Lynx and have only noticed this problem in the past couple weeks.  Before Lucid I ran Jaunty & Karmic on this same box, although I installed Lucid as a clean install.

My problem is that up to 5 or 6 times per minute my networking card drops its connection and then has its connection re-established.  I have an integrated Intel 82566DC gigabit card on an Intel Motherboard DG35EC connected to a 10/100 network and am running the 64-bit version of Lucid.  I've done some considerable searching on this problem and although I've seen many references to similar problems dating back several years, I have found none that seem to have any solutions that do anything for me.  I never had this problem under any prior version of Linux on this box (all prior versions were also 64-bit).

In short, this block of messages repeats in my messages log:

May 18 20:18:50 mark-desktop kernel: [10121.062129] e1000e: eth0 NIC Link is Down
May 18 20:18:52 mark-desktop kernel: [10122.730873] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
May 18 20:18:52 mark-desktop kernel: [10122.730876] 0000:00:19.0: eth0: 10/100 speed: disabling TSO

Most of the time I don't even see that the connection has gone down.  Sonetimes everything seems to be operating fine for a half-hour or more, although it could be dropping out and coming back really quickly all of the time. Sometimes it goes out for 10 seconds.  Sometimes it goes out for many minutes and I can get networking back by killing disabling networking and then re-enabling it.  It's quite annoying.

I'm sorry if I'm duplicating an existing issue on this forum, but I can't find this exact problem anywhere.  Does anyone have any clever ideas about how to fix this?

---

### Post by herrmoody on 2010-05-20
I've noticed that this problem is also logged in the syslog, kern, and daemon logs.  I thought maybe it might be something strange in the Network Manager that is causing this problem, so I removed it and configured the network manually with a static address using /etc/network/interfaces.  All this seems to have done is remove the error messages from the daemon logs.  The syslog, kern, and messages logs continue to accrue "eth0 NIC Link is up/down" messages.

---

### Post by herrmoody on 2010-05-20
I suspect this may be some kind of problem with the e1000e driver.  The symptoms are similar to a [bug report I found in the Sourceforge forum]("http://sourceforge.net/tracker/?func=detail&aid=1975565&group_id=42302&atid=447449") for the driver although that problem was related to having AMT enabled on an Intel motherboard, and my motherboard does not support AMT.

---

### Post by herrmoody on 2010-05-27
This problem has gone away in a somewhat mysterious fashion.  The main thing I did before it went away was install LyX and all of its dependencies, but how this could affect network connectivity is beyond me.  Maybe another update or some other change affected it.  At any rate, it went away.

---

### Post by herrmoody on 2010-05-27
Almost as soon as I posted that this started happening again.  Very strange.  It stopped and behaved well for a couple days and then started going on/off again.

---

### Post by herrmoody on 2010-06-08
I finally found the cause of this problem and I'm happy to say that it's not completely the OS's fault (and in fact the OS may have played no role whatsoever, although I'd have to be much more of a networking guru to say that definitively).  My Ubuntu box is plugged into a switch into which I had a connection from my router and a Netgear PS121 print server plugged in.  After a while I noticed that occasionally all of the lights except the computer's port light would just go black.  It seems the print server was sending out some kind of weird/nefarious/screwed up signal out on the switch that was somehow breaking the connection.  It would do this frequently.  I unplugged the print server and the problem immediately stopped.

I would certainly love to know why this happened, but I'm happy just having solved this thing for now.

---

