---
title: "Losing DNS on resume from standby"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by thymox on 2012-08-21
Ubuntu 12.04 running on an Acer Aspire One Happy (PAV70)

I almost exclusively use this netbook with WiFi - it does have an Ethernet port but I don't use it.

So, the problem is this:
1. Use netbook in the Internet using WiFi.
2. Close lid and put netbook into suspend-to-RAM (standby/sleep).
3. Open lid (after any period of time) - netbook resumes from S2R.
4. Network Manager connects to WiFi.
5. For about 10 seconds, you're good to go. After that, resolv.conf becomes empty.

At this point things get really annoying.

Restarting the Network Manager service re-connects to the WiFi, then drops the DNS settings as per steps 4 & 5.

Restarting the whole networking service stack does the same.

Manually issuing "sudo dhclient wlan0" seems to just sit there doing absolutely nothing. Manually issuing "sudo ifconfig wlan0 down;sudo dhclient wlan0" brings us back to step 4 & 5.

Manually editing resolv.conf works... for about 10 seconds, and then it gets overwritten with a blank one.

The only resolution I have found that actually works is to reboot the netbook... which kinda negates the whole point of putting it into suspend-to-RAM in the first place.

Please note that I do NOT want to make resolv.conf immutable or any other sledgehammer-to-crack-a-nut resolutions. I would like to find out what is causing the problem so it can be resolved.

Any advice and guidance would be greatly appreciated.

Grant.

---

