---
title: "MAC Changing"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by G-Unot on 2008-12-17
Hi I'm doing an experiment in a lab I set up on my local area connection. I have other linux distros on different pcs that i am using, and i have all spoofed their mac addresses and connected sucessfully (none of these distros are ubuntu). However, on my ubuntu machine, i can successfully change the mac address but not connect to my AP using ifconfig, or macchanger. The hardware is not a problem, because i have successfully changed the same interface using a different distro on the same machine. So im not sure what im missing. 

So basic summary: ifconfig and macchanger will change the mac address of my bcm43xx card, but it won't connect to my AP afterwards.

Thanks in advance,
G-Unot

---

### Post by PoHandle on 2008-12-22
I have the same problem. I have a BCM4311 and I'm able to successfully change my mac, but when it comes time to connect to my AP, no dice.

I believe that this may be a problem with either the new Broadcom STA drivers that became available with 8.10, or a problem with nmapplet 0.7.0.  Back in previous versions of Ubuntu, I was able to use macchanger and connect to my network with the ndiswrapper setup and nmapplet 0.6.4.  I've been looking for a workaround, and I may try using ndiswrapper in 8.10 to install the wireless drivers and see if that works.

I don't want to go back to using ndiswrapper, because my wireless gets in a bad mood for certain APs, like the one a my buddy's house or the one at school.  I was so happy when 8.10 allowed my wireless to work right off the bat, but it's a shame that I can't change my mac and connect to a network.

---

### Post by PoHandle on 2008-12-22
I'm going to go ahead and say the problem is the network manager applet.  I tried using ndiswrapper with my wireless card and was unable to connect to my network with an altered mac.  I also used another card (a D-Link DWA-643) which I have had great success using in the past with madwifi, and was still unable to connect.

I will try to downgrade nmapplet and see if that works.  Other than that, we may have to wait for an update.

---

### Post by PoHandle on 2008-12-30
I take back what I said in my last post... (About network-manager being the problem)

After playing around a little, I found that macchanger interferes with dhclient, making it impossible to get an IP address from the network.  I ran into a similar problem with dhclient when attempting to use wicd as my network manager to see if that would solve the problem of being unable to connect with a spoofed mac.  It inadvertently show me what the real problem was with trying to connect to a network with a changed mac address. 

I suppose the question now is, How can we get dhclient to successfully obtain an IP address in this situation?

---

### Post by lensman3 on 2008-12-30
When you load the driver, can you pass the desired MAC address to it?  This will probably require you to play with modprobe.conf and the aliases of eth0.

Once upon a time, there used to be a program called "rarp" for reverse arp.  It was used for booting a system given an IP address and it would return a MAC (I think).

Sorry I can't help you too much.  I think the problem is the emulation software the windows driver is being controlled by.

---

### Post by PoHandle on 2009-01-01
After playing around with another wireless card (a DWA-643 with Atheros chipset, running with madwifi) I found that you must change the mac address before the interface is loaded.  For the Atheros card, it was as simple as
```
sudo wlanconfig ath0 destroy
sudo macchanger -A wifi0
sudo wlanconfig ath0 create wlandev wifi0 wlanmode managed
```
with ath0 being the interface used for connecting to the network, and wifi0 being the parent interface.

It's not that simple for the BCM4311 on eth1 because wlanconfig returns that the card does not support the operation.  I used to be able to get away with
```
sudo ifconfig eth1 down
sudo macchanger -A eth1
sudo ifconfig eth1 up
```
But that no longer works.
I've also tried to assign a random mac when the driver loads with 
```
sudo rmmod wl
sudo modprobe wl | sudo macchanger -A eth1
```
but that doesn't work either.

I'm thinking of purchasing an Atheros mini PCIe adapter because I'm finally seeing why Broadcom is so unpopular amongst Linux users.  Any suggestions?

---

### Post by GuyWires on 2009-02-15
Anyone figure this out?

I think they switched the driver from madwifi to the compat-wireless set because the madwifi-tools don't work on this driver.

I say this because I heard that you need to destroy the VAP (i.e. ath0) and change the physical interface MAC (i.e. wifi0) then remake the VAP with the altered wifi interface. so i tried wlanconfig on wlan0 but I just got a message "Not Supported".

madwifi made interface names ath0 & wifi0 but these drivers make wlan0 and wmaster0 which is what happened when I used compat-wireless eons ago on a different install...

so anyways, i need this feature re-enabled ASAP!

---

### Post by Alfred_McGee on 2009-10-07
I have connected to networks under a spoofed MAC address using a number of different wifi cards, including a bcm43xx. I believe that was when I was using Ubuntu Hardy, or perhaps Intrepid. With Jaunty, regardless of which wifi card I use, once I fake my MAC, I cannot connect to any network until I reset my MAC to its default value. Is it time to change distros?

EDIT: Actually, it appears that Ubuntu is not the problem. I have the same inability to connect under Knoppix 6.0.1, and using different wifi cards, and even when using Wicd instead of the Gnome Network Manager. It appears, therefore, that there is some deeper problem/regression. Anybody have a clue?

---

### Post by Adanufgail on 2010-01-11
Has any progress been made on this front? I am having the same problem on my netbook. I can change my MAC, but I cannot connect with it.

---

### Post by ironclaw on 2010-01-21
Hi Adanufgail. Which Ubuntu release are you on?

I experienced the problem with Ubuntu 9.04 on an Asus Eee 900 netbook, but the problem seems to go away with Ubuntu 9.10. It also works fine on BackTrack 4.

---

### Post by Adanufgail on 2010-01-21
I'm using 9.10 Netbook Remix.

---

### Post by ihadwindows on 2010-01-26
I am having the same problem with Ubuntu 9.10. I can spoof my MAC with ifconfig and macchanger, but I cannot connect to internet after that. Even when I change my MAC back, I need to restart OS if I want to access internet. Can anyone help?

---

### Post by danmiddle2 on 2010-02-23
> **PoHandle said:**
> After playing around with another wireless card (a DWA-643 with Atheros chipset, running with madwifi) I found that you must change the mac address before the interface is loaded.  For the Atheros card, it was as simple as
```
sudo wlanconfig ath0 destroy
sudo macchanger -A wifi0
sudo wlanconfig ath0 create wlandev wifi0 wlanmode managed
```
with ath0 being the interface used for connecting to the network, and wifi0 being the parent interface.

It's not that simple for the BCM4311 on eth1 because wlanconfig returns that the card does not support the operation.  I used to be able to get away with
```
sudo ifconfig eth1 down
sudo macchanger -A eth1
sudo ifconfig eth1 up
```
But that no longer works.
I've also tried to assign a random mac when the driver loads with 
```
sudo rmmod wl
sudo modprobe wl | sudo macchanger -A eth1
```
but that doesn't work either.

I'm thinking of purchasing an Atheros mini PCIe adapter because I'm finally seeing why Broadcom is so unpopular amongst Linux users.  Any suggestions?

I have the same problem. I am running Hardy. I have an Atheros card. This so nearly works for me, but I need to use a specific MAC not a random one. I assign it to wifi0 which works, ath0 then gets created with a slightly different mac to the one I assigned.

e.g. if I assign wifi0 as 00:ff:ff:ff:ff:ff, ath0 would be 01:ff:ff:ff:ff:ff

Any ideas?

---

### Post by kirb3 on 2010-06-11
This happened to me as well with a Linksys USB Wi-Fi adaptor.  I took it back to the store because I thought the adaptor was at fault, so I don't have the specific serial number, but it was the really popular one -- WSUG<something>.  I have been looking for a USB Wi-Fi adaptor that will allow me to change the MAC and still connect afterwards, but haven't found one yet.

Edit: Forgot to mention, my laptop has a Broadcom chip internally.  That one doesn't even let me change the MAC at all.  I just got "too many files open" errors (even though I had the limit set to unlimited) or "operation not permitted."

---

### Post by cryppie on 2011-06-15
I'm also experiencing this problem using Debian 6.0.1a (2.6.32-5-686) on a netbook with a broadcom internal wireless card (BCM43224 w/brcm80211 - cfg80211 - mac80211)and a alfa awus036h (rtl8187) usb wireless adaptor.

As soon as the mac is changed on either one, dhcp is broken.  Nothing fixes this except a reboot.  Like another mentioned, it works fine on backtrack.

I noticed that many of the people experiencing this are on netbooks with a broadcom card.

I don't expect an answer or a remedy will posted here, just leaving more info for others that google about this issue.

---

### Post by lisati on 2011-06-15
I don't have an answer but a question: Why?

For some of us, talking about spoofing MAC addresses looks a bit suspicious and raises questions about the legality and morality of the intent, e.g. breaking into someone else's network without their permission. Backlash from that sort of thing is something we don't want here.


(And this thread is a year old.)

---

