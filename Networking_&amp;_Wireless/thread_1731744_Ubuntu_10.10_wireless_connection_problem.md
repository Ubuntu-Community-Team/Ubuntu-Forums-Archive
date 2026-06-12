---
title: "Ubuntu 10.10 wireless connection problem"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by Smokje on 2011-04-17
Hello..

i couldnt connect the network via wless at my home but it done at work office. and also there is no problem in WIN XP. Why the connection is OK at office and why not at home.? 

In /var/log/messages

kernel: [  816.969577] cfg80211: Calling CRDA to update world regulatory domain
kernel: [  816.969636] cfg80211: Calling CRDA for country: TR
kernel: [  816.992161] cfg80211: Regulatory domain changed to country: TR
kernel: [  816.992170]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
kernel: [  816.992180]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
kernel: [  816.992188]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (N/A, 2000 mBm)
kernel: [  816.992195]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 2000 mBm)

In iw reg get

country TR:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 20), (N/A, 20)
	(5250 - 5330 @ 20), (N/A, 20), DFS

what should i do, have any idea .?
Thanks..

---

### Post by mrcollinz on 2011-04-17
To better assist you I need some clarification on the issue, so you're saying that you're running 10.10 and you can get wifi to work at you're office and not at home?. Well first off when you're at home does the wireless adapter see other networks in the area?. In addition to this are there other devices in you're home that are successfully connected to you're router?. First, troubleshoot it as a hardware issue first because the wifi drivers (in ubuntu) is indeed working with another router and connects fine. Could be a possible incompatibility issue with you're home router (Check to make sure the router is broadcasting in /B/G/N not just N.

Other then that try power cycling you're router for 30secs, and check to see if ubuntu picks up you're SSID and see if you can connect. Oh and for the sake of testing try removing wireless security and see if you can connect, ONLY if all else fails.

Good luck!

---

### Post by Smokje on 2011-04-17
Hey mrcollinz;
thank you for your reply.
my adapter see all other networks in the area also see mine, on wless network list when i click for connect, it says me nothing just rolling infinitely.

im noob one for using Ubuntu ;)

---

### Post by mrcollinz on 2011-04-17
Did you change you're wireless security settings recently?, change from WEP to WPA etc?. I've seen issues like this before when I've made changes to my wireless settings and my computer keeps trying to connect to the network automatically using the previous settings and not prompting me to enter in the new security password etc. Try accessing you're router and changing you're SSID (wireless network name) and change the wireless security type to WPA personal. After all this is done reboot you're modem and you're router. Then restart ubuntu and find you're network enter you're security info and see if you can connect.

Again, is there any other computers in the use surfing using wifi right now?..trying to figure out if its ubuntu specifically or the router is having network issues.

Hope this helps!

---

### Post by bill_meilahn on 2011-04-17
I've got the same problem... just installed 10.10 and cannot connect to wireless.  Wireless is fine, per se... I have 4 other devices still connected, including this one.  Moreover, the laptop (an old dell x200, loaded with xp 3 until about an hour ago) was talking just fine to the same router under windows.  

I use a WEP 128 security.

What am I missing?

---

### Post by Smokje on 2011-04-18
i did everything but problem is still going on..
Its on WPA&WPA2 Personal.
all other computers included my computer's XP are surfing with wifi but Ubuntu.
:confused::confused::confused:

---

### Post by conualfy on 2011-05-01
It's been a while since the upgrade to 11.4 and it's not so nice to know  that something basic as a wifi connection that should just work out of  the box it's not actually working.
Reconnecting the wifi connection makes the internet work again, but it's  just a matter of minutes or seconds before I have to do this operation  again.

I have changed the router encryption to none (I've lowered security by  using only the MAC filter) and there is no difference, it's showing that  I'm connected to the router, but the internet is not working at all.

I've just tried disabling the IPv6 and the bug is still here.

I tested the connection with this script:
[http://sourceforge.net/projects/wirelessscript/files/](http://sourceforge.net/projects/wirelessscript/files/)
The results for both the working wifi and the one not working (but showed by the network manager as connected) here:
[http://goo.gl/hyrZg](http://goo.gl/hyrZg) (reconnected, wifi working)
[http://goo.gl/sdgwL](http://goo.gl/sdgwL) (wifi not working)

I would allow some good willing specialist to debug this on my computer  or any other way he/she suggests. If there is anyone interested in  fixing this nasty bug, please send me an email on florin [at] drumliber  [dot] ro


PS: I'm using a laptop (Toshiba Satellite C650 with Atheros wifi card and wifi under Windows 7 work perfectly.

---

