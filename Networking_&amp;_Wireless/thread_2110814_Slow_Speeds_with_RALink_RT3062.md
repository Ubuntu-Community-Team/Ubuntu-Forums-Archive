---
title: "Slow Speeds with RALink RT3062"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by AP0ll0UK on 2013-01-31
Morning All

I'm struggling with slow speeds on my network card. It reports that it's connecting @ 43MB/s to my Asus RT-N66U, everything else in the house works fine.

I'm currently looking through this thread - [http://ubuntuforums.org/showthread.php?t=1794360](http://ubuntuforums.org/showthread.php?t=1794360) but this refers to an RT2860 whereas mine is an RT3062. I'm a little reluctant to start tinkering as it took me quite a while with some manual editing of files to get it working.

lspci -nn | grep -i net

Network controller [0280]: Ralink corp. RT3062 Wireless 802.11n 2T/2R [1814:3062]

lsmod | grep rt2

rt2800pci              18340  0
rt2800lib              53298  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48875  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436493  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
eeprom_93cx6           12687  1 rt2800pci

Can anyone point me in the right direction of whether I need to be using an alternate driver or setting something up in the blacklist please? I'm currently running Ubuntu 12.04.

---

### Post by AP0ll0UK on 2013-02-15
I managed to this card working faster by following this info:- 

> 
Once you have downloaded the source package from the Ralink website, follow these steps:

Open a terminal with Ctrl+Alt+T, and paste the following, line by line:

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
cd Downloads
tar -xzf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
WPA1=HAS_WPA_SUPPLICANT
WPA2=HAS_NATIVE_WPA_SUPPLICANT
sed -i -e "s/$WPA1=n/$WPA1=y/g" -e "s/$WPA2=n/$WPA2=y/g" os/linux/config.mk
sudo make && sudo make install && sudo make clean
cd ..
  

Blacklist the built-in driver, and load the new one with:

echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt3562sta



However, in Connection Information, it says my wireless card is now using the rt2860 driver as opposed to rt2800 - which would it show rt2860 and not rt3562 or rt3062 which is what the PCI card is?

Also, the speed changes quite a lot. Initially it says the speed is 280MB/s, but when the machine starts to download data, or I stream audio from this machine to my laptop, the speed plummits to 54MB/s and the audio playback is choppy.

As mentioned in my initial post, I have an Asus RT-N66U which is more than capable of pumping out decent wireless speeds for all my devices.

---

### Post by AP0ll0UK on 2013-02-16
Bump.

Can anyone please advise, I'm a bit confused. I dont know if that's the correct driver for my card or if there is anything I can do to fix the wireless speed?

---

