---
title: "WiFi Problem"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by ConfickerLove on 2012-02-20
I learned all I could about Win and wanted a new challenge so I installed kubuntu 10.4 or 10 because I prefer KDE and now I can't seem to connect to my home network.
I have tried many things and have been searching for over a month so I decided to get some help.
The wireless works on anything unsecured so I do know it works but on WEP 64bit it doesn't want to allow me to put in either my passphrase or my hex key. 
My wireless adapter is the: Wifi Link 1000 Series by Intel
My machine is x64 bit
i5 CPU, 4Gig RAM
I am running VMWare Workstation and ESET NOD32 AV and the wireless manager is the default.
I am on a new work deadline so the faster I can get up and running the better.
 
On a secondary note I do ask that no comments against running an av be mentioned at all. I study Win, Mac, Linux, and Mobile Malware and am aware of what is said on forums. I appreciate that.
 
If you need anything extra from me please don't email me just post as I am using a friends computer and don't trust anyones but mine for any passwords. I will check this post multiple times a day until I get this figured out
Thanks for understanding and I hope to hear from someone soon.
Thanks for your time,
ConfickerLove

---

### Post by SeijiSensei on 2012-02-20
Is Kubuntu running as a VM guest or is it the host?  If it's the guest, it usually doesn't communicate directly with the wifi AP at all.  The VM host should be making that connection and the Kubuntu guest should be using the virtual interface provided by VMWare to connect through the host.

---

### Post by ConfickerLove on 2012-02-21
Its the host. VMware is just for my malware labs

---

### Post by SeijiSensei on 2012-02-21
Have you tried using WPA-PSK2 instead of WEP?  I wouldn't use WEP unless I absolutely had to support hardware that could not use WPA.

---

### Post by ConfickerLove on 2012-02-23
I would if I had a choice, I have the time warner wep and I believe everyone knows what my key is. Unfortunantly I am unable to because of my living situation. Is there any chance that using WPA2-Personal would work?

---

### Post by Gregory Lee on 2012-02-23
> **ConfickerLove said:**
> Is there any chance that using WPA2-Personal would work?
I would guess not.  I use a WEP 64-bit key for my local network -- works fine on Ubuntu and other devices.  A WEP key can either be alphabetic or in hex -- is it possible you entered it in one form on your router and a different form on the Ubuntu system?

---

