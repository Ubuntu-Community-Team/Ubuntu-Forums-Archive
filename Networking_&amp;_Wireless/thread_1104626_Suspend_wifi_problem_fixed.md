---
title: "Suspend wifi problem fixed"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by hufemj on 2009-03-23
I had a problem in which wifi worked fine until my system went into SUSPEND. This was on a desktop with a Broadcom wireless card with Intrepid 8.10.

After coming out of SUSPEND, nothing would make the wireless work again. Rebooting didn't work either. REALLY FRUSTRATING. After much searching, I found a post that mentioned the iwconfig command. From this, first I saw that my ESSID was gone. The man pages show how to set that. Then I set the key the same way. For example:

sudo iwconfig wlan1 essid Valley
sudo iwconfig wlan1 key 4961727272

(where Valley is my hypothetical ESSID and 4961727272 is my hypothetical WEP key)

The network manager icon (overlapping monitors) still indicated no connection. Left-clicking on the icon showed everything grayed out, except for VPN, which I'm not using. But I tried to ping my router, and it worked! Then I tried my browser, and sure enough, I had access to the web.

Something is obviously messed up with the network manager. Don't know what it is. It all started with SUSPEND, which worked fine with the wired interface. But, at least I have a manual workaround.

---

