---
title: "Elusive Driver for Intel 6205 Wireless"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by DSim on 2012-07-20
I just installed 12.04 on a Dell Latitude 6520 with the Intel 6205 wireless chip. The install process asked for "iwlwifi-6000g2a-6.ucode", however the only related file on intelwirelesslinux.org is "iwlwifi-6000g2a-ucode-17.168.5.3.tgz", which contains the previous version - "iwlwifi-6000g2a-5.ucode". I'm on kernel vmlinuz-3.2.0-26-generic, btw.

I've done quite a bit of searching and haven't found the file, but I have found modinfo dumps of people's systems in forum messages that show it.

Could someone please let me know where to find it? It's the only thing left to get the system running flawlessly.

---

### Post by chili555 on 2012-07-20
The required firmware is installed by default. If your wireless isn't working, something else is wrong. Please post:```
rfkill list all
dmesg | grep iwl
ls /lib/firmware/ | grep iwlwifi
```What are your symptoms?

---

### Post by DSim on 2012-07-20
> **chili555 said:**
> The required firmware is installed by default. If your wireless isn't working, something else is wrong. Please post:```
rfkill list all
dmesg | grep iwl
ls /lib/firmware/ | grep iwlwifi
```What are your symptoms?
I failed the morale check and left the system at work for the weekend. The (proprietary) file I'm looking for was prompted for (on removable media) early on in the install process. I've done enough research to know it just needs to be copied into /lib/firmware (IIRC) once I find it.

Wireless is definitely not working right now. I'll be happy to run the commands you listed when I'm in front of the machine on Monday, but I'm pretty confident things would work if I can find the "-6" ucode version.

Thanks for the response, good to see another Ubuntu supporter here in SC! :)

---

### Post by chili555 on 2012-07-21
I will be interested in your results. This may or may not prove to be relevant: [http://www.spinics.net/lists/linux-wireless/msg88962.html](http://www.spinics.net/lists/linux-wireless/msg88962.html)> > > We don't really know, but it was really just due to a bug in the driver,
> > it should use MODULE_FIRMWARE with the latest released rather than the
> > latest testing version -- there's a patch in our queue to fix that.We may find this driver parameter useful:```
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
```All this speculation of course, depends on your findings.

---

### Post by DSim on 2012-07-21
> **chili555 said:**
> I will be interested in your results. This may or may not prove to be relevant: [http://www.spinics.net/lists/linux-wireless/msg88962.html](http://www.spinics.net/lists/linux-wireless/msg88962.html)
Yes, I think it is - I'm a bit curious as to why that version hasn't been pushed to the intelwirelesslinux.org repository, it's been over three months since that post.

> We may find this driver parameter useful:```
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
```All this speculation of course, depends on your findings.
If I don't have the "-6" version by Monday morning, I'll try that - I was unaware of that parameter, I've never set up wireless on Linux before. Thanks!

---

### Post by chili555 on 2012-07-21
> I'm a bit curious as to why that version hasn't been pushed to the intelwirelesslinux.org repository, it's been over three months since that post.I wonder if it's in the compat-wireless suite. *linux-backports-modules-cw* or some such in Synaptic.> I was unaware of that parameter, I've never set up wireless on Linux before. I'm not exactly sure how to use it; something like:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi ucode_alternative=iwlwifi-6000g2a-5.ucode
```I'd try that and check:```
dmesg | grep iwl
```Complaints? Errors? Success?

Then we could write a conf file to make it permanent.

---

### Post by sunbird on 2012-07-21
I just did a fresh install of 12.04 on a Thinkpad x220 and got the same dialog box during the install. I just continued without the driver. My wireless works, but not reliably on the 5ghz band. It connects fine to the 2.4ghz band.

I'm wondering if I should give this a try:

> **chili555 said:**
> I wonder if it's in the compat-wireless suite. *linux-backports-modules-cw* or some such in Synaptic.I'm not exactly sure how to use it; something like:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi ucode_alternative=iwlwifi-6000g2a-5.ucode
```I'd try that and check:```
dmesg | grep iwl
```Complaints? Errors? Success?

---

### Post by chili555 on 2012-07-21
> My wireless works, but not reliably on the 5ghz band. It connects fine to the 2.4ghz band.A long-standing bug for this driver. Please try instead:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Yeah, I know, no N speeds. If it helps, we'll write a conf file.

---

### Post by sunbird on 2012-07-22
> **chili555 said:**
> A long-standing bug for this driver. Please try instead:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Yeah, I know, no N speeds. If it helps, we'll write a conf file.

Hmmm... the thing is, I think I get N speeds currently on the 2.4 ghz band, so I'd rather not disable it. Is there any hope for a fix at some point? Is there a bug report that I can watch/contribute to?

Thanks!

---

### Post by chili555 on 2012-07-22
I'd look here: [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2368](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2368)

Or here, generally: [http://bugzilla.intellinuxwireless.org/](http://bugzilla.intellinuxwireless.org/)

Intel is the developer of the driver:> $ modinfo iwlwifi
filename:       /lib/modules/3.2.0-26-generic-pae/updates/cw-3.3/iwlwifi.ko
alias:          iwlagn
license:        GPL
[COLOR="Red"]author:         Copyright(c) 2003-2011 Intel Corporation [/COLOR]<ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux

---

### Post by DSim on 2012-07-23
> **chili555 said:**
> The required firmware is installed by default. If your wireless isn't working, something else is wrong. Please post:```
rfkill list all
dmesg | grep iwl
ls /lib/firmware/ | grep iwlwifi
```What are your symptoms?

Good morning. Looks like I'll be trying the "-5" version.

Results of these commands:

$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

$ dmesg | grep iwl
[   27.857794] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.857852] iwlwifi 0000:03:00.0: setting latency timer to 64
[   27.857941] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   27.857944] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90005790000
[   27.857946] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[   27.858352] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[   27.858487] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   27.858581] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   27.869465] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   27.869468] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   27.869470] iwlwifi 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   27.869492] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   27.871551] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   27.929954] iwlwifi 0000:03:00.0: loaded firmware version 17.168.5.3 build 42301
[   27.932077] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  257.096162] iwlwifi 0000:03:00.0: PCI INT A disabled

" sudo lshw -C network" shows it as "Unclaimed" meaning no driver loaded.

---

### Post by chili555 on 2012-07-23
> iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.> $ rfkill list all
0: dell-wifi: Wireless LAN
Soft blocked: yes
[COLOR="Red"]Hard blocked: yes[/COLOR]Please move the wireless switch or key combination so as to enable wireless.

---

### Post by DSim on 2012-07-23
> **chili555 said:**
> Please move the wireless switch or key combination so as to enable wireless.
Hah! So this thing has a switch, eh? I bet you've typed that same advice quite a few times.

That did it, I guess it uses the "-5" version if it works...?

Just so this wasn't a complete waste of your time, I did find this:

> [PATCH 02/16] iwlwifi: remove uCode alternatives mechanism

From: Johannes Berg <[johannes.berg@...]("http://gmane.org/get-address.php?address=johannes.berg%2dral2JQCrhuEAvxtiuMwx3w%40public.gmane.org")>

We've never released firmware using the alternatives mechanism and our build process makes that difficult anyway. [...] From: [http://permalink.gmane.org/gmane.linux.kernel.wireless.general/89133](http://permalink.gmane.org/gmane.linux.kernel.wireless.general/89133)

I don't think the "ucode_alternative" parameter was quite what you thought it was regardless.

Thanks again for your help, I'll mark this solved and just figure on getting the "-6" version in a future update.

---

### Post by chili555 on 2012-07-23
> I don't think the "ucode_alternative" parameter was quite what you thought it was regardless.What I thought we might need to do is force the module to use the -5 ucode, which we have, and not insist it wanted to use the -6 ucode which doesn't, as far as I can see, exist at all.

No?

---

### Post by DSim on 2012-07-25
> **chili555 said:**
> What I thought we might need to do is force the module to use the -5 ucode, which we have, and not insist it wanted to use the -6 ucode which doesn't, as far as I can see, exist at all.

No?
Right, but the quote I included seemed to imply that only designated firmware, which never existed, could be loaded by that mechanism. Also, your first suggested example included the full ucode filename, while the parameter takes an int.

At any rate, since it's going away there's not much point worrying about it. I expect the "-6" ucode will be slipstreamed into a future version/update.

It's still not clear to me why Ubuntu was prompting for the "-6" version at all. It also occurs to me that if the rfkill command can detect a "hard-block", the network gui should advise the user accordingly. Perhaps I'll take a look and see how hard such an enhancement might be.

Thanks again for your help!

---

