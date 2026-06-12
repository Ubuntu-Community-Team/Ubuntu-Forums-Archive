---
title: "Wireless Problem on Ubuntu 11.10"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by noisysoul on 2011-10-21
Hi, a few days ago I installed **Ubuntu 11.10** *(32bits)* on my laptop *(Samsung R430)*. When I try to connect to the internet using wi-fi a pop-up message asks the password as usual and after I type it correctly it shows a notification box telling me that I'm disconnected. If I connect the cable directly it works perfectly. _Ubuntu 11.04 or any older gives no problem_, I mean, it's not my router or my laptop, it's the OS (Ubuntu 11.10). I've read many forums and pages and lots of buddies out there are having the very same problem (or similar). I've updated and tried a few things but it hasn't worked.

Please help me out...
Thank you so much. Greetings from Chile.
Have a nice day, bye!

:p :p :p

---

### Post by burnblack on 2011-10-25
> **noisysoul said:**
> Hi, a few days ago I installed **Ubuntu 11.10** *(32bits)* on my laptop *(Samsung R430)*. When I try to connect to the internet using wi-fi a pop-up message asks the password as usual and after I type it correctly it shows a notification box telling me that I'm disconnected. If I connect the cable directly it works perfectly. _Ubuntu 11.04 or any older gives no problem_, I mean, it's not my router or my laptop, it's the OS (Ubuntu 11.10). I've read many forums and pages and lots of buddies out there are having the very same problem (or similar). I've updated and tried a few things but it hasn't worked.

Please help me out...
Thank you so much. Greetings from Chile.
Have a nice day, bye!

:p :p :p

same problem here :(
i'm a 100% sure it's the OS as well :x

---

### Post by dooper on 2011-10-25
I do hope Ubuntu prioritises the whole wireless issue as it seems very common and is now a major sticking point for many people. Everything else is just fine for me ..errmm...except for wireless.  :o

---

### Post by hero1900 on 2011-10-27
i also have this issue hope they fix it

---

### Post by faruk.onder on 2011-11-01
Hi,

did you find any solution for this bug. it is really annoying me.

and also this is not probably an os problem, it is exacly an os problem. wish they solve this immediately

---

### Post by IJHarvey on 2011-11-01
Just wanted to add to this cry for help.  I have a MiFi hotspot that works with pretty much everything I've thrown at it (Desktop on Natty, 2 android tabs, windows notebook, Natty notebook)  but I can only connect very occasionally with oneiric on my notebook and then it tends to lose the connection quite quickly.
Ian

---

### Post by TBABill on 2011-11-01
Without hardware information it'll be impossible to help. Can you post information on the chipset of your wireless card so we can assist? If unsure how, easiest is to just open a terminal and run ```
lspci
``` and ```
lsmod
``` and paste their outputs here for review.

---

### Post by faruk.onder on 2011-11-02
Hi @TBABill

here the requested information below.
thank you for your assistance.


onder@onder-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 03)
03:00.4 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 03)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
onder@onder-ubuntu:~$ lsmod
Module                  Size  Used by
rfcomm                 47946  8 
bnep                   18436  2 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  1 
vboxdrv               282548  4 vboxpci,vboxnetadp,vboxnetflt
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  4 
arc4                   12529  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
i915                  566711  11 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
drm_kms_helper         42558  1 i915
snd_seq_midi           13324  0 
btusb                  18600  2 
bluetooth             166112  23 rfcomm,bnep,btusb
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   236330  7 i915,drm_kms_helper
iwlagn                314213  0 
snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
dell_laptop            13831  0 
soundcore              12680  1 snd
mac80211              310872  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
dell_wmi               12681  0 
ppdev                  17113  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
dcdbas                 14490  1 dell_laptop
intel_ips              18089  0 
sparse_keymap          13890  1 dell_wmi
parport_pc             36962  0 
psmouse                73882  0 
wmi                    19256  1 dell_wmi
serio_raw              13166  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  3 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
libahci                26861  1 ahci
e1000e                160535  0 
onder@onder-ubuntu:~$ ^C
onder@onder-ubuntu:~$


My notebook is a dell e6410.

the problem is, I can connect internet with wireless but some times it starts to asking username and password then it never connects again until restart or pass some long time. In our office we have many connections we can use, If this problem happens, I can't connect with none off them

---

### Post by faruk.onder on 2011-11-02
Hi,

how can we create a bug report for this problem. if anyone can create quickly, could he/she open a bug for it.

---

### Post by tuxt on 2011-11-02
have a look at this:

[http://www.liberiangeek.net/2011/09/having-wireless-wi-fi-trouble-in-ubuntu-use-wicd-network-manager-instead/](http://www.liberiangeek.net/2011/09/having-wireless-wi-fi-trouble-in-ubuntu-use-wicd-network-manager-instead/)

---

### Post by faruk.onder on 2011-11-03
hi tuxt,

thank you for link, but I want to use with default settings and programs.

---

### Post by siddi on 2011-11-20
lspci gave me the following
iddharth@siddharth-Aspire-5570:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


lsmod gave me this....
siddharth@siddharth-Aspire-5570:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
gspca_vc032x           31999  0 
gspca_main             27610  1 gspca_vc032x
videodev               85626  1 gspca_main
joydev                 17393  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
pcmcia                 39822  0 
snd_hda_intel          24262  5 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
btusb                  18160  2 
snd_seq_midi_event     14475  1 snd_seq_midi
tifm_7xx1              12937  0 
bluetooth             148839  23 bnep,rfcomm,btusb
tifm_core              15040  1 tifm_7xx1
yenta_socket           27428  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia_rsrc            18367  1 yenta_socket
psmouse                73673  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
iwl3945                73329  0 
i915                  505108  3 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
snd                    55902  18 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
wmi                    18744  1 acer_wmi
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0


Please Help... The problem keeps getting worse....

---

### Post by OwnSurname on 2012-01-06
Same problem here: the wireless work nicely (on a Dell Latitude D630) until it gets disconnected. Then, it prompts for the password, and although it's correct, it's not able to connect anymore. Any help is appreciated, it's quite an annoying bug as the only option it works for me is to reboot.

---

### Post by voradeaur on 2012-01-06
Your problem is rather similar to that of my own... I can reboot the computer with about 10% chance of successful internet connection (also running 11.10.) Those that do not suffer this rather frequent failure (with the dialog box showing disconnected 7 times before quitting) doesnt seem to understand the horror this produces. Its a nicely laid out system I would love to use, however; given this problem... its not looking like a possible answer. I hope you get this figured out for both our sake.. lol

---

### Post by mvsrinivas on 2012-01-06
I installed Ubuntu 11.10 on my DELL laptop 2 days ago and I had no problem at all. The wireless detected my home Wifi network and connected as soon as I entered the KEY.

---

### Post by OwnSurname on 2012-01-06
Just to point out the obvious: everything works fine with the wireless, until it disconnects, and it can happen after many hours. Only once it disconnects, it's not able to connect again. Also, upon reboot, it always works fine until the next disconnection.

---

