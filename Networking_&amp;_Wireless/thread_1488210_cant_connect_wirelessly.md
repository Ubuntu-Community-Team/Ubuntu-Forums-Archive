---
title: "cant connect wirelessly"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by mrwise32 on 2010-05-19
i am new to ubuntu and i cant connect wirelessly. I have the version 10.04. i dont know if something is missing like some type of wireless card or some type of drivers. i have a dell mini notebook. i worked before but dont know what happened i had the old version 8 until i loaded 10 yesterday. any help would be appreciated.

---

### Post by purelinuxuser on 2010-05-19
We need some debug information.  Open a Terminal (Applications > Accessories > Terminal), type the following commands, and press Enter.  Copy and paste the output here.

```
lspci
```

```
lshw -c network
```

```
iwconfig
```

```
iwlist scan
```

Good luck! :)

---

### Post by mrwise32 on 2010-05-20
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
shannon@shannon-laptop:~$ lsw-c network
lsw-c: command not found
shannon@shannon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
shannon@shannon-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

---

### Post by purelinuxuser on 2010-05-20
> **mrwise32 said:**
> shannon@shannon-laptop:~$ lsw-c network
lsw-c: command not found

You misspelled that command, it should be "**lshw** -c network." :P

Anyway, I think you have a Broadcom BCM4312 wireless card.  In my experience, this card works OK with the proper firmware, but wireless tends to disconnect a lot and is VERY slow.  Your mileage may vary however. ;)

To install firmware for your card (the easy way, anyway):

[LIST=1]
[*]Plug your laptop into an Ethernet cord to gain an Internet connection.
[*]Open Synaptic Package Manager (System > Administration).
[*]Perform a quick search for "b43-fwcutter."
[*]Double-click on the b43-fwcutter package, and it should be marked for installation.
[*]Click "Apply" in the toolbar at the top.
[*]As installation progresses, you will be prompted with a dialog that has a checkbox labeled "Automatically download and install firmware?"; be sure it is **CHECKED**.
[*]Reboot, and hopefully everything will be working.
[/LIST]
If not, post back with the commands listed earlier, as well as this one:
```
dmesg | grep -i b43
```
That "|" is a vertical pipe: type it by pressing Shift+Backslash (\).

I'm sorry if this is all so complicated. :( Unfortunately Broadcom has not always been the friendliest wireless manufacturer to Ubuntu and the Linux community in general...

---

### Post by TheGnomeOfMetal on 2010-05-20
I see you have a Bcm4312 Wireless card. I too have one in my netbook. What I did was I Connected it via ethernet cable to my router, then went to update manager and updated everything. reboot the computer, then go to hardware drivers, there should be one the has the letters STA in it. Enable that then reboot and the wireless card should be on.

---

### Post by mrwise32 on 2010-05-21
thanks for the help, followed everyones steps and tonight it connected wirelessly!!

---

### Post by purelinuxuser on 2010-05-21
> **mrwise32 said:**
> thanks for the help, followed everyones steps and tonight it connected wirelessly!!

Great!  Don't forget to click Thread Tools and mark this thread as [Sovled]. :)

---

