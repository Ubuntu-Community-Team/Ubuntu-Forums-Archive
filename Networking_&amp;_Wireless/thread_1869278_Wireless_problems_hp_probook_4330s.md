---
title: "Wireless problems hp probook 4330s"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by airplanesimen on 2011-10-25
i got some problems. My network card wont work, and i tried theese commands to get it work (i read it somwhere):

$sudo modprobe -rf rt2800pci
$sudo modprobe -rf rt2860sta
$sudo modprobe rt2860sta

It all started with my network interface saying that my wireless device wasnt ready. i typed:

Sudo ifconfig wlan0 up

i have this network card:  Realtek Ethernet (10/100/1000 NIC)
                           HP lc2010 HSPA
                           Ralink 802.11b/g/n Wi-Fi

but it didnt work. i have the hp probook 4330s, and i have 11.10 ubuntu on it, and everyone with this computer got the same problem with their networkcard. so? any suggestions what to do to recover these drivers, or fix my big problem?
When the driver is working, my networkconnection wont. i cant even see the networks in range?!

---

### Post by nothingspecial on 2011-10-25
Please do not hijack someone else's thread.

I have moved your question to it's own thread.

---

### Post by airplanesimen on 2011-10-25
> **nothingspecial said:**
> Please do not hijack someone else's thread.

I have moved your question to it's own thread.

So sorry! :( Thanks for moving it!

---

### Post by praseodym on 2011-10-25
Hi, please show:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
sudo iwlist scan
dmesg | grep rt2
```
Use driver rt2800pci in 11.10

---

### Post by airplanesimen on 2011-10-25
> **praseodym said:**
> Hi, please show:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
sudo iwlist scan
dmesg | grep rt2
```
Use driver rt2800pci in 11.10

Thanks, but i am not that good in ubuntu. that driver, how do i install it inside the terminal? normal like ```
sudo apt-get install rt2800pci
``` ?

i am going to enter ubuntu to check those values, and show them here :P wait to my next reply:P

---

### Post by praseodym on 2011-10-25
Its:

```
sudo modprobe rt2800pci
```
to load the module, the driver is already part of the kernel.

---

### Post by airplanesimen on 2011-10-25
Here is the results: 

for the first line u asked for:

```

24:00.0 Network controller [0280]: Ralink corp. Device [1814:3592] 
	Subsystem: Hewlett-Packard Company Device [103c:1638] 
	Kernel driver in use: rt2800pci 
-- 
25:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06) 
	Subsystem: Hewlett-Packard Company Device [103c:167f] 
	Kernel driver in use: r8169 

```

LSMOD:
```

Module                  Size  Used by 
parport_pc             32114  0  
ppdev                  12849  0  
snd_hda_codec_hdmi     31426  1  
snd_hda_codec_idt      60049  1  
rfcomm                 38408  0  
bnep                   17923  2  
bluetooth             148839  10 rfcomm,bnep 
binfmt_misc            17292  1  
joydev                 17393  0  
uvcvideo               67271  0  
videodev               85626  1 uvcvideo 
hp_wmi                 13652  0  
sparse_keymap          13658  1 hp_wmi 
snd_hda_intel          24262  2  
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
arc4                   12473  2  
rt2800pci              18340  0  
rt2800lib              48717  1 rt2800pci 
crc_ccitt              12595  1 rt2800lib 
rt2x00pci              14202  1 rt2800pci 
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci 
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib 
cfg80211              172392  2 rt2x00lib,mac80211 
eeprom_93cx6           12653  1 rt2800pci 
psmouse                73673  0  
serio_raw              12990  0  
snd_seq_midi           13132  0  
snd_rawmidi            25241  1 snd_seq_midi 
jmb38x_ms              17406  0  
snd_seq_midi_event     14475  1 snd_seq_midi 
memstick               15857  1 jmb38x_ms 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
hp_accel               21632  0  
lis3lv02d              19280  1 hp_accel 
input_polldev          13648  1 lis3lv02d 
i915                  505108  3  
wmi                    18744  1 hp_wmi 
snd_timer              28932  2 snd_pcm,snd_seq 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
drm_kms_helper         32889  1 i915 
drm                   192226  4 i915,drm_kms_helper 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
i2c_algo_bit           13199  1 i915 
video                  18908  1 i915 
soundcore              12600  1 snd 
mei                    36466  0  
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm 
lp                     17455  0  
parport                40930  3 parport_pc,ppdev,lp 
ahci                   21634  2  
libahci                25727  1 ahci 
r8169                  43104  0  
xhci_hcd               72915  0  
sdhci_pci              13658  0  
sdhci                  27360  1 sdhci_pci 

```

RFKILL list:
```

0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: hp-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
2: hp-bluetooth: Bluetooth 
	Soft blocked: no
	Hard blocked: no 


```
The Last one was like this:
```

lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     No scan results 

```

one more thing: My driver is there now, but i cant find ANY network, it doesnt work like it should -_-
when i click on the network icon, it shows under wireless: "device not ready".
So i used
```

sudo iwconfig wlan0 up 
```
and now it is only "disconnected"

---

### Post by praseodym on 2011-10-25
Check your router settings, namely "MAC-address filtering" if your card is allowed. Router firmware is up-to-date?

Check now:

```
iwconfig
sudo iwlist scan
iwlist chan
dmesg | grep rt2
```
Which encryption do you use? Best ist WPA2-AES, not mixed WPA/WPA2.

---

### Post by airplanesimen on 2011-10-25
> **praseodym said:**
> Check your router settings, namely "MAC-address filtering" if your card is allowed. Router firmware is up-to-date?

Check now:

```
iwconfig
sudo iwlist scan
iwlist chan
dmesg | grep rt2
```
Which encryption do you use? Best ist WPA2-AES, not mixed WPA/WPA2.
this is a home network with wep encryption. It works well in windows 7, but i cant find any network in linux. yes, my router firmware is up to date :P and no filters are active on my router ^^ i do wonder what to do to fix this issue? i need to find the router first, before i check my router settings?

---

### Post by praseodym on 2011-10-25
Please show the outputs.

---

### Post by airplanesimen on 2011-10-25
Iwconfig:
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```
Sudo iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```
iwlist chan:
```
lo        no frequency information.

eth0      no frequency information.

wlan0     27 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 151 : 5.755 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 159 : 5.795 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

```
dmesg | grep rt2
```
[   11.377430] rt2800pci 0000:24:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.377443] rt2800pci 0000:24:00.0: setting latency timer to 64
[   11.400282] Registered led device: rt2800pci-phy0::radio
[   11.400339] Registered led device: rt2800pci-phy0::assoc
[   11.400394] Registered led device: rt2800pci-phy0::quality

```

---

### Post by praseodym on 2011-10-25
Deactivate the power management:

```
sudo iwconfig wlan0 power off
sudo service network-manager restart
```

---

### Post by airplanesimen on 2011-10-25
> **praseodym said:**
> Deactivate the power management:

```
sudo iwconfig wlan0 power off
sudo service network-manager restart
```

i did, but it still cant find any networks? wierd!

---

### Post by airplanesimen on 2011-10-25
[http://ubuntuforums.org/showthread.php?p=11212087#post11212087](http://ubuntuforums.org/showthread.php?p=11212087#post11212087)
-- if u show me how to download and install a new driver (if u can), i maybe think this is solved, just look at the last post in the link. :P

---

### Post by praseodym on 2011-10-25
Via cable:

```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
tar xzvf angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make
sudo make install
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

Check:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
dmesg | egrep 'rt2|rt3'
```

From here: [http://forum.ubuntuusers.de/topic/sorry-bin-zu-bloed-treiber-zu-wlan-compilieren/#post-2814031](http://forum.ubuntuusers.de/topic/sorry-bin-zu-bloed-treiber-zu-wlan-compilieren/#post-2814031)

---

### Post by airplanesimen on 2011-10-25
have to wait som days, to see if it works. i dont have the possibility to plug in a cable yet, But thank you so much anyway :P

---

### Post by airplanesimen on 2011-10-26
> **praseodym said:**
> Via cable:

```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
tar xzvf angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make
sudo make install
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

Check:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
dmesg | egrep 'rt2|rt3'
```

From here: [http://forum.ubuntuusers.de/topic/sorry-bin-zu-bloed-treiber-zu-wlan-compilieren/#post-2814031](http://forum.ubuntuusers.de/topic/sorry-bin-zu-bloed-treiber-zu-wlan-compilieren/#post-2814031)
sudo apt-get install linux-headers-$(uname -r) build-essential - is that the command, or shuld (uname -r) be with my username -r?

---

### Post by airplanesimen on 2011-10-26
THANK YOU SO MUCH :P It did work, thanks thanks thanks! Evryone who read this topic, and got the same problem as me, just update your driver! Thanks to praseodym for the amazing help!

---

### Post by praseodym on 2011-10-26
$(uname -r) is the place holder for the current kernel. Please show the output of

```
uname -r
```

---

### Post by airplanesimen on 2011-11-24
okay, have the same problem again after installing updates -_- So, i have to install this driver every time im updating the system? (Kernel files). Thanks for you help ^^

---

### Post by praseodym on 2011-11-24
Yes,

after a kernel upgrade:
```
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make clean
sudo make
sudo make uninstall
sudo make install
```
Please show:

```
uname -a
```
and install the corresponding metapackage (e.g. linux-headers-generic, linux-headers-generic-pae, whatever kernel you are using). This updates the header automatically

---

### Post by airplanesimen on 2011-11-24
> **praseodym said:**
> Yes,

after a kernel upgrade:
```
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make clean
sudo make
sudo make uninstall
sudo make install
```
Please show:

```
uname -a
```
and install the corresponding metapackage (e.g. linux-headers-generic, linux-headers-generic-pae, whatever kernel you are using). This updates the header automatically

Thanks! u want me to show the output of "uname -a" ?

---

### Post by praseodym on 2011-11-24
yes

---

### Post by airplanesimen on 2011-11-25
```
 Linux SIMLA190995 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux 
```

That was my output from 
```
 sudo -a 
```

:P

---

### Post by praseodym on 2011-11-25
Install the metapackage:

```
sudo apt-get install linux-geaders-generic
```
This updates the headers automatically, and the reinstallation is reduced to:

```
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make clean
sudo make
sudo make uninstall
sudo make install
```

---

### Post by airplanesimen on 2011-11-25
> **praseodym said:**
> Install the metapackage:

```
sudo apt-get install linux-geaders-generic
```
This updates the headers automatically, and the reinstallation is reduced to:

```
cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make clean
sudo make
sudo make uninstall
sudo make install
```
Okay, thanks a lot! :P

---

### Post by TorkelG on 2012-08-20
Could someone make a simple resumé of what is needed to do to get the wifi working?
I have tried the same commands but in afraid i may have missed some, school started today and i will need my laptop soon.

---

### Post by airplanesimen on 2012-08-23
> **TorkelG said:**
> Could someone make a simple resumé of what is needed to do to get the wifi working?
I have tried the same commands but in afraid i may have missed some, school started today and i will need my laptop soon.

Yep, i can help you do that! I will make a resumê of it all, just give me a hour.

---

### Post by airplanesimen on 2012-08-23
Okay, here is my Resumè of this topic. 

If you cant get your Wireless card working on the HP Probook 4330s Computer, this is the steps you must follow:

1. Do this Code via a network cable on your Ubuntu, it downloads the driver for your Network card:

```

wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz
tar xzvf angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz

```

2. Navigate to it, and install it: (the file need to be extracted to a folder, because you cant install from a tar.gz archive)

```

cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo make
sudo make install

```

3. Now remove the old Drivers:
```

echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

RESTART :D
==========================================================================================

After an Update of your system, this driver will be deleted, so you MUST keep this file you downloaded for later use.

Lets imagine you just updated the system, and the network stopped working again:

4. Navigate to your File in the terminal, using 
```
 cd [location of the folder with driver]
```

5. Clean up the old install of the driver, and install it again:
```
sudo make clean
sudo make
sudo make uninstall
sudo make install
```

6. Restart Computer!

---

