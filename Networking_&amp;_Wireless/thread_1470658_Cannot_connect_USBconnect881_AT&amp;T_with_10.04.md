---
title: "Cannot connect USBconnect881 AT&amp;T with 10.04"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by cigtoxdoc on 2010-05-03
I haven't been able to use my USBConnect881 since I upgraded from 8.10 to 9.xx.  I looks like it is trying to work with 10.04, but network manager will not save AT&T password and a window pops up saying that I need to enter a password to get to AT&T.

Under 8.10, I used a generic keyring password to get around this problem.  One PC did not even require it.

When I try to set keyring, I get error message that keyring daemon won't connect.

Please send help.

John

---

### Post by cigtoxdoc on 2010-05-03
Okay, this was just as simple as moving the USBconnect881 from USB port on back of PC to the one on the front.  All the popup boxes asking for a password for Sierra Wireless to connect to AT&T were someone's bad code.

DIAL: *99#
USER: [email]WAP@cingulargprs.com[/email]
PASSWORD: leave blank

APN: WAP.CINGULAR

John

---

### Post by cigtoxdoc on 2010-05-03
I just upgraded another PC to 10.04.  After shutting down the PC, I put the USBconnect881 in one of the front panel USB ports.  I started PC, logged-in, answer the dialogue questions (which AT&T plan) and the card started transmitting on its own.

John

---

