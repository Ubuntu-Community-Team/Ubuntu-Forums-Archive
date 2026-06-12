---
title: "Wireless in 8.04 with Netgear WG311T"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by Ningen on 2008-12-23
Yes, another person with wireless issues. I can't get my computer to even see my wireless card, and last night when I was on 7.10 upgrading to 8.04, the wireless was working fine. I've spent the last hour looking through these forums trying to find something to help, but nothing has worked.

---

### Post by pytheas22 on 2008-12-23
Please try using the script in [this thread]("http://www.google.com/search?q=ubuntu+madwifi+installation+script&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a") to install madwifi drivers--as I recall, the WG311T should have an Atheros chipset and this should do the trick on 8.04 (FYI: on 8.10 this card should work out-of-the-box).

If after running that script without errors and rebooting you still don't have wireless, please post the output of these commands:
```

uname -m
lspci -nn
lshw -C Network
sudo iwlist scan
dmesg | grep -e ath -e wlan
```

---

### Post by Ningen on 2008-12-23
When I try running the make command to install madwifi, it gives me Error 2, and when I try the make install command, it gives me Error 1. Help?

Or could you explain how I could update it to 8.10 without that computer having internet access, that would probably be a lot easier to do and much less frustrating.

---

### Post by pytheas22 on 2008-12-23
If you download the [alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") for 8.10 (not the regular CD), I believe there's an upgrade option available.

If that doesn't work or you prefer to stick with 8.04, I can give instructions for installing the driver offline.  Please let me know.  It would also be good to see the output of 'lspci -nn' just to verify that you indeed have an Atheros wireless card.

---

### Post by Ningen on 2008-12-23
I remember from before that it is an Atheros card. I just didn't know ahead of time that it wouldn't work on 8.04. I just finished downloading and burning the 8.10 Live CD, so I'm going to go try that now. Thanks for your help.

---

