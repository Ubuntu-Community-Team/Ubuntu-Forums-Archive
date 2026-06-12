---
title: "Wireless problems"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by Roaming_Roman on 2011-08-02
I'm having an issue getting my wireless internet to work, I'm running Ubuntu Unity(11.04) and I have tried absolutely everything on this site to no avail. I've tried NDISgrabber, Windows Wireless Drivers, everything I know, and that I've found on here, and nothing works. The drivers ARE installed(Thanks to Windows Wireless Drivers). But in the top left, it says Firmware Missing or something like that; I just checked while writing this, and it's not even there now... I'm hardwired right now, and I'm using a Dell Inspiron Mini 10v. Here is my wireless card info from the terminal:


00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Dell Device 02f4
    Flags: medium devsel, IRQ 10
    I/O ports at 18c0 [size=32]
    Kernel modules: i2c-i801

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card
    Flags: fast devsel, IRQ 17
    Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: ssb

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Dell Device 02f4
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at 2000 [size=256]
    Memory at f0510000 (64-bit, prefetchable) [size=4K]
    Memory at f0500000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at f0520000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169


Can someone please help me with this? I've been trying for 5 hours now, and nothing has worked.

---

### Post by lordleemo1 on 2011-08-02
Try having a look here
[http://ubuntuforums.org/showthread.php?t=1352270](http://ubuntuforums.org/showthread.php?t=1352270)

sudo apt-get install bcmwl-kernel-source

---

### Post by Roaming_Roman on 2011-08-02
It says it's unable to locate the package? :|

---

### Post by lordleemo1 on 2011-08-02
> **Roaming_Roman said:**
> It says it's unable to locate the package? :|

1) Open Synaptic Pacakage Manager
2) Ensure 11.04 LiveCd is in CD drive
3) Settings > Repositories > Ubuntu Software
4) Check the installable from cd and close
5) Refresh
6) Search for "bcmwl-kernel-source"
7) Mark for installation
Install it
9) Reboot computer

As szated from the link i provided you,hope that helps..

---

### Post by wildmanne39 on 2011-08-02
Hi, you do not need ndiswrapper or windows drivers.

You do not need the bcmwl-kernel-source in unity.

Please remove them and any driver or firmware you have installed in synaptic by typing bcm into the search window in synaptic and remove the ones that have broadcom or bcm or sta in them, then restart your computer.

Then run this command in a terminal
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer
```
then disconnect your wired connection and restart your computer and it should work, if not we need to most likely blacklist some drivers that you have installed.
Thank you

---

### Post by trooperchix on 2011-08-03
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/")

It works.  Just remember to do a complete shutdown then restart otherwise it won't work.  Saved my behind so much I'm trying to get the word out.  Enjoy!

Be sure to disable the proprietary drivers option under software sources or update manager will update your driver right back to the one that doesn't work.  Go to Update Manger.  At the bottom left hit the settings button.  It's under the Ubuntu Software tab, right in the middle of the page.

---

### Post by Roaming_Roman on 2011-08-03
> **wildmanne39 said:**
> Hi, you do not need ndiswrapper or windows drivers.

You do not need the bcmwl-kernel-source in unity.

Please remove them and any driver or firmware you have installed in synaptic by typing bcm into the search window in synaptic and remove the ones that have broadcom or bcm or sta in them, then restart your computer.

Then run this command in a terminal
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer
```then disconnect your wired connection and restart your computer and it should work, if not we need to most likely blacklist some drivers that you have installed.
Thank you

^ That did the job, thank you very much. I will be saving this incase it stops working lol

---

### Post by wildmanne39 on 2011-08-03
Hi, I am glad you have it working,would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

