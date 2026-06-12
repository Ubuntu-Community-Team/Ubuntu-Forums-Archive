---
title: "LG P1 Express Dual &quot;Kill switch must be turned off for wireless networking to work&quot;"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by Awale on 2010-02-17
Dear people,

I am frustrated with this issue I cannot solve. Recently I installed ubuntu in my LG P1 express dual laptop, and got it working with the sound, webcam, and LAN. It took me a while, but I have learned a lot..

The thing is, I cannot manage to set up wireless networking working. For what I read and discovered, it has to do with an internal RF switch that deactivates the wifi card.

On windows, one may switch it on or off with fn+F6. However, that is not working on linux. Anyone has any idea on how to access and change this switch with a command or something? 

Nothing on BIOS about wireless. 

when I do 

```
 sudo cat /var/log/messages | grep -i wireless

```

I get:

```
Feb 17 20:08:34 XXXXX kernel: [   27.889915] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Feb 17 20:08:34 XXXXX kernel: [   29.163795] Kill switch must be turned off for wireless networking to work.
```


On doing: iwconfig, it reads:

lo        no wireless extensions.
eth0      no wireless extensions.

So no wlan0 is listed.

However with "sudo lshw -C network" the network is there and the driver is loaded

  *-network               
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:91:14:0e:3f
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=et131x ip=192.168.0.6 latency=0 module=et131x multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945


Any hint? Thank you very much in advance ;)

Awale

---

### Post by chili555 on 2010-02-17
Please open a terminal and do:```
sudo rfkill unblock all
rfkill list
```Please post the results.

---

### Post by Awale on 2010-02-17
Hello Chilli555,

I dont seem to have any command named rfkill, since I get:

```
sudo: rfkill: command not found
```

Maybe this is something very basic but, Im having trouble finding this program and installing it (its not on synaptic). Could you please tell me how I do it?

Thank you!

---

### Post by chili555 on 2010-02-17
> Could you please tell me how I do it?```
sudo apt-get install wireless-tools
```You might have to open System -> Admin -> Software Sources and be sure that universe, multiverse and restricted are enabled. 

I'm sorry, I thought it was installed by default.

---

### Post by Awale on 2010-02-17
Already installed wireless-tools, but its not solving the problem. Still rfkill is not available. 

Maybe it has something to do with "backports-modules-hardy"? I installed it because I read about that on another thread. I rebooted and I got something new:

Now iwconfig throws this: (edit: what I wanted to express is that before wmaster0 and wlan0 where not showing in this list)
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```But I cannot access rfkill. I removed and reinstalled wireless-tools, but it makes no difference. I also tried to install rfkill from a tarball (with make) but it displays many errors.

Any idea whats wrong? thanks again

---

### Post by chili555 on 2010-02-17
> backports-modules-*hardy*I don't believe rfkill is available in Hardy, unfortunately. Let's approach it another way. First, let's see:```
lsmod
lspci -nn
dmesg | grep iwl
```I am googling. Thanks.

Do you have any interest in installing Karmic?

---

### Post by Awale on 2010-02-18
Hello again! Still no wifi...

this is what lsmod says:

```
Module                  Size  Used by
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  2 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ipv6                  268036  10 
sbp2                   24072  0 
af_packet              23812  2 
lp                     12324  0 
tifm_sd                12936  0 
pcmcia                 40876  0 
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
snd_hda_intel         346264  3 
blkcipher               8324  1 ecb
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78724  2 snd_hda_intel,snd_pcm_oss
iwl3945                96244  0 
lbm_iwl_mac80211      242420  1 iwl3945
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
rfkill                  8596  2 iwl3945
led_class               6020  1 iwl3945
lbm_iwl_cfg80211       33376  2 iwl3945,lbm_iwl_mac80211
snd_seq_dummy           4868  0 
fglrx                1555468  23 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
et131x                 42528  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sdhci                  19076  0 
container               5632  0 
snd_timer              24836  2 snd_pcm,snd_seq
video                  19856  0 
output                  4736  1 video
tifm_7xx1               8576  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mmc_core               51460  2 tifm_sd,sdhci
serio_raw               7940  0 
tifm_core              11012  2 tifm_sd,tifm_7xx1
ac                      6916  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
wmi_acer                9644  0 
battery                14212  0 
intel_agp              25492  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
evdev                  13056  8 
button                  9232  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                34760  2 fglrx,intel_agp
soundcore               8800  2 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
psmouse                40336  0 
ext3                  136968  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  4 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
ata_generic             8324  0 
ata_piix               19588  3 
ohci1394               33584  0 
libata                159728  3 pata_acpi,ata_generic,ata_piix
scsi_mod              151692  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36616  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

lspci -nn returns this:

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X1400 [1002:7145]
02:00.0 Ethernet controller [0200]: Agere Systems ET-131x PCI-E Ethernet Controller [11c1:ed00] (rev 02)
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
06:00.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
06:00.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
06:00.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
06:00.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

```

and finally dmesg says:

```
[   24.441056] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   24.441060] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   24.442332] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   24.495439] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   24.496126] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   25.209426] iwl3945: Radio disabled by HW RF Kill switch
[   25.552914] iwl3945: Radio disabled by HW RF Kill switch
[   25.917692] iwl3945: Radio disabled by HW RF Kill switch
[   25.918236] iwl3945: Radio disabled by HW RF Kill switch
[   27.625359] iwl3945: Radio disabled by HW RF Kill switch
[   27.633876] iwl3945: Radio disabled by HW RF Kill switch
[   27.687171] iwl3945: Radio disabled by HW RF Kill switch
[   27.687701] iwl3945: Radio disabled by HW RF Kill switch
[   30.396228] iwl3945: Radio disabled by HW RF Kill switch

```

I hope this can tell you the info you need. Thanks again! 
Awale

---

### Post by Awale on 2010-02-18
> **chili555 said:**
> Do you have any interest in installing Karmic?

I think that installing karmic may be a good idea, but I dont have the time now... and I would rather keep with old good hardy if possible :)

However if the problem persists I will eventually change into karmic

---

### Post by chili555 on 2010-02-18
> [   30.396228] iwl3945: Radio disabled by [COLOR="Red"]HW[/COLOR] RF Kill switchYou are sure, super sure that there is no physical (hardware) slider or pushbutton in addtion to Fn+F6 to activate or disable the wireless?

I am pretty interested in this:> wmi_acer                9644  0 
It looks like Acer is the OEM. You might try:```
sudo rmmod -f wmi-acer
```Does the behavior of Fn+F6 change? If not, you might also try:```
sudo modprobe wmi-acer
sudo modprobe acerhk
```I am not totally sure Hardy still had *acerhk.*

Finally, I am interested in this:> [COLOR="Red"]rfkill  [/COLOR]                8596  2 iwl3945
led_class               6020  1 iwl3945
lbm_iwl_cfg80211       33376  2 iwl3945,lbm_iwl_mac80211
Can you please run:```
modinfo rfkill
```Is there a parameter (parm:) we can manipulate?

---

### Post by Awale on 2010-02-18
Hello Chili555,

Yes, I am positive: there is no button/slider whatsoever to turn on/off the wifi. Only fn + f6.. I see the problem may be the RFswitch is in "hard" off. But there is no "hardware" switch... ther should be a way to turn it on with software, just like in windows.

About the commands you suggested, I get these responses:

removing wmi-acer does not change anything on the behaviour of fn+f6. 

modprobing acerhk returns this:

```
sudo modprobe acerhk
FATAL: Error inserting acerhk (/lib/modules/2.6.24-27-generic/ubuntu/misc/acerhk.ko): Cannot allocate memory
```

and rfkill seems to have no parameters:

```
modinfo rfkill
filename:       /lib/modules/2.6.24-27-generic/kernel/net/rfkill/rfkill.ko
license:        GPL
description:    RF switch support
version:        1.0
author:         Ivo van Doorn <IvDoorn@gmail.com>
srcversion:     78515B99CD84322FA102944
depends:        
vermagic:       2.6.24-27-generic SMP mod_unload 586
```

There's no parameter.. I also tried, with no result,

```
modinfo -F param rfkill
```

Any other idea? thank you for all your help so far.

---

### Post by chili555 on 2010-02-18
We're kind of experimenting here. I can't find much about LG laptops. We may be groundbreakers!

I wonder if ami_acer is actually conflicting with acerhk. Please try this:```
sudo rmmod -f ami_acer
sudo rmmod -f acerhk
```It is probably not loaded, but we'll be sure.```
sudo modprobe acerhk poll=0
```Now are FN+F6 working? If not, please try:```
sudo rmmod -f acerhk
sudo modprobe acerhk autowlan=1
```Please report your results.

---

### Post by Awale on 2010-02-18
Uhm its not working at all, sorry... all commands are complaining about something:

```
*sudo rmmod -f ami_acer*
ERROR: Removing 'ami_acer': No such file or directory

*sudo rmmod -f acerhk*
ERROR: Removing 'acerhk': No such file or directory

*sudo modprobe acerhk poll=0*
FATAL: Error inserting acerhk (/lib/modules/2.6.24-27-generic/ubuntu/misc/acerhk.ko): Cannot allocate memory

*sudo rmmod -f acerhk*
ERROR: Removing 'acerhk': No such file or directory

*sudo modprobe acerhk autowlan=1*
FATAL: Error inserting acerhk (/lib/modules/2.6.24-27-generic/ubuntu/misc/acerhk.ko): Cannot allocate memory

```

Is there any way to access the rfswitch without modules? perhaps something that sets the desired value at boot time? 

I ve been looking for info on this switch but didnt find much..

Thanks again. Any clue about what else could be done?

---

### Post by Awale on 2010-02-27
Hello again! 

Im playing right now with ubuntu karmic cd, and testing if wifi works before installing...
It seems it isnt thou.. 

rfkill list shows the wifi is hard blocked. Any tips, now that i am in karmic? Tnx!!

---

### Post by chili555 on 2010-02-27
May I please see:```
iwconfig
```While you do that, I am going to get a Xanax and a scotch.

---

### Post by Awale on 2010-02-27
Hey there,

finally, i got tired and i took the easy way... installed windows :(

Sorry for the disapointment, but i am giving my thesis speech soon and i need a working computer...

I will install karmic afterwards and check for the wifi. Besides, i read somewhere that turning wifi on in windows with fn f6 then solves the problem in ubuntu, and i have to try.

Thank you for all your help; It is because of the community that i want to have linux (if only hardware worked right away!)

i will post some news on the topic after i install karmic. 

Regards to you, Chili

---

### Post by omidbrb on 2010-06-08
Guys,

I have the exact same problem on the exact same laptop. All hints lead to nowhere. Any idea how to enable the wlan card?

Awale, did you manage to do something for it?

Best,
Omid

---

### Post by Awale on 2010-06-09
No, I'm sorry. I would be very happy to be able to help. I think I read somewhere that the solution is to double boot into windows, enable the wifi there, then come back to linux. 

My problem was that I had uninstalled windows, and I didnt want to go that way... In the end I just got tired and switched back to windows (too bad... now I swear something everytime windows does something I dont like --- that is, three times per second)

As soon as I have some free time, I will try to return to ubuntu and solve the issues with the wifi :)

Good luck in finding an answer, let me know if you find something omidbrb.

---

### Post by omidbrb on 2010-06-13
I did a dummy Win XP installation, turned the Wifi card on by fn-f6 and now it works in Ubuntu! 

The funny thing was that the driver that was reacting to fn-f6 in Win XP was "On-screen display driver" !!

---

### Post by Luponiano on 2011-08-07
Hello, I have the same laptop. I had the wifi working by turning it on throught Win XP On Screen display. Sounds strange but that was the way to make it working.

I also remember making some configurations arrangements... but I can not quite remember them. I found them by googling. It was when I was beggining with ubuntu and I tried everything I read without knowing what was I doing.

---

