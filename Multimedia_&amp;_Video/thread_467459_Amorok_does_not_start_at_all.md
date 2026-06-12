---
title: "Amorok does not start at all"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by Gizim on 2007-06-07
When i click the icon the Amorok icon bobs up and down but it never starts any ideas?

---

### Post by Gizim on 2007-06-07
gizim@Spartan:~$ gdb -p `pidof amarokapp`
gdb: option `-p' requires an argument
Use `gdb --help' for a complete list of options.
gizim@Spartan:~$ gdb -p `pidof amarokapp`
gdb: option `-p' requires an argument
Use `gdb --help' for a complete list of options.
gizim@Spartan:~$ gdb -p `pidof amarokapp`
gdb: option `-p' requires an argument
Use `gdb --help' for a complete list of options.
gizim@Spartan:~$ gdb -p `pidof amarokapp`
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
Attaching to process 9023
Reading symbols from /usr/bin/amarokapp...(no debugging symbols found)...done.
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Reading symbols from /usr/lib/libamarok.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libamarok.so.0
Reading symbols from /usr/lib/libkutils.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkutils.so.1
Reading symbols from /usr/lib/libkio.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkio.so.4
Reading symbols from /usr/lib/libkdeui.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkdeui.so.4
Reading symbols from /usr/lib/libkdecore.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkdecore.so.4
Reading symbols from /usr/lib/libkhtml.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkhtml.so.4
Reading symbols from /usr/lib/libknewstuff.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libknewstuff.so.1
Reading symbols from /usr/lib/libtag.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libtag.so.1
Reading symbols from /usr/lib/libGL.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...
(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread -1261708512 (LWP 9023)]
[New Thread -1315542128 (LWP 9033)]
[New Thread -1307149424 (LWP 9031)]
[New Thread -1298756720 (LWP 9030)]
[New Thread -1288475760 (LWP 9029)]
[New Thread -1265931376 (LWP 9028)]
[New Thread -1274324080 (LWP 9027)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libtunepimp.so.5...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libtunepimp.so.5
Reading symbols from /usr/lib/libmysqlclient.so.15...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libmysqlclient.so.15
Reading symbols from /usr/lib/libpq.so.5...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpq.so.5
Reading symbols from /usr/lib/libstdc++.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/libgcc_s.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /lib/tls/i686/cmov/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libqt-mt.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libqt-mt.so.3
Reading symbols from /usr/lib/libkdesu.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkdesu.so.4
Reading symbols from /usr/lib/libkwalletclient.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkwalletclient.so.1
Reading symbols from /usr/lib/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /lib/libacl.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libacl.so.1
Reading symbols from /lib/libattr.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libattr.so.1
Reading symbols from /usr/lib/libDCOP.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libDCOP.so.4
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXext.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libresolv.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libresolv.so.2
Reading symbols from /lib/tls/i686/cmov/libutil.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libutil.so.1
Reading symbols from /usr/lib/libart_lgpl_2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libart_lgpl_2.so.2
Reading symbols from /usr/lib/libidn.so.11...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libidn.so.11
Reading symbols from /usr/lib/libkdefx.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkdefx.so.4
Reading symbols from /usr/lib/libjpeg.so.62...
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/libkjs.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkjs.so.1
Reading symbols from /usr/lib/libpcreposix.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpcreposix.so.3
Reading symbols from /usr/lib/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpcre.so.3
Reading symbols from /usr/lib/libkparts.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkparts.so.2
Reading symbols from /usr/lib/libkdeprint.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkdeprint.so.4
Reading symbols from /usr/lib/libGLcore.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLcore.so.1
Reading symbols from /usr/lib/tls/libnvidia-tls.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/tls/libnvidia-tls.so.1
Reading symbols from /usr/lib/libX11.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libgssapi_krb5.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgssapi_krb5.so.2
Reading symbols from /usr/lib/libkrb5.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkrb5.so.3
Reading symbols from /usr/lib/libk5crypto.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libk5crypto.so.3
Reading symbols from /lib/libcom_err.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libcom_err.so.2
Reading symbols from /usr/lib/libkrb5support.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libkrb5support.so.0
Reading symbols from /usr/lib/libgnutls.so.13...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnutls.so.13
Reading symbols from /usr/lib/libtasn1.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libtasn1.so.3
Reading symbols from /usr/lib/libgcrypt.so.11...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgcrypt.so.11
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /usr/lib/libgpg-error.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgpg-error.so.0
Reading symbols from /usr/lib/libfftw3.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfftw3.so.3
Reading symbols from /usr/lib/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/libcurl-gnutls.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcurl-gnutls.so.3
Reading symbols from /usr/lib/libofa.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libofa.so.0
Reading symbols from /usr/lib/libmusicbrainz.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libmusicbrainz.so.4
Reading symbols from /lib/tls/i686/cmov/libcrypt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libcrypt.so.1
Reading symbols from /usr/lib/i686/cmov/libssl.so.0.9.8...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i686/cmov/libssl.so.0.9.8
Reading symbols from /usr/lib/i686/cmov/libcrypto.so.0.9.8...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i686/cmov/libcrypto.so.0.9.8
Reading symbols from /usr/lib/libfontconfig.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libaudio.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libaudio.so.2
Reading symbols from /usr/lib/libXt.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXt.so.6
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libXi.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXi.so.6
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libXrandr.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libXinerama.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXft.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXft.so.2
Reading symbols from /usr/lib/libfreetype.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/kde3/plugins/styles/polyester.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/kde3/plugins/styles/polyester.so
Reading symbols from /usr/lib/kde3/libamarok_void-engine_plugin.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/kde3/libamarok_void-engine_plugin.so
Reading symbols from /usr/lib/qt3/plugins/imageformats/libqmng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/qt3/plugins/imageformats/libqmng.so
Reading symbols from /usr/lib/libmng.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libmng.so.1
Reading symbols from /usr/lib/liblcms.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/liblcms.so.1
Reading symbols from /usr/lib/kde3/libamarok_massstorage-device.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/kde3/libamarok_massstorage-device.so
Reading symbols from /usr/lib/kde3/libamarok_smb-device.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/kde3/libamarok_smb-device.so
Reading symbols from /usr/lib/kde3/libamarok_nfs-device.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/kde3/libamarok_nfs-device.so
Reading symbols from /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
Reading symbols from /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
Reading symbols from /usr/lib/qt3/plugins/inputmethods/libqsimple.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/qt3/plugins/inputmethods/libqsimple.so
Reading symbols from /usr/lib/qt3/plugins/inputmethods/libqxim.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/qt3/plugins/inputmethods/libqxim.so
Reading symbols from /usr/lib/qt3/plugins/inputmethods/libqscim.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/qt3/plugins/inputmethods/libqscim.so
Reading symbols from /usr/lib/libscim-x11utils-1.0.so.8...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libscim-x11utils-1.0.so.8
Reading symbols from /usr/lib/libscim-1.0.so.8...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libscim-1.0.so.8
Reading symbols from /usr/lib/kde3/libamarok_xine-engine.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/kde3/libamarok_xine-engine.so
Reading symbols from /usr/lib/libxine.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxine.so.1
Reading symbols from /lib/tls/i686/cmov/librt.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_dvb.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_dvb.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_vcdo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_vcdo.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_mms.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_mms.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_vcd.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_vcd.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_http.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_http.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_file.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_file.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_pvr.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_pvr.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_v4l.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_v4l.so
Reading symbols from /usr/lib/libasound.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libasound.so.2
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_cdda.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_cdda.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_inp_dvd.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_inp_dvd.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_decode_w32dll.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_decode_w32dll.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_decode_qt.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_decode_qt.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_decode_real.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_decode_real.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_decode_sputext.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_decode_sputext.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/post/xineplug_post_goom.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/post/xineplug_post_goom.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/post/xineplug_post_tvtime.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/post/xineplug_post_tvtime.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_ao_out_alsa.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_ao_out_alsa.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_ogg.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_ogg.so
Reading symbols from /usr/lib/libvorbis.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libvorbis.so.0
Reading symbols from /usr/lib/libspeex.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libspeex.so.1
Reading symbols from /usr/lib/libtheora.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libtheora.so.0
Reading symbols from /usr/lib/libogg.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libogg.so.0
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_image.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_image.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_yuv4mpeg2.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_yuv4mpeg2.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_nsv.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_nsv.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_qt.so...
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_qt.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_avi.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_avi.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_pva.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_pva.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_audio.so
Reading symbols from /usr/lib/libmodplug.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libmodplug.so.0
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_mng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_mng.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_slave.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_slave.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_asf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_asf.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_flv.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_flv.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_fli.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_fli.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_iff.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_iff.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_real.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_real.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_games.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_matroska.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_matroska.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_rawdv.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_rawdv.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_yuv_frames.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_yuv_frames.so
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_flac.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_flac.so
Reading symbols from /usr/lib/libFLAC.so.7...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libFLAC.so.7
Reading symbols from /usr/lib/xine/plugins/1.1.4/xineplug_dmx_sputext.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/xine/plugins/1.1.4/xineplug_dmx_sputext.so
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()

---

