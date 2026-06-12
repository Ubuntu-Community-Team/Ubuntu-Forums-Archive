---
title: "Modem reports &quot;error&quot; when checking for SIM"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2011-05-31
Hi,

Using a Vodafone K3806 USB modem on Ubuntu 9.10, trying to connect with Sakis3g (I already know from previous experience that VMC is out of the question), I get the following message: "Modem responded "ERROR" when checking fror SIM".

Any help greatly appreciated.

---

### Post by sanderj on 2011-05-31
> **rdh61 said:**
> Hi,

Using a Vodafone K3806 USB modem on Ubuntu 9.10, trying to connect with Sakis3g (I already know from previous experience that VMC is out of the question), I get the following message: "Modem responded "ERROR" when checking fror SIM".

Any help greatly appreciated.

There's a typo in your post: "fror". Not a problem for humans, but probably a problem for search engines.

So: did you Google the (exact) error message?

I would do this:
- post the modem's relevant info / id from lsusb here, and google for it.
- live-boot Ubuntu 11.04 and see it version gives better results.
- what does the ethernet/wireless/mobile icon in the upper right corner tell you about the USB modem?

---

### Post by rdh61 on 2011-06-01
Thanks for your answer. Yes, I have googled the exact error message (without typo!). There are two or three people out there with the same problem  (all quite recent), but I couldn't find a solution.

Here's the lsusb:

 robert@robert-desktop:~$ lsusb
    Bus 001 Device 040: ID 12d1:14ad Huawei Technologies Co., Ltd. 
    Bus 001 Device 036: ID 125f:c03a A-DATA Technology Co., Ltd. 
    Bus 001 Device 035: ID 058f:6254 Alcor Micro Corp. USB Hub
    Bus 001 Device 004: ID 0d49:7450 Maxtor 
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


And this is after I eject the device:


  
robert@robert-desktop:~$ lsusb
    Bus 001 Device 041: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
    Bus 001 Device 036: ID 125f:c03a A-DATA Technology Co., Ltd. 
    Bus 001 Device 035: ID 058f:6254 Alcor Micro Corp. USB Hub
    Bus 001 Device 004: ID 0d49:7450 Maxtor 
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam
    Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    [FONT=&quot]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]   
  In both cases I get the same error message.

The network connection icon in the upper right corner does not list my mobile broadband connection even though I have added it correctly.

I have stuck with 9.10 as it seems to me to be the most stable, trouble free system I have tried, and it does everything I want it to do... until now. I know from experience that upgrading ALWAYS brings new problems, so I'd prefer to leave that as the last option.

---

### Post by sanderj on 2011-06-01
@ lsusb: strange: the number of devices stays the same, only the Huawei modem changes it's ID? 

For the test, you don't need to upgrade nor install 11.04; I said "live-boot Ubuntu 11.04" :-) 
So, burn a CD (or USB-stick) with Ubuntu 11.04, boot it into live-test-mode (do not install), and see the result with your USB-modem.


BTW: Eventually you will probably need to install a newer Ubuntu version; 9.10 desktop is not supported anymore since April 2011.

---

### Post by rdh61 on 2011-06-01
OK, thanks for the clarification. I'll give the live CD a try, then post back.

---

### Post by rdh61 on 2011-06-02
Well, 11.04 seems to have a problem with my graphics (desktop distorted and flaky), a problem I was already having when I tried 10.04 - which reminds me of one reason I stuck with 9.10.
 
On the other hand my USB modem works out of the box with 11.04.
 
So it's a question of lesser evils.
 
I would really like to get this thing working with the system that has served me well up till now (9.10) and not to have to put up with a crappy desktop.
 
Any further suggestions greatly appreciated.

---

### Post by rdh61 on 2011-06-02
Tried 10.10. Wonder of wonders: no installation problems, no graphics problems (as long as I take out my Nvidia graphics card and only use the onboard card), and my modem connects out of the box. Something unique these days. I'll mark the thread solved.

---

