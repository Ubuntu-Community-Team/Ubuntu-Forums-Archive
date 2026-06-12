---
title: "WLAN seriously slow (Toshiba)"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by DjRedo on 2009-10-30
Hello all helpful souls

Its been years since I last ran Linux, but the release of Ubuntu 9.10 gave me a kick in the butt to install it on my oh-so-faithful Toshiba Laptop.

The install (own partion, side by side wth XP) went fine, and I was especially glad to get online with no problems. It seemed.

However, when I started downloading some of the programs I wanted, I came to realize that my WLAN is working at about 1/20 of the speed in Windows. I have fiber net, and can usually pull about 20Mbit/s on WLAN in XP. Now im down at a steady 900Kb or so. I have about 3-4Mbit out, which is kinda weird, but this is also about 20% of the usual speed. In all other terms the network seems to be running fine (no packet loss etc)

I have a Toshiba [Equium A100-299]("http://nordic.computers.toshiba-europe.com/innovation/jsp/productPage.do?LNG=18&service=ND&PRODUCT_ID=123506&PRODUCT_ID=123506") with a PA3489U-1MPC built-in WLAN card. The current driver is iwl3945 and the network is WEP encrypted (yeah I know its worthless).

Is this most likely a driver issue, or am I missing something here?

I'd hate to go back to Bill, but 900Kb is painfully slow and 5 hours of googling didnt find me any specific driver althouhg the WLAN card seems to be quite common in Toshiba laptops.

All help appreciated, thanx for lending your time!

---

### Post by efflandt on 2009-10-30
Have you done a speed test on a broadband speed test site (when nothing else on your LAN is using internet), or are you judging from something you are downloading (which may depend upon how busy the site is being downloaded from)?  Or are you confusing kilobits with kilobytes?

I have a Tosiba A105 which uses same inl3945 module in Ubutu 9.04 and it is currently getting 4.950 mbps in a DSL speed test, which is slower than its usual 5+, but not bad considering that another PC is currently downloading 9.10 updates (at a rather leasurely pace due to busy servers).

---

### Post by DjRedo on 2009-10-31
> **efflandt said:**
> Have you done a speed test on a broadband speed test site (when nothing else on your LAN is using internet), or are you judging from something you are downloading (which may depend upon how busy the site is being downloaded from)?  Or are you confusing kilobits with kilobytes?

I have a Tosiba A105 which uses same inl3945 module in Ubutu 9.04 and it is currently getting 4.950 mbps in a DSL speed test, which is slower than its usual 5+, but not bad considering that another PC is currently downloading 9.10 updates (at a rather leasurely pace due to busy servers).

Both.
The figures i gave is from a broadband test, and compared to the same test in XP.

Weirdly enough its all working fine now. I just got [COLOR=#000000]18 Mbit/s on the same test (with 23Mbit/s up). Still a bit weird with higher up than down but Im guessing it is because the test is a bit unreliable on higher speeds.
My DL speed was much lower, since you ask. 

Well, im thinking it might be my Router that had a hickup, I see no other explanation. I haven't even restarted the machine since I went to bed yesterday so there is absolutely nothing that has changed since then...

But thanks for caring :-)
[/COLOR]

---

