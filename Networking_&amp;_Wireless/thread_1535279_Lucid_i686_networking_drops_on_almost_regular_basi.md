---
title: "Lucid i686: networking drops on almost regular basis"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by kimbo305 on 2010-07-20
Here's my kernel info:
Linux T61MMAO-linux 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

This issue cropped up today at work, which is the only place where I used a wired connection.

Between last Friday (7/16, when I lasted use the wired connection with no incident) and today (7/20), I've upgraded the following packages:
Start-Date: 2010-07-16  20:43:51
Upgrade: libusb-0.1-4 (0.1.12-14ubuntu0.1, 0.1.12-14ubuntu0.2), gwibber-service (2.30.0.1-0ubuntu3, 2.30.1-0ubuntu1), nautilus (2.30.1-0ubuntu1, 2.30.1-0ubuntu1.1), evince-dbg (2.30.3-0ubuntu1, 2.30.3-0ubuntu1.1), libevview2 (2.30.3-0ubuntu1, 2.30.3-0ubuntu1.1), libatspi-dbg (1.30.0-0ubuntu2, 1.30.1-0ubuntu1), empathy (2.30.1.1-0ubuntu1, 2.30.2-0ubuntu1), nautilus-data (2.30.1-0ubuntu1, 2.30.1-0ubuntu1.1), nautilus-sendto-empathy (2.30.1.1-0ubuntu1, 2.30.2-0ubuntu1), libpanel-applet2-0 (2.30.2-0ubuntu0.1, 2.30.2-0ubuntu0.2), libatspi1.0-0 (1.30.0-0ubuntu2, 1.30.1-0ubuntu1), gnome-orca (2.30.0-0ubuntu3, 2.30.2-0ubuntu1), python-pyatspi (1.30.0-0ubuntu2, 1.30.1-0ubuntu1), python-vte (0.23.5-0ubuntu1, 0.23.5-0ubuntu1.1), libvte9 (0.23.5-0ubuntu1, 0.23.5-0ubuntu1.1), at-spi (1.30.0-0ubuntu2, 1.30.1-0ubuntu1), dpkg (1.15.5.6ubuntu4, 1.15.5.6ubuntu4.1), evince (2.30.3-0ubuntu1, 2.30.3-0ubuntu1.1), gnome-panel-dbg (2.30.2-0ubuntu0.1, 2.30.2-0ubuntu0.2), libevdocument2 (2.30.3-0ubuntu1, 2.30.3-0ubuntu1.1), dpkg-dev (1.15.5.6ubuntu4, 1.15.5.6ubuntu4.1), nautilus-dbg (2.30.1-0ubuntu1, 2.30.1-0ubuntu1.1), libservlet2.5-java (6.0.24-2ubuntu1.1, 6.0.24-2ubuntu1.2), gnome-panel (2.30.2-0ubuntu0.1, 2.30.2-0ubuntu0.2), gwibber (2.30.0.1-0ubuntu3, 2.30.1-0ubuntu1), libnautilus-extension1 (2.30.1-0ubuntu1, 2.30.1-0ubuntu1.1), libvte-common (0.23.5-0ubuntu1, 0.23.5-0ubuntu1.1), gnome-panel-data (2.30.2-0ubuntu0.1, 2.30.2-0ubuntu0.2), empathy-common (2.30.1.1-0ubuntu1, 2.30.2-0ubuntu1)
End-Date: 2010-07-16  20:47:47

Start-Date: 2010-07-20  11:21:24
Upgrade: ubuntuone-client (1.2.1-0ubuntu3, 1.2.2-0ubuntu2), hunspell-en-ca (3.2.0-3ubuntu3, 3.2.0-3ubuntu3.1), libnotify1 (0.4.5-1ubuntu3, 0.4.5-1ubuntu4), ubuntuone-client-gnome (1.2.1-0ubuntu3, 1.2.2-0ubuntu2), libfreetype6-dev (2.3.11-1ubuntu2, 2.3.11-1ubuntu2.1), openoffice.org-thesaurus-en-us (3.2.0-3ubuntu3, 3.2.0-3ubuntu3.1), libfreetype6 (2.3.11-1ubuntu2, 2.3.11-1ubuntu2.1), myspell-en-gb (3.2.0-3ubuntu3, 3.2.0-3ubuntu3.1), myspell-en-za (3.2.0-3ubuntu3, 3.2.0-3ubuntu3.1), python-ubuntuone-client (1.2.1-0ubuntu3, 1.2.2-0ubuntu2)
End-Date: 2010-07-20  11:24:12

None of that seems related to networking, but who knows.

I wrote a script that pings the local gateway on a regular basis. When a ping doesn't return, that indicates the period for which I am experiencing no available network. I can't ping any ports, internet doesn't work, etc.
Curiously, when pings resume working, all of my ssh connections repair themselves and let me continue working.

For very long runs (as much as 30 min), the outages seem to be 160s apart. For other times, it's more erratic. The outages last over a minute, so I have plenty of time to run something to debug it.

Any advice on how to diagnose the issue?



Here's a sample of my script's output, to illustrate both the 160s periods and the erratic bits.
[SIZE="1"]05:11:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.469 ms
05:11:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.467 ms
05:11:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.448 ms
05:11:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.471 ms
05:11:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.449 ms
05:12:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.491 ms
05:12:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=1.03 ms
05:12:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.438 ms
05:12:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.437 ms
05:12:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.459 ms
05:12:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.442 ms
05:13:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.604 ms
05:13:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=1.38 ms
05:13:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.891 ms
05:13:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.500 ms
05:13:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.632 ms
05:13:59 PM |
05:14:14 PM |
05:14:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.466 ms
05:14:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.523 ms
05:14:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.422 ms
05:14:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.483 ms
05:15:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.490 ms
05:15:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.412 ms
05:15:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.459 ms
05:15:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.426 ms
05:15:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.538 ms
05:15:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.800 ms
05:16:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.474 ms
05:16:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.496 ms
05:16:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.471 ms
05:16:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.487 ms
05:16:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.489 ms
05:16:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.490 ms
05:17:09 PM |
05:17:24 PM |
05:17:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.467 ms
05:17:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=1.08 ms
05:17:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=1.05 ms
05:18:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=1.50 ms
05:18:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.497 ms
05:18:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.486 ms
05:18:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.424 ms
05:18:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.498 ms
05:18:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.467 ms
05:19:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.487 ms
05:19:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.947 ms
05:19:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.482 ms
05:19:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.478 ms
05:19:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.466 ms
05:19:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.465 ms
05:20:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.449 ms
05:20:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.447 ms
05:20:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.490 ms
05:20:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.474 ms
05:20:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.478 ms
05:20:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.408 ms
05:21:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.455 ms
05:21:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.457 ms
05:21:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.417 ms
05:21:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.482 ms
05:21:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=1.44 ms
05:21:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.449 ms
05:22:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.452 ms
05:22:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.464 ms
05:22:29 PM |
05:22:44 PM |
05:22:59 PM |
05:23:14 PM |
05:23:29 PM |
05:23:44 PM |
05:23:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.492 ms
05:24:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.466 ms
05:24:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.478 ms
05:24:29 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.475 ms
05:24:39 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.407 ms
05:24:49 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.496 ms
05:24:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.428 ms
05:25:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.457 ms
05:25:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.456 ms
05:25:29 PM |
05:25:44 PM |
05:25:59 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.466 ms
05:26:09 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.488 ms
05:26:19 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.513 ms
05:26:30 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.444 ms
05:26:40 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.464 ms
05:26:50 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.456 ms
05:27:00 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.508 ms
05:27:10 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.752 ms
05:27:20 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=1.34 ms
05:27:30 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.474 ms
05:27:40 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.873 ms
05:27:50 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.487 ms
05:28:00 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=1.10 ms
05:28:10 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.481 ms
05:28:20 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.417 ms
05:28:30 PM | 64 bytes from 10.0.0.2: icmp_seq=1 ttl=255 time=0.497 ms
05:28:40 PM |
05:28:55 PM |
05:29:10 PM |
[/SIZE]

---

