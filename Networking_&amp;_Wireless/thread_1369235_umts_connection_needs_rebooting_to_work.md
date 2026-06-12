---
title: "umts connection needs rebooting to work"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by mpolito1969 on 2009-12-31
I have posted this problem several times in the last two years without getting a lot fo help (this time I have some more information). If you can't help me but have some suggestion about where I could find some help that would be very useful too.

I use an ASUS laptop (F3SR) with an internal HSDPA modem and I've always had the following problem.

When I start the computer, sometimes it can't connect, if I reboot my computer sometimes it starts sometimes it doesn't. If I reboot it enough times (also 5-6 times) sooner or later UMTS connection starts.

I've got a feeling there is a synchronization problem, depending on "when" services are started the modem gets found by the system or not. Sometimes it's found on the wrong port.

Today I've noticed the following difference.

When UMTS works, 'nm-tool' output contains three sections: eth0, wlan0 and ttyUSB0 (this is my UMTS modem).

When it doesn't work that output can have only two sections (eth0 and wlan0, without ttyUSB0), or three sections but while the first two are the same as before, the third one is ttyUSB2 instead of ttyUSB0.

In both cases the only workaround I have found is rebooting, after some reboots things start working properly (generally).

Does anybody knows about a better solution to this problem? Is there a way to have the same result by only rebooting some services instead rebooting the computer? Is there a way to force network-manager to use ttyUSB0 instead of ttyUSB2 for my UMTS modem?

Ciao,
Max

---

### Post by mpolito1969 on 2010-01-03
This morning (8:00 to 9:00) it was really bad, I rebooted 6-7 times without being able to connect (nm-tool showed my UMTS modem on ttyUSB2).

I've just succeeded, after two more reboots (now nm-tool correctly shows my UMTS modem on ttyUSB0).

Ciao,
Max

---

### Post by mpolito1969 on 2010-01-03
Come on... I've been rebooting for two years, I'm sure Linux was not designed to work like that.

I need to understand why network-manager uses sometimes ttyUSB0 and sometimes ttyUSB2. If you can't help me, would you please point me to a site/forum/mailing list where I can get some help?

Ciao,
Max

---

### Post by mpolito1969 on 2010-01-08
Just in case someone else would come here in the future with the same problem...

NetworkManager community sent me this link:

[http://cgit.freedesktop.org/ModemManager/ModemManager/commit/?id=2fc0c039e65173123a39a0fb6c8f44804cbd773a](http://cgit.freedesktop.org/ModemManager/ModemManager/commit/?id=2fc0c039e65173123a39a0fb6c8f44804cbd773a)

it's about a patch in ModemManager that should solve the problem.

I don't know how to apply that patch but I'll ask Ubuntu maintainers if they can release a fix for Ubuntu.

Ciao,
Max

---

