---
title: "automatic wifi conection"
date: 2010-05-06
forum: Mythbuntu
---

### Post by itlarson on 2010-05-06
I am planing to use wifi for the internet connection on a new mythbox.  All I know about wifi is how to click on the taskbar widget to connect.  How can I set it up to connect automatically at boot?  I would also like to know how I can control it without the widget, in case I decide to work without a task bar.

---

### Post by funkydan2 on 2010-05-06
(I'm not at my Linux box at the moment, so this is from memory).

In NetworkManager, when you go into the settings there is a check box called 'Connect Automatically' - make sure this is checked.

However, I have found a problem with NetworkManager in the past when, after the wireless connection was lost, it didn't reconnect automatically. So I've changed to using wicd (install it through synaptic) instead of NM, and it works just fine.

---

### Post by shidiksaragih on 2010-05-06
just setting DHCP

---

