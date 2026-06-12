---
title: "hauppauge nova-t-500 diversity"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by tobycatlin on 2007-07-30
I was giddy as a school boy when i received my brand spanking new nova-t 500 on friday. I spent a good part of the weekend trying to get this damn thing to work on my Ubuntu feisty machine.

I read [Jonathan Fors blog]("http://www.omskakas.se/2007/01/howto-hauppauge-nova-t-500-pci-under-linux.html") which seemed to help most people, not me. I also followed the [URL="http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux"]efficient PC tutorial 
[/URL] still no dice.

I do have the Diversity model, which has two antennae inputs for improved signal, which i understand may be using different chip sets to the previous nova-t-500 model. [see here]("http://www.gossamer-threads.com/lists/mythtv/users/280612") 

I was hoping someone on this forum has got this new version of the nova-t-500 working. If any of you driver guru's want a problem to crack please help me out. Really any help or advice would be really great.

Some details of my system:
Ubuntu Fiesty Fawn on a 2ghz amd athlon cpu, motherboard asus a7v socket a

```

uname -a
Linux toby 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
 
```

The card is listed in the pci bus, but ubuntu doesn't know what it is
```

lspci

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
**01:0a.0 Multimedia controller: Hauppauge computer works Inc. Unknown device 6800 (rev 01)**
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
03:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

lspci -v

01:0a.0 Multimedia controller: Hauppauge computer works Inc. Unknown device 6800 (rev 01)
        Subsystem: Hauppauge computer works Inc. Unknown device 6800
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d4000000 (32-bit, prefetchable) [size=16M]
        Capabilities: [f0] Power Management version 2
 
```

There are 4 devices ont he usb bus.  note: There is a usb mouse plugged in which is the Kensington device. I am guessing/hoping that the other devices are the nova-t-500 hub and two dvb chips
```

lsusb

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 047d:102a Kensington 
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

 
```

Lots of things that mention dvb_usb that i don't understand
```

lsmod

Module                  Size  Used by
dvb_usb_dib0700        18696  0
dib7000m               16004  1 dvb_usb_dib0700
dib7000p               14468  1 dvb_usb_dib0700
dvb_usb                22924  1 dvb_usb_dib0700
dvb_core               82472  1 dvb_usb
dib3000mc              13444  1 dvb_usb_dib0700
dibx000_common          4996  3 dib7000m,dib7000p,dib3000mc
snd_rtctimer            4384  0
nls_iso8859_1           5120  0
usb_storage            72256  0
libusual               17936  1 usb_storage
smbfs                  66040  2
isofs                  36284  1
udf                    85252  0
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0
vmnet                  39076  13
vmmon                 113420  0
nfsd                  218992  17
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ipv6                  268960  22
ppdev                  10116  0
fglrx                 540004  35
cpufreq_conservative     8200  0
cpufreq_userspace       5408  0
cpufreq_stats           7360  0
cpufreq_ondemand        9228  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0
dev_acpi               12292  0
sony_acpi               6284  0
tc1100_wmi              8068  0
pcc_acpi               13184  0
dock                   10268  0
battery                10756  0
asus_acpi              17308  0
button                  8720  0
container               5248  0
sbs                    15652  0
i2c_ec                  6016  1 sbs
video                  16388  0
backlight               7040  1 asus_acpi
ac                      6020  0
nls_utf8                3072  1
nls_cp437               6784  2
vfat                   14208  1
fat                    53916  1 vfat
eeprom                  8336  0
asb100                 21780  0
hwmon_vid               4224  1 asb100
sbp2                   23812  0
parport_pc             36388  0
lp                     12452  0
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  1
snd_intel8x0           34332  1
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
serio_raw               7940  0
psmouse                38920  0
pcspkr                  4224  0
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0
nvidia_agp              9500  1
i2c_core               22656  9 dib7000m,dib7000p,dvb_usb,dib3000mc,dibx000_common,i2c_ec,eeprom,asb100,i2c_nforce2
agpgart                35400  2 fglrx,nvidia_agp
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
af_packet              23816  6
evdev                  11008  3
tsdev                   8768  0
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sd_mod                 23428  4
ide_cd                 32672  1
cdrom                  37664  1 ide_cd
sata_nv                20868  0
ata_generic             9092  0
generic                 5124  0 [permanent]
usbhid                 26592  0
hid                    27392  1 usbhid
3c59x                  46632  0
mii                     6528  1 3c59x
forcedeth              46728  0
sata_sil               12808  3
libata                125720  3 sata_nv,ata_generic,sata_sil
scsi_mod              142348  5 usb_storage,sbp2,sg,sd_mod,libata
ohci1394               36528  0
ieee1394              299448  2 sbp2,ohci1394
amd74xx                15260  0 [permanent]
ehci_hcd               34188  0
ohci_hcd               22532  0
usbcore               134280  8 dvb_usb_dib0700,dvb_usb,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability
 
```

---

### Post by MrHippocampus on 2007-07-30
Try running "sudo update-pciids" and then "lspci" to see if your card is recognised (The first command will download the lastest list of pciid's from the internet).

---

### Post by tobycatlin on 2007-07-30
Thanks for the suggestion. I ran that command and updated successfully. Re-ran lspci and nothing had changed :(

```

01:0a.0 Multimedia controller: Hauppauge computer works Inc. Unknown device 6800 (rev 01)

```

---

### Post by MrHippocampus on 2007-07-30
Does dmesg say anything about finding the card?

---

### Post by tobycatlin on 2007-07-30
i have posted the full dmesg output to this [file ]("http://tobycatlin.is-a-geek.com/dmesg.txt")
It doesn't specifically mention the nova-t-500 or anything even similar. One thing Jonathan Fors tutorial  says is that i should expect the following in dmesg output:

```
[ 47.706381] dib0700: loaded with support for 2 different device-types
[ 47.755845] dvb-usb: found a &#8216;Hauppauge Nova-T 500 Dual DVB-T&#8217; in cold state, will try to load a firmware
[ 47.831894] dvb-usb: downloading firmware from file &#8216;dvb-usb-dib0700-01.fw&#8217;
[ 48.004945] dib0700: firmware started successfully.
[ 48.106970] dvb-usb: found a &#8216;Hauppauge Nova-T 500 Dual DVB-T&#8217; in warm state.
[ 48.107568] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 48.107929] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T).
[ 48.191285] DVB: registering frontend 1 (DiBcom 3000MC/P)&#8230;
[ 48.192903] MT2060: successfully identified (IF1 = 1220)
[ 48.657038] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 48.657373] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T).
[ 48.661165] DVB: registering frontend 2 (DiBcom 3000MC/P)&#8230;
[ 48.663158] MT2060: successfully identified (IF1 = 1220)
[ 49.129041] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[ 49.129071] **usbcore: registered new interface driver dvb_usb_dib0700**

```

This last line is mentioned in my dmesg but nothing as promising as 'Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected'

any clues?

---

### Post by MrHippocampus on 2007-07-30
From the dmesg youve posted it seems the dvb usb chip has been found (dib0700, same as normal nova 500) so it might just be a very similar card which the dvb drivers don't recognise yet (hopefully). My suggestion to you is to go to [this page]("http://www.linuxtv.org/lists.php") (linuxtv.org) and either go on the dvb irc channel for help or post on the linux-dvb mailing list.

Ive looked on the mailing list already for nova 500 diversity related message and there was one person asking about it (in the July 2007 archive) with a follow up from a developer but nothing after that :(.

Good luck :)

---

### Post by tobycatlin on 2007-07-30
Thanks for your help. I can tell it's close to working, i just don't have this level of linux skills to go the last mile. I'll try linuxtv.

---

### Post by tobycatlin on 2007-07-30
Thanks for your help. I can tell it's close to working, i just don't have this level of linux skills to go the last mile. I'll try linuxtv.

---

### Post by hossa1c on 2007-07-31
Hi,
I just brought this same card. I think it's actually called  a Nova-TD 500 to indicate it's a diversity model. I've checked the linuxtv forum and found this thread

[http://linuxtv.org/pipermail/linux-dvb/2007-July/019397.html](http://linuxtv.org/pipermail/linux-dvb/2007-July/019397.html)

It looks like Patrick Boettcher is the main guy who writes the drivers. He says the nova-TD 500 card uses the DiB0710 PCI controller, but it was never released for mass production :( and there is no plan to write a driver for it.

If the nova-td 500 is the new card that Hauppauge is now making, will it eventually replace the nova-t 500 product. If so then all new mythtv users will end up buying one, and end up not being able to make their system work. Then I guess a driver will be written, and my card will work, one day...

If the nova-td 500 is just to get rid of old stock and wont be made for the long run, then I had better send mine back ASAP and find the non-diversity model

cheers

---

### Post by DannyW on 2007-07-31
I hope it isn't the case that a driver will not be produced. I've just got this card today from EBuyer. They don't mention that it is the diversity model they are selling and the images only have one antenna input, so hopefully I can send it back.

There is a comment on the ebuyer site saying do not buy for use with linux, unfortunately though, i ordered this the day before that comment was posted.

---

### Post by hossa1c on 2007-07-31
hi,
I just phoned up Hauppauge technical support help line (020 7378 0202) and asked about the nova-TD 500. Apparently this is only a short run of cards. The chip used on the nova-T 500 dried up, so Hauppauge started sourcing a different chip set for the nova-TD 500. Then the chip manufacture said they had found more of the original chip sets. This meant that only a small amount of nova-TD 500 cards were made.

The good news is, that they said that they would exchange my nova-TD 500 card for an original nova-T 500 card. All I have to do it send it back to them with a cover note explaing that I want to use it in a Linux box. I guess this will cost me £5 p&p, but at least I get the card I wanted. :)

Hopes this help everybody stuck with a nova-TD 500 card.

---

### Post by MrHippocampus on 2007-07-31
Wow, that's really good of Hauppauge to do that. It might be a good idea to post that to the linuxtv dvb mailing list or put it on the linuxtv nova 500 wiki page so other people in the same situation can do the same :)

---

### Post by DannyW on 2007-07-31
Ah, this is good news!

I have just filed a return at ebuyer to swap it for a HVR-1300. If they decline, I too shall contact hauppauge. Thanks for that info.

---

### Post by jonny on 2007-07-31
I was the person who posted the warning to the ebuyer web site, having taken delivery of one of the TD cards from them on Friday.  It's a shame that I made my discovery too late for some of you.

It's good that Hauppauge seems to be willing to substitute the TD model for one that actually works with Linux.   I'll be giving them a call tomorrow.

---

### Post by jonny on 2007-08-01
I've just contacted Hauppauge and they were extremely helpful.  Substitution is no problem.

---

### Post by tobycatlin on 2007-08-01
damn it just my luck to buy a duff card out of a batch of dodgy ones. thanks for the info hossa1c , i have emailed the linuxtv mail list with the new info. i am sure they will update the wiki

---

