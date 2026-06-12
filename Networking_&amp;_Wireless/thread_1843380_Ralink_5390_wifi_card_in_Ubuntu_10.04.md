---
title: "Ralink 5390 wifi card in Ubuntu 10.04"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by bookworm4life on 2011-09-13
I just installed Ubuntu 10.04.03 on a HP Pavilion G6, everything works fine except that the wireless networking does not show up in the network menu.  From what I have read here and on other forums it is a common problem with a "simple" solution.

I have seen a couple of solutions listed below.

[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716) (This is the one I tried to follow)
[http://ubuntuforums.org/showthread.php?t=1740963](http://ubuntuforums.org/showthread.php?t=1740963)
[http://ubuntuforums.org/showthread.php?t=1780954](http://ubuntuforums.org/showthread.php?t=1780954)

I was able to find the driver off the Ralink website and unpack it but that is as far as I got.  I am not really new to Ubuntu but it has always "just worked" for me and I have never even had to open the terminal before today.

I made it to step 5 and then got confused.  I am not even sure how the "make" and "make install" commands work, and even less sure about actually using them. 

If anyone could give me some pointers I would greatly appreciate it.  Or if anyone wanted to volunteer to show me how to do it via remote desktop sometime this weekend(assuming i could figure that out) that would be even more wonderful.

For now however I need to hit the hay because I have to wake up for work in a couple of hours.  I will be sure to check back here before I leave this afternoon and maybe even a few times at work.

Thanks for any help you are able to give me.

---

### Post by praseodym on 2011-09-13
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
```

---

### Post by bookworm4life on 2011-09-13
I ran into a bit of other trouble when I got up this afternoon.  I went  to turn it on and the display did not work.  I also tried using the  external display without success.

I think I came across threads relating to this issue while I was  browsing this morning and I will check them out to see what I can come  up with.

I guess this is is what I get for buying a brand new laptop and  expecting it to work right out of the box.  I wish I could return it but  I am pretty sure I voided the warranty when I deleted windows :  ).   Thanks for your reply and Ill post back  here when I get the display up  and running again.

PS Just out of curiosity what does this command do for me?


> **praseodym said:**
> 

```
lspci -nnk | grep-iA2 net
lsusb
lsmod
iwconfig
```

---

### Post by praseodym on 2011-09-13
These command show us your system info, PCI- and USB-devices, kernel-modules and wireless interfaces.

---

### Post by varunendra on 2011-09-14
@ bookworm4life,

If everything except wifi was working fine as you mentioned in your first post, then it should still work in a live session. Boot off your live medium that you used to install Ubuntu (live cd or usb) and run the commands suggested by praseodym from there. If you can successfully boot into the live session, it may also help troubleshooting other issues like the one with your graphics now. In case any further error occurs, just post back describing the nature of the problem. HP uses pretty decent hardware, and Ubuntu 10.04 should work quite stably on it.

By the way, you should have learnt by now why backups are so important. Next time, consider making a system image using clonezilla or any of your favourite disk-imaging tools before messing up with a working installation :).

---

### Post by bookworm4life on 2011-09-16
Sorry for the long delay....I am back and have the display working for the most part.  Albeit nothing I did intentionally except leave it sit for a few days while I was away from home and turn it on when I got back.

At the moment I am connected to the internet on the laptop using and old Belkin USB dongle that I had laying around and that worked the instant I plugged it in.

I ran the commands you mentioned in the terminal and sadly am not sure I did it right because not all of them worked but this is what they showed:

[INDENT]```

:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1510]
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9802]
00:01.1 Audio device [0403]: ATI Technologies Inc Device [1002:1314]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [SATA and FC Enabled] [1002:4394]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:15.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a0]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.1 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a1]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:15.2 PCI bridge [0604]: ATI Technologies Inc Device [1002:43a2]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Device [1022:1719]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
06:00.0 Network controller [0280]: RaLink Device [1814:5390]
07:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

:~$ grep-iA2 net
grep-iA2: command not found
(IF I AM DOING SOMETHING WRONG HERE LET ME KNOW)

:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 050d:705e Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

:~$ lsmod
Module                  Size  Used by
joydev                  8740  0 
hid_logitech            7388  0 
ff_memless              4093  1 hid_logitech
usbhid                 36110  1 hid_logitech
hid                    67288  2 hid_logitech,usbhid
binfmt_misc             6587  1 
ppdev                   5259  0 
arc4                    1153  2 
rtl8187                50680  0 
mac80211              205402  1 rtl8187
snd_hda_codec_idt      52042  1 
snd_hda_codec_atihdmi     2367  1 
led_class               2864  1 rtl8187
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_idt,snd_hda_codec_atihdmi,snd_hda_intel
snd_seq_dummy           1338  0 
snd_hwdep               5412  1 snd_hda_codec
cfg80211              126144  2 rtl8187,mac80211
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               57374  0 
eeprom_93cx6            1333  1 rtl8187
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
i2c_piix4               8335  0 
video                  17375  0 
output                  1871  1 video
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Brandon"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:CD:01:DC   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```[/INDENT]

---

### Post by praseodym on 2011-09-16
You need to install this driver for your device:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747)

Just copy/paste the commands into the terminal.

---

### Post by bookworm4life on 2011-09-16
Still doesnt seem to work.  When asked yes or no I get an Abort message.
[INDENT]```
:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.4 libstdc++6-4.4-dev xz-utils
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc
  libstdc++6-4.4-dbg libstdc++6-4.4-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dkms dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
  xz-utils
0 upgraded, 9 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 7,820kB/8,601kB of archives.
After this operation, 25.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

```[/INDENT]

---

### Post by varunendra on 2011-09-16
Did you press 'y' then 'enter' and still the 'Abort' message? Seems strange to me. What if you try to install the same packages via Synaptic (**System > Administration > Synaptic Package Manager** > type package names in the search box)?

---

### Post by bookworm4life on 2011-09-16
yes I pressed Y and then enter and got the abort message.  I also thought it was strange.  I will try the Synaptic package manager when I get home in the evenening.  Thanks for the tip.

---

### Post by bookworm4life on 2011-09-19
Hey everyone, I tried the Synaptic Package Manager and never did find the package there.  So out of desperation I tried the Terminal route again and for reasons beyond me when I pressed Y it started working.  It seemed like it worked and did its thing, but when it was done I still didn't see my hardware in the networking box.  So I tried restarting with no luck and now here I am again.  I tried the command again and it said that it was going to reinstall, so I assume the package was installed the first time.  

I checked to see if it shows up with the first command I was given but I do not see it on the list.[INDENT]```

user@Mobile1:~$ lspci -nnk | grep-iA2 net
grep-iA2: command not found
user@Mobile1:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 050d:705e Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@Mobile1:~$ lsmod
Module                  Size  Used by
arc4                    1153  2 
rtl8187                50680  0 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52042  1 
snd_hda_codec_atihdmi     2367  1 
snd_hda_intel          22069  2 
snd_pcm_oss            35308  0 
snd_hda_codec          74201  3 snd_hda_codec_idt,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_pcm_oss,snd_hda_codec
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57374  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
video                  17375  0 
output                  1871  1 video
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_pcm_oss,snd_hda_codec,snd_hwdep,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
i2c_piix4               8335  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
user@Mobile1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Junxion_Box"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:02:6F:47:B4:D6   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0d

```[/INDENT]And this is what shows up when I tried to install a second time.[INDENT]```

-essential dkms patch fakeroot unzipux-headers-$(uname -r) build 
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 6 reinstalled, 0 to remove and 12 not upgraded.
Need to get 0B/1,276kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 

```[/INDENT]I am even more confused at this point because it seemed like it should have worked.

---

### Post by praseodym on 2011-09-19
Did you also install the driver itself and not only the compilation tools?

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u 
```

---

### Post by varunendra on 2011-09-19
Since *praseodym* is handling the issue much better than I can, I'd only point out this (which has nothing to do with solution, only some more info will be available):> **bookworm4life said:**
> [INDENT]```

user@Mobile1:~$ lspci -nnk | [COLOR=Red]**grep-iA2 net**[/COLOR]
grep-iA2: command not found
```
[/INDENT] The quoted command should have been
```
lspci -nnk | grep -iA2 net
```
Please notice that there is a space between **grep** and **-iA2**. I felt the urge to point this out as the same mistake is being repeated again and again in the thread.


@praseodym,

Please correct the error in your original post so that people following it don't repeat the mistake.

---

### Post by bookworm4life on 2011-09-19
Thanks varunendra, I was wondering why I kept getting the command not recognized error.

The Ralink 5390 card did show up when I corrected the command, but still is not accessible in the networking menu.
[INDENT]```

~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
06:00.0 Network controller [0280]: RaLink Device [1814:5390]
07:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)


```[/INDENT]

---

### Post by praseodym on 2011-09-19
Again: Did you also install the driver? If no, do so, if yes, load the module by hand:

```
sudo modprobe -v rt5390sta
sudo service network-manager restart
```

Edit: Typo in the named posting corrected, thanks to varunendra

---

### Post by bookworm4life on 2011-09-19
Apparently the driver does not exist, or is under another name.
[INDENT]```

sudo modprobe -v rt5390sta
FATAL: Module rt5390sta not found.
user@Mobile1:~$ sudo service network-manager restart
network-manager start/running, process 1554


```[/INDENT]

---

### Post by praseodym on 2011-09-19
Try to install it again and reboot

---

### Post by CalSkeptic on 2011-09-19
> **praseodym said:**
> You need to install this driver for your device:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747)

Just copy/paste the commands into the terminal.

Hey, thank you, praseodym.  It does work!

I would note that I had to copy and paste each command separately into the terminal and wait for it to finish before continuing.

---

