---
title: "NetworkManager automatically reconnects to my wireless network"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by skotos on 2009-04-30
At every reboot / user login, Network Manager automatically reconnects my notebook to my wireless network and this is not my favourite default option. 

Unfortunately I did not find a way in the Gnome Network Manager applet to  permanently unmark the *Enable Wireless* flag. How can this be achieved?
The *Connect automatically* flag is not set for my only one configured wireless lan.

Furthermore, I have noticed that Network Manager is currently able to automatically re-enable my hardware switched off wireless nic. Any idea on how this hardware switch might be treated/configured in order to have Network Manager act accordingly to its hardware state?

FYI: My notebook is an Acer Aspire 9815WKMi (20" LCD).

---

### Post by skotos on 2009-05-16
As of today the problem has been partially solved probably due to an update: there is no more wifi automatic reconnection (no change in any automatic login flag has been performed).

This can be sufficiently secure, though I have not still found a way to automatically avoid to start the wifi nic.

---

### Post by tp42 on 2009-05-25
Hi Skotos,
Sorry for not providing a solution... but rather sharing a similar problem...
I work on an Lenovo X301 notebook. And I am faced with a rather similar situation:
I switch off the WLAN-access with the Function Key (F5) or within the Network-Manager Applet and both works perfect. But when I restart my X301, it connects automatically to LAN *and* WLAN interface. I am really looking for an option to make the LAN interface active per default and to make the WLAN interface inactive per default.
Perhaps someone more experienced could provide us a hint?

---

### Post by skotos on 2009-11-10
Since many has come here looking for a solution, I am giving a very late feedback anyway: I have just upgraded to Karmic (9.10) and this is no more an issue.

The Gnome NetworkManager applet, in fact, has got this flag:

[LIST]
[*]Connect automatically
[/LIST]
and this definitely solves the problem. Still, I think it has been solved/added before, but I cannot check any more: all my Ubuntu network is proudly and simply running Karmic.

---

