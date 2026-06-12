---
title: "Alternatives to Aircrack-ng"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by Fenlig on 2011-08-19
Hey Guys,

Seems my latops wireless card is not compadible for the Aircrack-ng, is there any other options for me :confused:

Thanks

---

### Post by Dangertux on 2011-08-19
Have you installed injection capable drivers for your card? Even if there is an alternative, an application isn't going to be able to perform injection without drivers capable of it.

---

### Post by Fenlig on 2011-08-19
Im still fairly new to Linux but i dont think my card is compadible at all

fenlig@Lappy:~$ lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

---

### Post by Dangertux on 2011-08-19
> **Fenlig said:**
> Im still fairly new to Linux but i dont think my card is compadible at all

fenlig@Lappy:~$ lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

I think it should be ok, I use a Broadcom Airforce 54G for injection and it works fine, double check the compatibility list

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers#which_is_the_best_card_to_buy](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers#which_is_the_best_card_to_buy)

Also, make sure you are patching the mac80211 stack, there is also a tutorial for that on the same  aircrack-ng site.

---

### Post by spiky001 on 2011-08-19
I have looked through the aircrack website no it,s not supported for monitor or injection

---

### Post by Dangertux on 2011-08-19
> **spiky001 said:**
> I have looked through the aircrack website no it,s not supported for monitor or injection

It does not support it with the brcom80211 driver however, the b43 drivers should work just fine, and DO support both injection and monitor modes. With the exception of fragmentation attacks from aireplay-ng (on some chipsets)

---

### Post by Fenlig on 2011-08-19
> **Dangertux said:**
> It does not support it with the brcom80211 driver however, the b43 drivers should work just fine, and DO support both injection and monitor modes. With the exception of fragmentation attacks from aireplay-ng (on some chipsets)

Thanks for looking Dangertux, but im having problems installing this b43 driver as I am abit of a newbie, could you briefly explain how I need to go about this as im getting lost with all the information out there :)

---

### Post by Dangertux on 2011-08-19
> **Fenlig said:**
> Thanks for looking Dangertux, but im having problems installing this b43 driver as I am abit of a newbie, could you briefly explain how I need to go about this as im getting lost with all the information out there :)

This should help :-)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Fenlig on 2011-08-20
Okay ive gotten to the part Installing b43 drivers and cant get by step 2 of that section as i only see Broadcom STA wireless drivers in my Additional drivers section. Any Ideas?

---

### Post by Tetsh on 2012-03-17
For the driver to work on your card you need kernel version 3.1 or later.

---

