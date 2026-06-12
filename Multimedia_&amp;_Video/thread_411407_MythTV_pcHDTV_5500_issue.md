---
title: "MythTV pcHDTV 5500 issue"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by lionsnob on 2007-04-16
Hello all!

I can't seem to get MythTV to find any ATSC channels using my pcHDTV 5500 card.  I am running Feisty right now.

This is the error showing up on the command line when MythTV is doing the scanning, using the pcHDTV DTV capture card (w/V4L drivers) card type:
pcHDTV::GetSignal_v4l1(fd 10, input 1, v4l2): error(Invalid argument)

Interestingly enough, when I use the Analog V4L capture card card type MythTV can find the analog channels.  Also, when using dtvsignal the card is reporting strong signals on several channels.

Any suggestions?

---

### Post by lionsnob on 2007-04-17
Never mind... figured it out :oops:

---

### Post by majoridiot on 2007-04-18
what was the problem, in case someone else makes the same error?

---

### Post by Gina on 2007-04-18
I can't get MythTV working at all - get MySQL errors - but I'm working on it.  Using 8.08 Dapper ATM but upgrading to Feisty shortly.

---

### Post by majoridiot on 2007-04-18
> **Gina said:**
> I can't get MythTV working at all - get MySQL errors - but I'm working on it.  Using 8.08 Dapper ATM but upgrading to Feisty shortly.

you will LOVE the feisty packages, gina... you won't have any problems with the mysql password, etc.

be sure to follow the install guides: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

