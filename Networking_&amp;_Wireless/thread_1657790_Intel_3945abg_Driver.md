---
title: "Intel 3945abg Driver"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by hiever1 on 2011-01-01
I have a Dell Inspiron 6400 with Windows 7 and Ubuntu 10.10. I cannot connect to the internet. My wifi light is on, but it'll flash?  Any ideas? Works fine on Windows.

I'm a noobie  so be gentle.

---

### Post by chili555 on 2011-01-01
The driver is built in to the kernel and usually works well. Let's run a few diagnostics. Please open Applications > Accessories > Terminal and do:```
rfkill list all
dmesg | grep iwl
lsmod | grep dell
```The pipe symbol | is on the right side of my US keyboard along with \.

Post the result and we'll proceed.

---

### Post by hiever1 on 2011-01-02
> tristan@tristan-laptop:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
tristan@tristan-laptop:~$ dmesg | grep iwl
[ 1487.720187] iwl3945 0000:0b:00.0: Card state received: HW:Kill SW:On
[ 1487.756024] iwl3945 0000:0b:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x040003DD
[ 3477.659952] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[ 3800.727459] iwl3945 0000:0b:00.0: Master Disable Timed Out, 100 usec
[ 3801.064020] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
tristan@tristan-laptop:~$ lsmod | grep dell
dell_wmi                2852  0 
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop.

---

### Post by chili555 on 2011-01-02
Fascinating. Although rfkill list all shows no hardware or software switches that are interfering with the operation of your wireless card, dmesg suggests it is:```
Card state received: HW:Kill SW:On
```The time stamp indicates you may have manipulated the switch later. 

I do not see these items (from my dmesg) that show the card starting normally:> [   18.594214] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.594230] iwl3945 0000:03:00.0: setting latency timer to 64
[   18.651851] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   18.651857] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.652041] iwl3945 0000:03:00.0: irq 48 for MSI/MSI-X
[   18.683843] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   19.641354] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9I am going to use a bit of guesswork here. The module dell-laptop sometimes, but not always interferes with the correct operation of wireless. Presses of the wireless switch don't always get properly translated into kernel messages. Let's remove it temporarily and see if the wireless improves:```
sudo rmmod -f dell-laptop
dmesg | grep iwl
```Please look for and post messages after [ 3801.064020]. Thanks.

---

### Post by hiever1 on 2011-01-02
> tristan@tristan-laptop:~$ sudo rmmod -f dell-laptop
ERROR: Removing 'dell_laptop': No such file or directory


We got a problem.

---

### Post by chili555 on 2011-01-02
> tristan@tristan-laptop:~$ lsmod | grep dell
dell_wmi 2852 0
[COLOR="Red"]dell_laptop[/COLOR] 5730 0
dcdbas 5402 1 dell_laptop I thought it was loaded. Please check again.```
lsmod | grep dell
modinfo dell-laptop
```

---

### Post by hiever1 on 2011-01-02
lsmod | grep dell
modinfo dell-laptop 

> tristan@tristan-laptop:~$ lsmod | grep dell
dell_wmi                2852  0 
tristan@tristan-laptop:~$ 
tristan@tristan-laptop:~$ modinfo dell-laptop
filename:       /lib/modules/2.6.35-23-generic/kernel/drivers/platform/x86/dell-laptop.ko
alias:          dmi:*svnDellComputerCorporation.:*:ct8:*
alias:          dmi:*svnDellInc.:*:ct8:*
license:        GPL
description:    Dell laptop driver
author:         Matthew Garrett <mjg@redhat.com>
srcversion:     937E56ACAE113942D6266C1
depends:        dcdbas
vermagic:       2.6.35-23-generic SMP mod_unload modversions 686

And 

> tristan@tristan-laptop:~$ sudo rmmod -f dell-laptop
ERROR: Removing 'dell_laptop': No such file or directory 			 		


---

### Post by hiever1 on 2011-01-03
Ok, a little more info. When I connect to my network, I enter my password and then it just keep trying to connect then the light will flash.

---

### Post by chili555 on 2011-01-04
Either your driver, Network Manager or wpa_supplicant have problems in two areas. I don't know which. First, it can be troublesome to connect to SSIDs with a space, such as "Chili House." If yours has a space, try changing to something else, such as, "ChiliHouse."

Second, many routers have a mixed WPA and WPA2 mode. The intent, I believe, is to be backwards compatible with older hardware that may not be WPA2 capable. If yours is so configured, you will have better luck with WPA ***or*** WPA2; not both.

Finally, have you double-checked the password? Does it work seamlessly in other computers on the network?

---

### Post by hiever1 on 2011-01-04
1. No spaces.
2. I think this is it. My netowork is WPA.
3. It's correct.

---

### Post by SaintDanBert on 2011-01-04
> **chili555 said:**
> Fascinating. Although rfkill list all shows no hardware or software switches that are interfering with the operation of your wireless card, dmesg suggests it is...

There are reported bugs with the Intel module, **iwlagn**, used for the 3965 and other Intel wifi-parts.

I did not have inclination to chase kernel editions and module builds and such to implement many of the available patches and work-arounds.
I found that troubles "went away" using the [highlight]wicd[/highlight] package of wireless manager in place of **network-manager**. Your mileage may vary.

PM if you want more details of replacing net-mgr with wicd.

Bonne chance,
~~~ 0;-Dan

---

### Post by hiever1 on 2011-01-05
Ok I got wifi to work. Now the light keeps flashing. Any ideas?

---

### Post by chili555 on 2011-01-05
My 3945ABG works perfectly and the light flickers, too. Is there supposed to be something wrong with that?

---

### Post by SaintDanBert on 2011-01-05
> **SaintDanBert said:**
> ...
PM if you want more details of replacing net-mgr with wicd.
...

We started a PM conversation to accomplish the swap. Once all of the bodies are cleared and blood washed away, we'll report back with
the details.

[highlight]Does anyone know [/highlight] what the blinking wifi-LED means? My laptop shows several patterns:
[list]
[*]fast blink
[*]slow blink
[*]long pause LED on
[*]long pause LED off
[/list]
This is in addition to the general no-LED=radio-off vs. LED=radio-on.


~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-01-05
[highlight]Re: blinking wifi LED[/highlight]

I found the following at: [https://bbs.archlinux.org/viewtopic.php?id=74269](https://bbs.archlinux.org/viewtopic.php?id=74269)
> 
========== Member: wankel wrote on 2009-08-28 ==========
I have finally found a solution to this issue on my Dell Vostro 1400. Wireless card is iwl3945 and has that really annoying blinking.

First create this file:

**vim noblink.sh**

and put the following in the file:

[b]echo none > /sys/class/leds/iwl-phy0::RX/trigger
echo none > /sys/class/leds/iwl-phy0::TX/trigger
echo none > /sys/class/leds/iwl-phy0::radio/trigger
echo none > /sys/class/leds/iwl-phy0::assoc/trigger[/b]

[indent]
*SaintDanBert -- I confirmed that Ubuntu Lucid in fact has the several /sys/class/leds/iwl* objects. I have not confirmed that this works.*
[/indent]

Make it executable:

**chmod +x noblink.sh**

and finally run it as root:

**sudo ./noblink.sh**

Now you will have a constantly lit wireless led smile


I don't know if there are formal, ui-based ways to configure wifi-LED behavior. The wifi driver for Intel parts is **iwlagn** and it serves a multitude of net adapters.

The existence of the RX and TX objects tells me that the wifi-LED serves several purposes:
[list]
[*] TX+RX data transfer happening
[*] ON to indicate "radio on", "associated" and "authenticated"
[*] OFF to indicate "radio off" or "not associated" or "not authenticated"
[/list]

I agree with folks who say blinking for TX-RX is eye-noise that is not needed.

~~~ 0;-Dan

---

### Post by hiever1 on 2011-01-05
It doesn't find the file when I make it exe.

---

### Post by ekjsim on 2011-01-05
Why not try installing the latest compat-wireless and see whether it fixes the issue.

---

### Post by chili555 on 2011-01-05
> The wifi driver for Intel parts is **iwlagn** and it serves a multitude of net adapters.Some, but not all. Intel parts are also driven by ipw2100, ipw2200 and iwl3945.

---

### Post by SaintDanBert on 2011-01-06
> **chili555 said:**
> Some, but not all. Intel parts are also driven by ipw2100, ipw2200 and iwl3945.

You are correct in naming these other drivers for "Intel" parts.
My experience is with more recent details. I know that at some point **iwlagn** "replaced" **iwl4695** and the **ipw *** modules
in the distros I work with.

Intel is very good with their linux support. See here for details:
[http://intellinuxwireless.org/](http://intellinuxwireless.org/) quoting from those pages:
[indent]
[i]There used to be a driver specific for the 3945 hardware (ipw3945 hosted on ipw3945.sourceforge.net). This project is **deprecated**, please use the iwlwifi driver instead.

Projects for **older hardware** are hosted on Sourceforge:

     Intel® PRO/Wireless 2100 Network Connection adapter
     Intel® PRO/Wireless 2200BG Network Connection adapter
     Intel® PRO/Wireless 2915ABG Network Connection adapter

Drivers for the 2100/2200/2915 devices can be found in any recent kernel so it is not necessary to obtain the source code from the project page. Even so, their project pages do still contain some useful information as well as the firmware. [/i]
[/indent]

I don't know the details of **iwlagn** vs. **iwlwifi** mentioned at the Intel site.  I'll do some reading and report back to this thread.

Cheers,
~~~ 0;-D

==============================
I found the following at:
[http://wiki.debian.org/iwlagn](http://wiki.debian.org/iwlagn)
[indent][i]
**iwlagn** is a module for the Intel Wireless WiFi Link 4965AGN, 5100AGN, 5300AGN, 5350AGN, 5150AGN, 1000BGN, 6200AGN, 6300AGN and 6250AGN series of devices. This driver is included in the mainline Linux kernel since 2.6.27 and present in Debian kernel images since 2.6.28.1 Supported devices are listed at the end of this page.

Non-free firmware is required, which can be provided by the **firmware-iwlwifi** package since version 0.15.2 Firmware must be installed prior to device operation. 
...
```

PCI: 8086:0083 Intel Corporation Centrino Wireless-N 1000
PCI: 8086:0084 Intel Corporation Centrino Wireless-N 1000
PCI: 8086:0086 Intel Corporation (Device name unknown)
PCI: 8086:0087 Intel Corporation Centrino Advanced-N + WiMAX 6250
PCI: 8086:0088 Intel Corporation (Device name unknown)
PCI: 8086:0089 Intel Corporation Centrino Advanced-N + WiMAX 6250
PCI: 8086:008D Intel Corporation (Device name unknown)
PCI: 8086:008E Intel Corporation (Device name unknown)
PCI: 8086:4229 Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
PCI: 8086:422B Intel Corporation Centrino Ultimate-N 6300
PCI: 8086:422C Intel Corporation Centrino Advanced-N 6200
PCI: 8086:4230 Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
PCI: 8086:4232 Intel Corporation WiFi Link 5100
PCI: 8086:4235 Intel Corporation Ultimate N WiFi Link 5300
PCI: 8086:4236 Intel Corporation Ultimate N WiFi Link 5300
PCI: 8086:4237 Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
PCI: 8086:4238 Intel Corporation Centrino Ultimate-N 6300
PCI: 8086:4239 Intel Corporation Centrino Advanced-N 6200
PCI: 8086:423A Intel Corporation PRO/Wireless 5350 AGN [Echo Peak] Network Connection
PCI: 8086:423B Intel Corporation PRO/Wireless 5350 AGN [Echo Peak] Network Connection
PCI: 8086:423C Intel Corporation WiMAX/WiFi Link 5150
PCI: 8086:423D Intel Corporation WiMAX/WiFi Link 5150

```
[/i][/indent]
(emphasis added)

---

### Post by chili555 on 2011-01-06
> iwlagn is a module for the Intel Wireless WiFi Link 4965AGN, 5100AGN, 5300AGN, 5350AGN, 5150AGN, 1000BGN, 6200AGN, 6300AGN and 6250AGN series of devices.But not 3945ABG, the subject of this thread.> There used to be a driver specific for the 3945 hardware (ipw3945 hosted on ipw3945.sourceforge.net). This project is deprecated, please use the iwlwifi driver instead.iwlwifi is in Ubuntu as a system, but not a stand-alone driver; viz:> /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/[COLOR="Red"]iwlwifi[/COLOR]/iwl3945.ko> Projects for **older** hardware are hosted on Sourceforge:

Intel® PRO/Wireless 2100 Network Connection adapter
Intel® PRO/Wireless 2200BG Network Connection adapter
Intel® PRO/Wireless 2915ABG Network Connection adapterYes, indeed. There is plenty of older hardware around here, primarily because it works perfectly well with Ubuntu and doesn't have the steep hardware requirements of those proprietary operating systems.

Some of us old semi-retired investors living on a fixed income would love to have a 6300AGN system!

---

### Post by hiever1 on 2011-01-06
Flashing gone! Thanks guys!

---

### Post by SaintDanBert on 2011-01-06
1.  What was your choice at resolution so that others might do similar things?

2.  Pleae use Thread Tools to mark this item SOLVED.

Congratualtions,
~~~ 0;-Dan

---

### Post by hiever1 on 2011-01-06
1. Done
2. Wrong password lol.

---

### Post by SaintDanBert on 2011-01-06
> **hiever1 said:**
> ...
2. Wrong password ...

We all have a huge collection of THOSE tee shirts...

Cheers,
~~~ 0;-Dan

---

### Post by tylersontag on 2011-03-15
Ever since i upgraded to the latest version of Ubuntu (10.10) i've been getting REALLY lousy performance out of my wireless adapter (An intel 3945abg) I used to get ~1MB/S intranetwork transfers prior to the upgrade.  Now i really only average 200kb/s... which is horrible trying to move multi-gig files.  I changed my network to ONLY allow G network traffic and haven't seen any affect.

Other computers on the network get ~2MB/S and if i change to a wired connection, i get 7MB/s transfer time all to the same folder.

Any ideas on what i can change to improve performance?

---

