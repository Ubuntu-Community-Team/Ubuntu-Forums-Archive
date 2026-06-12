---
title: "Challenge to everyone: wireless disappears randomly..."
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by Adamantus on 2009-03-24
Okay, I've had this problem since I installed Ubuntu about 5 months back. I'm running Ubuntu 8.04 on an HP dv5-1004nr with an Atheros 242x wireless card. As with all Atheros chipsets, I got it working by using madwifi, and it does work for the most part. But it stops working for periods of time and it's starting to get really annoying. Up to now, I have asked this question about 5 times at a couple forums and no one has been able to answer, and no one on Google who has had this problem has been able to fix it properly.

It seems to happen most often (95% of the time) when I start my computer without the ethernet cord plugged in. It also happens if it fails to connect to an access point for too long / too many times. When it does happen, no wireless networks appear and will never appear unless I restart (it usually takes two or three restarts for the wireless to reappear).

As of right now, in my /home folder, I have a .madwifi-hal-0.10.5.6-r3879-20081204 and a .madwifi-hal-0.10.5.6-r3933-20090127 folder, and I'm not sure which I'm using.

Could anyone please help? This has been the only consistent problem that I've had with Ubuntu.

---

### Post by Adamantus on 2009-03-28
Bump

It seems like other people have similar problems and that it may be that Atheros doesn't report the signal correctly. But no one seems to have a solution.

---

### Post by binbash on 2009-03-28
I used this method : [http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html)

It works ok at intrepid as long as you disabled bluetooth.

I am using jaunty at the moment and ar242x crap seems to be fixed.It works out of the box (at least for me).

---

