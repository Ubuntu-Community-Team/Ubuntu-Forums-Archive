---
title: "Atheros AR242x, can see networks, WICD hangs on &quot;Validating Authetication&quot;"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by slickhare on 2008-12-17
So I have a Toshiba Satellite U305, which has an Atheros AR242x for wireless. After tons of troubleshooting, I finally got WICD to detect my network. When I try and connect it hangs on the "validating authentication" phase and then just fails. I'm sure my password is correct. What am I doing wrong?

---

### Post by slickhare on 2008-12-18
bump

---

### Post by K3N8 on 2008-12-18
Hi,

I installed my driver with:```
apt-get install linux-backports-modules-intrepid-generic
```.

It will install a different driver for your wireless called 5xxx....... Just activate it in the hardware section, restart and you're off.

Gr. Alexander

---

### Post by slickhare on 2008-12-18
> **K3N8 said:**
> Hi,

I installed my driver with:```
apt-get install linux-backports-modules-intrepid-generic
```.

It will install a different driver for your wireless called 5xxx....... Just activate it in the hardware section, restart and you're off.

Gr. Alexander

Thank you for the suggestion. I already did that though, I have that driver activated, but I still get this result.

---

### Post by slickhare on 2008-12-18
bump

---

### Post by IQRules on 2008-12-18
Do you get "$ iwlist scan" and can detech available hot spots?
And from Windows, can you connect to internet?

---

### Post by slickhare on 2008-12-19
> **IQRules said:**
> Do you get "$ iwlist scan" and can detech available hot spots?
And from Windows, can you connect to internet?

It works swimmingly through Windows Vista, i'll try that script and update, thank you for the reply.

---

### Post by K3N8 on 2008-12-19
> **slickhare said:**
> Thank you for the suggestion. I already did that though, I have that driver activated, but I still get this result.Did you de-activate the old one? Another thing is that teh recent update broke my wireless. When I removed the linux-backports-modules-intrepid-generic (including --purge), it worked again?!

---

### Post by remali on 2009-03-03
I have an asus x51rl laptop (Hardy 8.04) with the same wireless card and the exact same problem. 

At the beginning I had the problem that the card would not detect any networks, and so I tried everything --> madwifi, ndiswrapper, compat and finally it did work and it detected networks.
But when I click connect WICD hangs on "Validating Authetication" :confused::confused:

What should I do??? Please help!!! I've been searching for 3 days in a row ](*,)](*,)](*,)

PS. In "Hardware drivers", the device driver "Support for 5xxx series of Atheros 802.11 wireless LAN cards" is enabled

---

### Post by VotaVader on 2009-06-06
I'm having the same problem now. Wicd worked fine on my new Atheros 5008 with ndiswrapper for about a week, and then I started getting this problem that it gets stuck on "Validating Authentication". I've tried using other options besides wext in preferences, but they fail almost immediately to connect. The only one that has worked is wext, and now it has this problem. Has anyone figured out how to fix it yet??
Any help would be greatly appreciated.

Edit: It's working fine in Windows Vista.

---

