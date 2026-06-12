---
title: "Linksys WUSB54GS + WPA2 personal"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by electronjockey on 2009-10-30
Anyone have a Linksys WUSB54GS v2.1 configured to use WPA2 personal working under 9.10 [Karmic]? If so how? 
I've tried following steps in several threads, but still no joy. One suggests that I shouldn't need the ndiswrapper. "Out of the box" if I try to "connect to hidden network" (as I'm not broadcasting my SSID) I just get repeated authentication prompts until it gives up. If I "create new network" it appears to connect and then immediately crashes, which of course I can't send because I'm not connected. 
If I have to use ndiswrapper, I'd rather not, but if that's how it has to be I can certainly live with it. This is the show stopper right now preventing me from saying b' bye to Bill.
If someone has this working using an existing how-to please point me there.

---

### Post by electronjockey on 2009-11-02
Well after many configuration tests, turns out that the thing works, if I broadcast my AP broadcasts SSID. So I'm still digging for a solution without broadcasting SSID. I've found a few posts, but they all out of date. /etc/network/interfaces doesn't list wlan0 at all, so I'm at a loss as to how to configure wpa_supplicant. Any nudges would be appreciated.

---

