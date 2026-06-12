---
title: "Newbie - Wireless Internet Connection (PC)"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by errbee on 2011-06-14
Hey guys,
 
I'm new to the Ubuntu community, so I'm kind of a newbie although I've been very involved with computers in the past. I recently installed the most updated version of Ubuntu on my PC last night, and I'm absolutely baffled on how to connect to the wireless internet router I have at home. I have no idea where to start. Please help!
 
Errbee (Lucas)

---

### Post by tuxonapogostick on 2011-06-14
The followings can get you started with the wireless thing.
If you are on Ubuntu Classic Session, 
   you will see "System" at the top of the screen. Do: system->preferences->network connections-> wireless
If you are on default session: 
   Press the dash key (with microsoft logo may be?), and type network. Click on "Network Connections"  then go to wireless.

---

### Post by errbee on 2011-06-14
I am on the Ubuntu Classic Section, but when I click on wireless, no network connections show up. I'm 105% certain that there are wireless routers in my area, including mine. Is this a problem with my installation? What can I do?

---

### Post by tuxonapogostick on 2011-06-14
What is your ubuntu version?
Can you give the output of "lspci -v" and "lsmod" commands?
Just checking: do you know how to open the "terminal" or command line interface application?

---

### Post by garvinrick4 on 2011-06-14
What operating system were you using with the router before now? If that worked
Ubuntu will work with same. The only thing that could be a problem is if you have
a card you have to install a driver for because it is not in the Linux kernel. So if you
were using router with another OS and are having trouble with Ubuntu connecting.
Open a terminal  (ctrl/alt/t) and copy and paste this and hit enter and copy and paste
results here:
```
sudo lshw -C network
```

---

### Post by kroq-gar78 on 2011-06-14
can't you just click the bar-ish icon at the top left (network indicator) and go from there? I though network connections only shows ones that you have set up, but I may be wrong. Is your wifi router a hidden network/non-broadcasting?

---

### Post by froar on 2011-06-15
Hi,
     Do you have a fixed connection ?
 If you do use it to download your updates and then you should see a little hardware icon on the right side of the top panel, this will be for additional third party software and drivers. click on it and make sure your wireless drivers are installed.
This is what it did with my install, the fact that you can't see and wireless networks usually means your hardware is driverless.
Hope this helps mate :)

---

### Post by errbee on 2011-06-15
Wow, thanks for the replies guys!
 
**@tux**
Yeag, I know how to open terminal. 
lsmod results: Will post soon!
 
**@garvin**
[EMAIL="lucas@lucas-KT600-8237:~$"]lucas@lucas-KT600-8237:~$[/EMAIL] sudo lshw -C network
[sudo] password for lucas: 
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: [EMAIL="pci@0000:00:12.0"]pci@0000:00:12.0[/EMAIL]
       logical name: eth0
       version: 78
       serial: 00:11:5b:23:e7:6f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:e400(size=256) memory:e2001000-e20010f
**@kroq**
No, my wifi is not hidden. I can click on that icon you're talking about, but it shows no wireless networks. So confused..

---

### Post by jsgosselin on 2011-06-15
I  may have the same issue. Sometimes, when I first boot in Ubuntu, Network Manager shows no wireless network at all, in spite of having the latest up to date proprietary driver for my wireless card installed.

As a workaround, I Suspend/Resume and everything works fine after that. Do not know exactly why, it seems to be a bug with a random behavior that appeared after I upgraded to 11.04 from 10.10.

---

### Post by errbee on 2011-06-15
**@tux**
This is lsmod, the other one you gave me doesn't work for some reason?
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
isofs                  39571  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
binfmt_misc            13213  1 
snd_via82xx            24685  2 
gameport               15027  1 snd_via82xx
snd_ac97_codec        105614  1 snd_via82xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_via82xx,snd_ac97_codec
radeon                896428  3 
snd_page_alloc         14073  2 snd_via82xx,snd_pcm
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
ttm                    65184  1 radeon
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   180037  5 radeon,ttm,drm_kms_helper
parport_pc             32111  1 
lp                     13349  0 
i2c_algo_bit           13184  1 radeon
parport                36746  3 ppdev,lp,parport_pc
snd                    55295  12 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro             12969  0 
shpchp                 32345  0 
soundcore              12600  1 snd
usbhid                 41704  0 
hid                    77084  1 usbhid
floppy                 60032  0 
sata_via               13464  2 
via_rhine              27131  0 
pata_via               13368  0
 
**@froar**
What do you mean by fixed? Is that the ethernet cable thing that connects the computer directly from the router? That sounds like it might just work actually. How do I download my updates? I'm sorry for these questions, I'm sure the answer is obvious, I'm just getting used to Ubuntu.
 
Thanks for the help guys!

---

### Post by froar on 2011-06-15
Yes, that's the cable. If you click on Applications then scroll down to Ubuntu Software center and click on that. On the left hand panel it should say updates I think. Just click on it and away you go. This is unless the update console opens up automatically.
cheers

---

### Post by tuxonapogostick on 2011-06-15
> **errbee said:**
> **@tux**
This is lsmod, the other one you gave me doesn't work for some reason?

It is not working? That's weird. What if you only do:
```
lspci
```

---

### Post by jsgosselin on 2011-06-15
To install a proprietary driver that is sometimes necessary for a wireless card to work properly (this is mi case), you can do it from the "additional drivers" panel.

---

### Post by errbee on 2011-06-15
LSPCI:
 
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

---

### Post by errbee on 2011-06-15
@froar
 
I established a wired connection, and the Internet is indeed working. However, when I go to the Ubuntu Software Center, I see no tab/icon labeled updates. I'm so close, yet so far..

---

### Post by jsgosselin on 2011-06-15
In order to do the update, you can do it from the Update Manager.

---

### Post by tuxonapogostick on 2011-06-15
do the following in the terminal for the update-manager:
```
update-manager
```

---

### Post by errbee on 2011-06-15
Thanks guys! It's fixed! I think it was a combination of all your suggestions. Your willingness to help is really something. Go Ubuntu!

---

### Post by froar on 2011-06-15
Sweet As :)

---

### Post by jsgosselin on 2011-06-15
This is great news. Wireless and video cards are sometimes not well supported in linux (yet) and it is (for me at least) really frustrating sometimes. I'm glad to see you were able to get it working.

Since your issue is solved, I think you can mark it as so from the drop down Threads Tool menu.

Welcome to Ubuntu btw. JS

---

