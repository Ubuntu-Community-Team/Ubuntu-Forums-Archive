---
title: "USB Dongle for Access Point (master mode)"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by mgc8 on 2009-02-02
Hello,

I've currently bought an EEEBox I plan to use as a router, however the wireless part of it uses a Ralink RT2860 chipset which is not yet supported in Linux at all -- there is a driver on the Ralink website but it is STA only so no AP mode, also there is some work going on in rt2x00 but it's in no way usable yet.

In the meantime I'd like to still use the hardware, so I am thinking about buying a **Wireless USB dongle** and using that until RT2860 support matures.

The question thus would be -- has anyone successfully used any of the available WiFi-USB dongles on the market as an Acces Point (also known as "master mode")? I've heard some things about the Edimax EW-7318USG, however it also uses a Ralink chipset and nobody could confirm if it was indeed working for my needs.

I should point out that by "working" I mean a stable, good performance and good coverage connection with WPA2/AES enabled. So, can anyone give me an advice?

Thanks in advance,
Mihnea

---

### Post by mgc8 on 2009-02-05
> **mgc8 said:**
> Hello,
The question thus would be -- has anyone successfully used any of the available WiFi-USB dongles on the market as an Acces Point (also known as "master mode")? I've heard some things about the Edimax EW-7318USG, however it also uses a Ralink chipset and nobody could confirm if it was indeed working for my needs.


I kept searching and found out the Edimax EW-7318USG is indeed using the RT73 chipset, so theoretically it **should** work in AP mode. However I'd like to have some confirmation if this is true for Ubuntu/Debian: has anyone actually used this card in master mode with or without encryption (WPA2) successfully?

Thanks for any input!

---

### Post by raco on 2009-02-12
Hello,

[http://rt2x00.serialmonkey.com/wiki/index.php/AP-mode_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/AP-mode_Howto)

« This is a short guide to setting up AP-mode on rt2x00 chips. Note that this will not work with Ralink's USB chips because we don't know how to get status messages (ACK/FAIL) for sent packets. »

The Edimax EW-7318USG is based on a Ralink chip so it is supposed not to work in master mode.

I'll trying to find some USB device that accepts master mode too but it seems that it doesn't exists.

---

### Post by mgc8 on 2009-02-12
> **raco said:**
> Hello,
[http://rt2x00.serialmonkey.com/wiki/index.php/AP-mode_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/AP-mode_Howto)
« This is a short guide to setting up AP-mode on rt2x00 chips. Note that this will not work with Ralink's USB chips because we don't know how to get status messages (ACK/FAIL) for sent packets. »


Thank you for the reply, I've read that as well however look at this forum thread:
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5053&hilit=rt73usb](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5053&hilit=rt73usb)

There someone is using hostapd with that specific USB dongle (note the rt73usb module is used) and it appears to work... confusing, eh? I also asked a question on their forums and hopefully I'll get a definitive answer.

> **raco said:**
> 
I'll trying to find some USB device that accepts master mode too but it seems that it doesn't exists.

If you find something, please post here, I've been searching for some time for a device like this and couldn't find any... Maybe more eyes will have better luck :)

---

### Post by raco on 2009-02-12
I found that the "Zyxel G-202" key can be used in master mode with this driver : [http://zd1211.wiki.sourceforge.net/VendorBasedDriver](http://zd1211.wiki.sourceforge.net/VendorBasedDriver) but it seems to be buggy and not maintained anymore.

I'm giving up because I found another way to do what I wanted. I'll probably built my access point with this kind of computer : [http://www.norhtec.com/products/mcjrdx/index.html]("http://www.norhtec.com/products/mcjrdx/index.html"). It can have 2 NICs so I can put it between an ethernet-based AP and my LAN. The AP will have no protection but the computer will only let wireless clients connect to an openVPN server that requires authentication.

---

### Post by mgc8 on 2009-02-13
> **raco said:**
> I found that the "Zyxel G-202" key can be used in master mode with this driver : [http://zd1211.wiki.sourceforge.net/VendorBasedDriver](http://zd1211.wiki.sourceforge.net/VendorBasedDriver) but it seems to be buggy and not maintained anymore.

Hmm, interesting, I'll look more into it... thanks for the link!

> **raco said:**
> 
I'm giving up because I found another way to do what I wanted. I'll probably built my access point with this kind of computer : [http://www.norhtec.com/products/mcjrdx/index.html]("http://www.norhtec.com/products/mcjrdx/index.html"). It can have 2 NICs so I can put it between an ethernet-based AP and my LAN. The AP will have no protection but the computer will only let wireless clients connect to an openVPN server that requires authentication.

I see what you want to do is pretty similar to what I have in plan -- however that device has a very slow processor, little memory, the graphics is probably unusable in Linux, only 10/100 ethernet... The biggest advantage for it seems to be the price, you can deck it out at around 260$, which is significantly less than the price of an EeeBox; on the other hand, that would come with 1GB Ram, intel video+dvi, gigabit lan, wifi and a faster processor... Too bad the Wifi doesn't work yet in Linux  or it would've been perfect.

Anyway, I see on that page that you can choose between wifi and the 2nd nic, if you plan on using that for an AP anyway maybe it's worth investigating what chipset the Wifi would use (probably a miniPCI card) and if it works properly, it might save you some hassle!

Returning to the initial topic, I've spoken to IvD on serialmonkey.com and he explained that no USB adapters work at the moment in Master mode, although the driver *could* be patched to sort-of work, basically ignoring failed frames, although that would mean dropped connections and instability. However right now no USB dongle functions properly and work on the drivers is stalled because of lack of intereset/developers. Drats!

Guess I'll have to go and buy a small AP myself and use that until rt2800pci support matures in several months (with luck)...

---

### Post by raco on 2009-02-13
> **mgc8 said:**
> Hmm, interesting, I'll look more into it... thanks for the link!
Some people (here: [http://www.nabble.com/BCN-problem-td9672892.html]("http://www.nabble.com/BCN-problem-td9672892.html")) managed to make it work in master mode but it's not reliable.


> **mgc8 said:**
> I see what you want to do is pretty similar to what I have in plan -- however that device has a very slow processor, little memory, the graphics is probably unusable in Linux, only 10/100 ethernet...
It's quite powerful provided you don't want to install Ubuntu + Gnome on it. Certainly powerful enough to run an OpenVPN server. The ethernet is slow but the limiting factor is the WIFI speed which is even slower. In my opinion this computer has more power than needed to make a secure access point. Their WIFI option is not suitable for linux but you can buy the computer without it and with a mini-PCI slot so you can use the card you want.

Actually, buying an Eee-Box would be cheaper for me because of shipping costs and customs fees. But it is a lot bigger, its wireless card doesn't support master mode (and I don't know if it can be replaced by another one) and it is not fanless.

---

### Post by mgc8 on 2009-02-14
> **raco said:**
> Some people (here: [http://www.nabble.com/BCN-problem-td9672892.html]("http://www.nabble.com/BCN-problem-td9672892.html")) managed to make it work in master mode but it's not reliable.

That is indeed interesting, unfortunately the original driver is not maintained and the newer, rewritten driver does not support any interesting features so far... bummer. At least the cards are cheap and I found a store nearby that has them, might be worth a shot.

> **raco said:**
> It's quite powerful provided you don't want to install Ubuntu + Gnome on it. Certainly powerful enough to run an OpenVPN server.

Don't get me wrong, I currently use a very low-power router as the main "hub" in the house, it is an ASUS WL-700g with a 266 Mhz MIPS processor and a whopping 64MB of RAM :) It runs Debian with an OpenWRT kernel and actually manages around 80 Mbps on the wire and 30 Mbps over wireless. I also have it set up as an OpenVPN gateway and it tops out at around 7-8 Mbps there, which is hardly enough. That was one of the primary reasons I wanted a more powerful system, and the EeeBox seemed perfect for the job.

> **raco said:**
> Actually, buying an Eee-Box would be cheaper for me because of shipping costs and customs fees. But it is a lot bigger, its wireless card doesn't support master mode (and I don't know if it can be replaced by another one) and it is not fanless.

I can tell you from direct experience that the fan is completely silent, I never heard it over the other equipment in my living room (and it's not a noisy room). And the wireless is removeable, it is also miniPCI, however the case is a pain to dismantle and put back again. I actually considered that as an option, but decided against it when I saw the prices on some miniPCI adapters around -- although it could be a solution.

By the way, it seems there is a chance of rt73usb working after all -- here is the thread on the serialmonkey forums where I discussed it with IvD:
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5203&p=32195](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5203&p=32195)

Best of luck with your own project and hopefully we'll have more choice in this matter as the wireless drivers mature under Linux...

---

### Post by raco on 2009-02-14
Thank you and good luck with your project. Let us know if you make some USB dongle work as an access point.

Recently I realized that relying on the OpenVPN server is not enough because the wireless clients are still exposed to hackers, which demotivated me a bit. I guess that wiring my home for ethernet is simpler while being much more secure...

---

### Post by housty on 2009-05-10
> **raco said:**
> Thank you and good luck with your project. Let us know if you make some USB dongle work as an access point.

Recently I realized that relying on the OpenVPN server is not enough because the wireless clients are still exposed to hackers, which demotivated me a bit. I guess that wiring my home for ethernet is simpler while being much more secure...

I use this works perfect with no problems in master mode on linux

[http://www.planex.net/product/wireless/gw-us54gxs.htm](http://www.planex.net/product/wireless/gw-us54gxs.htm)

cya

---

### Post by mgc8 on 2009-05-10
> **housty said:**
> I use this works perfect with no problems in master mode on linux
[http://www.planex.net/product/wireless/gw-us54gxs.htm](http://www.planex.net/product/wireless/gw-us54gxs.htm)
cya

It seems to be using the ZyDAS zd1211 chipset, therefore I understand [this page]("http://linuxwireless.org/en/users/Drivers/zd1211rw") is incorrect when it states "Master mode -- not yet"? I see it's last been updated for 2.6.26, and a lot of development must have happened since...

Are you using WPA2/AES? How is the range and link quality?

Thanks,
Mihnea

---

### Post by loomis_2 on 2009-10-26
raco
 
  sorry to bring back an older post,  can anyone tell me if they have gotten the "Zyxel G-202" in AP mode?  trying to do this myself and found alot of links, but none really saying what has to be done, what driver, firmware etc.

---

### Post by nesimi on 2009-12-13
Hi,
I have been using my wireless usb dongle as access point (master mode) on Windows XP/7. I cannot use it on Ubuntu 9.10 yet. Actually I have just installed an appropriate driver for it. Now it can connects to wireless access points but it cannot create an access point. I am investigating... You can also look at my thread in [ubuntuforums]("http://ubuntuforums.org/showthread.php?t=1353061&highlight=edimax+ew7711uan").
Regards,

---

### Post by timmilicious on 2009-12-14
Hi Nesimi,

> **nesimi said:**
> Hi,
I have been using my wireless usb dongle as access point (master mode) on Windows XP/7. 

What WinXP software are you using to create the AP -- is it freeware?

Thanks.

---

### Post by timmilicious on 2009-12-14
Hi Mgc8/Housty/all,

> **mgc8 said:**
> It seems to be using the ZyDAS zd1211 chipset, therefore I understand [this page]("http://linuxwireless.org/en/users/Drivers/zd1211rw") is incorrect when it states "Master mode -- not yet"? I see it's last been updated for 2.6.26, and a lot of development must have happened since...

Are you using WPA2/AES? How is the range and link quality?


I too have a zd1211-based USB dongle (Belkin F5D7050 v4000, RAXWN4501H). It works fine as a client out of the box under Netbook-remix 9.10. But won't go into AP mode. 

Does anyone know which driver for this dongle does work in AP mode?

More generally, does anyone know *any* USB dongle and driver combination that will work in AP mode? I've searched the net for ages but can't come up with anything that works.

Thanks

---

### Post by BkkBonanza on 2009-12-14
I've been using master mode to run an access point using my Atheros AR9281. Driver is atk9k. Worked great with hostap and dnsmasq. 

This is on my Acer 4920 notebook. It came with an Intel wifi adapter but I bought a real cheap miniPCI AR9281 off ebay ($12 US) and swapped it. It seems to report a lower signal level value but connects just as well. If I recall correctly it needed either backport or compatible-wireless drivers built. I did this months ago but when I upgraded recently to Karmic it still worked fine.

I don't know if a dongle version of AR9281 is out there. Should be possible because often the miniPCI cards actually use USB for communicating anyway.

---

### Post by nesimi on 2009-12-14
> **timmilicious said:**
> Hi Nesimi,
What WinXP software are you using to create the AP -- is it freeware?
Thanks.
On Win XP I use a software of Edimax which was given with the usb dongle packet. On Win 7 I dont need to use any software, operating system can perform this.

---

### Post by timmilicious on 2009-12-14
> **BkkBonaza said:**
> I've been using master mode to run an access point using my Atheros AR9281. Driver is atk9k. Worked great with hostap and dnsmasq. 

...

I don't know if a dongle version of AR9281 is out there. Should be possible because often the miniPCI cards actually use USB for communicating anyway.

Thanks. I had gathered that Atheros chips are ideal for Master mode but I haven't found any USB dongles of this type.

---

### Post by nesimi on 2009-12-17
I have set up an AP on Ubuntu 9.04. Look at [this subject.]("http://ubuntuforums.org/showthread.php?p=8515835#post8515835")
Regards,

---

### Post by BkkBonanza on 2009-12-17
Does Windows actually provide master mode AP software now? Or are you talking about an ad-hoc connection. These are completely different things. Any dongle will work in ad-hoc mode generally but only dongles with specific master mode driver support will work in a true AP mode.

---

### Post by nesimi on 2009-12-18
> **BkkBonaza said:**
> ...but only dongles with specific master mode driver support will work **in a true AP mode**.

Sure, I know I need the proper driver (also support of hardware) for the wireless dongle. That is why I cannot use this dongle on 9.10. I think you should see the thread that I have given in my previous post.

What do you mean with "true AP mode"?

---

### Post by BkkBonanza on 2009-12-18
May be nothing, I just thought it seemed like you said because you could connect together and access the net it meant you were in master mode. But you can connect and share the net using just an ad-hoc connection. That's not AP mode. AP mode would be using the driver's master mode, which is not the normal operating mode for wifi adapters. In AP mode the adapter is set to broadcast as a station that many users can connect to and receive IP addresses from such that you are all on a LAN hosted by the AP. This may be what you are doing in W7 but the wording seemed a bit unclear. Usually you need to run special software to do AP mode because it needs DHCP, and often DNS and routing etc. For example, a Linksys wifi router is using master mode of the adapter built in.

---

### Post by f0gr3at on 2010-06-15
I thought maybe this thread could be revived as some wireless drivers may have matured recently. I have the exact same issue as the first post: how to make a wireless AP using either the built in (mini pcie) rt2860 card or a usb adapter?

I've found:
[http://wireless.kernel.org/en/users/Drivers/rt2800pci](http://wireless.kernel.org/en/users/Drivers/rt2800pci)

Which seems to support the rt2860 in AP mode. Anyone used these drivers successfully (running 10.04)?

Cheers.

---

### Post by mgc8 on 2010-06-16
> **f0gr3at said:**
> I thought maybe this thread could be revived as some wireless drivers may have matured recently. I have the exact same issue as the first post: how to make a wireless AP using either the built in (mini pcie) rt2860 card or a usb adapter?
I've found:
[http://wireless.kernel.org/en/users/Drivers/rt2800pci](http://wireless.kernel.org/en/users/Drivers/rt2800pci)
Which seems to support the rt2860 in AP mode. Anyone used these drivers successfully (running 10.04)?
Cheers.

Hi, I actually gave up hoping for a driver to run the rt2860, there is one currently but it's buggy and unstable after years of development, so it's not worth it in my opinion, we'll have newer hardware before it becomes usable :-/

On the other hand, I did manage to get the older Edimax EW-7318USG USB dongle to work nicely.  The advantage with that is you can basically turn any Linux device that has USB ports into an access point, so it's quite nice. See [this thread](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5053&hilit=rt73usb) for more info, there are more details on the serialmonkey site too.

Basically I use the newest version of hostapd (older ones required patching) and a recent kernel, version 2.6.32 atm. since Debian is in freeze. Things work smoothly 90% of the time, except the odd bug which creeps up from time to time making the card crash, in which case you get lots of errors in the logs and you need to manually extract and replace it -- [this thread](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=4927&p=34374#p34374) has more information regarding the problem.

Other than that, things work fine, signal is strong and speed around 25-30Mbps over WPA2, which is great for a G-level card.

Hope this helps!

---

