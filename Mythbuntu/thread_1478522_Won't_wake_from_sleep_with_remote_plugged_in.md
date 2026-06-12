---
title: "Won't wake from sleep with remote plugged in"
date: 2010-05-09
forum: Mythbuntu
---

### Post by russell5 on 2010-05-09
So i have been trying to do auto wakeup shutdown on my mythbuntu  10.04 box. Upgraded to 10.04 this weekend but this was happening before also. 

I have tested the auto function as i can set a time for it to wake up and it will work. 

My issue is that when i have my ir sensor plugged in it won't wake form sleep. 

So i put it into suspend from either the command line of from the xfce menu and it goes to sleep. I then hit the power button to wake it and you can see the video initialize then just get a blinking cursor in the top left corner. Never wakes up just sits there. The odd this is when i unplug my ir sensor and put it to suspend it has no problems waking up.

Any help would be greatly appreciated.  

I have a rosewill rrc-127 remote. heres the link. 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16880101003](http://www.newegg.com/Product/Product.aspx?Item=N82E16880101003)

Here is how the remote shows up in lsusb

```
Bus 003 Device 003: ID 1784:0011 TopSeed Technology Corp. 
```

Here is my pm-suspend.log
```
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Sun May  9 09:57:58 EDT 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux mythtv 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
Module                  Size  Used by
lirc_serial             9763  0
nfsd                  238935  13
exportfs                3437  1 nfsd
snd_hda_codec_realtek   203168  1
nfs                   264702  0
lockd                  64849  2 nfsd,nfs
nfs_acl                 2245  2 nfsd,nfs
auth_rpcgss            33735  2 nfsd,nfs
snd_hda_intel          21877  2
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0
sunrpc                193181  13 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
tuner_simple           13577  2
tuner_types            14233  1 tuner_simple
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
wm8775                  2873  2
snd_seq_dummy           1338  0
tda9887                 9589  1
snd_seq_oss            26726  0
snd_seq_midi            4557  0
tda8290                12092  0
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tuner                  20412  3
cx25840                25839  2
snd                    54148  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0
fbcon                  35102  71
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
lirc_mceusb            12068  1
nvidia               7087672  26
vga16fb                11385  1
vgastate                8961  1 vga16fb
psmouse                63245  0
lirc_dev                8890  4 lirc_serial,lirc_mceusb
parport_pc             25962  1
lp                      7028  0
ivtv                  137807  0
i2c_algo_bit            5028  1 ivtv
cx2341x                12469  1 ivtv
v4l2_common            15431  5 wm8775,tuner,cx25840,ivtv,cx2341x
videodev               34361  5 wm8775,tuner,cx25840,ivtv,v4l2_common
v4l1_compat            13251  1 videodev
serio_raw               3978  0
tveeprom               11102  1 ivtv
via_agp                 5310  1
agpgart                31724  2 nvidia,via_agp
shpchp                 28820  0
soundcore               6620  2 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_viapro              5573  0
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0
hid                    67032  1 usbhid
floppy                 53016  0
pata_via                7272  0
via_rhine              19154  0
mii                     4381  1 via_rhine
sata_via                6945  3
             total       used       free     shared    buffers     cached
Mem:       1543652     534412    1009240          0      49832     244388
-/+ buffers/cache:     240192    1303460
Swap:      3084440          0    3084440
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Sun May  9 09:57:59 EDT 2010: performing suspend
```

```
MythTV Version   : 24291
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 56
Library API      : 0.23.20100314-1
QT Version       : 4.5.2
Options compiled in:
 linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libudev using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

```
```
Linux mythtv 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```

---

