---
title: "cannot connect to particular wireless network that works fine on other computers"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by zachzach on 2010-04-09
I'm not a computer expert so bear with me...

For the last 3 days I have been unable to connect to my house's secured wireless network called "212". My laptop (running Ubuntu) detects the network (with strong signal), tries to connect, asks for the password, accepts the password, tries to connect for another few minutes, then asks again for the password, and on and on until after about 10 minutes it stops trying.

Obviously, this happens to everyone from time to time but now it is especially confusing for the following reasons:

-My computer has been able to connect to other (unsecured) networks within range.
-When I reboot my computer and start it up in Windows (I have a hard drive partition), it connects perfectly fine to "212". But I would prefer to run Ubuntu, which is unable to connect to "212". So it does not appear to be an issue with the hardware.
-My housemates' computers (all PC or Mac) have had no problems connecting.

I tried turning the router off and on.

I have been running Ubuntu and connecting to this wireless network with no issues for months now.

Advice?

---

### Post by bkratz on 2010-04-09
> **zachzach said:**
> I'm not a computer expert so bear with me...

For the last 3 days I have been unable to connect to my house's secured wireless network called "212". My laptop (running Ubuntu) detects the network (with strong signal), tries to connect, asks for the password, accepts the password, tries to connect for another few minutes, then asks again for the password, and on and on until after about 10 minutes it stops trying.

Obviously, this happens to everyone from time to time but now it is especially confusing for the following reasons:

-My computer has been able to connect to other (unsecured) networks within range.
-When I reboot my computer and start it up in Windows (I have a hard drive partition), it connects perfectly fine to "212". But I would prefer to run Ubuntu, which is unable to connect to "212". So it does not appear to be an issue with the hardware.
-My housemates' computers (all PC or Mac) have had no problems connecting.

I tried turning the router off and on.

I have been running Ubuntu and connecting to this wireless network with no issues for months now.

Advice?

Did you have an update recently? If you temporarily remove encryption from you AP, does it connect ok?  Do you know what your wireless card is?  If not, go to the terminal and enter in 

```
lspci
```

Read through the output or copy/paste it back here so someone else can.  Certain devices are having some difficulties, especially if you are using ndiswrapper ( which I doubt) following some recent updates. By the way that was a lowercase LSPCI earlier.

---

### Post by zachzach on 2010-04-09
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

My computer is fully updated.

Does "remove encryption from your AP" mean make the wireless an unsecured network? Because if so I can't try that at the moment because the wireless is not in my house, so it might be a while before I can get together with someone next door to remove encryption.

---

### Post by zachzach on 2010-04-09
OK I just tried connecting to another encrypted network whose password I was told, and it does not work either. So that seems to be the problem. What do I do?

---

### Post by bkratz on 2010-04-09
> **zachzach said:**
> OK I just tried connecting to another encrypted network whose password I was told, and it does not work either. So that seems to be the problem. What do I do?


Unfortunately I will be off-line for several days, but I did find a "bug" report

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/434342](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/434342)

where it mentions your device with issues regarding wpa encryption which several people seemed to solve by switching to wpa2 with aes encryption.  

Also, here is a list of "bugs" which you might find useful, perhaps one will have an answer for you.

[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=wpa+%2B+3945ABG&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=wpa+%2B+3945ABG&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)


Boy that was a long url, I hope it all shows up!

---

