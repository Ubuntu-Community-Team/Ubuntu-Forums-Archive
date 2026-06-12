---
title: "Ubuntu 12.04 doesn't recognize wireless"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by jdhoskins on 2013-06-06
Thanks in advance to anyone that can help me fix this problem.  I'm installing Lubuntu 12.04 as a fresh install on a brand new machine.  I've gotten as far as getting it installed and getting the video drivers to work (they didn't out of the box).  My wired connection is working just fine (using it to write this now).  However, I can not, for the life of me, get the wireless card to work.  I've been trying to get this to work for a couple of days and don't know what else to do at this point.  Any help would be so greatly appreciated.  Also, I'm a complete noob as this is my first time working with any form of linux.  I've included output concerning the hardware in question below.  Thanks again.

lsb_release -d
```
Description:    Ubuntu 12.04 LTS
```



lspci -nn |grep 'Ralink'
```
[FONT=Verdana]01:00.0 Network controller [0280]: Ralink corp. Device [1814:3593][/FONT]
```

 $ iwconfig 
```
lo        no wireless extensions.


eth0      no wireless extensions. 
```

$ lsmod
```
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  1 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
joydev                 17693  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
usbhid                 47199  0 
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
hid                    99559  1 usbhid
uvcvideo               72627  0 
rt2x00pci              14577  1 rt2800pci
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
snd                    78855  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6           12725  1 rt2800pci
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  468651  3 
drm_kms_helper         46978  1 i915
mac_hid                13253  0 
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
rt2860sta             864748  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0
```

I also got this from lshw regarding the wireless card:

           ```
*-network UNCLAIMED
                description: Network controller
                product: Ralink corp.
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:fe900000-fe90ffff
```

---

### Post by Hadaka on 2013-06-06
Hi it looks like you have a conflicting
driver loaded...rt2860sta
the rt2800pci drivers  looks like it will work best for you.

hadaka@the-beach:~$ modinfo rt2800pci | grep 3593
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*

so lets bounce some stuff around and toss the rt2860 into the blackhole.
please do..
```
echo "blacklist rt2860sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv rt2860sta
sudo modprobe -rf rt2800pci
sudo modprobe rt2800pci
```
thanks.

---

### Post by jdhoskins on 2013-06-06
Thanks for your help Hadaka!  I've done what you said to do.  Should the wireless have started working or is there something else I need to do?

---

### Post by Hadaka on 2013-06-06
One can only hope.;)
Boot and report back good things.
thanks

---

### Post by jdhoskins on 2013-06-06
Oh well, still not working...

---

### Post by Hadaka on 2013-06-06
ok, well at least the keyboard didnt burst into flames..
lets rummage around and see whats going on.
please do,,
```
modprobe -v rt2800pci
dmesg | grep -i rt2800
lsmod
```
post the output
thanks.

---

### Post by jdhoskins on 2013-06-06
Well, i did almost set it on fire due to frustration but that's a different thing all together haha.

Here goes:

```
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
joydev                 17693  0 
parport_pc             32866  0 
bluetooth             180104  10 rfcomm,bnep
ppdev                  17113  0 
snd_hda_codec_realtek   223867  1 
nls_iso8859_1          12713  1 
snd_hda_intel          33773  1 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
nls_cp437              16991  1 
snd_hwdep              13668  1 snd_hda_codec
vfat                   17585  1 
fat                    61512  1 vfat
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
uvcvideo               72627  0 
snd_rawmidi            30748  1 snd_seq_midi
videodev               98259  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
usbhid                 47199  0 
hid                    99559  1 usbhid
snd                    78855  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6           12725  1 rt2800pci
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  468651  3 
mac_hid                13253  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
rt2860sta             864748  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0
```

---

### Post by Hadaka on 2013-06-06
where is the other outputs??
try again... one line at a time
please do..
```
sudo modprobe -rfv rt2860sta
sudo modprobe -v rt2800pci
dmesg | grep -i rt2800
```
post the output..each line..
and..mash the "#"  in the center row of your reply...look up
then post the output between the CODE brackets [.CODE] post here [./CODE]
called code tages...makes for eaiser reading..
thanks.

---

### Post by jdhoskins on 2013-06-06
Here ya go.. Sorry I didn't know how to do that before.  


```
sudo modprobe -rfv rt2860sta
[FONT=Verdana]rmmod /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt2860sta.ko[/FONT]
```

```
sudo modprobe -v rt2800pci
[FONT=Verdana]no output. Just returns to the command line,[/FONT]
```

```
dmesg | grep -i rt2800
[FONT=Verdana][ 12.034996] rt2800pci 0000:01:00.0: enabling device (0000 -> 0002)[/FONT]
[FONT=Verdana][ 12.035019] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/FONT]
[FONT=Verdana][ 12.035045] rt2800pci 0000:01:00.0: setting latency timer to 64[/FONT]
[FONT=Verdana][ 12.037037] phy0 -> rt2800_init_eeprom: Error - Invalid RT chipset detected.[/FONT]
[FONT=Verdana][ 12.037144] rt2800pci 0000:01:00.0: PCI INT A disabled[/FONT]
```

Hope this is better.

---

### Post by Hadaka on 2013-06-06
good job...thanks...ok lets keep looking.
click the icon next to the envelope...network mgr thing
see that "Enable Wireless" is checked
then. please do.
```
rfkill list
lsmod
cat /etc/modules
```
post the output.
thanks.

---

### Post by jdhoskins on 2013-06-06
I think maybe I don't have network manager.  I don't see it at all anywhere.

---

### Post by Hadaka on 2013-06-06
Do you have an up/down arrow looking thing next to the
envelope...upper right corner? If yes..click that and
see what it says.
thanks.

---

### Post by jdhoskins on 2013-06-06
I'm actually using Lubuntu for my desktop.  So, there's no envelope but shouldn't it be on the task bar if I have it?  Is it the app that says network connections and lets you edit network connections?  If that is it, there's no option for enable wireless only "Enable Networking".

---

### Post by jdhoskins on 2013-06-06
Here is what I get when I run the commands you asked me to run.

rfkill list
```
Returns to prompt with no output
```

lsmod
```
Module                  Size  Used by
joydev                 17693  0 
snd_hda_codec_realtek   223867  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_intel          33773  1 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
snd                    78855  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47199  0 
hid                    99559  1 usbhid
i915                  468651  2 
drm_kms_helper         46978  1 i915
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mac_hid                13253  0 
rt2860sta             864748  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 

```

cat /etc/modules
```
loop
lp
rtc
rt2860sta

```

---

### Post by Hadaka on 2013-06-06
lets see if we found it..
please do..
```
sudo modprobe -rf rt2860sta
```
this is where it was hideing...lets get it outta there
```
sudo gedit /etc/modules
```
backspace out rt2860sta...delete it
save and close gedit.
boot
then do,,
```
sudo modprobe rt2800pci
```
got wireless?

---

### Post by jdhoskins on 2013-06-06
Still no wireless.  Should I have gotten output after "sudo modprobe rt2800pci"?

---

### Post by Hadaka on 2013-06-06
Getting no output on that command is a good thing.
lets look at a couple more things and then possibly go
a different direction.
please post the output of..
```
lsmod
ifconfig
iwconfig
cat /etc/modprobe.d/blacklist.conf | grep blacklist
```
thanks.

---

### Post by jdhoskins on 2013-06-06
Sorry, I got pulled to another project at work.  I'll do this and post back ASAP when I get back to work!  Thanks a bunch!  I really appreciate your help!

---

### Post by jdhoskins on 2013-06-07
Goodmorning!  Here's the output from the commands you requested.


lsmod
```
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
joydev                 17693  0 
snd_hda_codec_realtek   223867  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_intel          33773  1 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
snd_seq_midi_event     14899  1 snd_seq_midi
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usbhid                 47199  0 
hid                    99559  1 usbhid
mac_hid                13253  0 
i915                  468651  2 
drm_kms_helper         46978  1 i915
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:18:7d:28:e8:8e  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:7dff:fe28:e88e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1244991 (1.2 MB)  TX bytes:142277 (142.2 KB)
          Interrupt:42 Base address:0xc000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35346 (35.3 KB)  TX bytes:35346 (35.3 KB)

```

iwconfig
```
lo        no wireless extensions.


eth0      no wireless extensions.

```

cat /etc/modprobe.d/blacklist.conf | grep blacklist
```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rt2860sta

```

---

### Post by Hadaka on 2013-06-07
Hi, lets see what happens when we use the
driver that we blacklisted. My good friend dr chilli555
has informed me that sometimes it works better with it.
please open a terminal ..ctrl/alt/t
and do..
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
insert this..
```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```
and be sure to remove this.
```
blacklist rt2860sta
```
save and close gedit
BOOT
then do..
```
sudo modprobe -rfv rt2800pci
sudo modprobe rt2860sta
```
then..
```
dmesg | grep rt2
```
cross your toes..

---

### Post by jdhoskins on 2013-06-10
OK, so, I just did all of that, rebooted and still no wireless.  Any ideas?

---

### Post by Hadaka on 2013-06-10
How frustrating ! ;)
ok..lets verify and rummage.
please do ..
```
sudo modprobe rt2860sta
dmesg | grep rt
```
then..verify
```
cat /etc/modprobe.d/blacklist.conf | grep blacklist
cat /etc/modules
```
thanks.

---

### Post by jdhoskins on 2013-06-10
Thanks!  Here it is!

sudo modprobe rt2860sta
```
No output

```

dmesg | grep rt
 ```
0.000000] KERNEL supported cpus:
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Checking aperture...
[    0.015368] mce: CPU supports 5 MCE banks
[    0.076004] smpboot cpu 1: start_ip = 99000
[    0.164356] smpboot cpu 2: start_ip = 99000
[    0.256294] smpboot cpu 3: start_ip = 99000
[    0.381134] ACPI: (supports S0 S1 S4 S5)
[    0.425616] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.427361] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.427530] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.427666] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.427815] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.428358] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.428835] pci 0000:00:1f.2: PME# supported from D3hot
[    0.429210] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.436414] pci 0000:02:00.0: supports D1 D2
[    0.436421] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.652846] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.652907] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.653104] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.653155] pcieport 0000:00:1c.5: irq 41 for MSI/MSI-X
[    0.653397] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.653448] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.659993] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.356630] Linux agpgart interface v0.103
[    1.356778] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.356921] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.357224] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.357489] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.521037] ehci_hcd 0000:00:1a.7: debug port 1
[    1.524927] ehci_hcd 0000:00:1a.7: cache line size of 4 is not supported
[    1.540028] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.540363] hub 1-0:1.0: 4 ports detected
[    1.540750] ehci_hcd 0000:00:1d.7: debug port 1
[    1.544642] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
[    1.560028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.560342] hub 2-0:1.0: 6 ports detected
[    1.561159] hub 3-0:1.0: 2 ports detected
[    1.561853] hub 4-0:1.0: 2 ports detected
[    1.562517] hub 5-0:1.0: 2 ports detected
[    1.563246] hub 6-0:1.0: 2 ports detected
[    1.563951] hub 7-0:1.0: 2 ports detected
[    1.564380] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.565713] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.566393] rtc_cmos 00:0a: RTC can wake from S4
[    1.566610] rtc_cmos 00:0a: rtc core: registered rtc_cmos as rtc0
[    1.566654] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.658870] rtc_cmos 00:0a: setting system clock to 2013-06-10 18:06:33 UTC (1370887593)
[    1.697240] sd 1:0:1:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.775653] udevd[99]: starting version 175
[    6.943716] udevd[356]: starting version 175
[    7.456426] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    7.456433] [drm] Driver supports precise vblank timestamp query.
[    7.923304] [drm] initialized overlay support
[    9.371476] ppdev: user-space parallel port driver
[   12.207700] init: plymouth-stop pre-start process (1218) terminated with status 1

```

cat /etc/modprobe.d/blacklist.conf | grep blacklist
```
no output

```

cat /etc/modules
```
no output

```

---

### Post by Hadaka on 2013-06-10
Hi, i think you forgot a space between cat and /etc
try again please..
copy and paste
```
cat /etc/modprobe.d/blacklist.conf | grep blacklist
cat /etc/modules
```
thanks.

---

### Post by jdhoskins on 2013-06-10
I also can't help but notice network manager doesn't show as many options as it should.  Here is a screenshot of what it looks like on my computer.  Does this look correct to you?  Seems to be missing a few things maybe.

---

### Post by jdhoskins on 2013-06-10
Oh yeah I gots output now!

```
cat /etc/modprobe.d/blacklist.conf | grep blacklist
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib

```



cat /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


loop
lp
rtc
rt2860sta
```

---

### Post by Hadaka on 2013-06-10
I have no idea what Lubuntu network manager is suppose to look like
your post is tagged Ubuntu..sooo..
Where did you get the rt2860sta driver, did you downoad it from a site?
please do ..
```
modinfo rt2860sta
```
thanks.

---

### Post by Hadaka on 2013-06-10
OK, lets go back with the rt2800pci driver..
This is like creating a fine wine, takes a little
time to get that just right blend.
open a terminal and do..
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
REMOVE..
```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```
ADD..INSERT
```
blacklist rt2860sta
```
SAVE and close gedit.
then..didnt think we were through did you?
open another terminal and do...
```
sudo gedit /etc/modules
```
REMOVE
```
rt2860sta
```
SAVE and close gedit
remove the ethernet cable and boot
thanks.

---

### Post by jdhoskins on 2013-06-11
I got the rt2860sta driver from the Ralink website.  Here is the modinfo for the rt2860sta

 modinfo rt2860sta
```
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt2860sta.ko
license:        GPL
version:        2.4.0.0
srcversion:     65223B8B7D9C2800C048813
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-23-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
```

---

### Post by jdhoskins on 2013-06-11
Did what you asked in your last post.  Still got nothing.

---

### Post by varunendra on 2013-06-11
@jdhoskins,

As per your last modinfo output, the compiled sta driver is clearly not meant for your card. Your card is -
> **jdhoskins said:**
> lspci -nn |grep 'Ralink'
```
01:00.0 Network controller [0280]: Ralink corp. Device [**[COLOR="#FF0000"]1814:3593[/COLOR]**]
```
And the above modinfo has no reference (alias) for it.

Soo... where did you find that gem ? :P
Please provide the link where you found the driver and/or the idea to install it. If it was a guide or blog, we may get an idea of whether there is something else you need to 'undo' to make the card work.

As of now you're better off trying the native driver for the card, or download and compile the correct driver for it.

Over to Hadaka again :)

---

### Post by jdhoskins on 2013-06-11
It was my understanding from the Ralink website that it was the correct driver.  Perhaps I misread though.  It definitely wouldn't be the first time.  I got the driver here [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501).  So I went back and looked again and I can't even find the 3593 listed.  I wonder if it is actually the 3592 since it's the closest thing they have listed on their site.  At this point, to be honest, I've read and tried so many things I can't remember where I got the info to install those drivers.  Do you think I should try the 3592 driver?

---

### Post by varunendra on 2013-06-11
> **jdhoskins said:**
> It was my understanding from the Ralink website that it was the correct driver.  Perhaps I misread though.  It definitely wouldn't be the first time.  I got the driver here [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501).  So I went back and looked again and I can't even find the 3593 listed.  I wonder if it is actually the 3592 since it's the closest thing they have listed on their site.  At this point, to be honest, I've read and tried so many things I can't remember where I got the info to install those drivers.  Do you think I should try the 3592 driver?

I already tried that driver here (just to make sure), as well as a few others I had doubts about.

Apparently they haven't yet provided the driver for it on their website, not even for windows. In fact, a linux driver doesn't exist for it as per this database : [http://wikidevi.com/wiki/Ralink_RT3593_Reference_Design](http://wikidevi.com/wiki/Ralink_RT3593_Reference_Design)

But we know that the native rt2800pci driver shows support for it. It means either the support is experimental or the above database is outdated (which is unlikely as it is dedicated to such info and is an active site).

The chip is not absolutely new, so it is possible that the support is included in some other driver that I haven't tested yet. I'll do some research and will post back accordingly.

---

### Post by jdhoskins on 2013-06-11
I just downloaded the DPO_RT3562_3592 etc... driver.  Opened the config.mk in /os/linux and found this:

ifeq ($(CHIPSET),3593)
WFLAGS +=-DRTMP_MAC_PCI -DDOT11N_SS3_SUPPORT -DNEW_RATE_ADAPT_SUPPORT -DRT3593 -DRT28xx -DRT30xx -DRT35xx -DRTMP_PCI_SUPPORT -DRTMP_RF_RW_SUPPORT -DRTMP_EFUSE_SUPPORT -DA_BAND_SUPPORT
CHIPSET_DAT = 2860
endif

Does this mean this driver should work for the 3593?

---

### Post by varunendra on 2013-06-11
> **jdhoskins said:**
> I just downloaded the DPO_RT3562_3592 etc... driver.  Opened the config.mk in /os/linux and found this:

ifeq ($(CHIPSET),3593)
WFLAGS +=-DRTMP_MAC_PCI -DDOT11N_SS3_SUPPORT -DNEW_RATE_ADAPT_SUPPORT -DRT3593 -DRT28xx -DRT30xx -DRT35xx -DRTMP_PCI_SUPPORT -DRTMP_RF_RW_SUPPORT -DRTMP_EFUSE_SUPPORT -DA_BAND_SUPPORT
CHIPSET_DAT = 2860
endif

Does this mean this driver should work for the 3593?
That's strange. I can confirm that line exists in the one I have downloaded as well, but I compiled it, checked modinfo and it didn't have an alias for 3593 (only 3592, like the name suggests).

But yes it does mean the support should be there. So try compiling it, then check with modinfo -
```
modinfo os/linux/rt3562sta.ko | grep 359
```
..from the directory where you run "make" to compile it.

---

### Post by jdhoskins on 2013-06-11
This is what I got.

```
pci:v00001814d00003592sv*sd*bc*sc*i*
```

---

### Post by Hadaka on 2013-06-11
Hi, lets see if that puppy will fly
unplug the wired connection and
dont boot
please do..
```
sudo modprobe -rfv rt2800pci
sudo modprobe -rfv rt2x00pci
sudo modprobe -v rt3562sta
dmesg | grep rt
```

---

### Post by jdhoskins on 2013-06-11
Unfortunately, still no wireless...but here's the output.

dmesg | grep rt
```

[    0.000000] KERNEL supported cpus:
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Checking aperture...
[    0.015477] mce: CPU supports 5 MCE banks
[    0.076004] smpboot cpu 1: start_ip = 99000
[    0.164356] smpboot cpu 2: start_ip = 99000
[    0.284296] smpboot cpu 3: start_ip = 99000
[    0.409127] ACPI: (supports S0 S1 S4 S5)
[    0.453614] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.455335] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.455499] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.455636] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.455786] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.456327] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.456805] pci 0000:00:1f.2: PME# supported from D3hot
[    0.457179] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.464415] pci 0000:02:00.0: supports D1 D2
[    0.464423] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.680865] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.680927] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.681114] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.681164] pcieport 0000:00:1c.5: irq 41 for MSI/MSI-X
[    0.681397] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.681454] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.688076] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.388591] Linux agpgart interface v0.103
[    1.388737] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.388880] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.389182] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.389445] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.553022] ehci_hcd 0000:00:1a.7: debug port 1
[    1.556909] ehci_hcd 0000:00:1a.7: cache line size of 4 is not supported
[    1.572029] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.572356] hub 1-0:1.0: 4 ports detected
[    1.572743] ehci_hcd 0000:00:1d.7: debug port 1
[    1.576624] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
[    1.592028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.592338] hub 2-0:1.0: 6 ports detected
[    1.593137] hub 3-0:1.0: 2 ports detected
[    1.593846] hub 4-0:1.0: 2 ports detected
[    1.594513] hub 5-0:1.0: 2 ports detected
[    1.595257] hub 6-0:1.0: 2 ports detected
[    1.595956] hub 7-0:1.0: 2 ports detected
[    1.596395] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.597313] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.597986] rtc_cmos 00:0a: RTC can wake from S4
[    1.598205] rtc_cmos 00:0a: rtc core: registered rtc_cmos as rtc0
[    1.598248] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.691578] rtc_cmos 00:0a: setting system clock to 2013-06-11 13:25:58 UTC (1370957158)
[    1.729245] sd 1:0:1:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.807499] udevd[99]: starting version 175
[    7.906864] udevd[346]: starting version 175
[    8.011124] rt3562sta: module license 'unspecified' taints kernel.
[    8.330332] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.330338] [drm] Driver supports precise vblank timestamp query.
[    8.744365] [drm] initialized overlay support
[    8.975958] ppdev: user-space parallel port driver
[   10.715381] init: plymouth-stop pre-start process (1206) terminated with status 1

```

---

### Post by Hadaka on 2013-06-11
please post the output of.
```
lsmod
cat /etc/modules
```
then blacklist the rt2800 & rt2x00 like you did
in post 20
thanks.

---

### Post by jdhoskins on 2013-06-11
One thing I noticed is there were some errors when doing the make for the rt3562 driver.  Not sure if that makes a difference or not...

lsmod
```

Module                  Size  Used by
joydev                 17693  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
snd_hda_codec_realtek   223867  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_intel          33773  1 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd                    78855  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  468651  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mac_hid                13253  0 
rt3562sta             990799  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 

```


cat /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


loop
lp
rtc
rt3562sta

```

---

### Post by Hadaka on 2013-06-11
ok, lets see if there is any error messages
please do ..
```
sudo modprobe -rf rt3562sta
sudo modprobe -v rt3562sta
dmesg | grep rt
```

---

### Post by jdhoskins on 2013-06-11
OK here's what was returned.

 sudo modprobe -rf rt3562sta 
No output at all.  A good thing?

sudo modprobe -v rt3562sta
```
insmod /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt3562sta.ko

```
dmesg | grep rt
```
[    0.000000] KERNEL supported cpus:
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Checking aperture...
[    0.015477] mce: CPU supports 5 MCE banks
[    0.076004] smpboot cpu 1: start_ip = 99000
[    0.164356] smpboot cpu 2: start_ip = 99000
[    0.284296] smpboot cpu 3: start_ip = 99000
[    0.409127] ACPI: (supports S0 S1 S4 S5)
[    0.453614] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.455335] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.455499] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.455636] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.455786] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.456327] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.456805] pci 0000:00:1f.2: PME# supported from D3hot
[    0.457179] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.464415] pci 0000:02:00.0: supports D1 D2
[    0.464423] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.680865] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.680927] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.681114] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.681164] pcieport 0000:00:1c.5: irq 41 for MSI/MSI-X
[    0.681397] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.681454] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.688076] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.388591] Linux agpgart interface v0.103
[    1.388737] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.388880] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.389182] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.389445] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.553022] ehci_hcd 0000:00:1a.7: debug port 1
[    1.556909] ehci_hcd 0000:00:1a.7: cache line size of 4 is not supported
[    1.572029] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.572356] hub 1-0:1.0: 4 ports detected
[    1.572743] ehci_hcd 0000:00:1d.7: debug port 1
[    1.576624] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
[    1.592028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.592338] hub 2-0:1.0: 6 ports detected
[    1.593137] hub 3-0:1.0: 2 ports detected
[    1.593846] hub 4-0:1.0: 2 ports detected
[    1.594513] hub 5-0:1.0: 2 ports detected
[    1.595257] hub 6-0:1.0: 2 ports detected
[    1.595956] hub 7-0:1.0: 2 ports detected
[    1.596395] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.597313] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.597986] rtc_cmos 00:0a: RTC can wake from S4
[    1.598205] rtc_cmos 00:0a: rtc core: registered rtc_cmos as rtc0
[    1.598248] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.691578] rtc_cmos 00:0a: setting system clock to 2013-06-11 13:25:58 UTC (1370957158)
[    1.729245] sd 1:0:1:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.807499] udevd[99]: starting version 175
[    7.906864] udevd[346]: starting version 175
[    8.011124] rt3562sta: module license 'unspecified' taints kernel.
[    8.330332] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.330338] [drm] Driver supports precise vblank timestamp query.
[    8.744365] [drm] initialized overlay support
[    8.975958] ppdev: user-space parallel port driver
[   10.715381] init: plymouth-stop pre-start process (1206) terminated with status 1
```

---

### Post by Hadaka on 2013-06-11
ok, i found a thread with a like issue...
please do..
```

cat /etc/Wireless/RT2860STA/RT2860STA.dat
```
thanks.

---

### Post by jdhoskins on 2013-06-11
OK here's what it looks like...

```
cat /etc/Wireless/RT2860STA/RT2860STA.dat#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
FtSupport=0
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
PSP_XLINK_MODE=0
WscManufacturer=
WscModelName=
WscDeviceName=
WscModelNumber=
WscSerialNumber=
RadioOn=1
```

---

### Post by Hadaka on 2013-06-11
ok, dr chili555 informs me he doubts this dirver is going to work.
so..if you are willing..lets undo all the stuff.
please do.
```
sudo gedit /etc/modules
```
REMOVE 
```
rt3562sta
```
save and close gedit
then do..
```
gedit /etc/modprobe.d/blacklist.conf
```
REMOVE
```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```
ADD..insert
```
blacklist rt3562sta
```
save and close gedit
boot
unplug the ethernet
then do..
```
sudo modprobe -rfv rt3562sta
sudo modprobe -rf rt2800pci
sudo modprobe -v rt2800pci
```
then do..
```
dmesg
```
copy and paste the output of dmesg to -> [http://paste.ubuntu.com](http://paste.ubuntu.com)
then post back the pastebin file here
thanks.

---

### Post by jdhoskins on 2013-06-11
That was a long one!

[http://paste.ubuntu.com/5755452/](http://paste.ubuntu.com/5755452/)

---

### Post by Hadaka on 2013-06-11
Thanks, lets look at a couple things
please do..
```
modinfo rt2800pci | grep 3593
lsmod
cat etc/network/interfaces
cat /etc/modules
```
post the output
thanks.

---

### Post by jdhoskins on 2013-06-11
Thanks again for all your help and time!

modinfo rt2800pci | grep 3593 
```
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*

```

lsmod
```
Module                  Size  Used byrt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
joydev                 17693  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
bnep                   18281  2 
rfcomm                 47604  0 
snd_hda_codec_realtek   223867  1 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_intel          33773  1 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  468651  3 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
```


cat etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
#NetworkManager#iface eth0 inet dhcp

```

cat /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


loop
lp

```

---

### Post by Hadaka on 2013-06-11
ok, lets get rid of a file that got created when you loaded
the first downloaded driver. Please COPY and paste.
```
sudo cp /etc/Wireless/RT2860STA/RT2860STA.dat /etc/Wireless/RT2860STA/RT2860STA.old 
```
then..
```
sudo rm -r /etc/Wireless/RT2860STA/RT2860STA.dat
```
then..
ethernet cable unpluged
```
sudo modprobe -rf rt2800pci
sudo modprobe -v rt2800pci
dmesg | grep rt2
```
post the results

---

### Post by jdhoskins on 2013-06-11
sudo modprobe -v rt2800pci
```
insmod /lib/modules/3.2.0-23-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.2.0-23-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-23-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.2.0-23-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
insmod /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko

```



dmesg | grep rt2
```
[    8.267155] rt2800pci 0000:01:00.0: enabling device (0000 -> 0002)
[    8.267177] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.267204] rt2800pci 0000:01:00.0: setting latency timer to 64
[    8.269179] phy0 -> rt2800_init_eeprom: Error - Invalid RT chipset detected.
[    8.269194] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[    8.269274] rt2800pci 0000:01:00.0: PCI INT A disabled
[  173.715392] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  173.715414] rt2800pci 0000:01:00.0: setting latency timer to 64
[  173.717347] phy0 -> rt2800_init_eeprom: Error - Invalid RT chipset detected.
[  173.717355] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[  173.717397] rt2800pci 0000:01:00.0: PCI INT A disabled
[ 4938.921292] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4938.921323] rt2800pci 0000:01:00.0: setting latency timer to 64
[ 4938.923278] phy0 -> rt2800_init_eeprom: Error - Invalid RT chipset detected.
[ 4938.923289] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[ 4938.923349] rt2800pci 0000:01:00.0: PCI INT A disabled

```

---

### Post by Hadaka on 2013-06-11
this is telling us the driver we are trying to load is
bumping heads with another driver..
```
[    8.269179] phy0 -> rt2800_init_eeprom: Error - Invalid RT chipset detected.
 [    8.269194] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device
```

please do..
```
cat /etc/modules
lsmod
```

---

### Post by jdhoskins on 2013-06-11
I thought we got rid of all of the offending drivers.  Maybe one is sneaking in somewhere.


```
cat /etc/modulesloop
lp
rtc
```

```
smodModule                  Size  Used by
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
joydev                 17693  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
bnep                   18281  2 
rfcomm                 47604  0 
snd_hda_codec_realtek   223867  1 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_intel          33773  1 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  468651  3 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 
```

---

### Post by Hadaka on 2013-06-11
I noticed a rt2860.bin for firmware in the modinfo for rt2800pci
so lets put that file we took out back..
please do..COPY and  paste please
```
sudo mv /etc/Wireless/RT2860STA/RT2860STA.old /etc/Wireless/RT2860STA/RT2860STA.dat
```
and just for good measure
```
sudo apt-get update
sudo apt-get upgrade
```
thanks.

---

### Post by Hadaka on 2013-06-11
After you have done your updates..
```
sudo apt-get update
sudo apt-get upgrade
```
please post the output of..
```
uname -r
```
thanks.

---

### Post by jdhoskins on 2013-06-12
Good morning!  updated and upgraded.  3.2.0-23-generic.

---

### Post by Hadaka on 2013-06-12
Hi,please do..
```

sudo apt-get install linux-backports-modules-cw-3.3-precise-generic
```
reboot then do..
```
dmesg | grep rt2
```
post the results.
thanks

---

### Post by jdhoskins on 2013-06-12
Now uname -r gives 3.2.0-45-generic

```

dmesg | grep rt
[    0.000000] KERNEL supported cpus:
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Checking aperture...
[    0.015622] mce: CPU supports 5 MCE banks
[    0.076004] smpboot cpu 1: start_ip = 99000
[    0.164357] smpboot cpu 2: start_ip = 99000
[    0.256292] smpboot cpu 3: start_ip = 99000
[    0.380393] ACPI: (supports S0 S1 S4 S5)
[    0.423562] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.425345] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.425504] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.425637] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.425779] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.426270] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.426738] pci 0000:00:1f.2: PME# supported from D3hot
[    0.427104] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.432403] pci 0000:02:00.0: supports D1 D2
[    0.432412] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.640046] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.640116] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.640334] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.640383] pcieport 0000:00:1c.5: irq 41 for MSI/MSI-X
[    0.640626] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.640677] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.648653] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.296593] Linux agpgart interface v0.103
[    1.296750] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.296891] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.297178] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.297434] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.460981] ehci_hcd 0000:00:1a.7: debug port 1
[    1.464856] ehci_hcd 0000:00:1a.7: cache line size of 4 is not supported
[    1.480028] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.480362] hub 1-0:1.0: 4 ports detected
[    1.480753] ehci_hcd 0000:00:1d.7: debug port 1
[    1.484632] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
[    1.500028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.500354] hub 2-0:1.0: 6 ports detected
[    1.501180] hub 3-0:1.0: 2 ports detected
[    1.501881] hub 4-0:1.0: 2 ports detected
[    1.502574] hub 5-0:1.0: 2 ports detected
[    1.503280] hub 6-0:1.0: 2 ports detected
[    1.503982] hub 7-0:1.0: 2 ports detected
[    1.504412] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.506060] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.506764] rtc_cmos 00:0a: RTC can wake from S4
[    1.506982] rtc_cmos 00:0a: rtc core: registered rtc_cmos as rtc0
[    1.507026] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.603441] rtc_cmos 00:0a: setting system clock to 2013-06-12 13:18:53 UTC (1371043133)
[    1.637207] sd 1:0:1:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.714962] udevd[99]: starting version 175
[    2.320862] USB Mass Storage support registered.
[   10.156513] udevd[334]: starting version 175
[   10.563740] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.563746] [drm] Driver supports precise vblank timestamp query.
[   10.950475] [drm] initialized overlay support
[   11.170298] ppdev: user-space parallel port driver
[   13.729584] init: plymouth-stop pre-start process (1169) terminated with status 1
```

---

### Post by Hadaka on 2013-06-12
ok, please do..
```
sudo modprobe -rf rt2800pci
sudo modprobe -v rt2800pci
```
then again
```
dmesg | grep rt2
```
thanks.

---

### Post by jdhoskins on 2013-06-12
Here ya go!

```
dmesg | grep rt[    0.000000] KERNEL supported cpus:
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Checking aperture...
[    0.015400] mce: CPU supports 5 MCE banks
[    0.076004] smpboot cpu 1: start_ip = 99000
[    0.164357] smpboot cpu 2: start_ip = 99000
[    0.256291] smpboot cpu 3: start_ip = 99000
[    0.381043] ACPI: (supports S0 S1 S4 S5)
[    0.424193] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.425922] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.426086] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.426219] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.426358] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.426851] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.427320] pci 0000:00:1f.2: PME# supported from D3hot
[    0.427681] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.432397] pci 0000:02:00.0: supports D1 D2
[    0.432404] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.639913] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.639974] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.640235] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.640285] pcieport 0000:00:1c.5: irq 41 for MSI/MSI-X
[    0.640523] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.640574] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.648662] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.292588] Linux agpgart interface v0.103
[    1.292743] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.292884] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.293168] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.293417] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.456977] ehci_hcd 0000:00:1a.7: debug port 1
[    1.460860] ehci_hcd 0000:00:1a.7: cache line size of 4 is not supported
[    1.476028] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.476362] hub 1-0:1.0: 4 ports detected
[    1.476749] ehci_hcd 0000:00:1d.7: debug port 1
[    1.480636] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
[    1.496027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.496358] hub 2-0:1.0: 6 ports detected
[    1.497183] hub 3-0:1.0: 2 ports detected
[    1.497885] hub 4-0:1.0: 2 ports detected
[    1.498578] hub 5-0:1.0: 2 ports detected
[    1.499277] hub 6-0:1.0: 2 ports detected
[    1.499974] hub 7-0:1.0: 2 ports detected
[    1.500402] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.501895] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.502600] rtc_cmos 00:0a: RTC can wake from S4
[    1.502818] rtc_cmos 00:0a: rtc core: registered rtc_cmos as rtc0
[    1.502862] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.599832] rtc_cmos 00:0a: setting system clock to 2013-06-12 13:42:08 UTC (1371044528)
[    1.633209] sd 1:0:1:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.711278] udevd[99]: starting version 175
[   10.195891] udevd[342]: starting version 175
[   10.674027] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.674033] [drm] Driver supports precise vblank timestamp query.
[   11.073392] [drm] initialized overlay support
[   11.208139] ppdev: user-space parallel port driver
[   13.380289] init: plymouth-stop pre-start process (1256) terminated with status 1
[  772.095182] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  772.156586] rt2800pci 0000:01:00.0: enabling device (0000 -> 0002)
[  772.156612] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  772.156639] rt2800pci 0000:01:00.0: setting latency timer to 64
[  772.158614] phy0 -> rt2800_init_eeprom: Error - Invalid RT chipset detected.
[  772.158624] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[  772.158673] rt2800pci 0000:01:00.0: PCI INT A disabled
```

---

### Post by jdhoskins on 2013-06-13
I noticed when I did the make for the Linux driver provided by RaLink on their website, I got an error that said something to the effect of "module license taints kernel".  I did some research and it seems this is a problem where they have left "MODULE_LICENSE("GPL")  out of the code somewhere.  I wonder if this would cause problems.  I also noticed in the readme file of said driver that it is was tested with the Linux 2.4 and 2.6 Kernels but there no mention of newer kernels.

---

### Post by Hadaka on 2013-06-13
Hi, I spent several hours researching your card.

[FONT=Verdana]Ralink corp. Device [1814:3593]

seems you lucked out and have a device that has drivers for windows
but not linux. One refrence stated that the card was included in the
rt2800pci driver. Thus far we have failed to get the rt2800pci driver
to work.The first driver you compiled 2860? I found in a post along
with instructions to mod other files, If this is by chance what you did
this may be why the rt2800pci still fails to load correctly. Were it me
that was having these issues i would do one of 2 things,both a pain
1.reload Ubuntu 12.04 along with all the updates so i would know i had
  a clean os and then attempt to get the card working with the rt2800pci driver
2. Get out the hacksaw,vicegrips and hammer and change out the wireless card
   with a known 100% linux supported card for your computer.
3 of 2 things... I would probably do both of the above so i knew i had a clean install
for my new card.
I am sorry I was unable to help you.
[/FONT]

---

### Post by jdhoskins on 2013-06-13
I'm not surprised at all to be honest.  I tried to get the rt2800pci to work before I tried the 2860.  DIdn't mod any files though, just compiled and installed it as the instructions said.  Nothing fancy since I don't know anything fancy.  Regardless of whether it works or not I sincerely appreciate the time you put into helping.  Have a great day!

---

### Post by varunendra on 2013-06-15
I know I am late to respond, but thought I should add the info that I gathered after doing some more research after my last post. Just for the sake of adding info on the issue, not really something that I'm very hopeful about.

As is evident now, the Ralink site ([http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)) doesn't have any dedicated drivers to offer for this particular chip (RT3593). I tried compiling and checking all the drivers *(including some USB ones that I found being referenced to it)* that seemed relevant. None have the support for this chip after being compiled (as can be verified by "modinfo" command).

Bottomline - we don't seem to have readymade support for this chip from any of the proprietary driverd as of now (June 15, 2013), I wish and hope somebody can prove me wrong, but... (read on)..

As per this Linux driver database site, a Linux driver for this chip doesn't even exist : [http://wikidevi.com/wiki/Ralink_RT3593_Reference_Design](http://wikidevi.com/wiki/Ralink_RT3593_Reference_Design)
Although we have clearly seen an alias in the native rt2800pci driver. So I was thinking may be this database is just outdated..
Besides this chip is in the market since 2010 !

So then I went to linuxwireless.org , looked up rt2800pci and found this : [http://wireless.kernel.org/en/users/Drivers/rt2800pci?highlight=%28rt2800pci%29#Unsupported_chips](http://wireless.kernel.org/en/users/Drivers/rt2800pci?highlight=%28rt2800pci%29#Unsupported_chips)
> **Unsupported chips**
RF3053/**[COLOR="#FF0000"]RT3593[/COLOR]**, 802.11a/b/g/n 3T3R 450 Mbps 2.4/5 GHz PCI Express Single Chip.
This is a site that I trust the most (but is definitely not the end of world, so I kept looking on...)

Interestingly enough, even though the chip is in the market since 2010, there is very little information on it on the net. I couldn't find any case suggesting it could work on Linux, only a very few problem posts, bug reports etc with no solution or anything significant. Only because of the fact that how long it has been in the market, I was (to some extent still am) still hopeful.

However, since I have seen this error message in jdhoskins' dmesg outputs -
> **jdhoskins said:**
> ```
dmesg | grep rt
....
[  772.158614] phy0 -> **[COLOR="#FF0000"]rt2800_init_eeprom[/COLOR]**: Error -**[COLOR="#FF0000"] Invalid RT chipset detected[/COLOR]**.
[  772.158624] phy0 -> **[COLOR="#FF0000"]rt2x00lib[/COLOR]**_probe_dev: Error - **[COLOR="#FF0000"]Failed to allocate device[/COLOR]**.
```
..I have almost lost hope with the native **rt2800pci** driver also.
My own interpretation *(which can be wrong, I wish it is..)* of the above error message is that it is a way for the rt2800pci driver to say that - "I'm not meant for this particular chip. I'm not going to work with it, period."

If so, I wonder then what that alias for it is doing in its modinfo :-k

**The only link that gives me some hope is an archlinux custom package** that seems to specifically address this chip : [https://aur.archlinux.org/packages/rt3593/](https://aur.archlinux.org/packages/rt3593/)

I have never used archlinux myself and so I have no idea how its package system works. Analysing the package detail files and included package *(it is a hidden .tar.gz package, same one as downloaded from Ralink site)* suggest that it is nothing but some patches and modifications applied to **RT3573 USB** driver downloaded from mediatek site.

I tried to manually do everything that the PKGBuild file in the package seems to do *(it is basically the package handling and installation instructions set for archlinux package manager)*. That is, I did all the renames, string changes, applied patches etc. The driver compiled fine, but the modinfo returned same old output with no alias to 3593. :(

Now I'm wondering maybe archlinux package manager has some way of further affecting the compilation process or 'force-bind' the compiled driver with a chip ID based on the info included in the PKGBuild file. I have no way to try archlinux on my laptop, partly because I don't have enough time right now and mainly because I'm already out of space on my hdd. So, **jdhoskins**, maybe you can try posting your issue on archlinux forums with reference to this package and asking if someone there can kindly try compiling it and (/or otherwise) confirm if it really supports rt3593 after being installed *(output of modinfo or if there is some other way to confirm that)*.

Whoever (mentioned in the first line of the PKGBuild file, with email address) has created that package seems to have specifically targeted this chip, that's what makes me most hopeful. So if you haven't already given up, I'd suggest to try your luck on archlinux forums and let us know how it goes. I think you can also try directly emailing the person who created that package.

In any case, I'm just stumped on how such an old chip can still be so troublesome.

---

### Post by jdhoskins on 2013-06-17
Checking this out right now Varun!  I appreciate you spending so much time looking for a solution and hope to find something that works.  I've definitely not completely given up...

---

### Post by varunendra on 2013-06-17
> **jdhoskins said:**
> Checking this out right now Varun!  I appreciate you spending so much time looking for a solution and hope to find something that works.  I've definitely not completely given up...

It's fun! :)

I just read a post mentioning something about 'manually adding an ID (alias in modinfo) before compiling'. That's exactly what I was looking for with the suggested archlinux package, but got lost in other things.

If time allows, I may try to read more on it and see if I can do that. It will force the driver to recognize the device and get loaded for it.

Like you noticed in the rt3592 driver source, there are instances of 3593 in the code of several drivers, but the finally compiled drivers don't include that ID. This (if possible) can be a way to at least make it load for the card. However, it will only work if the driver is already capable of handling the device.

I hope to get enough time to concentrate on it soon. If I did, I'll post back if found something significant. Can't promise anything though.

---

### Post by jdhoskins on 2013-06-17
It seems like I recall reading something about doing that as well but I've read so much at this point, in such a small period of time that I can't be sure.  I'll also see what I can find regarding that subject as well!

---

### Post by jdhoskins on 2013-06-17
So I emailed the person that created the patch to see if it would also work in Ubuntu and he said he didn't see why not.  So I'd like to at least give it a try and see what happens.  I certainly can't hurt anything because it isn't working already...just gotta figure out how to get started.

---

### Post by varunendra on 2013-06-17
> **jdhoskins said:**
> So I emailed the person that created the patch to see if it would also work in Ubuntu and he said he didn't see why not.  So I'd like to at least give it a try and see what happens.  I certainly can't hurt anything because it isn't working already...just gotta figure out how to get started.

After compiling, I checked its modinfo. There was no 'alias' for 3593 in it. What it tells me is that it won't recognize the device "Ralink corp. Device [1814:**3593**]" therefore. You can ask him to confirm whether it is supposed to include that ID in its supported device list (modinfo output) or not. If not, then how is it going to bind with it?

---

### Post by chili555 on 2013-06-17
> **varunendra said:**
> After compiling, I checked its modinfo. There was no 'alias' for 3593 in it. What it tells me is that it won't recognize the device "Ralink corp. Device [1814:**3593**]" therefore. You can ask him to confirm whether it is supposed to include that ID in its supported device list (modinfo output) or not. If not, then how is it going to bind with it?Please check PM, Varun.

---

### Post by jdhoskins on 2013-06-17
So here is the reply I got when I asked if this was intended for the Ralink rt3593 card.  "Hi, yes, it is. No references because it actually uses the driver for the previous 3573 version. There are no linux version for 3593 chip at all.
So basically we're simply adding our device to the supported devices list:
+	{USB_DEVICE(0x13B1,0x003B)}, /* Cisco LinkSys AE3000 */ (in rtusb_dev_id.patch)
 
All the other patches are only bugfixes, to allow this driver to work with new kernels, to rename network name to wlan0, etc"

---

### Post by varunendra on 2013-06-17
> **chili555 said:**
> Please check PM, Varun.
I'm on it sir.
I'm super happy to see you are interested :D

> **jdhoskins said:**
> No references because it actually uses the driver for the previous 3573 version. There are no linux version for 3593 chip at all.
So basically we're simply adding our device to the supported devices list:
+	{USB_DEVICE(0x13B1,0x003B)}, /* Cisco LinkSys AE3000 */ (in rtusb_dev_id.patch)
 
All the other patches are only bugfixes, to allow this driver to work with new kernels, to rename network name to wlan0, etc"

Hmm.. that "{USB_DEVICE(0x13B1,0x003B)}" part may be the key. Let me know if you need help with applying the patches/changes manually.

I am working on making it easier anyway. Will post back soon I hope.

---

### Post by jdhoskins on 2013-06-17
To be honest, I'm not really sure how to start on this one.

---

### Post by varunendra on 2013-06-17
> **jdhoskins said:**
> To be honest, I'm not really sure how to start on this one.

Just wait then till I post back the complete steps with an automation script. I already have a dirty way to do that, just trying to make it cleaner (at the moment, learning advanced usage of 'patch' command to fit the existing patches).

---

### Post by jdhoskins on 2013-06-17
That sounds great!

---

### Post by chili555 on 2013-06-17
> **jdhoskins said:**
> So here is the reply I got when I asked if this was intended for the Ralink rt3593 card.  "Hi, yes, it is. No references because it actually uses the driver for the previous 3573 version. There are no linux version for 3593 chip at all.
So basically we're simply adding our device to the supported devices list:
+	{USB_DEVICE(0x13B1,0x003B)}, /* Cisco LinkSys AE3000 */ (in rtusb_dev_id.patch)
 
All the other patches are only bugfixes, to allow this driver to work with new kernels, to rename network name to wlan0, etc"I would suggest you also add:```
+	{USB_DEVICE(0x[COLOR="#FF0000"]1814[/COLOR],0x[COLOR="#FF0000"]3593[/COLOR])}, /* Ralink Whatever */ 
```...to rtusb_dev_id.c.

---

### Post by jdhoskins on 2013-06-18
Thanks Chili but I have no idea how to even get started on this.  I'm not sure what to do with the patches or even what I should do first.  Do I install the driver and then run the patches?  If so, how does one install the patches?  There's a file called rt3593.install.  Do I need to run that file?  If so, how do I go about doing that?

---

### Post by chili555 on 2013-06-18
@zalta1990--

I believe the exact way to get this going is still, so far, unknown. Please continue to follow this thread.

@jdhoskins--

I beiieve Varun is trying to work that out now. Please stand by.

---

### Post by varunendra on 2013-06-18
> **chili555 said:**
> I beiieve Varun is trying to work that out now. Please stand by.

Almost done.

Just going to try the package in a VM (have to make some room for it too :(), then will post back with instructions.

One thing that still doesn't look good is that the device in question is a PCI one, while we are defining the modalias as USB.

I got a very useful link from our friend Hadaka about this : [https://wiki.archlinux.org/index.php/Modalias](https://wiki.archlinux.org/index.php/Modalias) , but that does not make it clear (or I didn't read it thoroughly) whether this difference can be ignored or not.

When trying to define the modalias as "PCI_DEVICE", I get errors during compilation. So, for now, I've just left it as USB_DEVICE, which works.

So.. *(due to space crisis on my hdd and my world-class snail-speed)* it may take me a couple more hours to post back the links and instructions for building what I could manage so far.

I am ready and willing to work on it further as and if required.

---

### Post by jdhoskins on 2013-06-18
Varun,

---

### Post by jdhoskins on 2013-06-18
Varun, thanks so much for everything you're doing to help with this!  Also, I do really appreciate the update as well.

---

### Post by varunendra on 2013-06-18
> **jdhoskins said:**
> Varun, thanks so much for everything you're doing to help with this!  Also, I do really appreciate the update as well.
No problem! :) Like I said, it's fun, and I am learning a lot in the process..

So, I'm back with the experimental stuff now.

It is Highly Recommended to examine all the custom files, especially the installation script (**install_rt3593.sh**), that you will be downloading in the second step below to make sure they are safe.
**[COLOR="#FF0000"]Never trust a script or custom package from an unknown or un-verified source[/COLOR]**.
*[COLOR="#808080"](wow! Feels like the "Smoking is injurious to health" warning.. :P)[/COLOR]*

**[SIZE=3]_The steps to compile and install_ :[/SIZE]**

[indent]
**1)** Make sure the necessary packages for compiling packages are installed on your system :
```
sudo apt-get install linux-headers-generic build-essential
```

**2)** Download the patch package *[COLOR="#808080"](it's from my brand new dropbox account by the way, Yay!!)[/COLOR]*:
```
wget -N -t 4 -T 10 "https://dl.dropbox.com/s/jyhujntwgc9x5i6/rt3593_patch.tar.bz2"
```

**3)** Extract the included folder to Desktop (keep the terminal open after this) :
```
tar xjf rt3593_patch.tar.bz2 -C ~/Desktop
```

**4)** Download the "RT3573 USB" driver from Ralink's official download site : [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5034](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5034)

**5)** Copy the downloaded Ralink driver package *(20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO.tar.bz2)* into the "rt3593_patch" directory on the Desktop.

**6)** In the terminal, change to the "rt3593_patch" directory on the Desktop :
```
cd ~/Desktop/rt3593_patch
```

**7)** Run the installation script that I have created to automate the patching and installation process :
```
sudo ./install_rt3593.sh
```

**8)** After building the driver, the script will prompt you to install the driver. Just press 'Enter' to accept (or change '**Y**' to '**N**' if you are only testing it, and don't want to install).

**9)** After finishing, check if the driver was loaded and attached with your card -
```
lspci -nnk | grep -iA2 net
lsmod | grep rt3
```
[/indent]

Post back the result of the last step (9). Let's see if it can prove to be a solution, even if with some extra efforts.

**PS:**
Due to modification in the "rtusb_dev_id.patch" file (addition of 3593 ID), its md5sum won't match with the provided one in case you wish to verify it. I'll address this and some other things if this seems worth the effort.

---

### Post by jdhoskins on 2013-06-18
Gonna go give this a try!  I'll post back soon!

---

### Post by jdhoskins on 2013-06-18
OK...so it didn't work.  Still no wireless.  Is there anything you'd like for me to look for or print?

```
 lspci -nnk | grep -iA2 net01:00.0 Network controller [0280]: Ralink corp. Device [1814:3593]
        Subsystem: Ralink corp. Device [1814:3593]
        Kernel modules: rt2800pci
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
        Kernel driver in use: r8169
```

```
lsmod | grep rt3
rt3573sta             720974  0
```

---

### Post by varunendra on 2013-06-18
> **jdhoskins said:**
> OK...so it didn't work.  Still no wireless.  Is there anything you'd like for me to look for or print?

Yes. Please do now -
```
sudo modprobe -rfv rt2800pci
sudo modprobe -rfv rt3573sta
sudo modprobe -v rt3573sta
dmesg | grep -E 'rt2|rt3' | tail -20
```
..and post back the output of the last dmesg command. I hope to get some further clue to work on.

---

### Post by jdhoskins on 2013-06-18
Here ya go... 


```
kimes@kimes:~$ sudo modprobe -rfv rt3593sta
FATAL: Module rt3593sta not found.
kimes@kimes:~$ sudo modprobe -v rt3593sta
FATAL: Module rt3593sta not found.
```

```
kimes@kimes:~$ dmesg | grep -E 'rt2|rt3' | tail -20
[   10.462348] rtusb init rt3573 --->
[   10.464139] usbcore: registered new interface driver rt3573
```

---

### Post by varunendra on 2013-06-18
> **jdhoskins said:**
> 
```
kimes@kimes:~$ sudo modprobe -rfv rt3593sta
FATAL: Module **[COLOR="#FF0000"]rt3593sta[/COLOR]** not found.
kimes@kimes:~$ sudo modprobe -v rt3593sta
FATAL: Module rt35**[COLOR="#FF0000"]93[/COLOR]**sta not found.
```

Ugh, I've lost my mind, sorry. It was rt35**[COLOR="#006400"]73[/COLOR]**sta, not rt35**[COLOR="#FF0000"]93[/COLOR]**sta. Please try that instead, all the same four commands. I'm going to correct my previous post.

---

### Post by jdhoskins on 2013-06-18
It's been a long thread...  Here's the new stuff!

```

 dmesg | grep -E 'rt2|rt3' | tail -20
[   10.462348] rtusb init rt3573 --->
[   10.464139] usbcore: registered new interface driver rt3573
[ 6302.960048] usbcore: deregistering interface driver rt3573
[ 6330.885364] rtusb init rt3573 --->
[ 6330.885484] usbcore: registered new interface driver rt3573

```

---

### Post by varunendra on 2013-06-18
Hmm.. no hints there. Let's take a look at syslog also.

Please run the first three commands as before, then instead of dmesg, run -
```
cat /var/log/syslog | grep -iE 'rt2|rt3' | tail -20
```

and post back its output. If no hints are found, I'll have to take a closer look at other drivers to see if any looks promising with this patch.

You should also notify the author of the driver of this progress, especially mentioning the fact that he has used a USB driver (RT3573 USB) while the device is a PCI one.

Oh, and you can also help not only yourself, but many others as well by filing a bug report regarding rt2800pci driver on launchpad. That is, if you don't find the process overwhelming ;) : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by jdhoskins on 2013-06-18
Sounds like a brilliant idea.  I'll send him an email this evening.  I take it there's a lengthy process in reporting a bug...


```
 
 cat /var/log/syslog | grep -iE 'rt2|rt3' | tail -20


Jun 18 12:33:53 kimes kernel: [  524.640915] rtusb init rt3573 --->
Jun 18 12:33:53 kimes kernel: [  524.641636] usbcore: registered new interface driver rt3573
Jun 18 12:42:18 kimes kernel: [   10.462348] rtusb init rt3573 --->
Jun 18 12:42:18 kimes kernel: [   10.464139] usbcore: registered new interface driver rt3573
Jun 18 14:27:09 kimes kernel: [ 6302.960048] usbcore: deregistering interface driver rt3573
Jun 18 14:27:37 kimes kernel: [ 6330.885364] rtusb init rt3573 --->
Jun 18 14:27:37 kimes kernel: [ 6330.885484] usbcore: registered new interface driver rt3573
Jun 18 15:03:56 kimes kernel: [ 8509.188141] usbcore: deregistering interface driver rt3573
Jun 18 15:04:03 kimes kernel: [ 8516.476216] rtusb init rt3573 --->
Jun 18 15:04:03 kimes kernel: [ 8516.476357] usbcore: registered new interface driver rt3573

```

---

### Post by varunendra on 2013-06-18
Nothing interesting here as well.
Out of curiosity though, after running the first three commands, does the rt3573sta driver show up in the output of -
```
lspci -nnk | grep -iA2 net
```
.. where rt2800pci was earlier ??

I think there will be no driver at all after that, but at this point anything and everything would be helpful that shows any response from the device.

I would await any feedback you may get from the author. Perhaps the RT359**[COLOR="#800000"]2[/COLOR]** driver may be our next experiment subject if we don't get anything significant out of this one.

However, I should clarify that I am venturing in a totally unknown territory now. I may not even realize when I'm lost. :P

---

### Post by jdhoskins on 2013-06-24
Varun. Sorry I've been MIA.  I've been pulled to another project for a while.  Still haven't heard back from the author.  I'll try what you're asking ASAP and post back.  Thanks again!

---

### Post by varunendra on 2013-06-24
> **jdhoskins said:**
> Varun. Sorry I've been MIA.  I've been pulled to another project for a while.  Still haven't heard back from the author.  I'll try what you're asking ASAP and post back.  Thanks again!

No problem at all !

We know that users just want their system work and not everyone may have this much time to keep experimenting with us when there are much easier options, like getting a cheap compatible adapter instead, are available.

However, if you, like us, enjoy the fun of troubleshooting stuff, we'll always be ready to work with you until we are totally out of ideas. So far we are not.

I and Dr. Chili were having some conversation in the background about this chip, and he suggested that we should also try a newer "compat-wireless" package. It is nothing but a newer version of drivers backported from newer kernels. We hope that since the native rt2800pci driver includes a modalias for the chip, its newer version may happen to support it better in case its support was experimental in earlier versions. But like our earlier attempts, it is also just a guess, albeit an educated one.

Let me know when and if you are ready to try that. We are in no hurry, and we all understand that it has already dragged far away from the limits of patience a normal user can have.

---

### Post by jdhoskins on 2013-06-25
Personally, I'd rather get this working than get another.  I actually enjoy troubleshooting these things and making them work as well.  I'm really knew to Linux but I'm enjoying it so far.  As a matter of fact, I'm thinking of getting a laptop for myself to install and run as a Linux machine.  I'm not sure when I'll be able to appropriate time at work to work on this again since I'm currently working on other projects but look forward to getting back to it again!  People like you and Chili are definitely great to have around and I'm sure I'm not alone in appreciating your patience and help!  Also, I had actually looked at the compat-wireless option but was confused as to which version I should use.

---

### Post by chili555 on 2013-06-25
>  Also, I had actually looked at the compat-wireless option but was confused as to which version I should use. Varun has that all figured out for you and will write full instructions soon.

---

### Post by jdhoskins on 2013-06-25
Thanks for the info!

---

### Post by jdhoskins on 2013-06-25
Varun,

Also here is the output of the last set of commands you asked me to run.  It looks as though, for some reason, the 2800 is still hanging around in there.

  lspci -nnk | grep -iA2 net

01:00.0 Network controller [0280]: Ralink corp. Device [1814:3593]
        Subsystem: Ralink corp. Device [1814:3593]
        Kernel modules: rt2800pci
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
        Kernel driver in use: r8169

---

### Post by varunendra on 2013-06-26
> **jdhoskins said:**
> Also here is the output of the last set of commands you asked me to run.  It looks as though, for some reason, the 2800 is still hanging around in there.

Not surprising to me. The compiled driver being meant for USB devices only, couldn't bind with your card, hence the native one still hanging out there.

Here are the steps to compile a compatible **compat-wireless** package (tested successfully on Ubuntu 12.04. Once again, link & short steps both courtesy of Dr. Chili) :

[Indent]
**1)** As always, get a cable connection and make sure you have linux-headers and build-essential installed to be able to compile the driver -
```
sudo apt-get install build-essential linux-headers-generic
```

**2)** Download this package (right-click > save link as) : [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.7.9/compat-drivers-3.7.9-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.7.9/compat-drivers-3.7.9-1.tar.bz2)

**3)** Copy the downoaded file to your desktop

**4)** Right-Click the downloaded .tar.bz2 file > Extract here

**5)** Open a terminal, and do -
```
cd ~/Desktop/compat-drivers-3.7.9-1
./scripts/driver-select rt2x00
make
sudo make install
```
watch out for errors and post back if there are any.[/indent]

Load the new module (although it should've been done during the install process, just to make sure) :
```
sudo modprobe -rfv rt2800pci
sudo modprone -v rt2800pci
```

Try to connect. Any change?

If not, post back outputs of -
```
modinfo rt2800pci | egrep -i 'version|3593'
dmesg | grep rt2
```

Please note that you can try an even newer version by just booting with a live DVD/USB of 13.04, as it contains kernel 3.8 by default, while we are compiling above the one from kernel 3.7.9-1. If it works in 13.04, we can try to make it work in your current 12.04.

---

### Post by jdhoskins on 2013-07-03
Finally getting around to trying this today.  So I did sudo apt-get install build-essential linux-headers-generic and build essential was up to date but there were some things downloaded and installed with the headers.  So now I have no display.  The splash screen flashes a few times and then nothing but black screen.

---

### Post by chili555 on 2013-07-03
> **jdhoskins said:**
> Finally getting around to trying this today.  So I did sudo apt-get install build-essential linux-headers-generic and build essential was up to date but there were some things downloaded and installed with the headers.  So now I have no display.  The splash screen flashes a few times and then nothing but black screen.Were you able to re-boot? What happened next? Are there any clues as to the problem at:```
cat /var/log/dmesg.0 | tail -n20
```Both of the packages you installed are used to compile from source code. Until you compile and modprobe the driver, they should have no effect.

The solution Varun proposed was tested and compiled without error or warning on a 12.04 system.

---

### Post by jdhoskins on 2013-07-03
After reboot the bios screen comes up, then the splash screen flashes a couple of times and nothing but black...I'm guessing display drivers because when I try to boot and use recovery mode it sticks at a line that says "fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver.  However, it stays stuck on that line and never moves on.

---

### Post by chili555 on 2013-07-03
> **jdhoskins said:**
> After reboot the bios screen comes up, then the splash screen flashes a couple of times and nothing but black...I'm guessing display drivers because when I try to boot and use recovery mode it sticks at a line that says "fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver.  However, it stays stuck on that line and never moves on.I am guessing display as well. I suggest you ask in General Help. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331) Sorry for your trouble.

---

### Post by varunendra on 2013-07-03
> **jdhoskins said:**
> I'm guessing display drivers because when I try to boot and use recovery mode it sticks at a line that says "fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver.

I'm quite certain it is a graphics driver or its configuration issue. As a quick-fix, you may try adding "nomodeset" option (or other vesa modes) to the grub boot line. You can easily and safely try this using boot repair live cd : [https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

(or just manually edit the boot line by pressing "e" at the grub menu > add "nomodeset" (without quotes) before or between "quiet splash" > ctrl+x to boot with it.)

If that doesn't help, you should start a relevant thread in general help section as Dr. chili suggested.

Sorry for the additional trouble, but I can assure it is unrelated to what we are dealing with here.

---

### Post by jdhoskins on 2013-07-08
Thanks for the help fellas.  I think I'm gonna have to just start over from scratch though.  The computer hangs at that message and won't boot into recovery mode.  I think for some reason the kernel updates didn't like that generic driver I was using for the display.  If I load the original kernel I can at least get to grub but startx gives errors indicating that xorg isn't working and for some reason I can't uninstall, reinstall nor download anything related to it because it says it can't be found.  I think the best thing to do is just start over with a clean slate and see what I can do.

---

