---
title: "WiFi Troubles"
date: 2006-04-20
forum: Networking &amp; Wireless
---

### Post by kyoushu on 2006-04-20
I just recently installed Ubuntu on my laptop.  The wifi does not connect.  I typed in the WEP code and the SSID but it does not connect.  If I plug in my laptop, via a regular ehternet cable, I activate the eth0 and it works.  I have a truemobile 1150 wireless card.  Can anyone help me with this problem? Thanks in advance.

---

### Post by verbalshadow on 2006-04-20
* Some Dells boot with the radio disabled depending on the BIOS config. Fn-F2 toggles the wireless.
* What does iwconfig show?

check what chipset it is running?
if its boardcom chipset the search the forums for a howto

* if orinoco/prism/athero/etc make the proper modules are loaded

---

### Post by kyoushu on 2006-04-22
iwconfig just shows that none of the different eth0, eth1 etc aren't active.  And I don't understand the last 
> * if orinoco/prism/athero/etc make the proper modules are loaded

---

### Post by kyoushu on 2006-04-22
Okay, here's the info from typing iwconfig into the terminal:
> lo        no wireless extensions.


eth0      no wireless extensions.


eth1      no wireless extensions.


eth2      IEEE 802.11-DS  ESSID:"NETGEAR2"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 44:44:44:44:44:44
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


---

### Post by kyoushu on 2006-04-23
Ok, I followed [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?) and understood how to everything and was, most likely doing everything correctly.  I couldn't find my exact driver on the list of drivers, so I tried out a number of other drivers that were similar to mine.  None worked.  I then went onto my other windows computer, put the Truemobile 1150 series Wireless LAN cd into the cd drive and explored it.  I found the need .inf file and saved it onto a flash drive.  I took the flash drive, put it into my laptop and tried using the .inf file in the ndisgtk thing.  Didn't work.  I then put the cd into my laptop and tried installing it onto the laptop with wine.  I accidently installed the files onto the C:\ drive in wine, which, I assume cannot be accessed through ubuntu.  So I deleted the folders that were installed through the cd, and then tried installing it again, but in Ubuntu(My Documents).  It then says that I already have it installed(I didn't actually uninstall it).  
Is there any way I can be able to install it again, but on ubuntu, or does anyone have the needed drivers(Dell TrueMobile 1150 Series Mini PCI Card)?

---

### Post by spd106 on 2006-04-24
[QUOTE=kyoushu]iwconfig just shows that none of the different eth0, eth1 etc aren't active.  And I don't understand the last[/QUOTE]

According to this wiki page [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")
your card has a native driver. If you type **lsmod** at the terminal you should see  an entry for orinoco_cs. If not try **sudo modprobe orinoco_cs**. It should just work. Have you tried scanning for APs?

---

### Post by kyoushu on 2006-04-24
I see an entry for orinoco_cs.  Then what do I do?

---

### Post by mulder_edu on 2006-04-25
I'm having trouble with the same card.

---

### Post by mulder_edu on 2006-04-25
I don't understand any of this lingo. I'm a recently converted Windows user. Could you give a little more explanation?:-k

---

### Post by kyoushu on 2006-04-26
I too just converted to Linux and and am currently using windows(and propably will always considering I haven't gotten much help on this), but after using the livecd for months and installing software(automatix etc) on it, and eventually understood this "lingo".  Anyway, if anyone knows how to help me, so that, I can finally use ubuntu with internet, then I would truly appreciate it, and propably,mulder_edu would to. Thanks in advanced.

---

### Post by kyoushu on 2006-04-26
Well, supposedly, Linux supports my card wit Orinoco([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html)](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html)).  But, I don't know how to install it.  If anyone can tell me, that'd be a HUGE help.

---

### Post by kyoushu on 2006-04-28
Anyone....?

---

### Post by cvmostert on 2006-04-29
[QUOTE=kyoushu]
eth2 IEEE 802.11-DS ESSID:"NETGEAR2" Nickname:"HERMES I"
Mode:Managed Frequency:2.462 GHz Access Point: 44:44:44:44:44:44
Bit Rate:2 Mb/s Tx-Power=15 dBm Sensitivity:1/3
Retry limit:4 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=0/92 Signal level=134/153 Noise level=134/153
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
[/QUOTE]

this output of yours show that your card is being seen and that the wireless network is being seen as NETGEAR2, i think the only thing you should do is activate eth2 at your network configuration settings... should work... normally does for me.

did you acually activate the card at your network settins...? system -> admin ->networking?

---

### Post by kyoushu on 2006-04-29
Yes, I did.  I put in the info NETGEAR 2 and my WEP code.

---

### Post by el duderino on 2006-04-30
You have tried it with the WEP turned off right?

I'm a newbie too or I would offer more. 

It seems there a quite a few users having difficulties getting their WIFI cards to work well.

---

### Post by kyoushu on 2006-04-30
No, I never tried with the WEP off.  What would be the point of that?

---

### Post by mulder_edu on 2006-05-12
What's a WEP?
Some cards are suposedly working out of the box. I think I'll just buy a new one.

---

### Post by captylor on 2006-05-13
If I am not wrong, WEP stands for Wired Equivalent Privacy - a method of encrypting your wireless channel communications. This is usually configured on your wireless access point.

I recently managed to get my wireless working after I have changed the encryption key from "Shared" to "Open". Maybe this will help in your case.

---

