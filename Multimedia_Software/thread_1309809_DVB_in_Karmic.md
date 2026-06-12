---
title: "DVB in Karmic"
date: 2009-11-01
forum: Multimedia Software
---

### Post by chuggly on 2009-11-01
Hi all
Upgraded today to 9.10
Using Kaffeine
Scanned for tv channels and found them, but when I go to watch tv I get the following error "Could not open media source"

Any ideas

Regards

Tim

---

### Post by garyjohn80 on 2009-11-01
having simular problem with Kaffeine after upgrade to 9.10.   Can scan channels put when i go to watch a channel i get the error "cannot find demultiplexer plugin for the given media data"

---

### Post by epek on 2009-11-01
I have "just" an old tuning problem with karmic.
see [http://ubuntuforums.org/showthread.php?t=1309831](http://ubuntuforums.org/showthread.php?t=1309831)

You two should provide some more info. What´s your hardware? What does dmesg say?

Since you don´t get data, but can tune, it may still be a driver problem - or your user is no member of the group "video". To be sure, check the logs for strange errors.

---

### Post by xc3RnbFO8P on 2009-11-02
delete

---

### Post by garyjohn80 on 2009-11-02
ok have twice now been able to rescan for channels and then watch tv    but when i restart PC it looses the ability to playback the channels giving the message  "cannot find demultiplexer plugin for the given media data"

I've tried running kaffeine from terminal and am getting the following

gary@gary-desktop:~$ kaffeine
gary@gary-desktop:~$ demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

---

### Post by epek on 2009-11-02
is´nt the demultiplexer part of the kernel driver module?
Please compare lsmod, when it´s working with lsmod after a reboot. Probably something is missing. Also check blacklist form updated installations.

---

### Post by garyjohn80 on 2009-11-02
thanks i'll try and get it working again and post here but i'm kinda new to linux   could you tell me how to "Also check blacklist form updated installations."

thanks

---

### Post by garyjohn80 on 2009-11-02
**ok when working lsmod gives**

gary@gary-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  2 
nls_cp437               5372  2 
vfat                   10716  2 
fat                    51452  1 vfat
binfmt_misc             8356  1 
xt_limit                2176  8 
xt_tcpudp               2780  7 
ipt_LOG                 5344  8 
ipt_MASQUERADE          2204  0 
xt_DSCP                 2844  0 
ipt_REJECT              2812  1 
nf_conntrack_irc        4992  0 
nf_conntrack_ftp        6880  0 
xt_state                1820  6 
mt2060                  4896  2 
snd_hda_codec_realtek   203328  1 
iptable_nat             5500  0 
nf_nat                 17808  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13352  9 iptable_nat,nf_nat
nf_conntrack           67608  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
iptable_mangle          3452  0 
snd_hda_intel          26920  4 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio          84224  1 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_seq_dummy           2656  0 
snd_pcm                75296  5 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_seq_oss            28576  0 
dvb_usb_dib0700        40836  5 
snd_usb_lib            16284  1 snd_usb_audio
dib7000p               16676  1 dvb_usb_dib0700
snd_seq_midi            6432  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi
dib7000m               14560  1 dvb_usb_dib0700
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  1 
dvb_usb                16200  1 dvb_usb_dib0700
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
dvb_core               87364  1 dvb_usb
x_tables               16544  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
dib3000mc              12196  3 dvb_usb_dib0700
snd_timer              22276  2 snd_pcm,snd_seq
psmouse                56180  0 
snd_hwdep               7200  2 snd_hda_codec,snd_usb_audio
nvidia               9586440  36 
dibx000_common          3328  3 dib7000p,dib7000m,dib3000mc
lp                      8964  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 10272  0 
serio_raw               5280  0 
pwc                    81632  0 
agpgart                34988  1 nvidia
dib0070                 7616  1 dvb_usb_dib0700
i2c_nforce2             6784  0 
ppdev                   6688  0 
parport_pc             31940  1 
videodev               36736  1 pwc
v4l1_compat            14496  1 videodev
k8temp                  4188  0 
parport                35340  3 lp,ppdev,parport_pc
snd                    59204  22 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_hwdep,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
hid_microsoft           3328  0 
usbhid                 38208  0 
usb_storage            52544  2 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
floppy                 54916  0 
forcedeth              54152  0 


**when not working ls mod gives**

gary@gary-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  2 
nls_cp437               5372  2 
vfat                   10716  2 
fat                    51452  1 vfat
binfmt_misc             8356  1 
xt_limit                2176  8 
xt_tcpudp               2780  7 
ipt_LOG                 5344  8 
ipt_MASQUERADE          2204  0 
xt_DSCP                 2844  0 
ipt_REJECT              2812  1 
nf_conntrack_irc        4992  0 
nf_conntrack_ftp        6880  0 
xt_state                1820  6 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  3 
snd_usb_audio          84224  1 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_lib            16284  1 snd_usb_audio
iptable_nat             5500  0 
snd_pcm_oss            37920  0 
nf_nat                 17808  2 ipt_MASQUERADE,iptable_nat
mt2060                  4896  2 
snd_mixer_oss          16028  1 snd_pcm_oss
nf_conntrack_ipv4      13352  9 iptable_nat,nf_nat
snd_pcm                75296  4 snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
nf_conntrack           67608  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_seq_midi            6432  0 
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_mangle          3452  0 
dvb_usb_dib0700        40836  5 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dib7000p               16676  1 dvb_usb_dib0700
snd_timer              22276  2 snd_pcm,snd_seq
snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
dib7000m               14560  1 dvb_usb_dib0700
dvb_usb                16200  1 dvb_usb_dib0700
snd_hwdep               7200  2 snd_usb_audio,snd_hda_codec
iptable_filter          3100  1 
dvb_core               87364  1 dvb_usb
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
pwc                    81632  0 
snd                    59204  21 snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
dib3000mc              12196  3 dvb_usb_dib0700
nvidia               9586440  36 
soundcore               7264  1 snd
dibx000_common          3328  3 dib7000p,dib7000m,dib3000mc
x_tables               16544  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
videodev               36736  1 pwc
i2c_nforce2             6784  0 
dib0070                 7616  1 dvb_usb_dib0700
ppdev                   6688  0 
agpgart                34988  1 nvidia
psmouse                56180  0 
lp                      8964  0 
v4l1_compat            14496  1 videodev
parport_pc             31940  1 
serio_raw               5280  0 
k8temp                  4188  0 
joydev                 10272  0 
parport                35340  3 ppdev,lp,parport_pc
hid_microsoft           3328  0 
usbhid                 38208  0 
floppy                 54916  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
forcedeth              54152  0 
usb_storage            52544  2 
gary@gary-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  2 
nls_cp437               5372  2 
vfat                   10716  2 
fat                    51452  1 vfat
binfmt_misc             8356  1 
xt_limit                2176  8 
xt_tcpudp               2780  7 
ipt_LOG                 5344  8 
ipt_MASQUERADE          2204  0 
xt_DSCP                 2844  0 
ipt_REJECT              2812  1 
nf_conntrack_irc        4992  0 
nf_conntrack_ftp        6880  0 
xt_state                1820  6 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  3 
snd_usb_audio          84224  1 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_lib            16284  1 snd_usb_audio
iptable_nat             5500  0 
snd_pcm_oss            37920  0 
nf_nat                 17808  2 ipt_MASQUERADE,iptable_nat
mt2060                  4896  2 
snd_mixer_oss          16028  1 snd_pcm_oss
nf_conntrack_ipv4      13352  9 iptable_nat,nf_nat
snd_pcm                75296  4 snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
nf_conntrack           67608  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_seq_midi            6432  0 
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_mangle          3452  0 
dvb_usb_dib0700        40836  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dib7000p               16676  1 dvb_usb_dib0700
snd_timer              22276  2 snd_pcm,snd_seq
snd_rawmidi            22208  2 snd_usb_lib,snd_seq_midi
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
dib7000m               14560  1 dvb_usb_dib0700
dvb_usb                16200  1 dvb_usb_dib0700
snd_hwdep               7200  2 snd_usb_audio,snd_hda_codec
iptable_filter          3100  1 
dvb_core               87364  1 dvb_usb
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
pwc                    81632  0 
snd                    59204  21 snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
dib3000mc              12196  3 dvb_usb_dib0700
nvidia               9586440  36 
soundcore               7264  1 snd
dibx000_common          3328  3 dib7000p,dib7000m,dib3000mc
x_tables               16544  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
videodev               36736  1 pwc
i2c_nforce2             6784  0 
dib0070                 7616  1 dvb_usb_dib0700
ppdev                   6688  0 
agpgart                34988  1 nvidia
psmouse                56180  0 
lp                      8964  0 
v4l1_compat            14496  1 videodev
parport_pc             31940  1 
serio_raw               5280  0 
k8temp                  4188  0 
joydev                 10272  0 
parport                35340  3 ppdev,lp,parport_pc
hid_microsoft           3328  0 
usbhid                 38208  0 
floppy                 54916  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
forcedeth              54152  0 
usb_storage            52544  2

---

### Post by slaamer on 2009-11-03
Hi all,

I had the same problem after upgrading to 9.10 over the weekend.
**Fixed by installing libxine1-ffmpeg and libavcodec-unstripped-52**.

Works great now.

---

### Post by ramadan on 2009-11-22
> **slaamer said:**
> Hi all,

I had the same problem after upgrading to 9.10 over the weekend.
**Fixed by installing libxine1-ffmpeg and libavcodec-unstripped-52**.

Works great now.

thanks, it works great

---

### Post by Cresho on 2009-12-03
perfect!  works.

---

### Post by Philip Farrugia on 2009-12-05
Anyone having similar problems might like to know how I solved it.
Installing libxine1-all-plugins via synaptic worked for me.
Also found I needed to install linux-firmware-nonfree before I could tune my tv card.

---

### Post by binlinus on 2009-12-13
> **slaamer said:**
> Hi all,

I had the same problem after upgrading to 9.10 over the weekend.
**Fixed by installing libxine1-ffmpeg and libavcodec-unstripped-52**.

Works great now.

Thanks very much for this, slaamer. That did it.

Bin

---

### Post by ahycka on 2009-12-19
> **Philip Farrugia said:**
> Anyone having similar problems might like to know how I solved it.
Installing libxine1-all-plugins via synaptic worked for me.
Also found I needed to install linux-firmware-nonfree before I could tune my tv card.

Thaaaaaaaaaaaaaaaaaaaaaaanks!!!!!!
With that package, after 2 months i can watch my tv!!!!! :D :D :D

Thaaaanks again _o_

---

### Post by comprodtv on 2010-03-22
delete

---

