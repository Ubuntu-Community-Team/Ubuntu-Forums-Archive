---
title: "New router, Ubuntu simply refuses to connect"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by Rhapsody on 2010-02-07
I've got an Ubuntu PC here that only connects to the internet through Wi-Fi (the position makes a wired connection ludicrously impractical) and it worked fine for a while. But then the wireless router we were using died, and had to be replaced with a new one.

Ubuntu immediately started acting weird. Despite the new router using the same encryption protocol (WEP, I'll try WPA if I can make it work at all later) and the same encryption key, Ubuntu doesn't want to connect to it.

If I try setting it up to automatically connect, it just doesn't work. As far as I can tell, Ubuntu doesn't even *attempt* to establish a connection.

If I select Create a New Wireless Network and enter the same settings as before, Ubuntu connects to the router, but says the connection strength is 0% and no sites are accessible. If I disconnect, the same router appears on the list of available routers, at 80%+ connection strength.

If I just click on that router, Ubuntu asks for the WPA/WPA2 Personal encryption key, not giving me an option for WEP (I've only specified a WEP key on the router), so I can't connect.

Finally, up until recently, the only way to connect was to select Connect to Hidden Wireless Network, enter the same settings as I did for automatic or new wireless network, and then it connected.

However, Ubuntu has now stopped accepting that. If I try, the wireless networking icon changes to indicate that it's connecting, I get one green light, two green lights, then it asks for the encryption key again (this time giving me an option for WEP) but never connects no matter how many times I enter it.

The connection strength is obviously more than strong enough, and my Wii is connected wirelessly using exactly the same encryption key (I get notifications from Nintendo, so it's a working connection), so the router is definitely functioning correctly. The problem also started at *exactly* the same time as I switched routers, so I doubt the networking card on the PC in question is at fault.

I'm at a loss as to why Ubuntu has suddenly decided it won't connect, but I'm seriously considering switching distros, as this PC is all but useless without wireless internet. I'm coming here first in the hopes that someone can find a solution, because I do like other things about Ubuntu, but this situation is completely intolerable.

---

### Post by llawwehttam on 2010-02-07
Right click on your network symbol, go to 'edit connections'.

Now click on wireless, press edit  go to wireless security and change the security to WEP.

Hope that helps.

---

### Post by Rhapsody on 2010-02-07
> **llawwehttam said:**
> Right click on your network symbol, go to 'edit connections'.

Now click on wireless, press edit  go to wireless security and change the security to WEP.

Hope that helps.
It doesn't. I specify WEP numerous times, but Ubuntu doesn't seem to want to listen. I create a connection, and specify WEP. Then I click on my router's name in the list Ubuntu gives me, and Ubuntu asks for the WPA key. I go into Edit Connections after this, and find that Ubuntu has created a new connection, all by itself, with WPA/WPA2 Personal as the encryption system selected.

---

### Post by lz1dsb on 2010-02-07
Hi, 
I'm facing a similar situation with my Dell Studio laptop, and I'm digging into it right now. In my case I'm using WPA though. Did you try reconfiguring your router with WPA? Was there any difference? 

Regards,
Boyan

---

### Post by Rhapsody on 2010-02-07
> **lz1dsb said:**
> I'm facing a similar situation with my Dell Studio laptop, and I'm digging into it right now. In my case I'm using WPA though. Did you try reconfiguring your router with WPA? Was there any difference? 
I'm somewhat reluctant to, since that would mean resetting the router and WPA didn't work at all the last time I tried. It was suggested that I may be missing the wpasupplicant package. If so, I'll have to download the correct package here, then sneakernet it to the other PC to test.

Worth a try anyway though.

Edit: WPA didn't work at all (not even with my Wii, so I suspect the router is at fault) but changing the router from "WPA or WEP security" to "WEP security only" finally broke Ubuntu's obsession with WPA, and it connected. That's solved my problem, so thanks for the suggestions everyone.

---

### Post by lz1dsb on 2010-02-08
Glad to hear that. I was still not able to localize my problem, so I'm still troubleshooting. You now mark this thread as Solved.

Regards,
Boyan

---

