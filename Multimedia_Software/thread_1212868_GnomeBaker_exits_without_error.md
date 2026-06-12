---
title: "GnomeBaker exits without error"
date: 2009-07-14
forum: Multimedia Software
---

### Post by parovelb on 2009-07-14
Hello Ubu People!
I am running the Jaunty on a Dell Latitude D400 notebook with an external cd burner. I had to burn some audio cds for my car which unfortunately digest only discs burned at low speed. I burned two discs: one with GnomeBaker and the other with K3B resulting GnomeBaker to be the keeper. Uninstalled K3B and... GnomeBaker is suddenly exiting without any reason, randomly, just after adding some files to the project. There are no errors reported. Any ideas?

---

### Post by hansdown on 2009-07-14
Hi parovelb.

When K3B was removed, it probably removed some dependencies that gnomebaker

also relies on.

Try reinstalling gnomebaker, and see if it helps.

---

### Post by parovelb on 2009-07-14
I have reinstalled GnomeBaker without getting any improvements. However here it is what I have managed to get from the terminal:
[I]
(gnomebaker:12329): GStreamer-CRITICAL **: gst_pad_link: assertion `GST_PAD_IS_SINK (sinkpad)' failed

***MEMORY-ERROR***: gnomebaker[12329]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted
[/I]

---

### Post by parovelb on 2009-07-15
the latest error

*** glibc detected *** gnomebaker: corrupted double-linked list: 0x09a01978 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7233604]
/lib/tls/i686/cmov/libc.so.6[0xb7235383]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb72355b6]
/usr/lib/libcairo.so.2(cairo_pattern_destroy+0xa6)[0xb77b0a06]
/usr/lib/libcairo.so.2[0xb77a0a3d]
/usr/lib/libcairo.so.2(cairo_destroy+0x8e)[0xb779a8ee]
/usr/lib/libgdk-x11-2.0.so.0[0xb7933756]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_begin_paint_region+0x1bb)[0xb7935a8b]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x51e)[0xb7ac155e]
/usr/lib/libgdk-x11-2.0.so.0[0xb7935e95]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xff)[0xb79364af]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a384cf]
/usr/lib/libgdk-x11-2.0.so.0[0xb79198fb]
/usr/lib/libglib-2.0.so.0[0xb75c8c81]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb75cab88]
/usr/lib/libglib-2.0.so.0[0xb75ce0eb]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x68)[0xb75ce268]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_iteration+0x34)[0xb7ac1634]
gnomebaker(media_info_new+0x275)[0x8074345]
gnomebaker[0x807f7ed]
gnomebaker[0x808051a]
gnomebaker(project_add_selection+0xab)[0x8075dcb]
gnomebaker(gnomebaker_on_add_files+0x130)[0x80617f0]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb76663a4]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb7658c7b]
/usr/lib/libgobject-2.0.so.0[0xb766ee57]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb76704b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_by_name+0x1a3)[0xb76707e3]
/usr/lib/libgtk-x11-2.0.so.0[0xb7b9bee0]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb76663a4]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb7658c7b]
/usr/lib/libgobject-2.0.so.0[0xb766ee57]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb76704b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7670936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_clicked+0x8a)[0xb7a0cbda]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a0e1f8]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb76663a4]
/usr/lib/libgobject-2.0.so.0[0xb76573d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb7658c7b]
/usr/lib/libgobject-2.0.so.0[0xb766e6c0]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7b9)[0xb76704b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7670936]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_released+0x8a)[0xb7a0cc7a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a0ccb3]
/usr/lib/libgtk-x11-2.0.so.0[0xb7ac7526]
/usr/lib/libgobject-2.0.so.0[0xb76573d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb7658c7b]
/usr/lib/libgobject-2.0.so.0[0xb766eaff]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64f)[0xb767034f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7670936]
/usr/lib/libgtk-x11-2.0.so.0[0xb7be22ae]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xec)[0xb7abff7c]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2e7)[0xb7ac1327]
/usr/lib/libgdk-x11-2.0.so.0[0xb794e34a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb75cab88]
/usr/lib/libglib-2.0.so.0[0xb75ce0eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb75ce5ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7ac17d9]
gnomebaker(main+0x23e)[0x80564ee]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb71da775]
gnomebaker[0x8056171]
======= Memory map: ========
08048000-0808e000 r-xp 00000000 08:01 4221859    /usr/bin/gnomebaker
0808e000-0808f000 r--p 00046000 08:01 4221859    /usr/bin/gnomebaker
0808f000-08090000 rw-p 00047000 08:01 4221859    /usr/bin/gnomebaker
092ef000-09a3c000 rw-p 092ef000 00:00 0          [heap]
b4800000-b4821000 rw-p b4800000 00:00 0 
b4821000-b4900000 ---p b4821000 00:00 0 
b496c000-b4979000 r-xp 00000000 08:01 4472897    /lib/libgcc_s.so.1
b4979000-b497a000 r--p 0000c000 08:01 4472897    /lib/libgcc_s.so.1
b497a000-b497b000 rw-p 0000d000 08:01 4472897    /lib/libgcc_s.so.1
b4989000-b498b000 r-xp 00000000 08:01 2646208    /usr/lib/gconv/ISO8859-15.so
b498b000-b498c000 r--p 00001000 08:01 2646208    /usr/lib/gconv/ISO8859-15.so
b498c000-b498d000 rw-p 00002000 08:01 2646208    /usr/lib/gconv/ISO8859-15.so
b498d000-b499d000 r-xp 00000000 08:01 4220942    /usr/lib/libgstrtp-0.10.so.0.16.0
b499d000-b499e000 r--p 0000f000 08:01 4220942    /usr/lib/libgstrtp-0.10.so.0.16.0
b499e000-b499f000 rw-p 00010000 08:01 4220942    /usr/lib/libgstrtp-0.10.so.0.16.0
b499f000-b49b4000 r-xp 00000000 08:01 4219550    /usr/lib/libbluetooth.so.3.2.1
b49b4000-b49b5000 r--p 00014000 08:01 4219550    /usr/lib/libbluetooth.so.3.2.1
b49b5000-b49b6000 rw-p 00015000 08:01 4219550    /usr/lib/libbluetooth.so.3.2.1
b49b6000-b49c2000 r-xp 00000000 08:01 2850890    /usr/lib/gstreamer-0.10/libgstsubparse.so
b49c2000-b49c3000 r--p 0000b000 08:01 2850890    /usr/lib/gstreamer-0.10/libgstsubparse.so
b49c3000-b49c4000 rw-p 0000c000 08:01 2850890    /usr/lib/gstreamer-0.10/libgstsubparse.so
b49c4000-b49e3000 r-xp 00000000 08:01 4236519    /usr/lib/gstreamer-0.10/libgstbluetooth.so
b49e3000-b49e4000 ---p 0001f000 08:01 4236519    /usr/lib/gstreamer-0.10/libgstbluetooth.so
b49e4000-b49e5000 r--p 0001f000 08:01 4236519    /usr/lib/gstreamer-0.10/libgstbluetooth.so
b49e5000-b49e6000 rw-p 00020000 08:01 4236519    /usr/lib/gstreamer-0.10/libgstbluetooth.so
b49e6000-b49f3000 r-xp 00000000 08:01 4235567    /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
b49f3000-b49f4000 r--p 0000c000 08:01 4235567    /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
b49f4000-b49f5000 rw-p 0000d000 08:01 4235567    /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
b49f5000-b4a01000 r-xp 00000000 08:01 2850894    /usr/lib/gstreamer-0.10/libgsttypefindfunctions.so
b4a01000-b4a02000 r--p 0000b000 08:01 2850894    /usr/lib/gstreamer-0.10/libgsttypefindfunctions.so
b4a02000-b4a04000 rw-p 0000c000 08:01 2850894    /usr/lib/gstreamer-0.10/libgsttypefindfunctions.so
b4a04000-b4a0e000 r-xp 00000000 08:01 4220936    /usrAborted

---

### Post by hansdown on 2009-07-15
I don't know how much help this will be, but a search for```
 glibc detected 
```links to this post.

[http://ubuntuforums.org/showthread.php?t=175050](http://ubuntuforums.org/showthread.php?t=175050)

The entire search output is here.

[http://www.google.ca/search?q=glibc+detected&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=glibc+detected&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Gnomebaker is a beautiful program. I wish I knew more about this.

---

