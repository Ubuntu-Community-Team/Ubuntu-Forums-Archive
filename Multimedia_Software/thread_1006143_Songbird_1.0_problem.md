---
title: "Songbird 1.0 problem"
date: 2008-12-09
forum: Multimedia Software
---

### Post by IceReaver75 on 2008-12-09
no matter how i install this program i get this when trying to run songbird in a terminal and it wont start at all:

*** glibc detected *** ././songbird-bin: double free or corruption (out): 0xb2795320 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7dcf3f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7dd1456]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb2699141]
/usr/lib/libvisual-0.4.so.0[0xb2690407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb26905e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb269fec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb285c1f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb41392c2]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb4139b79]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb41447ee]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb4144993]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb40f4a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb40f4f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb40f5589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb40f5b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6bd47e3]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb40f3d1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb40f3e25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3fbfcf3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3fc68e1]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3fcd252]
/usr/share/Songbird/xulrunner/libxul.so[0xb7681449]
/usr/share/Songbird/xulrunner/libxul.so[0xb768090b]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3fca2ef]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3fca319]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3fc9ac5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3fc53a5]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3fc5b5c]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3fc6841]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3fcd252]
/usr/share/Songbird/xulrunner/libxul.so[0xb7681449]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb50910f9]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb5091126]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb50909c1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb507d8b5]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb507b1e7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb507b564]
/usr/share/Songbird/xulrunner/libxul.so[0xb765e21f]
/usr/share/Songbird/xulrunner/libxul.so[0xb765e7c4]
/usr/share/Songbird/xulrunner/libxul.so[0xb6ef3a98]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x1aba)[0xb6ef17b2]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d76685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:01 4243532    /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:01 4243532    /usr/share/Songbird/songbird-bin
094c1000-094e2000 rw-p 094c1000 00:00 0          [heap]
b267f000-b26bb000 r-xp 00000000 08:01 4180413    /usr/lib/libvisual-0.4.so.0.0.0
b26bb000-b26bc000 r--p 0003b000 08:01 4180413    /usr/lib/libvisual-0.4.so.0.0.0
b26bc000-b26bd000 rw-p 0003c000 08:01 4180413    /usr/lib/libvisual-0.4.so.0.0.0
b26bd000-b26e4000 r-xp 00000000 08:01 3055705    /usr/lib/libsidplay.so.1.0.3
b26e4000-b26f4000 rw-p 00026000 08:01 3055705    /usr/lib/libsidplay.so.1.0.3
b26f4000-b2800000 rw-p b26f4000 00:00 0 
b280e000-b282c000 rw-p b280e000 00:00 0 
b2831000-b284a000 r-xp 00000000 08:01 4179724    /usr/lib/libdv.so.4.0.3
b284a000-b284b000 r--p 00018000 08:01 4179724    /usr/lib/libdv.so.4.0.3
b284b000-b284d000 rw-p 00019000 08:01 4179724    /usr/lib/libdv.so.4.0.3
b284d000-b2859000 rw-p b284d000 00:00 0 
b285a000-b2860000 r-xp 00000000 08:01 3563569    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2860000-b2861000 r--p 00005000 08:01 3563569    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2861000-b2862000 rw-p 00006000 08:01 3563569    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2862000-b2867000 r-xp 00000000 08:01 3563693    /usr/lib/gstreamer-0.10/libgstsid.so
b2867000-b2868000 r--p 00004000 08:01 3563693    /usr/lib/gstreamer-0.10/libgstsid.so
b2868000-b2869000 rw-p 00005000 08:01 3563693    /usr/lib/gstreamer-0.10/libgstsid.so
b2869000-b28ec000 r-xp 00000000 08:01 4180823    /usr/lib/libx264.so.59
b28ec000-b28ed000 rw-p 00082000 08:01 4180823    /usr/lib/libx264.so.59
b28ed000-b28ef000 rw-p b28ed000 00:00 0 
b28ef000-b2938000 r-xp 00000000 08:01 4180383    /usr/lib/libtheora.so.0.3.3
b2938000-b293a000 rw-p 00049000 08:01 4180383    /usr/lib/libtheora.so.0.3.3
b293a000-b2948000 r-xp 00000000 08:01 4180806    /usr/lib/libfaac.so.0.0.0
b2948000-b2949000 r--p 0000d000 08:01 4180806    /usr/lib/libfaac.so.0.0.0
b2949000-b294c000 rw-p 0000e000 08:01 4180806    /usr/lib/libfaac.so.0.0.0
b294c000-b2955000 r-xp 00000000 08:01 4180816    /usr/lib/liba52-0.7.4.so
b2955000-b2956000 rw-p 00008000 08:01 4180816    /usr/lib/liba52-0.7.4.so
b2956000-b2957000 rw-p b2956000 00:00 0 
b2957000-b2dad000 r-xp 00000000 08:01 4211918    /usr/lib/i686/cmov/libavcodec.so.51.50.0
b2dad000-b2dae000 r--p 00455000 08:01 4211918    /usr/lib/i686/cmov/libavcodec.so.51.50.0
b2dae000-b2db4000 rw-p 00456000 08:01 4211918    /usr/lib/i686/cmov/libavcodec.so.51.50.0
b2db4000-b2eab000 rw-p b2db4000 00:00 0 
b2eab000-b2f48000 r-xp 00000000 08:01 4211920    /usr/lib/i686/cmov/libavformat.so.52.7.0
b2f48000-b2f49000 r--p 0009c000 08:01 4211920    /usr/lib/i686/cmov/libavformat.so.52.7.0
b2f49000-b2f4c000 rw-p 0009d000 08:01 4211920    /usr/lib/i686/cmov/libavformat.so.52.7.0
b2f4c000-b2f7a000 r-xp 00000000 08:01 3563617    /usr/lib/gstreamer-0.10/libgstffmpeg.so
b2f7a000-b2f7b000 ---p 0002e000 08:01 3563617    /usr/lib/gstreamer-0.10/libgstffmpeg.so
b2f7b000-b2f7c000 r--p 0002e000 08:01 3563617    /usr/lib/gstreamer-0.10/libgstffmpeg.so
b2f7c000-b2f7d000 rw-p 0002f000 08:01 3563617    /usr/lib/gstreamer-0.10/libgstffmpeg.so
b2f7d000-b2f84000 r-xp 00000000 08:01 4180099    /usr/lib/libkrb5support.so.0.1
b2f84000-b2f85000 r--p 00006000 08:01 4180099    /usr/lib/libkrb5support.so.0.1
b2f85000-b2f86000 rw-p 00007000 08:01 4180099    /usr/lib/libkrb5support.so.0.1
b2f86000-b2f9c000 r-xp 00000000 08:01 4180319    /usr/lib/libsasl2.so.2.0.22
b2f9c000-b2f9d000 r--p 00015000 08:01 4180319    /usr/lib/libsasl2.so.2.0.22
b2f9d000-b2f9e000 rw-p 00016000 08:01 4180319    /usr/lib/libsasl2.so.2.0.22
b2f9e000-b2faa000 r-xp 00000000 08:01 4180103    /usr/lib/liblber-2.4.so.2.1.0
b2faa000-b2fab000 r--p 0000b000 08:01 4180103    /usr/lib/liblber-2.4.so.2.1.0
b2fab000-b2fac000 rw-p 0000c000 08:01 4180103    /usr/lib/liblber-2.4.so.2.1.0
b2fac000-b2fd4000 r-xp 00000000 08:01 4179954    /usr/lib/libgssapi_krb5.so.2.2
b2fd4000-b2fd5000 r--p 00028000 08:01 4179954    /usr/lib/libgssapi_krb5.so.2.2
b2fd5000-b2fd6000 rw-p 00029000 08:01 4179954    /usr/lib/libgssapi_krb5.so.2.2
b2fd6000-b2ff8000 r-xp 00000000 08:01 4180091    /usr/lib/libk5crypto.so.3.1
b2ff8000-b2ff9000 r--p 00022000 08:01 4180091    /usr/lib/libk5crypto.so.3.1
b2ff9000-b2ffa000 rw-p 00023000 08:01 4180091    /usr/lib/libk5crypto.so.3.1
b2ffa000-b3089000 r-xp 00000000 08:01 4180097    /usr/lib/libkrb5.so.3.3
b3089000-b308b000 r--p 0008e000 08:01 4180097    /usr/lib/libkrb5.so.3.3
b308b000-b308c000 rw-p 00090000 08:01 4180097    /usr/lib/libkrb5.so.3.3
b308c000-b30cb000 r-xp 00000000 08:01 4180108    /usr/lib/libldap_r-2.4.so.2.1.0
b30cb000-b30cc000 r--p 0003e000 08:01 4180108    /usr/lib/libldap_r-2.4.so.2.1.0
b30cc000-b30cd000 rw-p 0003f000 08:01 4180108    /usr/lib/libldap_r-2.4.so.2.1.0
b30cd000-b30ce000 rw-p b30cd000 00:00 0 
b30ce000-b30fe000 r-xp 00000000 08:01 4180073    /usr/lib/libidn.so.11.5.37
b30fe000-b30ff000 r--p 00030000 08:01 4180073    /usr/lib/libidn.so.11.5.37
b30ff000-b3100000 rw-p 00031000 08:01 4180073    /usr/lib/libidn.so.11.5.37
b3100000-b3109000 r-xp 00000000 08:01 5112985    /lib/tls/i686/cmov/libcrypt-2.8.90.so
b3109000-b310a000 r--p 00008000 08:01 5112985    /lib/tls/i686/cmov/libcrypt-2.8.90.so
b310a000-b310b000 rw-p 00009000 08:01 5112985    /lib/tls/i686/cmov/libcrypt-2.8.90.so
b310b000-b3132000 rw-p b310b000 00:00 0 
b3132000-b316b000 r-xp 00000000 08:01 4179687    /usr/lib/libcurl-gnutls.so.4.1.0
b316b000-b316c000 r--p 00038000 08:01 4179687    /usr/lib/libcurl-gnutls.so.4.1.0
b316c000-b316d000 rw-p 00039000 08:01 4179687    /usr/lib/libcurl-gnutls.so.4.1.0
b316d000-b330b000 r-xp 00000000 08:01 3055637    /usr/lib/libmysqlclient.so.15.0.0
b330b000-b330c000 ---p 0019e000 08:01 3055637    /usr/lib/libmysqlclient.so.15.0.0
b330c000-b330f000 r--p 0019e000 08:01 3055637    /usr/lib/libmysqlclient.so.15.0.0
b330f000-b334f000 rw-p 001a1000 08:01 3055637    /usr/lib/libmysqlclient.so.15.0.0
b334f000-b3350000 rw-p b334f000 00:00 0 
b3350000-b3370000 r-xp 00000000 08:01 3055641    /usr/lib/libgmyth.so.0.0.0
b3370000-b3372000 rw-p 0001f000 08:01 3055641    /usr/lib/libgmyth.so.0.0.0
b3375000-b3380000 r-xp 00000000 08:01 3563548    /usr/lib/gstreamer-0.10/libgstdv.so
b3380000-b3381000 r--p 0000a000 08:01 3563548    /usr/lib/gstreamer-0.10/libgstdv.so
b3381000-b3382000 rw-p 0000b000 08:01 3563548    /usr/lib/gstreamer-0.10/libgstdv.so
b3382000-b3387000 r-xp 00000000 08:01 3563638    /usr/lib/gstreamer-0.10/libgstmythtvsrc.so
b3387000-b3388000 r--p 00004000 08:01 3563638    /usr/lib/gstreamer-0.10/libgstmythtvsrc.so
b3388000-b3389000 rw-p 00005000 08:01 3563638    /usr/lib/gstreamer-0.10/libgstmythtvsrc.so
b3389000-b33c4000 r-xp 00000000 08:01 4180813    /usr/lib/libfaad.so.0.0.0
b33c4000-b33c5000 ---p 0003b000 08:01 4180813    /usr/lib/libfaad.so.0.0.0
b33c5000-b33c6000 r--p 0003b000 08:01 4180813    /usr/lib/libfaad.so.0.0.0
b33c6000-b33c9000 rw-p 0003c000 08:01 4180813    /usr/lib/libfaad.so.0.0.0
b33c9000-b33e1000 r-xp 00000000 08:01 3563692    /usr/lib/gstreamer-0.10/libgstrmdemux.so
b33e1000-b33e2000 r--p 00017000 08:01 3563692    /usr/lib/gstreamer-0.10/libgstrmdemux.so
b33e2000-b33e3000 rw-p 00018000 08:01 3563692    /usr/lib/gstreamer-0.10/libgstrmdemux.so
b33e3000-b33f8000 r-xp 00000000 08:01 4180358    /usr/lib/libspeex.so.1.4.0
b33f8000-b33f9000 r--p 00014000 08:01 4180358    /usr/lib/libspeex.so.1.4.0
b33f9000-b33fa000 rw-p 00015000 08:01 4180358    /usr/lib/libspeex.so.1.4.0
b33fb000-b33fe000 r-xp 00000000 08:01 3563549    /usr/lib/gstreamer-0.10/libgstefence.so
b33fe000-b33ff000 r--p 00002000 08:01 3563549    /usr/lib/gstreamer-0.10/libgstefence.so
b33ff000-b3400000 rw-p 00003000 08:01 3563549    /usr/lib/gstreamer-0.10/libgstefence.so
b3400000-b3408000 r-xp 00000000 08:01 3563642    /usr/lib/gstreamer-0.10/libgstladspa.so
b3408000-b3409000 r--p 00007000 08:01 3563642    /usr/lib/gstreamer-0.10/libgstladspa.so
b3409000-b340a000 rw-p 00008000 08:01 3563642    /usr/lib/gstreamer-0.10/libgstladspa.so
b340a000-b3415000 r-xp 00000000 08:01 3563592    /usr/lib/gstreamer-0.10/libgstspeex.so
b3415000-b341600 r--

it seems to be a problem with the songbird-bin file since it always says songbird-bin is still running when trying to restart my computer.  DOes anyone know why this is happening.

---

### Post by peakshysteria on 2008-12-09
Not sure why it happens. Have you tried to uninstall via Synaptic then reinstalled with a .deb from Getdeb: [http://www.getdeb.net/release.php?id=3519](http://www.getdeb.net/release.php?id=3519) (remember to get it according to your OS version).

---

### Post by IceReaver75 on 2008-12-09
Yeah I have downloaded the deb file from getdeb (got the one for intrepid ibex) tried that one it didn't work so i uninstalled it through synaptic and downloaded a different deb that said it was tested with intrepid and works. Installed that one and same problem.  I click on songbird in the sound/video and it brings up a window on the bottom that says starting songbird and after a minute or so the little window on the bottom disappears and songbird never starts. If i try to start it again it says that songbird is already running but not responding please stop the process or restart your computer.  Not sure whats going onunless something from the first deb isn't uninstalling when i uninstalled it.

i get this message if i try to open songbird-bin as root :
/usr/share/Songbird/songbird-bin: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory

if that helps anyone

---

### Post by collegeKid28 on 2008-12-09
I've had a similar experience with other apps.  Did you try rebooting?

Tim

---

### Post by IceReaver75 on 2008-12-09
yes i tried reinstalling songbird deb and then restarted after restart it does the same thing window on the bottom, nothing shows up and if i try to restart the computer i get the message of a program is still running : songbird-bin not responding

---

### Post by IceReaver75 on 2008-12-10
well after fighting with songbird 1.0 for almost a day with no solution I did some deep searching and found the Songbird .0.7 version.  Extracted that folder to my home folder and clicked the songbird file inside.  Started right up no problems at all.  Might not be the newest version but it works and thats all that matters to me.  Thanks to those who tried to help.

---

### Post by supertux on 2008-12-10
strange, on one machine (intrepid) it works here, otherone doesnt. I think i have to look for the differences then.. :(

---

### Post by peakshysteria on 2008-12-10
**IceReaver75:** Are you running 64 bit or 32 bit Intrepid? Are you sure you have tried the right version of the .deb? (Yeah a know it's a lame question,but I have to ask anyway..........).

---

### Post by IceReaver75 on 2008-12-12
i downloaded the 32 bit so it should have worked. I made sure it was the right version

---

### Post by tyroeternal on 2008-12-16
I trawled around the forums for a while and stumbled onto the solution via this [1] thread.  I followed it to the songbird ticket [2] where someone suggests upgrading (I removed it) the package 'libvisual-0.4-plugins'.  I'm not sure why it worked, but it certainly did the trick for me, and I was experiencing what appear to be the same problems.

[1] [http://ubuntuforums.org/showthread.php?t=1005356]("http://ubuntuforums.org/showthread.php?t=1005356")
[2] [https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448]("https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448")

---

### Post by 4KvRMU7Nnv on 2008-12-25
WOW! thank you! i can't believe it was that easy! that worked perfectly!

---

