---
title: "[FOR US NOOBS] - 11.10 Broadcom wifi problem SOLVED"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by winterlight on 2012-01-08
In both 11.10 and 11.04 it's been impossible for me to get my laptop (a DELL XPS with the broadcom 4311 wifi adapter)

I think i found the solution.  This is for all the ubuntu users like me (noobius maximus) so please, no flaming by the super-experts.

It basically involves deleting all wifi drivers, reinstalling some wifi drivers and then refreshing your wifi config info.  Just giving ubuntu a fresh start for Wifi...

You will need a wired connection to do this though.

I'm going to walk through symptoms first them my solution:

SYMPTOMS
- "device not managed" message in wifi
- blank wifi icon on the top line
- existing wifi profiles in the "wireless" tab of "edit connections" from the wifi icon
- upgraded from a previous version of Ubuntu
- when booting in 11.10 the machine stays on the screen with "ubuntu" and the 5 dots for a long time and takes a long time to get through network configuration (which should normally be instant).


SOLUTION STEPS
- Go to Synaptic Package Manager (box with green arrow)
- search for "broadcom" and in the resulting list "Mark for complete removal" everything 
- search for "b43" and in the resulting list "Mark for complete removal" everything
- search for "ndis" and in the resulting list "Mark for complete removal" everything
- reboot

- Go back to Synaptic Package Manager 
- search for "b43" and in the resulting list "Mark for installation" two things:  1) "firmware-b43-installer"   2) "b43-cutter"
- reboot

- open a terminal window
- type "sudo -i"  (careful now, you can do anything on the system including kill it)
- type "gedit"
- use "open" in the text editor and click on the "file system" icon on the list on the left
- navigate to  etc/network/  and open the "interfaces" file in that directory
- delete the paragraph that deals with your wireless adapter (specified "wlan0")  the paragraph should say something about an SSID and a have large hexadecimal number
- save and close this file

- click on the wifi icon and "Edit Connections" and then the "Wireless" tab
- DELETE all the profiles in here
- reboot
-(the above three steps seems to have been the magic bullet)

My wifi started working again at this point.  I just had to re-enter my Wifi networks and I was on the intarwebz again!

I hope this helps, it really shook my confidence and love for Ubuntu when this problem manifested in v11.  Hope they the developers get it right for v12.

---

### Post by carl4926 on 2012-01-08
I guess that's one way.

I just keep a copy of the firmware on a pen drive and drop the b43 folder in /lib/firmware

Job done

Don't accept any offer of Additional Drivers from the system. They are not open and not required. Least not for my or your device.

---

### Post by bkratz on 2012-01-08
Here is the best source for information on the BCM4311 in both 11.04 and 11.10.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by mörgæs on 2012-01-08
Moved to the networking forum.

---

