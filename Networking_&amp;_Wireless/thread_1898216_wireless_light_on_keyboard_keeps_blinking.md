---
title: "wireless light on keyboard keeps blinking"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by bsantos83 on 2011-12-20
Just installed Ubuntu and the wireless LED keeps blinking when I have a connection but if I disable it turns red like it should.
Laptop- HP Pavilion DV6 1355dx
Wireless card- WIFI LINK 1000 BGN

---

### Post by chili555 on 2011-12-21
I believe your wireless card uses the driver module iwlagn. Check with:```
lsmod | grep iwl
```If it is indeed iwlagn, let's try a temporary fix:```
sudo modprobe -r iwlagn
sudo modprobe iwlagn led_mode=1
```Now does the LED behave as expected? If so, let's write a simple file to make it permanent:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn led_mode=1
```Proofread carefully, save and close gedit.

You should be all set.

---

### Post by SaintDanBert on 2011-12-21
The LED blinks to show send-receive activity in addition to wireless on-off.

What do you mean by "work as it should?" Isn't that what you want, Doc?

~~~ 0;-Dan

---

### Post by chili555 on 2011-12-21
> **SaintDanBert said:**
> The LED blinks to show send-receive activity in addition to wireless on-off.

What do you mean by "work as it should?" Isn't that what you want, Doc?

~~~ 0;-DanI do, and many of us do, but many others are offput by the incessant blinking (nagging? sorta like my ex??) and would prefer a simple ON if the wireless is connected and OFF if it's not. The developers of iwlagn and a few other wireless drivers give us the option to select.

If he were using most other drivers, I would have said, "I can do nuthin' fer ya, son."

---

### Post by bsantos83 on 2011-12-21
> **chili555 said:**
> I believe your wireless card uses the driver module iwlagn. Check with:```
lsmod | grep iwl
```If it is indeed iwlagn, let's try a temporary fix:```
sudo modprobe -r iwlagn
sudo modprobe iwlagn led_mode=1
```Now does the LED behave as expected? If so, let's write a simple file to make it permanent:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn led_mode=1
```Proofread carefully, save and close gedit.

You should be all set.

Worked like a charm. Thank you for the help.

---

### Post by SaintDanBert on 2011-12-22
> **chili555 said:**
> 
...
The developers of iwlagn and a few other wireless drivers give us the option to select.

If he were using most other drivers, I would have said, "I can do nuthin' fer ya, son."

Well! (grin, blush) I learn something new every day.

Cheers,
~~~ 0;-Dan

---

### Post by chili555 on 2011-12-22
> **SaintDanBert said:**
> Well! (grin, blush) I learn something new every day.

Cheers,
~~~ 0;-DanA great place to start with driver issues is:```
modinfo <your_driver>
```In this case:```
$ modinfo iwlagn
filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
<snip>
srcversion:     8BCB911ABE7887D81943F53
alias:          pci:v00008086d00000892sv*sd00000466bc*sc*i*
<snip>
depends:        mac80211,cfg80211
vermagic:       3.0.0-14-generic SMP mod_unload modversions 686 
[COLOR="Red"]parm:           led_mode[/COLOR]:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (bool)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Disable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
```Have fun and keep learning!

---

### Post by SaintDanBert on 2011-12-26
Where does one find details to help understand [aka, decode] the details one learns from **modinfo**?

If I need to set **led_mode** with each system startup, which script or job or whatever-they-get-called-this-week do I use to hold the proper commands that run during system start?

Cheers,
~~~ 0;-Dan

---

### Post by chili555 on 2011-12-26
> **SaintDanBert said:**
> Where does one find details to help understand [aka, decode] the details one learns from **modinfo**?

If I need to set **led_mode** with each system startup, which script or job or whatever-they-get-called-this-week do I use to hold the proper commands that run during system start?

Cheers,
~~~ 0;-DanYou write a .conf file as above so that the driver name is here:> sudo gedit /etc/modprobe.d/[COLOR="Red"]**iwlagn**[/COLOR].confAnd here:> options [COLOR="Red"]**iwlagn**[/COLOR] led_mode=1That means, roughly, 'when you load iwlagn, as you would automatically based on the pci.id, load it using an available parameter led_mode and set it to 1.'

You can also find parameters in the driver's dependencies:```
$ modinfo iwlagn
filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
<snip>
[COLOR="Red"]depends:        mac80211,cfg80211[/COLOR]
<snip>

``````
$ modinfo mac80211
filename:       /lib/modules/3.0.0-14-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     64349C3033DDDABE80DEBE4
depends:        cfg80211
vermagic:       3.0.0-14-generic SMP mod_unload modversions 686 
[COLOR="Red"]parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)[/COLOR]

``````
$ modinfo cfg80211
filename:       /lib/modules/3.0.0-14-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DBED8A055F9C0F3E8E07D54
depends:        
vermagic:       3.0.0-14-generic SMP mod_unload modversions 686 
[COLOR="Red"]parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)[/COLOR]

```Finding documentation on how all these work is difficult. It's also tough if you don't have a device using the driver in question so you can experiment. Often, I ask the poster to try it and cross my fingers!

---

### Post by josephellengar on 2011-12-27
> **chili555 said:**
> I believe your wireless card uses the driver module iwlagn. Check with:```
lsmod | grep iwl
```If it is indeed iwlagn, let's try a temporary fix:```
sudo modprobe -r iwlagn
sudo modprobe iwlagn led_mode=1
```Now does the LED behave as expected? If so, let's write a simple file to make it permanent:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn led_mode=1
```Proofread carefully, save and close gedit.

You should be all set.

Thanks man! One more "feature" of 11.10 that is no longer bugging me. :lolflag:

---

### Post by ninja001 on 2011-12-29
I am using Ubuntu 11.10 on Dell D630 laptop with Intel's 4965 network card. 
I have tried the above but it has not worked for me (I am quite novice at coding in Ubuntu). 

After coding for > sudo gedit /etc/modprobe.d/wlan.conf and saving the following in the text editor > options iwlagn led_mode=1 I get the following error message in terminal: 

> 
(gedit:2295): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.6AC66V': No such file or directory

(gedit:2295): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

I hope someone has a solution :)

---

### Post by chili555 on 2011-12-29
> sudo gedit /etc/modprobe.d/wlan.confI believe your card uses not iwlagn but iwl4965. Please verify:```
lsmod | grep iwl
```The module iwl4965 does not have an LED parameter, unfortunately.

---

### Post by ninja001 on 2011-12-29
Yes, my wireless driver is iwl4965. 

I only happen to have this issue on Ubuntu 11.10. I have Win7 (dual boot) and don't  have any issues. The led indicator is lit up when the wifi connection is on and when it is not, it's off. 

I have never seen the blinking before and it is distracting when I try to work, so I would highly appreciate any assistance :)

Thanks again

---

### Post by chili555 on 2011-12-30
Please try this:```
sudo mkdir /root/.local/share/
sudo gedit /etc/modprobe.d/iwl-legacy.conf 
```Add one line:```
options iwl-legacy led_mode=1 
```Proofread carefully. Save and close gedit. Now do:```
sudo rm /etc/modprobe.d/wlan.conf 
```Reboot and let us have your report.

---

### Post by SaintDanBert on 2011-12-30
> **chili555 said:**
> 
...
Finding documentation on how all these work is difficult. It's also tough if you don't have a device using the driver in question so you can experiment. Often, I ask the poster to try it and cross my fingers!

There was a time, in the world of *nix, when one did not release programs or libraries without man-pages. Notice that there are such pages for much of the C-language (now C++) run-time-library. Would it be that much trouble to write a man-page such that **man module-name** would report details about available parameters and their meaning and usage, caveats about use of the module, dependencies on other modules, and so on?

When I was coding for a living, we wrote these man pages first while writing the implementation requirements. They later served as input into unit test planning and sometimes code specification.

I lament, also, the proliferation of command line software that does not implement options that are defacto standard such as **--help** and **--version** and the short-form equivalents **-h** or  **-?**, and **-v**.

Cheers,
~~~ 0;-Dan

---

### Post by chili555 on 2011-12-30
> Would it be that much trouble to write a man-page such that man module-name would report details about available parameters and their meaning and usage, caveats about use of the module, dependencies on other modules, and so on?One would think not, however, there doesn't seem to be any. I had hoped there might be available published data sheets from the manufacturers explaining all this, but have not found it so far.

I have sometimes found sparse documentation in the form of comments in .c files; for example, here:```
less /usr/src/linux-source-2.6.38/drivers/net/wireless/iwlwifi/iwl-3945.c
```For me, at least, it's a combination of trial and error, educated guess-work and...luck. Sorta blows the Doctor image, doesn't it!

PS - Dependencies are well covered in *modinfo module-name*.

---

### Post by ninja001 on 2011-12-30
> **chili555 said:**
> Please try this:```
sudo mkdir /root/.local/share/
sudo gedit /etc/modprobe.d/iwl-legacy.conf 
```Add one line:```
options iwl-legacy led_mode=1 
```Proofread carefully. Save and close gedit. Now do:```
sudo rm /etc/modprobe.d/wlan.conf 
```Reboot and let us have your report.

Thanks a lot! That fixed the problem!

---

### Post by MadMarc on 2012-08-24
> **chili555 said:**
> Please try this:```
sudo mkdir /root/.local/share/
sudo gedit /etc/modprobe.d/iwl-legacy.conf 
```Add one line:```
options iwl-legacy led_mode=1 
```Proofread carefully. Save and close gedit. Now do:```
sudo rm /etc/modprobe.d/wlan.conf 
```Reboot and let us have your report.

This worked for me, THANK YOU VERY MUCH.

EDIT: sudo mkdir /root/.local/share/ already existed.

---

### Post by ThatNewGuy on 2013-05-29
I would just like to add to the solutions here:

LINK: [https://alexcabal.com/stop-blinking-intel-wifi-led-on-ubuntu-karmic/](https://alexcabal.com/stop-blinking-intel-wifi-led-on-ubuntu-karmic/)

Solution that worked for me :  echo "echo \"options iwlwifi led_mode=1\" >> /etc/modprobe.d/iwlwifi.conf" | sudo bash

I tried the above steps in this post and did not work for me but i did find the site and it worked. So i figured id share this with yall.



ThatNewGuy

---

### Post by VinDSL on 2013-12-03
For those that have found this old thread (comes up high in search results) while desperately seeking a solution...

> **ninja001 said:**
> I am using Ubuntu 11.10 on Dell D630 laptop with Intel's 4965 network card.

I have tried the above but it has not worked for me [...]

I hope someone has a solution :)

I'm currently doing +1 testing on Ubuntu 14.04 LTS.  Sorry to report this, but the blinking LED light problem still exists.

Supposedly (according to posts on Launchpad) this 'problem' is actually a kernel feature.  Whatever.

I own a Dell Latitude D620.  The LED light doesn't blink on Ubu 14.04 with a Linux 3.13-rc2 kernel.

I also own a Dell Latitude D630 ATG. The LED light DOES blink on Ubu 14.04 with a Linux 3.13-rc2 kernel.

The difference between these two laptops is:

[LIST]
[*]The Dell D620 has a Dell Wireless DW1390 mini-card (no blinking)
[*]The Dell D630 ATG has an Intel Wireless Pro 3945abg mini-card (non-stop blinking)
[/LIST]

The 'fix' for the D630 was to swap its 3945 wifi card with the 1390 wifi card from the D620.

Put another way, the 3945abg blinks, and the 1390 doesn't.

Hopefully, somebody will find this helpful.

BTW, I just bought a new 1390 on Ebay for $3.00 with free shipping.  I'll put it in my D620 and throw the 3945 on the junk pile.

Problem solved... :D

---

### Post by chili555 on 2013-12-04
>  I'll put it in my D620 and throw the 3945 on the junk pile.

Problem solved... Really?? Rather than do any sort of troubleshooting or even putting a bit of tape or paint over the LED, you just give up and get an unknown quantity from Ebay? OK, good luck then.

---

### Post by VinDSL on 2013-12-04
> **chili555 said:**
> Really?? Rather than do any sort of troubleshooting [...]
Here's the thing...

Last week -- Thanksgiving week -- I worked 32 hours on Wednesday.  Went home Thursday afternoon, passed out for 8 hours, and worked another 24 hours on Friday.

Normally I would have ignored the blinking WiFi LED, but I spent all day Saturday, and all day Sunday troubleshooting the problem, while I was recuperating.

When I went to work Monday, and reflected on the situation, it occurred to me that my almost identical D620 had no such blinking problem.

Gotta admit, I never thought about putting duct tape on my business laptop -- covering it with fingernail polish, or whatever.  LoL! :D

Good one...

---

### Post by chili555 on 2013-12-05
> I worked 32 hours on Wednesday.Wow! You *were* busy!

---

### Post by VinDSL on 2013-12-05
> **chili555 said:**
> Wow! You *were* busy!
Yeah, that's about it, for me.  Might be somebody/somewhere that can be on their feet longer, but not me.

I suffered through another 32-hour day, a few years ago -- thought I did permanent damage to my feet -- they were 'lobster red'. LoL!

On my FleaBay purchases, I've been pretty lucky, so far.  I try to stick with 'new' OEM overstock, whenever possible.

Kind of hard to pass-up genuine Dell parts, new in the bag/box, for pennies on the wholesale dollar.  Don't know how the sellers make any money on this stuff -- buy something for a dollar, and sell it for two dollars I guess (100% profit).  When you deal in tonnage, I suppose it makes a big difference.

Anyway, I did try all the usual tricks -- worked the search engines for two days, and tried everything I ran across.

Bottom line:  Nothing I ran across gave me a solid LED light.  That's what I was looking for.  Everything I tried either continued to gave me a blinking LED or no LED at all.

---

### Post by chili555 on 2013-12-05
May I assume you tried *options iwlegacy led_mode=1*?

---

### Post by VinDSL on 2013-12-06
> **chili555 said:**
> May I assume you tried *options iwlegacy led_mode=1*?
Yes.

That was my fallback workaround -- the one I kept coming back to, when other 'solutions' failed.

As mentioned above, it extinguished the LED, but that wasn't what I was looking for.  I want the LED to come on solid, when wifi is activated, and go dormant when wifi is switched off.

That's the way my Latitude D620 wifi LED always worked, on WinXP Pro, and all flavors of Linux.

Never experienced the 'problem' until I bought the Latitude ATG D630.  The culprit turned out to be the Intel 3945 WLAN mini-card. The Dell 1390 mini-card displays no such bad behavior. ;)

EDIT

BTW, in order to be crystal-clear, the Dell 1390 doesn't require ANY workarounds.  As a matter of fact, the 'iwlegacy' trick does nothing for it, because the 1390 is rather featureless, and has no 'options' to control the LED through scripting, et cetera.  It's basically dumb as a rock, but works like a champ.

---

### Post by chili555 on 2013-12-06
> BTW, in order to be crystal-clear, the Dell 1390 doesn't require ANY workarounds. As a matter of fact, the 'iwlegacy' trick does nothing for it, I'm quite certain it doesn't work because I doubt it has an *iwl*-whatever card. I assume it has a Broadcom. 

The other options for iwlegacy are 0 and 2. I'd try those as well, just for fun.

---

### Post by VinDSL on 2013-12-06
> **chili555 said:**
> I assume it has a Broadcom.[...]

Correctamundo...

```
vindsl@Gorgar ~ $ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
	Subsystem: Dell Device [1028:01f9]
	Kernel driver in use: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge

vindsl@Gorgar ~ $ modinfo b43
filename:       /lib/modules/3.13.0-031300rc2-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     61503538419D225CDF80F48
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-031300rc2-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

vindsl@Gorgar ~ $ 

```

---

### Post by bacco2 on 2014-07-17
[FONT=arial]Confirm the approach 
[/FONT][FONT=arial]"lsmod | grep iwl"
worked for me on Ubuntu 14.04 on a old Dell Latitude D430.

Note: chance is there are more than one "iwl..." and you don't know which one is the right one, like in

[/FONT][FONT=courier new]iwl3945                63619  0 [/FONT]
[FONT=courier new]iwlegacy               88016  1 iwl3945[/FONT]
[FONT=courier new]mac80211              546051  2 iwl3945,iwlegacy[/FONT]
[FONT=courier new]cfg80211              409394  3 iwl3945,iwlegacy,mac80211

[FONT=arial]I tried both and one was the right one...[/FONT][/FONT]


[FONT=arial]



[/FONT]

---

