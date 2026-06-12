---
title: "Intel Centrino 6230 problems"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by blooz4u on 2013-03-11
Good morning!

I'm having trouble getting linux to recognize my Intel Centrino wireless card.

I'm only able to connect to the internet when hard-wired.

I've installed the proper firmware, and copied the file to the /lib/firmware directory.  I've googled and followed the wiki step by step and still have had no results.

I've been working on this problem for almost 48 hours straight.. and I'm at a loss for what to do next.

I'm ready to run commands and post output as needed.

---

### Post by chili555 on 2013-03-11
Is your driver iwlagn or iwlwifi?```
lsmod | grep iwl
```Are there any clues here?```
dmesg | grep iwl
```Just because I'm a nervous nellie, let's actually confirm your device:```
lspci -nn | grep 0280
rfkill list all
```Thanks!

---

### Post by blooz4u on 2013-03-11
"Is your driver iwlagn or iwlwifi?"

[SIZE=4][FONT=comic sans ms][B]lsmod | grep iwl 
[/B][/FONT][/SIZE]
iwl3945
iwlcore





"Are there any clues here?"

[SIZE=4][FONT=comic sans ms][B]dmesg | grep iwl -
[/B][/FONT][/SIZE]
iwl3945 Intel Pro Wireless 3945ABG/BG Connection Driver for Linux, 1.2.26ks

"Just because I'm a nervous nellie, let's actually confirm your device"

[SIZE=4][FONT=comic sans ms]**02:00.0 Network controller [0280]: Intel Corporation Device [8086:0091] (rev 34)**[/FONT][/SIZE]


**[SIZE=4][FONT=comic sans ms]0: hci0: Bluetooth[/FONT][/SIZE]**
**[SIZE=4][FONT=comic sans ms]    Soft blocked: no[/FONT][/SIZE]**
**[SIZE=4][FONT=comic sans ms]    Hard blocked: no[/FONT][/SIZE]**

Please bear with me as I'm fairly new to Linux, and this is my first box setup.

It would appear that neither iwlagn or iwlwifi drivers are loaded, even though I loaded them last night.

What next ?

---

### Post by blooz4u on 2013-03-11
*UPDATED* with more information.

---

### Post by chili555 on 2013-03-11
The correct driver for your device is not iwl3945; it is iwlagn or iwlwifi depending on your kernel version. Find out which you have with:```
modinfo iwlagn
```If you get this, you know you have iwlwifi:> chili@Think60:~$ modinfo iwlagn
ERROR: modinfo: could not find module iwlagnWhichever you have, check for your device, like this:```
modinfo iwlwifi | grep -e filename -e 0091
```I suspect you have an old kernel and a new device so that the device isn't covered since it didn't exist when the driver was written. I'm betting you have iwlagn.

Please, no more bold and huge font. I'm not *that* old!

---

### Post by blooz4u on 2013-03-11
modinfo iwlagn

```
 filename:       /lib/modules/2.6.32-5-amd64/kernel/drivers/net/wireless/iwlwifi/iwlagn.koalias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
srcversion:     DDFC7C79B1D70AF76CFF36D
alias:          pci:v00008086d00000084sv*sd*bc*sc*i*
alias:          pci:v00008086d00000083sv*sd*bc*sc*i*
alias:          pci:v00008086d00000089sv*sd*bc*sc*i*
alias:          pci:v00008086d00000088sv*sd*bc*sc*i*
alias:          pci:v00008086d00000087sv*sd*bc*sc*i*
alias:          pci:v00008086d00000086sv*sd*bc*sc*i*
alias:          pci:v00008086d00004239sv*sd*bc*sc*i*
alias:          pci:v00008086d00004238sv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000008Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000008Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,mac80211,cfg80211
vermagic:       2.6.32-5-amd64 SMP mod_unload modversions 
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int) 
```

sudo modinfo iwlwifi | grep -e filename -e 0091

```
ERROR: modinfo: could not find module iwlwifi
```

And my apologies for the large, bold font.  Won't happen again ! :o

---

### Post by chili555 on 2013-03-11
In your modinfo iwlagn, we don't see pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]0091[/COLOR]sv*sd*bc*sc*i*. As I suspected, you have an older kernel, 2.6.32-xx and a newer device. You could do several things:

#Upgrade to a newer version (read: newer kernel); or

# Look for and install a backports package. In Ubuntu, it's linux-backports-modules-cw; or

# Compile compat-wireless from scratch. Hint: the cw just above refers to compat-wireless; or

# Buy a $10-15 USB wireless device.

It appears you have capable hardware, so my recommendation is upgrade. You could run a live CD, for example from Ubuntu 12.04 LTS and see if your wireless works. I'm pretty sure it does.

Sadly, I know of no way to issue a couple of terminal commands and make it work. I will be happy to assist you in any of these strategies.

---

### Post by blooz4u on 2013-03-11
Unfortunately, that's the feeling that I've been getting (Kernel issue)

When I get home from work, I'll attempt to install 2.6.38, as I've read it corrects the issue for some folks.

Any pitfalls or warnings I need to know about doing a kernel upgrade ??

---

### Post by chili555 on 2013-03-11
> When I get home from work, I'll attempt to install 2.6.38, as I've read it corrects the issue for some folks.Can you confirm the 2.6.38 kernel includes your device ID? I have been Googling and suspect it does, but I haven't found a source saying absolutely or the changelog.

I am unaware of any particular issues with a kernel upgrade except that it's a fairly major change; more than a new version of gedit, for example. I'd back up and check the backup before I proceeded.

---

### Post by blooz4u on 2013-03-11
I can't confirm *for sure* that the device ID is included, just that it has worked for some other folks with my same issue. 

I'll make sure and backup before going forward.  I'll have an update for you this evening.

Thank you so much!  I've been banging my head for the last 48 hours, messing around with this issue !!

Stay tuned.

---

### Post by blooz4u on 2013-03-11
I did find this line in the networking section documentation for the new kernel:

[COLOR=#000000][FONT=Arial]"iwlagn: update PCI ID for 6000g2a series devices [/FONT][/COLOR][(commit)]("http://git.kernel.org/linus/fb30eaf38703d7562606e49a5872745d66366a50")[COLOR=#000000][FONT=Arial], update PCI ID for 6000g2b series devices"[/FONT][/COLOR]

---

### Post by blooz4u on 2013-03-11
Success !!

Upgraded the kernel to 3.2, and magically, everything works!! 

Thank you so much for all of your help.

This problem is SOLVED !!

---

