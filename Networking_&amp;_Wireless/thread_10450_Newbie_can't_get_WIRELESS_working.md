---
title: "Newbie can't get WIRELESS working"
date: 2005-01-07
forum: Networking &amp; Wireless
---

### Post by Heretushi on 2005-01-07
Hello everyone.

First I have done my homeworks. I DID search the forums. And I found what was SUPPOSED to be the answer to my question. But the "answer" does not work. ;)

So here I am. I have a D-Link DWL-G520 card. Yes, this is the one with an Atheros "fully-supported" chipset on it.

So I installed Ubuntu. And no, it did not recognized my card during setup. Yes, I know it's ok. So I went into Ubuntu full installation anyway.

Ok, I enter Gnome. (Nice interface, I always used KDE before. Or Explorer...) I go into the interface configuration. I set up my ESSID name, my WEP key, and set it to DHCP. And off we ... DON'T ... go!!

Here it is : 

[IMG]http://heretushi.net/ubuntu/ath0_dhcp.png[/IMG] 

All I have is packet error. No transmission, no IP, no nothing!

So I say to myself : Don't worry, I'll set my information manually... I set my IP, my subnet, my gateway. And off we ... DON'T ... go!!! :sad:

Here it is : 

[IMG]http://heretushi.net/ubuntu/ath0.png[/IMG] 

My routeur (DI-624) is set to static DHCP. This means that my DHCP detect the MAC and deliver a specific IP to the computer. This should not interfere with the process.

Soooooooo. I see that nothing is going on in Ubuntu. So I go on my pure evil Compaq/WindowsXP machine and check if there's ANYTHING, even the cofee machine or something, trying to make a connection. My cofee machine is indeed connected but my Linux machine is nowhere to be found.

Is there anything I can do?

P.S.: Yes, I'm a frenchie. Peace. Hehehe.

---

### Post by Heretushi on 2005-01-08
I've been on the chat and they pointed me to [this FAQ about Wifi.](http://www.ubuntulinux.org/wiki/WiFiHowto/view?searchterm=atmel) 

The problem is that it's completely not working for me.

Here is the return :

[IMG]http://heretushi.net/ubuntu/no_perm.png[/IMG] 

So, errors, errors, errors...  ](*,)

Is there anything I can do?

---

### Post by Heretushi on 2005-01-08
**Here are some infos that might help :**

vincent@Linuxiez:~ $ uname -r
2.6.8.1-3-386

vincent@Linuxiez:~ $ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (r ev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller  (rev a1)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:01:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 96 00]
0000:02:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Se condary)

vincent@Linuxiez:~ $ lsmod
Module                  Size  Used by
nls_iso8859_1           4352  0
nls_cp437               6016  0
vfat                   13312  0
fat                    41792  1 vfat
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230020  8
button                  6936  0
ac                      5132  0
battery                 9740  0
af_packet              20872  2
ath_pci                50724  0
wlan                  105564  2 ath_pci
ath_hal               129232  2 ath_pci
shpchp                 87276  0
pciehp                 83948  0
pci_hotplug            30640  2 shpchp,pciehp
snd_intel8x0           33068  3
snd_ac97_codec         59268  1 snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
forcedeth              16128  0
ehci_hcd               27780  0
ohci_hcd               19460  0
usbcore               104292  4 ehci_hcd,ohci_hcd
nvidia_agp              7580  1
agpgart                31784  1 nvidia_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  0
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
ide_disk               16768  4
amd74xx                13340  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   25904  728
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

---

### Post by cllow on 2005-01-08
Hi, try re-installing in expert instead of default mode. My wireless card was only detected in expert mode. Good luck!

---

### Post by Heretushi on 2005-01-08
W00t!!! =D> 

I was able to do it! I'm writing this from my Ubuntu box!

How I did it? Simply disabled the WEP encryption. :oops: 

Now, I don't like this situation so I'll have to try to get my Ubuntu work with WEP enabled. I live in an appartment block so stolen frequency is a very real possibility.

Anyway, I'll keep puting my tests in here.

Thanks to the folks on the IRC channel. You guys should go take a look.

---

### Post by Heretushi on 2005-01-08
I understand. I understand everything. :o

My card wouldn't connect because my WEP was ASCII 128bits.

Now that I use a HEX 64bits WEP, everything is juuuuust fine! :)

So, here I am, using my Ubuntu box like I always wanted to use a Linux distro before but wasn't able to.

It really is amazing.

Status : Problem SOLVED.

---

### Post by MrTrumpets on 2005-01-28
Heretushi, can you post your /etc/network/interfaces file?

I cannot get WEP to work no matter what I try.. it's kind of annoying.

(I did try 64 bit)

thanks!

---

