---
title: "Low signal woes"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by Vunutus on 2009-02-14
I'm attempting to improve the quality of my home wireless network. First off, here's my network setup as of yesterday:

[LIST]
[*]DSL connection coming in through a modem and wired/wireless router all-in-one thing
[*]One desktop computer wired directly into above router
[*]One desktop computer far away from the router connecting wirelessly
[*]Misc devices (laptops, game consoles, etc) connecting wirelessly 
[/LIST]

Seems straightforward, the only problem was that the computer far away from the router had some real signal issues. This isn't surprising, it's separated from the router by a floor and a few walls. It could connect, but at a slower speed than everything else and with frequent interrupts.

I happened to have an old linksys wireless router sitting around not in use. I thought the obvious solution here was to turn it into a repeater. I downloaded the DD-WRT third party firmware (it it excellent I must say) and set it up midway between my main router and the computer with bad signal. The repeating function seems to work fine (traceroutes show it correctly going from repeater to main router and on to the internet), but the situation with the bad signal computer has not seemed to improve much. 

When I log on to the repeater's administration page, I can see that it is getting only 28% signal quality to the desktop in question. It is only about 45 feet or so away with almost clear line-of-sight to the repeater. The repeater itself shows 48% signal quality to the main router.

The 48% reading seems about right to me just guesstimating from how far it is from the router, but 28% seems incredibly low for a computer so close to it.

I'm thinking this is the cause of my problems. What could be causing such a low signal? I don't think there are any interfering devices around either of the nodes.

---

### Post by cariboo on 2009-02-14
A cordless phone in the area can cause interference, You can also get add on antennas that help a lot. I use a SMC Barricade as a wireless access point and I've added a +16db antenna to it and the sigan; strength seems to be quite a bit higher, this is only subjective, as I really haven't bothered to check it.

Jim

---

### Post by afeasfaerw23231233 on 2009-03-11
Bump.
I have the same very weak signal isuue on my realtek 8187 too. 
I am using ndiswrapper win 98 driver now and the wireless siganl will be broken if distance from the router to the notebook more than 3 metres, making the wlan completely useless. 

Bump.

---

