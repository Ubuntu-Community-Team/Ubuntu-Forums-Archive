---
title: "No Wireless"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by Hman242 on 2010-06-14
I have installed Ubuntu mom's laptop and the wireless isn't working. Before this it had the Ubuntu 10 Beta 2 on it and the wireless worked fine. My wireless is Broadcom BCM4322 which is on an HP laptop.

Normally to get it working I have to install the proprietary driver, but it doesn't show any. When opening Hardware Drivers it says "Downloading package indexes failed, please check your network status. Most drivers will not be available."

---

### Post by purelinuxuser on 2010-06-14
> **Hman242 said:**
> Normally to get it working I have to install the proprietary driver, but it doesn't show any. When opening Hardware Drivers it says "Downloading package indexes failed, please check your network status. Most drivers will not be available."

Did you have an active Internet connection?  You can plug into Ethernet.

---

### Post by Hman242 on 2010-06-14
I had the laptop plugged in with an ethernet cord, yes.

---

### Post by purelinuxuser on 2010-06-14
While plugged into Ethernet, try running Update Manager and then trying to install the driver again.

---

### Post by JakeFrederix on 2010-06-14
Have you tried installing the backport-modules for wireless?

---

### Post by Hman242 on 2010-06-15
> **purelinuxuser said:**
> While plugged into Ethernet, try running Update Manager and then trying to install the driver again.
I have tried that, but the driver still doesn't appear and I get that same error message.

---

### Post by paul_harris on 2010-06-15
> **JakeFrederix said:**
> Have you tried installing the backport-modules for wireless?
 
what are the backport-modules by the way, new lingo to me.
cheers

---

### Post by elkanji on 2010-06-15
yea what's backports? is it the repositories that aren't enabled by default?

---

### Post by purelinuxuser on 2010-06-15
> **Hman242 said:**
> I have tried that, but the driver still doesn't appear and I get that same error message.

Ouch, looks like you'll have to compile the driver manually!  You can find the binary download and installation instructions [here]("http://www.broadcom.com/support/802.11/linux_sta.php").

---

### Post by purelinuxuser on 2010-06-15
> **elkanji said:**
> yea what's backports? is it the repositories that aren't enabled by default?

"Backports" are packages that are more up to date than the ones shipped with Ubuntu, in this case wireless-related modules.  However, they are not as stable, and in this case, won't help at all.

---

### Post by JakeFrederix on 2010-06-15
All I know is that my wireless didn't work on my previous laptop, and that after installing the backports, it did. I would not be so unkind as to give advice intended only to keep you busy.

Kind regards,
Jake

---

### Post by purelinuxuser on 2010-06-15
> **JakeFrederix said:**
> All I know is that my wireless didn't work on my previous laptop, and that after installing the backports, it did. I would not be so unkind as to give advice intended only to keep you busy.

Kind regards,
Jake

It's all right, you were just trying to be helpful :) The problem is that his BCM4322 wireless card is 802.11n, and Broadcom 802.11n cards are not supported by any open-source Linux drivers (which backports just grabs later versions of).

---

### Post by harry003 on 2010-06-15
I spent weeks trying to make an Atheros card work in Lucid because I had Windows 7 installed. Backports, madwifi, not of that stuff worked.

When I found the Windows XP driver, copied it into the Ubuntu partition, and ran it under ndiswrapper, bingo, it worked right away.

---

