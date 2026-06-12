---
title: "WinTV-PVR USB2 Remote"
date: 2007-10-30
forum: Mythbuntu
---

### Post by ghuber on 2007-10-30
I have 7.10 up and running and patched with the WinTV-PVR USB2 working.  I am able to record and watch TV with no problems.  I now need to get the Remote and IR blaster working.  Remote is first but may be related.  Has anyone here had any luck getting this to work?  Is there a good list of things to try to get this to work?  I'm a little grey as far as where to start.  I have enabled the remote with a number of the choices with the gui with no luck. I suspect I just need to modify my config file but I'm not sure what it might need.

Thanks

---

### Post by ghuber on 2007-10-30
Ok,  getting close.

Found in the Wiki that my model does I2C so the Hauppauge TV Card choice should work.  

Did that but no joy yet.

Found that /dev had both a /dev/lirc0 and lirc1

Read that lirc1 is what I want...  
tried this:
lircd --driver=default --device=/dev/lirc1 --output=/dev/lircd1 \
    --pidfile=/var/run/lircd1.pid --listen
This added a process to listed to lirc1..

Now irw command shows all my remote button commands but no response from MythTV yet.  Getting close.

---

### Post by superm1 on 2007-10-30
> **ghuber said:**
> Ok,  getting close.

Found in the Wiki that my model does I2C so the Hauppauge TV Card choice should work.  

Did that but no joy yet.

Found that /dev had both a /dev/lirc0 and lirc1

Read that lirc1 is what I want...  
tried this:
lircd --driver=default --device=/dev/lirc1 --output=/dev/lircd1 \
    --pidfile=/var/run/lircd1.pid --listen
This added a process to listed to lirc1..

Now irw command shows all my remote button commands but no response from MythTV yet.  Getting close.
If you've got a /dev/lirc1, you will need to black list whatever module is automatically loading that you don't need.

Usually its something like lirc_imon that would be loading.  After that happens, everythign should come back to life with the standard init scripts.

---

### Post by ghuber on 2007-10-31
Great, got it working...  added the device into the conf file and blacklisted the name you gave me.  Rebooted and all is well.

Thanks

Now has anyone got the IR blaster to work?

---

### Post by superm1 on 2007-10-31
Open a separate thread for that.  I'm marking this one solved :)

---

### Post by bluec99 on 2007-12-04
Running mythbuntu with the pvr-usb2, so far cannot get remote working.  Box is model 941.  Unit is 24022 LF Rev E1A3.  White sticker on unit says 0107 8669106

only have lirc0 and it looks almost like this is the 'correct' one?
dmesg | grep lirc
[   70.844000] lirc_dev: IR Remote Control driver registered, at major 61 
[   72.036000] lirc_i2c: chip 0x10005 found @ 0x18 (Hauppauge IR)
[   72.036000] lirc_dev: lirc_register_plugin: sample_rate: 10

lsmod | grep lirc
lirc_i2c               11268  2 
lirc_dev               15860  1 lirc_i2c
i2c_core               26112  11 cx88xx,ivtv,bttv,i2c_algo_bit,lirc_i2c,wm8775,tuner,cx25840,pvrusb2,tveeprom,nvidia

ls -l /dev/lir*
crw-rw---- 1 root root 61, 0 2007-12-01 00:23 /dev/lirc0
srw-rw-rw- 1 root root     0 2007-12-01 00:23 /dev/lircd

ps -eaf | grep lir
root      6340     2  0 Dec01 ?        00:00:03 [lirc_dev]
root      6356     1  0 Dec01 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0

irw
<pressing buttons, no output>


dpkg -l lirc
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                         Version                      Description
+++-============================-============================-========================================================================
ii  lirc                         0.8.2-0ubuntu8               Linux Infra-red Remote Control support

which lircd
/usr/sbin/lircd

lircd -v
lircd 0.8.2

uname -a
Linux mythbuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

lsmod
Module                  Size  Used by
cpufreq_stats           7232  0 
freq_table              5792  1 cpufreq_stats
cx8800                 34944  0 
cx88xx                 68132  1 cx8800
ivtv                  134928  0 
bttv                  177012  0 
video_buf              26244  3 cx8800,cx88xx,bttv
ir_common              35460  2 cx88xx,bttv
compat_ioctl32          2304  2 cx8800,bttv
i2c_algo_bit            7428  3 cx88xx,ivtv,bttv
btcx_risc               5896  3 cx8800,cx88xx,bttv
lirc_i2c               11268  2 
lirc_dev               15860  1 lirc_i2c
af_packet              24840  2 
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ipv6                  273892  110 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
container               5504  0 
video                  18060  0 
battery                11012  0 
sbp2                   24072  1 
lp                     12580  0 
wm8775                  7180  0 
tuner                  63144  0 
cx25840                26640  0 
pvrusb2               143700  1 
cx2341x                13316  2 ivtv,pvrusb2
videodev               29312  5 cx8800,cx88xx,ivtv,bttv,pvrusb2
v4l2_common            18432  10 cx8800,cx88xx,ivtv,bttv,wm8775,tuner,cx25840,pvrusb2,cx2341x,videodev
v4l1_compat            15364  4 ivtv,bttv,pvrusb2,videodev
tveeprom               16784  4 cx88xx,ivtv,bttv,pvrusb2
snd_maestro3           26628  1 
snd_ac97_codec        100644  1 snd_maestro3
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
ehci_hcd               36492  0 
ohci_hcd               22916  0 
snd_seq_dummy           4740  0 
pcmcia                 41388  0 
snd_seq_oss            33152  0 
parport_pc             37412  1 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
parport                37448  2 lp,parport_pc
irda                  202300  0 
crc_ccitt               3072  1 irda
pcspkr                  4224  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               4716468  36 
snd                    54660  12 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               8068  0 
soundcore               8800  1 snd
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               26112  11 cx88xx,ivtv,bttv,i2c_algo_bit,lirc_i2c,wm8775,tuner,cx25840,pvrusb2,tveeprom,nvidia
psmouse                39952  0 
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
usbhid                 29536  0 
hid                    28928  1 usbhid
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  5 
ata_generic             8452  0 
uhci_hcd               26640  0 
usbcore               138632  6 pvrusb2,ehci_hcd,ohci_hcd,usbhid,uhci_hcd
ohci1394               36528  1 
ieee1394               96312  2 sbp2,ohci1394
ata_piix               17540  3 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
3c59x                  46632  0 
mii                     6528  1 3c59x
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


help?

---

### Post by superm1 on 2007-12-05
> **bluec99 said:**
> Running mythbuntu with the pvr-usb2, so far cannot get remote working.  Box is model 941.  Unit is 24022 LF Rev E1A3.  White sticker on unit says 0107 8669106

only have lirc0 and it looks almost like this is the 'correct' one?
dmesg | grep lirc
[   70.844000] lirc_dev: IR Remote Control driver registered, at major 61 
[   72.036000] lirc_i2c: chip 0x10005 found @ 0x18 (Hauppauge IR)
[   72.036000] lirc_dev: lirc_register_plugin: sample_rate: 10

lsmod | grep lirc
lirc_i2c               11268  2 
lirc_dev               15860  1 lirc_i2c
i2c_core               26112  11 cx88xx,ivtv,bttv,i2c_algo_bit,lirc_i2c,wm8775,tuner,cx25840,pvrusb2,tveeprom,nvidia

ls -l /dev/lir*
crw-rw---- 1 root root 61, 0 2007-12-01 00:23 /dev/lirc0
srw-rw-rw- 1 root root     0 2007-12-01 00:23 /dev/lircd

ps -eaf | grep lir
root      6340     2  0 Dec01 ?        00:00:03 [lirc_dev]
root      6356     1  0 Dec01 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0

irw
<pressing buttons, no output>


dpkg -l lirc
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                         Version                      Description
+++-============================-============================-========================================================================
ii  lirc                         0.8.2-0ubuntu8               Linux Infra-red Remote Control support

which lircd
/usr/sbin/lircd

lircd -v
lircd 0.8.2

uname -a
Linux mythbuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

lsmod
Module                  Size  Used by
cpufreq_stats           7232  0 
freq_table              5792  1 cpufreq_stats
cx8800                 34944  0 
cx88xx                 68132  1 cx8800
ivtv                  134928  0 
bttv                  177012  0 
video_buf              26244  3 cx8800,cx88xx,bttv
ir_common              35460  2 cx88xx,bttv
compat_ioctl32          2304  2 cx8800,bttv
i2c_algo_bit            7428  3 cx88xx,ivtv,bttv
btcx_risc               5896  3 cx8800,cx88xx,bttv
lirc_i2c               11268  2 
lirc_dev               15860  1 lirc_i2c
af_packet              24840  2 
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ipv6                  273892  110 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
container               5504  0 
video                  18060  0 
battery                11012  0 
sbp2                   24072  1 
lp                     12580  0 
wm8775                  7180  0 
tuner                  63144  0 
cx25840                26640  0 
pvrusb2               143700  1 
cx2341x                13316  2 ivtv,pvrusb2
videodev               29312  5 cx8800,cx88xx,ivtv,bttv,pvrusb2
v4l2_common            18432  10 cx8800,cx88xx,ivtv,bttv,wm8775,tuner,cx25840,pvrusb2,cx2341x,videodev
v4l1_compat            15364  4 ivtv,bttv,pvrusb2,videodev
tveeprom               16784  4 cx88xx,ivtv,bttv,pvrusb2
snd_maestro3           26628  1 
snd_ac97_codec        100644  1 snd_maestro3
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
ehci_hcd               36492  0 
ohci_hcd               22916  0 
snd_seq_dummy           4740  0 
pcmcia                 41388  0 
snd_seq_oss            33152  0 
parport_pc             37412  1 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
parport                37448  2 lp,parport_pc
irda                  202300  0 
crc_ccitt               3072  1 irda
pcspkr                  4224  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               4716468  36 
snd                    54660  12 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               8068  0 
soundcore               8800  1 snd
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               26112  11 cx88xx,ivtv,bttv,i2c_algo_bit,lirc_i2c,wm8775,tuner,cx25840,pvrusb2,tveeprom,nvidia
psmouse                39952  0 
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
usbhid                 29536  0 
hid                    28928  1 usbhid
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  5 
ata_generic             8452  0 
uhci_hcd               26640  0 
usbcore               138632  6 pvrusb2,ehci_hcd,ohci_hcd,usbhid,uhci_hcd
ohci1394               36528  1 
ieee1394               96312  2 sbp2,ohci1394
ata_piix               17540  3 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
3c59x                  46632  0 
mii                     6528  1 3c59x
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


help?
I don't think the PVRUSB2 uses the same driver (there is no external I2C bus afaik).  I'm not actually sure it's supported.  Have you found anything referring to the fact that it should be?

---

### Post by bluec99 on 2007-12-05
As far as i2c in the 24xxx box:
[http://www.isely.net/pvrusb2/usage.html](http://www.isely.net/pvrusb2/usage.html)
"The IR receiver within the model 24xxx series devices is some glue logic and firmware within the FX2 microcontroller that is operating the device. There's no actual I2C interface and thus no way for any external chip-level driver to reach into the pvrusb2 driver and operate the part. The pvrusb2 driver handles this situation by operating this feature itself and presenting the results as an emulation of the I2C chip that would otherwise be present in 29xxx devices. Thus, even though 24xxx devices don't actually have the expected chip, everything still works properly and outside logic (e.g. lirc) still thinks it is talking to a normal Hauppauge I2C-based IR receiver."

The Hauppauge bundled remote shows model number A415-HPG-A inside the battery compartment.

Then:
[http://wiki.ljackson.us/Lirc](http://wiki.ljackson.us/Lirc)
[http://lircconfig.commandir.com/lircd.conf/?viewremote=237](http://lircconfig.commandir.com/lircd.conf/?viewremote=237)


[http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft](http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft)
"Grey/Black (A415-HPG) Hauppauge remote with the 4 color buttons at the bottom. If you have this remote, the lirc that ships with Edgy will not work. You must compile the CVS version of lirc."
...
"lirc-0.8.1.tar.bz2" while mythbuntu ships with lirc 0.8.2-0ubuntu8.



And can now add testing the latest lirc version to the testing and still no output.
On the troubleshooting front I stopped lircd and tried 'cat /dev/lirc0'.  Never got any output. So i'm still unclear if it's
a) remote just not transmitting (batteries checked out with DMM)
b) IR sensor in box not working
c) pvrusb2<->lirc_i2c handoff




Have you had better experience with the MCE bundle on mythbuntu?

---

### Post by house82 on 2008-09-22
I got my remote to work with 8.04.01.
My PVR USB2 is the 2400 model with IR blaster
I had to add 
```
options pvrusb2 ir_mode=0
```
to /etc/modprobe.d/options to hide the non-working first lirc interface.

---

