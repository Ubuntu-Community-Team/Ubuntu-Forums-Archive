---
title: "No bcm4306 drivers for Intrepid"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by DaleFarrell on 2008-12-06
Intrepid seems to have started ndiswrapper and fwcutter by itself.
I can see wap's, and I can ping mine.
"Hardware Drivers" says I have activated a Broadcom B43 wireless driver, but
"Windows Wireless Drivers" shows none loaded! I am stopped at the repeating
authentication step. Spent all day and just screwed it up, so I reinstalled.
Can I download the inf and sys files? The wired connection works. Dale.

---

### Post by superprash2003 on 2008-12-06
are you using WPA authentication?

---

### Post by DaleFarrell on 2008-12-07
yes. for last hour I have been looking for .inf and .sys drivers

---

### Post by kevdog on 2008-12-07
Why aren't you using the b43 driver?

---

### Post by Ayuthia on 2008-12-07
Before you start looking for .inf and .sys files, you might want to test the b43 driver first like kevdog recommended.  You might start off with trying to connect without encryption (just to see if the driver works).  Then if it works, come back and we can see if we can get it to work with encryption for you.

---

### Post by divague on 2008-12-07
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by DaleFarrell on 2008-12-07
HardwareDrivers says b43 is activated, but WindowsWirelessDrivers shows
no drivers. Ndiswrapper -l returns absolutely nothing, returns to next command line. Some sites have said for the revision 3 card the STA driver should be used, but I don't know. Have tried turning off the routers security, no luck. Have reloaded WPA Supplicant. Am still using NetworkManager, as Wcuid didn't help. I will try everything you have suggested. I have read all your reply's to many others so I really feel confident. Thanks, Dale.

---

### Post by superprash2003 on 2008-12-08
test with WEP or no encryption and see if it works..

---

### Post by Ayuthia on 2008-12-08
> **DaleFarrell said:**
> HardwareDrivers says b43 is activated, but WindowsWirelessDrivers shows
no drivers. Ndiswrapper -l returns absolutely nothing, returns to next command line. Some sites have said for the revision 3 card the STA driver should be used, but I don't know. Have tried turning off the routers security, no luck. Have reloaded WPA Supplicant. Am still using NetworkManager, as Wcuid didn't help. I will try everything you have suggested. I have read all your reply's to many others so I really feel confident. Thanks, Dale.

Just to let you know, the STA (wl) driver does not work with the 4306 card.  I have a 4306 rev 03 card and did try it out once just to verify (it did not work) and I also looked at the modinfo for the driver and it does not list the card either.

---

### Post by DaleFarrell on 2008-12-09
I set up another router with no security enabled and same problem. I am using Ndiswrapper and Fwcutter at the same time because that's the way the HardwareDriver applet did it. Shouldn't there be SOME driver showing in WindowsWirelessDrivers?   Thanks for hangin with me. Dale.

---

### Post by Ayuthia on 2008-12-09
Hardware Drivers will activate the b43 driver by installing the firmware using b43-fwcutter.  However, it does not control or blacklist ndiswrapper for you.  If you install ndiswrapper and activate the b43 driver in Hardware Drivers, you will have the two drivers conflicting with each other.  If you want to use ndiswrapper, you will have to disable the module through Hardware Drivers.

Windows Wireless Drivers should show that the hardware is present if has the correct Windows driver installed.

---

### Post by DaleFarrell on 2008-12-10
Aha! thank you. I will probably remove fwcutter as I have read that Ndiswrapper gives higher network speed. By getting rid of one or the other I should have some driver show up in WindowsWirelessDrivers. I have never read anything remotely resembling this problem, AND your insightful answers. Dale.

---

