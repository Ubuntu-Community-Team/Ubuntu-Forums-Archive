---
title: "Is there a way to get Wireshark working if you use ndsiwrapper?"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by OldNewb on 2009-01-14
I have just installed Wireshark, when I tried to select a device to capture there were none listed.

I am using ndsiwrapper to run my wireless network drivers.

Any help would be appreciated.

---

### Post by Ayuthia on 2009-01-14
You might try this from the Terminal:
```
gksu wireshark
```I think that it still needs to be run with admin privileges.

---

### Post by ASchweitzer on 2009-01-14
From my experience, if you're trying to raw-capture packets, you'll need to switch your card into *monitor mode*, which ndiswrapper can't do.

What are you capturing packets for? WEP cracking? If so, I can maybe be of help.

---

