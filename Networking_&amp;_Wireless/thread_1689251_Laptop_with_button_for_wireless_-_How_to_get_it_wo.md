---
title: "Laptop with button for wireless - How to get it working?"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by JC Cheloven on 2011-02-16
Hi all, 

The laptop is some 6 year-old, xp preinstalled, and has an Intel 2200BG wireless card, as reported by lspci:
```
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```
It has a special button next to the keyboard to enable wireless. It seems NOT to be a hardware button, as it launches (in windows) some program, which pops up a window showing whether you have wireless and/or bluetooth activated (there's another button for bluetooth; bluetooth works BTW). I think the launched program is something like 
Program Files\Intel\Wireless\Bin\iFrmewrk.exe
Just in case it matters. 

Just installed Maverick, and wireless doesn't work. NM shows "wireless network is deactivated". I think it's about that wireless activation button. Im unfamiliar with this. Can someone please give a clue?

JC

PD.-the button doesn't anything in Ubuntu. I can't even assign it to some customary task, as maximizing a window or so. Seems not to be treated as an ordinary key.

---

### Post by chili555 on 2011-02-17
Let's see what's going on under the hood. Please open Applications > Accessories > Terminal and run and post:```
rfkill list all
dmesg | grep -e ipw -e eth
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

What brand and model of laptop is it? Thanks.

---

### Post by JC Cheloven on 2011-02-17
Hi, thanks very much for answering.

It's a Medion MD96500.

The output of rfkill list all:
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

The output of dmesg | grep -e ipw -e eth:
```
[    1.377300] r8169 0000:06:07.0: eth0: RTL8169sb/8110sb at 0xf80d4000, 00:0a:e4:ae:da:be, XID 10000000 IRQ 18
[   25.989810] libipw: 802.11 data/management/control stack, git-1.1.13
[   25.989814] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.044852] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   26.044856] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.218580] ipw2200 0000:06:05.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   26.233484] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   27.144876] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   27.221467] r8169 0000:06:07.0: eth0: link down
[   27.221741] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.256022] eth1: no IPv6 routers present
```

---

### Post by chili555 on 2011-02-17
> 1: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="Red"]Hard blocked: yes[/COLOR]That suggests the button is indeed blocking the wireless. Please try:```
sudo rfkill unblock all
rfkill list all
```Any improvement? You might also do:```
sudo tail -f /var/log/messages
```Leave the terminal window open as you press the key a couple of times. Are there any indications that the system recognizes the key press?

What brand and model laptop is it?

---

### Post by elbanaan on 2011-02-18
If above doesn't work (the rfkill should do it though), you can try going to BIOS (F12 on startup) and disabling the hardware button (i.e. setting it so that wireless is always on)

Not a pretty solution, but it should work :)

---

### Post by JC Cheloven on 2011-02-18
Thanks again for your awesome support. This is a great community.

** the laptop is a MEDION96500 **
It has a bios from Phoenix tech. It's not mine: I "volunteer" installing Ubuntu for everyone asking for it (or I manage to get him envious, he he). I have to give back the computer soon, and I'd like this to be a success, as usual :)

I have  some news, but first the commands you suggested:

--> Unfortunately the rfkill unblock didn't make a difference:
```
riki@medion:~$ sudo rfkill unblock all
[sudo] password for riki: 
riki@medion:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

--> No new messages appear at /var/log/messages when pressing the button. The last 10 lines shown by tail remain unchanged, and are about unrelated things (bluetooth, and the mounting of sda6).

THE NEWS:
Just had a walk on the bios (thanks elbanaan), and under "advanced" found an entry for the "default wireless device". Weirdly, the options given are only:
1.-Disabled
2.-Last used state :confused:
So if I can't enable once, I can never enable (?)
Anyway, booted twice into the bios, and settled "last state" twice without intervention of any OS. Surprisingly it worked. Ubuntu connects now to the wireless network. 

BUT: in this new situation, if the button is pressed (under ubuntu), NM comes back to no connection and the "wireless deactivated" message. This produces nothing in /var/log/messages (!). And of course, pressing it again does nothing: don't enable wireless nor puts any message in /var/log. 
 
So, it's not a good solution. The risk of pressing the damn button, or a boot in win2 changing things, is too high. The owner is a joe-user, booting into bios is too much to ask for him, I'm affraid. So if you guys have further ideas, they're still welcome.

---

### Post by chili555 on 2011-02-18
Is it, under the skin, an Acer? Please check:```
lsmod | grep acer
```The module acer-wmi is notoriously a bit tricky.

---

### Post by JC Cheloven on 2011-02-18
Don't seem to be an acer-in-the-heart. lsmod doesn't report any line with the word "acer", as for the grep filter. Please see below the whole list of loaded modules, just in case you appreciate something noticeable.

I think Medion is a German brand, not subsidiary of any other. They're not bad, but IMO they tend to incorporate too much gimmick to justify the price. In this case, several additional buttons (weirdly managed by win2 software), a fingerprint reader (rare for a pc of that time), and such.

Output of lsmod: 
```
Module                  Size  Used by
michael_mic             1744  8 
arc4                    1165  4 
lib80211_crypt_tkip     7736  2 
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
snd_hda_codec_si3054     3440  1 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22203  2 
radeon                829447  3 
snd_hda_codec          87552  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
joydev                  8767  0 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
pcmcia                 35973  0 
drm_kms_helper         30200  1 radeon
ipw2200               136715  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
libipw                 39808  1 ipw2200
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
btusb                  10969  2 
cfg80211              144694  2 ipw2200,libipw
tifm_7xx1               3766  0 
yenta_socket           21518  0 
intel_agp              26566  0 
pcmcia_rsrc            10566  1 yenta_socket
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
ati_remote              8291  0 
tifm_core               6089  1 tifm_7xx1
snd                    49038  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
soundcore                880  1 snd
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
agpgart                32011  3 ttm,drm,intel_agp
lib80211                5058  3 lib80211_crypt_tkip,ipw2200,libipw
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5168  1 radeon
irda                  178970  0 
ppdev                   5556  0 
parport_pc             26058  0 
video                  18712  0 
crc_ccitt               1351  1 irda
output                  1883  1 video
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
firewire_ohci          21234  0 
sdhci_pci               6339  0 
r8169                  36521  0 
firewire_core          46643  1 firewire_ohci
sdhci                  15890  1 sdhci_pci
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 r8169
```

---

### Post by I&#9829;HTML5 on 2011-02-18
I had a problem similar to this on my Compaq laptop. Try enabling wireless in Windows, then going into Ubuntu. That worked for me.

---

### Post by JC Cheloven on 2011-02-19
Well, the computer is back to his owner. He's quite impressed overall, I think. He's even able to see/edit .dwg files (installed draftsight on wine). 

As to the subject of this thread, a procedure from withing ubuntu for activation of the wireless card would have been prefereable, but finally I gave him written instructions on how to proceed in the bios if wireless gets down by accident. Let's hope the best :rolleyes:

Thank you all for your advice. 
Chili555: I learned quite a lot from your posts. Special thanks.

Marking the thread as solved (not completely so, but I think there is a nice amount of info that may be useful for someone with a similar problem).

---

