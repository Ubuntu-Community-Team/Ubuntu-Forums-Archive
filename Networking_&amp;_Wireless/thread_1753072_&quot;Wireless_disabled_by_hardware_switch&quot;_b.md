---
title: "&quot;Wireless disabled by hardware switch&quot; bug? - Natty"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by eruheru on 2011-05-08
Hey all, just upgraded to natty and am having trouble with wireless. It won't let me activate the wireless through hardware switch or from the dropdown. I've tried doing rfkill unblock all as per other threads which then lists everything as unblocked but nothing actually changes to the system. 
I'm on an acer 3935
from rfkill list

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: acer-threeg: Wireless WAN
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

after rfkill unblock all

0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: acer-threeg: Wireless WAN
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

Thanks so much

---

### Post by eruheru on 2011-05-10
Bump. Please help me!

---

### Post by chili555 on 2011-05-10
> 0: acer-wireless: Wireless LAN
Soft blocked: no
Hard blocked: no
1: acer-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
2: acer-threeg: Wireless WAN
Soft blocked: no
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
5: hci0: Bluetooth
Soft blocked: no
Hard blocked: noWhen you get to this point, your wireless should work, assuming you have a working driver and the ethernet is disconnected. What is your wireless device?```
lspci -nn
```

---

### Post by eruheru on 2011-05-11
from lspci -nn
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]

Should I assume it's a driver issue? I've never had problems with it before. 
thanks

---

### Post by chili555 on 2011-05-11
> Should I assume it's a driver issue? I've never had problems with it before. I doubt it is, but let's check:```
dmesg | grep iwl
```

---

### Post by eruheru on 2011-05-11
```
[   26.303940] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   26.303943] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   26.304026] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.304035] iwlagn 0000:04:00.0: setting latency timer to 64
[   26.304067] iwlagn 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   26.325946] iwlagn 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   26.325949] iwlagn 0000:04:00.0: Device SKU: 0Xb
[   26.325970] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   26.326054] iwlagn 0000:04:00.0: irq 47 for MSI/MSI-X
[   26.363112] iwlagn 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[   26.369240] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  300.028498] iwlagn 0000:04:00.0: RF_KILL bit toggled to disable radio.

```

---

### Post by chili555 on 2011-05-11
Everything looks perfect until here:> iwlagn 0000:04:00.0: RF_KILL bit toggled to disable radio.Let's have a look at:```
lsmod | grep-e acer -e wmi
```

---

### Post by eruheru on 2011-05-11
okay, I got

snd_rawmidi            30486  1 snd_seq_midi
acer_wmi               23771  0 
sparse_keymap          13898  1 acer_wmi
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

---

### Post by SpaceMaster on 2011-05-13
I've been closely monitoring this thread, because I've been having a similar problem with my HP Pavilion.  The wireless refused to toggle back on when I hit the switch.

full details here -> [HP Pavilion Wireless Enable/Disable Button 11.04]("http://ubuntuforums.org/showthread.php?p=10812226#post10812226")

quick summary:
-turns out the wireless button has a software switch with "Disabled," "Enabled but off," and "Enabled & on" states
-Natty Narwhal only toggled the first 2
-still had Windows Vista w/manufacturer's wireless util on comp
-boot into Vista, open util (in my case, HP Wireless Assistant)
-use button to toggle from "Disabled" to "Enabled but off"
-used HP's wireless util to then switch to "Enabled and On"
-reboot
-now afraid to bump wireless button again.

Don't know how this will translate onto an Acer, and I don't know if you're dual-booting or not, so I don't know how much help this'll be.  Plus, I never actually figured out WHY it reverted to off on each boot.

---

### Post by smodon on 2011-05-14
same **** here on an thinkpad x201. additionally, i cannot connect to 802.11a WLANs anymore since upgrading to 11.04 :X

---

### Post by abisdad on 2011-05-14
I think I've similar problems here too!  I've posted on [11.04 "Natty wireless issue - Acer - Device not ready, rfkill soft auto blocked"]("http://ubuntuforums.org/showthread.php?p=10748476#post10748476") but had no replies as yet.

I've an Acer TravelMate TM8372T-354G32Mibb and it appears that my wireless is automatically soft blocked almost immediately I unblock it, by either using the "Fn+F3" or "sudo rfkill unblock all".

Any suggestions gratefully received! [-o<

Thanks,  Rob.

---

### Post by RBLevin on 2011-05-23
Same problem here. Lenovo S12. There are MANY threads about this problem on the web. Nobody has seemed to come up with a fix. One common denominator seems to be the Broadcom wireless chipset. I have tried everything suggested, to no avail. At the end of the day, upgrading to 11.04 stepped on my WiFi, and I now have no wireless capability. I even went out and bought a D-Link USB WiFi device which is natively supported. Doesn't work. Same error message: Wireless disabled by hardware switch. Something is rotten.

---

### Post by chili555 on 2011-05-24
Did you check the thread referenced above? I magically solved the problem twice.

---

### Post by RBLevin on 2011-05-24
> **chili555 said:**
> Did you check the thread referenced above? I magically solved the problem twice.

Yep. No luck. Here's the output:

```
xxx@xxx-xxx:~$ sudo rmmod -f acer-wmi
[sudo] password for xxx: 
xxx@xxx-xxx:~$ sudo rfkill unblock all
xxx@xxx-xxx:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
xxx@xxx-xxx:~$ 

```

Wireless switch is ON. Hit Fn+F5 a few times. No luck. Here's what I see: [http://yfrog.com/niworkspace1199p]("http://yfrog.com/niworkspace1199p")


Frustrating. I actually installed Debian 6 last night because I am so frustrated with the bugs and instability in Natty. I feel like a traitor, having used and evangelized Ubuntu for many years. But I am seriously considering just moving to Debian at this point.

---

### Post by chili555 on 2011-05-24
> Frustrating. I actually installed Debian 6 last night because I am so frustrated with the bugs and instability in Natty. I feel like a traitor, having used and evangelized Ubuntu for many years. But I am seriously considering just moving to Debian at this point.Do the Fn+F5 buttons work in Debian? I'd be interested in what the differences are. For instance:```
modinfo ideapad-laptop
```Is acer-wmi loaded in Ubuntu? In Debian?

---

### Post by RBLevin on 2011-05-24
> **chili555 said:**
> Do the Fn+F5 buttons work in Debian? I'd be interested in what the differences are. For instance:```
modinfo ideapad-laptop
```Is acer-wmi loaded in Ubuntu? In Debian?

Here's the output on the host OS (Ubuntu 11.04):

```
:~$ modinfo ideapad-laptop
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/platform/x86/ideapad-laptop.ko
license:        GPL
description:    IdeaPad ACPI Extras
author:         David Woodhouse <dwmw2@infradead.org>
srcversion:     458EF0B5AF996ABEDC03545
alias:          acpi*:VPC2004:*
depends:        sparse-keymap
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           no_bt_rfkill:No rfkill for bluetooth. (bool)

```

Since Debian is running in a VM, would the output still be helpful?

Here's the output of rfkill with the D-Link USB wireless dongle attached. (I have Broadcom 4312 on the mobo [STA driver], which doesn't work, and added a D-Link DWA-160A2 USB wireless, which also doesn't work. Same error message for both.)

```

:~$ sudo rmmod -f acer-wmi
:~$ sudo rfkill unblock all
:~$ rfkill list all
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
7: phy2: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Thanks.

---

### Post by chili555 on 2011-05-24
> Since Debian is running in a VM, would the output still be helpful?Yep, as well as:```
rfkill list all
```Have you exhausted every option on the Broadcom? Is the required firmware in place?

---

### Post by _murphy_ on 2011-05-24
The very same problem here:

Lenovo S10-3s

rfkill list all

0: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no

1: ideapad_bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no

2: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: yes

3: hci0: Bluetooth
Soft blocked: no
Hard blocked: no



no acer nor dell drivers loaded. broadcom kernel drivers loaded, installed, uninstalled several times, still no wifi.

do not want to install windows just to enable driver . . .


:sad:

---

### Post by chili555 on 2011-05-24
> **_murphy_ said:**
> no acer nor dell drivers loaded. broadcom kernel drivers loaded, installed, uninstalled several times, still no wifi.

do not want to install windows just to enable driver . . .
:sad:Mind if we have a peek?```
lsmod
```Thanks.

---

### Post by _murphy_ on 2011-05-24
lsmod:

```
Module                  Size  Used by
parport_pc             32111  1 
ppdev                  12849  0 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
rfcomm                 38125  8 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
sco                    17779  2 
bnep                   17785  2 
snd_seq_midi           13132  0 
l2cap                  48656  16 rfcomm,bnep
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
i915                  450944  3 
snd_timer              28659  2 snd_pcm,snd_seq
lib80211_crypt_tkip    17203  0 
psmouse                73312  0 
videodev               75143  1 uvcvideo
wl                   2642531  0 
btusb                  18160  1 
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
ideapad_laptop         13262  0 
sparse_keymap          13666  1 ideapad_laptop
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  2 
libahci                25548  1 ahci
tg3                   131476  0

```

I thank you

---

### Post by chili555 on 2011-05-24
I'm googling. It's a known bug. You may wish to register at Launchpad and add your comments.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773918](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773918)

---

### Post by chili555 on 2011-05-24
YIKES!!

[https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/730972](https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/730972)> I stumbled upon the same problem here on

Linux sat4 2.6.38-8-generic #41-Ubuntu SMP Tue Apr 5 19:30:49 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

As said in #4 system immediately freezes when trying to access (iwlist scan, activate in KDE network manager, ...) the Wifi device with brcm80211 loaded.

In the case of Broadcom STA I figured out that according to [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) [B]the driver itself might not have support for rfkill in kernel 2.6.38? I'm unable to rfkill unblock the device due to its "Hard blocked: yes" status as said in #1.
[/B]
I wonder why it worked in Ubuntu 10.10, the Broadcom STA release version there was 5.60.48.36 too, but this release had no support for Kernel > 2.6.32.


---

### Post by chili555 on 2011-05-24
Sorry to use the forum as a notepad, but this is important stuff. From the Broadcom link above:> WHAT'S NEW IN RELEASE 5.100.82.38
---------------------------------
+ Support for bcm43227 and bcm43228
+ Fix for issue where iwconfig was sometime reporting rate incorrectly
+ Supports rfkill in kernels 2.6.31 to 2.6.36
+ Supports scan complete event (SIOCGIWSCAN)
+ Adds EAGAIN (busy signal) to query of scan results
So it appears that rfkill is ***NOT*** supported in 2.6.38-8, the kernel Natty uses.

Proposed options:[LIST]
[*]Revert to 10.10
[*]Ndiswrapper
[/LIST]Comments, Ubuntians??

---

### Post by bkratz on 2011-05-24
Looking at the site
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
you will see that those drivers were published in Dec of last year (before 11.04), but there is a patch for kernels >37 there too.

---

### Post by RBLevin on 2011-05-24
> **chili555 said:**
> Yep, as well as:```
rfkill list all
```Have you exhausted every option on the Broadcom? Is the required firmware in place?

Well, the firmware *should *be in place. I've been using this PC with Ubuntu since v10.04. The 11.04 upgrade stepped on my wireless config and it hasn't worked since. And as I mentioned earlier in this thread, this is clearly a common problem. Lots of people and threads complaining they lost their wireless and can't get it back, and it seems especially bad with Broadcom chipsets. Lots of wild goose chases to fix the problem. Nothing seems to work. Common denominator is the message, "Wireless disabled by hardware switch."

I've uninstalled and reinstalled drivers. Used B43, STA, etc. Nothing worked. I thought if I put a USB device into the mix, that anything related to the Broadcom problem would be avoided. But as I stated earlier, that didn't work. Gets the same error message. So the problem is deeper than drivers or a given chipset's firmware.

I'll report the Debian info when I get a chance to hit the Lenovo and fire up the VM (I'm on a different PC at the moment).

---

### Post by RBLevin on 2011-05-24
> **chili555 said:**
> Sorry to use the forum as a notepad, but this is important stuff. From the Broadcom link above:So it appears that rfkill is ***NOT*** supported in 2.6.28-8, the kernel Natty uses.

Proposed options:[LIST]
[*]Revert to 10.10
[*]Ndiswrapper
[/LIST]Comments, Ubuntians??

NDISWRAPPER doesn't work. Been there, done that, got the T-shirt.

I don't think it's a driver problem. I think it goes deeper than that. I've plugged other USB WiFi adapters into the PC -- devices that are natively supported by Ubuntu -- and they are detected, the drivers load, and the same exact error message appears when you look for wireless networks: Wireless disabled by hardware switch.

Whatever causes THAT error message is at the root of this problem. If I knew how to, I'd search the source code for the conditions that cause that error.

Unfortunately, all the fixes I have seen to date -- and I have spent many days and nights researching this -- seem to be variations of swapping drivers in and out.

---

### Post by chili555 on 2011-05-24
> **bkratz said:**
> Looking at the site
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
you will see that those drivers were published in Dec of last year (before 11.04), but there is a patch for kernels >37 there too.Did you look at the patch? I doubt it has anything to do with rfkill:> -		init_MUTEX(&wl->sem);
+		sema_init(&wl->sem, 1);Our old friend the MUTEX change.

---

### Post by chili555 on 2011-05-24
> **RBLevin said:**
> Well, the firmware *should *be in place. I've been using this PC with Ubuntu since v10.04. The 11.04 upgrade stepped on my wireless config and it hasn't worked since. And as I mentioned earlier in this thread, this is clearly a common problem. Lots of people and threads complaining they lost their wireless and can't get it back, and it seems especially bad with Broadcom chipsets. Lots of wild goose chases to fix the problem. Nothing seems to work. Common denominator is the message, "Wireless disabled by hardware switch."

I've uninstalled and reinstalled drivers. Used B43, STA, etc. Nothing worked. I thought if I put a USB device into the mix, that anything related to the Broadcom problem would be avoided. But as I stated earlier, that didn't work. Gets the same error message. So the problem is deeper than drivers or a given chipset's firmware.

I'll report the Debian info when I get a chance to hit the Lenovo and fire up the VM (I'm on a different PC at the moment).I wonder if the Broadcom wl driver is causing the problem, even with the USB dongles. Have you tried blacklisting it?

---

### Post by RBLevin on 2011-05-24
> **chili555 said:**
> I'm googling. It's a known bug. You may wish to register at Launchpad and add your comments.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773918](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773918)

Good find, thanks. I've also seen several reports on Launchpad related to this.

These threads may also be related/useful, but nothing in any of them has enabled my Lenovo S12's wireless:

[http://ubuntuforums.org/showthread.php?t=1744892](http://ubuntuforums.org/showthread.php?t=1744892)

[http://ubuntuforums.org/showthread.php?p=10183902&posted=1#post10183902](http://ubuntuforums.org/showthread.php?p=10183902&posted=1#post10183902)

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

[http://ubuntuforums.org/showthread.php?p=10824088#post10824088](http://ubuntuforums.org/showthread.php?p=10824088#post10824088)

[http://ubuntuforums.org/archive/index.php/t-948475.html](http://ubuntuforums.org/archive/index.php/t-948475.html)

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by RBLevin on 2011-05-24
> **chili555 said:**
> I wonder if the Broadcom wl driver is causing the problem, even with the USB dongles. Have you tried blacklisting it?

Hmm. No. Will try that and report back.

---

### Post by chili555 on 2011-05-24
> **RBLevin said:**
> Hmm. No. Will try that and report back.Of course, a super-nerd could also try swapping the wireless card itself for another that is supplied in Ideapads. I am going to buy a new Lenovo at some point; I shall avoid the Broadcom.

---

### Post by RBLevin on 2011-05-24
> **chili555 said:**
> Of course, a super-nerd could also try swapping the wireless card itself for another that is supplied in Ideapads. I am going to buy a new Lenovo at some point; I shall avoid the Broadcom.

Heh

I have a new Lenovo X220 arriving (hopefully) this week. Preloaded with Windows 7. I'm just going to use that as the host and install Linux in VBox VMs. Then I won't have to deal with any driver issues. And I won't have to deal with Windows or commercial software -- or upgrades that step on my once-working config.

---

### Post by _murphy_ on 2011-05-25
> **RBLevin said:**
> Hmm. No. Will try that and report back.


I was trying to uninstall STA drivers and let Ubuntu use some generic one. Whenever I soft unblock the driver, the whole system freezes (even the mouse pointer)  . . .


I will try to compile STA drivers with new patch published 2 days ago at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by chili555 on 2011-05-25
Please see post #27 above. I think the patch will make the driver compile under Natty, but I doubt it will work. Support for rfkill is evidently not yet written in to the driver. In any event, we await your report.

---

### Post by RBLevin on 2011-05-25
> **_murphy_ said:**
> I was trying to uninstall STA drivers and let Ubuntu use some generic one. Whenever I soft unblock the driver, the whole system freezes (even the mouse pointer)  . . .


I will try to compile STA drivers with new patch published 2 days ago at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I'm able to uninstall STA via System | Administration | Additional Hardware, but that doesn't change anything. I also then installed the B43 driver, but that did not work or even load. I haven't gone into Synaptic and physically removed anything, but that is on my to-test list.

B43Cutter doesn't work for me. I never see the UI after I launch the tool. I get help text instead.

---

### Post by chili555 on 2011-05-25
It may not be readily evident to all the Broadcom fans (??) but the STA driver applies to one group of cards and b43 applies to another wholly separate group. They cannot be interchanged. Look at the pci.id for your card. Here's an example:> Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)In this example, 14E4:4318 is driven by b43 and ssb:```
$ modinfo ssb  | grep 4318
alias:          pci:v000014A4d0000[COLOR="Red"]4318[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4318[/COLOR]sv*sd*bc*sc*i*
```It is not claimed by wl:```
$ modinfo wl  | grep 4318
$
```Long story short, you must use the driver appropriate to your device and none other will work.

---

### Post by RBLevin on 2011-05-25
> **chili555 said:**
> It may not be readily evident to all the Broadcom fans (??) but the STA driver applies to one group of cards and b43 applies to another wholly separate group. They cannot be interchanged. Look at the pci.id for your card. Here's an example:In this example, 14E4:4318 is driven by b43 and ssb:```
$ modinfo ssb  | grep 4318
alias:          pci:v000014A4d0000[COLOR="Red"]4318[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4318[/COLOR]sv*sd*bc*sc*i*
```It is not claimed by wl:```
$ modinfo wl  | grep 4318
$
```Long story short, you must use the driver appropriate to your device and none other will work.

Thanks. That was not apparent to me. There are threads out there that instruct users to remove STA and install B43, and they claim it works, but is not as fast in terms of DTR and also has weaker reception.

For example from here: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
> 
b43/b43legacy drivers conflicts with broadcom-wl otherwise known as Broadcom's 802.11 Linux STA driver or broadcom-sta. Make sure that if you want to use b43 in favour of broadcom-sta and your Broadcom wireless chipset is supported from the device list you will need to either remove or unload the broadcom-wl driver first prior to using b43 by following: How do I use b43/b43legacy driver instead of broadcom-wl?


That would explain why it didn't work or even load for me. ;-) That raises the question, though, if there is an open source driver for the STA series ... ?

---

### Post by chili555 on 2011-05-25
> **b43/b43legacy drivers conflicts with broadcom-wl** otherwise known as Broadcom's 802.11 Linux STA driver or broadcom-sta. Make sure that if you want to use b43 in favour of broadcom-sta and your Broadcom wireless chipset is supported from the device list you will need to either remove or unload the broadcom-wl driver first prior to using b43 by following: How do I use b43/b43legacy driver instead of broadcom-wl? The highlighted part is just plain wrong. It's not the first, last or only misconception about Broadcom drivers on the web.> if there is an open source driver for the STA series ... ? I am not aware of one. bcmwl-kernel-source is proprietary as well as the driver you download from Broadcom.

This begs the question: what is your pci.id and is it driven by wl? If rfkill is not yet included in wl and you are running Natty, I believe it won't work and any discussion of wl is needless.> There are threads out there that instruct users to remove STA and install B43I have not yet seen a pci.id that is claimed by both b43/ssb and wl. I am open to being disproven.

---

### Post by eelfner on 2011-05-29
Facing the "Wireless disabled by hardware switch" bug, I found my wife's wireless USB adapter (D-Link DWA-125) worked fine. I ordered one with hopes to buy time for the fantastic ubuntu community to create an equally no-brainer solution that does not involve an extra appendage on my laptop.

---

### Post by kuvanito on 2011-06-04
i am right with you eelfner
i got a compaq presario cq60 and have the same problem
i had to physically remove the mini pci card from the laptop to by pass the switch issue and inserted an old belkin g usb card and woola! i got wireless now but hate the 3" thing hanging out to the side,every now and then it gets wacked!
come on team,we now know it's a driver issue,go get it boy!

---

### Post by kuvanito on 2011-06-04
zhit!!!!!!!!
i fixed it
just a minute after i posted above
this is what i did:
1-open a terminal
2-rfkill list
  (0: hp-wifi: Wireless LAN)
  (Soft blocked: yes)
  (Hard blocked: no)
  (1: phy0: Wireless LAN)
  (Soft blocked: yes)
  (Hard blocked: yes)
3-rfkill unblock 0: hp-wifi
4-rfkill unblock 1: phy0
5-rfkill list
  (0: hp-wifi: Wireless LAN)
  (Soft blocked: no)
  (Hard blocked: no)
  (1: phy0: Wireless LAN)
  (Soft blocked: no)
  (Hard blocked: no)

after this my wifi button turned on BLUE baby BLUE and now i am typing from my internal wifi. :p :p :p

---

### Post by chili555 on 2011-06-04
> **kuvanito said:**
> zhit!!!!!!!!
i fixed it
just a minute after i posted above
this is what i did:
1-open a terminal
2-rfkill list
  (0: hp-wifi: Wireless LAN)
  (Soft blocked: yes)
  (Hard blocked: no)
  (1: phy0: Wireless LAN)
  (Soft blocked: yes)
  (Hard blocked: yes)
3-rfkill unblock 0: hp-wifi
4-rfkill unblock 1: phy0
5-rfkill list
  (0: hp-wifi: Wireless LAN)
  (Soft blocked: no)
  (Hard blocked: no)
  (1: phy0: Wireless LAN)
  (Soft blocked: no)
  (Hard blocked: no)

after this my wifi button turned on BLUE baby BLUE and now i am typing from my internal wifi. :p :p :pWhen you say, "Gowsh, my guru frens, how do I make this permanent?" we'll be waiting with a suggestion.

---

### Post by kuvanito on 2011-06-04
i am watching this thread now
what do you mean?
i just posted how i fixed my problem and here i am typing again from my wifi,it's fixed and looks permanent! i have rebooted three times just to check it out and as soon as my laptop comes on the wifi button lights up BLUE! hooray!

1-open a terminal and type rfkill list
2-check to see if you have any software blocked (yes)
3-then rfkill unblock ??? what ever you got blocked and bingo!

---

### Post by chili555 on 2011-06-04
I mean, if you have to type the command every time you boot and you'd like your machine to boot already unblocked, I can help. If your machine boots up all ready to go, then you don't need any help from me.

OK?

---

### Post by kuvanito on 2011-06-04
thank you but nope,i don't need your help,it's fixed for good!!!

---

### Post by nm_geo on 2011-06-04
Let us also not forget if you ever had the wl driver installed.  You have b43 blacklisted.

Some Natty user have installed the Maverick version of the wl driver with good results.

I have Maverick running on this laptop with the older wl and it does just fine. 

I have Lucid, Natty, Xbuntu 11.04, Fedora15 and Oneiric on the same laptop all running well on the b43 driver with ssb module.  And i happen to run some speed tests today all were good. In fact the b43 performs a little better than the wl on Maverick.

Like Chili said if you want help finding a solution give the results to the code.

```
lspci -nn
```The Broadcom version number mean little, but the pc:id number helps.

---

### Post by MountainX on 2011-07-16
> **nm_geo said:**
> 

Like Chili said if you want help finding a solution give the results to the code.

```
lspci -nn
```The Broadcom version number mean little, but the pc:id number helps.

Thanks. I could use some help. I have a Thinkpad x120e with 11.04 and all updates. 

My wifi is hardblocked. The Fn-F5 switch only enables/disables bluetooth. Wifi remains hardblocked always.

For the kernel power bug, I applied the fix listed here:
[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)
which is to add "pcie_aspm=force" to this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"

Here's my other info
$ uname -a
Linux laptop 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 athlon i386 GNU/Linux

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

$ rfkill list
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

$ rfkill unblock 1:phy0

$ rfkill list
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

After toggling Fn-F5 once, here are the results:

$ rfkill list
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no

toggling again returns wifi to the original state:
phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by chili555 on 2011-07-17
> My wifi is hardblocked. The Fn-F5 switch only enables/disables bluetooth. Wifi remains hardblocked always.May we see:```
lsmod
```Thanks.

---

### Post by greenblob on 2011-07-17
Lots of people have been having this issue on ACER devices.

**A very common & easy fix for this is to hold down the wifi switch/button for around 2 seconds BEFORE ubuntu boots (while on BIOS start-up screen) while turning your laptop on.**

I'm not sure as to how or why this works, but I think it's in relation to the device's default drivers being overridden by Ubuntu when is starts up. 

11.04 (natty) & above has lots of driver & hardware issues, if things like this are important to you I'd recommend going a step back to 10.04 which is MUCH more stable.

---

### Post by MountainX on 2011-07-17
> **chili555 said:**
> May we see:```
lsmod
```Thanks.

Sure, thanks for the help. Here it is:

Module                  Size  Used by
nfs                   282952  2 
lockd                  74292  1 nfs
fscache                50364  1 nfs
nfs_acl                12771  1 nfs
auth_rpcgss            39173  1 nfs
sunrpc                199096  15 nfs,lockd,nfs_acl,auth_rpcgss
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_conexant    43782  1 
rfcomm                 38125  8 
snd_hda_codec_hdmi     27535  1 
binfmt_misc            13213  1 
sco                    17827  2 
snd_hda_intel          24140  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_hda_codec          90901  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8192ce             120858  0 
thinkpad_acpi          73750  0 
rtlwifi                78961  1 rtl8192ce
mac80211              257001  2 rtl8192ce,rtlwifi
snd_seq_midi           13132  0 
uvcvideo               66851  0 
joydev                 17322  0 
videodev               75143  1 uvcvideo
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
cfg80211              156212  2 rtlwifi,mac80211
psmouse                73312  0 
snd_timer              28659  2 snd_pcm,snd_seq
btusb                  18160  2 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
k10temp                12951  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd                    55295  15 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
nvram                  14035  1 thinkpad_acpi
fglrx                2434640  92 
video                  18951  0 
sp5100_tco             13456  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
ahci                   21591  4 
uas                    17676  0 
r8169                  42534  0 
libahci                25548  1 ahci

---

### Post by MountainX on 2011-07-17
> **greenblob said:**
> Lots of people have been having this issue on ACER devices.

**A very common & easy fix for this is to hold down the wifi switch/button for around 2 seconds BEFORE ubuntu boots (while on BIOS start-up screen) while turning your laptop on.**

I'm not sure as to how or why this works, but I think it's in relation to the device's default drivers being overridden by Ubuntu when is starts up. 
.

Does it matter if this is a cold boot or a restart? Just to be sure, I tried it both ways and my wifi was still hard blocked even after holding down Fn-F5 during the bios start up screen.

---

### Post by MountainX on 2011-07-17
> **MountainX said:**
> Thanks. I could use some help. I have a Thinkpad x120e with 11.04 and all updates. 

My wifi is hardblocked. The Fn-F5 switch only enables/disables bluetooth. Wifi remains hardblocked always.



**Wow, I feel stupid**. I checked my bios setup screen and found that there is a setting in the bios that turns the wifi radios off. I have no idea how it got set to "off." I don't even remember seeing it before. But I changed the setting and now wifi is no longer hard blocked. Wifi immediately started working again as soon as I booted up. Even the password was still saved, etc. It just worked immediately. 

Could a kernel upgrade cause a bios setting to change? Doubtful, right? Or could losing power (running battery all the way down)? I guess it is possible I changed the setting myself, but I sure don't remember doing that!

---

### Post by chili555 on 2011-07-17
removed

---

### Post by Wilbefast on 2011-08-16
I have this problem whenever the computer is booted with the switch off. Turning the switch while running is not recognised so I've needed to shut down, switch on and start back up (Dell Vostro 1510, Ubuntu 11.04 64bit). This worked for me:

**rkill unblock all**

---

### Post by lenooh on 2011-10-07
I had a similar problem on a HP ProBook 4730s (Ubuntu 11.10., Oneiric Beta 2). 

Everything worked out of the box (wired, wireless, bluetooth), until I pressed the button for wireless switching:
wireless became disabled by hardware and there was no way to enable it, no matter how many times I pressed it. Changing the BIOS settings did not enable it.

So the solution that worked for me was:
- enable the LAN/WLAN switch in BIOS
- boot to Ubuntu, plug a LAN cable, wait a few seconds then unplug the LAN cable
- wireless should now be enabled by hardware switch (although it says device not ready)
- restart and it works

Have fun!

---

### Post by photosyn on 2011-10-16
I'm having a Wireless disabled problem with Natty and have tried all I could find in these threads but still can't fix.  

below is the rfkill list.  I see that my wireless is hard blocked but don't know how to unblock it.   

charlie@Dilo-Wolf:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


I have tried rfkill unblock all and that doesn't seem to work.  Also have tried pushing down the wireless button (F11 on this computer) prior to booting, while booting and while booted.    Doesn't work at all.  

Thanks for your help.

---

### Post by photosyn on 2011-10-16
I'm a dope, Function F11 turns on/off the wireless.  Now I can turn it on manually that way, but it would be great if someone could tell me how to fix this permanently as I have to manually turn on the wireless every time I boot the computer.

And Fn-F11 held down while booting permanently fixes the problem.  Hopefully this addendum will help others.

---

### Post by michealk on 2011-10-21
I had this problem with my Lenovo X120e. Wireless showed up as disabled in Ubuntu 11.10. Checked BIOS settings and wireless *was* set to enabled. There is no physical wireless enable/disable switch on the X120e. Fn-F5 may turn wifi on/off, but Ubuntu didn't support this.

I had removed Windows 7 entirely, so wasn't able to boot into Windows to try re-enabling it there.

Struggled with this for a few days with no luck. I then happened to try booting a Linux Mint 11.10 CD (to test something else), and lo and behold wireless started to work.

Don't know exactly what Mint does differently, and haven't had time to look - but thought I'd share just in case someone has more time than I do :-)

---

### Post by tent405 on 2011-12-08
> **michealk said:**
> 
Struggled with this for a few days with no luck. I then happened to try booting a Linux Mint 11.10 CD (to test something else), and lo and behold wireless started to work.

Don't know exactly what Mint does differently, and haven't had time to look - but thought I'd share just in case someone has more time than I do :-)

Similar problem with a Lenovo Ideapad v570, with an Intel Centrino 6150.

Turned out needed to install a package called firmware-iwlwifi. That's why Mint works: it has the non-free firmware already loaded. 

This problem is a systemic problem resulting from proprietary licenses on firmware. If hardware manufacturers would GPL their code I would have never had this problem to begin with.

---

### Post by chili555 on 2011-12-08
> **tent405 said:**
> 
This problem is a systemic problem resulting from proprietary licenses on firmware. If hardware manufacturers would GPL their code I would have never had this problem to begin with.You're right. It's refreshing to see that someone recognizes that manufacturers have a role to play in all this. If it's the slightest consolation, Intel is actually pretty good about this. Broadcom is...well, not so good. Other manufacturers are rather nightmares.

I'm glad you got it sorted and thanks for posting back so the searchers will learn from your experience.

---

### Post by maartsen on 2012-01-02
I also had this problem. And I fixed it by using the initramfs.

With initramfs you can sequence the way modules are loaded. You need to put hp-wmi (or what ever WiFi driver you are using) before ath5k (the phy0 wifi)!!

So edit the "/etc/initramfstools.d/modules" file as SUDO and add first the hp-wmi and on the next line ath5k.

Run as "sudo update-initramfs -u" and reboot. This should clear any blocks. If they remain, use rfkill unblock all to get ride of them.

This solution will survive a reboot, but the blocks will return when you switch off the wireless via network-control. But on the bright side, after a reboot everything should be back to normal ;-)

Cheers,
Michel

---

### Post by ilyich on 2012-01-22
Hello.
I have a similar problem on lenovo x121e:
phy0 is 
 - Soft blocked after the restart
 - Hard blocked after suspend (and nothing helps to unblock it, only restart)
I have Intel Centrino Wireless-N 1000 network card and iwlagn 3.0.0-15-generic driver
Ubuntu 11.10
Nothing helps. Have no idea what to do with it.

---

### Post by chili555 on 2012-01-22
> **ilyich said:**
> Hello.
I have a similar problem on lenovo x121e:
phy0 is 
 - Soft blocked after the restart
 - Hard blocked after suspend (and nothing helps to unblock it, only restart)
I have Intel Centrino Wireless-N 1000 network card and iwlagn 3.0.0-15-generic driver
Ubuntu 11.10
Nothing helps. Have no idea what to do with it.Let's see the exact wording of:```
rfkill list all
lsmod
```Thanks.

---

### Post by ilyich on 2012-01-22
There are two sets of output: after reboot and after suspend (they seems different)
Just after reboot:
===============
```

$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
``````

$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
joydev                 17393  0 
binfmt_misc            17292  1 
thinkpad_acpi          73942  0 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  509487  2 
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
iwlagn                273944  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              393459  1 iwlagn
cfg80211              172427  2 iwlagn,mac80211
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
psmouse                73673  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
drm_kms_helper         32889  1 i915
drm                   192194  3 i915,drm_kms_helper
rts_pstor             353227  0 
nvram                  14029  1 thinkpad_acpi
serio_raw              12990  0 
tpm_tis                14002  0 
i2c_algo_bit           13199  1 i915
lp                     17455  0 
video                  18908  1 i915
wmi                    18744  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
atl1c                  36638  0 
ahci                   21634  2 
libahci                25727  1 ahci
```After suspend:
============
```

$ rfkill list all
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
``````

$ lsmod
Module                  Size  Used by
iwlagn                273944  0 
mac80211              393459  1 iwlagn
cfg80211              172427  2 iwlagn,mac80211
atl1c                  36638  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
joydev                 17393  0 
binfmt_misc            17292  1 
thinkpad_acpi          73942  0 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  509487  2 
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
psmouse                73673  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mei                    36466  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
drm_kms_helper         32889  1 i915
drm                   192194  3 i915,drm_kms_helper
rts_pstor             353227  0 
nvram                  14029  1 thinkpad_acpi
serio_raw              12990  0 
tpm_tis                14002  0 
i2c_algo_bit           13199  1 i915
lp                     17455  0 
video                  18908  1 i915
wmi                    18744  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
libahci                25727  1 ahci
```------------------------
Thank you for helping.

---

### Post by chili555 on 2012-01-22
This is a new one on me, so it may take some experimentation to stumble on a reasonable answer.> After suspend:
============
```
$ rfkill list all
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```Please suspend and then let me see:```
rfkill list all
sudo modprobe -r thinkpad-acpi
sudo modprobe thinkpad-acpi
rfkill list all
```Have we made any difference? My hope is to figure out an answer and write a script or a conf file or similar that runs as you resume.

---

### Post by ilyich on 2012-01-23
Hello, there are results (after modprobe both - soft/hard blocked):
```
$ rfkill list all
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
princessa@princessa-think:~$ sudo modprobe -r thinkpad-acpi
princessa@princessa-think:~$ sudo modprobe thinkpad-acpi
princessa@princessa-think:~$ rfkill list all
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
3: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
```--------------
Thanks.

---

### Post by chili555 on 2012-01-24
Wow! You are soft-blocked, hard-blocked and every-blocked! What is happening with the Fn+F5 key combination all this time? Is there any acknowledgement from the wireless LED? Please try:```
rfkill list all
sudo rfkill unblock all
rfkill list all
```Now press the Fn+F5 combination and run the sequence again. Is there any change? Does the machine even recognize the key presses?

---

### Post by volksy on 2012-02-05
Similar problems here, I'm a newb to Ubuntu but just upgraded to 11:10.

Acer Aspire 5732Z The wifi will run on start up for a reasonable length of time, then suddenly drop out, only way to get it back up is to reboot, hardware switch does nothing at all - LED doesn't light, switch is dead.

Right clicking on the WIFI icon at the top right shows everything ok, but when it drops off I get the infamous @Wifi disabled by hardware switch and the options are greyed out.

rfkill unblock all doesn't work on the hardblocked 'yes'

It's driving me nuts!! Any help much appreciated!!

---

### Post by chili555 on 2012-02-05
Is the module acer-wmi loaded?```
lsmod | grep acer
```Try to remove it and see if the behavior improves:```
sudo rmmod -f acer-wmi
```Post back and let us know.

---

### Post by volksy on 2012-02-06
Nope, shows "no such file or directory"

So I assume there is something missing?

Seems that most people have no connection at all, why would mine suddenly deactive the (dead) switch?

---

### Post by chili555 on 2012-02-06
> Nope, shows "no such file or directory"Which command shows that?

---

### Post by volksy on 2012-02-06
The second one.


chris@chris-Aspire-5732Z:~$ sudo rmmod -f acer-wmi
[sudo] password for chris: 
ERROR: Removing 'acer_wmi': No such file or directory
chris@chris-Aspire-5732Z:~$

---

### Post by chili555 on 2012-02-06
So I guess acer-wmi was *not* loaded. Was acer-something else? Or none whatever?

Shortcut: please just show me:```
lsmod
```

---

### Post by volksy on 2012-02-06
Haha, probably the best idea, as I have no idea what's on or not...

chris@chris-Aspire-5732Z:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
lib80211               14570  1 wl
arc4                   12473  2 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
brcmsmac              591864  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                63474  0 
brcmutil               16885  1 brcmsmac
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  509522  3 
snd_timer              28932  2 snd_pcm,snd_seq
mac80211              393459  1 brcmsmac
mxm_wmi                12859  0 
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172427  2 brcmsmac,mac80211
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
crc_ccitt              12595  1 brcmsmac
video                  18908  1 i915
soundcore              12600  1 snd
wmi                    18744  1 mxm_wmi
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
coretemp               13188  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25761  1 ahci
atl1c                  36638  0 
chris@chris-Aspire-5732Z:~$ 


Hope this helps. Thanks for having a look!

Chris

---

### Post by chili555 on 2012-02-06
> wl 2646601 0
brcmsmac 591864 0
brcmutil 16885 1 brcmsmac
mac80211 393459 1 brcmsmacMan! That's quite a pile of possibly conflicting wireless drivers there! Let's troubleshoot; please post:```
lspci -nn | grep 0280
```We probably need to blacklist or remove a few things.

---

### Post by volksy on 2012-02-06
Here you go:

chris@chris-Aspire-5732Z:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)

---

### Post by chili555 on 2012-02-06
> **volksy said:**
> Here you go:

chris@chris-Aspire-5732Z:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)Please do:```
sudo modprobe -r wl
```Is your wireless still working?```
iwconfig
```Does it work better? If so, we can remove *wl* permanently.

---

### Post by volksy on 2012-02-06
Done that, wireless is still working. 

Typically, like when you take your car into the shop, it's not dropped out in a while either! :roll:

---

### Post by chili555 on 2012-02-06
> **volksy said:**
> Done that, wireless is still working. 

Typically, like when you take your car into the shop, it's not dropped out in a while either! :roll:Please let us know. Upon reboot, the change will go away; you'll need to rmmod *wl* again. If it seems to help, we can remove it permanently.

---

### Post by volksy on 2012-02-07
Well, I left the computer running overnight, an this morning it dropped out and hard blocked itself. 

Is there further drivers to block/remove? 

Regards,

Chris

---

### Post by chili555 on 2012-02-07
> an this morning it dropped out and hard blocked itself.Let's look at power management. After you reboot and the wireless is working again, run:```
iwconfig
```What does it say about power management? Does it drop and hard block if you do:```
sudo iwconfig wlan0 power off
```

---

### Post by volksy on 2012-02-07
results of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Bellmount"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:F0:16:5A   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2518   Missed beacon:0

As for for the power off command, no.

chris@chris-Aspire-5732Z:~$ sudo iwconfig wlan0 power off
[sudo] password for chris: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
chris@chris-Aspire-5732Z:~$

---

### Post by deh on 2012-02-09
Just to add to the pervasiveness of this problem, I have an Acer Aspire One: AOA 150-1635 netbook with this wireless problem.  

I have Ubuntu 10.10 installed and the wireless works OK.  Yesterday, I tried Ubuntu 11.10 on an USB drive and the wireless shows the problems in the foregoing posts.  The USB drive with 11.10 works OK in my Toshiba laptop.  I then tried Ubuntu 10.04 and 10.04 LTS on an USB drive and these did not work on the Acer netbook, but they worked OK on the Toshiba.  Ubuntu 10.10 on an USB drive worked OK in both machines.

So far none of the fixes in the previous posts have worked to make 11.10 work.  Since the netbook works OK with the installed Ubuntu 10.10 there is no pressing need to fix the 11.10 USB drive.  However, I want to send a USB drives with some other programs loaded to a couple of chaps that have company laptops and they don't want to rock the boat with their IT dept installing some Linux distro.  I wanted to be sure the USB drive worked OK before I sent it, and not knowing what machines they had, I tested it on all the machines I have, and as a result stumbled into the Acer problem.

---

### Post by volksy on 2012-02-11
The fault seems to be getting worse. Wifi only lasts for about 5 mins. If it comes up at all on reboot.

Any ideas anyone?

---

### Post by ogranadino on 2012-05-19
Well the solution is here.
Remove the file NetworkManager.conf (weirds configs use to store there)

sudo rm  /etc/NetworkManager/NetworkManager.conf

Then do

sudo rfkill unblock all
rfkill list all

:guitar:

Thats all.
Works for me, now the on/off switch works.

---

### Post by johnh44 on 2012-05-23
> **smodon said:**
> same **** here on an thinkpad x201. additionally, i cannot connect to 802.11a WLANs anymore since upgrading to 11.04 :X

Same here on a Dell D630 laptop

---

### Post by Askme Later on 2012-05-27
Try shutting down(if not already off), disconnecting the power, remove  battery(if it is a laptop), press power a few times to release stored  energy, reinsert battery(if it is a laptop), reconnect AC power. Turn on  computer. Worked for me. After trying multiple fixes I found on the  internet I remembered reading this somewhere. My hardware was blocked  via a hardware switch(fn+f8 which doesn't work in ubuntu(works with  windows, but uninstalled windows). rfkill showed 0: phy0: Wireless Lan  as Hard Blocked.

---

### Post by SkipHuffman on 2012-05-28
Alright, I have just tried this on my new HP Pavilion g series.   Lets see if the wifi dies faster than it takes to deliver a crappy pizza.


> **ogranadino said:**
> Well the solution is here.
Remove the file NetworkManager.conf (weirds configs use to store there)

sudo rm  /etc/NetworkManager/NetworkManager.conf

Then do

sudo rfkill unblock all
rfkill list all

:guitar:

Thats all.
Works for me, now the on/off switch works.

---

### Post by ogranadino on 2012-06-01
and?

> **SkipHuffman said:**
> Alright, I have just tried this on my new HP Pavilion g series.   Lets see if the wifi dies faster than it takes to deliver a crappy pizza.

---

### Post by volksy on 2012-06-17
> **ogranadino said:**
> Well the solution is here.
Remove the file NetworkManager.conf (weirds configs use to store there)

sudo rm  /etc/NetworkManager/NetworkManager.conf

Then do

sudo rfkill unblock all
rfkill list all

:guitar:

Thats all.
Works for me, now the on/off switch works.

Doesn't work with mine sadly - :(

rm: cannot remove `/etc/networkmanager.conf': No such file or directory

---

### Post by chili555 on 2012-06-18
> rm: cannot remove `/etc/networkmanager.conf': No such file or directoryBut the request was:```
sudo rm [COLOR="Red"]/etc/NetworkManager/NetworkManager.conf[/COLOR]

Then do

sudo rfkill unblock all
rfkill list all
```It appears that's not what you typed.

---

### Post by Mr.Dee on 2012-06-19
I went through the thread, but didn't notice anyone mention resetting CMOS.  I have a Lenovo s-10 netbook.  Apparently there is a bug in the bios which can only be resolved by resetting CMOS.  This bug occurs when using the physical wireless on/off switch.  It was a pain to reset it since I had never taken apart a laptop before.  After I reset it worked fine.  I took a tooth pick and dabbed it with crazy glue so I would never use the switch again or accidently move it.

---

### Post by volksy on 2012-06-19
OK, I've done as instructed for the removal of the Network manager file. I had typed it incorrectly the first time. 
 
The switch does now work, but after a while it then loses wifi and no amount of switch pressing or 'rfkill unblock all' will bring the wifi back to life. It still states it is Hardblocked under the 'list all' command no matter what I do.
 
Any ideas, it's getting to the stage where it is begining to become unusable, and as I only have the choice of Wifi - no wired connection in my home.
 
Thanks in advance.

---

### Post by ziocarlone on 2012-06-19
I had the same problem with official driver on my Broadcom 4311, so I installed the unofficial and free driver and it started working well.

---

### Post by Majisto on 2012-08-09
I had the same issue with my laptop. I disabled the wireless to connect a wired network cable for some testing. When I was done, I couldn't re-enable my wireless. I tried the whole RFKILL thing and had no luck. I  read many other post and tried their solutions with no luck..until I came across a one post. In the post they said to use a"Fn+F2" to try and re-enable the wireless card. That particular key combination wouldn't work for me, but it did make me think. So, I tried holding down the function key while using the hardware switch. Amazingly, this worked for me. Don't ask my why it worked, but it did.

I hope this helps others out there.

---

### Post by pyro.xyz on 2012-08-09
Hey, SpaceMaster and smodon, I think that I figured out the problem. I tried bumping the wireless switch a couple of times, and it activated the driver (assuming that's the problem.) For me, the driver was activated, but not being used, and bumping the switch apparently caused the driver to feel obligated to become useful. Hope that helped.

---

