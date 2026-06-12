---
title: "Broadcom wireless driver installed on Natty but not working"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by markling on 2012-06-10
Specifications
--------------
Broadcom Wireless network controller: BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

HP 530 notebook computer

Problem
-------
Wireless not working. The network manager applet doesn't even allow me to search for available networks. (Neither does the network manager applet tell me that the reason its not showing networks is because it can't detect the wireless driver. It would be helpful if it did).

The Broadcom wireless driver
----------------------------
This was installed by doing the menu System > Administration > Additional Drivers. It tells me it has installed the "Broadcom STA proprietary wireless driver".

If I type "sudo lshw -C network" in a terminal window it gives me the following information:

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0003fff

Ubuntu version: Ubuntu 11.04 - the Natty Narwhal

Request for help
-----------------
Can someone please help me get this driver working?

A tuppeny's worth, as an aside
---------------------------------
HP, one of the largest computer companies in the entire world, released this 530 laptop as some sort of horrible joke, it seems to me. An elderly relative of mine had the misfortune to buy it off someone unscrupulous enough to sell it. It came with Vista. It ran like a over-fed dog on a sunny afternoon. The relative asked for my help. I ended up putting Ubuntu on it. It was like putting the dog down. But the wireless card didn't work. The computer ended up gathering dust. What an utter waste of money. If you look on the forums, you see that these Broadcom network adapters had been a problem for years because they couldn't be bothered to release a linux driver. Broadcom seemed like some fat, lazy dog as well. I hope they get worms and fleas, and that they get old-dog bowel problems in the lobby of HP's corporate headquarters when they go there to gloat over the huge amount of money they made from selling this horrible laptop computer. And so now it seems there is at last a driver. But it doesn't work out of the box. What a surprise. Someone call a vet. Tell them they'll need rubber gloves.

---

### Post by BeenLikeFlynn on 2012-06-10
Make sure your modem/router driver is installed, be careful of wrong sites. Otherwise obtain a wifi card/usb antenna.

---

### Post by westie457 on 2012-06-10
Hi, plug in an ethernet cable if not already using one.

Remove the STA Driver this can be done with 'Additional Drivers', just deactivate it.

Open a terminal type and run these commands.```
sudo apt-get install b43-fwcutter

sudo apt-get install firmware-b43-installer
```

Remove the cable and reboot your machine to complete the removal of the STA driver. Wireless should now be working.

Post back here with the news.

Thank you.

---

### Post by markling on 2012-06-11
Success! 

This is brilliant. Thank you westie457. I followed your excellent advice. The wireless on this HP 530 is now working perfectly. Even the blue wireless button is working.

Seems there is life in the old dog yet. But why oh why oh why could Broadcom and HP not manage to fix it so it simply worked in the first place - or failing that, simply updated and then simply worked - or failing that, fix it so when you discover by chance that they have at last produced a driver and click on the (hidden) button to install it, that it then simply works?

Tell me if I'm wrong, but I thought this was a fine tradition:

i) Press button to install driver
ii) Watch for message saying driver installed
iii) Use device

Even that sounds quaintly old-fashioned since the invention of the automatic update.

What we have instead is:

i) Press button to install driver
ii) Watch for message saying driver installed
iii) Discover driver is not working as advertised
iv) Spend hours trawling support forums for solution
v) Blindly follow some arcane instruction that uninstalls the driver and installs something else entirely in its place
vi) Resolve to make the best of things though a little piece of one's soul has just withered and died
vii) Use device

Well done Broadcom and HP!

---

