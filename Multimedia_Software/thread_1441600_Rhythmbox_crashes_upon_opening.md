---
title: "Rhythmbox crashes upon opening"
date: 2010-03-28
forum: Multimedia Software
---

### Post by Weepleman on 2010-03-28
Whenever I open Rhythmbox, it looks like it is about to work, but crashes.  I get this when I run it from the command line.
```
** (rhythmbox:3002): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3002): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:3002): Rhythmbox-WARNING **: Could not open device /dev/radio0

(<unknown>:3015): GLib-WARNING **: g_set_prgname() called multiple times

(rhythmbox:3002): GLib-CRITICAL **: g_sequence_get: assertion `iter != NULL' failed
Segmentation fault

```I have no idea what all that means though.

I found out that this was just a problem of having a certain album ripped, so this does not happen any more.  Still, this should not happen, should it?

---

### Post by qwestlabz on 2010-04-09
I'm having the same problem but my output is:

** (rhythmbox:3925): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3925): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory

(rhythmbox:3925): Rhythmbox-WARNING **: Could not open device /dev/radio0

(<unknown>:3937): GLib-WARNING **: g_set_prgname() called multiple times

(rhythmbox:3925): GLib-CRITICAL **: g_sequence_get: assertion `iter != NULL' failed
Segmentation fault.


If anyone can provide any help that would be awesome.

---

### Post by w33k on 2010-04-26
I get seg fault as well with the following message:

```
** (rhythmbox:4747): WARNING **: iTunesDB and ArtworkDB artwork sizes inconsistent (0+1 != 0)

Segmentation fault
```

---

### Post by razor7 on 2010-04-30
Whoha, lucky you!, i just get this

"** (rhythmbox:4293): DEBUG: Loading the real store page
** (rhythmbox:4293): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
Fallo de segmentación
"

I filed a bug report, p'lease mark it as you are affected too. [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/569524](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/569524)

---

### Post by Rosemachinegun on 2010-05-01
I'm getting a similar problem since upgrading to Lucid. Unless I disable rhythmbox-plugins via Synaptic the program crashes on me on load with a Seg Fault. :( Until someone finds a fix I can't see any of the new RB features...

---

### Post by kaurie on 2010-05-02
I have just upgraded by Ubuntu 64 bit system to  10.04 and Rhythmbox fails to open

when run from the keyboard there is a segmentation fault 
sudo gives more information

Has anyone any idea what I should do?

~$ rhythmbox
** (rhythmbox:1870): DEBUG: Loading the real store page
** (rhythmbox:1870): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
Segmentation fault


$ sudo rhythmbox

(rhythmbox:2042): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

(rhythmbox:2042): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:2042): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2042): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(rhythmbox:2042): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:2042): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(rhythmbox:2042): Gdk-CRITICAL **: gdk_drawable_get_size: assertion `GDK_IS_DRAWABLE (drawable)' failed

(rhythmbox:2042): Gdk-CRITICAL **: gdk_window_invalidate_rect_full: assertion `GDK_IS_WINDOW (window)' failed
** (rhythmbox:2042): DEBUG: Loading the real store page
** (rhythmbox:2042): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
Segmentation fault

---

### Post by DJ_Cripple on 2010-05-02
+1 

rhythmbox segfaults regularly for me since upgrading to lucid. on x64.  tried uninstalling ubuntuone plugin, still segfaults if i try and click last.fm.

---

### Post by scollyer on 2010-05-02
This has fixed it for me....

$ sudo apt-get remove rhythmbox-ubuntuone-music-store

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdb4.6 libreadline5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  rhythmbox-ubuntuone-music-store
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 324kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 169398 files and directories currently installed.)
Removing rhythmbox-ubuntuone-music-store ...

---

### Post by kaurie on 2010-05-03
Thanks - 
[INDENT][/INDENT]sudo apt-get remove rhythmbox-ubuntuone-music-store
worked for me too

Note the first time I tried Applications - Sound and Video - rhythmbox
did not work

but after running rhythmbox on the terminal it worked

I wonder why sudo apt-get remove rhythmbox-ubuntuone-music-store
works:confused:

Thanks a million

---

### Post by vegham on 2010-05-09
My problem still persists. Suggestion?

v@stealth:~$ rhythmbox
** (rhythmbox:5137): DEBUG: Loading the real store page
** (rhythmbox:5137): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
*** glibc detected *** rhythmbox: double free or corruption (fasttop): 0x00000000022b5a90 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f6c545215b6]
/lib/libc.so.6(cfree+0x73)[0x7f6c54527e53]
/lib/libusb-0.1.so.4(usb_destroy_configuration+0x156)[0x7f6c41d981a6]
/lib/libusb-0.1.so.4(usb_free_dev+0x9)[0x7f6c41d978c9]
/lib/libusb-0.1.so.4(usb_find_devices+0xce)[0x7f6c41d97c9e]
/usr/lib/libmtp.so.8(+0x1caf5)[0x7f6c41fbbaf5]
/usr/lib/libmtp.so.8(LIBMTP_Detect_Raw_Devices+0x1f)[0x7f6c41fbd47f]
/usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so(+0x7a08)[0x7f6c421eda08]
/usr/lib/librhythmbox-core.so.0(rb_marshal_OBJECT__OBJECT+0x98)[0x7f6c598bbe98]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f6c555eb5de]
/usr/lib/libgobject-2.0.so.0(+0x21598)[0x7f6c555ff598]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x639)[0x7f6c556008b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f6c55601033]
/usr/lib/librhythmbox-core.so.0(+0x5975a)[0x7f6c5983e75a]
/usr/lib/librhythmbox-core.so.0(rb_removable_media_manager_scan+0x20d)[0x7f6c5983e9dd]
/usr/lib/librhythmbox-core.so.0(+0x481f5)[0x7f6c5982d1f5]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f6c54f328c2]
/lib/libglib-2.0.so.0(+0x42748)[0x7f6c54f36748]
/lib/libglib-2.0.so.0(g_main_loop_run+0x195)[0x7f6c54f36c55]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f6c58a91af7]
rhythmbox(main+0x3cb)[0x403e8b]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f6c544c8c4d]
rhythmbox[0x403919]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:03 5637327                            /usr/bin/rhythmbox
00607000-00608000 r--p 00007000 08:03 5637327                            /usr/bin/rhythmbox
00608000-00609000 rw-p 00008000 08:03 5637327                            /usr/bin/rhythmbox
011bc000-029c2000 rw-p 00000000 00:00 0                                  [heap]
7f6c344e0000-7f6c34540000 rw-s 00000000 00:04 4128794                    /SYSV00000000 (deleted)
7f6c34540000-7f6c34580000 rw-p 00000000 00:00 0 
7f6c3458f000-7f6c349a1000 rw-p 00000000 00:00 0 
7f6c349a1000-7f6c349e0000 r-xp 00000000 08:03 5639506                    /usr/lib/libibus.so.1.0.0
7f6c349e0000-7f6c34be0000 ---p 0003f000 08:03 5639506                    /usr/lib/libibus.so.1.0.0
7f6c34be0000-7f6c34be2000 r--p 0003f000 08:03 5639506                    /usr/lib/libibus.so.1.0.0
7f6c34be2000-7f6c34be3000 rw-p 00041000 08:03 5639506                    /usr/lib/libibus.so.1.0.0
7f6c34be3000-7f6c34be4000 rw-p 00000000 00:00 0 
7f6c34be4000-7f6c34be9000 r-xp 00000000 08:03 5643259                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f6c34be9000-7f6c34de9000 ---p 00005000 08:03 5643259                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f6c34de9000-7f6c34dea000 r--p 00005000 08:03 5643259                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f6c34dea000-7f6c34deb000 rw-p 00006000 08:03 5643259                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f6c34deb000-7f6c34e4b000 rw-s 00000000 00:04 4096024                    /SYSV00000000 (deleted)
7f6c34e4b000-7f6c34ed7000 r--p 00000000 08:03 5797103                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7f6c34ed7000-7f6c34ed8000 ---p 00000000 00:00 0 
7f6c34ed8000-7f6c356d8000 rw-p 00000000 00:00 0 
7f6c356d8000-7f6c356da000 r-xp 00000000 08:03 5642648                    /usr/lib/gconv/ISO8859-1.so
7f6c356da000-7f6c358d9000 ---p 00002000 08:03 5642648                    /usr/lib/gconv/ISO8859-1.so
7f6c358d9000-7f6c358da000 r--p 00001000 08:03 5642648                    /usr/lib/gconv/ISO8859-1.so
7f6c358da000-7f6c358db000 rw-p 00002000 08:03 5642648                    /usr/lib/gconv/ISO8859-1.so
7f6c358db000-7f6c358e6000 r-xp 00000000 08:03 5641127                    /usr/lib/enchant/libenchant_ispell.so
7f6c358e6000-7f6c35ae6000 ---p 0000b000 08:03 5641127                    /usr/lib/enchant/libenchant_ispell.so
7f6c35ae6000-7f6c35ae7000 r--p 0000b000 08:03 5641127                    /usr/lib/enchant/libenchant_ispell.so
7f6c35ae7000-7f6c35ae8000 rw-p 0000c000 08:03 5641127                    /usr/lib/enchant/libenchant_ispell.so
7f6c35ae8000-7f6c35b24000 r-xp 00000000 08:03 5639502                    /usr/lib/libhunspell-1.2.so.0.0.0
7f6c35b24000-7f6c35d23000 ---p 0003c000 08:03 5639502                    /usr/lib/libhunspell-1.2.so.0.0.0
7f6c35d23000-7f6c35d24000 r--p 0003b000 08:03 5639502                    /usr/lib/libhunspell-1.2.so.0.0.0
7f6c35d24000-7f6c35d28000 rw-p 0003c000 08:03 5639502                    /usr/lib/libhunspell-1.2.so.0.0.0
7f6c35d28000-7f6c35d2d000 r-xp 00000000 08:03 5641128                    /usr/lib/enchant/libenchant_myspell.so
7f6c35d2d000-7f6c35f2c000 ---p 00005000 08:03 5641128                    /usr/lib/enchant/libenchant_myspell.so
7f6c35f2c000-7f6c35f2d000 r--p 00004000 08:03 5641128                    /usr/lib/enchant/libenchant_myspell.so
7f6c35f2d000-7f6c35f2e000 rw-p 00005000 08:03 5641128                    /usr/lib/enchant/libenchant_myspell.so
7f6c35f2e000-7f6c35fdc000 r-xp 00000000 08:03 5639032                    /usr/lib/libaspell.so.15.1.4
7f6c35fdc000-7f6c361dc000 ---p 000ae000 08:03 5639032                    /usr/lib/libaspell.so.15.1.4
7f6c361dc000-7f6c361e2000 r--p 000ae000 08:03 5639032                    /usr/lib/libaspell.so.15.1.4
7f6c361e2000-7f6c361e3000 rw-p 000b4000 08:03 5639032                    /usr/lib/libaspell.so.15.1.4
7f6c361e3000-7f6c361eb000 rw-p 00000000 00:00 0 
7f6c361eb000-7f6c361ed000 r-xp 00000000 08:03 5641125                    /usr/lib/enchant/libenchant_aspell.so
7f6c361ed000-7f6c363ec000 ---p 00002000 08:03 5641125                    /usr/lib/enchant/libenchant_aspell.so
7f6c363ec000-7f6c363ed000 r--p 00001000 08:03 5641125                    /usr/lib/enchant/libenchant_aspell.so
7f6c363ed000-7f6c363ee000 rw-p 00002000 08:03 5641125                    /usr/lib/enchant/libenchant_aspell.so
7f6c363ee000-7f6c363f9000 r-xp 00000000 08:03 5641126                    /usr/lib/enchant/libenchant_hspell.so
7f6c363f9000-7f6c365f8000 ---p 0000b000 08:03 5641126                    /usr/lib/enchant/libenchant_hspell.so
7f6c365f8000-7f6c365f9000 r--p 0000a000 08:03 5641126                    /usr/lib/enchant/libenchant_hspell.so
7f6c365f9000-7f6c365fc000 rw-p 0000b000 08:03 5641126                    /usr/lib/enchant/libenchant_hspell.so
7f6c365fc000-7f6c365fd000 ---p 00000000 00:00 0 
7f6c365fd000-7f6c36dfd000 rw-p 00000000 00:00 0 
7f6c36dfd000-7f6c36dfe000 ---p 00000000 00:00 0 
7f6c36dfe000-7f6c3770e000 rw-p 00000000 00:00 0 
7f6c3770e000-7f6c38653000 r--p 00000000 08:03 5639514         Aborted
v@stealth:~$ sudo apt-get --purge remove rhythmbox-ubuntuone-music-store
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  rhythmbox-ubuntuone-music-store*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 324kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 150161 files and directories currently installed.)
Removing rhythmbox-ubuntuone-music-store ...
Purging configuration files for rhythmbox-ubuntuone-music-store ...
v@stealth:~$ rhythmbox
Segmentation fault
v@stealth:~$ sudo apt-get --reinstall install rhytmbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rhytmbox
v@stealth:~$ sudo apt-get --reinstall install rhythmbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/1,279kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 150151 files and directories currently installed.)
Preparing to replace rhythmbox 0.12.8-0ubuntu4 (using .../rhythmbox_0.12.8-0ubuntu4_amd64.deb) ...
Unpacking replacement rhythmbox ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up rhythmbox (0.12.8-0ubuntu4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
v@stealth:~$ rhythmbox
*** glibc detected *** rhythmbox: double free or corruption (fasttop): 0x00000000016576b0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f8de19285b6]
/lib/libc.so.6(cfree+0x73)[0x7f8de192ee53]
/lib/libusb-0.1.so.4(usb_destroy_configuration+0x156)[0x7f8dcb0a61a6]
/lib/libusb-0.1.so.4(usb_free_dev+0x9)[0x7f8dcb0a58c9]
/lib/libusb-0.1.so.4(usb_find_devices+0xce)[0x7f8dcb0a5c9e]
/usr/lib/libmtp.so.8(+0x1caf5)[0x7f8dcb2c9af5]
/usr/lib/libmtp.so.8(LIBMTP_Detect_Raw_Devices+0x1f)[0x7f8dcb2cb47f]
/usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so(+0x7a08)[0x7f8dcb4fba08]
/usr/lib/librhythmbox-core.so.0(rb_marshal_OBJECT__OBJECT+0x98)[0x7f8de6cc2e98]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x15e)[0x7f8de29f25de]
/usr/lib/libgobject-2.0.so.0(+0x21598)[0x7f8de2a06598]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x639)[0x7f8de2a078b9]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83)[0x7f8de2a08033]
/usr/lib/librhythmbox-core.so.0(+0x5975a)[0x7f8de6c4575a]
/usr/lib/librhythmbox-core.so.0(rb_removable_media_manager_scan+0x20d)[0x7f8de6c459dd]
/usr/lib/librhythmbox-core.so.0(+0x481f5)[0x7f8de6c341f5]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f2)[0x7f8de23398c2]
/lib/libglib-2.0.so.0(+0x42748)[0x7f8de233d748]
/lib/libglib-2.0.so.0(g_main_loop_run+0x195)[0x7f8de233dc55]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f8de5e98af7]
rhythmbox(main+0x3cb)[0x403e8b]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f8de18cfc4d]
rhythmbox[0x403919]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:03 5647173                            /usr/bin/rhythmbox
00607000-00608000 r--p 00007000 08:03 5647173                            /usr/bin/rhythmbox
00608000-00609000 rw-p 00008000 08:03 5647173                            /usr/bin/rhythmbox
00759000-01707000 rw-p 00000000 00:00 0                                  [heap]
7f8dc9d9d000-7f8dc9dfd000 rw-s 00000000 00:04 4259866                    /SYSV00000000 (deleted)
7f8dc9dfd000-7f8dc9e3c000 r-xp 00000000 08:03 5639506                    /usr/lib/libibus.so.1.0.0
7f8dc9e3c000-7f8dca03c000 ---p 0003f000 08:03 5639506                    /usr/lib/libibus.so.1.0.0
7f8dca03c000-7f8dca03e000 r--p 0003f000 08:03 5639506                    /usr/lib/libibus.so.1.0.0
7f8dca03e000-7f8dca03f000 rw-p 00041000 08:03 5639506                    /usr/lib/libibus.so.1.0.0
7f8dca03f000-7f8dca040000 rw-p 00000000 00:00 0 
7f8dca040000-7f8dca045000 r-xp 00000000 08:03 5643259                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8dca045000-7f8dca245000 ---p 00005000 08:03 5643259                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8dca245000-7f8dca246000 r--p 00005000 08:03 5643259                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8dca246000-7f8dca247000 rw-p 00006000 08:03 5643259                    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
7f8dca247000-7f8dca255000 r-xp 00000000 08:03 5782992                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8dca255000-7f8dca454000 ---p 0000e000 08:03 5782992                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8dca454000-7f8dca455000 r--p 0000d000 08:03 5782992                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8dca455000-7f8dca456000 rw-p 0000e000 08:03 5782992                    /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
7f8dca456000-7f8dca45e000 r-xp 00000000 08:03 5639165                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f8dca45e000-7f8dca65d000 ---p 00008000 08:03 5639165                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f8dca65d000-7f8dca65e000 r--p 00007000 08:03 5639165                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f8dca65e000-7f8dca65f000 rw-p 00008000 08:03 5639165                    /usr/lib/libdbusmenu-gtk.so.1.0.6
7f8dca65f000-7f8dca674000 r-xp 00000000 08:03 5639561                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f8dca674000-7f8dca873000 ---p 00015000 08:03 5639561                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f8dca873000-7f8dca874000 r--p 00014000 08:03 5639561                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f8dca874000-7f8dca875000 rw-p 00015000 08:03 5639561                    /usr/lib/libjson-glib-1.0.so.0.706.0
7f8dca875000-7f8dca87f000 r-xp 00000000 08:03 5639545                    /usr/lib/libindicator.so.0.0.0
7f8dca87f000-7f8dcaa7e000 ---p 0000a000 08:03 5639545                    /usr/lib/libindicator.so.0.0.0
7f8dcaa7e000-7f8dcaa7f000 r--p 00009000 08:03 5639545                    /usr/lib/libindicator.so.0.0.0
7f8dcaa7f000-7f8dcaa80000 rw-p 0000a000 08:03 5639545                    /usr/lib/libindicator.so.0.0.0
7f8dcaa80000-7f8dcaa8e000 r-xp 00000000 08:03 5639163                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f8dcaa8e000-7f8dcac8e000 ---p 0000e000 08:03 5639163                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f8dcac8e000-7f8dcac8f000 r--p 0000e000 08:03 5639163                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f8dcac8f000-7f8dcac90000 rw-p 0000f000 08:03 5639163                    /usr/lib/libdbusmenu-glib.so.1.0.6
7f8dcac90000-7f8dcac98000 r-xp 00000000 08:03 5639019                    /usr/lib/libappindicator.so.0.0.0
7f8dcac98000-7f8dcae97000 ---p 00008000 08:03 5639019                    /usr/lib/libappindicator.so.0.0.0
7f8dcae97000-7f8dcae98000 r--p 00007000 08:03 5639019                    /usr/lib/libappindicator.so.0.0.0
7f8dcae98000-7f8dcae99000 rw-p 00008000 08:03 5639019                    /usr/lib/libappindicator.so.0.0.0
7f8dcae99000-7f8dcaea2000 r-xp 00000000 08:03 5776960                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8dcaea2000-7f8dcb0a2000 ---p 00009000 08:03 5776960                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8dcb0a2000-7f8dcb0a3000 r--p 00009000 08:03 5776960                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8dcb0a3000-7f8dcb0a4000 rw-p 0000a000 08:03 5776960                    /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
7f8dcb0a4000-7f8dcb0ab000 r-xp 00000000 08:03 2490549                    /lib/libusb-0.1.so.4.4.4
7f8dcb0ab000-7f8dcb2aa000 ---p 00007000 08:03 2490549                    /lib/libusb-0.1.so.4.4.4
7f8dcb2aa000-7f8dcb2ab000 r--p 00006000 08:03 2490549                    /lib/libusb-0.1.so.4.4.4
7f8dcb2ab000-7f8dcb2ad000 rw-p 00007000 08:03 2490549                    /lib/libusb-0.1.so.4.4.4
7f8dcb2ad000-7f8dcb2eb000 r-xp 00000000 08:03 5639626                    /usr/lib/libmtp.so.8.3.2
7f8dcb2eb000-7f8dcb4ea000 ---p 0003e000 08:03 5639626                    /usr/lib/liAborted
v@stealth:~$

---

### Post by edhornby on 2010-06-09
worked great for me too - cheers :)

now how do I rep you ?!

---

### Post by rp3 on 2010-06-10
> **edhornby said:**
> worked great for me too - cheers :)

now how do I rep you ?!

Makes it work more, but I still get a Segmentation fault and thats all it says.. 

Bummer, need to load some new music for my trip... :(

---

### Post by Cenci-Thomas on 2010-06-18
Me too. I was getting

```
** (rhythmbox:4293): DEBUG: Loading the real store page
** (rhythmbox:4293): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
Segmentation fault
```

and

```
$ sudo apt-get remove rhythmbox-ubuntuone-music-store
``` 

fixed it.

---

### Post by pwall on 2010-07-27
This fixed it for me also.
Thanks heaps !

---

### Post by neanderslob on 2010-08-01
I don't even have the music store installed and it still crashes.  No idea why, it just hits a segmentation fault as soon as I click on a song.

---

### Post by Paresh on 2010-08-04
I get this problem when I start rhythmbox without an internet connection:-
```

(rhythmbox:8127) Rhythmbox-WARNING **: Could not open device /dev/radio0
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory
** (rhythmbox:8127): DEBUG: Loading the real store page
** (rhythmbox:8127): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
Segmentation fault

```
and then rhythmbox dies

With an internet connection, I get:-
```

(rhythmbox:8246) Rhythmbox-WARNING **: Could not open device /dev/radio0
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory
** (rhythmbox:8246): DEBUG: Loading the real store page
** (rhythmbox:8246): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
** (rhythmbox:8246): DEBUG: navigation requested to file:///usr/share/libubuntuone/1/javascript/load_error.html?https://one.ubuntu.com/music/store-no-token

```
and rhythmbox loads and behaves normally.

---

### Post by Misterbadexample on 2010-08-28
Removing the music store worked for me as well. Thanks!

---

### Post by mistercrunch on 2010-08-30
Unchecking "last.fm" in the (Edit->Plugins) screen fixed the "Segentation Fault" on my side.

---

### Post by drewsus on 2010-09-10
> **mistercrunch said:**
> Unchecking "last.fm" in the (Edit->Plugins) screen fixed the "Segentation Fault" on my side.

How might one open Rhythmbox to uncheck last.fm if it closes with a seg fault before opening?

***sudo apt-get remove rhythmbox-ubuntuone-music-store*** fixed it for me as well.

I was then able to disable last.fm and I suppose reinstalling rhythmbox-ubuntuone-music-store would now be kosher, but I will never use it so there is no need.

---

### Post by enfant_terible_1 on 2010-09-15
i get always the same seg fault when i try to use one of the plugins... like magnatune or jamendo. I think that the problem is in the plugins side. Does anyone found a solution?

Update: It affects 32 and 64 bit versions 
        It has started crashes from last updates.

---

### Post by theselby on 2010-10-22
Same here. No matter which audio app i launch, it crashes.

Rhytmox crashes, Audacious crashes, all video players when playing audio crash, etc.

Weird :)

---

### Post by ethanay on 2010-12-07
I was getting crashes after adding several new files to Rhythmbox.  Unchecking "watch for new files" in preferences stopped the crash.  So I went into the .local/share/rhythmbox folder and deleted the old database file, and let Rhythmbox rebuild a new one.

After that, no more crashes after startup.

---

