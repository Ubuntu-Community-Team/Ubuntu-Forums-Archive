---
title: "skystar 2 wrong drivers"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by wallygator.uk on 2008-01-31
Hi forum, here is my first post so i introduce myself. I' wally from uk.

i recently bought a skystar 2 but i'm having problems installing it.

i'm running gutsy with kernel 2.6.22-14, so the driver should be with it.

my dmesg

[   60.102855] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   60.125835] Linux agpgart interface v0.102 (c) Dave Jones
[   60.140806] flexcop-pci: will use the HW PID filter.
[   60.140811] flexcop-pci: card revision 2
[   60.141117] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   60.141123] ACPI: PCI Interrupt 0000:03:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 22
[   60.145331] DVB: registering new adapter (FlexCop Digital TV device)
[   60.147103] b2c2-flexcop: MAC address = 00:d0:d7:13:b6:b9
[   60.328872] nvidia: module license 'NVIDIA' taints kernel.
[   60.720251] usbcore: registered new interface driver xpad
[   60.720254] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-rt/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   60.943446] usbcore: registered new interface driver snd-usb-audio
[   61.503064] b2c2-flexcop: i2c master_xfer failed
[   61.703238] b2c2-flexcop: i2c master_xfer failed
[   61.761173] b2c2-flexcop: i2c master_xfer failed
[   61.761175] mt352_read_register: readreg error (reg=127, ret==-121)
[   61.781941] b2c2-flexcop: i2c master_xfer failed
[   61.781944] nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -121)
[   61.781945] Unknown/Unsupported NXT chip: 00 00 00 00 00
[   61.799976] b2c2-flexcop: i2c master_xfer failed
[   61.799980] lgdt330x: i2c_read_demod_bytes: addr 0x59 select 0x02 error (ret == -121)
[   61.819318] b2c2-flexcop: i2c master_xfer failed
[   61.839792] b2c2-flexcop: i2c master_xfer failed
[   61.839795] stv0297_readreg: readreg error (reg == 0x80, ret == -121)
[   61.860170] b2c2-flexcop: i2c master_xfer failed
[   61.860175] mt312_read: ret == -121
[   61.860191] b2c2-flexcop: no frontend driver found for this B2C2/FlexCop adapter

somebody on another board suggested that he had a REV1 card, while mine is rev2 and had no problems.

the card is recognized as Technisat Skysatr 2

lsmod gives me

Module                  Size  Used by
snd_rtctimer            4384  1 
binfmt_misc            13320  1 
rfcomm                 43672  2 
l2cap                  26752  11 rfcomm
bluetooth              58980  4 rfcomm,l2cap
nfsd                  222832  13 
exportfs                7040  1 nfsd
lockd                  67976  2 nfsd
sunrpc                174844  8 nfsd,lockd
ppdev                  10244  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7488  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0 
ac                      6276  0 
dock                   11124  0 
container               5504  0 
sbs                    19848  0 
button                  9104  0 
battery                11012  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14336  1 
fat                    54684  1 vfat
ipv6                  281444  22 
sbp2                   24584  0 
lp                     13252  0 
xt_limit                3712  8 
mt312                   8964  0 
stv0297                 8704  0 
xt_tcpudp               4224  11 
bcm3510                10884  0 
lgdt330x                9988  0 
nxt200x                14852  0 
mt352                   7684  0 
ipt_LOG                 7680  8 
ipt_MASQUERADE          4736  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8216  0 
nf_conntrack_ftp       11264  0 
xt_state                3456  6 
snd_hda_intel         263840  0 
stv0299                11528  0 
snd_seq_dummy           4740  0 
snd_emu10k1x           20868  0 
snd_ac97_codec        100772  1 snd_emu10k1x
snd_pcm_oss            44928  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_usb_audio          81408  0 
snd_usb_lib            18176  1 snd_usb_audio
snd_pcm                80644  5 snd_hda_intel,snd_emu10k1x,snd_ac97_codec,snd_pcm_oss,snd_usb_audio
snd_hwdep              10500  1 snd_usb_audio
b2c2_flexcop_pci       11288  0 
xpad                   10372  0 
b2c2_flexcop           29836  1 b2c2_flexcop_pci
emu10k1_gp              4864  0 
dvb_core               80696  3 lgdt330x,stv0299,b2c2_flexcop
nvidia               6222896  34 
gameport               17672  2 emu10k1_gp
agpgart                35284  1 nvidia
ac97_bus                3456  1 snd_ac97_codec
snd_seq_oss            33792  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_emu10k1x,snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54128  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             37796  1 
parport                38216  3 ppdev,lp,parport_pc
snd                    55172  14 snd_hda_intel,snd_emu10k1x,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               8196  0 
pcspkr                  4352  0 
psmouse                40208  0 
soundcore               9312  1 snd
i2c_nforce2             7168  0 
snd_page_alloc         11400  3 snd_hda_intel,snd_emu10k1x,snd_pcm
i2c_core               26880  10 mt312,stv0297,bcm3510,lgdt330x,nxt200x,mt352,stv0299,b2c2_flexcop,nvidia,i2c_nforce2
shpchp                 34964  0 
pci_hotplug            33460  1 shpchp
joydev                 11456  0 
evdev                  11136  5 
iptable_nat             8836  0 
nf_nat                 20780  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19852  8 iptable_nat
nf_conntrack           67592  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               7064  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16772  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ide_cd                 32800  0 
cdrom                  37664  1 ide_cd
ext3                  134536  1 
jbd                    59688  1 ext3
mbcache                 9860  1 ext3
sg                     36764  0 
sd_mod                 30976  5 
usbhid                 30176  0 
hid                    29056  1 usbhid
amd74xx                15388  0 [permanent]
ide_core              118980  2 ide_cd,amd74xx
sata_nv                20612  4 
ahci                   23556  0 
ohci1394               37040  0 
ieee1394               98360  2 sbp2,ohci1394
floppy                 63428  0 
ata_generic             8580  0 
ehci_hcd               36108  0 
forcedeth              50952  0 
libata                125424  3 sata_nv,ahci,ata_generic
scsi_mod              148844  4 sbp2,sg,sd_mod,libata
ohci_hcd               22788  0 
usbcore               139912  7 snd_usb_audio,snd_usb_lib,xpad,usbhid,ehci_hcd,ohci_hcd
thermal                14600  0 
processor              32200  1 thermal
fan                     5892  0 
fuse                   48404  3 
apparmor               41624  0 
commoncap               8320  1 apparmor

(here are the lines about the card
b2c2_flexcop           29836  1 b2c2_flexcop_pci
emu10k1_gp              4864  0 
dvb_core               80696  3 lgdt330x,stv0299,b2c2_flexcop


but no /DVB/ folder is created in /dev.

i tried about every single google and wiki page but i'm really stack, anybody else made this working?

Many thanks

---

### Post by steefjeqv on 2008-01-31
Hi Wally,

There's two things you can try :

1. Type the two following commands in your terminal :

sudo modprobe b2c2-flexcop-pci
sudo modprobe stv0299

After this, just start up Kaffeine and look if there are any DVB devices recognized.

I'm not sure if you're version is using the stv0299 frontend, but you can give it a try.

2. Perhaps you'll have to insert the correct firmware in /lib/firmware.

Greetings,
Steven

---

### Post by wallygator.uk on 2008-01-31
steven, thanks for your reply. tried but nothing shows up, still no DVB folder under /dev

I have few firmwares in the kernel 2.6.22-14-rt

these are

dvb-fe-or51132-qam.fw

dvb-fe-or51132-vsb.fw

dvb-fe-or51211.fw

dvb-ttpci-01.fw

the last one i understand should be the one for my card. the fact is that the SS2 should be working out of the box, that's the main reason i bought it. As usual, in winx works like a charme.... inlcuding remote control.

in ubuntu under this line

[ 61.860191] b2c2-flexcop: no frontend driver found for this B2C2/FlexCop adapter

let's me understand that the card hasnt got a driver. i followed step by step the wiki on linuxtv for the installation of the drivers.



any help is really appreciated

---

### Post by steefjeqv on 2008-01-31
Hi Wally,

You're not the only one having this problem with the Skystar2 version 2.

Which version do you have exactly ?

If it's a 2.7, then you may have a problem which is unsolvable (for the moment).

I found a thread on the German VDR forum (VDR Portal) which solved your exact problem.
The card in this thread was a Skystar2 (version 2.6). 

You'll have to blacklist your drivers :

Edit the following file by typing in terminal :

sudo gedit /etc/modprobe.d/blacklist 

Add the following two lines to the file :
blacklist dvb_ttpci
blacklist b2c2_flexcop_pci

Save and close.

Now add your drivers to the following file (in terminal) :

sudo gedit /etc/modules

Add the following two lines to this file :
dvb_ttpci
b2c2_flexcop_pci

Save and close.

Restart your computer and hopefully your Skystar2 will work.

Greetings,
Steven

---

### Post by wallygator.uk on 2008-01-31
Steven, glad you understand german.. i tried to do what you suggested but still no trace of the ss2 anywhere in my apps - as said it does load the module but then i does not find the right driver.

the result are still the same as decribed in the top thread

i just bought it from germany, and it's inside the pc now but i will check the version as soon as i'll have time to open it.

Any idea if something is being done if it's a 2.7?

i just can't belive this.....

---

### Post by steefjeqv on 2008-01-31
Hi Wally,

The thread starter on the German forum first bought a version 2.7 of the Skystar2.
The shop he bought it from took it back in the end (no linux support).

It's a shame because the Skystar cards have good linux support.

I'm going to have a further look on the German VDR forum.

Greetings,
Steven

---

### Post by steefjeqv on 2008-01-31
Hi Wally,

This maybe a long shot but you can try a different pci slot.

Greetings,
Steven

---

### Post by steefjeqv on 2008-01-31
Hi Wally,

The 2.7 drivers are still in development.
They're not merged into the v4l-drivers at the moment.

I've found this driver (attached) at v4l (still development).

So if your Skystar is a 2.7 you can give this a try.



Download and untar the attached file to your home folder.

Open up your terminal and navigate to the v4l-dvb-skystar2-rev27 directory :

In terminal type :

sudo make

sudo make install



Hopefully this will give you a working driver for a Skystar2 version 2.7.

Greetings,
Steven

---

### Post by wallygator.uk on 2008-01-31
steven, i managed to find the file googleing, now the driver WORKS!!! you are the man!!!

I'll play a bit with it tonite, even if nothing is not still showing in kaff, but now i got a DVB directory in /dev

cheers mate, ill keep you and the community posted.

---

### Post by steefjeqv on 2008-02-01
Hello wally,

Sorry, I forgot to attach the driver I mentioned in my previous post.

Anyway, there seems to be some progress now.

Please let me know if there's any trouble !

Greetings,
Steven

---

### Post by wallygator.uk on 2008-02-02
I managed to get the card recognized and now have DVB folder and option on kaffeine, but the program fails to tune any channel.

here is a log from kaffeine started from consolle

wally@ubuntudesk:~$ ls -l /dev/dvb/adapter0/
total 0
crw-rw---- 1 root video 212, 4 2008-02-02 17:19 demux0
crw-rw---- 1 root video 212, 5 2008-02-02 17:19 dvr0
crw-rw---- 1 root video 212, 3 2008-02-02 17:19 frontend0
crw-rw---- 1 root video 212, 7 2008-02-02 17:19 net0
wally@ubuntudesk:~$ kaffeine
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
DCOP Cleaning up dead connections.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
0
/dev/dvb/adapter0/frontend0 : opened ( Samsung S5H1420/PnpNetwork PN1010 DVB-S )
/dev/dvb/0/frontend1 : : No such file or directory
Loaded epg data : 0 events (0 msecs)
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
wally@ubuntudesk:~$ DvbCam::probe(): /dev/dvb/adapter0/ca0: : No such file or directory
Using DVB device 0:0 "Samsung S5H1420/PnpNetwork PN1010 DVB-S"
tuning DVB-S to 11919000 v 27500000
inv:2 fecH:2
DiSEqC: switch pos 0, 13V, hiband (index 2)
DiSEqC: e0 10 38 f1 00 00
...............

Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
Transponders: 1
dvbsi: The end :)
Channels found: 0
Saved epg data : 0 events (0 msecs)

i deleted all the transponders from the Hotbird satellite list but one, on which i'm sure there is something 9just to speed up channel scan). it does not seem to lock on the satellite at all despite during the scan the signal level rieaches 100%. the SNR level is 0% and the little green light of the "lock" does not lite, so i guess ther is no lock at all.

in winxp on the same TP everything works fine, it seems like the card cannot get signal.

many thanks, i've been googlein and looking of the kaffeine forum, but i dont think the issue is with the app but with the card.

---

### Post by steefjeqv on 2008-02-02
Hi wally,

A possible solution for your tuning problem :

1. I just found out that before you install the driver (make & make install), you have to configure the driver with the following command : make config.
Make sure to answer yes for the Samsung S5H1420 option.

2. You may need additional firmware for your Samsung tuner. This can be copied from the (windows) driver cd that came with the Skystar2 package. I don't know where exactly to look for it on the cd but it maybe a .bin file.

Maybe it's best to try these two options separately.

Hope this helps,

Steven

---

### Post by wallygator.uk on 2008-02-02
so are you suggesting to reinstall the drivers, but instead going to make > make config > make install?

do i have to unistall the previosly installed drivers? if yes how to?

PS: tried te above selecting Y and M (module) on the bits of code i recognised as part of the hardware but still no luck..

thanks for all this help, i changed the title of the thread to reflect the model of skystar 2 having this problem, as i read on other forums other revisions just work out of the box (what a lucky man i am..)

---

### Post by steefjeqv on 2008-02-04
Hi Wally,

Sorry for the late reply (busy weekend).

I've thought about the "make config" command, and I don't think it's going to make a difference. The Samsung frontend is being recognized, so I figure the driver is configured correctly.

This leaves us with the option of adding firmware. This may very well the problem.

You can check this using "dmesg". Open up your terminal and use the following command :

sudo dmesg

You can try and specify your search in dmesg by specifying for example "firmware" :

sudo dmesg | grep firmware

Just look for any error messages concerning your Skystar2.

Greetings,
Steven

---

### Post by wallygator.uk on 2008-02-04
Steven, hope you had a nice weekend. tried  dmesg and thant's the result (at least the bit for the ss2). for what i see the module is loaded correctly

```
[   47.899331] lp0: using parport0 (interrupt-driven).
[   48.010854] Linux video capture interface: v2.00
[   48.046397] saa7146: register extension 'dvb'.
[   48.066940] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   48.068036] flexcop-pci: will use the HW PID filter.
[   48.068040] flexcop-pci: card revision 2
[   48.068348] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   48.068353] ACPI: PCI Interrupt 0000:03:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 22
[   48.072230] DVB: registering new adapter (FlexCop Digital TV device)
[   48.072430] rd(53): f8 00 d0 d7 13 b6 b9 00 1b 
[   48.073726] b2c2-flexcop: MAC address = 00:d0:d7:13:b6:b9
[   48.073757] rd(53): 00 03 
[   48.125180] wr(08): 20 
[   48.125183] b2c2-flexcop: ISL6421 successfully attached
[   48.137205] wr(53): 02 01 
[   48.137340] rd(61): 00 00 
[   48.137428] ITD1000: id: 0
[   48.137430] ITD1000: successfully identified
[   48.137432] b2c2-flexcop: ITD1000 successfully attached
[   48.137433] b2c2-flexcop: found 'Samsung S5H1420/PnpNetwork PN1010 DVB-S' .
[   48.137436] DVB: registering frontend 0 (Samsung S5H1420/PnpNetwork PN1010 DVB-S)...
[   48.137469] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.7a/u' at the 'PCI' bus controlled by a 'FlexCopIIb' complete

```

the sudo dmesg | grep firmware

does not give any result



I have few firmwares in the kernel 2.6.22-14-rt

these are

dvb-fe-or51132-qam.fw

dvb-fe-or51132-vsb.fw

dvb-fe-or51211.fw

dvb-ttpci-01.fw

the last one i understand (from reading and goggling) should be the one for my card, unless the rev 2.7 uses other or modified version.

thanks  for the effort

---

### Post by steefjeqv on 2008-02-04
Hi Wally,

As you say, the dmesg output is good.

Just to be sure, you can check the output of /var/log/messages. Just type the following in terminal :

sudo tail -f /var/log/messages


You can also try doing a channel scan using dvb-utils. Type in terminal :

sudo apt-get install dvb-utils
sudo scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Hotbird-13.0E


Chances are that this driver version is still too buggy. So it's best to keep an eye on following link :

[http://linuxtv.org/hg/~pb/v4l-dvb.skystar2.rev27/]("http://linuxtv.org/hg/~pb/v4l-dvb.skystar2.rev27/")

I've found an active thread on the German Ubuntu forum concerning the Skystar2 version 2.7.
The last few posts in this thread stated that there might be a finished driver somewhere in the middle of March.

[http://forum.ubuntuusers.de/topic/141553/15/]("http://forum.ubuntuusers.de/topic/141553/15/")


Greetings,
Steven

---

### Post by wallygator.uk on 2008-02-04
sudo tail -f /var/log/messages gave us the following

```
Feb  4 18:09:54 ubuntudesk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Feb  4 18:09:54 ubuntudesk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Feb  4 18:09:54 ubuntudesk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Feb  4 18:09:54 ubuntudesk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Feb  4 18:28:11 ubuntudesk -- MARK --
Feb  4 18:48:12 ubuntudesk -- MARK --
Feb  4 19:08:11 ubuntudesk -- MARK --
Feb  4 19:28:11 ubuntudesk -- MARK --
Feb  4 19:48:12 ubuntudesk -- MARK --
Feb  4 20:08:11 ubuntudesk -- MARK -
```

sudo scan /usr/share/doc/dvb-utils/examples/scan/dvb-s/Hotbird-13.0E

gave me

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-s/Hotbird-13.0E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 12539000 H 27500000 3
>>> tune to: 12539:h:0:27500
WARNING: >>> tuning failed!!!
>>> tune to: 12539:h:0:27500 (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

i can confirm that on that TP there are active channels (checked with the receiver). and there is signal down the cable (i'm a satellite installer myself).

I traslated and bookmarked  the thread you reported and .. well i understand that there may be a bit to wait.

thanks for your effor, i appreciated it.

Meanwhile

---

### Post by gpap1266 on 2008-03-24
I have the same problem,  ver 2.7 don't scan the channels , as i saw in the linux tv site , the drivers about this card they stay developed 4 months ago, since then no news....
I thing we have to sell the 2.7 , piti for Technisat :(

---

### Post by wallygator.uk on 2008-03-25
already sold it, and bought on ebay a compatible one....

---

