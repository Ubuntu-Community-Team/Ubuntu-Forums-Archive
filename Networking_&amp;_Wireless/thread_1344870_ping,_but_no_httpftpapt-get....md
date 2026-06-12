---
title: "ping, but no http/ftp/apt-get..."
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by mrcpu on 2009-12-03
Just installed karmic from CD in a ESX server virtual machine.  Install hung at configuring apt-get at 81% for a looooooooong time, finally I hit skip and completed the install.

Boots fine, I can login, I can ping, name resolution works, but nothing moves back and forth.

Like if I telnet to ubuntu.com port 80, I get the "Connected" message, typ ein some garbage and hit 2 returns, I get no reply back.

ufs says the firewall is disabled, but ping works.

It kind of reminds me of the vista issue with disabling auto-tuning because of some TCP/IP/RFC extensions.

If I got to update manager and try to "check", it sits for a loooong time, and then in the added details, they all show "failed".

I can't ftp, I get connected, but no FTP server banner.

Any ideas?

Thanks.

I'm an experienced FreeBSD admin, but less familiar with the ubuntu stuff.

---

### Post by mrcpu on 2009-12-03
OK.  using sysctl to disable tcp_window_scaling enabled everything to work.

How do I make this change permanent in the system startup?

sysctl -w net.inet4.tcp_window_scaling=0

---

### Post by bogo-mips on 2009-12-20
I had the same problem a week or two ago in karmic.

Was connecting via pppoe, and could ping, but could not get anything via firefox or wget.

In the end, setting the pppoe connection's mtu fixed the problem (the window scaling trick didn't work for me).

At first I tried a few conservative settings (about 1400, 100 down from the default 1500), but no luck. It was not until 576 (I think) that it kicked in!

[FONT=Courier New]ifconfig ppp0 mtu 576[/FONT]

---

