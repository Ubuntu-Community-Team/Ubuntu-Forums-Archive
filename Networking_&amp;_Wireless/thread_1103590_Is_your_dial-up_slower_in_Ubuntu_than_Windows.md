---
title: "Is your dial-up slower in Ubuntu than Windows?"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by Bartender on 2009-03-22
I have a Dell Precision 470 running Windows XP/Ubuntu 8.10.  I'm using a USR serial external modem for dial-up, so the hardware is identical under either OS.
Fry's.com is our ISP.
The connection is always slower in Ubuntu than XP.  It feels slower, and various online speed tests verify.  If XP gets 40 kbps, Ubuntu will often be 30 to 32 kbps.

Anyone else have any observations on this?  I'm wondering if it's the ISP, or the way Ubuntu communicates with the modem, or what.  AFAIK, the USR external serials are supposed to be just about the most reliable way of connecting via dial-up.

---

### Post by _duncan_ on 2009-03-28
It probably has to do with configuration settings of the dialer program you're using in Ubuntu. Specifically, the init strings.

My experience with USR external serial modems is that the newer models will work with just the default init strings supplied by the Ubuntu dialer programs. However, some older models require tweaking the init strings to work satisfactorily. I can't give you the exact model numbers coz I don't have these modems anymore.

Anyway, what you can do is boot into XP and search for the modemlogs file. This will give you the exact init strings xp uses to connect. Jot them down and boot back to Ubuntu. See if you can replicate these init strings into your dialer app.

Just make sure to take note of the default init strings ubuntu uses so you can revert back if things don't work out.

-----------------

BTW, deducing the init strings from the XP modemlogs file is not an easy task. This will probably take a bit of trial-and-error on your part.

---

### Post by Bartender on 2009-04-02
Hi, duncan!
OK, thanks for the pointers.  I've heard of the init strings but never really figured out what they are or how to mess with them.

---

