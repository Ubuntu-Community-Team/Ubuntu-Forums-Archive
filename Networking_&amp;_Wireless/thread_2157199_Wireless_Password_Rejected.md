---
title: "Wireless Password Rejected"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by AdrianThorn101 on 2013-06-24
I am using Lubuntu 13.04 and I am having an issue that has totally stumped me.  I am attempting to connect to a WPA2 encrypted wireless network but the password I enter keeps being rejected by NetworkManager. I KNOW this password is correct.  It is identical to the one I use for the same network on another machine, which can access it fine from either Ubuntu or Windows.  I doubt the issue is related to drivers, as the computer has no problem connecting to another WPA2 network.  I am running dd-wrt on the router my Lubuntu machine is trying to connect to and can find nothing to explain why the Lubuntu machine alone cannot connect.  Suggestions>

---

### Post by BazBear on 2013-06-24
I have the same exact problem. Neither of my Lubuntu installs will connect to my dd-wrt router (Linksys e1200 v2), I get the same bad password error on both. The Windows dual boot OSes on these machines connect without issue, and the Lubuntu boxes will connect to all the other routers (all stock firmware) I've tried them with. This has been a problem at least as far back as 12.04, including 12.10 and now 13.04, and it's done it with every flavor of Ubuntu I've tried (as well Mint). I've tried WPA2, WPA, WEP as well as trying Mixed mode, NG mixed, just G etc. I've been banging my head off the wall off and on for months trying to solve this, with the only benefit being I've learned a lot of terminal commands.

---

### Post by varunendra on 2013-06-25
Welcome to the forums Adrian!

Please follow the "Wireless Script" link in my signature and run the script as mentioned in the linked post. Run it when the connection attempt fails (so we can have relevant messages in the logs).

@ BazBear,

I'd suggest you do the same, and be ready to post (or direct me to) a thread of your own if your device/drivers and/or overall problem appear to be different than OP's.

---

### Post by BazBear on 2013-06-25
Thanks Varunendra. I'll resurrect the original thread on my problem, and post the results of the wireless script there.

ETA- My post is [here]("http://ubuntuforums.org/showthread.php?t=2130035").

---

### Post by tinkerpad on 2013-07-17
Hi,
I have this at times with some flavors of ubuntu - it seems to help to edit the connection and to set the ipv6 "method" setting from automatic to none.
Cheers!

---

