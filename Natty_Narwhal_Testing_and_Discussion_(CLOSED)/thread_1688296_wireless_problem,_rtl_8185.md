---
title: "wireless problem, rtl 8185"
date: 2011-02-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ronacc on 2011-02-15
wireless for me is getting worse , at the start of natty my wireless sometimes would not connect on boot up but could be made to connect by disabling wireless and then re-enabling , just disconnecting and reconnecting did not work only disabling and re-enabling . now with fully updated natty, wireless connects on boot up but then disconnects after a few minutes ~2>5 and then cannot be reconnected without reboot since the option to disable wireless has been removed from NM . This is not a problem with my card (rtl8185)or router since other installs (maverick , Suse and Sabayon )  do not exhibit this behavior . a live cd (natty daily amd64 of feb 7 ) does exhibit it .

---

### Post by dreamslides on 2011-04-26
It's interesting but I just upgraded to Natty and am experiencing the same issue :-/ exactly the same. It will only work if I delete the network and then enter the key again. It's rather strange. And it NEVER connects after a reboot so I must constantly delete the network and re-enter it. I'd like to mention mine is RTL2860 so clearly something is amiss :(

Update: I figured out what it was doing! I checked my key right? and for some reason it's placing a return character into the key in place of \ so it makes the key come out over 2 lines instead of 1. I've no idea why it does this because it's only for 1 of the \ characters not all of them. Basically this makes the key wrong when it tries to connect.

---

