---
title: "can anyone recommend a no-BS Wireless Adapter?"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by jbeiter on 2009-08-15
I'm setting a neighbor up with Jaunty and he needs wireless. He got a netgear usb and now an otherwise smooth install has come to a grinding and screeching halt.

I don't want to go on a scavanger hunt for drivers, spend hours screwing with wpasupplicant or ndiswrapper and trying 100 different failed suggestions on how to get this stupid thing working.

Can ANYONE suggest a USB Wireless Adapater I can plug into a Ubuntu 9.04 machine and it just works without the BS?

Yes - I have looked at the hardware compatibility sheet. It looks seriously outdated and I can't find anything that looks like what I'm hoping to find (a no-BS adapater.)

If there is no such animal out there, how about a no-BS pci?

Thank you!

---

### Post by Whiffle on 2009-08-15
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833124350](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124350)

I plugged one of those into my computer yesterday, 9.04 picked it up and used it right away.

---

### Post by Lupgaru on 2009-08-15
[http://www.linksysbycisco.com/US/en/products/WUSBF54G](http://www.linksysbycisco.com/US/en/products/WUSBF54G)

You might try this one, I've used it on laptops and desktops with 6 different Linux distros, using it on Ubuntu 9.04 right now. It also works with all versions of Winsuck.
    Ubuntu picks it up automatically.

---

### Post by MaindotC on 2009-08-15
How about an N adapter?

---

### Post by jbeiter on 2009-08-15
Many thanks folks!!

---

### Post by jbeiter on 2009-08-18
Got a WUSB54GC (ver 3) from radio shack and, no go. The system did not recognize it at boot up. Jumped through a couple of hoops in other threads to download/compile drivers... SOS.

Are the USB FOBs so similar in part number but different in function that it is this picky?

My laptop (Acer One w/wireless) hooks up to the router no problems at all. It's also running ubuntu 9.04.

My neighbor's PC is at a point where it can see the router's SSID (I have it wide open now) but will not join up.  Tailing syslog has this in it:

------------------------------------------------
Aug 18 15:55:31 john-desktop NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug 18 15:55:31 john-desktop NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug 18 15:55:36 john-desktop NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug 18 15:55:36 john-desktop kernel: [  449.191731] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Aug 18 15:55:36 john-desktop kernel: [  449.192050] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Aug 18 15:55:36 john-desktop kernel: [  449.249015] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
Aug 18 15:55:46 john-desktop NetworkManager: <info>  Activation (ra0/wireless): association took too long, failing activation. 
Aug 18 15:55:46 john-desktop NetworkManager: <info>  (ra0): device state change: 5 -> 9 
Aug 18 15:55:46 john-desktop NetworkManager: <info>  Activation (ra0) failed for access point (foo-bar) 
Aug 18 15:55:46 john-desktop NetworkManager: <info>  Marking connection 'Auto foo-bar' invalid. 
--------------------------------------------------

started down the path of ndiswrapper, and wpa_supplicant but I'm just not getting anywhere with this. The documentation for both are hideous.

I've sent the poor guy back to exchange the Netgear USB for the Linksys. Is the WUSBF54G really that different from the WUSB54GC that he got? This is getting embarassing. Hate to recommend windows but I don't want this boogering up on him down the road after these gymnastics.

Appreciate the help.

---

### Post by Whiffle on 2009-08-18
Huh.  Thats really strange.  Ralink is the same as what I had tried, I'm certain of that.  I googled that error message you got and it didn't show up as anything common either.  Hmmm.

---

### Post by demosthene1 on 2009-08-18
Zonet zew2507 is a super compatible wifi usb adapter. Plug it in and go!

---

### Post by Lupgaru on 2009-08-18
> **jbeiter said:**
> Got a WUSB54GC (ver 3) from radio shack and, no go. The system did not recognize it at boot up. Jumped through a couple of hoops in other threads to download/compile drivers... SOS.

Are the USB FOBs so similar in part number but different in function that it is this picky?

My laptop (Acer One w/wireless) hooks up to the router no problems at all. It's also running ubuntu 9.04.

My neighbor's PC is at a point where it can see the router's SSID (I have it wide open now) but will not join up.  Tailing syslog has this in it:

------------------------------------------------
Aug 18 15:55:31 john-desktop NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected 
Aug 18 15:55:31 john-desktop NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning 
Aug 18 15:55:36 john-desktop NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating 
Aug 18 15:55:36 john-desktop kernel: [  449.191731] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Aug 18 15:55:36 john-desktop kernel: [  449.192050] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Aug 18 15:55:36 john-desktop kernel: [  449.249015] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
Aug 18 15:55:46 john-desktop NetworkManager: <info>  Activation (ra0/wireless): association took too long, failing activation. 
Aug 18 15:55:46 john-desktop NetworkManager: <info>  (ra0): device state change: 5 -> 9 
Aug 18 15:55:46 john-desktop NetworkManager: <info>  Activation (ra0) failed for access point (foo-bar) 
Aug 18 15:55:46 john-desktop NetworkManager: <info>  Marking connection 'Auto foo-bar' invalid. 
--------------------------------------------------

started down the path of ndiswrapper, and wpa_supplicant but I'm just not getting anywhere with this. The documentation for both are hideous.

I've sent the poor guy back to exchange the Netgear USB for the Linksys. Is the WUSBF54G really that different from the WUSB54GC that he got? This is getting embarassing. Hate to recommend windows but I don't want this boogering up on him down the road after these gymnastics.

Appreciate the help.

I hate to say this but they are different and I could not find out why. I started with the 54G then later tried the 54GC. I had to return it. There has to be some difference in the driver. Hope you have luck with the 54G, I always have.

---

### Post by SpitfireSMS on 2009-08-18
Seriously try ebay.
I bought a $10 usb adapter on ebay and it has been plugged in and just works.
Tried on Ubuntu, Suse, Fedora, and various windows.
It didnt have a sticker or label on it, it was just black.
If I still had it I would lookup the chip name for you, but one quick ebay search will actually show you some good and inexpensive solutions

[http://shop.ebay.com/?_from=R40&_trksid=p3907.m38.l1313&_nkw=linux+usb+wireless&_sacat=See-All-Categories](http://shop.ebay.com/?_from=R40&_trksid=p3907.m38.l1313&_nkw=linux+usb+wireless&_sacat=See-All-Categories)

---

### Post by MaindotC on 2009-08-19
There's a USB adapter called the WiBee that doesn't seem to have a manufacturer but it uses the RTL8187 chipset and is fully compatible with kernel 2.6.x  I have four of them :D

---

