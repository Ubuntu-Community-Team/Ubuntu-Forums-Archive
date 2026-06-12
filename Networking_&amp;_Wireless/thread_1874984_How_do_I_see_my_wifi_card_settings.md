---
title: "How do I see my wifi card settings ?"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by BADGER.BRAD on 2011-11-04
Hello All,

I have a problem with the fact my new Playstation 3 does not see my wifi ,as a result of this I need to look at the settings of my pci wifi card in order to see if the settings are incorrect. Can I do this in Ubuntu and how ?

Many thanks all

Brad

---

### Post by jonobr on 2011-11-04
What settings are you looking for?

You can open a terimnal windows 
(application-> accessories

and tupe 
ifconfig 

look for wlan 0

if you enter
lshw -C network and lshw it should show you settings also,

However, if you cant see the ssid on your PS3 then either its not being broadcast, or your out of range or your wireless on the PS3 is a dud

---

### Post by BADGER.BRAD on 2011-11-04
Thanks for the info much appreciated, I wondered if the playstation was only able to use wireless N but I have since found this not to be the case , I think we just have a dud as another issue has turned up with it.

Thanks again.

Brad

---

### Post by haqking on 2011-11-04
> **BADGER.BRAD said:**
> Hello All,

I have a problem with the fact my new Playstation 3 does not see my wifi ,as a result of this I need to look at the settings of my pci wifi card in order to see if the settings are incorrect. Can I do this in Ubuntu and how ?

Many thanks all

Brad

what does your Ubuntu PCI wireless card have to do with your PS3 no seeing your wifi ?

You need to look at your wireless device (router) not your Ubuntu machines WIFI card.

---

### Post by BADGER.BRAD on 2011-11-04
I have no router in my wifi network, I use a wired connection to my pc via a modem and then a wireless card in the pc to allow other devices to have access to the inet !

---

### Post by jonobr on 2011-11-04
Im guessing you do.......

From the wiki
*A router is a device that forwards data packets between computer networks, creating an overlay internetwork.*

Your PC is routing packets between your home network and the wireless network.

---

### Post by BADGER.BRAD on 2011-11-04
That's correct the PC is acting as a router and as the Wifi card is the thing which would limit the wireless type those are the settings I need to look at. For your benefit I will refrase my coment about not having a router ( which I'm sure everyone else would understand what was meant)  I do not have a stand alone router ! Thanks for all your help in not helping at all, now do us all a favour and screw up your own internet connection.

---

### Post by haqking on 2011-11-04
> **BADGER.BRAD said:**
> That's correct the PC is acting as a router and as the Wifi card is the thing which would limit the wireless type those are the settings I need to look at. For your benefit I will refrase my coment about not having a router ( which I'm sure everyone else would understand what was meant)  I do not have a stand alone router ! Thanks for all your help in not helping at all, now do us all a favour and screw up your own internet connection.

is that directed at me ? I am trying to help.

as are most people on here, we need better pictures of configurations and setup to be able to help fully.

With it being on your PC then i am presuming you have a ad-hoc network setup.

See here [http://www.ehow.com/how_6808376_can-connect-ad-hoc-network_.html](http://www.ehow.com/how_6808376_can-connect-ad-hoc-network_.html)

---

### Post by jonobr on 2011-11-04
Nah,  I think it was aimed at me.....

---

### Post by BADGER.BRAD on 2011-11-05
The comments were not aimed at you Haqking, Help is always appreciated when help is given. I have since found that as suspected I have a duff Playstation as I tested against another which found my network no problem.

Thanks 
Brad

---

### Post by haqking on 2011-11-05
> **BADGER.BRAD said:**
> The comments were not aimed at you Haqking, Help is always appreciated when help is given. I have since found that as suspected I have a duff Playstation as I tested against another which found my network no problem.

Thanks 
Brad

cool, glad you got it sorted.  Remember to use thread tools to mark it as solved.

Cheers

---

