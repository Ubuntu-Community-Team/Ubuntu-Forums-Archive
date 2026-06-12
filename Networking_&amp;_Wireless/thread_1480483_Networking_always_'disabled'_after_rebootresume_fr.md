---
title: "Networking always 'disabled' after reboot/resume from sleep"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by FiveSidedPoly on 2010-05-11
I've searched the forums already and didn't find much help, most of the threads were left unsolved, or didn't cover the same issue.

I recently decided to test Lucid on two newly built systems and have been fairly happy with it.  Until today that is and I'm at a loss to figure out what is the exact issue; I just don't have the experience with Ubuntu to dig too deep in this area.

The problem I am having is that each time one of these boxes goes to sleep or is rebooted the networking is 'disabled' under Network Manager.  The easy fix is just to select 'Enable Networking' but then I still have to manually select 'Auto Ethernet' and then the connection is fine.

Something I can say is that to my knowledge that the one box did not start doing this until I updated it today about 8hrs ago.  The other box I believe it started having this problem last Friday from what the user said, but for certain it is having the problem today.

If it helps the NICs are Realtek 8112L PCIe Gigabit LAN controllers on Asus M4A785-M mobos.

Thank you in advance for any help

---

### Post by FiveSidedPoly on 2010-05-11
Bump

Does anyone have a clue as to why this is happening?  Someone else posted a thread about networking being disabled after a reboot.

I hope I'm not missing something small.

---

### Post by HansCombee on 2010-05-23
Same issue here on an Asus 1005P netbook running Xubuntu 10.04.

Help anyone?

:guitar:

---

### Post by cabinetman on 2010-05-23
Did you try right mouse click on network manager icon/edit connections/click on auto etho0 or whatever is there/then click edit/and then click on connect automatically. If it is wireless then you do then same on wireless tab.

---

### Post by PvtPapa on 2010-06-30
> **cabinetman said:**
> Did you try right mouse click on network manager icon/edit connections/click on auto etho0 or whatever is there/then click edit/and then click on connect automatically. If it is wireless then you do then same on wireless tab.


Thats not the problem when I resume and I right-click on the network icon it says networking disabled and not the connection to the router.

Hope someone figures out the problem!

---

### Post by cabinetman on 2010-07-01
> **PvtPapa said:**
> Thats not the problem when I resume and I right-click on the network icon it says networking disabled and not the connection to the router.

Hope someone figures out the problem!


What version are you using?

---

### Post by sirwhiteout on 2010-11-06
Same problem on a Vaio Y Series. The wireless card is an Atheros Communications Inc. AR9285 Wireless Network Adapter.

The issue started on Lucid but persists after upgrading to Maverick.

---

### Post by Eklod on 2010-11-07
Same issue on my Dell Inspiron 2200, since I upgraded from Hardy to Lucid, except that it behaves other way.  Wireless gets re-enabled every time I boot or resume. Broadcom B43 wireless driver.   I do not have any wireless connection setup under Network.

---

### Post by sailor420 on 2010-11-11
Anyone every figure anything out regarding this? I'm having the same issue--wireless is disabled when machine wakes. BCM4312 w/ Broadcom STA drivers. Issue began after upgrading to 10.10.

---

### Post by sssent on 2011-01-02
I've just fixed a Realtek Ethernet card using the r8169 driver on Maverick by making it a suspend module as suggested in [this old bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288281").

To find out which driver your card is using, run
```
lshw -C network
```
and look for ```
configuration: driver=[yourdriver]
```

Then create/edit a file in /etc/pm/config.d/ with the line
```
SUSPEND_MODULES="[yourdriver1] [yourdriver2] ..."
```

---

### Post by archenroot on 2011-01-10
Hello sssent,

thank you for posting this information. I use Ubuntu Maverick and of course I use sometimes sleep mode, and always after wake up/resume the network manager is running, but when try to enable network via network manager nothing happen. trying to run 
```
 sudo service networking start
```doesn't work. the service is still in stopped status.
Next time I will try to use what you just proposed and post the result here.

Thank you.

Best regards,

Ladislav Jech

---

### Post by hashky on 2011-04-01
> **sssent said:**
> I've just fixed a Realtek Ethernet card using the r8169 driver on Maverick by making it a suspend module as suggested in [this old bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288281").

To find out which driver your card is using, run
```
lshw -C network
```
and look for ```
configuration: driver=[yourdriver]
```

Then create/edit a file in /etc/pm/config.d/ with the line
```
SUSPEND_MODULES="[yourdriver1] [yourdriver2] ..."
```


This worked for me.  I created a file suspend-resume.conf in /etc/pm/config.d.

In the file I put the following
SUSPEND_MODULES=r8169

Works every time.

I have a dual boot with Windows XP.  XP would not connect unless I unplugged the power cord before booting.

Network drive on Asus P7H55-M PRO motherboard.

This bug has been around for many years and should be addressed.

Ron Spruell

---

