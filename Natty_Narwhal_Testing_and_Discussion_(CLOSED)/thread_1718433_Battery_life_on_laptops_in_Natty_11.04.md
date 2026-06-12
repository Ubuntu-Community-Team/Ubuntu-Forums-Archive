---
title: "Battery life on laptops in Natty 11.04"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lifelike27 on 2011-03-31
Has anyone else had lower battery life when using Ubuntu 11.04? I have a Dell Studio 1558. On Lucid and Maverick I would get a good four hours of battery life. For Natty, I only get an hour, and my fan is pretty darn loud.

I know, what you'll are going to say, it's an alpha release you should expect it. I'm just wondering if I'm not the only one and if this would affect my average battery life if I keep this going...

Overall, I'm loving Unity! :)

---

### Post by martydelaney3 on 2011-04-01
My eeePC 1005P has had its battery life cut from 8 hours to around 3. So you aren't the only one. But I expect it to just be because it's an alpha, hopefully it'll be addressed soon.

---

### Post by Yellow Pasque on 2011-04-01
If the devs are unaware of the problem, they can;t fix it. What kind of hardware do you folks have?
```
lspci
```

---

### Post by davidmohammed on 2011-04-01
it might be worth checking that your cpu governor is not stuck at performance when you boot.  For my laptop it sometimes stays at ondemand - on some occasions it defaults to the highest performance.

If you are using ubuntu classic you can right click the panel and choose "cpu frequency".  

If you are using unity then add the indicator-cpufreq as per instructions [here]("http://www.ubuntugeek.com/indicator-cpufreq-cpu-frequency-indicator-ppa-installation-instructions-included.html")

---

### Post by lifelike27 on 2011-04-04
So I ended up checking this post only today and as I was reading your posts Update Manager popped up and I let it install updates. Then the friendly driver icon appeared in my indicator applet saying it had to activate my ATI graphics card driver! Which usually takes up a helluva lot battery if you don't (from my experience). 

It's odd, because when I installed Natty, video acceleration seemed fine without it. It was just battery life that was being terrible.

Anyway, I think you guys should check the Update Manager as well.

Good luck!


UPDATE: I guess I spoke to soon. After activating the drivers, it made all of Unity and text boxes black. I just deactivated it for now.

UPDATE 2: Update to fix my problems finally released!

---

### Post by lifelike27 on 2011-04-04
> **Temüjin said:**
> If the devs are unaware of the problem, they can;t fix it. What kind of hardware do you folks have?
```
lspci
```

Since you were curious.. :)

```
jon@jon-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
07:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

---

### Post by nanog on 2011-04-21
My battery life has been reduced to 1 hr on a dell mini 9. Previously it was close to 3 hrs. Powertop shows a massive increase in interrupts but its not application specific. I suspect a kernel or driver problem.

---

### Post by lifelike27 on 2011-04-22
Before I was able to use the ATI proprietary driver, this is what my battery's discharge profile was: [http://dl.dropbox.com/u/8515110/Desktops/Battery%20discharge%20graph.png](http://dl.dropbox.com/u/8515110/Desktops/Battery%20discharge%20graph.png)

After I was able to and using Beta 2: [http://dl.dropbox.com/u/8515110/Desktops/Battery%20discharge%20graph%20%28Beta%202%29.png](http://dl.dropbox.com/u/8515110/Desktops/Battery%20discharge%20graph%20%28Beta%202%29.png)

Not much change from I can notice, but my battery lasts around 1.30 - 2.00 hours now. It isn't the optimal amount, but at least it's half of what it used to be instead of quarter...

---

### Post by handy on 2011-04-22
You may want to give Jupiter a try. I know a number of people that have had very good results battery life wise by using it:

[http://www.fewt.com/2010/07/jupiter-ppa-now-available-for-ubuntu.html](http://www.fewt.com/2010/07/jupiter-ppa-now-available-for-ubuntu.html)

---

### Post by phibxr on 2011-04-22
If you were running without compiz effects before, you've most likely got your battery drain right there.

Dual booting several versions of Ubuntu, Natty drains the least battery with effects enabled here, thought significantly more than with effects disabled.

---

### Post by lifelike27 on 2011-04-22
> **phibxr said:**
> If you were running without compiz effects before, you've most likely got your battery drain right there.

Dual booting several versions of Ubuntu, Natty drains the least battery with effects enabled here, thought significantly more than with effects disabled.

That must be some kind of bug right? Without compiz it should be better.

---

### Post by Toz on 2011-04-22
Came across this earlier today.

[http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1)

---

### Post by 5149.5 on 2011-04-23
> **Toz said:**
> Came across this earlier today.

[http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1)

That is very interesting. I thought I noticed a heat difference on my laptop.

---

### Post by M4570D0N on 2011-04-23
Yep. I've definitely noticed a battery drain and higher temps. Looks like it's a major bug in the 2.6.38 and 2.6.39 kernels

Phoronix has another article on it out today, in addition to the one posted above.

> *This is the prequel to [Mobile  Users Beware: Linux Has Major Power Regression]("http://www.phoronix.com/vr.php?view=15926") and [Uff  Da! The Linux Power Bug Even More Mysterious]("http://www.phoronix.com/scan.php?page=news_item&px=OTM2NQ"). It was written in advance of  tracking down the issue to a matter in the upstream Linux kernel. Though as the  Phoronix Test Suite stack is presently bisecting and analyzing the kernel during  the period in question (Linux 2.6.37 to 2.6.38 ), this article is being published  now and hopefully on Easter Sunday or Monday the actual offending commit will  be known along with much more information. This bug has also now been confirmed independent  of Phoronix by at least six separate parties that I'm aware of, with reports of  Natty either consuming excessive power or a very significant increase in heat  output compared to Ubuntu 10.10. These independent reports have occurred on a  range of hardware -- including desktops. There is also [at  least one bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131") on the matter for Ubuntu 11.04.*

...
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_power&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_power&num=1)

---

### Post by Blasphemist on 2011-04-23
I came to natty during the last alpha and at the beginning I think this may have been the case for me but now I don't. I have a screenlet that shows CPU usage and both cores are usually at very low usage, under 5%. Who knows, my GPU may be different but if so I can't tell it by performance or battery life. My battery life is the same as with maverick and my performance better I believe. I don't have any good test data to back this up.

The link above doesn't show the kind of change described, the testing showed up to 26% shorter battery life. I think y'all may need to look deeper.

---

### Post by M4570D0N on 2011-04-24
> **Blasphemist said:**
> I came to natty during the last alpha and at the beginning I think this may have been the case for me but now I don't. I have a screenlet that shows CPU usage and both cores are usually at very low usage, under 5%. Who knows, my GPU may be different but if so I can't tell it by performance or battery life. My battery life is the same as with maverick and my performance better I believe. I don't have any good test data to back this up.

The link above doesn't show the kind of change described, the testing showed up to 26% shorter battery life. I think y'all may need to look deeper.

I'm not noticing higher CPU or RAM usage, compared to 10.10 or Mint 10, but I've still noticed a shortened battery life. It's a 12-cell lithium ion that's about 1 year old, and I'm getting significantly less life out of each charge since I switched to the 2.6.38 kernel.

---

### Post by cariboo on 2011-04-24
Have any of you used powertop to optimize your battery usage?

---

### Post by fuduntu on 2011-04-24
I found the bug report that Phoronix is referencing.  If you look at the powertop metrics there are all kinds of things running in the background like Chromium, WIFI, touchpad / keyboard.

Of course it's registering over 500 wakeups per second..

[http://phoronix.com/forums/showthread.php?48656-Mobile-Users-Beware-Linux-Has-Major-Power-Regression&p=201105#post201105](http://phoronix.com/forums/showthread.php?48656-Mobile-Users-Beware-Linux-Has-Major-Power-Regression&p=201105#post201105)

[https://launchpadlibrarian.net/69300044/hardcopy.0](https://launchpadlibrarian.net/69300044/hardcopy.0)

Like Cariboo said, powertop should be used (or a utility like Jupiter that applies common powertop recommendations automatically).

This is growing way out of proportion and it isn't even an issue (IMHO).

---

### Post by phoronix on 2011-04-24
> **fuduntu said:**
> I found the bug report that Phoronix is referencing.  If you look at the powertop metrics there are all kinds of things running in the background like Chromium, WIFI, touchpad / keyboard.

Of course it's registering over 500 wakeups per second..

[http://phoronix.com/forums/showthread.php?48656-Mobile-Users-Beware-Linux-Has-Major-Power-Regression&p=201105#post201105](http://phoronix.com/forums/showthread.php?48656-Mobile-Users-Beware-Linux-Has-Major-Power-Regression&p=201105#post201105)

[https://launchpadlibrarian.net/69300044/hardcopy.0](https://launchpadlibrarian.net/69300044/hardcopy.0)

Like Cariboo said, powertop should be used (or a utility like Jupiter that applies common powertop recommendations automatically).

This is growing way out of proportion and it isn't even an issue (IMHO).

To be clear, that bug report isn't from me but James Fergusson, a Canonical engineer. I can't speak for his wakeup results, but I can tell you that a very real problem does exist with 2.6.38+.

---

### Post by fuduntu on 2011-04-24
> **phoronix said:**
> To be clear, that bug report isn't from me but James Fergusson, a Canonical engineer. I can't speak for his wakeup results, but I can tell you that a very real problem does exist with 2.6.38+.

Can you point to a real reference of the bug so it can be verified?  

I am seeing less than 150 wakeups per second on battery with 2.6.38, 2.6.38.3, and 2.6.38.4 on multiple machines..

---

### Post by Mars73 on 2011-04-24
Well I've been using 11.04 for a few days now and trying the AMD opensource or fglrx driver that comes with it but in both cases my laptop fan is on constantly.
This is my main workhorse and am behind it most of the day and it is very very annoying.
I had the same problem with 10.10 and the opensource driver but after installed the catalyst 11.3 driver it was gone.
I have 2 cpu gnome desklets running and see the CPU is on demand, so not on performance.
So it's proably a kernel driver issue...well the kernel driver team better fix this but imo it's a major issue.
It's not nice to see and hear your collegae's same laptop with Win7 almost quiet as a mouse and your Ubuntu machine with nothing running is blowing like hell.
For now I'm going back to 10.10 and watch this space to see if there's any improvement on this.

---

### Post by ejarg7 on 2011-04-28
I am having the same problem too.  I can get about 4-5 hours with Windows 7 before this.  I wiped out Windows 7 from the machine and installed Natty beta 2.  I am loving the new interface overall but it seems like the battery only lasts about 2 1/2 hours max now.  I have Lucid on my other laptop (much older, albeit with a smaller screen) and I can still get 4-5 hours of battery life out of it.  

Will this be fixed in the official release?

---

### Post by Yellow Pasque on 2011-04-28
You should never expect the same battery life in Linux that you have on Windows. OEM's write crappy ACPI implementations and then write the corrective quirks into the Windows drivers. C'est la vie..

---

### Post by lifelike27 on 2011-04-28
My problem was a little different, Windows 7 gave me an hour and a half. Ubuntu 10.04 and 10.10 gave me four hours, but 11.04 gives me an hour and a half as well. =\

---

