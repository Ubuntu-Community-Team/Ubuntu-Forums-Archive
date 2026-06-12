---
title: "Arista MKV to m4v issues..."
date: 2010-11-06
forum: Multimedia Software
---

### Post by aperture123 on 2010-11-06
Ok, I've been having some recent troubles with a certain mkv file I wanted to convert, so if anybody can help, I'd appreciate that.

The movie has two audio tracks and a subtitle track. I, however, created it again with just one audio track and one subtitle track, and also extracted that subtitle track and saved it as a .srt

I started up arista transcoder and set to convert the mkv to my ipod format, and to include the .srt file for subs. Arista acts as it should, starts the conversion...and then instantly stops and closes. In the end I get a 0mb file. I opened up arista through terminal arista-gtk.

**Also, I turned off live preview. **

Here's the terminal code when arista closes out.

```
tx@tx-laptop:~$ arista-gtk
*** glibc detected *** /usr/bin/python: double free or corruption (!prev): 0x0ae0d408 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x2f3591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0x2f4de8]
/lib/tls/i686/cmov/libc.so.6(+0x70b11)[0x2f8b11]
/lib/tls/i686/cmov/libc.so.6(realloc+0xdd)[0x2f8f9d]
/lib/libglib-2.0.so.0(g_realloc+0x3f)[0x43a00f]
/lib/libglib-2.0.so.0(+0x14f67)[0x40af67]
/lib/libglib-2.0.so.0(g_array_append_vals+0x2d)[0x40b56d]
/usr/lib/libgstreamer-0.10.so.0(+0x72f02)[0x205ef02]
/usr/lib/libgstreamer-0.10.so.0(gst_structure_id_set_value+0xb9)[0x205f6d9]
/usr/lib/libgstreamer-0.10.so.0(+0x78e99)[0x2064e99]
/usr/lib/libgstreamer-0.10.so.0(+0x78f48)[0x2064f48]
/usr/lib/libgstreamer-0.10.so.0(gst_structure_foreach+0x53)[0x205e233]
/usr/lib/libgstreamer-0.10.so.0(gst_tag_list_insert+0x74)[0x2066ff4]
/usr/lib/libgstreamer-0.10.so.0(gst_tag_setter_merge_tags+0xb6)[0x2069b06]
/usr/lib/gstreamer-0.10/libgstffmpeg.so(+0x2d1d9)[0x4ec51d9]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_send_event+0x3e3)[0x203b0c3]
/usr/lib/libgstreamer-0.10.so.0(gst_pad_push_event+0x27a)[0x203b63a]
/usr/lib/gstreamer-0.10/libgstcoreelements.so(+0x196f0)[0x45f56f0]
/usr/lib/libgstreamer-0.10.so.0(+0x7dd6b)[0x2069d6b]
/usr/lib/libgstreamer-0.10.so.0(+0x7f377)[0x206b377]
/lib/libglib-2.0.so.0(+0x67d0c)[0x45dd0c]
/lib/libglib-2.0.so.0(+0x65def)[0x45bdef]
/lib/tls/i686/cmov/libpthread.so.0(+0x596e)[0xa6f96e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0x355a4e]
======= Memory map: ========
00110000-00248000 r-xp 00000000 08:01 524336     /lib/i686/cmov/libcrypto.so.0.9.8
00248000-00250000 r--p 00137000 08:01 524336     /lib/i686/cmov/libcrypto.so.0.9.8
00250000-0025e000 rw-p 0013f000 08:01 524336     /lib/i686/cmov/libcrypto.so.0.9.8
0025e000-00262000 rw-p 00000000 00:00 0 
00262000-00286000 r-xp 00000000 08:01 524954     /lib/tls/i686/cmov/libm-2.11.1.so
00286000-00287000 r--p 00023000 08:01 524954     /lib/tls/i686/cmov/libm-2.11.1.so
00287000-00288000 rw-p 00024000 08:01 524954     /lib/tls/i686/cmov/libm-2.11.1.so
00288000-003db000 r-xp 00000000 08:01 524944     /lib/tls/i686/cmov/libc-2.11.1.so
003db000-003dc000 ---p 00153000 08:01 524944     /lib/tls/i686/cmov/libc-2.11.1.so
003dc000-003de000 r--p 00153000 08:01 524944     /lib/tls/i686/cmov/libc-2.11.1.so
003de000-003df000 rw-p 00155000 08:01 524944     /lib/tls/i686/cmov/libc-2.11.1.so
003df000-003e2000 rw-p 00000000 00:00 0 
003e2000-003e5000 r-xp 00000000 08:01 9178725    /usr/lib/libpyglib-2.0-python2.6.so.0.0.0
003e5000-003e6000 r--p 00002000 08:01 9178725    /usr/lib/libpyglib-2.0-python2.6.so.0.0.0
003e6000-003e7000 rw-p 00003000 08:01 9178725    /usr/lib/libpyglib-2.0-python2.6.so.0.0.0
003e7000-003ea000 r-xp 00000000 08:01 9178901    /usr/lib/libxcb-render-util.so.0.0.0
003ea000-003eb000 r--p 00002000 08:01 9178901    /usr/lib/libxcb-render-util.so.0.0.0
003eb000-003ec000 rw-p 00003000 08:01 9178901    /usr/lib/libxcb-render-util.so.0.0.0
003ed000-003f4000 r-xp 00000000 08:01 524966     /lib/tls/i686/cmov/librt-2.11.1.so
003f4000-003f5000 r--p 00006000 08:01 524966     /lib/tls/i686/cmov/librt-2.11.1.so
003f5000-003f6000 rw-p 00007000 08:01 524966     /lib/tls/i686/cmov/librt-2.11.1.so
003f6000-004be000 r-xp 00000000 08:01 532229     /lib/libglib-2.0.so.0.2400.1
004be000-004bf000 r--p 000c7000 08:01 532229     /lib/libglib-2.0.so.0.2400.1
004bf000-004c0000 rw-p 000c8000 08:01 532229     /lib/libglib-2.0.so.0.2400.1
004c0000-004c5000 r-xp 00000000 08:01 9178188    /usr/lib/libffi.so.5.0.10
004c5000-004c6000 ---p 00005000 08:01 9178188    /usr/lib/libffi.so.5.0.10
004c6000-004c7000 r--p 00005000 08:01 9178188    /usr/lib/libffi.so.5.0.10
004c7000-004c8000 rw-p 00006000 08:01 9178188    /usr/lib/libffi.so.5.0.10
004c8000-004d8000 r-xp 00000000 08:01 524965     /lib/tls/i686/cmov/libresolv-2.11.1.so
004d8000-004d9000 r--p 00010000 08:01 524965     /lib/tls/i686/cmov/libresolv-2.11.1.so
004d9000-004da000 rw-p 00011000 08:01 524965     /lib/tls/i686/cmov/libresolv-2.11.1.so
004da000-004dc000 rw-p 00000000 00:00 0 
004dc000-004ed000 r-xp 00000000 08:01 9311871    /usr/lib/pyshared/python2.6/cairo/_cairo.so
004ed000-004ee000 r--p 00010000 08:01 9311871    /usr/lib/pyshared/python2.6/cairo/_cairo.so
004ee000-004f1000 rw-p 00011000 08:01 9311871    /usr/lib/pyshared/python2.6/cairo/_cairo.so
004f1000-0051f000 r-xp 00000000 08:01 9178190    /usr/lib/libfontconfig.so.1.4.4
0051f000-00520000 r--p 0002d000 08:01 9178190    /usr/lib/libfontconfig.so.1.4.4
00520000-00521000 rw-p 0002e000 08:01 9178190    /usr/lib/libfontconfig.so.1.4.4
00521000-00527000 r-xp 00000000 08:01 9178903    /usr/lib/libxcb-render.so.0.0.0
00527000-00528000 r--p 00005000 08:01 9178903    /usr/lib/libxcb-render.so.0.0.0
00528000-00529000 rw-p 00006000 08:01 9178903    /usr/lib/libxcb-render.so.0.0.0
00529000-0052d000 r-xp 00000000 08:01 9177909    /usr/lib/libXdmcp.so.6.0.0
0052d000-0052e000 r--p 00003000 08:01 9177909    /usr/lib/libXdmcp.so.6.0.0
0052e000-0052f000 rw-p 00004000 08:01 9177909    /usr/lib/libXdmcp.so.6.0.0
0052f000-00542000 r-xp 00000000 08:01 524486     /lib/libz.so.1.2.3.3
00542000-00543000 r--p 00012000 08:01 524486     /lib/libz.so.1.2.3.3
00543000-00544000 rw-p 00013000 08:01 524486     /lib/libz.so.1.2.3.3
00544000-00567000 r-xp 00000000 08:01 524420     /lib/libpng12.so.0.42.0
00567000-00568000 r--p 00022000 08:01 524420     /lib/libpng12.so.0.42.0
00568000-00569000 rw-p 00023000 08:01 524420     /lib/libpng12.so.0.42.0
0056a000-00586000 r-xp 00000000 08:01 9311901    /usr/lib/pyshared/python2.6/gtk-2.0/gobject/_gobject.so
00586000-00587000 r--p 0001b000 08:01 9311901    /usr/lib/pyshared/python2.6/gtk-2.0/gobject/_gobject.so
00587000-00589000 rw-p 0001c000 08:01 9311901    /usr/lib/pyshared/python2.6/gtk-2.0/gobject/_gobject.so
00589000-005e0000 r-xp 00000000 08:01 9178669    /usr/lib/libpixman-1.so.0.16.4
005e0000-005e2000 r--p 00057000 08:01 9178669    /usr/lib/libpixman-1.so.0.16.4
005e2000-005e3000 rw-p 00059000 08:01 9178669    /usr/lib/libpixman-1.so.0.16.4
005e3000-005e5000 r-xp 00000000 08:01 9177921    /usr/lib/libXinerama.so.1.0.0
005e5000-005e6000 r--p 00001000 08:01 9177921    /usr/lib/libXinerama.so.1.0.0
005e6000-005e7000 rw-p 00002000 08:01 9177921    /usr/lib/libXinerama.so.1.0.0
005e7000-005ed000 r-xp 00000000 08:01 9177931    /usr/lib/libXrandr.so.2.2.0
005ed000-005ee000 r--p 00005000 08:01 9177931    /usr/lib/libXrandr.so.2.2.0
005ee000-005ef000 rw-p 00006000 08:01 9177931    /usr/lib/libXrandr.so.2.2.0
005f0000-005f3000 r-xp 00000000 08:01 9176748    /usr/lib/libgmodule-2.0.so.0.2400.1
005f3000-005f4000 r--p 00002000 08:01 9176748    /usr/lib/libgmodule-2.0.so.0.2400.1
005f4000-005f5000 rw-p 00003000 08:01 9176748    /usr/lib/libgmodule-2.0.so.0.2400.1
005f5000-0060d000 r-xp 00000000 08:01 9178905    /usr/lib/libxcb.so.1.1.0
0060d000-0060e000 r--p 00017000 08:01 9178905    /usr/lib/libxcb.so.1.1.0
0060e000-0060f000 rw-p 00018000 08:01 9178905    /usr/lib/libxcb.so.1.1.0
0060f000-00610000 r-xp 00000000 00:00 0          [vdso]
00610000-00687000 r-xp 00000000 08:01 9178031    /usr/lib/libcairo.so.2.10800.10
00687000-00689000 r--p 00076000 08:01 9178031    /usr/lib/libcairo.so.2.10800.10
00689000-0068a000 rw-p 00078000 08:01 9178031    /usr/lib/libcairo.so.2.10800.10
0068a000-0068e000 r-xp 00000000 08:01 9176749    /usr/lib/libgthread-2.0.so.0.2400.1
0068e000-0068f000 r--p 00003000 08:01 9176749    /usr/lib/libgthread-2.0.so.0.2400.1
0068f000-00690000 rw-p 00004000 08:01 9176749    /usr/lib/libgthread-2.0.so.0.2400.1
00690000-0072a000 r-xp 00000000 08:01 9176750    /usr/lib/libgio-2.0.so.0.2400.1
0072a000-0072b000 ---p 0009a000 08:01 9176750    /usr/lib/libgio-2.0.so.0.2400.1
0072b000-0072c000 r--p 0009a000 08:01 9176750    /usr/lib/libgio-2.0.so.0.2400.1
0072c000-0072d000 rw-p 0009b000 08:01 9176750    /usr/lib/libgio-2.0.so.0.2400.1
0072d000-0072e000 rw-p 00000000 00:00 0 
0072e000-0079f000 r-xp 00000000 08:01 9175937    /usr/lib/libfreetype.so.6.3.22
0079f000-007a3000 r--p 00070000 08:01 9175937    /usr/lib/libfreetype.so.6.3.22
007a3000-007a4000 rw-p 00074000 08:01 9175937    /usr/lib/libfreetype.so.6.3.22
007a4000-00817000 r-xp 00000000 08:01 9178127    /usr/lib/libdirectfb-1.2.so.0.8.0
00817000-00818000 ---p 00073000 08:01 9178127    /usr/lib/libdirectfb-1.2.so.0.8.0
00818000-00819000 r--p 00073000 08:01 9178127    /usr/lib/libdirectfb-1.2.so.0.8.0
00819000-0081a000 rw-p 00074000 08:01 9178127    /usr/lib/libdirectfb-1.2.so.0.8.0
0081a000-0081b000 rw-p 00000000 00:00 0 
0081b000-0081d000 r-xp 00000000 08:01 9177907    /usr/lib/libXdamage.so.1.1.0
0081d000-0081e000 r--p 00001000 08:01 9177907    /usr/lib/libXdamage.so.1.1.0
0081e000-0081f000 rw-p 00002000 08:01 9177907    /usr/lib/libXdamage.so.1.1.0
0081f000-00820000 r-xp 00000000 08:01 9311859    /usr/lib/pyshared/python2.6/_dbus_glib_bindings.so
00820000-00821000 r--p 00001000 08:01 9311859    /usr/lib/pyshared/python2.6/_dbus_glib_bindings.so
00821000-00822000 rw-p 00002000 08:01 9311859    /usr/lib/pyshared/python2.6/_dbus_glib_bindings.so
00823000-00860000 r-xp 00000000 08:01 9176747    /usr/lib/libgobject-2.0.so.0.2400.1
00860000-00861000 r--p 0003c000 08:01 9176747    /usr/lib/libgobject-2.0.so.0.2400.1
00861000-00862000 rw-p 0003d000 08:01 9176747    /usr/lib/libgobject-2.0.so.0.2400.1
00862000-00886000 r-xp 00000000 08:01 524364     /lib/libexpat.so.1.5.2
00886000-00888000 r--p 00024000 08:01 524364     /lib/libexpat.so.1.5.2
00888000-00889000 rw-p 00026000 08:01 524364     /lib/libexpat.so.1.5.2
00889000-008a2000 r-xp 00000000 08:01 9176755    /usr/lib/libatk-1.0.so.0.3009.1
008a2000-008a3000 ---p 00019000 08:01 9176755    /usr/lib/libatk-1.0.so.0.3009.1
008a3000-008a4000 r--p 00019000 08:01 9176755    /usr/lib/libatk-1.0.so.0.3009.1
008a4000-008a5000 rw-p 0001a000 08:01 9176755    /usr/lib/libatk-1.0.so.0.3009.1
008a5000-008ca000 r-xp 00000000 08:01 9178643    /usr/lib/libpangoft2-1.0.so.0.2800.0
008ca000-008cb000 r--p 00024000 08:01 9178643    /usr/lib/libpangoft2-1.0.so.0.2800.0
008cb000-008cc000 rw-p 00025000 08:01 9178643    /usr/lib/libpangoft2-1.0.so.0.2800.0
008cc000-008e4000 r-xp 00000000 08:01 9176939    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
008e4000-008e5000 r--p 00017000 08:01 9176939    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
008e5000-008e6000 rw-p 00018000 08:01 9176939    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
008e6000-008ea000 r-xp 00000000 08:01 9177913    /usr/lib/libXfixes.so.3.1.0
008ea000-008eb000 r--p 00003000 08:01 9177913    /usr/lib/libXfixes.so.3.1.0
008eb000-008ec000 rw-p 00004000 08:01 9177913    /usr/lib/libXfixes.so.3.1.0
008ec000-008ed000 r-xp 00000000 08:01 9175496    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
008ed000-008ee000 r--p 00000000 08:01 9175496    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
008ee000-008ef000 rw-p 00001000 08:01 9175496    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
008f0000-00931000 r-xp 00000000 08:01 9311894    /usr/lib/pyshared/python2.6/gtk-2.0/gio/_gio.so
00931000-00934000 r--p 00040000 08:01 9311894    /usr/lib/pyshared/python2.6/gtk-2.0/gio/_gio.so
00934000-0093a000 rw-p 00043000 08:01 9311894    /usr/lib/pyshared/python2.6/gtk-2.0/gio/_gio.so
0093d000-00974000 r-xp 00000000 08:01 524349     /lib/libdbus-1.so.3.4.0
00974000-00975000 r--p 00036000 08:01 524349     /lib/libdbus-1.so.3.4.0
00975000-00976000 rw-p 00037000 08:01 524349     /lib/libdbus-1.so.3.4.0
00976000-00979000 r-xp 00000000 08:01 9311888    /usr/lib/pyshared/python2.6/gtk-2.0/pangocairo.so
00979000-0097a000 r--p 00002000 08:01 9311888    /usr/lib/pyshared/python2.6/gtk-2.0/pangocairo.so
0097a000-0097b000 rw-p 00003000 08:01 9311888    /usr/lib/pyshared/python2.6/gtk-2.0/pangocairo.so
0097b000-009aa000 r-xp 00000000 08:01 9178215    /usr/lib/libgconf-2.so.4.1.5
009aa000-009ab000 r--p 0002e000 08:01 9178215    /usr/lib/libgconf-2.so.4.1.5
009ab000-009ad000 rw-p 0002f000 08:01 9178215    /usr/lib/libgconf-2.so.4.1.5
009ad000-009ed000 r-xp 00000000 08:01 9178639    /usr/lib/libpango-1.0.so.0.2800.0
009ed000-009ee000 ---p 00040000 08:01 9178639    /usr/lib/libpango-1.0.so.0.2800.0
009ee000-009ef000 r--p 00040000 08:01 9178639    /usr/lib/libpango-1.0.so.0.2800.0
009ef000-009f0000 rw-p 00041000 08:01 9178639    /usr/lib/libpango-1.0.so.0.2800.0
009f0000-009fe000 r-xp 00000000 08:01 9177911    /usr/lib/libXext.so.6.4.0
009fe000-009ff000 r--p 0000d000 08:01 9177911    /usr/lib/libXext.so.6.4.0
009ff000-00a00000 rw-p 0000e000 08:01 9177911    /usr/lib/libXext.so.6.4.0

```


Quite long I know. The other news is NOW when I use it through terminal, it will just give me "Aborted" for the reason of the crash. :/


Anybody know if this is an easy fix?

---

### Post by aperture123 on 2010-11-10
...bump?

I've got the video mkv with subs converted to mp4 with subs hardencoded through my vista, but still no answer on the arista. I'd rather not use windows, so is there any fix to this problem?

---

