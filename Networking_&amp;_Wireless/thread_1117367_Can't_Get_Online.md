---
title: "Can't Get Online"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by atravnic on 2009-04-05
Both 8.04 and 8.10 load fine from LiveCD but neither connects wirelessly to the Internet.

HP tx2500z laptop
Vista Home Premium SP1
AMD Turion X2 Dual-Core Mobile processor RM
ATI Radeon HD 3200 graphics card
Broadcom 4322AG 802.11a/b/g/draft-n WiFi adapter
Realtek RTL 8186C (P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)

So if I need a driver, a) does anyone know which one, and b) how will I find it in Ubuntu since I'll  have to use Vista to download it since I can't get online in Ubuntu? Catch-22 . Help appreciated! Thanks!

...Fred

---

### Post by battlebison on 2009-04-05
First go to System -> Administration -> Network Tools or Networks and see if you can figure it out from there. If not, continue:

Could you open terminal from Applications -> Accessories -> Terminal, and then type in "iwconfig" and copy (Ctrl + Shift + C in terminal) and paste the results to here? I've been moving files back and forth from Ubuntu to Vista with a USB drive. To save those results, just type "gedit" to bring up the text editor, paste (just Ctrl + V here) those results into there and save them to the USB key. Also, at the top of this forum, there are a few really helpful stickies that you might want to look at. Apparently, [your wireless should work]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom#miniPCI"). I'm having issues with my wireless too though, even though it's also on the supported list. Good luck, hope to see what the iwconfig turns up!

---

### Post by Favux on 2009-04-05
Hi atravnic,

Did you go to System>Administration>Hardware Drivers?  You'll see "Broadcom STA wireless driver".  This is the proprietary Broadcom driver.  Go ahead and activate it.  Reboot.

Edit: Oops, you're running live CD, not installed?

---

### Post by atravnic on 2009-04-06
> **atravnic said:**
> Both 8.04 and 8.10 load fine from LiveCD but neither connects wirelessly to the Internet.

HP tx2500z laptop
Vista Home Premium SP1
AMD Turion X2 Dual-Core Mobile processor RM
ATI Radeon HD 3200 graphics card
Broadcom 4322AG 802.11a/b/g/draft-n WiFi adapter
Realtek RTL 8186C (P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)

So if I need a driver, a) does anyone know which one, and b) how will I find it in Ubuntu since I'll  have to use Vista to download it since I can't get online in Ubuntu? Catch-22 . Help appreciated! Thanks!

...Fred
Yes, I'm running Live CD, for now, to check out 8.04 and 8.10 on this new laptop before I install it and discover problems. My ultimate goal is dual boot because, much as I want to, I cannot entirely leave the Windows world. Any pearls of wisdom? Thanks.  ...Fred

---

### Post by atravnic on 2009-04-06
> **battlebison said:**
> First go to System -> Administration -> Network Tools or Networks and see if you can figure it out from there. If not, continue:

Could you open terminal from Applications -> Accessories -> Terminal, and then type in "iwconfig" and copy (Ctrl + Shift + C in terminal) and paste the results to here? I've been moving files back and forth from Ubuntu to Vista with a USB drive. To save those results, just type "gedit" to bring up the text editor, paste (just Ctrl + V here) those results into there and save them to the USB key. Also, at the top of this forum, there are a few really helpful stickies that you might want to look at. Apparently, [your wireless should work]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom#miniPCI"). I'm having issues with my wireless too though, even though it's also on the supported list. Good luck, hope to see what the iwconfig turns up!
Maybe I should have mentioned I'm not overly technical and what you're suggesting sounds a tad scary to me. Nonetheless, I will take a stab at it and let you know. It may take me a few days though because there is life before, during and after Ubuntu, sad huh. Thanks.     ...Fred

---

### Post by Ayuthia on 2009-04-06
You might try the following to see if this will work with the liveCD:
Go into System->Administration->Hardware Drivers and activate the Broadcom STA driver.  Next try the following in the Terminal:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
These commands will remove the possible conflicting wireless modules and then activate the Broadcom STA (wl) module.  It will then bring up the wireless card and attempt to scan for wireless sites.

Hope this helps.

---

### Post by lisati on 2009-04-06
> **atravnic said:**
> Maybe I should have mentioned I'm not overly technical and what you're suggesting sounds a tad scary to me. Nonetheless, I will take a stab at it and let you know. It may take me a few days though because there is life before, during and after Ubuntu, sad huh. Thanks.     ...Fred

That's what we're here for - to provide support and encouragement, and to bounce ideas around.

All of us here at the Ubuntu forums have been new to finding our way Ubuntu (and Linux=based systems in general) at some point and many of us will be able to relate to experiencing a degree of apprehension when trying to figure things out.

---

