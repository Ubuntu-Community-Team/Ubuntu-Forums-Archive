---
title: "Need a Wireless N USB Dongle that just works!!!"
date: 2009-06-23
forum: Mythbuntu
---

### Post by t_hutch on 2009-06-23
I got the green light from my wife to build a small (mini-ITX) frontend for my son's playroom. I'd like to avoid running wires, so I want to use wireless N. The case I have doesn't allow for a PCI card, so USB would be the way to go. Does anyone have a suggestion for a USB wireless N adapter that works out of the box or at least is a quick download away from working?

Thanks!

---

### Post by db260179 on 2009-06-23
[http://www.amazon.co.uk/Belkin-WIRELESS-BUNDLE-F5D8053-F5D8633-4A/dp/B0012MUSN4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1245784762&sr=8-2](http://www.amazon.co.uk/Belkin-WIRELESS-BUNDLE-F5D8053-F5D8633-4A/dp/B0012MUSN4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1245784762&sr=8-2)

or just adapter

[http://www.amazon.co.uk/Belkin-N-Wireless-USB-Adapter/dp/B001HO3ZTQ/ref=dp_cp_ob_ce_title_1?ie=UTF8&qid=1245784833&sr=1-2](http://www.amazon.co.uk/Belkin-N-Wireless-USB-Adapter/dp/B001HO3ZTQ/ref=dp_cp_ob_ce_title_1?ie=UTF8&qid=1245784833&sr=1-2)

download windows drivers then use ndiswrapper



> **t_hutch said:**
> I got the green light from my wife to build a small (mini-ITX) frontend for my son's playroom. I'd like to avoid running wires, so I want to use wireless N. The case I have doesn't allow for a PCI card, so USB would be the way to go. Does anyone have a suggestion for a USB wireless N adapter that works out of the box or at least is a quick download away from working?

Thanks!

---

### Post by chitowner2 on 2009-09-10
> **db260179 said:**
> [http://www.amazon.co.uk/Belkin-WIRELESS-BUNDLE-F5D8053-F5D8633-4A/dp/B0012MUSN4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1245784762&sr=8-2](http://www.amazon.co.uk/Belkin-WIRELESS-BUNDLE-F5D8053-F5D8633-4A/dp/B0012MUSN4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1245784762&sr=8-2)

or just adapter

[http://www.amazon.co.uk/Belkin-N-Wireless-USB-Adapter/dp/B001HO3ZTQ/ref=dp_cp_ob_ce_title_1?ie=UTF8&qid=1245784833&sr=1-2](http://www.amazon.co.uk/Belkin-N-Wireless-USB-Adapter/dp/B001HO3ZTQ/ref=dp_cp_ob_ce_title_1?ie=UTF8&qid=1245784833&sr=1-2)

download windows drivers then use ndiswrapper


Yo db, that's not "just works"! I've been rummaging in related details and Belkin is a problem with ubu, even jaunty because it uses Raylink chipsets.

:-(

---

### Post by tonycollinet on 2009-09-10
> **chitowner2 said:**
> Yo db, that's not "just works"! I've been rummaging in related details and Belkin is a problem with ubu, even jaunty because it uses Raylink chipsets.

:-(

Have you considered homeplug (net over mains)?

---

### Post by novellahub on 2009-09-11
Another option would be using a Wireless N Access Point / Bridge.

---

### Post by williammanda on 2009-09-11
I read this post concerning using wireless N. He apparently gets great results using the 5Ghz 802.11N. He didn't mention the use of a usb nic.

[http://ubuntuforums.org/showpost.php?p=7759404&postcount=5](http://ubuntuforums.org/showpost.php?p=7759404&postcount=5)

Also here is what I found for working nic's in ubuntu:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

Thanks

---

### Post by Joe_Linux on 2009-09-11
You might try this 
[http://www.amazon.com/Mvix-Nubbin-MS-811N-Wireless-N-Adapter/dp/B0028YX24C](http://www.amazon.com/Mvix-Nubbin-MS-811N-Wireless-N-Adapter/dp/B0028YX24C)

---

### Post by williammanda on 2009-09-11
Ok I decided to do a HD wireless test. I have the following equipment:

wrt350n 2.4Ghz
wrt54g 2.4Ghz I used this post for the driver: [http://ubuntuforums.org/showpost.php?p=7200515&postcount=2](http://ubuntuforums.org/showpost.php?p=7200515&postcount=2)
wmp300n

I setup the wrt350n as a wireless N only and the wrt54g as a wireless G only (due to the dual N band of Linksys here [http://www.linksysbycisco.com/US/en/products/WRT610N](http://www.linksysbycisco.com/US/en/products/WRT610N)). I cascaded the wrt54g onto the wrt350n, the wrt350n was the router. I tested a digital video and it was good so I upped the stakes and tested a HD video and it also was good (HD NFL football game).
I also tried to upload a video while the HD video was playing and the HD video had problems. I right clicked on the network icon in the upper panel and I was getting 14Mbs. This explains any problems I may have had during the HD video. Another user expressed that he had great video preformance using 802.11n at 5 Ghz. 
[http://ubuntuforums.org/showpost.php?p=7759404&postcount=5](http://ubuntuforums.org/showpost.php?p=7759404&postcount=5)
At this point I can only tell you what I got with what equipment I had. It seems that more could be had. If you are using wireless, please post your results.
Thanks

---

### Post by nunrgguy on 2009-09-12
I wouldn't want to go USB anyway even if possible. Even on windows boxes it can sometimes be a pain getting one that will work on a system.
Used to be on home plug here until one box got moved onto a second ring so couldn't get fast enough net transfer. Went the AP route and have never looked back - it's a bit more expensive but is pretty much just plug and play apart from configuring the AP.

---

### Post by williammanda on 2009-09-12
> **nunrgguy said:**
> 
Used to be on home plug here until one box got moved onto a second ring so couldn't get fast enough net transfer.

What is home plug?

> Went the AP route and have never looked back - it's a bit more expensive but is pretty much just plug and play apart from configuring the AP.

Please define AP?

Thanks

---

### Post by wiebeest on 2009-09-12
Must dongles work out of the box, as long as you have disabled the PIN code beforehand.

For some reason Ubuntu doesn't really like it all that much.

When you disabled the PIN code, (under Windows or through swapping the SIM into your mobile phone and do so) the problem seems solved...

Helpful?

---

### Post by williammanda on 2009-09-13
> **t_hutch said:**
> I got the green light from my wife to build a small (mini-ITX) frontend for my son's playroom. I'd like to avoid running wires, so I want to use wireless N. The case I have doesn't allow for a PCI card, so USB would be the way to go. Does anyone have a suggestion for a USB wireless N adapter that works out of the box or at least is a quick download away from working?

Thanks!

Here one that requires alittle work:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB600N](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB600N)

It is dated 2008, it maybe better now. If I had the spare cash I would buy the linksys dual band 802.11 N. After my 2.4Ghz wireless n test, I'm convinced wireless video can be a reality.

---

