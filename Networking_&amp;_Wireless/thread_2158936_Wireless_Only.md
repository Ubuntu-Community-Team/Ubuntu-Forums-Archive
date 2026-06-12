---
title: "Wireless Only"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by knubles on 2013-07-01
How does one get wirelees working when you do not have a wired system ?
Cheers
Knubles

I have solved the problem.
Thank you all.

---

### Post by grahammechanical on 2013-07-01
This document will help you collect the information needed to help others help you.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

It is best if this post was transferred to the section on Networking & Wireless. There are people on the section who have special experience in the subject of networking.

Regards.

---

### Post by knubles on 2013-07-02
I have found by experiment the trial of Ubuntu does work.
When installed it stops working.
Cheers
knubles

---

### Post by naga2raja on 2013-07-03
@Knubles: Can you give more details on your question? Are you using somekind of tablet that don't have a ethernet port or you have wired connection working and wireless devices are not enabled?

---

### Post by varunendra on 2013-07-03
> **knubles said:**
> I have found by experiment the trial of Ubuntu does work.
When installed it stops working.

Then most probably it is a broadcom chip that works with the wl driver. But it's better to make sure than guessing.

Please boot from the CD/USB (where wireless works) > go to trial mode > open a terminal (ctrl+alt+T) > run the following commands in it -
```
lspci -nnk | grep -iA2 net
lsusb
```

Post back outputs of these commands here so we can see what chip you are using and accordingly which driver you need.

---

### Post by Irihapeti on 2013-07-03
*Thread moved to **Networking & Wireless**.*

---

