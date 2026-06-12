---
title: "Wireless not working only windows laptop can connect  via ethernet"
date: 2013-06-12
forum: Networking &amp; Wireless
---

### Post by MadMax2 on 2013-06-12
Hmmm I fired up my laptop but couldn't get it to connect. Funnily [not sure but ] my ssid had a 2 attached. I don't recall doing that.
I've tested cables and only my Windows laptop can connect (via ethernet) but my linux laptop and PC can't. I tried pinging the gateway and router but no luck.
Any ideas?
Thanks.

---

### Post by scbingham on 2013-06-13
Do you mean SSID or connection name?

If you click on the network icon in notification area, select edit connections & then wireless. You should see a list, select the one with a 2 & then edit. You will probably see the SSID is correct.
When I have tried setting different security options for the same SSID, the system adds a 1, a 2, etc to the connection name.

You then mentioned cables ie ethernet & also a pc, which will have nothing to do with an SSID.

Maybe you can clarify your problems & connection methods.

---

### Post by MadMax2 on 2013-06-13
I have a PC Ubuntu 12.10 and a laptop (Lubuntu) also a laptop running windows 7. This morning windows laptop wouldn't connect via wireless. I thought there must be a problem with the provider but apparently not (they said). I tried bypassing the router plugging the PC into the modem but couldn't connect. Ditto the lubuntu lap top. The windows laptop can connect to the modem by ethernet. I've tried a good cable on all three with the same result. The modem is giving a strong signal. I would have suspected the router but why can I not connect to the modem the PC and lubuntu laptops?

---

### Post by MadMax2 on 2013-06-13
not sure how to configure.

---

### Post by MadMax2 on 2013-06-13
Appeared to be caused by firing up the modem this morning. It was off at the wall and i may have switched it on/off while it was firing up (or something). Oddly though only my Windows 7 machine could use it.

---

### Post by scbingham on 2013-06-13
Ok, unplug the power from both the modem & router for a minute to allow them both to reset.
Power them back up & connect them together, wait a minute for your modem to settle down.

Using an thernet cable, connect Ubuntu pc to the router.

From a terminal try & ping the router's ip address (probably on a label underneath, mine is 192.168.0.1).
Does that work? If so, try to ping 8.8.8.8, does that work?

If that works, try using your browser to connect to a site.

---

### Post by MadMax2 on 2013-06-13
Yes it's fixed now. Last night I remembered some advice about holding the button down on the motorola modem *and* I unplugged it. I had done that to the router several times. I can't remember whether i had powered off the modem. I think what threw me was that the fact that i could connect on the windows laptop but not the linux machines?

---

