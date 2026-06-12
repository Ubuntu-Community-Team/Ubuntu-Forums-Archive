---
title: "if u can fix my no sounds problem your are a pro!!"
date: 2009-10-03
forum: Multimedia Software
---

### Post by shkdwn on 2009-10-03
ok now i have been installing ubuntu 4-5 time each time after a reboot or my system froze
for no reason my sound is gone!! my pc speaker seem to be on when i shutdown my pc
it making beeping song . i would love to love this ubuntu but it does not love me .


need some serius helps even in irc channel there not able to help me
every thing is on no mute!!!!!


help help help or i just gonna format ubuntu for good!!!


infos

Ubuntu 9.04 in proscess to upgrade to 9.10

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
06:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem (rev 01)
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

---

### Post by Zeliwin on 2009-10-03
I had the same problem. And here is the fix for you man.  Enjoy.

[http://moderngeek.com/node/10](http://moderngeek.com/node/10)

---

### Post by shkdwn on 2009-10-13
> **Zeliwin said:**
> I had the same problem. And here is the fix for you man.  Enjoy.

[http://moderngeek.com/node/10](http://moderngeek.com/node/10)



nope not working!!!!!

---

### Post by shkdwn on 2009-10-13
my sounds work fine until that day when i boot up and i lost sounds

---

### Post by shkdwn on 2009-10-13
olivier@olivier-desktop:~$ sudo killall pulseaudio
olivier@olivier-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/olivier/.gvfs
      Output information may be incomplete.
Terminating processes: 2430lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/olivier/.gvfs
      Output information may be incomplete.
 2463lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/olivier/.gvfs
      Output information may be incomplete.
 2488lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/olivier/.gvfs
      Output information may be incomplete.
 2518lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/olivier/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 2550lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/olivier/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 2579(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/olivier/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 2579(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

---

### Post by shkdwn on 2009-10-13
alsa-firmware-1.0.16/hdsploader/multiface_firmware.dat
alsa-firmware-1.0.16/mixartloader/
alsa-firmware-1.0.16/mixartloader/miXart8.xlx
alsa-firmware-1.0.16/mixartloader/miXart8AES.xlx
alsa-firmware-1.0.16/mixartloader/Makefile.in
alsa-firmware-1.0.16/mixartloader/README
alsa-firmware-1.0.16/mixartloader/miXart.conf
alsa-firmware-1.0.16/mixartloader/Makefile.am
alsa-firmware-1.0.16/mixartloader/miXart8.elf
alsa-firmware-1.0.16/vxloader/
alsa-firmware-1.0.16/vxloader/x1_1_vx2.rbt
alsa-firmware-1.0.16/vxloader/bd563v2.boot
alsa-firmware-1.0.16/vxloader/bx_1_vxp.b56
alsa-firmware-1.0.16/vxloader/vxpocket.conf
alsa-firmware-1.0.16/vxloader/l_1_vp4.d56
alsa-firmware-1.0.16/vxloader/Makefile.in
alsa-firmware-1.0.16/vxloader/x1_1_vp4.rbt
alsa-firmware-1.0.16/vxloader/l_1_vxp.d56
alsa-firmware-1.0.16/vxloader/bd56002.boot
alsa-firmware-1.0.16/vxloader/vx222.conf
alsa-firmware-1.0.16/vxloader/toxlx.c
alsa-firmware-1.0.16/vxloader/l_1_v22.d56
alsa-firmware-1.0.16/vxloader/README
alsa-firmware-1.0.16/vxloader/vxboard.conf
alsa-firmware-1.0.16/vxloader/Makefile.am
alsa-firmware-1.0.16/vxloader/bx_1_vp4.b56
alsa-firmware-1.0.16/vxloader/vxp440.conf
alsa-firmware-1.0.16/vxloader/x1_1_vxp.rbt
alsa-firmware-1.0.16/vxloader/bd563s3.boot
alsa-firmware-1.0.16/vxloader/l_1_vx2.d56
alsa-firmware-1.0.16/vxloader/x1_2_v22.rbt
alsa-firmware-1.0.16/usx2yloader/
alsa-firmware-1.0.16/usx2yloader/us224.rbt
alsa-firmware-1.0.16/usx2yloader/tascam_loader.asm
alsa-firmware-1.0.16/usx2yloader/us122.rbt
alsa-firmware-1.0.16/usx2yloader/Makefile.in
alsa-firmware-1.0.16/usx2yloader/us428.prepad
alsa-firmware-1.0.16/usx2yloader/an2131.asm
alsa-firmware-1.0.16/usx2yloader/us428.conf
alsa-firmware-1.0.16/usx2yloader/tascam_loader.ihx
alsa-firmware-1.0.16/usx2yloader/README
alsa-firmware-1.0.16/usx2yloader/us122fw.ihx
alsa-firmware-1.0.16/usx2yloader/us224.prepad
alsa-firmware-1.0.16/usx2yloader/us428fw.ihx
alsa-firmware-1.0.16/usx2yloader/us122.prepad
alsa-firmware-1.0.16/usx2yloader/Makefile.am
alsa-firmware-1.0.16/usx2yloader/us224.conf
alsa-firmware-1.0.16/usx2yloader/us122.conf
alsa-firmware-1.0.16/usx2yloader/us224fw.ihx
alsa-firmware-1.0.16/usx2yloader/us428.rbt
alsa-firmware-1.0.16/config.guess
alsa-firmware-1.0.16/README
alsa-firmware-1.0.16/Makefile.am
alsa-firmware-1.0.16/aclocal.m4
alsa-firmware-1.0.16/COPYING
alsa-firmware-1.0.16/korg1212/
alsa-firmware-1.0.16/korg1212/Makefile.in
alsa-firmware-1.0.16/korg1212/k1212.dsp
alsa-firmware-1.0.16/korg1212/Makefile.am
alsa-firmware-1.0.16/sb16/
alsa-firmware-1.0.16/sb16/sb16_csp_codecs.h
alsa-firmware-1.0.16/sb16/Makefile.in
alsa-firmware-1.0.16/sb16/Makefile.am
alsa-firmware-1.0.16/sb16/fw_writer.c
alsa-firmware-1.0.16/missing
alsa-firmware-1.0.16/install-sh
alsa-firmware-1.0.16/config.sub
alsa-firmware-1.0.16/aica/
alsa-firmware-1.0.16/aica/aica_firmware.bin
alsa-firmware-1.0.16/aica/Makefile.in
alsa-firmware-1.0.16/aica/Dreamcast_sound.txt
alsa-firmware-1.0.16/aica/license.txt
alsa-firmware-1.0.16/aica/Makefile.am
alsa-firmware-1.0.16/echoaudio/
alsa-firmware-1.0.16/echoaudio/Makefile.in
alsa-firmware-1.0.16/echoaudio/DSP/
alsa-firmware-1.0.16/echoaudio/DSP/Echo3gDSP.c
alsa-firmware-1.0.16/echoaudio/DSP/IndigoIODSP.c
alsa-firmware-1.0.16/echoaudio/DSP/Gina24_361DSP.c
alsa-firmware-1.0.16/echoaudio/DSP/LoaderDSP.c
alsa-firmware-1.0.16/echoaudio/DSP/Mona361DSP.c
alsa-firmware-1.0.16/echoaudio/DSP/MiaDSP.c
alsa-firmware-1.0.16/echoaudio/DSP/Darla24DSP.c
alsa-firmware-1.0.16/echoaudio/DSP/Darla20DSP.c
alsa-firmware-1.0.16/echoaudio/DSP/MonaDSP.c
alsa-firmware-1.0.16/echoaudio/DSP/Layla24DSP.c
alsa-firmware-1.0.16/echoaudio/DSP/Layla20DSP.c
alsa-firmware-1.0.16/echoaudio/DSP/IndigoDSP.c
alsa-firmware-1.0.16/echoaudio/DSP/Gina20DSP.c
alsa-firmware-1.0.16/echoaudio/DSP/IndigoDJDSP.c
alsa-firmware-1.0.16/echoaudio/DSP/Gina24DSP.c
alsa-firmware-1.0.16/echoaudio/ASIC/
alsa-firmware-1.0.16/echoaudio/ASIC/3G_ASIC.c
alsa-firmware-1.0.16/echoaudio/ASIC/Gina24ASIC.c
alsa-firmware-1.0.16/echoaudio/ASIC/Mona1ASIC48.c
alsa-firmware-1.0.16/echoaudio/ASIC/Layla24_2A_ASIC.c
alsa-firmware-1.0.16/echoaudio/ASIC/Mona2ASIC.c
alsa-firmware-1.0.16/echoaudio/ASIC/LaylaASIC.c
alsa-firmware-1.0.16/echoaudio/ASIC/Mona1ASIC96.c
alsa-firmware-1.0.16/echoaudio/ASIC/Layla24_2S_ASIC.c
alsa-firmware-1.0.16/echoaudio/ASIC/Gina24ASIC_361.c
alsa-firmware-1.0.16/echoaudio/ASIC/Mona1ASIC48_361.c
alsa-firmware-1.0.16/echoaudio/ASIC/Mona1ASIC96_361.c
alsa-firmware-1.0.16/echoaudio/ASIC/Layla24_1ASIC.c
alsa-firmware-1.0.16/echoaudio/Makefile.am
alsa-firmware-1.0.16/echoaudio/fw_writer.c
olivier@olivier-desktop:~$ tar -xvf /home/olivier/alsa-utils-1.0.16.tar.bz2
alsa-utils-1.0.16/
alsa-utils-1.0.16/ABOUT-NLS
alsa-utils-1.0.16/ChangeLog
alsa-utils-1.0.16/depcomp
alsa-utils-1.0.16/speaker-test/
alsa-utils-1.0.16/speaker-test/readme.txt
alsa-utils-1.0.16/speaker-test/Makefile.in
alsa-utils-1.0.16/speaker-test/speaker-test.1
alsa-utils-1.0.16/speaker-test/Makefile.am
alsa-utils-1.0.16/speaker-test/pink.c
alsa-utils-1.0.16/speaker-test/speaker-test.c
alsa-utils-1.0.16/speaker-test/samples/
alsa-utils-1.0.16/speaker-test/samples/sample_map.csv
alsa-utils-1.0.16/speaker-test/samples/Makefile.in
alsa-utils-1.0.16/speaker-test/samples/Noise.wav
alsa-utils-1.0.16/speaker-test/samples/Side_Right.wav
alsa-utils-1.0.16/speaker-test/samples/Front_Left.wav
alsa-utils-1.0.16/speaker-test/samples/Front_Center.wav
alsa-utils-1.0.16/speaker-test/samples/Front_Right.wav
alsa-utils-1.0.16/speaker-test/samples/Rear_Center.wav
alsa-utils-1.0.16/speaker-test/samples/Rear_Left.wav
alsa-utils-1.0.16/speaker-test/samples/Side_Left.wav
alsa-utils-1.0.16/speaker-test/samples/Makefile.am
alsa-utils-1.0.16/speaker-test/samples/Rear_Right.wav
alsa-utils-1.0.16/speaker-test/pink.h
alsa-utils-1.0.16/alsaconf/
alsa-utils-1.0.16/alsaconf/alsaconf.in
alsa-utils-1.0.16/alsaconf/Makefile.in
alsa-utils-1.0.16/alsaconf/alsaconf.8
alsa-utils-1.0.16/alsaconf/po/
alsa-utils-1.0.16/alsaconf/po/Makefile.in
alsa-utils-1.0.16/alsaconf/po/ja.po
alsa-utils-1.0.16/alsaconf/po/ru.po
alsa-utils-1.0.16/alsaconf/Makefile.am
alsa-utils-1.0.16/alsaconf/alsaconf.fr.8
alsa-utils-1.0.16/mkinstalldirs
alsa-utils-1.0.16/TODO
alsa-utils-1.0.16/acinclude.m4
alsa-utils-1.0.16/configure.in
alsa-utils-1.0.16/seq/
alsa-utils-1.0.16/seq/aseqnet/
alsa-utils-1.0.16/seq/aseqnet/aseqnet.c
alsa-utils-1.0.16/seq/aseqnet/Makefile.in
alsa-utils-1.0.16/seq/aseqnet/aseqnet.1
alsa-utils-1.0.16/seq/aseqnet/Makefile.am
alsa-utils-1.0.16/seq/aseqnet/README.aseqnet
alsa-utils-1.0.16/seq/aplaymidi/
alsa-utils-1.0.16/seq/aplaymidi/aplaymidi.c
alsa-utils-1.0.16/seq/aplaymidi/Makefile.in
alsa-utils-1.0.16/seq/aplaymidi/arecordmidi.1
alsa-utils-1.0.16/seq/aplaymidi/Makefile.am
alsa-utils-1.0.16/seq/aplaymidi/arecordmidi.c
alsa-utils-1.0.16/seq/aplaymidi/aplaymidi.1
alsa-utils-1.0.16/seq/aconnect/
alsa-utils-1.0.16/seq/aconnect/aconnect.1
alsa-utils-1.0.16/seq/aconnect/Makefile.in
alsa-utils-1.0.16/seq/aconnect/README.aconnect
alsa-utils-1.0.16/seq/aconnect/Makefile.am
alsa-utils-1.0.16/seq/aconnect/aconnect.c
alsa-utils-1.0.16/seq/Makefile.in
alsa-utils-1.0.16/seq/aseqdump/
alsa-utils-1.0.16/seq/aseqdump/aseqdump.1
alsa-utils-1.0.16/seq/aseqdump/Makefile.in
alsa-utils-1.0.16/seq/aseqdump/Makefile.am
alsa-utils-1.0.16/seq/aseqdump/aseqdump.c
alsa-utils-1.0.16/seq/Makefile.am
alsa-utils-1.0.16/hgcompile
alsa-utils-1.0.16/INSTALL
alsa-utils-1.0.16/configure
alsa-utils-1.0.16/Makefile.in
alsa-utils-1.0.16/amixer/
alsa-utils-1.0.16/amixer/amixer.h
alsa-utils-1.0.16/amixer/amixer.c
alsa-utils-1.0.16/amixer/Makefile.in
alsa-utils-1.0.16/amixer/amixer.1
alsa-utils-1.0.16/amixer/Makefile.am
alsa-utils-1.0.16/amidi/
alsa-utils-1.0.16/amidi/amidi.c
alsa-utils-1.0.16/amidi/amidi.1
alsa-utils-1.0.16/amidi/Makefile.in
alsa-utils-1.0.16/amidi/Makefile.am
alsa-utils-1.0.16/config.guess
alsa-utils-1.0.16/m4/
alsa-utils-1.0.16/m4/gettext.m4
alsa-utils-1.0.16/m4/ulonglong.m4
alsa-utils-1.0.16/m4/xsize.m4
alsa-utils-1.0.16/m4/longdouble.m4
alsa-utils-1.0.16/m4/inttypes_h.m4
alsa-utils-1.0.16/m4/Makefile.in
alsa-utils-1.0.16/m4/lcmessage.m4
alsa-utils-1.0.16/m4/lib-link.m4
alsa-utils-1.0.16/m4/progtest.m4
alsa-utils-1.0.16/m4/inttypes-h.m4
alsa-utils-1.0.16/m4/signed.m4
alsa-utils-1.0.16/m4/lib-prefix.m4
alsa-utils-1.0.16/m4/glibc2.m4
alsa-utils-1.0.16/m4/longlong.m4
alsa-utils-1.0.16/m4/inttypes-pri.m4
alsa-utils-1.0.16/m4/stdint_h.m4
alsa-utils-1.0.16/m4/intdiv0.m4
alsa-utils-1.0.16/m4/wint_t.m4
alsa-utils-1.0.16/m4/uintmax_t.m4
alsa-utils-1.0.16/m4/glibc21.m4
alsa-utils-1.0.16/m4/lock.m4
alsa-utils-1.0.16/m4/wchar_t.m4
alsa-utils-1.0.16/m4/printf-posix.m4
alsa-utils-1.0.16/m4/lib-ld.m4
alsa-utils-1.0.16/m4/iconv.m4
alsa-utils-1.0.16/m4/Makefile.am
alsa-utils-1.0.16/m4/intmax.m4
alsa-utils-1.0.16/m4/po.m4
alsa-utils-1.0.16/m4/codeset.m4
alsa-utils-1.0.16/m4/nls.m4
alsa-utils-1.0.16/m4/size_max.m4
alsa-utils-1.0.16/m4/visibility.m4
alsa-utils-1.0.16/README
alsa-utils-1.0.16/config.rpath
alsa-utils-1.0.16/utils/
alsa-utils-1.0.16/utils/buildrpm
alsa-utils-1.0.16/utils/Makefile.in
alsa-utils-1.0.16/utils/alsa-utils.spec.in
alsa-utils-1.0.16/utils/Makefile.am
alsa-utils-1.0.16/po/
alsa-utils-1.0.16/po/en@quot.header
alsa-utils-1.0.16/po/alsa-utils.pot
alsa-utils-1.0.16/po/stamp-po
alsa-utils-1.0.16/po/boldquot.sed
alsa-utils-1.0.16/po/remove-potcdate.sin
alsa-utils-1.0.16/po/Makefile.in.in
alsa-utils-1.0.16/po/POTFILES.in
alsa-utils-1.0.16/po/ja.po
alsa-utils-1.0.16/po/Rules-quot
alsa-utils-1.0.16/po/quot.sed
alsa-utils-1.0.16/po/insert-header.sin
alsa-utils-1.0.16/po/en@boldquot.header
alsa-utils-1.0.16/po/Makevars
alsa-utils-1.0.16/po/LINGUAS
alsa-utils-1.0.16/po/ja.gmo
alsa-utils-1.0.16/aplay/
alsa-utils-1.0.16/aplay/arecord.1
alsa-utils-1.0.16/aplay/Makefile.in
alsa-utils-1.0.16/aplay/Makefile.am
alsa-utils-1.0.16/aplay/aplay.c
alsa-utils-1.0.16/aplay/aplay.1
alsa-utils-1.0.16/aplay/formats.h
alsa-utils-1.0.16/iecset/
alsa-utils-1.0.16/iecset/iecset.1
alsa-utils-1.0.16/iecset/Makefile.in
alsa-utils-1.0.16/iecset/Makefile.am
alsa-utils-1.0.16/iecset/iecset.c
alsa-utils-1.0.16/iecset/iecbits.c
alsa-utils-1.0.16/Makefile.am
alsa-utils-1.0.16/aclocal.m4
alsa-utils-1.0.16/include/
alsa-utils-1.0.16/include/Makefile.in
alsa-utils-1.0.16/include/gettext.h
alsa-utils-1.0.16/include/aconfig.h.in
alsa-utils-1.0.16/include/version.h
alsa-utils-1.0.16/include/Makefile.am
alsa-utils-1.0.16/COPYING
alsa-utils-1.0.16/alsactl/
alsa-utils-1.0.16/alsactl/alsactl.1
alsa-utils-1.0.16/alsactl/alsactl.c
alsa-utils-1.0.16/alsactl/Makefile.in
alsa-utils-1.0.16/alsactl/names.c
alsa-utils-1.0.16/alsactl/Makefile.am
alsa-utils-1.0.16/alsactl/state.c
alsa-utils-1.0.16/alsactl/alsactl.h
alsa-utils-1.0.16/alsamixer/
alsa-utils-1.0.16/alsamixer/alsamixer.1
alsa-utils-1.0.16/alsamixer/Makefile.in
alsa-utils-1.0.16/alsamixer/alsamixer.c
alsa-utils-1.0.16/alsamixer/README
alsa-utils-1.0.16/alsamixer/Makefile.am
alsa-utils-1.0.16/missing
alsa-utils-1.0.16/install-sh
alsa-utils-1.0.16/config.sub
olivier@olivier-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-wqy-zenhei binutils-static
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.4 libstdc++6-4.4-dev
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc
  libstdc++6-4.4-dbg libstdc++6-4.4-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.4 libstdc++6-4.4-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,773kB of archives.
After this operation, 22.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main libstdc++6-4.4-dev 4.4.1-4ubuntu7 [1,490kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main g++-4.4 4.4.1-4ubuntu7 [4,701kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main g++ 4:4.4.1-1ubuntu2 [1,446B]   
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main dpkg-dev 1.15.4ubuntu2 [573kB]  
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main build-essential 11.4 [7,172B]   
Fetched 6,773kB in 19s (350kB/s)                                               
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 219242 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.1-4ubuntu7_i386.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.1-4ubuntu7_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.4ubuntu2_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Processing triggers for man-db ...
Setting up dpkg-dev (1.15.4ubuntu2) ...
Setting up libstdc++6-4.4-dev (4.4.1-4ubuntu7) ...
Setting up g++-4.4 (4.4.1-4ubuntu7) ...
Setting up g++ (4:4.4.1-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4) ...
olivier@olivier-desktop:~$ cd /home/olivier/alsa-driver-1.0.16
olivier@olivier-desktop:~/alsa-driver-1.0.16$ ./configure --with-cards=ICH6
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/olivier/alsa-driver-1.0.16
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.31-13-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.31-13-generic
checking for GCC version... ./configure: eval: line 4950: syntax error near unexpected token `)'
./configure: eval: line 4950: `my_compiler_version=4.4.1-4ubuntu7)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.4.1-4ubuntu7) 4.4.1

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... no
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/latency.h... no
Creating <linux/latency.h>...
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... no
Creating a dummy <asm/irq_regs.h>...
checking for kernel linux/seq_file.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.31-13-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.16
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... no
checking for gfp_t... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for which soundcards to compile driver for... configure: error: Unknown soundcard ICH6
olivier@olivier-desktop:~/alsa-driver-1.0.16$ make
make all-deps
make[1]: Entering directory `/home/olivier/alsa-driver-1.0.16'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/olivier/alsa-driver-1.0.16'

Please, run the configure script as first...

olivier@olivier-desktop:~/alsa-driver-1.0.16$ make install
if [ -L /include/sound ]; then \
        rm -f /include/sound; \
        ln -sf /home/olivier/alsa-driver-1.0.16/include/sound /include/sound; \
    else \
        rm -rf /include/sound; \
        install -d -m 755 -g root -o root /include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /include/sound; \
        done \
    fi
install: cannot create directory `/include': Permission denied
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
olivier@olivier-desktop:~/alsa-driver-1.0.16$

---

### Post by shkdwn on 2009-10-13
olivier@olivier-desktop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x92100000 irq 16

olivier@olivier-desktop:~$ cat /proc/asound/card0/codec#*
Codec: Realtek ALC880
Address: 2
Function Id: 0x1
Vendor Id: 0x10ec0880
Subsystem Id: 0x08600000
Revision Id: 0x90000
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf0051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals: 
  Power: setting=D0, actual=D0
  Connection: 0
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals:  [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 7
     0x18* 0x19 0x1a 0x1b 0x1c 0x14 0x15
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals:  [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23] [0x23 0x23]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 10
     0x18* 0x19 0x1a 0x1b 0x1c 0x0b 0x14 0x15 0x16 0x17
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x23, nsteps=0x41, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x41 0x41] [0x80 0x80] [0x80 0x80]
  Connection: 8
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 4
     0x0c* 0x0d 0x0e 0x0f
Node 0x11 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 4
     0x0c* 0x0d 0x0e 0x0f
Node 0x12 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 4
     0x0c* 0x0d 0x0e 0x0f
Node 0x13 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 4
     0x0c* 0x0d 0x0e 0x0f
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003f: IN OUT HP Detect Trigger ImpSense
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 0
Node 0x18 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x03000097: [Jack] Line Out at Ext Left
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x9, Sequence = 0x7
  Pin-ctls: 0x40: OUT VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x10
Node 0x19 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x00000020: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x11
Node 0x1a [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x00003737: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Blue
    DefAssociation = 0x3, Sequence = 0x7
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x12
Node 0x1b [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x13
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x00000000: [Jack] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=10
  Processing Coefficient: 0x8a00
  Coefficient Index: 0x09
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=64, direct=0, val=0
  Unsolicited: tag=00, enabled=0
  Connection: 0
olivier@olivier-desktop:~$

---

### Post by Tiede on 2009-10-29
Hello, shkdwn.
Next time, try using attachments instead of multiple posts with command outputs :)
Have you followed [https://help.ubuntu.com/community/HdaIntelSoundHowto[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto"]this wiki?](https://help.ubuntu.com/community/HdaIntelSoundHowto[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto"]this wiki?)
For me, this is what works: Adding this to /etc/modprobe.d/alsa-base.conf
```

#Options suggested by Launchpad to fix sound bug. Delete the next few lines if this does not work.
##options snd-hda-intel model=laptop
##options snd-hda-intel enable_msi=1
##options snd-hda-intel single_cmd=1
#second set of options...
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=mobile
alias sound-slot-3 snd-hda-intel

```

---

### Post by Ulysses361 on 2009-10-29
@shkdwn: please execute step 1, then reboot and send us output from step 3 and step 4 using this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Ulysses361 on 2009-10-29
Please try this procedure:

1. Upgrade ALSA to version 1.0.21 using this procedure:

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

2. copy-paste the following command into the Terminal:

gksudo gedit /etc/modprobe.d/alsa-base.conf

3. and add these lines to the end of the /etc/modprobe.d/alsa-base.conf file:

# So you need to go into the alsa-base.conf file and then add the following lines at the end of it.

# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=3stack

4. Save the changes to the /etc/modprobe.d/alsa-base.conf file

5. Then navigate to System>Preferences>Sound and change everything to ALSA

6. REBOOT and retest sound

7. In the Mixer control panel, make sure to unmute all channels and increase the volume on all channels

8. If it still does not work, please try one of the following model options instead (replacing 3stack as model option):

 ALC880
   3stack 3-jack in back and a headphone out
   3stack-digout 3-jack in back, a HP out and a SPDIF out
   5stack 5-jack in back, 2-jack in front
   5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
   6stack 6-jack in back, 2-jack in front
   6stack-digout 6-jack with a SPDIF out
   w810 3-jack
   z71v 3-jack (HP shared SPDIF)
   asus 3-jack (ASUS Mobo)
   asus-w1v ASUS W1V
   asus-dig ASUS with SPDIF out
   asus-dig2 ASUS with SPDIF out (using GPIO2)
   uniwill 3-jack
   fujitsu Fujitsu Laptops (Pi1536)
   F1734 2-jack
   lg LG laptop (m1 express dual)
   lg-lw LG LW20/LW25 laptop
   tcl TCL S700
   clevo Clevo laptops (m520G, m665n)
   medion Medion Rim 2150
   auto auto-config reading BIOS (default)

You will need to reboot and retest sound after every change to the alsa-base.conf file

---

### Post by shkdwn on 2009-12-04
sorry i gave up on ubuntu!!! sound it to unstable

---

