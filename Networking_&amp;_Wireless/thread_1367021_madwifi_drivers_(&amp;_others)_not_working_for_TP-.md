---
title: "madwifi drivers (&amp; others) not working for TP-Link TL-WN350G card"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by macho on 2009-12-29
Just got a new TL-WN350G PCI wireless card.  Ubuntu autodetects the madwifi drivers when I boot up on hardy:

```
# lsmod | grep ath
ath_pci      101024  0
wlan         207856  1 ath_pci
ath_hal      192582  1 ath_pci
```

But I don't get an wireless interface:

```
# iwconfig
lo         no wireless extensions.

eth0       no wireless extensions.
```

dmesg, after loading the modules, includes the line

```
[   31.252507] wifi%d: unable to attach hardware: 'No hardware present or device not yet supported' (HAL status 1)
```

Which is probably a bad sign for me.  I heard of a different module called ath5k that might work, so I blacklisted the ath drivers above, and tried it.

I had to modprobe for it manually, and it loaded, but didn't give me a wireless interface either.  Any advice on what else I can try?  Are there newer versions of these modules that might work?

I am using the madwifi modules from linux-restricted-modules-2.6.24-26-generic version 2.6.24.18-26.3 and the ath5k module from linux-backports-modules-2.6.24-26-generic version 2.6.24-26.34

Thanks for your time.


Here are the relevant results of lspci and lshw:

```
# lspci | grep "Ethernet controller"
01:0a.0 Ethernet controller: Atheros Communications Inc. Unknown device 001d (rev 01)
```

```
# lshw -C Network
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 01
       width: 32 bits
       clock: 32 MHz
       capabilities: pm cap list
       configuration: latency=168 maxlatency=28 mingnt=10
```

---

### Post by macho on 2009-12-30
I got slightly further with this after installing the current cvs madwifi [as described in this thread]("http://ubuntuforums.org/showthread.php?t=1240781"), which still didn't work until I tried switching the PCI slot the card was in [as suggested in this thread]("http://madwifi-project.org/ticket/808").

Now I'm getting an ath0:
```
$ iwconfig ath0
ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

However, it doesn't seem to be able to detect any of the several wireless networks in the area.  Any thoughts?

```
$ iwlist ath0 scan
ath0      No scan results
```

---

### Post by pytheas22 on 2009-12-30
If you could please post the output of these commands, I'll try to help:
```

lspci -nn | grep -i atheros
dmesg | grep -e ath -e wlan
uname -rm
cat /etc/issue
modinfo ath5k
modinfo ath_pci
```

---

### Post by macho on 2009-12-31
thanks.  i like your icon.  are you interested in may 1968?

```
$ lspci -nn | grep -i atheros
01:0a.0 Ethernet controller [0200]: Atheros Communications Inc. Unknown device [168c:001d] (rev 01)
```

```
$ dmesg | grep -e [Aa]th -e wlan
[   33.580819] MadWifi: ath_attach: Switching rfkill capability off.
[   33.605224] wifi0: Atheros AR2425 chip found (MAC 15.0, PHY SChip 7.0, Radio 10.2)
[   33.633715] ath_pci: wifi0: Atheros 2417: mem=0xdfff0000, irq=20
```

```
$ uname -rm
2.6.24-26-generic i686
```

```
$ cat /etc/issue
Ubuntu 8.04.3 LTS \n \l

```

```
$ modinfo ath5k
filename:       /lib/modules/2.6.24-26-generic/updates/ath5k.ko
version:        0.5.0 (EXPERIMENTAL)
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     CA00006F676CBF707463724
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        lbm_cw-mac80211,led-class,lbm_cw-cfg80211
vermagic:       2.6.24-26-generic SMP mod_unload 586 
```

```
$ modinfo ath_pci
filename:       /lib/modules/2.6.24-26-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r4099
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     A134E374A76B7ECEBF3CF7B
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-26-generic SMP mod_unload 586 
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)
```

also, maybe i should mention, since i installed the new madwifi driver i'm getting an extra wirless module (ath_rate_sample):
```
$ lsmod | grep ath
ath_rate_sample        15232  1 
ath_pci               242872  0 
wlan                  236656  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               353440  3 ath_rate_sample,ath_pci
```

---

### Post by pytheas22 on 2009-12-31
I'm not sure why the ath_pci module won't claim your device, but I think it would be worth trying ath5k instead.  However, the version of ath5k that you have currently installed (0.5) doesn't support your wireless card (device ID 168c:001d), according to the 'modinfo' output.  The most recent version of ath5k, on the other hand, does (according to the 'modinfo' output on my Ubuntu 9.10 system).

So I think that compiling the latest version of the ath5k driver would help you.  To do that, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-old-2009-12-11.tar.bz2." Save it to your desktop.  Then run these commands to compile and install it:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless*tar.bz2
cd compat-wireless*
make
sudo make install
echo ath5k | sudo tee -a /etc/modules
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

If you get any error messages while running these commands, please post them.  Otherwise, please reboot after you finish installing the new ath5k driver, and hopefully your wireless will work.  If it still doesn't, please let me know the output of these commands:
```

lsmod | grep ath
sudo modprobe ath5k
dmesg | grep -e ath -e wlan
sudo iwlist scan
```

Don't worry about the ath_rate_sample module; it's normal.

I am interested in May 1968 in France.  I wish they had won!  Perhaps then we'd have no proprietary software...

---

### Post by macho on 2009-12-31
Thanks for the advice, but no dice, unfortunately!  I installed the newer module and rebooted, but then...

```
$ lsmod | grep ath
ath5k                 101632  0 
mac80211              230132  1 ath5k
led_class               6020  1 ath5k
cfg80211               36192  2 ath5k,mac80211
```

And the other three commands gave no output at all (well iwlist gave lo and eth0, but that doesn't seem terribly relevant).  Same result no matter which of my two PCI slots I put the card in.

Just for fun, I tried rebooting again using ath9k instead of ath5k.  Still didn't work, though something showed up in dmesg at least (though not much):

```
$ dmesg | grep -e ath -e wlan
[   41.632187] ath9k: 0.1
```

```
$ lsmod | grep ath
ath9k                 252344  0 
mac80211              230132  1 ath9k
led_class               6020  1 ath9k
```

If I am to get it working this way, does it mean I'll have to run "make install" again everytime I upgrade the kernel?

---

### Post by pytheas22 on 2009-12-31
That's strange.  If dmesg doesn't mention ath5k anywhere, it would seem like ath5k doesn't think it should claim your device.  What is the output of:
```

modinfo ath5k
```

I'm curious as to which devices your new ath5k modules thinks it should claim.

ath9k is for newer Atheros chips and probably won't work for you, but ath5k definitely is supposed to support 168c:001d devices, according to [this page]("http://linuxwireless.org/en/users/Drivers/ath5k").

One other thing that may help is to shut down your computer, then unplug it (and remove the battery if applicable), then hold the power button in for about a minute.  I've seen situations where the ath_pci driver leaves Atheros cards in a zombie state that ath5k can't wake up, and cutting off all power to the motherboard will force the device to reset and solve the problem.  I'm doubtful this is the problem in your case (if it were, I would expect dmesg to mention something about it when ath5k gets loaded), but it can't hurt to cut off power just in case.

Also, yes, you would have to compile the ath5k driver again after each kernel upgrade if you use this method.  However, you can make the process a lot faster by compiling just the ath5k driver rather than all the wireless modules; if you do it that way it only takes a few seconds rather than several minutes.

---

### Post by macho on 2009-12-31
```
$ modinfo ath5k
filename:       /lib/modules/2.6.24-26-generic/updates/drivers/net/wireless/ath5k/ath5k.ko
version:        0.5.0 (EXPERIMENTAL)
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     D843F9E93CD7C397D7FCC67
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        led-class,cfg80211,mac80211
vermagic:       2.6.24-26-generic SMP mod_unload 586
```

which part tells what devices it should handle?

i did the power button thing while the machine was unplugged, which didn't seem to affect anything.  i'm not sure if removing the battery is applicable...?  i imagine there's a CMOS battery somewhere on the mobo, if that's what you mean, but i've never messed with it.  it's an ALiveNF6G-VSTA board.

thanks again, i really appreciate all your help.

---

### Post by macho on 2009-12-31
I think I see now, it's the "Support for 5xxx..." line above.

The linuxwireless.org link you provided above seems to say that my 168c:001d chipset is named AR2417.  
[This post]("http://osdir.com/ml/linux.drivers.ath5k.devel/2008-08/msg00059.html") to an ath5k developers list last fall seems to be adding a patch to support my card, which apparently is an alternate version of the AR2425 chipset, which could be why the previous ath5k driver I had identified it as AR2425 as you can see in output I pasted above.

Any other ideas?  Is it significant that my chipset is 2417, which falls outside 5xxx?  The linuxwireless page seems to say 2417 is also handled OK.

---

### Post by pytheas22 on 2009-12-31
> which part tells what devices it should handle?

The 'alias' lines in the modinfo output tell you.  Unfortunately, it looks like even the newer ath5k module that you installed doesn't think it should support your device.  You want a line that looks like this:
```

alias:          pci:v0000**168C**d0000**001D**sv*sd*bc*sc*i*
```

That's from my Ubuntu 9.10 system.  As you can see from the parts in bold, it tells you that devices with your PCI ID are supported by the module.  Unfortunately you have no such line.

I'm not sure why the version of ath5k that you compiled using the latest source code still doesn't want to support your device.  It's possible that the compat-wireless-old code, which you used, doesn't have the patch for your device applied.  Unfortunately, as far as I know, compat-wireless-old is the only one that will compile on Ubuntu 8.04, as explained [here]("http://linuxwireless.org/en/users/Download#Compat-wireless_release_types"), because of Hardy's kernel.  You can try compiling the normal compat-wireless, but the last time I did that on Hardy, the compiler threw errors and it failed.

So at this point I think you have three options:
1. upgrade to a more recent version of Ubuntu, where your wireless will hopefully work out-of-the-box, and if not you can compile normal compat-wireless
2. go back to trying to get the ath_pci driver to work, although I think we'd be kind of shooting in the dark there because I didn't see any clues in the output you posted as to why it wasn't working before, plus ath_pci is not really supported anymore
3. try to use ndiswrapper

My first recommendation would be solution #1, but that depends on how easy it is for you to upgrade Ubuntu (or, better, reinstall the system from scratch using a newer version).  If you need to use Ubuntu 8.04 for some reason, or you have too much invested in your current system to upgrade, we can try the other approaches.
> 
Is it significant that my chipset is 2417, which falls outside 5xxx? The linuxwireless page seems to say 2417 is also handled OK.

That's normal.  ath5k supports all the 2xxx and 5xxx devices (except for a handful of 5xxx that use ath9k), while ath9k supports the 9xxx chips (there's no ath2k; not sure why they do it this way).

---

### Post by macho on 2009-12-31
Thanks yet again.  I'm happy to upgrade after bad experiences with ndiswrapper in the past and ath_pci looking bleak.  I was planning to just put it off until May, when the new LTS version was due out, but I don't mind doing it now.

IIRC I have to either reinstall karmic from scratch, or incrementally go from hardy->intrepid->jaunty->karmic.  Or I can stop earlier as soon as my card is supported.  I think I'll opt for the latter, and let you know how it goes.

---

### Post by macho on 2010-01-03
Okay, I had a few rough spots on the way to intrepid, but I think I've worked those out.

I compiled the newer compat-wireless stuff.  My kernel seems new enough to support it:
```
$ uname -r
2.6.27-16-generic
```

Then after rebooting and doing "modprobe ath5k":

```
$ lsmod | grep ath
ath5k                 136584  0 
mac80211              222512  1 ath5k
ath                    17152  1 ath5k
cfg80211              143432  3 ath5k,mac80211,ath
led_class              12164  1 ath5k
```

```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan2     Failed to read scan data : Network is down

```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan2     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```          

```
$ dmesg -e ath =e wlan
[  114.583598] ath5k 0000:01:0a.0: PCI INT A -> Link[LNKC] -> GSI 19 (level, low) -> IRQ 19
[  114.587555] ath5k 0000:01:0a.0: registered as 'phy0'
[  115.089492] ath: EEPROM regdomain: 0x809c
[  115.089505] ath: EEPROM indicates we should expect a country code
[  115.089511] ath: doing EEPROM country->regdmn map search
[  115.089515] ath: country maps to regdmn code: 0x52
[  115.089520] ath: Country alpha2 being used: CN
[  115.089524] ath: Regpair used: 0x52
[  115.246343] ath5k phy0: Atheros AR2417 chip found (MAC: 0xf0, PHY: 0x70)
[  115.378208] udev: renamed network interface wlan0 to wlan2

```

Any idea why I can't see any of the wireless networks in the area?

Also, I was swapping a different wireless card that was working out of my box so I could communicate on here and try to resolve the problem.  After installing compat-wireless, it doesn't want to load anymore.  Any ideas about that?  It uses the rtl8180 module, and was going fine when I first upgraded to intrepid.

```
dmesg | grep rtl
[   19.084698] rtl8180: disagrees about version of symbol ieee80211_free_hw
[   19.084705] rtl8180: Unknown symbol ieee80211_free_hw
[   19.084838] rtl8180: disagrees about version of symbol ieee80211_alloc_hw
[   19.084840] rtl8180: Unknown symbol ieee80211_alloc_hw
[   19.084969] rtl8180: disagrees about version of symbol ieee80211_register_hw
[   19.084972] rtl8180: Unknown symbol ieee80211_register_hw
[   19.085104] rtl8180: disagrees about version of symbol ieee80211_wake_queue
[   19.085106] rtl8180: Unknown symbol ieee80211_wake_queue
[   19.085282] rtl8180: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   19.085285] rtl8180: Unknown symbol ieee80211_tx_status_irqsafe
[   19.085670] rtl8180: disagrees about version of symbol ieee80211_stop_queue
[   19.085672] rtl8180: Unknown symbol ieee80211_stop_queue
[   19.085806] rtl8180: disagrees about version of symbol ieee80211_unregister_hw
[   19.085808] rtl8180: Unknown symbol ieee80211_unregister_hw
[   19.086037] rtl8180: disagrees about version of symbol ieee80211_rx_irqsafe
[   19.086039] rtl8180: Unknown symbol ieee80211_rx_irqsafe
[   19.086180] rtl8180: disagrees about version of symbol ieee80211_rts_duration
[   19.086183] rtl8180: Unknown symbol ieee80211_rts_duration

```

I assime some kind of module conflict is happening?

Thanks.

---

### Post by pytheas22 on 2010-01-03
Thanks for doing the upgrade; hopefully it will make things easier.

The reason iwlist didn't return any networks is probably that the interface is down.  Try bringing it up with "sudo ifconfig wlan2 up" and then scan again. Otherwise, things look much better now and hopefully ath5k will finally work for you.

As for the rtl8180 stuff, usually the symbol disagreement stuff happens if you install compat-wireless and then load the new modules without rebooting.  Please see if rebooting solves the problem.  Also remember that you can always uninstall compat-wireless by cd'ing into the directory with the Makefile and running "sudo make uninstall"  If for some reason the rtl8180 module in compat-wireless doesn't work for you but the ath5k one does, you could always keep the original rtl8180 driver and install just ath5k from compat-wireless.

Also, did you try connecting using the normal ath5k module that ships with Intrepid?  Did it recognize your card at all?  I don't know if the necessary patch had been applied by the time Interpid was released.

---

### Post by macho on 2010-01-03
excellent!  thank you so much again one final time for all of your help.  the ath5k module that ships with intrepid seems to work fine, too.

i'm definitely keeping a link to this thread; i expect it will be very helpful to me in future wireless throubleshooting.

don't forget to look under the paving stones from time to time!

---

