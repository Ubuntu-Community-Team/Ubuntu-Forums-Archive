---
title: "Broadcom 4311 wireless install in Kubuntu 9.04"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by K8JWT on 2009-08-23
Was checking to see if there had been a easier fix for setting up the Broadcom 4311 wireless card in the newest version of Kubuntu/Ubuntu?


Have been searching around on the site(s) and it seems like many ways to do it but gets confusing after a while.

Hoping to remove Fedora11 tommorrow and replace it with Kubuntu 9.04 as I am having software setup problems that seem to be a easier setup on Kubuntu.

Thank you

---

### Post by Metaljaz on 2009-08-23
This has been the easiest way for me:

If your results of typing lspci in a terminal window reveals something to the effect of Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02) 

Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it.
Make sure you unplug your wired connection.

---

