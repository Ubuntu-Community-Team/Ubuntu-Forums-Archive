---
title: "Any Plug n Play USB Wireless Adapters?"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by Jonah11 on 2010-02-18
I recently purchased the Asus N13 wireless usb adapter, which is supported on linux.  However, the instructions for installing the drivers are quite long and complicated (for a linux newb like me, at least), and it will probably take me 45 minutes to an hour to install, with a good chance that it doesn't work afterward.  

My question is: Are there any wireless-N USB adapters for linux that are either:
1. plug n play?
2. have a simple double-click type installer for installing the drivers?

thanks,
jonah

---

### Post by 2hot6ft2 on 2010-02-18
For just plug and play compatibility anything with a Realtek chip RTL8187B or RTL8187L with the L being the better of the 2. It can be hard to find in stores since most of those in stores have Ralink chips which can be a pain. If it's in a store here in the US and it has N then it's pretty much guaranteed to be Ralink. Some eBay ones are:

ALFA Network AWUS036H 500mW USB WiFi Wireless-G
Gsky 500mW USB Wireless G

---

### Post by warp99 on 2010-02-18
> **Jonah11 said:**
> 
My question is: Are there any wireless-N USB adapters for linux that are either:
1. plug n play?
2. have a simple double-click type installer for installing the drivers?

thanks,
jonah

The modules (drivers) should already be in the kernel and will be loaded when you insert the card. What guide are you using? It may be outdated.

---

### Post by 2hot6ft2 on 2010-02-18
My mistake. Well I have a Belkin N Wireless F5D8053v4. While it is possible to get it working I wouldn't recommend it.

---

### Post by Jonah11 on 2010-02-18
> **warp99 said:**
> The modules (drivers) should already be in the kernel and will be loaded when you insert the card. What guide are you using? It may be outdated.

Nothing happens when I insert the card, and it shows no signs of being recognized.  Restarting does not help.  I'm using the guide that came with the downloaded drivers from ASUS's website.

I also have wicd network manager, if that is relevant.

---

### Post by Jonah11 on 2010-02-18
hot, i had a usb wireless-G from iogear that was working before and required little setup, but i need wireless-N since i stream video over the connection.

---

### Post by warp99 on 2010-02-18
I checked with the Asus site and that adapter uses a RT2870 chipset, which is Ralink. A quick kernel search shows that module is already in the kernel:

```
locate rt2870
/lib/firmware/rt2870.bin
/lib/modules/2.6.31-19-generic/kernel/drivers/staging/rt2870
/lib/modules/2.6.31-19-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

```

Did you try and see if the adapter works?

Edit:

If it doesn't work you can install the package "linux-backports-modules-wireless-karmic-generic" which has the lastest and greatest modules available.

---

### Post by Jonah11 on 2010-02-18
"Did you try and see if the adapter works?"

Thanks very much for your help, so sorry for this newb question: but how do i do that beyond just plugging in the adapter?

---

### Post by 2hot6ft2 on 2010-02-18
> **Jonah11 said:**
> 
I also have wicd network manager, if that is relevant.
I tried WICD since it works so good in backtrack. But it wouldn't connect or for that matter even recognize 2 of 3 wifi adapters. It would recognize my internal Atheros AR928x but just once then it was gone. So I went back to network manager and all 3 are recognised and can connect.

By the way the internal is N Wireless Atheros AR5009 with the AR928x chipset. Unfortunately I don't know of any usb adapters that use that chipset.

---

### Post by warp99 on 2010-02-18
> **Jonah11 said:**
> Nothing happens when I insert the card, and it shows no signs of being recognized.  Restarting does not help.  I'm using the guide that came with the downloaded drivers from ASUS's website.

I also have wicd network manager, if that is relevant.

Try installing the package "linux-backports-modules-wireless-karmic-generic", then reboot the computer with the adapter plugged in.

---

### Post by Jonah11 on 2010-02-18
also, it does show up in driver/staging when i run your locate code.  

however, that may be from some installation i did for my old buffalo infiniti card, which i had hired someone to help me get the drivers working for, took about an hour of troubleshooting, and then when linux updated they broke, so i gave up and decided to try a new card.

---

### Post by 2hot6ft2 on 2010-02-18
> **warp99 said:**
> I checked with the Asus site and that adapter uses a RT2870 chipset, which is Ralink. A quick kernel search shows that module is already in the kernel:

```
locate rt2870
/lib/firmware/rt2870.bin
/lib/modules/2.6.31-19-generic/kernel/drivers/staging/rt2870
/lib/modules/2.6.31-19-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

```

Did you try and see if the adapter works?

Edit:

If it doesn't work you can install the package "linux-backports-modules-wireless-karmic-generic" which has the lastest and greatest modules available.
That's the same as the Belkin I mentioned earlier and for the N wireless you need to use Ralink's rt3070 driver (module rt3070sta). I'm using mine right now. Here's the guide for it:
[RALINK RT2870STA and RT3070STA USB WiFi Tutorial]("http://ubuntuforums.org/showthread.php?t=1342593")

---

### Post by Jonah11 on 2010-02-18
> **2hot6ft2 said:**
> That's the same as the Belkin I mentioned earlier and fore the N wireless you need to use Ralink's rt3070 driver (module rt3070sta). I'm using mine right now. Here's the guide for it:
[RALINK RT2870STA and RT3070STA USB WiFi Tutorial]("http://ubuntuforums.org/showthread.php?t=1342593")

yes, that looks about the same as the instructions that came with the driver, and i was hoping to avoid it because there is a good chance i mess up somewhere along the way.

if any wireless-N are available that don't require a roll your own driver, i'd rather just return my asus and buy that.  if none are available, i will obviously attempt it.

---

### Post by 2hot6ft2 on 2010-02-18
It's not all that bad the writer of the guide did a good job in making it about as easy as you'll find. I've looked all over the place for just what you're looking for and never found a usb N Wireless that didn't have that pesky Ralink chipset. Now if you have an INTERNAL mini pci slot the Atheros AR5009 with the AR928x chipset works out of the box.

---

### Post by warp99 on 2010-02-18
I would try the backport modules first, you may be surprised. If that doesn't work then use the guide 2hot6ft2 posted.

---

### Post by Jonah11 on 2010-02-18
thanks for your help.  i will try both of these things tonite and report back.

---

### Post by UBUSHEP on 2010-02-21
2Hot, just to confirm - you mentioned that to do wireless N with that guy's Belkin (which uses an rt2870 chipset), you needed to use the 3070 driver. To confirm, are you saying that even though he's using a 2870 chipset, he'd still need to use the 3070 driver with the 2870 chipset if he wants to use N?
I have a similar problem, similar chipset and have been terribly unsuccessful.. am going to follow the instructions on the link you sent here in a bit.

---

### Post by 2hot6ft2 on 2010-03-06
> **UBUSHEP said:**
> 2Hot, just to confirm - you mentioned that to do wireless N with that guy's Belkin (which uses an rt2870 chipset), you needed to use the 3070 driver. To confirm, are you saying that even though he's using a 2870 chipset, he'd still need to use the 3070 driver with the 2870 chipset if he wants to use N?
I have a similar problem, similar chipset and have been terribly unsuccessful.. am going to follow the instructions on the link you sent here in a bit.
A bit late in answering I just came across this thread again.
To answer your question **Yes** that is what I'm saying apparently the 3070sta driver works better for N on the 2870 chipset.
Also to use N you need to use WPA AES encryption on your AP (Access Point).

I can confirm that it's working for me.

I wouldn't install any backports kernels to make it work. They're backports for a reason.

---

### Post by Jonah11 on 2010-03-08
This isn't working for me.  I followed the steps of the tutorial, but after building my ko file I get:

insmod: error inserting 'rt3070sta.ko': -1 Unknown symbol in module

Any idea whats wrong?

Thanks,
Jonah

---

