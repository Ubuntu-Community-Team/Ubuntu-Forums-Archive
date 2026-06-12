---
title: "WG511 wireless card not available as network device"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by bratman91 on 2011-02-22
I have just installed Ubuntu 10.10 on a Dell Laptop. It has a Netgear WG511 (made in China) PCI wireless card but I cannot see any connections other than the wired one. Entering in lspci in the terminal mode and removing/replacing the WG511 shows (I think) that something is being detected in the PCI slot "Network Controller: Intersil Corporation ISL 3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] rev 01". Is this the WG511 and, if so, how do I get it to be detected as a network device?

---

### Post by chili555 on 2011-02-22
> "Network Controller: Intersil Corporation ISL 3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] rev 01". Is this the WG511 and, if so, how do I get it to be detected as a network device?Yes, it is. Usually, these devices simply need firmware. When you have a wired internet connection, please do:```
sudo apt-get install linux-firmware-nonfree
```After it installs, detach the wired ethernet and reboot. You should have working wireless. Post back if you need further guidance.

---

### Post by bratman91 on 2011-02-22
> **chili555 said:**
> Yes, it is. Usually, these devices simply need firmware. When you have a wired internet connection, please do:```
sudo apt-get install linux-firmware-nonfree
```After it installs, detach the wired ethernet and reboot. You should have working wireless. Post back if you need further guidance.

 Brilliant - works a treat. Very many thanks

---

### Post by jtraceypgh on 2011-03-10
I found this thread several weeks ago when working with Ubuntu 10.10 on my wife's Dell and it worked great to get the Netgear card working.  Unfortunately, it is NOT working for my IBM Thinkpad g40!:confused: 

Any suggestions??

Thanks!

---

### Post by chili555 on 2011-03-10
Please post:```
rfkill list all
dmesg | grep p54
lspci -nn
```Thanks.

---

### Post by jtraceypgh on 2011-03-10
rfkill list all  yielded no results


sudo dmesg | grep p54
[   30.160598] p54pci 0000:03:00.0: enabling device (0000 -> 0002)
[   30.160618] p54pci 0000:03:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   30.160636] p54pci 0000:03:00.0: setting latency timer to 64
[   30.219546] phy0: p54 detected a LM86 firmware
[   30.219552] p54: rx_mtu reduced from 3240 to 2376
[   31.453022] p54pci 0000:03:00.0: PCI INT A disabled
[   31.453036] p54pci: probe of 0000:03:00.0 failed with error -110


lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 01)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 01)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 01)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5901 100Base-TX [14e4:170d] (rev 01)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
03:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)

---

### Post by chili555 on 2011-03-11
This may offer some guidance: [http://ubuntuforums.org/showthread.php?t=1459068](http://ubuntuforums.org/showthread.php?t=1459068)

Do you believe you have a Version 1 card? Let's try the fix outlined in the link. Remove the card. Obtain a wired ethernet connection. Now open a terminal and do:```
cd /lib/firmware
sudo mv isl3886pci isl3886pci.old
wget http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.12.0.0.arm
sudo mv 2.12.0.0.arm isl3886pci
```Note any errors and post them here before you proceed.

Detach the cable. Now do:```
sudo rmmod -f p54pci
```Reinsert the device. Does it work now? If not, let's see what messages come up:```
dmesg | grep p54
```

---

### Post by jtraceypgh on 2011-03-11
Before I follow the steps you outline - which I probably won't get to until at LEAST later tonight, the card is clearly marked v3.0.  Further, it worked fine previously in this laptop (Ubuntu installed inside Win XP) as well as my wife's old Dell, after a firmware update I described above.  I'm currently working on an install of Ubuntu on a spare hard drive I swap with my XP drive when I have time to experiment...and it's THERE that I'm having the problem.

I said all that to say, I want to ensure the steps you outline won't cause any complications for a v3.0 card.  Of course I'm aware any changes can be reversed, even if it requires reinstall.  Just thought I'd ask...

Thanks again for your help!

---

### Post by chili555 on 2011-03-11
If you have a Version 3 card and these instructions are for a Version 1 card, then I'd recommend you *NOT* undertake them. Back to Google...

I should have a better answer a bit later today.

---

### Post by jtraceypgh on 2011-03-11
Thanks again...

---

### Post by chili555 on 2011-03-11
> the card is clearly marked v3.0. Could you please double-check: [http://forum1.netgear.com/showthread.php?t=12727](http://forum1.netgear.com/showthread.php?t=12727)

[http://kb.netgear.com/app/products/family/a_id/1270](http://kb.netgear.com/app/products/family/a_id/1270)

---

### Post by jtraceypgh on 2011-03-16
Thanks, Chili.  That clears that up!  I'll insert the Ubuntu drive,  give your previous instructions a shot and report back.  On vacation for a couple weeks and will have time to "play"...  ;)

---

### Post by chili555 on 2011-03-16
> **jtraceypgh said:**
> Thanks, Chili.  That clears that up!  I'll insert the Ubuntu drive,  give your previous instructions a shot and report back.  On vacation for a couple weeks and will have time to "play"...  ;)Post back if you get stuck or hit a snag. Enjoy the vacation.

---

### Post by jtraceypgh on 2011-03-16
Got this when executed:

 wget [http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.12.0.0.arm](http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.12.0.0.arm)
--2011-03-16 13:49:07--  [http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.12.0.0.arm](http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.12.0.0.arm)
Resolving daemonizer.de... 178.77.99.65, 2001:4dd0:fc1c::1
Connecting to daemonizer.de|178.77.99.65|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30076 (29K) [application/octet-stream]
2.12.0.0.arm: Permission denied

Cannot write to `2.12.0.0.arm' (Permission denied).

---

### Post by chili555 on 2011-03-16
> sudo mv 2.12.0.0.arm isl3886pciWas it at this step where you got 'permission denied?' Are you sure you preceded the command with sudo? You might try:```
cd /lib/firmware
sudo su
mv 2.12.0.0.arm isl3886pci
exit
```

---

### Post by jtraceypgh on 2011-03-16
never got there.  Got that error after issuing: wget [http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.12.0.0.arm](http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.12.0.0.arm)

---

### Post by chili555 on 2011-03-16
Ah, I see now. An ordinary user can't write to /lib/firmware. Oops, silly Chili!
```
sudo su
cd /lib/firmware
mv isl3886pci isl3886pci.old
wget http://daemonizer.de/prism54/prism54-fw/fw-softmac/2.12.0.0.arm
mv 2.12.0.0.arm isl3886pci
exit
```

---

### Post by jtraceypgh on 2011-03-16
Tried three more times...same outcome

---

### Post by jtraceypgh on 2011-03-16
If I'm following you, you're downloading a file that will then be moved and renamed, correct?  Could you just e-mail it to me?

---

### Post by chili555 on 2011-03-16
> **jtraceypgh said:**
> Tried three more times...same outcomeI edited my post; please check.

---

### Post by jtraceypgh on 2011-03-16
so, now what?

---

### Post by jtraceypgh on 2011-03-16
My turn for silly...missed your addition of "su"  Ran fine. 

Completed the process as instructed and now wireless!!

You da man, Chili!  Thanks!!

---

### Post by chili555 on 2011-03-16
> and now wireless!!Awesome! You have helped some searchers, too.

Are you ready to use Thread Tools at the top and mark the thread Solved?

---

### Post by jtraceypgh on 2011-03-16
> **chili555 said:**
> Awesome! You have helped some searchers, too.

Are you ready to use Thread Tools at the top and mark the thread Solved?


Would love to, but it's not an option, perhaps because I didn't start it??

Thanks again!

---

### Post by chili555 on 2011-03-16
> because I didn't start it??Yep, you're right. I'll do the best we can:


**[SIZE="4"]SOLVED.[/SIZE]**

---

### Post by Register208 on 2011-05-09
Hi,

I installed the non free package and try the solution explained upper.

But with no luck. The NetGear WG511 (V1) scan the networks and find mine but i can't get a connection.

Dmesg | grep p54
```

[   18.313380] p54pci 0000:03:00.0: enabling device (0000 -> 0002)
[   18.313402] p54pci 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   18.313421] p54pci 0000:03:00.0: setting latency timer to 64
[   18.564879] ieee80211 phy0: p54 detected a LM86 firmware
[   18.564888] p54: rx_mtu reduced from 3240 to 2376
[   19.638687] Registered led device: p54-phy0::assoc
[   19.638884] Registered led device: p54-phy0::tx
[   19.639037] Registered led device: p54-phy0::rx
[   19.639183] Registered led device: p54-phy0::radio
[   19.639199] p54pci 0000:03:00.0: is registered as 'p

```

Dmesg after trying to connect to the ssid
```

[   51.474468] wlan0: direct probe to e2:94:fd:52:cb:f4 (try 1/3)
[   51.672049] wlan0: direct probe to e2:94:fd:52:cb:f4 (try 2/3)
[   51.872243] wlan0: direct probe to e2:94:fd:52:cb:f4 (try 3/3)
[   52.072242] wlan0: direct probe to e2:94:fd:52:cb:f4 timed out

```

Regards,

R.
[http://flickr.com/r208](http://flickr.com/r208)

---

### Post by chili555 on 2011-05-09
> **Register208 said:**
> Hi,

I installed the non free package and try the solution explained upper.

But with no luck. The NetGear WG511 (V1) scan the networks and find mine but i can't get a connection.

Dmesg | grep p54
```

[   18.313380] p54pci 0000:03:00.0: enabling device (0000 -> 0002)
[   18.313402] p54pci 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   18.313421] p54pci 0000:03:00.0: setting latency timer to 64
[   18.564879] ieee80211 phy0: p54 detected a LM86 firmware
[   18.564888] p54: rx_mtu reduced from 3240 to 2376
[   19.638687] Registered led device: p54-phy0::assoc
[   19.638884] Registered led device: p54-phy0::tx
[   19.639037] Registered led device: p54-phy0::rx
[   19.639183] Registered led device: p54-phy0::radio
[   19.639199] p54pci 0000:03:00.0: is registered as 'p

```

Dmesg after trying to connect to the ssid
```

[   51.474468] wlan0: direct probe to e2:94:fd:52:cb:f4 (try 1/3)
[   51.672049] wlan0: direct probe to e2:94:fd:52:cb:f4 (try 2/3)
[   51.872243] wlan0: direct probe to e2:94:fd:52:cb:f4 (try 3/3)
[   52.072242] wlan0: direct probe to e2:94:fd:52:cb:f4 timed out

```

Regards,

R.
[http://flickr.com/r208](http://flickr.com/r208)When you click the Network Manager icon, do you see your network? When you click it and try to connect, are you asked for the encryption key; i.e. WEP, WPA, etc.? Does it try to connect?

---

### Post by Register208 on 2011-05-10
Thanks for the reply.

yes it ask for the password but after a long time about a minute.
I enter it and it re asks for it after the same time.

---

### Post by chili555 on 2011-05-10
Is your network set to WPA or WPA2 or the dreaded and tricky mixed WPA and WPA2 mode?

---

### Post by Register208 on 2011-05-10
It's WPA (TKIP + AES)

And the chanel is 5, how can i see that it had chosen the right channel?

---

