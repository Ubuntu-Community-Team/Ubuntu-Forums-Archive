---
title: "Connecting to wifi"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by kiwibrit on 2011-09-26
I have a ASUS EeePC 1000H.  It used to run on Widows Xp, but I formatted the HDD and installed Ubuntu 11.04 desktop version.  The installation appeared to be successful, however I cannot connect to wifi.  As a first step, I thought I should check whether Ubuntu had recognized the wireless card. Looking [here]("https://help.ubuntu.com/community/WifiDocs/WirelessNetworking") it appears that should be possible - but I cannot find a menu for 'System'.  I'd be grateful for advice.

---

### Post by nothingspecial on 2011-09-26
The system settings menu is now located from the far right icon, on the top bar.

Get a wired connection and choose "Additional Drivers" from that menu.

If that doesn't work, open a terminal (Ctrl-Alt-T)

and paste the output of

```
sudo lshw -C network
``` 

in a new post back here.

(you will have to type your password after that command. You won't see anything to indicate that you are typing it, don't worry, just type it then press enter.)

---

### Post by kiwibrit on 2011-09-26
Thank you for your prompt response.  The icon next to the on-off icon gives me: Chat Accounts, Broadcast Accounts, and About Me.

Ethernet connection is working fine.

Ctrl+Alt+T gives: 
```

  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:27:6e:e8
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fbfc0000-fbffffff ioport:ec00(size=128)

```

---

### Post by nothingspecial on 2011-09-26
Hang on, I'm using 11.10 beta.

Try pressing the windows key 

Then type drivers

You should get the additional drivers app

---

### Post by kiwibrit on 2011-09-26
'Addtional Drivers' tells me that "There are no proprietary drivers available for this system".

From another forum, I think I may have the Atheros AR5007EG Wireless Network Adapter (a mate of mine has a similar EeePC - so I'll double check).  If so, does **[this advice]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html")** look good to you (it was written for Ubuntu 8.10)?

---

### Post by nothingspecial on 2011-09-26
No.

Never follow out of date instructions unless you know for sure they will work.

I can't confirm or deny that they will. Wait for some more help.

I'll move this thread to the networking section. There are some knowledgeable people there.

---

### Post by nothingspecial on 2011-09-26
Did you update after installing btw?

---

### Post by kiwibrit on 2011-09-26
No.  I had password problems at the time, and now can't find how to do it.

---

### Post by nothingspecial on 2011-09-26
Get a wired connection.

Open the terminal again.

Type

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by kiwibrit on 2011-09-26
Done (thanks for hanging in on this, BTW).  Major download and follow-on activity.  Addtional Drivers still shows no proprietary drivers on system. Wireless card is AzureWare AW-NE 766, which I see from [this forum thread]("http://ubuntuforums.org/showthread.php?t=920332") is based on the Ralink RT2700E chipset.  However I am not clear form the other forum thread where to go from here.

But looking at this [fixunix thread]("http://fixunix.com/kernel/553136-ralink-rt2700e-driver.html") I saw there was a Linux driver, but the link in that thread no longer works - and going to Ralink's site it looks like the [RT2700E is not supported in Linux]("http://www.ralinktech.com/support.php?s=2").  

I am beginning to wonder if I should buy another wireless card that is supported out of the tin.  Is there a PCIE mini WLAN card you would recommend for which the driver is already in Ubuntu?

---

### Post by nothingspecial on 2011-09-26
Well if you've got the spare cash and don't mind parting with it.......

.....best bet is to take your eeepc to the shop and test the wireless there before you buy.

You may get more help here yet. I'd give it at least 24 hours.

---

### Post by collisionystm on 2011-09-26
intel wireless card's are usually a good bet.

---

### Post by kiwibrit on 2011-09-26
**nothingspecial, **apart form the wifi problem, Ubuntu in the EeePC is like having a new, fast, notebook. A new card would cost me about GBP 15 - I reckion if that's the only cost I've had a good deal.   I'll take your advice about hanging on for a bit, though.

**collisionystm**, I was wondering about the Intel 4965AGN.  According to Intel [there is a Linux driver for it]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Wireless+Networking&ProductLine=Intel%C2%AE+WiFi+Products&ProductProduct=Intel%C2%AE+Wireless+WiFi+Link+4965AGN") though I see there is a * after Linux.  Not sure if that is significant.

---

### Post by wildmanne39 on 2011-09-26
Hi, pleas post the results of these commands:
```
lspci -nn | grep -e 0280 -e 0200
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
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by kiwibrit on 2011-09-26
**wildmanne39,**:

```


lspci -nn | grep -e 0280 -e 0200
03:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)

``````

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

``````

rfkill list all
0: eeepc-wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: eeepc-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````

lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
rfcomm                 38125  8 
i915                  451033  3 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
sco                    17827  2 
bnep                   17785  2 
snd_rawmidi            25269  1 snd_seq_midi
l2cap                  48656  16 rfcomm,bnep
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
btusb                  18160  2 
drm                   184164  4 i915,drm_kms_helper
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
psmouse                73312  0 
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeepc_laptop           19417  0 
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
video                  18951  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
sparse_keymap          13666  1 eeepc_laptop
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
atl1e                  32576  0 

```

---

### Post by wildmanne39 on 2011-09-26
Hi, for some reason that command did not show the exact card and chip it is using, please try these three commands, maybe they will show it.
```
lspci -nnk | grep -iA2 net
```
```
lsusb
```
```
sudo pccardctl ident
```
Thank you

---

### Post by kiwibrit on 2011-09-26
Thanks for your interest.

```

lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
    Kernel driver in use: ATL1E

``````
lsusb
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0505 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
sudo pccardctl ident

---I was asked for password.  Gave it.  No result -----

```

---

### Post by wildmanne39 on 2011-09-26
Hi, your card still did not show up.

You might want to check in your bios and see if there is a setting in there to turn it on, and see if a fn key will turn it on so we can see it, that will not get it working we will still need to install a driver but it must be detectable first.
Thank you

---

### Post by kiwibrit on 2011-09-26
Good call!  Onboard WLAN was disabled :oops:  It has now been enabled.

```

lspci -nn | grep -e 0280 -e 0200
01:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]
03:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)

``````

lsusb
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0505 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````

sudo pccardctl ident  ---as before, I was asked for password.  Gave it.  No result -----
```Actually, although I am new to this, I think this set is good news - in that we now have

```
Network controller [0280]: Ralink corp. RT2860 [1814:0781]
```Which I think has a Linux driver.  I'm going to have to turn in now, or divorce will threaten - but I will be keen to see, in the morning, if you have been able to give me further advice.

---

### Post by wildmanne39 on 2011-09-26
Hi, give me a few minutes to look up this wireless card to make sure we use the correct driver and how to install it.
Thank you

---

### Post by praseodym on 2011-09-26
Hi,

this device can be used with the rt2860sta or rt2800pci module. The latter is newer and currently further developed. Both drivers are part of the kernel.

Check:

```
grep rt28 /etc/modprobe.d/*
```
Load the driver by hand:

```
sudo modprobe -v rt2800pci
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by wildmanne39 on 2011-09-26
Hi praseodym, that is what I thought but I always like to be sure,especially since this is the first time I have seen that card.
Thank you

---

### Post by wildmanne39 on 2011-09-26
Hi, run the last three command given by praseodym, after you unplug your wired connection.

If it does not come on post the results if the first command he gave.
Thank you

---

### Post by kiwibrit on 2011-09-27
praseodym and wildmanne39, thank  you, that did it.  Than you very much =D>

---

### Post by nothingspecial on 2011-09-27
And you saved £15 :p

---

### Post by kiwibrit on 2011-09-27
nothingspecial, more than that, I would still have had to figure out the BIOS problem.  I have learnt quite a lot in a short time.  I've been really impressed by the concise, accurate and friendly advice here.

---

### Post by wildmanne39 on 2011-09-27
Hi, your welcome! I am glad it is working.

---

