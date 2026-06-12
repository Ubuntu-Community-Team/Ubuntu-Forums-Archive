---
title: "F5D8010 - Works, but does not save settings"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by lamard2 on 2010-05-06
I am able to enter all of the commands according to the 

[LIST]
[*][WifiDocs]("https://help.ubuntu.com/community/WifiDocs")
[*][Device]("https://help.ubuntu.com/community/WifiDocs/Device")
[*][URL="https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010?action=fullsearch&context=180&value=linkto%3A%22WifiDocs/Device/Belkin_F5D8010%22"]Belkin_F5D8010
[/URL]
[/LIST]
document, and I'm able to get connected!  However, when I reboot, I have to enter all of the commands again.  I must be getting  an error message somewhere regarding saving the settings.  Which step could be giving me this problem?

Thanks,
Lamar

PS - I really appreciate the help!  I thought for sure that I would have to buy a new usb network card!  Well, I just signed up with CLEAR wireless...that will be another project, on down the road.  First things first with this older notebook PC - Toshiba Satellite 1135-S125!

---

### Post by GSF1200S on 2010-05-06
> **lamard2 said:**
> I am able to enter all of the commands according to the 

[LIST]
[*][WifiDocs]("https://help.ubuntu.com/community/WifiDocs")
[*][Device]("https://help.ubuntu.com/community/WifiDocs/Device")
[*][URL="https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010?action=fullsearch&context=180&value=linkto%3A%22WifiDocs/Device/Belkin_F5D8010%22"]Belkin_F5D8010
[/URL]
[/LIST]
document, and I'm able to get connected!  However, when I reboot, I have to enter all of the commands again.  I must be getting  an error message somewhere regarding saving the settings.  Which step could be giving me this problem?

Thanks,
Lamar

PS - I really appreciate the help!  I thought for sure that I would have to buy a new usb network card!  Well, I just signed up with CLEAR wireless...that will be another project, on down the road.  First things first with this older notebook PC - Toshiba Satellite 1135-S125!

Can you be a little more specific? What commands are you using to get connected? We might be able to setup your /etc/network/interfaces file to handle your networks, or we could create a bash alias where you can use one word to invoke all the commands you need to connect. Does network manager not list your networks? You can try wicd which is available in the repos:
```
sudo apt-get install wicd
```
We need to know what your issue is in order to help you.

---

### Post by lamard2 on 2010-05-06
I think it's step # 9 - gksudo network-admin.

I get the following error message:

The configuration could not be loaded
You are not allowed to access the system configuration.

How do I enter my network-admin password?

Lamar

---

### Post by GSF1200S on 2010-05-06
> **lamard2 said:**
> I think it's step # 9 - gksudo network-admin.

I get the following error message:

The configuration could not be loaded
You are not allowed to access the system configuration.

How do I enter my network-admin password?

Lamar

The problem is, I dont know exactly WHERE you are talking about. Please answer the above questions so that someone else (and hopefully I) can help you.

Also, can you post the results of:
```
lspci
```
and
```
lsmod
```
here so that we know what chipset/modules you have/are using. What commands are you running that work for you?

---

### Post by lamard2 on 2010-05-06
Thank you GSF for your assitance.

I used the steps that were provided here:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010?action=show&redirect=F5D8010](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010?action=show&redirect=F5D8010)

When I got to Step #9, from the above referenced linked guidelines, that is when I got the error message:
The configuration could not be loaded
You are not allowed to access the system configuration.

Here are the results from lspci:
lamar@Toshiba1135:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
07:00.0 Ethernet controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card (rev 01)
lamar@Toshiba1135:~$ 

Here are the results from lsmod:
lamar@Toshiba1135:~$ lsmod
Module                  Size  Used by
i915                   32512  2 
drm                    82580  3 i915
ipv6                  267780  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5284  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
evdev                  13056  6 
serio_raw               7940  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
pcspkr                  4224  0 
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
psmouse                40336  0 
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
battery                14212  0 
container               5632  0 
ac                      6916  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
yenta_socket           27276  3 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
sg                     36880  0 
hid                    38784  1 usbhid
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_piix               19588  2 
ata_generic             8324  0 
8139too                27520  0 
pata_acpi               8320  0 
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 
lamar@Toshiba1135:~$ 

I hope this helps.  

Thanks again for your assistance.

Lamar

---

### Post by lamard2 on 2010-05-10
Did  give up on me? Did I do or say something wrong?

I there a way that I can create a script that would enter all of the commands every time I start the notebook pc?

Lamar

---

