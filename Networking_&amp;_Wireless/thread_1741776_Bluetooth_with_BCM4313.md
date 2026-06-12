---
title: "Bluetooth with BCM4313"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by carlos_debian on 2011-04-28
I have a Lenovo G460 laptop, that came with Windows 7 installed. It has a BCM4313. I wiped windows 7 and installed Linux, kernel is 2.6.32-5-686

```
lspci -vvnn

05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
        Subsystem: Broadcom Corporation Device [14e4:0510]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl

```Wi-Fi is working (I followed STA driver installation instructions: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)), but Bluetooth does not work.

I found this [http://ubuntuforums.org/newthread.php?do=newthread&f=336](http://ubuntuforums.org/newthread.php?do=newthread&f=336)

> *IMPORTANT* If dual-booting Windows and Ubuntu, be sure to enable the card (wireless light is on) in Windows before booting Ubuntu, otherwise it will not work.
in here [https://help.ubuntu.com/community/Ha...kCardsBroadcom]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom")
so I booted into win & checked if both wifi & bt are enabled -they have the same light & button and it was on all the time, but apparently, the BT part was disabled anyway...

so the conclusion:
if you dual-boot Win & Ubuntu and have combined wireless card with integrated BT, always check both components are enabled in Win, not only wifiBluetooth used to work with W7, but I think I turn it off before installing Linux. 
Unfortunately I cannot go back to Windows 7, so I cannot turn it on from there.

Does anybody know if there is another way to activate (or enable) BT

BTW.... rfkill shows nothing, even though WiFi is working...

---

### Post by carlos_debian on 2011-05-05
Anybody had a similar problem with Bluetooth? I can't find any other way to enable BT... really.. erase my Linux installation, reinstall Windows (sadly all I have is a "one touch recovery" or something like that) just to enable Bluetooth, and reinstall Linux again sounds insane... ](*,)

---

### Post by mahawksid on 2012-02-20
Well i have the same problem and i am searching whole forum for the answer.
But for the problem of having it turned off at in Windows-7 u can try sudo /etc/init.d/bluetooth status 
If it says Bluetooth is running, then all you need is the right module.
And this broadcom STA driver is of no good to me till now.

---

### Post by carlos_debian on 2012-02-20
Hi,

I didn't solve the problem yet...  I tried a couple of month ago with Knoppix and BT was working.

/etc/init.d/bluetooth status shows:

bluetooth is running.

So I guess something is wrong with my kernel configuration, or the module being loaded.

Also rfkill list all   shows nothing....

Should I install the latest kernel?? My actual kernel is 2.6.32-5-686 ... how does the latest kernel (3.0) impact on the filesystem (dev. sys, virtual machine, etc.) ??

---

### Post by mahawksid on 2012-02-20
Man, new kernel is not gonna help you with the bluetooth problem. What i believe is that, just like the wifi trouble of conflicting modules(Hope you are familiar), some other module must be conflicting with bluetooth too.

BUT, as i am new to linux world, i cant fix this problem myself.

Same here with me, my rfkill list shows my wireless lan but not bluetooh.

---

