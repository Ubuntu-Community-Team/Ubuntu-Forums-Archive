---
title: "Atheros AR5007 802.11b/g WiFi adapter manual driver assignment"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by Netbattler11 on 2011-09-26
I am trying to get a compaq cq-60 with an Atheros AR5007 802.11b/g WiFi adapter running natty 64 bit working.

It recognizes the adapter, but says it is disabled by wireless switch. The switch is a push-button next to the power. When I boot to windows (its dual-booting) the internet doesn't work until I push it down for a few seconds to turn the adaptor on. The normal ubuntu driver doesn't realize it needs to do this. 

I tried to use ndiswrapper to get it recognized, but it didn't work. I then disabled ndiswrapper. Currently ```
sudo lshw -C networking
``` returns *-network UNCLAIMED blablabla.

I unblacklisted the default drivers. How can I assign one of those back to the hardware? I'm not sure that all of them got tested with it.

An ubuntu driver that is known to work with this chipset would also be helpful.

---

### Post by chili555 on 2011-09-26
It's not the wireless driver, probably ath5k, that recognizes the wireless key press. It is probably *hp-wmi*, HP laptop WMI hotkeys driver. Let's unravel the mess. Let's see:```
cat /etc/modprobe.d/blacklist.conf | grep ath
cat /etc/modprobe.d/ndiswrapper
rfkill list all
lsmod | grep wmi
``` Thanks.

---

### Post by Netbattler11 on 2011-09-26
Well, that got something. Not sure what though.

```
cat /etc/modprobe.d/blacklist.conf | grep ath
```returns nothing.

```
cat /etc/modprobe.d/ndiswrapper

cat: /etc/modprobe.d/ndiswrapper: No such file or directory
``````
rfkill list all

0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

``````
lsmod | grep wmi

snd_rawmidi            30486  1 snd_seq_midi
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```

I thought i was getting pretty good at this kind of thing, but i feel like a complete noob again. Anyone mind deciphering this for me?

---

### Post by chili555 on 2011-09-27
We are looking for the blacklist that took place when you tried ndiswrapper; so far we haven't found it. A blacklist prevents the native driver, ath5k in your case, from loading. We'll have to find it and undo it.

The HP laptop WMI hotkeys driver, *hp-wmi*, is loaded:> hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmiAnd, based on experience, we believe it's the reason your system thinks the wireless is turned off by the switch:> 0: ***hp-wifi***: Wireless LAN
    Soft blocked: yes
    Hard blocked: yesLet's continue looking for the effects of ndiswrapper and undo it. Please show us:```
ls /etc/modprobe.d
ndiswrapper -l
```Let's see if we can remove the *hp-wmi* module and get things going temporarily:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
sudo modprobe ath5k
```Any improvement?

Even if this works, we'll need to tweak some things to make it permanent.

---

### Post by Netbattler11 on 2011-09-27
For the record, I unblacklisted all the things that I blacklisted when I set up ndiswrapper before my first post. They are no longer listed in /etc/modprobe.d/blacklist.conf. Does that change anything?

Also, I'm working from a clean install on this. If needed, I can reinstall the OS.

---

### Post by chili555 on 2011-09-27
What are the results of my suggested commands?```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
sudo modprobe ath5k
```

---

### Post by Netbattler11 on 2011-09-27
Oh right. Those. *facepalm*

None of those generated any terminal output. However, it does seem to recognize the card again. The wireless button is blue instead of orange, and the wireless networks are disconnected instead of saying 'hardware switch disabled'. This seems only temporary though. It goes back if I restart networking or the computer.

---

### Post by chili555 on 2011-09-27
> **Netbattler11 said:**
> Oh right. Those. *facepalm*

None of those generated any terminal output. However, it does seem to recognize the card again. The wireless button is blue instead of orange, and the wireless networks are disconnected instead of saying 'hardware switch disabled'. This seems only temporary though. It goes back if I restart networking or the computer.Well, as I said:> Even if this works, we'll need to tweak some things to make it permanent. Can you actually connect to the networks?

Once we know what works, even temporarily, we can figure out what we need to do to make it both work and persist.

---

### Post by Netbattler11 on 2011-09-27
No. I can't see any wireless networks. Its a step in the right direction though.

---

### Post by chili555 on 2011-09-28
Please run and post:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
iwconfig
sudo iwlist wlan0 scan
```Some of the commands may produce no output or an error or warning. The exact result is informative, so please post it. Thanks.

---

### Post by Netbattler11 on 2011-09-28
First three commands gave no output.

Fourth gave this:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

Fifth gave this:
```
wlan0     Interface doesn't support scanning.
```

---

### Post by chili555 on 2011-09-28
Weird! Let's have a look at:```
dmesg | grep ath
lsmod | grep -e ath -e ndis
```We'll get to the bottom of this.

---

### Post by Netbattler11 on 2011-09-28
returned
```
[    0.541142] device-mapper: multip**ath**: version 1.2.0 loaded
[0.541145] device-mapper: multip**ath** round robin: version 1.0.0 loaded
```

and nothing.

---

### Post by chili555 on 2011-09-29
We wonder why ath5k is not loading on boot! Let's dig deeper. Please post:```
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf | tail -n10
lspci -nn | grep 0280
sudo modprobe ath5k
dmesg | grep ath
```

---

### Post by Netbattler11 on 2011-09-29
First returned:
```
alsa-base.conf              blacklist-oss.conf
blacklist-ath_pci.conf      blacklist-rare-network.conf
blacklist.conf              blacklist-watchdog.conf
blacklist-firewire.conf     ndiswrapper.conf
blacklist-framebuffer.conf  nvidia-graphics-drivers.conf
blacklist-modem.conf
```

Second returned:
```
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist ndiswrapper

```

Third and fourth returned nothing.

Fifth returned:
```
[    0.551181] device-mapper: multipath: version 1.2.0 loaded
[    0.551184] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 1157.483398] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[ 1157.483412] ath5k 0000:07:00.0: setting latency timer to 64
[ 1157.483474] ath5k 0000:07:00.0: registered as 'phy0'
[ 1157.984833] ath: EEPROM regdomain: 0x64
[ 1157.984837] ath: EEPROM indicates we should expect a direct regpair map
[ 1157.984842] ath: Country alpha2 being used: 00
[ 1157.984844] ath: Regpair used: 0x64
[ 1157.997941] Registered led device: ath5k-phy0::rx
[ 1157.997966] Registered led device: ath5k-phy0::tx
[ 1157.997976] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
```

Thanks.

---

### Post by chili555 on 2011-09-29
I imagine that something in ndiswrapper.conf is a blacklist. We no longer need it, so please do:```
sudo rm /etc/modprobe.d/ndiswrapper.conf
```After you loaded ath5k, did your wireless come to life? dmesg looks pretty encouraging!

---

### Post by Netbattler11 on 2011-09-29
No, it didn't. Still says 'disabled by hardware switch'. 

No output from the command.

---

