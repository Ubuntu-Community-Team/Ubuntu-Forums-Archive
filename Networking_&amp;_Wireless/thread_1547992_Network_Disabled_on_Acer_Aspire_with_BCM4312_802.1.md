---
title: "Network Disabled on Acer Aspire with BCM4312 802.11 b/g (Broadcom)"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by iamnotloggedon on 2010-08-07
I'm running Kubuntu and Windows on the same machine but when I swap over to Kubuntu I can't get the wireless to work. The lshw command returns network disabled but the machine can see that there is a wlan0 connection.

I've been trying to install the broadcom Linux driver from their site but the instructions fall apart at step 3: cd bnx...version/ ( directory just created by tar). I'm guessing this is because I don't have a Live CD (after almost a week of trying to burn a disc I just broke down and got Wubi) but that doesn't change the fact I have no idea what to do now or if this will even work.

If it makes any difference, the wired connection will also occasionally die mysteriously after about 30-60 minutes of use and refuse to re-activate but work fine when I switch over to Windows or just plug it into the router.

---

### Post by iamnotloggedon on 2010-08-07
Never mind I got it. I didn't realize that Kubuntu has a GUI for installing drivers. From there it was a simple matter of point-and-click since I had already installed the driver at some point obviously. Thanks everybody who helped out...I think...

---

### Post by WJason on 2010-08-25
No, wait!  I have the same problem with Ubuntu.  How did you fix this?

---

### Post by iamnotloggedon on 2010-08-25
> **WJason said:**
> No, wait!  I have the same problem with Ubuntu.  How did you fix this?
  Sorry Jason but I'm on Kubuntu. First and foremost and looked into the other threads regarding BCM4312 802.11 b/g Broadcom routers. As it turns out there's a driver for the router. Broadcom's website has one that I was able to get about halfway through installing before their instructions became nullified. Soon afterwords I noticed a program called something like "hardware manager" or "driver manager" or something like that.

Turned out it had been waiting for me to click "install" on the driver to complete the process. I don't know if Kubuntu retrieved the driver or if it was the result of my attempt to follow Broadcom's instructions but once I installed it and rebooted the machine it hasn't given me a problem since.

---

