---
title: "Amilo A1650G WLAN problem in 9.10 Karmic"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by Jupeli on 2010-02-11
I spent a whole day Googling and banging my head to the wall trying to get the WLAN working on my laptop with a freshly installed Ubuntu. The laptop is the Fujitsu-Siemens Amilo A1650G and according to what I've read, many others have had problems with this laptop as well. I have read many threads regarding this problem but nothing seems to work for me. It's as if the laptop has never even heard of having a WLAN card inside. I have no other means of connecting the laptop to the Internet either. 

However, I can access the net via another laptop that has Windows XP so if I have to download something I can do it on this laptop and use an USB memory stick to tranfer files between these two computers.

This is my first venture outside Windows so I haven't really got a clue. Please let me know what I need to do in order for you to be able to help me out.

---

### Post by chili555 on 2010-02-11
The first step is find out what you have and where you are. Please open Applications -> Accessories -> Terminal and run these two separate commands and please post the result:```
lspci -nn | grep Network
iwconfig
```Thanks.

---

### Post by Jupeli on 2010-02-11
It says:

```
lo        no wireless extensions.
```
And nothing else.

Thanks.

---

### Post by chili555 on 2010-02-11
Do you mean that this command also returns nothing?```
lspci -nn | grep Network
```What kind of wireless card do you have??

---

### Post by Jupeli on 2010-02-11
> **chili555 said:**
> Do you mean that this command also returns nothing?```
lspci -nn | grep Network
```What kind of wireless card do you have??
Yes, it returns nothing. This is exactly similar to what I have: [Lite-On Mini WLAN Card 802.11 WN2302A-F4 ](http://cgi.ebay.co.uk/Lite-On-Mini-WLAN-Card-802.11-WN2302A-F4-Fujitsu-Amilo_W0QQitemZ260547364854QQcmdZViewItemQQimsxq20100203?IMSfp=TL100203158002r7148#ht_500wt_975)

---

### Post by chili555 on 2010-02-11
> Atheros AR5001We're closer, yet farther. Please post:```
lspci -nn
rfkill list
lsmod
```> It's as if the laptop has never even heard of having a WLAN card inside. Indeed! My favorite kind of problem: it all looks great but it simply doesn't work. Where is my sledgehammer?

---

### Post by Jupeli on 2010-02-11
Return of "lspci -nn":
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
02:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
02:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:09.2 Multimedia video controller [0400]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
02:09.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
```

"rfkill list" returns nothing.

Return of "lsmod":
```
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
usb_storage            52544  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_atiixp_modem       11940  0 
snd_atiixp             15720  2 
snd_ac97_codec        101216  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
pcmcia                 36808  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd                    59204  15 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
tifm_7xx1               5372  0 
tifm_core               7832  1 tifm_7xx1
joydev                 10272  0 
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
snd_page_alloc          9156  3 snd_atiixp_modem,snd_atiixp,snd_pcm
i2c_piix4               9932  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
k8temp                  4188  0 
shpchp                 32272  0 
psmouse                56180  0 
serio_raw               5280  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp
```

---

### Post by Jupeli on 2010-02-11
Uh, while I opened the cover to make sure of what wireless card mine is, I also happened to note that the plug of the processor fan was disconnected. I connected it and tried the 
```
lspci -nn | grep Network
iwconfig
```
again. Now it returned:
```

lo    no wireless extensions
eth0  no wireless extensions

```
The previous message was after connecting the plug as well.

Pretty surprising, by the way, how well this computer worked despite the lack of cooling... :D

---

### Post by chili555 on 2010-02-11
In System -> Administration -> Hardware Drivers do you see an option to activate your Atheros Communications Inc. AR2413 802.11bg NIC?

Do you have internet connectivity, through your wired ethernet card?

---

### Post by Jupeli on 2010-02-11
> **chili555 said:**
> In System -> Administration -> Hardware Drivers do you see an option to activate your Atheros Communications Inc. AR2413 802.11bg NIC?
When I open the "Hardware Drivers" it opens a window that says:
> Software modem
Tested by the Ubuntu developers
License: Proprietary
 The SmartLink modem daemon is the application part of the driver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) The old driver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be either recent ALSA (shipped with a newer kernel (>=2.6.4) with Alsa support and intel8x0m module) which is sufficient for basic operation and data/Internet connection, or the SmartLink kernel driver which is provided by separate packages which you can build using the source from the sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.
Then it says "This driver is not activated." and then there is a button that says "Activate". It doesn't say a word about "Atheros Communications Inc. AR2413 802.11bg NIC", though. My guess would be to hit that curiously labeled button, "Activate", or what?
 
> **chili555 said:**
> Do you have internet connectivity, through your wired ethernet card?
I do now. I think next time I should check all electrical connections FIRST. I do feel stupid now. The wlan isn't yet working, though, but a large step closer I think.

---

### Post by chili555 on 2010-02-11
I don't think we need to enable the modem and let's see if we have another method to get your Atheros going. Please do:```
sudo apt-get install linux-backports-modules-karmic-generic
sudo modprobe ath5k
iwconfig
```Do we now have a wireless interface?

---

### Post by Jupeli on 2010-02-11
> **Jupeli said:**
> My guess would be to hit that curiously labeled button, "Activate", or what?
So that's what I did. Now I have a window that says "Downloading and installing driver..." but there is absolutely no progress to be seen. Nothing seems to be happening. Edit: Cancelled that.

---

### Post by chili555 on 2010-02-11
I think you can cancel out of that. We're not interested in the dial-up modem.

---

### Post by Jupeli on 2010-02-11
```
sudo apt-get install linux-backports-modules-karmic-generic
```This returns an error. It says that package linux-backports-modules-karmic-generic was not found.

---

### Post by chili555 on 2010-02-11
Open System -> Admin -> Synaptic and go to Settings -> Repositories and make sure the correct repos are enabled. Press Reload and then search for 'backports' and install linux-backports-modules-karmic-generic. Please see attached. Select the correct server if you are not in the USA.

---

### Post by Jupeli on 2010-02-11
It helped, I now have the linux-backports-modules-karmic-generic installed succesfully.
This:
```

sudo modprobe ath5k
iwconfig
```returns:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by chili555 on 2010-02-11
Well, rats! May we please see:```
dmesg | grep ath
```Thanks.

---

### Post by Jupeli on 2010-02-11
That returned:
```
[    2.062262] device-mapper: multip[COLOR=Red]ath[/COLOR]: version 1.1.0 loaded
[    2.062268] device-mapper: multip[COLOR=Red]ath[/COLOR] round-robin: version 1.0.0 loaded
[   88.503566] [COLOR=Red]ath[/COLOR]5k 0000:02:05.0: enabling device (0014 -> 0016)
[   88.503580] [COLOR=Red]ath[/COLOR]5k 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   88.503647] [COLOR=Red]ath[/COLOR]5k 0000:02:05.0: registered as 'phy0'
[   88.514078] [COLOR=Red]ath[/COLOR]5k phy0: failed to wakeup the MAC Chip
[   88.514102] [COLOR=Red]ath[/COLOR]5k 0000:02:05.0: PCI INT A disabled
[   88.516539] [COLOR=Red]ath[/COLOR]5k: probe of 0000:02:05.0 failed with error -5
```

---

### Post by chili555 on 2010-02-11
Is there any change in System -> Administration -> Hardware Drivers? Would you please reboot and let us see:```
dmesg | grep ath
lsmod | grep ath
iwconfig
```Man! We are so close!

---

### Post by Jupeli on 2010-02-11
No changes in Hardware Drivers.
After reboot
"dmesg | grep ath" returned:
```
[    2.070266] device-mapper: multipath: version 1.1.0 loaded
[    2.070272] device-mapper: multipath round-robin: version 1.0.0 loaded
```
"lsmod | grep ath" returned nothing
and "iwconfig" returned:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by chili555 on 2010-02-11
Please do:```
sudo gedit /etc/modules
```Add a new line:```
ath5k
```Proofread, save and close gedit. Reboot and please do:```
dmesg | grep ath
lsmod | grep ath
iwconfig
```Thanks.

---

### Post by underquark on 2010-02-11
For what it's worth, my wife had a Fujitsu Amilo (running Win XP) and it did, indeed, have no wireless module in it even though it was supposed to.  Neither did its replacement which was from the same batch released by Fujitsu that all turned out to have no functioning wireless module.

---

### Post by Jupeli on 2010-02-11
After editing the /etc/modules like you suggested,
```
dmesg | grep ath
```
returns:
```
[    2.058232] device-mapper: multip[COLOR=Red]ath[/COLOR]: version 1.1.0 loaded
[    2.058238] device-mapper: multip[COLOR=Red]ath[/COLOR] round-robin: version 1.0.0 loaded
[    8.693594] [COLOR=Red]ath[/COLOR]5k 0000:02:05.0: enabling device (0014 -> 0016)
[    8.693606] [COLOR=Red]ath[/COLOR]5k 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    8.693664] [COLOR=Red]ath[/COLOR]5k 0000:02:05.0: registered as 'phy0'
[    8.704122] [COLOR=Red]ath[/COLOR]5k phy0: failed to wakeup the MAC Chip
[    8.704145] [COLOR=Red]ath[/COLOR]5k 0000:02:05.0: PCI INT A disabled
[    8.705150] [COLOR=Red]ath[/COLOR]5k: probe of 0000:02:05.0 failed with error -5

```
```
lsmod | grep ath
```
returns:
```
[COLOR=Red]ath[/COLOR]5k                 121988  0 
mac80211              210572  1 [COLOR=Red]ath[/COLOR]5k
[COLOR=Red]ath[/COLOR]                     8444  1 [COLOR=Red]ath[/COLOR]5k
cfg80211              130632  3 [COLOR=Red]ath[/COLOR]5k,mac80211,[COLOR=Red]ath[/COLOR]
led_class               4096  1 [COLOR=Red]ath[/COLOR]5k

```
and
```
iwconfig
```
returns once again:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

underquark, the wireless was working fine back when this laptop had Windows XP.

---

### Post by chili555 on 2010-02-11
Pretty obviously, this is the problem:> ath5k phy0: failed to wakeup the MAC ChipIt is a known bug:  [https://help.ubuntu.com/community/NC20#Wireless](https://help.ubuntu.com/community/NC20#Wireless)

I am also interested in this:  [http://forum.ts.fujitsu.com/forum/viewtopic.php?f=89&t=34742](http://forum.ts.fujitsu.com/forum/viewtopic.php?f=89&t=34742)  especially:> 
Re: [Li2735] Wireless broken in Linux

Postby tigertailz on Wed Mar 25, 2009 22:49
It works without a hardware mod with a program called acerhk. I am wondering if this is actually plausible. Could this be a hotkey issue? Does your wirless key turn the LED on and off? Does it seem responsive? Please post:```
lsmod | grep acer
```Puzzling. Thanks.

---

### Post by Jupeli on 2010-02-11
Thinking of the problem, maybe it's that I just can't turn the wlan card on. With the WinXP that came with the laptop, the wireless used to be toggled on and off with a quick button and a led would light up to indicate that it's on. In Ubuntu, that button does nothing.
Edit: Oh, you posted while I was typing. Let's see...

---

### Post by Jupeli on 2010-02-11
> **chili555 said:**
> Could this be a hotkey issue? Does your wirless key turn the LED on and off? Does it seem responsive? Please post:```
lsmod | grep acer
```
This returned:
```
Usage: lsmod
No command 'acer' found, did you mean:
 Command 'ace' from package 'libace-perl' (universe)
acer: command not found

```

I think this very well could be a hotkey issue.

---

### Post by chili555 on 2010-02-11
```
lsmod | grep acer
```I think you hit a wrong key, please try again. That first character is an L, not a One.

---

### Post by Jupeli on 2010-02-11
Oops, I had the | in wrong place. Now it was right and it returned nothing.

---

### Post by chili555 on 2010-02-11
From the acerhk README:> What is this driver good for?
*****************************

This driver will give access to the special keys on notebooks of the
Acer Travelmate series, which are not handled by the keyboard
driver.
It also works on notebooks from other manufacturers (some Medion,
[COLOR="Red"]Fujitsu-Siemens[/COLOR], ...).

It also has some other related functionality (depending on the model):
- controlling LEDs (Mail, Wireless)
- [COLOR="Red"]enable/disable wireless hardware[/COLOR]Hmmm. Interesting! Are you ready to try it?

---

### Post by chili555 on 2010-02-11
Let's try something else first:```
sudo rmmod ath5k
sudo modprobe acer-wmi
sudo modprobe ath5k
iwconfig
```Any good news?

---

### Post by Jupeli on 2010-02-11
"iwconfig" still returns the same as before but after ```
sudo modprobe acer-wmi
``` the orange led for the wireless lighted up.

---

### Post by chili555 on 2010-02-11
Well, we are closer yet. 

Let's see what *dmesg* says post 8.705150:```
dmesg | grep ath
dmesg | grep acer
```

---

### Post by Jupeli on 2010-02-11
```
dmesg | grep ath
``` says ```
[    2.066265] device-mapper: multipath: version 1.1.0 loaded
[    2.066272] device-mapper: multipath round-robin: version 1.0.0 loaded
[    8.850229] ath5k 0000:02:05.0: enabling device (0014 -> 0016)
[    8.850241] ath5k 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    8.850301] ath5k 0000:02:05.0: registered as 'phy0'
[    8.860684] ath5k phy0: failed to wakeup the MAC Chip
[    8.860704] ath5k 0000:02:05.0: PCI INT A disabled
[    8.861520] ath5k: probe of 0000:02:05.0 failed with error -5
[  234.324669] ath5k 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  234.324765] ath5k 0000:02:05.0: registered as 'phy1'
[  234.335228] ath5k phy1: failed to wakeup the MAC Chip
[  234.335266] ath5k 0000:02:05.0: PCI INT A disabled
[  234.341599] ath5k: probe of 0000:02:05.0 failed with error -5

```
and ```
dmesg | grep acer
``` says ```
[  144.586698] acer-wmi: Acer Laptop ACPI-WMI Extras
[  144.589815] Registered led device: acer-wmi::mail

```

---

### Post by chili555 on 2010-02-11
Here is what I suggest you do:```
sudo apt-get install build-essential linux-headers-generic module-assistant acerhk-source
cd /usr/src
sudo su
tar -xvjf acerhk.tar.bz2
cd modules/acerhk
make
make install
```I got this to compile without errors, but one negligible warning. Please post back if you see an error.```
exit
sudo rmmod ath5k
sudo modprobe acerhk autowlan=1
sudo modprobe ath5k
iwconfig
```Do you have a wireless interface?

If this works, we will need to take a few steps to get this to work permanently. If not, let's see our old pal:```
dmesg | grep ath5k
```

---

### Post by Jupeli on 2010-02-11
> **chili555 said:**
> Here is what I suggest you do:```
sudo apt-get install build-essential linux-headers-generic module-assistant acerhk-source
cd /usr/src
sudo su
tar -xvjf acerhk.tar.bz2
cd modules/acerhk
make
make install
```I got this to compile without errors, but one negligible warning. Please post back if you see an error.
I also saw no errors but one warning.

> **chili555 said:**
> ```
exit
sudo rmmod ath5k
sudo modprobe acerhk autowlan=1
sudo modprobe ath5k
iwconfig
```Do you have a wireless interface?
No such luck, iwconfig still returns the same as before.

> **chili555 said:**
> If this works, we will need to take a few steps to get this to work permanently. If not, let's see our old pal:```
dmesg | grep ath5k
```
Apparently it didn't work. Here's what our old pal said:
```
[    8.850229] ath5k 0000:02:05.0: enabling device (0014 -> 0016)
[    8.850241] ath5k 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    8.850301] ath5k 0000:02:05.0: registered as 'phy0'
[    8.860684] ath5k phy0: failed to wakeup the MAC Chip
[    8.860704] ath5k 0000:02:05.0: PCI INT A disabled
[    8.861520] ath5k: probe of 0000:02:05.0 failed with error -5
[  234.324669] ath5k 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  234.324765] ath5k 0000:02:05.0: registered as 'phy1'
[  234.335228] ath5k phy1: failed to wakeup the MAC Chip
[  234.335266] ath5k 0000:02:05.0: PCI INT A disabled
[  234.341599] ath5k: probe of 0000:02:05.0 failed with error -5
[ 4105.549267] ath5k 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 4105.549428] ath5k 0000:02:05.0: registered as 'phy2'
[ 4105.559928] ath5k phy2: failed to wakeup the MAC Chip
[ 4105.559963] ath5k 0000:02:05.0: PCI INT A disabled
[ 4105.567414] ath5k: probe of 0000:02:05.0 failed with error -5

```

---

### Post by chili555 on 2010-02-11
Does manipulating the wireless key do anything significant? What does this say?```
dmesg | grep acer
```> [ 4105.559928] ath5k phy2: failed to wakeup the MAC Chip
What a lazy module!

---

### Post by Jupeli on 2010-02-11
The key seems to do absolutely nothing. ```
dmesg | grep acer
``` says ```
[  144.586698] acer-wmi: Acer Laptop ACPI-WMI Extras
[  144.589815] Registered led device: acer-wmi::mail

```

---

### Post by chili555 on 2010-02-11
No evidence whatever of the insertion of *acerhk*. This gets crazier by the moment. I have to pour a scotch and think about this a while.

This is what I am studying now:  [https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123](https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123)

---

### Post by Jupeli on 2010-02-11
> **chili555 said:**
> No evidence whatever of the insertion of *acerhk*. This gets crazier by the moment. I have to pour a scotch and think about this a while.

This is what I am studying now:  [https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123](https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123)
From that thread: [quote=moma]The driver/module name is "acerhk.ko", and "sudo make install" will copy it from compilation directory to /lib/modules/$(uname -r)/extra/.
Check if you find it there.
$ ls -l /lib/modules/$(uname -r)/extra/[/quote]
This returns: ```
total 52
-rw-r--r-- 1 root root 50553 2010-02-11 21:44 acerhk.ko

```So if I understand this, it means that the acerhk does at least exist on the computer? Uhh... This is weird, huh?

Also:
[quote=moma]You must also run
$ sudo depmod -a
afterwards.[/quote]
What should it do? Should I try it?

Edit: Have to get some sleep now, an important exam tomorrow.

---

### Post by oldefoxx on 2010-02-12
It's late and I need to get to bed.  My wife left me to do the same hours ago, cutting down the heat, and it is beginning to get cold in here.

That said, lspci is assuming that the wireless card is a PCI plug-in card like you would find in a desktop.  Ain't no such critter in most laptops, but they can sometimes work a specific port controller in, so it might be there.  What others have found is that some OEMs just adopt a USB to LAN ethernet and USB to wireless adapter in liew of the PCI approach.  These won't show up under lspci.  you can use the extensive lshw or the more specific lsusb instructions to see it this might be what you have.

But you can do better than that add the given wireless card nomenclature in you network searches, plus a few appropriate terms, like Ubuntu OR Linux, and see if you can find out a few particulars about that wireless adapter.  One thing you are probably already aware of is that regardless of the brand name they are sold under, the chipsets and software in the adapters tend to run in certain families, and you probably need to find out which chip set you probably have used for wireless, and that should steer you towards the right driver.

And there may be some additional commands needed to activate your wireless adapter.  Make note of references to ifconfig, iwconfig, and similar efforts to bring matters under control.  You may have to try these.  Then some complain that they have to do this every time they turn their notebooks on, and some other people will steer you towards creating a startup script file to do that for you.

One of the things I found that helped me was replacing network-manager and network-manager-gnome with another package named wicd.  Just use a package manager to get wicd, such as apt-get install wicd, and it will remove the other two packages automatically.  It really helped a lot, though I can't quite say how or why.

It took weeks of twiddling before I got my notebook to work wirelessly, but now I might venture to say it even works flawlessly.
Hope you get it done faster but with equal success.

---

### Post by Jupeli on 2010-02-12
The hotkeys are now working, thanks to this:
[QUOTE=http://damagedspline.blogspot.com/]```
$ echo options acerhk autowlan=1 force_series=5020 | sudo tee -a /etc/modprobe.d/options
$ echo acerhk | sudo tee -a /etc/modules
$ sudo rmmod acerhk > /dev/null 2>&1 ; sudo modprobe acerhk autowlan=1 force_series=5020
```[/QUOTE]
No luck with getting the wireless to work, though, but I think this is a big step closer.

Edit:
```
dmesg | grep ath5k

``` now says: ```
[    8.594717] ath5k 0000:02:05.0: enabling device (0014 -> 0016)
[    8.594730] ath5k 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    8.594782] ath5k 0000:02:05.0: registered as 'phy0'
[    8.605250] ath5k phy0: failed to wakeup the MAC Chip
[    8.605273] ath5k 0000:02:05.0: PCI INT A disabled
[    8.605848] ath5k: probe of 0000:02:05.0 failed with error -5

```and ```
iwconfig
``` returns ```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by chili555 on 2010-02-12
> [    8.605250] ath5k phy0: failed to wakeup the MAC ChipHow do you feel about pin 13?

[http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI)

---

### Post by Jupeli on 2010-02-12
> **chili555 said:**
> How do you feel about pin 13?

[http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI)
YESS! I'm online via wireless right now. I really appreciate your help, thank you. I am now absolutely convinced that there is nothing in the whole world that can't be fixed with tape. :D

---

### Post by chili555 on 2010-02-12
Great! I am so happy that it's working for you. Have fun and welcome to the wonderful world of Ubuntu.

---

### Post by oldefoxx on 2010-02-12
Now that is what I really call teamwork.  As they say, persistence pays off.  Thank you both for a valuable object lesson. And the information brought forth will also serve others well.

---

