---
title: "Severe download slowdown with K3565 - V2 3G Modem"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by Nightstrike2009 on 2010-10-09
Hiya everyone,

I am experiencing problems with my Vodafone 3G modem it functions well with Ubuntu 10.04 but some times I get "Download rate: Unknown" messages and downloading seems to hang up.

Ive asked a mate who thinks it is down to 3G networks, it makes it hard to download updates 1st time any ideas on how to get around this?

---

### Post by Nightstrike2009 on 2010-10-09
Ive noticed that enabling [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner makes a difference in "software sources" otherwise the only solution I have found is to download the problem packages manually via "Ubuntu Packages/Lucid" and install via deb.

---

### Post by Nightstrike2009 on 2010-10-09
Well ive got around my problem by manually downloading problem packages and installing via deb but iam sure its supposed to be easier thatn this just to use update-manager with a 3g modem surely?

---

### Post by alexfish on 2010-10-09
Hi

try edit the ppp options /etc/ppp/options

to enable  ip forwarding add this line

[COLOR=Blue]ktune[/COLOR]

remove the # from the #-vj

to look like

[COLOR=Blue]-vj[/COLOR]

change  values of lcp-echo-failure and lcp-echo-interval

[COLOR=Blue]lcp-echo-failure 0[/COLOR]
[COLOR=Blue]lcp-echo-interval 0[/COLOR]

see what happens

alexfish

---

### Post by Nightstrike2009 on 2010-10-12
Hiya alexfish didn't fully understand that

I entered code:

gksudo nautilus

Navigated "Filesystem" to /etc/ppp/options

then got lost has to what to do next, could you please point me in the right direction, thanks.

My update manager is refusing to install "libc" updates, "xulrunner" and "erlang" updates (download speed becomes "unknown" and doesn't respond) all others it has accepted ok (or has after some forced via manual deb downloads)

I have gone to System>Administration>Software Sources and under Ubuntu tab:

Select Download from to "other"
"Select Best Server"
And gone with highlighted server option as UK server wasn't the best, however the same problems persist.

---

### Post by alexfish on 2010-10-12
hi

try this way

sudo gedit /etc/ppp/options

---

