---
title: "After install Ubuntu 11.04... No network nor wireless connection"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by young-dragon on 2011-07-28
Hi,

Here is the story of what happened...

I installed Jolicloud OS with Windows XP before because Windows XP have too many virus to attachment to Internet so whenever I go on the internet, most of the link take us to random site so I just installed Jolicloud OS however, some reason, I don't like Jolicloud very much because it require to enter the user name and password to link Jolicloud so wasted my time to use it... Its cool but pointless.

So, I just realised Ubuntu also provided free Ubuntu OS for netbook. After I downloaded Ubuntu desktop 11.04 and installed the system (all the datas is now gone and only current OS is Ubuntu)

So, once I installed it... The netbook seem running well and no problem however, there is a huge problem is wireless are not found so I can't even use the Internet!.

This netbook only got wireless and nothing else to connect like cable (wired).

Mine wireless called...
01:00.0 Network Controller [0280]: Broadcom corporation BCM4312 802.11b/g LP-PHY

I don't even know how to fix it and I can't even installed what I followed other people tried to. 

I hope someone tell me how to fix it so I can go on the internet once again :D

Thanks

---

### Post by young-dragon on 2011-07-28
No one cared bout me :'(

I spend a lots of time to figuring it out how to fix it and no luck!...
Shall I re-install it?... I downloaded alternate version so shall I try this to see if it work?

Thanks

---

### Post by young-dragon on 2011-07-28
It seem nobody really care bout it... I trying my best to fixing the wireless and yet, I went nut... I don't want waste my time to sit down and search for it to try different way without connecting to internet for package driver.

Can you please tell me how to fix it... Those word are too advance and I'm noob!... It kinda well out of order not support others member of people who want to fix it.

I am sorry if I speak like this but... I seriously want simple fix it asap!

---

### Post by young-dragon on 2011-07-28
Okay, I checked on this one... 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

And I am on the b43 - No Internet access, therefore I follow right way until step 2... The link does not work!... I was close to done without ur help :-(
Can someone please fix the link so i can download it again

---

### Post by wildmanne39 on 2011-07-28
Hi, please run these commands in a terinal
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by young-dragon on 2011-07-29
Ah, at last someone save my life!... :D
Okay, I am using different computer to use an Internet so the netbook right next to me... :-)

```
sudo lshw -C network

*-network
	description: Network controller
	product: BCM4312 802.11b/g LP-PHY
	vendor: Broadcom Corporation
	physical id: 0
	bus info: pci@0000:01:00.0
	version: 01
	width: 64 bits
	clock 33MHz
	capabilities: pm msi pciexpress bus_master cap_list
	configuration: driver-b43-pci-bridge latency=0
	resources: irq:16 memory:feafc000-feafffff
*-network
	description: Ethernet interface
	product: 88E8040 PCI-E Fast Ethernet Controller
	vendor: Marvell Technology Group Ltd.
	physical id: 0
	bus info: pci@0000:02:00.0
	logical name: eth0
	version: 00
	width: 64 bits
	clock 33MHz
	capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100-bt-fd autonegotiation
	configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
	resources: irq:42 memory:febfc000-febfffff ioport:ec00(size=256)
*-network DISABLED
	description: Wireless interface
	physical id: 1
	logical name: wlan0
	serial: 00:24:2b:7d:4d:7c
	capabilities: ethernet physical wireless
	configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

```
lspci -nn | grep 0280

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

```
iwconfig

lo		no wireless extensions.
eth0		no wireless extensions.
wlan0		IEEE 802.11bg ESSID:off/any
		Mode: Managed Access Point: Not-Associated Tx-Power=0 dBm
		Retry Long limit: 7 RTS the:off Fragment the:off
		Power Management:off
```

```
rfkill list all

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0 Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

```
lsmod

Module			Size		Used by
parport_pc		32111		0
ppdev			12849		0
binfmt_misc		13213		1
snd_hda_codec_idt	60537		1
snd_hda_intel		24140		2
arc4			12473		2
and_hda_codec		90901		2 snd_hda_codec_idt,snd_hda_intel
rfcomm			38125		8
snd_hwdep		13274		1 snd_hda_codec
snd_pcm			80244		2 snd_hda_intel,snd_hda_codec
b43			296610		0
i915			450944		3
snd_seq_midi		13132		0
sco			17779		2
bnep			17785		2
snd_rawmidi		25269		1 snd_seq_midi
l2cap			48656		16 rfcomm,bnep
mac80211		257001		1 b43
hp_wmi			13418		0
and_seq_midi_event	14475		1 snd_seq_midi
joydev			17322		0
snd_seq			51291		2 snd_seq_midi,snd_seq_midi_event
sparse_keymap		13666		1 hp_wmi
btusb			18160		2
uvcvideo		66851		0
bluetooth		65565		9 rfcomm,sco,bnep,l2cap,btusb
snd_timer		28659		2 snd_pcm.snd_seq
drm_kms_helper		40745		1 i915
videodev		75143		1 uvcvideo
drm			180037		4 i915,drm_kms_helper
psmouse			73312		0
cfg80211		156212		2 b43,mac80211
snd_seq_device		14110		3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw		12990		0
snd			55295		13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit		13184		1 i915
video			18951		1 i915
soundcore		12600		1 snd
snd_page_alloc		14073		2 snd_hda_intel,snd_pcm
lp			13349		0
parport			36746		3 parport_pc,ppdev,lp
sky2			49172		0
ssb			45942		1 b43
```

This is a long to type it up!... So here you can see the code on Ubuntu 11.04
So, I just checked Ethernet cable and it does not work as well!... Does it clash with Wireless?

Thanks

---

### Post by wildmanne39 on 2011-07-29
Hi, no it should not keep the wired connection from connecting but while the wired is connected it will over ride the wireless connection.

You are using the wrong driver, it would be a lot easier to fix if the wired connection was working.

You need to uninstall firmware-b43-installer
and install firmware-b43-lpphy-installer instead.

Hi, go to the link and follow the directions for Installing b43fwcutter with out an internet connection.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

It is possible after you remove the driver you do not need if you restart your system your wired connection might work.
Thank you

---

### Post by young-dragon on 2011-07-29
Hi, I am a noob and I don't know how to remove the drivers and what you mean restart my system?

Thanks

---

### Post by wildmanne39 on 2011-07-29
Hi, open synaptic package manager type bcm or broadcom in the search window after synaptic opens that should show you only the broadcom drivers for your card,look for firmware-b43-installer it will have a green dot next to it, click on it and remove it.

Then make sure your wired connection is plugged in and restart your computer then see if your wired connection is working if not you will need to go to the link I gave you in my last post and follow the directions for installing with out an internet connection.
Thank you

---

