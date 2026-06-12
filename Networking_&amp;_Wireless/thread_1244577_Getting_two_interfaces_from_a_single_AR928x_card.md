---
title: "Getting two interfaces from a single AR928x card"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by kfries6 on 2009-08-19
Can somebody point me in the right direction on this?

I want to see if I can use a single AR9280 wifi card and get two interfaces out of it: one in station mode; one in host mode.

Maybe the issue is my thinking process, but here is where I see the issue:

   - System fires up, and HAL sees the hard, passes identification to UDEV

   - UDEV identifies the card and the appropriate drivers
      - Loads driver
      - Sets up interface

   - Networking is configured based upon devices identified by UDEV

How can I get Ubuntu to see a card with 2xRx/2xTx to create two devices, and therefore have two configurable interfaces?

Thx in advance

---

