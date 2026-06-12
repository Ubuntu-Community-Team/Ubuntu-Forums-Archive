---
title: "Do I need a voice modem to filter phone calls?"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by mrdek11 on 2009-09-28
Hi there! I run a server using ubuntu.

I've been receiving tons of phone calls from annoying telemarketers (such as the NRA), and I've tried all normal channels to get them to stop. I had planned to set up asterisk (or some other software) to automatically drop phone calls coming from specific numbers.
However, I recently learned that my specific Intel 537 voice modem would not work with linux.

I have a number of normal fax/data modems that work well with linux. Is there any way I can filter phone calls without purchasing a voice modem?

Thanks in advance,

Derek

---

### Post by sr_guy on 2009-09-30
Is your phone service sip based? Either way, I believe you'd have to receive your inbound calls through asterisk, and then user the blacklist feature. Easiest way to use the blacklist function is by using FreePBX. I like the option to be able to block by an entire area code, so if the telemarketer tries to use a different phone that has the same area code it will still be blocked. See my screenshot.

This version of asterisk is 1.4 and FreePBX 2.5.2.2 running on Ubuntu 8.10

---

