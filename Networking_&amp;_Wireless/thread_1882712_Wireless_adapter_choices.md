---
title: "Wireless adapter choices"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by SliderTech on 2011-11-17
I am in the market for a new wireless adapter.  I am looking for advice on what adapter to pick that will work for Ubuntu, XP and Win7.

I have a duel boot system and the current adapter I have, I cant get it to work in Ubuntu.

So, any advice on what adapters I should look at buying would be appreciated.


Thanks

Steve

---

### Post by haqking on 2011-11-17
> **SliderTech said:**
> I am in the market for a new wireless adapter.  I am looking for advice on what adapter to pick that will work for Ubuntu, XP and Win7.

I have a duel boot system and the current adapter I have, I cant get it to work in Ubuntu.

So, any advice on what adapters I should look at buying would be appreciated.


Thanks

Steve

Well to troubleshoot your existing one you should post a support thread listing it and what you have done to get it to work.

However as for Ubuntu WIFI adaptors see here :

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

then double check them on the hardware compatability list for Windows here for windows 7 [http://www.microsoft.com/windows/compatibility/windows-7/en-us/default.aspx](http://www.microsoft.com/windows/compatibility/windows-7/en-us/default.aspx)

---

### Post by SliderTech on 2011-11-17
> **haqking said:**
> Well to troubleshoot your existing one you should post a support thread listing it and what you have done to get it to work.

The current one I have is the WUSB54G v1.  So it's really old and its just time to upgrade.

Ill look at the link.

Thanks

---

### Post by haqking on 2011-11-17
> **SliderTech said:**
> The current one I have is the WUSB54G v1.  So it's really old and its just time to upgrade.

Ill look at the link.

Thanks

your existing one [https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54GS_v1_%26_v2](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54GS_v1_%26_v2)

---

### Post by SliderTech on 2011-11-17
Crud, Really....

This is were the old fart rolls on the floor laughing. :rolleyes:
Thanks for the link. Ill keep that in mind for the desktop.

It looks like I am going to get the DWA-160. I think that will work for what I need.

Thank you.

Steve

---

### Post by haqking on 2011-11-17
> **SliderTech said:**
> Crud, Really....

This is were the old fart rolls on the floor laughing. :rolleyes:
Thanks for the link. Ill keep that in mind for the desktop.

It looks like I am going to get the DWA-160. I think that will work for what I need.

Thank you.

Steve

no worries you are welcome.

remember to use thread tools to mark as solved if you feel you have all the answers you need.

Cheers

---

### Post by GuiGuy on 2011-11-17
> **SliderTech said:**
> I am in the market for a new wireless adapter.  I am looking for advice on what adapter to pick that will work for Ubuntu, XP and Win7.


Hi,
I've long lamented that [I had never managed to get ANY wireless adapter to work]("http://ubuntuforums.org/showthread.php?t=1828920"), including those that were listed as being supposed to work with Ubuntu.

I'm pleased to say that the D-LINK DW140 (b2) works out of the box for me. Performance is brilliant, even in our wireless saturated house. It also works well on Windows. It's a USB adapter.

---

### Post by SliderTech on 2011-11-17
Thanks guys.

I have ordered the 160 and ill post back here when I get it running. After that I will close this thread.

Thanks !

Steve

---

### Post by SliderTech on 2011-11-23
Ok, I got the DWA-160; v1.4. I installed the software on windows xp and it works great. I then booted to Ubuntu and did some reading then I plugged in the 160 and it worked out of the box and online in about 30 seconds. Dam if I did not need to do a thing to it. \\:D/

The DWA-160 is working flawlessly! =D>  for about 90 min.:frown:  Then everything slowed down.  For example here in the forums.  I click on a link and wait and wait for a page to change.  This is the same for other sites; Weather, news, Amazon just about all places.

It's really enjoying....  

Ill start a new thread on this if I cant find something about it.

If no comments  on this thread then I close it *solved*

---

### Post by streetwriter on 2012-01-04
> **GuiGuy said:**
> Hi,
I'm pleased to say that the D-LINK DW140 (b2) works out of the box for me. Performance is brilliant, even in our wireless saturated house. It also works well on Windows. It's a USB adapter.

That's encouraging. I bought one today, after being assured it would work. But I decided to check online before removing the shrink wrap from the box, and I was getting worried. 

When you say "out of the box," what exactly do you mean? How did you set it up? Did you disable your existing wireless adapter first? Remove any drivers? Or did you just plug it in and it worked?

I'm using Natty 11.04 on an Acer Aspire 5002 laptop with a built-in Broadcom B43 wireless g adapter, and upgrading my network to a D-Link gigabyte router.

---

### Post by bkratz on 2012-01-04
> **streetwriter said:**
> That's encouraging. I bought one today, after being assured it would work. But I decided to check online before removing the shrink wrap from the box, and I was getting worried. 

When you say "out of the box," what exactly do you mean? How did you set it up? Did you disable your existing wireless adapter first? Remove any drivers? Or did you just plug it in and it worked?

I'm using Natty 11.04 on an Acer Aspire 5002 laptop with a built-in Broadcom B43 wireless g adapter, and upgrading my network to a D-Link gigabyte router.



Not the originator but I am sure that he/she meant that they just plugged it in and it worked without adding any drivers. If you have a current b43 device you will probably want to blacklist the driver to prevent it from loading at boot time.

---

### Post by streetwriter on 2012-01-04
> **bkratz said:**
> Not the originator but I am sure that he/she meant that they just plugged it in and it worked without adding any drivers. If you have a current b43 device you will probably want to blacklist the driver to prevent it from loading at boot time.

Thanks for the help. There is a Linux driver for the device on the D-Link website. I'm wondering if I should install it first or just try disabling my onboard wireless, leaving the B43 driver installed, and plugging in the DWA-140 to see what happens.

(Also, not sure how one "blacklists" something. I'm an open-source guy at heart, and a writer by trade.)

---

### Post by SliderTech on 2012-05-29
Sorry all, I have been gone for a while.

Yes, when I unpacked the  DWA-160; v1.4 and plugged it in, it worked without adding any driver or making adjustments.

It has 2 problems.
The connection speed slows down right about the 30 min mark.
For some reason the  DWA-160 will be disconnected whenever. It's not set to a regular time interval. 
The only solution so far is to unplug it wait 10 seconds then plug it back in again.

Any ideas why it drops and how to fix that?

---

