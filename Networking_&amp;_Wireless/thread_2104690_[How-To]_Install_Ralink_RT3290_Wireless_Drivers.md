---
title: "[How-To] Install Ralink RT3290 Wireless Drivers"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by spc_hicks09 on 2013-01-13
After much trial and error, here is the final How-To.

First let me explain, this is a mash-up of various posts all mixed into one. I've done this plenty of times myself and can say that it will always work.

**_I've always had the issue of installing Ubuntu 12.04 and not having wireless when I boot up. This solves that issue but ONLY for the Ralink RT3290 Chip and ONLY on Ubuntu 12.04. This will NOT work on 12.10 unless you downgrade the kernel._**

**_Prereq's_**

Internet Connection. (If you have an Android phone, download a USB Tether app for internet, otherwise you need to use Ethernet)
Ubuntu 12.04 installed 

First thing you're going to want to do is update and get the Linux Headers, for this you will open Terminal and type the following:

```
sudo apt-get update && sudo apt-get install build-essential linux-headers-generic
```

After that is complete, cd to your home directory if you're not already there:

```
cd ~
```

Now you're going to want to download the Ralink RT3290STA Driver

```
wget http://dl.dropbox.com/u/11876059/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz
```

Now extract the tar:

```
tar -xvf DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz
```

Open "DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/config.mk"

Find the following lines and make sure they look like this:

```
HAS_WPA_SUPPLICANT=y

HAS_NATIVE_WPA_SUPPLICANT=y
```

Now back in Terminal, cd into the extracted driver folder:

```
cd ~/DPO_RT3290_LinuxSTA_V2600_20120508
```

Now the following commands in order:

```
sudo su

make

make install
```

After that finishes, activate the wireless driver:

```
sudo modprobe rt3290sta
```

Your wifi should pop right up, but it will not survive a reboot yet.....

Now let's make sure it will activate on boot, for this we will be editing the "modules" file:

```
sudo gedit /etc/modules
```

Copy/paste these lines at the very bottom:

```
rt3290
rt3290sta
```

Save the file and exit

Now you need to blacklist the default driver so that it doesn't override the rt3290sta driver:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

Scroll down the bottom of that file and add these lines at the bottom:

```
#Wireless drivers conflicting with rt3562sta
blacklist rt2800pci
blacklist rt2x00pci
```

Save and exit

Now update your changes:

```
sudo update-initramfs -u
```

Now exit the terminal and reboot

Upon reboot you should have working wifi that will survive every reboot. Hope this helps everyone, it took me about 2 days to figure all this out.

---

### Post by spc_hicks09 on 2013-04-02
Alternatively, this can be done on 12.10 now if you update your kernel to any 3.7 kernel first. Then follow all instructions. Wifi drivers will survive a reboot every single time :)

---

### Post by paulajeromeg on 2013-04-17
You have no idea how frustrating this has been for me. I just bought my computer last week and removed win 8 for Ubuntu but couldn't get the wireless working. Every site I've visited, all of the info I got and tried and tried with no results. But spc_hicks09 you are great. I followed your advice exactly and it worked like a charm. THANK YOU SOOOOOO MUCH !!!! I am a happy camper...........................

---

### Post by zeflasher on 2013-04-30
I have registered just to THANK YOU!!!

I have been looking for a solution for days then gave up (got many kernel panic).
Anyways your instructions worked and I am so happy to tell you that after a reboot I am now wrtting you using my wireless!!!

AWESOME!!!

Just for google.
HP Envy DV7-7304tx

---

### Post by spc_hicks09 on 2013-05-13
Glad I could help you both! It took me a very long time to figure out how to get this all to work. I ended up having to mash together about 3 or 4 different methods to find one that worked perfectly. Enjoy Ubuntu :)

> **paulajeromeg said:**
> You have no idea how frustrating this has been for me. I just bought my computer last week and removed win 8 for Ubuntu but couldn't get the wireless working. Every site I've visited, all of the info I got and tried and tried with no results. But spc_hicks09 you are great. I followed your advice exactly and it worked like a charm. THANK YOU SOOOOOO MUCH !!!! I am a happy camper...........................

> **zeflasher said:**
> I have registered just to THANK YOU!!!

I have been looking for a solution for days then gave up (got many kernel panic).
Anyways your instructions worked and I am so happy to tell you that after a reboot I am now wrtting you using my wireless!!!

AWESOME!!!

Just for google.
HP Envy DV7-7304tx

---

### Post by praseodym on 2013-05-13
Hi,

I am interested if it was necessary to copy the firmware:

```
sudo cp DPO_RT3290_LinuxSTA_V2600_20120508/common/rt3290.bin /lib/firmware
```
I prepared an installation archive here:

[http://forum.ubuntuusers.de/post/5561332/](http://forum.ubuntuusers.de/post/5561332/)

---

### Post by ryanlitton on 2013-05-20
I tried this method on my HP envy dv6-7245us running Ubuntu 12.04 with the 3.5.0-30-generic kernel. Ubuntu is able to connect to my wifi network with no problem, but when I open firefox and try to load web pages, the system freezes. The keyboard and mouse become unresponsive, and the screen freezes completely. The only thing I can do is force shut down by holding the power button. I'm assuming it is a kernel panic, because the caps lock light blinks sometimes when it freezes. I followed these instructions carefully, yet I still get a kernel panic. I'm running a generic kernel now, but the kernel that was installed with Ubuntu was the amd64 kernel since I have an AMD cpu. Might that have something to do with the panic/unresponsiveness?

---

### Post by EnYao on 2013-05-22
I just registered to the forum to say THANK YOU VERY MUCH.

I'd been searching around for the past 2 days, after seeing so many methods that caused side issue. This is an excellent guide and good job.

Though I would like to add that, for the very first step (*sudo apt-get update && .....*), there's error during installation and required root user. So I decided to switch to root user (*sudo su*) and do *apt-get update && ....* all over again and it worked thereafter.

I'm wondering why Ubuntu (or Canonical) [certified]("http://www.ubuntu.com/certification/hardware/201206-11167/") the HP Pavilion Sleekbook 14, and yet Ubuntu 12.04.2 LTS doesn't worked out of the box.

---

### Post by ryanlitton on 2013-05-23
I have tried this on three different kernels in 12.04 (3.5.0-30, 3.5.0-31, and 3.8.0-x). Each time I install the module following all of these steps. Each time I get a kernel panic and unresponsive system. 

I'm using the rt3290sta driver (proprietary) from the mediatek site. Perhaps there is an open -source solution or some thing out there that will work better for my HP envy dv6-7245us (besides Ethernet)? I don't want to keep my laptop tethered to my phone indefinitely, and besides, easytether is not perfect.

---

### Post by prajil on 2013-05-25
> **spc_hicks09 said:**
> After much trial and error, here is the final How-To.First let me explain, this is a mash-up of various posts all mixed into one. I've done this plenty of times myself and can say that it will always work.**_I've always had the issue of installing Ubuntu 12.04 and not having wireless when I boot up. This solves that issue but ONLY for the Ralink RT3290 Chip and ONLY on Ubuntu 12.04. This will NOT work on 12.10 unless you downgrade the kernel._****_Prereq's_**Internet Connection. (If you have an Android phone, download a USB Tether app for internet, otherwise you need to use Ethernet)Ubuntu 12.04 installed First thing you're going to want to do is update and get the Linux Headers, for this you will open Terminal and type the following:```
sudo apt-get update && sudo apt-get install build-essential linux-headers-generic
```After that is complete, cd to your home directory if you're not already there:```
cd ~
```Now you're going to want to download the Ralink RT3290STA Driver```
wget http://dl.dropbox.com/u/11876059/DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz
```Now extract the tar:```
tar -xvf DPO_RT3290_LinuxSTA_V2600_20120508.tar.gz
```Open "DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/config.mk"Find the following lines and make sure they look like this:```
HAS_WPA_SUPPLICANT=yHAS_NATIVE_WPA_SUPPLICANT=y
```Now back in Terminal, cd into the extracted driver folder:```
cd ~/DPO_RT3290_LinuxSTA_V2600_20120508
```Now the following commands in order:```
sudo sumakemake install
```After that finishes, activate the wireless driver:```
sudo modprobe rt3290sta
```Your wifi should pop right up, but it will not survive a reboot yet.....Now let's make sure it will activate on boot, for this we will be editing the "modules" file:```
sudo gedit /etc/modules
```Copy/paste these lines at the very bottom:```
rt3290rt3290sta
```Save the file and exitNow you need to blacklist the default driver so that it doesn't override the rt3290sta driver:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Scroll down the bottom of that file and add these lines at the bottom:```
#Wireless drivers conflicting with rt3562stablacklist rt2800pciblacklist rt2x00pci
```Save and exitNow update your changes:```
sudo update-initramfs -u
```Now exit the terminal and rebootUpon reboot you should have working wifi that will survive every reboot. Hope this helps everyone, it took me about 2 days to figure all this out.hi i am using Backtrack5 .Me also facing the same problom in wifi.I think because of driver. So i tried this quota. I am new in linux so done these codes by step by step but after write "sudo gedit /etc/modules" this command terminal reply like this "sudo: gedit: command not found". Can you please help me to install wifi driver for Backtrack 5.I am using hp probook 4540s mdel laptop ."ralink RT 3290 802.11bgn"- this is my wifi drver.

---

### Post by praseodym on 2013-05-25
Hi friends,

please check this installation package with dkms:

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)

---

### Post by matej12 on 2013-07-10
Hi.

I bought HP probook 4540s, installed ubuntu 12.04 and experienced the problem with wireless. I did everything described in How-To at the begining of this thread. That seemed to solve the problem, the wireless was working for an hour or so max. then ubuntu crashes and I was stucked with this screen:

[http://shrani.si/?2t/MB/4o4QfPQd/dsc0863.jpg](http://shrani.si/?2t/MB/4o4QfPQd/dsc0863.jpg)

If I use the cable everything works fine but if I switch to wireless sooner or later system crashes. Help please.

Matej

---

### Post by praseodym on 2013-07-10
Please reboot, connect via cable and check the VGA card:
```

lspci -nnk | grep -iA2 VGA
lsmod
cat /etc/X11/xorg.conf
```

---

### Post by matej12 on 2013-07-10
I did as you said and thats what I get:

```

tina@tina-HP-ProBook-4540s:~$ lspci -nnk | grep -iA2 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:17f4]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Thames [Radeon 7500M/7600M Series] [1002:6841]
    Subsystem: Hewlett-Packard Company Device [103c:17f4]
    Kernel driver in use: radeon
tina@tina-HP-ProBook-4540s:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_idt      70774  1 
parport_pc             32867  0 
ppdev                  17114  0 
joydev                 17694  0 
rfcomm                 47562  0 
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
rt3290sta            1178464  1 
coretemp               13642  0 
snd_hda_intel          34117  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
kvm                   422160  0 
snd_hwdep              17765  1 snd_hda_codec
ghash_clmulni_intel    13221  0 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
hp_wmi                 18093  0 
sparse_keymap          13891  1 hp_wmi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19257  1 hp_wmi
hp_accel               25977  0 
jmb38x_ms              17647  0 
lis3lv02d              19878  1 hp_accel
input_polldev          13897  1 lis3lv02d
radeon                912794  1 
psmouse               102075  0 
i915                  530857  3 
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
memstick               16606  1 jmb38x_ms
mac_hid                13254  0 
serio_raw              13216  0 
microcode              23030  0 
lpc_ich                17145  0 
ttm                    88495  1 radeon
drm_kms_helper         49259  2 i915,radeon
drm                   290344  7 i915,radeon,ttm,drm_kms_helper
i2c_algo_bit           13565  2 i915,radeon
video                  19598  1 i915
soundcore              15092  1 snd
mei                    41410  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
sdhci_pci              18749  0 
r8169                  62766  0 
sdhci                  33145  1 sdhci_pci
tina@tina-HP-ProBook-4540s:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
tina@tina-HP-ProBook-4540s:~$ 



```

---

### Post by praseodym on 2013-07-10
Please check this one for hybrid VGA cards with ATI cards:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by thezman007 on 2013-08-10
So I get to this line...

> Open "DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/config.mk"
Find the following lines and make sure they look like this:
Code:

HAS_WPA_SUPPLICANT=y

HAS_NATIVE_WPA_SUPPLICANT=y



No "HAS_NATIVE_WPA_SUPPLICANT=y" exists in my file :shock:(the other one does, I used the search function)... I have not proceeded any further as I don't want to mess anyhing up. Any suggestions?

---

### Post by praseodym on 2013-08-11
The dkms installation already contains these changes. Did you try it?

---

### Post by thezman007 on 2013-08-11
> **praseodym said:**
> The dkms installation already contains these changes. Did you try it?

I just did with no luck... It was a little difficult as I am not German and the filenames do not match exactly (I had issues using 'tar' for a minute there). When I reboot the menu bar tells me ra0 wireless says 'device not ready'...now what? :)

---

### Post by praseodym on 2013-08-11
Check now:
```

iwconfig
lsmod
rfkill list
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by thezman007 on 2013-08-11
These are my results:

```
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ iwconfig
ra0       Ralink STA  
          
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"DHS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:3B:23:B9   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/100  Signal level=54/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:19  Invalid misc:518   Missed beacon:0

ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ lsmod
Module                  Size  Used by
arc4                   12530  2 
zd1211rw               63736  0 
mac80211              555272  1 zd1211rw
cfg80211              208382  2 zd1211rw,mac80211
snd_hda_codec_realtek    79855  1 
snd_hda_codec_hdmi     32476  1 
parport_pc             32867  0 
ppdev                  17114  0 
rfcomm                 47562  0 
bnep                   18240  2 
bluetooth             211860  10 rfcomm,bnep
nls_iso8859_1          12714  1 
kvm                   422160  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51134  0 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
hp_wmi                 18093  0 
sparse_keymap          13891  1 hp_wmi
microcode              23030  0 
psmouse               102506  0 
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
serio_raw              13216  0 
k10temp                13174  0 
rtsx_pci_ms            13181  0 
memstick               16606  1 rtsx_pci_ms
i2c_piix4              13302  0 
snd_hda_intel          34063  7 
snd_hda_codec         135141  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17694  0 
snd                    83674  23 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                917945  2 
ttm                    88495  1 radeon
drm_kms_helper         49259  1 radeon
soundcore              15092  1 snd
drm                   290595  4 radeon,ttm,drm_kms_helper
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13565  1 radeon
wmi                    19257  1 hp_wmi
rt3290sta            1178464  0 
video                  19653  0 
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
rtsx_pci_sdmmc         17801  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
rtsx_pci               33680  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  62741  0 
ahci                   25869  3 
libahci                27338  1 ahci
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ sudo iwlist scan
[sudo] password for ausername: 
ra0       Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:3B:23:B9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/100  Signal level=39/100  
                    Encryption key:on
                    ESSID:"DHS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a2372bba3f
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0003444853
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1C:DF:CC:F0:0C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=16/100  Signal level=16/100  
                    Encryption key:on
                    ESSID:"Bryan's"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000046957d1183
                    Extra: Last beacon: 1204ms ago
                    IE: Unknown: 0007427279616E2773
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD970050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD001CDFCCF00C1021000642656C6B696E1023000F463544373233302D342D763830303010240007575053303030311042000E32303831373732333030343637361054000800060050F204000110110020463544373233302D340000000000000000000000000000000000000000000000100800020084
                    IE: Unknown: DD090010180204F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 10:0D:7F:43:7A:29
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/100  Signal level=9/100  
                    Encryption key:on
                    ESSID:"WRINKLES"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001c9808b6180
                    Extra: Last beacon: 508ms ago
                    IE: Unknown: 00085752494E4B4C4553
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1D0050F204104A0001101044000102103C0001011049000600372A000120
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:15:6D:68:26:33
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=13/100  Signal level=13/100  
                    Encryption key:off
                    ESSID:"Fairgrounds"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005cfbef5254a
                    Extra: Last beacon: 344ms ago
                    IE: Unknown: 000B4661697267726F756E6473
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD2A000C42000000011E0000000000660A040000303031353644363832363333000000000000000005028F09
          Cell 05 - Address: 00:18:F8:CE:2D:32
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/100  Signal level=15/100  
                    Encryption key:on
                    ESSID:"FBI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e0f4a7c95
                    Extra: Last beacon: 160ms ago
                    IE: Unknown: 0003464249
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000

ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ cat /etc.resolv.conf
cat: /etc.resolv.conf: No such file or directory
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ 

```

Does this help? :P

edit:Thanks for the help by the way

---

### Post by praseodym on 2013-08-11
The driver is loaded. Do you use an USB-stick with Zydas chipset (module zd1211rw)?
```

sudo modprobe -rfv zd1211rw
sudo modprobe -rfv rt3290sta
sudo modprobe -v rt3290sta
```
Check:
```

iwconfig
dmesg | grep rt3
sudo iwlist scan
```

---

### Post by thezman007 on 2013-08-11
Yeah, I am using that to get on the web, but I removed it when I rebooted...let me try those codes

---

### Post by thezman007 on 2013-08-11
Here is what I get:

```
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ sudo modprobe -rfv zd1211rw
[sudo] password for ausername: 
rmmod /lib/modules/3.5.0-37-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
rmmod /lib/modules/3.5.0-37-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-37-generic/kernel/net/wireless/cfg80211.ko
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ sudo modprobe -rfv rt3290sta
rmmod /lib/modules/3.5.0-37-generic/updates/dkms/rt3290sta.ko
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ sudo modprobe -v rt3290sta
insmod /lib/modules/3.5.0-37-generic/updates/dkms/rt3290sta.ko 
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ iwconfig
ra0       Ralink STA  
          
eth0      no wireless extensions.

lo        no wireless extensions.

ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ dmesg | grep rt3
[   12.441855] rt3290sta: module license 'unspecified' taints kernel.
ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ sudo iwlist scan
ra0       Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

ausername@ausername-HP-Pavilion-17-Notebook-PC:~$ 

```

Also, I will need to find out how to make my USB Wifi work again LOL, now I have to use wires to get online :)

---

### Post by praseodym on 2013-08-11
**ra0       Interface doesn't support scanning : Network is down**

Any button, switch, key or key combination? Check your BIOS settings (on/off/last state), and if it helps to boot the networking first, then the OS

---

### Post by thezman007 on 2013-08-11
There is a button, but pushing it doesn't do anything. It's the F12 button. I have tried it with the 'fn' button as well. BIOS is very limited since it was expected to use the UEFI boot up I believe. I will try and enable the UEFI and get back to you :)

---

### Post by thezman007 on 2013-08-11
Ok pressing and <i>holding</i> the wireless button turns off the wireless network and the menu bar says 'wireless is disabled by hardware switch'...then of course I can turn it back on and I get the same 'device not ready.' BIOS doesn't give me any network options that I can see...Not sure what to do now :)

---

### Post by praseodym on 2013-08-11
Try to press the button during boot-up either permanently or repeatedly.

---

### Post by thezman007 on 2013-08-11
Either way it just tries to Network Boot, something about PXE 2.1 or whatever. I'm gonna be away from my comp for a while. Perhaps I need to start from a clean slate? Can I add the line needed to config.mk? Are there different drivers to use?

---

### Post by michael2009 on 2013-09-10
[**[COLOR=#000000]spc_hicks09[/COLOR]**]("http://ubuntuforums.org/member.php?u=1413160") thank you very much. Where would all us sleekbook ubuntu users be without you? Back using windows no doubt. You are flipping marvellous.

---

### Post by udaraau on 2013-09-20
Excellent guide ! Worked like a charm. The only slight difference was that in the config.mk i found HAS_NATIVE_WPA_SUPPLICANT_SUPPORT instead of HAS_NATIVE_WPA_SUPPLICANT. Thanks a lot for this :)

---

### Post by bEPmdPk on 2013-10-12
Thank you.  Your post was invaluable.

---

### Post by shubhampokhriyal on 2013-11-01
i tried these commands on backtrack 5 r3
i am facing few problems
*sudo su does nothing and _wifi is not turning on even after sudo modprobe _*[COLOR=#000000][FONT=Ubuntu Mono]rt3290sta(nothing shows up after this command)
[/FONT][/COLOR]*_and last _*[COLOR=#000000][FONT=Ubuntu Mono]sudo update-initramfs -u (this command says "cannot update because running on read-only")[/FONT][/COLOR]

---

### Post by praseodym on 2013-11-01
Which kernel is that?
```

uname -a
```

---

### Post by shubhampokhriyal on 2013-11-02
Linux bt 3.2.6 #1 SMP Fri Feb 17 10:34:20 EST 2012 x86_64 GNU/Linux

---

### Post by tejvirsaggu03 on 2014-01-21
Thanks a lot for your help.. This has been really helpful.. :)

---

### Post by fipem on 2014-01-21
I was doing fine till make install, got this error

root@rulo-note:/home/rulo/DPO_RT3290_LinuxSTA_V2600_20120508# make install
make -C /home/rulo/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/rulo/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/rulo/DPO_RT3290_LinuxSTA_V2600_20120508/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3290sta.ko /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3290sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/rulo/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux'
make: *** [install] Error 2


what can I do? still no wifi :( 

thanks for the help

---

### Post by praseodym on 2014-01-21
Try this one:
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
sudo tar xvf 5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz -C /usr/src/
sudo dkms add -m Ralink_3290sta -v 2.6.0.0
sudo dkms build -m Ralink_3290sta -v 2.6.0.0
sudo dkms install -m Ralink_3290sta -v 2.6.0.0 
sudo cp /usr/src/Ralink_3290sta/src/common/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
Reboot.

---

### Post by kenlibero on 2014-01-23
The how-to in the first post perfectly works on HP Envy DV6-7350SL with RT3290 wifi, ubuntu 12.04

Thank you very, very much spc_hicks09  :)  =D>

---

### Post by a5du on 2014-03-31
Hi,

wow - I am impressed! It "just" worked!

Thank you very much!

Axel

Lubuntu 12.04 on HP Pavilion TS11

---

### Post by Joseph_Neri on 2014-04-04
Thanks for this info.  Like so many other people, I've been very frustrated by this issue and actually purchased a different laptop in order to circumvent the problem.

---

### Post by branded7k on 2014-08-06
Spc_Hicks09;

    Thanks for this solution.  Worked the first time as advertised!  I was working on my Father-In-Law's HP Pavillion 15 N227nr laptop.  I had to remove Winbloze 8.1 and install Ubuntu 12.04.  I overcame the hurdles of the UEFI BIOS and removing the sub standard OS, but was having trouble getting the wireless interface up.  Tried a couple of solutions to no avail, before coming across this one.  Well done and nice job on the documentation.  I've been retired now for 7 years from the IT profession where I had to support Microsoft in an enterprise environment for over 30 years.  I've since converted many friends and family to Linux.  Ubuntu has made my life SO much easier and allowed me more time to enjoy my retirement!  Thanks again for the solution and professional job on the docs!!

---

### Post by Interruptor on 2014-09-09
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c:1136:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/var/lib/dkms/Ralink_3290sta/2.6.0.0/build/src/os/linux/../../os/linux/rt_linux.c:1137:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^

---

### Post by shivam_mishra2 on 2014-11-14
sir i can't instll it since it showing "DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/config.mk
-bash: DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/config.mk: Permission denied"   here is the screen shot

---

### Post by Dan_Rau on 2015-06-21
Thanks spc_hicks09 ... :) ;)

Here is my problem with WiFi
[http://ubuntuforums.org/showthread.php?t=2283137&p=13306559#post13306559](http://ubuntuforums.org/showthread.php?t=2283137&p=13306559#post13306559)

So I did for about 2 years that workaround 
[http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/](http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/)

Everytime my Ubuntu needs a restart (after updates) everytime I had to do that workaround.

No, I've tried what you write on the first page of this thread. So let's see if it's ok after other updates and restarts :)

I will let you know!

---

### Post by Dan_Rau on 2015-07-09
[COLOR=#000000]No![/COLOR]
[COLOR=#000000]It is happening again with the HP laptop![/COLOR]
[COLOR=#000000]I did some updates. It asked me for restart - and after restart the same thing -> WiFi not working[/COLOR]
[COLOR=#000000]So I have to do that workaround again[/COLOR]

---

### Post by javed2 on 2015-08-04
I followed exactly as written in here, but after the **make** command, some errors showed up and the **make install **command did not work after that. As a a result, **sudo modprobe rt3290sta** gives a fatal error. Any help with it? If it comes to any help, I've taken a screenshot of the last portion of the messages I got in the terminal. 
[IMG]http://i.imgur.com/Sc9O5xQ.png[/IMG][COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]

---

### Post by Lokesh_Kumar_Pande on 2015-09-05
Hi **[[COLOR=#000000]spc_hicks09[/COLOR]]("http://ubuntuforums.org/member.php?u=1413160")**
I've followed the same steps you disclosed in your posts. But I'm dealing with some error while make command. The errors are 

[COLOR=#000000][FONT=Verdana]scripts/Makefile.build:257: recipe for target '/home/aryan/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.o' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make[2]: *** [/home/aryan/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.o] Error 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Makefile:1394: recipe for target '_module_/home/aryan/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make[1]: *** [_module_/home/aryan/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux] Error 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-26-generic'[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Makefile:380: recipe for target 'LINUX' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]make: *** [LINUX] Error 2[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]And in file DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/config.mk it doesn't have " HAS_NATIVE_WPA_SUPPLICANT=y " this line.

[/FONT][/COLOR]It's getting frustrating please help me with this!!!!!

---

### Post by goran7 on 2015-12-22
I was getting the same [COLOR=#000000][FONT=Verdana]LINUX Error 2, so I found the solution [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466").[/FONT][/COLOR]


Here's what you do:

First, download the modified driver from [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466/+attachment/4275460/+files/rt3290sta-2.6.0.0.dkms.tar").

Then, right click on the file, choose 'open as administrator', and extract the archive in /usr/src

After that, open a terminal. If you don't have dkms installed, you need to install it:

```
sudo apt-get install dkms
```

Then run the following command:

```
 sudo dkms install -m rt3290sta -v 2.6.0.0 --force 
```

Reboot.


Update: It doesn't work anymore on 16.04. Neither do the other solutions posted here. Only the rt2800pci driver that comes with Ubuntu seems to work.

---

### Post by sandipkc7 on 2016-01-21
I have tried all replies and solutions on this thread. After trying according to #1 post, I am getting error after these commands

```
sudo su

make


```

Below is my error message

> make -C tools
make[1]: Entering directory `/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/tools'
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/tools/bin2h
cp -f os/linux/Makefile.6 /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/Makefile
make -C /lib/modules/3.19.0-32-generic/build SUBDIRS=/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-32-generic'
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_md5.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.o
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c:1466:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainTextLength));
      ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_aes.c:1561:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainLength));
      ^
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.o
In file included from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_os.h:42:0,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_comm.h:56,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/rt_config.h:36,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c:30:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c:529:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:463:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/mlme.c:530:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:463:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wep.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/action.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_data.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.o
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.c: In function ‘rt28xx_init’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.c:162:3: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat=]
   DBGPRINT(RT_DEBUG_OFF,("PllCtrl:0x%x\n",PllCtrl.word));
   ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_init_inf.c:178:10: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
          AUTO_WAKEUP_STRUC AutoWakeupCfg;
          ^
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_aes.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_sync.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/eeprom.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_info.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.o
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg3Action’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_wpa.c:1032:13: warning: unused variable ‘Cancelled’ [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_radar.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.o
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/spectrum.c:1972:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffer (size=%d).\n", __FUNCTION__, sizeof(MEASURE_RPI_REPORT)));
   ^
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_channel.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_profile.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_asic.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/ps.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/uapsd.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.o
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_profile.c:409:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION__, pRxBlk->DataSize + sizeof(wlan_ng_prism2_header)));
         ^
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/assoc.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/auth.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sync.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sanity.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.o
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxDataFrame’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable ‘pFmeCtrl’ [-Wunused-variable]
  FRAME_CONTROL *pFmeCtrl = &pHeader->FC;
                 ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable ‘OldPwrMgmt’ [-Wunused-variable]
  UCHAR OldPwrMgmt = PWR_ACTIVE;
        ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c: In function ‘STAHandleRxMgmtFrame’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/rtmp_data.c:766:5: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
     UCHAR uRSSI2;
     ^
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/connect.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/wpa.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.o
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c: In function ‘RTMPQueryInformation’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c:3956:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), pAd->CommonCfg.Channel));
    ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c: In function ‘RtmpIoctl_rt_private_get_statistics’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../sta/sta_cfg.c:7220:1: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 3 has type ‘EEPROM_NIC_CONFIG3_STRUC’ [-Wformat=]
 sprintf(extra+strlen(extra), "pAd->NicConfig3.field.CoexAnt == 0x%x\n\n",pAd->NicConfig3);
 ^
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../common/rt_os_util.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.o
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:508:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
   ^
In file included from ./arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/thread_info.h:23,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:18,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_os.h:42,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_comm.h:56,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:35:
./arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:510:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pData, DataSize);
   ^
In file included from ./arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/thread_info.h:23,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:18,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_os.h:42,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_comm.h:56,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:35:
./arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:662:20: warning: assignment makes integer from pointer without a cast [enabled by default]
   pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                    ^
In file included from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_os.h:42:0,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/rtmp_comm.h:56,
                 from /home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:35:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/include/os/rt_linux.h:992:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:681:2: note: in expansion of macro ‘SET_OS_PKT_DATATAIL’
  SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);
  ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:708:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:1136:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.c:1137:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^
make[2]: *** [/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/sandeep/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-32-generic'
make: *** [LINUX] Error 2

Anyone know how to solve these errors?

---

