---
title: "iwconfig txpower settings"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by khonnsu on 2010-02-24
Hi all, 

I'm having some difficulty setting my txpower setting on my atheros wifi card. I am using ath_pci driver on ubuntu 8.1 64 bit.

I can set the txpower to whatever, 12dBm for example, it accepts the change but quickly reverts back to a default value of 8dBm. Power saving is off.

How can I make these changes permanent, or adjust the default value?

Thank you!

EDIT: Is this possibly a firmware bug?

---

### Post by khonnsu on 2010-02-24
this is hella annoying.

---

### Post by khonnsu on 2010-02-26
So, the temporary patch I've chosen goes something like this:

root@computer:~/pwd$ while true; do iwconfig ath0 txpower 12; sleep 30; done

I'm not sure what is causing the txpower to return to 8 all the time; it could be one of many modifications I've made to get this thinkpad x61s running on less than 12 watts...

I will try diagnosing this further later, would lsof give me any idea for what's touching this interface??

---

