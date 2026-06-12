---
title: "how to get resurect wireless that worked out-of-the-box"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by alex sun on 2009-09-06
Hello!

I am rather new to Ubuntu, so sorry for this question.
I tried to read the manual and scan through the forum, but it didn't help.
I have two wireless networks available. One is fast, another is slow.
Slow one is a simple pass-protected and it worked until yesterday out-of-the-box.
Fast one requires PEAP(EAP-GTC), so I tried to connect to it using the standard NetworkManager.
Somehow it got crashed so I had to force-quit it.
Then I tried to connect to the fast wireless using wpa_supplicant
So I created /etc/wpa_supplicant.conf as suggested in wpa_supplicant man, configured it as described here: [http://svana.org/sjh/diary/2009/07/08](http://svana.org/sjh/diary/2009/07/08) (these details are exactly for my fast network), and ran:
wpa_supplicant -iwlan1 -c/etc/wpa_supplicant.conf
I must mention that it was reported by many not to work in general, but also mentioned by one guy to work successfully with 2.6.30 with his particular hardware.
I have a different wireless card and I use 2.6.28, so it didn't work for me, which doesn't matter too much.
The downside is that the slow wireless is not working any longer, so I don't have any Internet at home any-more.
Reboot doesn't help.
Could you please help me to return it to life?
Again, I made only 2 things to make it dead:
1) force quit the NetworkManager
2) run wpa_supplicant once
Many thanks in advance!

---

### Post by uylug on 2009-09-06
> **alex sun said:**
> Hello!

I am rather new to Ubuntu, so sorry for this question.
I tried to read the manual and scan through the forum, but it didn't help.
I have two wireless networks available. One is fast, another is slow.
Slow one is a simple pass-protected and it worked until yesterday out-of-the-box.
Fast one requires PEAP(EAP-GTC), so I tried to connect to it using the standard NetworkManager.
Somehow it got crashed so I had to force-quit it.
Then I tried to connect to the fast wireless using wpa_supplicant
So I created /etc/wpa_supplicant.conf as suggested in wpa_supplicant man, configured it as described here: [http://svana.org/sjh/diary/2009/07/08](http://svana.org/sjh/diary/2009/07/08) (these details are exactly for my fast network), and ran:
wpa_supplicant -iwlan1 -c/etc/wpa_supplicant.conf
I must mention that it was reported by many not to work in general, but also mentioned by one guy to work successfully with 2.6.30 with his particular hardware.
I have a different wireless card and I use 2.6.28, so it didn't work for me, which doesn't matter too much.
The downside is that the slow wireless is not working any longer, so I don't have any Internet at home any-more.
Reboot doesn't help.
Could you please help me to return it to life?
Again, I made only 2 things to make it dead:
1) force quit the NetworkManager
2) run wpa_supplicant once
Many thanks in advance!

If it worked "out-of-the-box" then, why not try booting up a live cd? If everythings allright, then it should still work fine.

Have you installed any programs lately, run upgrades or something?

---

### Post by alex sun on 2009-09-07
Thanks for the reply.

I didn't update or install anything during the last 3 days except epiphany, but I installed it before problems with the network started rising. I browsed the web for several hours and reconnected once with epiphany.

Unfortunately, I cannot load from Live CD, because my computer probably won't start again if i poweroff or reboot (I have hardware problems with the North Bridge). Yesterday I could reboot once during the last 2 month, but than had a very hard time trying to run CPU again. Perhaps it could be connected with wireless as well. But what confuses me is that I can see all wireless networks in Network Manager and can try to connect them. Fast one even asks to configure stuff, slow one doesn't ask anything, just drops before connecting. It means that at least to some extend my wireless works.

So it could be a hardware problem, but could someone help me to check it? Because if it's just a wrong setting somewhere arising from running wpa_supplicant manually or sending killall to Network Manager, it'll be pretty sad not to correct it.

---

