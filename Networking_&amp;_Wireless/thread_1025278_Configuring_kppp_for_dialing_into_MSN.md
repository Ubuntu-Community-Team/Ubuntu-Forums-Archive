---
title: "Configuring kppp for dialing into MSN"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by cigtoxdoc on 2008-12-29
Using my wireless device, I now have kppp.  kppp found my external modem.  It dials the local MSN dial-up just fine.  Apparently I don't have authentication or flow control correct as I cannot log in.  Get pppd error 16 or 19.  What am I missing?

Also, once I get in, how do I connect to FireFox.

Service with my wireless device is too flaky.  Good speed when 3G otherwise it makes a good dial-up line look fast.

I have noted that others have asked similar questions but no one has replied.

---

### Post by _duncan_ on 2008-12-30
MSN as in Microsoft? I won't be surprised if they require subscribers to use a proprietary Windows-only dialer to connect.

---

### Post by ieee488 on 2008-12-30
You got an answer to the very same question you asked at 
[http://www.linuxquestions.org/questions/linux-networking-3/dial-up-networking-to-bellsouth-or-msn-693771/](http://www.linuxquestions.org/questions/linux-networking-3/dial-up-networking-to-bellsouth-or-msn-693771/)

---

### Post by cigtoxdoc on 2008-12-30
To: IEEE488,

Yes, there was an answer on LQ, but it wasn't helpful.  I have used MSN long enough to remember the MSN/username.  I also get the same pppd errors (16 and 19) when I attempt to use my BellSouth dialup account.

John

---

### Post by ieee488 on 2008-12-30
MSN is Microsoft service after all.
If you are able to get Linux working with it then count it as a bonus. I wouldn't expect Linux to work with them.

Play around with the settings in kppp. If nothing works, then you'll just have to either live with it or switch to an ISP that works with Linux (AT&T Worldnet is one).

---

### Post by cigtoxdoc on 2008-12-30
Thank you IEEE-488. Since BellSouth is now part of AT&T, please let me know what you are using for kppp settings.

john

---

### Post by ieee488 on 2008-12-30
I switched over to Verizon DSL in July 2007.

Since my modem was recognized by Ubuntu 5.04 when I first tried Ubuntu, I installed gnome-ppp and used CHAP and the username/password for AT&T. What is great is that AT&T acknowledges that some people do use Linux - [http://www.wurd.com/instcon_linux.php](http://www.wurd.com/instcon_linux.php).

---

