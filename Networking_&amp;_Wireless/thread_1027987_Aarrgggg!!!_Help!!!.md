---
title: "Aarrgggg!!! Help!!!"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Baldrick_NZ on 2009-01-01
Someone please help me before this laptop's life is severely shortened!!!

I have Ubuntu 8.1 installed on an Acer Aspire 3002LC Laptop.

I also have installed an Asus L-107g PCMCIA card for wireless internet/networking.

The system works well when XP is booted, but I keep getting "Validating Authentication" pop up all the time using WICD in Ubuntu.

The linux drivers were crap (very slow speeds & signal strength) which seems to be a big issue in 8.1 going by the forums. So, I installed The program which allows a user to use native windows drivers on their PC. I know this has been installed because I now have a program called "Windows Wireless Drivers (WWD)" under System>Administration menu.

So, I download the latest XP drivers from the asus website and place them into my "Drivers" folder. I then open up the WWD utility and install the .ini file it requests for XP. It shows up immediately. I click to highlight the driver and then click to configure only to be greeted with the message "Could not find a network configuration tool". What the??!! 

I then restart the PC and then find WICD has logged be onto the internet using the card. Great! I then do a restart again to prove all is ok, and then get the "Validating Authentication" message in WICD. Lost all wireless.

The only way I can get internet back again is via ethernet.

As I said before, this does not happen under XP.

When the wireless does work with the XP driver under ubuntu, she's as fast as ethernet.

Here's my iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan2     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:24 Mb/s   Tx-Power:20 dBm   Sensitivity=-109 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Please help me, as I fear this computer's health & safety will be severely compromised!

By the way, I'm a bit of a newbie at this so please go gentle...

---

### Post by f37u5g0d on 2009-01-01
Don't be worried about your hardware.  Unfortunately this is somewhat typical of ubuntu and linux.  It sounds to me like you have two drivers battling for your wireless card.  One is ndiswrapper (your windows driver) and the other was probably assigned by ubuntu (which doesn't work or you wouldn't be trying other drivers).  Good luck and don't be afraid to experiment!

---

### Post by Baldrick_NZ on 2009-01-01
> **f37u5g0d said:**
> Don't be worried about your hardware.  Unfortunately this is somewhat typical of ubuntu and linux.  It sounds to me like you have two drivers battling for your wireless card.  One is ndiswrapper (your windows driver) and the other was probably assigned by ubuntu (which doesn't work or you wouldn't be trying other drivers).  Good luck and don't be afraid to experiment!

OK, thanks so much for your quick reply. 

If this is the case, how do I remove (or disable) the offending Ubuntu driver? Hopefully that's all it is...

---

### Post by Baldrick_NZ on 2009-01-02
Bump. Sorry don't mean to be impatient, need to be back on-line ASAP wirelessly... Please...

---

### Post by abn91c on 2009-01-02
check you router settings, the iwconfig sees you wireless card as wlan2 no SSID. you probably need the ssid to log in to the network also check the WPA key that is set up correctly

---

### Post by Baldrick_NZ on 2009-01-02
Thanks for your help.

OK, I've now checked the ssid settings inside the router and the password settings (many times). I've finally managed to connect wirelessly and this is the result I get using iwconfig, where XXX is my correct ssid as set up inside the router...
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     IEEE 802.11g  ESSID:"XXX"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1C:DF:16:71:48   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-109 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

I'm now about to do a re-boot, and if recent past experience is anything to go by, I'll loose wireless again and have to connect via ethernet.

I'll report back upon restart.

---

### Post by Baldrick_NZ on 2009-01-02
It connected that time after a restart!

However, I'm not convinced this will happen everytime I do a restart.

I think it would be prudent to at least check which drivers are assigned to the card. Because, if f37u5g0d is right, there will continue to be a conflict.

So how does one check, and if there are two drivers present, disable one?

Cheers.

In the meantime, I'll try another restart...

---

### Post by melojo on 2009-01-02
to list the modules that are loaded

```
lsmod
```

to keep one from loading add it to
/etc/modprobe.d/blacklist

---

### Post by Baldrick_NZ on 2009-01-02
It failed again! Arrrggghhh!

Here's the lsmod, Melojo..
```
baldrick@baldrick-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16904  1 
af_packet              25728  2 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ipv6                  263972  12 
ppdev                  15620  0 
powernow_k8            22148  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
ndiswrapper           196380  0 
pcmcia                 43052  0 
led_class              12164  0 
wmi                    14504  0 
evdev                  17696  8 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
psmouse                45200  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
serio_raw              13444  0 
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                 10624  0 
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket
battery                18436  0 
sis_agp                15232  0 
button                 14224  0 
soundcore              15328  1 snd
ac                     12292  0 
i2c_sis96x             12420  0 
amd64_agp              18184  1 
k8temp                 12416  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                42184  2 sis_agp,amd64_agp
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
i2c_core               31892  1 i2c_sis96x
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_sis               18436  2 
ata_generic            12932  0 
ohci_hcd               31888  0 
ehci_hcd               43276  0 
pata_acpi              12160  0 
sis900                 27904  0 
mii                    13440  1 sis900
usbcore               148848  4 ndiswrapper,ohci_hcd,ehci_hcd
libata                177312  3 pata_sis,ata_generic,pata_acpi
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  3 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
baldrick@baldrick-laptop:~$ 


```

Any ideas which one I should add to "/etc/modprobe.d/blacklist"? The chipset is RT2500 if that any help..

---

### Post by melojo on 2009-01-02
post the output of

```
lspci
```

---

### Post by Baldrick_NZ on 2009-01-02
Still no wireless on start up this morn. :-(

lspci as follows...```
baldrick@baldrick-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
02:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
baldrick@baldrick-laptop:~$ 

```
I really appreciate all the help. Thanks!

---

### Post by Baldrick_NZ on 2009-01-02
bump..

---

### Post by joukez on 2009-01-02
sudo gedit /etc/network/interfaces

See if the device is auto start

---

### Post by Baldrick_NZ on 2009-01-02
> **joukez said:**
> sudo gedit /etc/network/interfaces

See if the device is auto start

Comes up with...

auto lo
iface lo inet loopback

in text editor.

Is that any help?

---

### Post by melojo on 2009-01-02
> **Baldrick_NZ said:**
> It failed again! Arrrggghhh!

Here's the lsmod, Melojo..
```
baldrick@baldrick-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16904  1 
af_packet              25728  2 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ipv6                  263972  12 
ppdev                  15620  0 
powernow_k8            22148  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
ndiswrapper           196380  0 
pcmcia                 43052  0 
led_class              12164  0 
wmi                    14504  0 
evdev                  17696  8 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
psmouse                45200  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
serio_raw              13444  0 
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                 10624  0 
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket
battery                18436  0 
sis_agp                15232  0 
button                 14224  0 
soundcore              15328  1 snd
ac                     12292  0 
i2c_sis96x             12420  0 
amd64_agp              18184  1 
k8temp                 12416  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                42184  2 sis_agp,amd64_agp
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
i2c_core               31892  1 i2c_sis96x
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_sis               18436  2 
ata_generic            12932  0 
ohci_hcd               31888  0 
ehci_hcd               43276  0 
pata_acpi              12160  0 
sis900                 27904  0 
mii                    13440  1 sis900
usbcore               148848  4 ndiswrapper,ohci_hcd,ehci_hcd
libata                177312  3 pata_sis,ata_generic,pata_acpi
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  3 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
baldrick@baldrick-laptop:~$ 


```

Any ideas which one I should add to "/etc/modprobe.d/blacklist"? The chipset is RT2500 if that any help..

I don't see it loaded, the only thing I see for the card is ndiswrapper.
I don't know what to tell you.  maybe some one else can help!

---

### Post by Baldrick_NZ on 2009-01-02
Thanks for your help Melojo. 
Not so sure about that. When I issue the following "ndiwrapper l", I get this..

baldrick@baldrick-laptop:~$ ndiswrapper -l
rt2500 : driver installed
	device (1814:0201) present (alternate driver: rt2500pci)
baldrick@baldrick-laptop:~$ 

Which shows it's clearly installed, shown when I execute "lshw -C Network"

baldrick@baldrick-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:b0:fe:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.2.2 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan2
       version: 01
       serial: 00:1b:fc:e3:6c:1f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2500 driverversion=1.53+Ralink Technology, Inc.,07/ latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:76:fa:f4:fe:f1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
baldrick@baldrick-laptop:~$ 

Hopefully this will help someone out there resolve this very frustrating issue... I fear for the life of this PC - could be somewhat shortened!

---

### Post by Baldrick_NZ on 2009-01-02
Bump. Sorry, just need to get this resolved.. Pleeeeaaasssee...

---

### Post by melojo on 2009-01-02
the rt2500 is what ndiswrapper is loading

thats what ndiswrapper -l means
The l means list
thats the only module that is loaded there is not another rt2500 or you would see it in lsmod.

---

### Post by melojo on 2009-01-02
have you tried dissableing the security and see if that makes a difference, if so then it has something to do with the driver and security.

---

### Post by Baldrick_NZ on 2009-01-02
Well, it worked before and after a restart!

So the drivers must be ok then? 

Can you suggest what to look for next as I really don't want to have an unsecured internet connection. Was previously using WPA, will that no longer work for me?

Cheers.

---

### Post by melojo on 2009-01-02
I would try wep and see how that works.  That's better than none at all.

---

### Post by Baldrick_NZ on 2009-01-02
> **melojo said:**
> I would try wep and see how that works.  That's better than none at all.

Nope, same prob.

So, to summarise, using wicd I can only connect wirelessly with NO encryption. Using XP I can use WPA no prob at all. Ethernet access isn't a prob either way.

I have completely removed wicd having installed network manager in the meantime. Same there. I have installed a completely new copy of wicd, no change. I have factory reset the router and set it up correctly, and still no joy.

WTF???:mad::mad::mad:

I'm starting to see a compelling reason as to why people stick with windows. It works!

---

### Post by melojo on 2009-01-02
The trick to using linux as an os is to make sure that hardware is linux compatible.  If hardware manufacturers would make drivers for linux like they do for windows it would be no problem, so blame them.  Usually windows won't pick up some hardware thats why they provide drivers.  If you bought a system from dell or other company that has linux preinstalled just like windows it would not be a problem.  

So I guess what I am trying to say is its not linux fault and a lot of users don't have the problems that some have because they have linux friendly hardware.

You could try another flavor of linux like mandriva, suse, fedora, mint, there are many more.

my wirless doesn't work with network manager, so I had to uninstall and connect manually to get wep to work.  That is another option, it could be network manager. 

here is a link that i used to get my network up manually, of course this is not for your module bu the commands will still apply.
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

This was written by kevdog

[/quote]Unencrypted Connection

All commands typed at the command line:
Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

__________________________________________________ __________________________
WEP Connection

You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key.

Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

[/quote]

---

### Post by Baldrick_NZ on 2009-01-02
Thanks for the explanation. Tried network manager with the same result.

What's really annoying is that the 8.1 version was supposed to cure all wireless ills, yet going by the feedback & requests regarding wireless on this forum alone it appears that 8.1 has failed miserably, yet there has been no update (or service pack in windows speak) to resolve the issues.

On this one thing alone, 8.1 would have to be to Ubuntu what Vista is to Microsoft, a huge let down. 

Don't get me wrong, I love the concept of Ubuntu, if I didn't I wouldn't have stuck with it as long as I have. I just think for such a big issue to so many users, a patch or update would have been released to resolve the issue. Not make people wait another 6 months for a new release, that's how you loose people back to windows.

Sorry for the rant, I just feel completely frustrated that it takes so much to be resolved, yet there is more than enough history now for Ubuntu to release a fix.

Thanks again for your help, I'll stick with it for a while longer in the hope that a fix will come, so if someone can help I'd be truly grateful.

---

### Post by Favux on 2009-01-03
Hi Baldrick_NZ,

If you think your driver is OK, at least with no security, and you are still using NM, you might want to look at:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

---

