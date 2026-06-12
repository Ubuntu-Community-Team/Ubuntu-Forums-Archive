---
title: "RTL8191SEvB Wireless alerts"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by shibinj on 2010-11-22
Hi 

My distro is Ubuntu Maverick Meerkat on Toshiba Satelite L510 with RTL8191SEvB Wireless LAN.  I am keep on receiving following alerts.

[ 4103.112155] rtl8192_hw_sleep_down(): RF Change in progress!
[ 4125.335721] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4133.172522] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4143.563424] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4147.204535] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[ 4160.217257] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4161.738150] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[ 4190.149251] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[ 4280.708966] Received beacon ContryIE, SSID: <raj>
[ 4281.738501] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
[ 4401.734538] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5


What all these alerts?  This issue affects, when I use my SFL SIP phone services.  I can hardly make a call for 2 minutes.  When this "rtl8192se_update_ratr_table" alerts came up, all of a sudden line disconnects at other end.

Appreciate your help.

Thanks.
Shibin

---

### Post by wolfger on 2011-03-02
Bump. Seeing the same thing here.

---

### Post by Bucky Ball on 2011-06-30
Ever get anywhere with this? I have the Tosh Sat Pro L510 also and have very slow speed (-1Mbps compared to +10Mbps on three other machines and the Win7 install on the Tosh). 

I have been trying to fix my speed prob for months. Know it's not the same as your prob but might get some clues.

---

### Post by wolfger on 2011-06-30
Never got anywhere on Maverick. Migrated to Natty, and it's better, but not convinced it's fixed. Honestly, I quit booting into Ubuntu because of the problems, so I should check the latest updates and see how it is.

---

### Post by phaed on 2011-07-06
I seem to get these messages every 2 minutes like clockwork. My wireless works fine, I'm just wondering what they mean.

> Jul  6 22:39:25 laptop kernel: [86209.258027] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Jul  6 22:41:25 laptop kernel: [86329.213553] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Jul  6 22:43:25 laptop kernel: [86449.169355] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Jul  6 22:45:25 laptop kernel: [86569.125077] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Jul  6 22:47:25 laptop kernel: [86689.080847] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Jul  6 22:49:25 laptop kernel: [86809.036582] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Jul  6 22:51:25 laptop kernel: [86928.992286] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Jul  6 22:53:25 laptop kernel: [87048.952002] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Jul  6 22:55:25 laptop kernel: [87168.903912] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5

---

### Post by Bucky Ball on 2011-07-07
This card sucks in Linux! I have one in my Toshiba Satellite Pro L510. 10.04, 10.10, 11.04 ... it works ... at half the speed of the other machines in the house (three of them wired and wireless).

Not Ubuntu's fault: email Realtek and tell them to pull their finger out on this card (I have). 

I advise getting a wireless dongle or replacing the card. I had a wireless dongle on one of my other machines (the dongle has a Realtek wireless chip also but different one using driver rtl8187 in 10.10 at the moment but think different in other installs). Plugged it in, voila; automagically picked up and working like a dream! No issue whatever (in 10.10 and 11.04 that is).

So I blacklisted the driver for the internal card (add 'blacklist r8192se_pci' to the bottom of /etc/modprobe.d/blacklist.conf if that is the driver you are using) and am now primarily using the wireless dongle (the internal card gets not quite 1Mbps while the external dongle gets +10Mbps).

*Avoid this card* until Realtek improves the Linux drivers, but don't hold your breath. I've had my laptop since Nov 2010 and nothing's changed to this point. Still sucks in Linux (same in OpenSUSE incidentally so not a Ubuntu thing). Googling is more or less a waste of time as all I ever found were people's unresolved problems and a wild goose chase for a fix that doesn't exist. (When I first emailed Realtek they said the driver was really intended for 32Bit installs and results were unpredictable on 64Bit - I installed 32Bit Ubuntu and you guessed it; not a jot of difference.)

You can pick up an external wireless dongle for next to nothing nowadays on ebay. Do it if you're having trouble and I reiterate: EMAIL REALTEK about this driver ... 

Good luck. ;)

---

### Post by phaed on 2011-07-07
I have a Toshiba L550 that I got in March 2010. As I said, the wireless works fine for me with Ubuntu 10.10 32bit, and I don't have any speed issues. But I've been watching my logs and noticing various messages. First it was constant messages related to AP (access point) not being established. I looked into it and the suggestion was to get the latest driver. 10.10 has driver 17.0507.2010, or something like that, and I manually compiled / installed 19.1207.2010, which fixed that issue, but I keep getting the messages that I posted above... every 2 minutes.

I wonder what they mean. I can't find anything on Google. I just found this thread.

---

### Post by Bucky Ball on 2011-07-07
The 0019 driver fixed no issue for me. 10.04 attempts to use the 0015 and 10.10 the 0017. I installed 0019 and it was the same as (0015 actually seemed the least problematic). phaed, are you using this exact card? Could you post the result of:

```
lshw -C network
```

?

---

### Post by phaed on 2011-07-07
Here you go:

```
  *-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:34:40:3c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0019.1207.2010 firmware=63 ip=192.168.1.2 latency=0 multicast=yes wireless=802.11bg
       resources: irq:17 ioport:7000(size=256) memory:d5500000-d5503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 02
       serial: 70:5a:b6:7f:84:c4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:47 ioport:5000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d143ffff

```

---

### Post by Bucky Ball on 2011-07-07
Yep, that's the card and the driver I'm using in 10.10. Rubbish for me. Slow speed, drops from 100% signal to 50% for no reason then back up again. My USB wireless dongle works a treat, though, so sticking with that. ;)

---

### Post by phaed on 2011-07-27
I don't know if this is relevant or useful, but it might be for our wireless card:

[rtlwifi: rtl8192se: Modify Kconfig and Makefile routines for new driver]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=85e09b40405b44b049500702beb6856646b4be46")

That's included in kernel 3.0.

I found it through [H Online]("http://www.h-online.com/open/features/What-s-new-in-Linux-3-0-1279552.html?page=2"):

"Another new addition is the rtl8192se driver for Realtek's RTL8191SE and RTL8192SE PCIe Wi-Fi chips (for example 1). From Linux 3.0, the kernel drivers the developers create for Ralink Wi-Fi chips within the Rt2x00 project will offer experimental support for series RT5370 USB Wi-Fi chips. The driver for the RT53xx family continues to be classified as experimental, but it is now said to fully support these PCI Wi-Fi chips and to work better. The situation is similar with the drivers for series RT33xx PCI and USB chips, which no longer have "experimental" status. The drivers for Ralink chips have now matured far enough for the kernel developers to throw out the rt2860sta and rt2870sta drivers that were developed by Ralink and were later integrated into the staging branch."

---

### Post by Bucky Ball on 2011-07-27
Kernel 3.0? What exactly do you mean?

I am running kernel 2.6.35-30-generic in 10.10.

* UPDATE: I get it: 3.0.00-00-generic (called something different, of course). I see if I can find it and try it as I have this card.

Also, this link:

[rtlwifi: rtl8192se: Modify Kconfig and Makefile routines for new driver]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=85e09b40405b44b049500702beb6856646b4be46")

... is for KDE I think (Kubuntu). Unless OP using that not sure will work. ;)

---

### Post by Bucky Ball on 2011-07-27
You can install it from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0-oneiric/")

(headers=all, headers=amd or i386, image=amd or i386; install in that order)

Couldn't get it to boot on my machine for the very good reason that it is a testing kernel ONLY at this point and Oneric not due for release until October. ;)

If you want to install and start debugging, the community would more than appreciate the effort. ;)

---

### Post by phaed on 2011-07-27
Right, that's what I was thinking. Download and compile the source from the 3.0 kernel and see if it makes a difference. :)

You probably know how to do it better than me.

---

### Post by phaed on 2011-07-27
Well, I mean, what about just that one driver? I'm thinking that the source code is in the kernel 3.0 tree. Is it possible just to compile and add that one driver like we did with the 0019.1207.2010 driver?

---

### Post by Bucky Ball on 2011-07-27
Look here;

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2262](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2262)

Just about to try.

---

### Post by phaed on 2011-07-27
You know what's funny? I looked at that page *last night* (I have it bookmarked and check periodically, and after seeing that kernel commit, checked again) just to make sure, and it was still the one from December. So that got updated within the last 12 hours.  Yeah, I will try it when I get home.

---

### Post by phaed on 2011-07-27
Well I can tell you this: the ratr_table errors went away. Hopefully things are working better for you.

---

### Post by Bucky Ball on 2011-07-28
No, couldn't seem to get it to work. I'll keep trying tonight when I have a bit more time.

---

### Post by Bucky Ball on 2011-07-30
News: I just booted my 11.04 install which was using the version 0017 'out of the box' (I didn't need to install the driver) and ran the install on the driver from my link earlier (post #16) and all fixed! Great speed, solid connection, wireless was up when the desktop came up at boot. 

I'm happy. Strange thing is 10.10 won't use it even though I get no errors when I install it, all goes smoothly. I'll have another go. 

So basically, for 10.04 thru 11.04 (and possibly beyond):

* Download the new driver: [http://www.realtek.com/downloads/dow...oads=true#2262]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2262")
* Untar it, if not in a terminal open one and get into the top directory of the driver (/rtl_92ce_92se_92de_linux_mac80211_0003.0620.2011)
* Run these commands:

```
sudo su
make
make install
make clean
```... although the last is not necessary. ;)

Reboot and hopefully it'll work for you like it did for me. Finally. That card has been the only issue since I got this laptop last November. :)

---

### Post by Bucky Ball on 2011-07-30
Just fiddled some more in 10.10 but when I install and reboot (using exactly the same procedure that worked in 11.04) I get this from lshw -C network:

```
*-network UNCLAIMED
       description: Network controller
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:d4000000-d4003fff
```No driver. Nothing installed. When I install the 0019 driver and reboot it installs no problem, and retains the same crappy performance (the one on my link for the earlier kernels, though it says it's updated same time as the new driver is the same performance as always). 

So, seems like, at this point, new driver works great in 11.04, doesn't seem to install in 10.10 and I haven't tried 10.04 yet.

Incidentally, the 10.10 kernel I tried the new driver with (designed for 2.6.35 and above) was 2.6.35-30-generic.

---

### Post by Bucky Ball on 2011-07-30
And this is what I have in 11.04, how it should look, for lshw -C network:

```

*-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 10
       serial: b4:82:fe:3c:ad:72
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes** driver=rtl8192se driverversion=2.6.38-8-generic** firmware=N/A ip=192.168.0.34 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:d4000000-d4003fff
```Notice how the driver version in bold is different to what it was?

---

### Post by phaed on 2011-07-30
Glad it works for you! But that's odd, because I'm on Linux Mint 10 (basically Ubuntu 10.10), and it installed for me. Just make / sudo make install in the root of driver folder, and reboot.

Running "lshw -C network" produces this output:

configuration: broadcast=yes driver=rtl8192se driverversion=2.6.35-30-generic-pae firmware=N/A 

Where before it specifically mentions that 0019 driver version.

And as I said, the ratr_table errors that occurred every 2 minutes are gone.

Oh well, we finally have good support for this wireless card. :)

---

### Post by Bucky Ball on 2011-07-30
Nope, won't install in Ubuntu 10.10 for me (and I do know how, cheers ;)). Can't explain why; maybe a wiser head can. 

I got around it by installing the 2.6.38 kernel but it screws my graphics, though (for some reason doesn't like my fglrx version), so I can only run in low-graphics mode if I want to use the internal wireless at decent speeds. But I have found a fix for that. (See below)

The kernel install could be another (easy) avenue to get that card working. If it does muck things up, reboot and choose a working kernel. To install 2.6.38 in 10.10 follow instructions here:

[http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/)

Cheers Ramoonus. ;)

BE WARNED, though; this is essentially a Natty kernel running 10.10 (in my case) so others may get unpredictable results if not using 11.04 (and possibly if they are).

If using the 2.6.38 kernel in 10.10 the graphics conflict with ATI and fglrx can be fixed with the instructions on this page:

[http://www.mindwerks.net/2011/02/ubuntu-10-10-maverick-with-2-6-38-kernel-and-fglrx/](http://www.mindwerks.net/2011/02/ubuntu-10-10-maverick-with-2-6-38-kernel-and-fglrx/)

Thanks Mindwerkers! All works great for me in 2.6.38 now (2.6.38-020638-generic); resolution fine and the card with 98% signal and a racing speed. Happy as! Been at this since the thread was started last November. ;) ;)

---

### Post by phaed on 2011-08-08
I'm not going to upgrade, because the driver installed for me with kernel 2.6.35, but I'm just wondering, do you notice the power / heat regression that some have reported with 2.6.38+ ? Is our hardware susceptible to that?

Also, did you have multiple kernels installed at the same time, or were you doing fresh installs? I was reading the Makefile a few days ago, and although I don't know the language, I can figure out some of what it's doing. It looks like it selects the highest kernel version to install the driver to, so if you had .38 and .35 on your computer at the same time, maybe that's why it ignored .35.

---

### Post by Bucky Ball on 2011-08-08
Nope. Tried to install in .35. Just wouldn't (well, it showed no errors but the driver wasn't installed when I checked). I then installed .38. Working fine. I have a lot of kernels installed but didn't have that one.

---

