---
title: "fglrx Driver Not Detecting Hardware"
date: 2013-03-09
forum: Multimedia Software
---

### Post by JoeGoldman on 2013-03-09
Hi Crew,

 I have a Radeon HD 4870 graphics card.

 Previously, it was installed on a GA-MA790GP-DS4H motherboard with an AMD 9850 BE CPU. I installed Ubuntu 12.04.01 and it had taken it's updates regularily.

 On this setup, I was able to get fglrx installed from the actual AMD website (building the packages etc, as fglrx in apt was generating OpenGL errors with Steam).

 I upgraded slightly to a newer ASUS M4AB9GTD PRO Motherboard with AMD X2 550 CPU and 4GB DDR3 ram (over 2GB DDR2 last system). I moved the graphics card over to continue using it.

 I decided to do a fresh install so grabbed the desktop-amd64 ISO of 12.04.2, and did a clean install. So far so good, but I run into issues attempting to install fglrx.

 Ultimately, if I do an apt-get install fglrx, amdconfig --initial shows no adapters found, and if I reboot in that state, I will go into a very low quality graphics mode and not be able to do much. I can simply apt-get remove that package and it goes back to working OK but still not with fglrx drivers.

 When I try to build packages out of the AMD drivers, the .deb's generate fine but when trying to install they are after dependencies that break the whole install. I have tried both 12.6 and 13.1 file from AMD. The main issue appears to be that I am running on kernel 3.5.X when fglrx seems to be trying to get 3.2.X headers etc as a dependency.

 I have tried about 6 different fresh installs trying things in particular orders but have had 0 success.

 For now I am resigned to using it with the default drivers, so at least its a good desktop document work box, but I'd really like to know whats going on and have some success as I want to play some games!

Thanks.


EXTRA INFO (if you need any more just ask!):

Xorg version: 1.13
uname -r: 3.5.0-25-generic

```

$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:03.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4870]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV770 HDMI Audio [Radeon HD 4850/4870]
02:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

---

### Post by QIII on 2013-03-09
Hello!

Unfortunately, you are in a bad situation by moving to 12.04.2.

AMD/ATI stopped driver development support for HD 2xxx to HD 4xxx cards, and the unadulterated proprietary legacy driver does not work with X Server 1.13, which is used from 12.04.2 forward.  12.04 and 12.04.1 use X Server 1.12.  That is why you get the message that no adapters are found.  You need an HD 5xxx series or newer.

There are methods to get things to work, all of which require downgrading X Server, using the legacy driver and patching the kernel.  I cannot recommend those methods in good conscience because, quite frankly, with what is essentially a broken system nobody can predict with any real confidence what will happen when some new update comes along to knock down the house of cards.

My recommendations have been one of two things.

1.   For 12.04.2 onwards, use the default open source Radeon driver, which should work for the vast majority of users.
2.  Stick with 12.04 or 12.04.1/

I suspect someone will come along with a marvelous, scripted and very simple way to get you going with the proprietary driver.  There are several folks who have developed packages to do that.  Those methods generally work.  For now.

You'll have to decide for yourself what risk you want to take.

Best wishes!

---

### Post by JoeGoldman on 2013-03-09
G'day,

 I'm not impartial to going back to 12.04/12.04.1. It will be a pain to manage updates but I'll live. I can't afford new hardware, just time. EDIT: Or even moving to 12.10 if thats an option to help? But I doubt it.

 Problem with doing so is that I require the 12.04/12.04.1 install package, I can only seem to locate a 12.04.2 install iso, is there a place I can get archived ISO's?


 Is this a very NEW update thats occurred? As I kept my previous install which started from 12.04.1 up-to-date but everything continued to work. Is ubuntu smart enough to keep this under wraps i.e. not update xorg and others ?

 What if I moved to MATE desktop environment? Does that change my chances of it at all? (i.e. does it downgrade xorg?)

Thanks for your reply!

---

### Post by QIII on 2013-03-09
Sorry.  You're not going to get around it with a differend desktop environment.  This is with X Server.

It's not an entirely new development, but not likely something those who don't keep up with this sort of thing would know about.  You probably didn't get the memos!  ;)

X Server 1.13 is just part of Ubuntu 12.04.2 and later.  It's not really a matter of "being smart enough" not to update it.  It can be downgraded, but as I said I really do not recommend that approach.

Anyway, you can download 12.04.1 [here.]("http://old-releases.ubuntu.com/releases/precise/")

Ultimately, this is all due to a business decision made by AMD.  They are a business.  Businesses exist to make money.  I'm sure that their cost/revenue calculations for continuing to maintain driver compatibility going forward for the older cards didn't add up.

Frustrating to say the least.  But there isn't much to be done about it now.

---

### Post by QIII on 2013-03-09
*Moved to **Mulitmedia & Video***

---

### Post by JoeGoldman on 2013-03-09
Don't get me wrong - I completely understand the move by AMD. 4XXX is quite old.

The frustrating part was just finding the answer. Apart from things behaving completely strange saying there is no adapter etc, why not have the drivers detect the old unsupported devices still, but pop up saying can no longer service this card etc? Or even better check the xorg version too and pop up a meaningful message about that?

In any case, downloading 12.04.1 now and will do a clean install and see how it progresses :)

Thanks for the help!

---

### Post by JoeGoldman on 2013-03-10
Just confirming, now running 12.04.1, set apt-mark hold xorg* and then did a full upgrade through update manager, no issues. Installed fglrx out of apt first then installed 12.6 legacy from AMD's website (built packages and installed separately). Working perfectly!

---

### Post by pi6502 on 2013-06-01
I'm experiencing the same issues as you (using ATI HD 4850 and 12.04.2) and was wondering if going 12.04.1 or buying a new videocard.

Why did you set apt-mark hold xorg* ? Would 12.04.1 upgrade 'silently' to unsupported xorg version otherwise? Maybe I misunderstood QIII's post but I thought that using 12.02.1 will enable legacy ATI cards to be used with proprietary ATI drivers - 'forever'?.  If not, how long will other updates work if you hold XServer?

---

### Post by QIII on 2013-06-02
Hello!

I can't tell you how to spend your money, of course, but I'd say to save the money and just use 12.04.1.  It's supported for 4 more years.  

No, I don't think the hold is necessary in 12.04.1.  The upgrade in X Server and the kernel (among other things) was the point of the 12.04.2 release.  12.04.1 should be fine.

Cheers!

---

### Post by JoeGoldman on 2013-06-02
It *DOES* appear to want to upgrade xorg to the newest release on my 12.04.1 which is why I have put a hold on letting it upgrade. When I first got it working I think I recall reading that it will upgrade to the newer, non-supported version hence why I stopped it

I'll have to check the upgrade info more to see if it will but I'm afraid of breaking my now stable install. Will report my findings when I'm back on that computer.

---

### Post by Cheesemill on 2013-06-02
There's no need for the hold.

If you have 12.04.1 installed you can keep updating it until 2017 and the kernel and X server will still work with your card.

To upgrade 12.04.1 to the new kernel and X server you have to manually opt in to the new enablement stack by running...
```
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal
```

Obviously don't run this command as it will update you to the problematic (for your card) 12.04.2 release.

More information can be found on the wiki...
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by JoeGoldman on 2013-06-02
Thanks for the info I will remove the hold tonight, I'm currently on 1.12 and looks like it only wants to go to 1.14 so should be safe :)

---

