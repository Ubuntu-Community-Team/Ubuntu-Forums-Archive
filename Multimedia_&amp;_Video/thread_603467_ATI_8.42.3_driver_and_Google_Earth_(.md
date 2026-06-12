---
title: "ATI 8.42.3 driver and Google Earth :("
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by RavanH on 2007-11-05
Hi all,

Has anyone got this problem with Google Earth? If so, please confirm this on [http://ati.cchtml.com/show_bug.cgi?id=877](http://ati.cchtml.com/show_bug.cgi?id=877) ... Or am I the only one (on Ubuntu Gutsy AMD64 and using ATI Radeon Xpress 200M with AIGLX/Desktop Effects/CompizFusion)?

**DESCRIPTION**
After upgrading to the new 8.42.3 on Ubuntu Gutsy AMD64 with Radeon Xpress 200M
graphics card and AIGLX/Desktop Effects/Compiz Fusion enabled, Google Earth
(that ran only after adding the libGL.so.1 and libGL.so.1.2 from an older
driver) no longer works. After the initialization screen pops up, it disappears
again and GE does not start/continue... 

When I run googleearth in terminal I get:
```
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  ./googleearth-bin [0x8058399]
  [0xffffe500]
```

And the GE bugreport (that should be automatically sent to Google, but probably
isn't) says:
```
CRASHLOGVER 1
CRASHLOGID 0x58D6D3A3
APPVERMAJOR 4
APPVERMINOR 2
APPVERBUILD 198
APPBUILDDATE Sep 12 2007
APPBUILDTIME 15:29:59
OSTYPE 11
OSVERMAJOR 2
OSVERMINOR 6
OSVERBUILD 22
OSVERPATCH 0
PID 30856
CRASHSIGNAL 11
CRASHTIME 1194262404
PROGRAMUPTIME 5

STACK 0x8057fb4
STACK 0x8058399
STACK 0xffffe500

DSO googleearth-bin/0x8048000/111416
DSO linux-gate.so.1/0xffffe000/1992
DSO libbase.so/0xf7e85000/669696
DSO libcomponent.so/0xf7e6d000/86805
DSO libfusion.so/0xf7e68000/13124
DSO libgeobase.so/0xf7b02000/3443006
DSO libmath.so/0xf7ae7000/103833
DSO libwmsbase.so/0xf7a82000/395459
DSO libnet.so/0xf7a37000/288756
DSO libalchemyext.so/0xf7a32000/15216
DSO libcollada.so/0xf76d9000/3388384
DSO libgoogleearth.so/0xf756c000/1439454
DSO libGLU.so.1/0xf74ee000/507779
DSO libcrypto.so.0.9.8/0xf73c7000/1103016
DSO libcurl.so.3/0xf739e000/159800
DSO libfreeimage.so.3/0xf72db000/770245
DSO libgcc_s.so.1/0xf72d0000/39096
DSO libjpeg.so.62/0xf72ac000/139688
DSO libmng.so.1/0xf724e000/364312
DSO libpng12.so.0/0xf7226000/156964
DSO libqt-mt.so.3/0xf6af0000/7313347
DSO libqui.so.1/0xf6a54000/621811
DSO libssl.so.0.9.8/0xf6a19000/221460
DSO libstdc++.so.6/0xf693e000/849472
DSO libtiff.so.3/0xf68e2000/364328
DSO libz.so.1/0xf68cb000/86972
DSO libIGCore.so/0xf67d4000/952308
DSO libIGGfx.so/0xf671c000/704928
DSO libIGAttrs.so/0xf66b9000/365780
DSO libIGDisplay.so/0xf66a5000/70352
DSO libIGGui.so/0xf6663000/246068
DSO libIGSg.so/0xf6555000/1036804
DSO libIGCollision.so/0xf6546000/55044
DSO libIGMath.so/0xf64fc000/277228
DSO libIGUtils.so/0xf64d5000/146568
DSO libIGOpt.so/0xf63fa000/841480
DSO libIGExportCommon.so/0xf6372000/517352
DSO libcommon.so/0xf6275000/996938
DSO librender.so/0xf621a000/349174
DSO libauth.so/0xf618f000/548314
DSO libframework.so/0xf6178000/86398
DSO libm.so.6/0xf613e000/143176
DSO libc.so.6/0xf5ff4000/1323412
DSO libpthread.so.0/0xf5fdb000/78036
DSO libdl.so.2/0xf5fd7000/7424
DSO libXrender.so.1/0xf5fcf000/26920
DSO libXcursor.so.1/0xf5fc6000/30596
DSO libXft.so.2/0xf5fb3000/67768
DSO libfreetype.so.6/0xf5f43000/438628
DSO libfontconfig.so.1/0xf5f18000/141120
DSO libXext.so.6/0xf5f0a000/51440
DSO libX11.so.6/0xf5e19000/967336
DSO libSM.so.6/0xf5e11000/26384
DSO libICE.so.6/0xf5df8000/84464
DSO libGL.so.1/0xf5d59000/615175
DSO ld-linux.so.2/0xf7f32000/113700
DSO libXfixes.so.3/0xf5d54000/12628
DSO libexpat.so.1/0xf5d33000/121492
DSO libXau.so.6/0xf5d30000/5460
DSO libXdmcp.so.6/0xf5d2b000/15076
DSO libnss_compat.so.2/0xf5337000/25316
DSO libnsl.so.1/0xf531f000/80100
DSO libnss_nis.so.2/0xf6164000/32268
DSO libnss_files.so.2/0xf5314000/35220
DSO libnss_mdns4_minimal.so.2/0xf4abf000/5168
DSO libnss_dns.so.2/0xf4ab9000/14936
DSO libresolv.so.2/0xf4aa5000/60188
DSO libevll.so/0xf32f3000/6107868
DSO libnavigate.so/0xef55e000/1336238
DSO liblayer.so/0xef30d000/2359150
DSO libmeasure.so/0xef25d000/696250
DSO libbasicIngest.so/0xef172000/915434
DSO libgooglesearch.so/0xef0b7000/741326
DSO libinput_plugin.so/0xf4a50000/232214
DSO libflightsim.so/0xeefb2000/1022678
DSO fglrx_dri.so/0xee003000/14386816
DSO librt.so.1/0xf4a01000/27184
```

---

### Post by Cochise on 2007-11-05
Gutsy 32-Bit, ATi fglrx 8.42.3 with AIGLX and google earth is ok, just thought id let you know.

---

### Post by jimerickso on 2007-11-05
> **Cochise said:**
> Gutsy 32-Bit, ATi fglrx 8.42.3 with AIGLX and google earth is ok, just thought id let you know.
how did you get google earth to not flicker??

---

### Post by carpex on 2007-11-05
I think flickering disappears if you disable compiz (desktop effects). 

CP

---

### Post by Cochise on 2007-11-05
yup i turn compiz off usually as i personally dont like it that much

---

### Post by jimerickso on 2007-11-06
ok thanks Cochise!!

---

