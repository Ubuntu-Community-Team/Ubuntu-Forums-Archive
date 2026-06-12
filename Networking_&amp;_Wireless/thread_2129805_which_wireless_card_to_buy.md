---
title: "which wireless card to buy?"
date: 2013-03-27
forum: Networking &amp; Wireless
---

### Post by goodbye-windows(tm) on 2013-03-27
Hi all,

I have to buy a new wifi unit to connect my computer to my router. 

I don't need anything fancy and I don't want an expensive unit, it has to be a plug in usb type.

Ebay has usb wifi units based on the RTL8188 chipset. However, they are problematic with regard to installation, they have to be manually installed.

If i want a usb based wifi  (sub miniature usb memory module sized), which make and model do I look for?? I want something that can be plugged in and will function properly without having to mess around doing a manual install. Cheap is better, and I don't need the latest and greatest high speed units as we do not have high speed internet.

Can anyone make suggestion(s)??

TIA.

Art

---

### Post by sudodus on 2013-03-27
> **goodbye-windows(tm) said:**
> Hi all,

I have to buy a new wifi unit to connect my computer to my router. 

I don't need anything fancy and I don't want an expensive unit, it has to be a plug in usb type.

Ebay has usb wifi units based on the RTL8188 chipset. However, they are problematic with regard to installation, they have to be manually installed.

If i want a usb based wifi  (sub miniature usb memory module sized), which make and model do I look for?? I want something that can be plugged in and will function properly without having to mess around doing a manual install. Cheap is better, and I don't need the latest and greatest high speed units as we do not have high speed internet.

Can anyone make suggestion(s)??

TIA.

Art

You will get a good overview at the following link

[[COLOR=#ff0000]http://www.linuxwireless.org/en/users/Devices/USB[/COLOR]]("http://www.linuxwireless.org/en/users/Devices/USB")

where you can see what wifi chips are used.

---

### Post by eyeneedhelp on 2013-03-27
i came here after buying a " widemac" usb device.  the first time i plugged it in it found the network before i knew what happened. later i had trouble and came here for help.
as i struggled with that wifi problem,and learning ubuntu, i realized that i did not always connect so i moved my computer to a new location and ,,here i am solid connection every day.

i understand that the same unit may have a different chip in it so you can look at my previous posts under "wifi trouble" and read about the stuff we found or just try one, i see that device for $5 direct from china with 2 bucks shipping!
good luck

btw before i got to install the sw that came on a small cd, my cd reader ate it so i never got to install it. i guess ubuntu has the driver.

---

### Post by vapor0 on 2013-03-27
I've got one of those 5 dollar ralink ebay jobbies, and it works great! No driver installation in Ubuntu at all...

---

### Post by kurt18947 on 2013-03-27
If you have a pretty strong wifi signal, I bought an adapter off Ebay about a week ago.  Cost me $6 delivered and is plug 'n' play.  If you live in the U.S., here is a link to the Ebay posting I used.  I have no financial or other interest in the vendor, just know he/she bumped the price up $1 since I bought mine.  I live somewhat close so ordered one morning and had it the next day.

[http://www.ebay.com/itm/Newest-Mini-150Mbps-USB-WiFi-Wireless-N-LAN-Network-Adapter-802-11n-g-b-/170905493801?ssPageName=ADME:L:OC:US:3160](http://www.ebay.com/itm/Newest-Mini-150Mbps-USB-WiFi-Wireless-N-LAN-Network-Adapter-802-11n-g-b-/170905493801?ssPageName=ADME:L:OC:US:3160)

Likely the same device as vapor0 refers to.  It uses a Ralink 5370 chipset.  I don't find the signal strength as good as the Edimax EW7811Un (uses a Realtek 8188CUs chipset) but the Edimax is not plug 'n' play, it required downloading and installing a driver from Realtek.

---

### Post by goodbye-windows(tm) on 2013-03-31
Hi Kurt, thanks for the recommendation. I just bought it. 

The 5370 chipset is very linux compatible although some users do have to install it manually. Not sure why it works out fo the box for some, but needs to be manually installed by others.

It's hard to believe that unit works at all, there isn't much room for an antenna inside the thing. But, time will tell::>

Thanks to all who replied to my posting.

Art

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by kurt18947 on 2013-03-31
> **ahallubuntu said:**
> I don't find the RTL8188 chipset problematic - I can install the driver in about five minutes now, having done it a few times.  I have several of these dongles, and they work very well for me.  The fact that one must do the installation in a terminal and blacklist a few modules probably is intimidating to a few people, but there are detailed instructions on how to do it.

I haven't tried it lately, but the 8188CUs driver from RealTek wouldn't build on 13.04 using the included script.  It's fine on 12.04 & 12.10.  Stealth Dave posted a patch for the driver from Realtek which may well let it install on 13.04,  I haven't tried the patch.  Prasedym also posted a link to a modded driver on that also supported DKMS which should remove the need to reinstall the driver with each kernel upgrade.

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by kurt18947 on 2013-04-01
> **ahallubuntu said:**
> It's baffling that the Realtek driver will *STILL* broken in 13.04!!!  Unbelievable.  Can't they just get rid of the kernel driver it doesn't work?  It's never worked (reliably) for me in 12.04 or 12.10 without installing the Realtek driver...

Agreed.  I was hoping the 8188CUs devices would finally be "plug 'n' play" but not yet, it seems.

---

### Post by eyeneedhelp on 2013-04-02
btw, for what its worth, i extend mine on a 3 foot usb ext cable to get it up on top of comp. range is solid.

---

