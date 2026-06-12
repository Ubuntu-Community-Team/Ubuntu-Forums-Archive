---
title: "DVB Avermedia / Phillips wont show up in Kaffeine"
date: 2010-02-24
forum: Multimedia Software
---

### Post by Dikko on 2010-02-24
Hi All,
Not sure what you need to know to help me on this one.  I cant get my DVB tuner card to show in 9.10 worked in 8.04 just fine, different mobo/cpu though.

Have lspci'd for the below:
>  03:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)rmmod saa7134 gives:
> ERROR: Module saa7134 is in use by saa7134_dvb,saa7134_alsaUsing 9.10, AMD Phenom II, Gigabyte MB "GA-MA74GMT-S2H"

If there is anything else I should provide please let me know.

Thanks in advance,
Richard.

---

### Post by Jose Catre-Vandis on 2010-02-24
Output from **dmesg** and **lsmod**

Looks like the right modules are loaded. Have you tried any other way to play dvb tv? Can you scan for channels using the scan tool? Try mplayer if installed if you generate a channels.conf file.

Also what do you see if you start kaffeine from the terminal?

---

### Post by Dikko on 2010-02-25
Thanks for getting back Jose.  As requested here are the outputs.  Tried MythTV does that count?
Also no I can not scan for channels, the source is not in the listings...  I am installing mplayer now, let you know.

dmesg:
> [    7.403868] Linux video capture interface: v2.00
[    7.930644] saa7130/34: v4l2 driver version 0.2.15 loaded
[    7.930937]   alloc irq_desc for 21 on node 0
[    7.930940]   alloc kstat_irqs on node 0
[    7.930948] saa7134 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    7.930954] saa7133[0]: found at 0000:03:07.0, rev: 209, irq: 21, latency: 32, mmio: 0xfdcff000
[    7.930960] saa7133[0]: subsystem: 1461:f01d, board: Avermedia Super 007 [card=117,autodetected]
[    7.930973] saa7133[0]: board init: gpio is 40000
[    7.930979] IRQ 21/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    8.120020] saa7133[0]: i2c eeprom 00: 61 14 1d f0 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    8.120026] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[    8.120031] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 55 ff ff ff ff
[    8.120035] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120040] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 03 02 15 16 ff ff ff ff ff ff
[    8.120044] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120048] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120053] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120057] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120062] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120066] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120070] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120075] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120079] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120084] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120088] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    8.120093] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[    8.539745] __ratelimit: 3 callbacks suppressed
[    8.539748] type=1505 audit(1267018858.004:12): operation="profile_replace" pid=897 name=/usr/share/gdm/guest-session/Xsession
[    8.540167] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[    8.540678] type=1505 audit(1267018858.004:13): operation="profile_replace" pid=898 name=/sbin/dhclient3
[    8.540869] type=1505 audit(1267018858.004:14): operation="profile_replace" pid=898 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.540978] type=1505 audit(1267018858.004:15): operation="profile_replace" pid=898 name=/usr/lib/connman/scripts/dhclient-script
[    8.542883] type=1505 audit(1267018858.014:16): operation="profile_replace" pid=899 name=/usr/bin/evince
[    8.545786] type=1505 audit(1267018858.014:17): operation="profile_replace" pid=899 name=/usr/bin/evince-previewer
[    8.547566] type=1505 audit(1267018858.014:18): operation="profile_replace" pid=899 name=/usr/bin/evince-thumbnailer
[    8.550705] type=1505 audit(1267018858.014:19): operation="profile_replace" pid=901 name=/usr/lib/cups/backend/cups-pdf
[    8.550934] type=1505 audit(1267018858.014:20): operation="profile_replace" pid=901 name=/usr/sbin/cupsd
[    8.552089] type=1505 audit(1267018858.024:21): operation="profile_replace" pid=902 name=/usr/sbin/tcpdump
[    8.710022] tda829x 1-004b: setting tuner address to 60
[    8.764062] lp: driver loaded but no devices found
[    9.000023] tda829x 1-004b: type set to tda8290+75a
[   12.753672] r8169: eth0: link up
[   12.753677] r8169: eth0: link up
[   14.060278] saa7133[0]: dsp access error
[   14.190070] saa7133[0]: registered device video0 [v4l2]
[   14.190084] saa7133[0]: registered device vbi0
[   14.192991] saa7134 ALSA driver for DMA sound loaded
[   14.193000] IRQ 21/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   14.193013] saa7133[0]/alsa: saa7133[0] at 0xfdcff000 irq 21 registered as card -2
[   14.273470] dvb_init() allocating 1 frontend
[   14.390093] DVB: registering new adapter (saa7133[0])
[   14.390097] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)..lsmod:
> Module                  Size  Used by
usb_storage            65952  0 
isofs                  36424  1 
udf                    88136  0 
crc_itu_t               2336  1 udf
binfmt_misc            10220  1 
ppdev                   8232  0 
tda1004x               17956  1 
saa7134_dvb            26860  0 
videobuf_dvb            8452  1 saa7134_dvb
dvb_core              104528  1 videobuf_dvb
saa7134_alsa           14560  1 
tda827x                11492  2 
lp                     11908  0 
parport                40528  2 ppdev,lp
tda8290                15748  1 
tuner                  24520  1 
saa7134               178356  2 saa7134_dvb,saa7134_alsa
ir_common              52740  1 saa7134
v4l2_common            21024  2 tuner,saa7134
videodev               43360  3 tuner,saa7134,v4l2_common
v4l1_compat            16804  1 videodev
v4l2_compat_ioctl32    13344  1 videodev
videobuf_dma_sg        14436  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          21188  3 videobuf_dvb,saa7134,videobuf_dma_sg
amd64_edac_mod         26688  0 
tveeprom               14884  1 saa7134
snd_hda_codec_realtek   277860  1 
i2c_piix4              11728  0 
edac_core              48876  1 amd64_edac_mod
shpchp                 37756  0 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  19 saa7134_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3872  0 
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
usbhid                 43968  0 
r8169                  38884  0 
mii                     6368  1 r8169
floppy                 65192  0 
radeon                684512  2 
ttm                    43056  1 radeon
drm                   193856  4 radeon,ttm
i2c_algo_bit            7076  1 radeon


Running kaffeine:
> kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so


I also noticed last night while looking into why I can't get straight into x without using startx command and a supergrub disk, ck-list-sessions:
> Session1:
    unix-user = '1000'
    realname = 'Richard Lane'
    seat = 'Seat1'
    session-type = ''
    active = FALSE
    x11-display = ''
    x11-display-device = ''
    display-device = '/dev/tty1'
    remote-host-name = ''
    is-local = TRUE
    on-since = '2010-02-24T13:41:30.375866Z'
    login-session-id = '4294967295'
    idle-since-hint = '2010-02-24T13:42:02.001656Z'The active = FALSE says true on my other machine.

Cheers again,
Rick.

---

### Post by Jose Catre-Vandis on 2010-02-25
Well you card is definitely being recognised and drivers being loaded

so give the scan-apps (utils) a try and see if you get a signal and a channel list. I don't know why Kaffeine isn't picking up your card??

And sorry but can't help with your login issue, might be better to create a new thread about it.

---

### Post by steefjeqv on 2010-02-27
Hi,

Is IRQ21 shared ?
If so, you can try using a different PCI slot.

Greetings,
Steven

---

### Post by mpw on 2010-03-22
Hello,

I'm trying to use my video card, too.

All tried software(tvtime, kaffeine, me-tv, mplayer) doesn't recognize my saa7133:

lspci | -i saa7133
```
06:03.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)

```

dmesg | -i saa71
```
[   28.878050] saa7130/34: v4l2 driver version 0.2.15 loaded
[   29.078925] saa7134 0000:06:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   29.078933] saa7133[0]: found at 0000:06:03.0, rev: 208, irq: 19, latency: 181, mmio: 0xb4007800
[   29.078942] saa7133[0]: subsystem: 5168:0307, board: UNKNOWN/GENERIC [card=0,autodetected]
[   29.078958] saa7133[0]: board init: gpio is 10000
[   29.078965] IRQ 19/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   29.236021] saa7133[0]: i2c eeprom 00: 68 51 07 03 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   29.236034] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[   29.236045] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 e7 ff ff ff ff
[   29.236056] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236066] saa7133[0]: i2c eeprom 40: ff 24 00 c2 96 10 05 01 01 16 22 15 ff ff ff ff
[   29.236077] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236088] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236099] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236110] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236121] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236131] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236142] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236153] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236164] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236175] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.236186] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.237171] saa7133[0]: registered device video0 [v4l2]
[   29.237199] saa7133[0]: registered device vbi0
[   29.239519] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   29.239523] saa7134_alsa: Unknown symbol snd_ctl_add
[   29.239658] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   29.239660] saa7134_alsa: Unknown symbol snd_pcm_new
[   29.240426] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   29.240429] saa7134_alsa: Unknown symbol snd_pcm_stop
[   29.240700] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   29.240703] saa7134_alsa: Unknown symbol snd_ctl_new1
[   29.241445] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   29.241448] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   29.241828] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   29.241831] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   29.242220] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   29.242223] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   29.242921] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   29.242923] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   29.243043] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   29.243046] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[   29.258100] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   29.258104] saa7134_alsa: Unknown symbol snd_ctl_add
[   29.258238] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   29.258241] saa7134_alsa: Unknown symbol snd_pcm_new
[   29.258991] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   29.258994] saa7134_alsa: Unknown symbol snd_pcm_stop
[   29.259264] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   29.259267] saa7134_alsa: Unknown symbol snd_ctl_new1
[   29.260025] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   29.260027] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   29.260408] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   29.260410] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   29.260794] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   29.260797] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   29.261494] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   29.261496] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   29.261616] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   29.261619] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[ 1565.804476] saa7134 0000:06:03.0: restoring config space at offset 0xf (was 0x20540100, writing 0x205401ff)
[ 1565.804476] saa7134 0000:06:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xb4007800)
[ 1565.804476] saa7134 0000:06:03.0: restoring config space at offset 0x3 (was 0x0, writing 0xb500)
[ 1565.804476] saa7134 0000:06:03.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900006)
[ 1567.360253] saa7133[0]: board init: gpio is 10000
[ 3425.756475] saa7134 0000:06:03.0: restoring config space at offset 0xf (was 0x20540100, writing 0x205401ff)
[ 3425.756475] saa7134 0000:06:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xb4007800)
[ 3425.756475] saa7134 0000:06:03.0: restoring config space at offset 0x3 (was 0x0, writing 0xb500)
[ 3425.756475] saa7134 0000:06:03.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900006)
[ 3427.316254] saa7133[0]: board init: gpio is 10000
[11513.057663] saa7130/34: v4l2 driver version 0.2.15 loaded
[11513.057705] saa7133[0]: found at 0000:06:03.0, rev: 208, irq: 19, latency: 181, mmio: 0xb4007800
[11513.057713] saa7133[0]: subsystem: 5168:0307, board: ADS Tech Instant TV (saa7135) [card=58,insmod option]
[11513.057729] saa7133[0]: board init: gpio is 10000
[11513.057734] IRQ 19/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[11513.208036] saa7133[0]: i2c eeprom 00: 68 51 07 03 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[11513.208063] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[11513.208087] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 e7 ff ff ff ff
[11513.208111] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208135] saa7133[0]: i2c eeprom 40: ff 24 00 c2 96 10 05 01 01 16 22 15 ff ff ff ff
[11513.208158] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208182] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208205] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208229] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208252] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208276] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208299] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208323] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208346] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208370] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.208393] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[11513.468267] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[11518.352141] saa7133[0]: registered device video0 [v4l2]
[11518.352202] saa7133[0]: registered device vbi0
[11518.396075] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[11518.396085] saa7134_alsa: Unknown symbol snd_ctl_add
[11518.396381] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[11518.396387] saa7134_alsa: Unknown symbol snd_pcm_new
[11518.397988] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[11518.397994] saa7134_alsa: Unknown symbol snd_pcm_stop
[11518.398586] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[11518.398592] saa7134_alsa: Unknown symbol snd_ctl_new1
[11518.400141] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[11518.400147] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[11518.400961] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[11518.400967] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[11518.401809] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[11518.401816] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[11518.403341] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[11518.403347] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[11518.403612] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[11518.403618] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[11518.411554] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[11518.411561] saa7134_alsa: Unknown symbol snd_ctl_add
[11518.411856] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[11518.411862] saa7134_alsa: Unknown symbol snd_pcm_new
[11518.415164] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[11518.415171] saa7134_alsa: Unknown symbol snd_pcm_stop
[11518.415763] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[11518.415768] saa7134_alsa: Unknown symbol snd_ctl_new1
[11518.417318] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[11518.417324] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[11518.418143] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[11518.418149] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[11518.418989] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[11518.418996] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[11518.420547] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[11518.420553] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[11518.420818] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[11518.420824] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step

```

Any ideas?

Thanks für help.

bye
MPW

---

### Post by adri17171717 on 2010-03-29
I also I have the same problem and 
Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

zap tv 2202

---

### Post by tomlohave on 2010-05-10
for mpw :


patch waiting for inclusion at linuxtv.org :
see :

[https://patchwork.kernel.org/patch/73628/]("https://patchwork.kernel.org/patch/73628/")

cheers,

---

