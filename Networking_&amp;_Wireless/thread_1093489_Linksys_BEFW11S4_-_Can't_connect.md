---
title: "Linksys BEFW11S4 - Can't connect"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by Griffin Bandida on 2009-03-11
Another linksys problem in the forum. I'm sorry if there is a solution in some post, it's just I've seen so many linksys threads and none seems to be related to my problem or understandable to me (well, I'm still a 'novice' in ubuntu).
As you can guess, I can't connect to my wireless router, the system keeps saying:

> Mar 11 19:41:02 Jabeca NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Mar 11 19:41:02 Jabeca NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Mar 11 19:41:02 Jabeca kernel: [  267.283788] wlan0: authenticate with AP 00:00:00:00:00:00
Mar 11 19:41:02 Jabeca kernel: [  267.285359] wlan0: authenticated
Mar 11 19:41:02 Jabeca kernel: [  267.285375] wlan0: associate with AP 00:00:00:00:00:00
Mar 11 19:41:02 Jabeca kernel: [  267.287278] wlan0: RX ReassocResp from 00:00:00:00:00:00 (capab=0x15 status=0 aid=12)
Mar 11 19:41:02 Jabeca kernel: [  267.287290] wlan0: associated
Mar 11 19:41:02 Jabeca kernel: [  267.292692] iwlagn: index 0 not used in uCode key table.
Mar 11 19:41:02 Jabeca NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Mar 11 19:41:07 Jabeca NetworkManager: <info>  wlan0: link timed out.

Ironically, I connect successfully to linksys when the router is down (but I obviously don't have any internet connection).
When I connect to the router with a ethernet cable I am able to get a connection.
If it's also important, my laptop is a Toshiba A200-1EK and I'm using Intrepid Ibex (I think my wireless card is a Intel, not sure about the model though).

Any suggestions or links to a useful post? :confused:
Thanks in advance

---

### Post by chili555 on 2009-03-11
Could it be the router?  [http://www.dslreports.com/forum/remark,7069184](http://www.dslreports.com/forum/remark,7069184)

---

### Post by Griffin Bandida on 2009-03-11
I don't know, it works fine in Windows Vista. In a previous Ubuntu version (I think it was 7 something) it would connect successfully sometimes, other times it would state this same error.
Maybe an option in the router...help? D:

---

