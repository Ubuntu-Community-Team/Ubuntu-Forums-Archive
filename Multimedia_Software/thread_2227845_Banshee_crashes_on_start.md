---
title: "Banshee crashes on start"
date: 2014-06-04
forum: Multimedia Software
---

### Post by cybergalvez on 2014-06-04
Hi all,

I'm having issues with Banshee crashing just after startup. this is the terminal output. any help is appreciated

```

[Info  08:15:57.516] Running Banshee 2.6.2: [Ubuntu Trusty Tahr (development branch) (linux-gnu, x86_64) @ 2014-03-25 10:44:19 UTC]

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkComponent) to class (__gtksharp_49_Hyena_Gui_BaseWidgetAccessible) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_50_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_50_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_56_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_56_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_62_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_62_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_68_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_68_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_74_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:24873): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_74_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init
[Info  08:15:58.515] Updating web proxy from GConf
[Info  08:15:58.564] All services are started 0.846753

(Banshee:24873): GLib-CRITICAL **: Source ID 113 was not found when attempting to remove it

(Banshee:24873): GLib-CRITICAL **: Source ID 144 was not found when attempting to remove it
[Info  08:15:59.112] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/

(Banshee:24873): GLib-CRITICAL **: Source ID 230 was not found when attempting to remove it

(Banshee:24873): GLib-CRITICAL **: Source ID 229 was not found when attempting to remove it
[Info  08:15:59.674] nereid Client Started
[Info  08:15:59.717] GStreamer version 1.2.3.0, gapless: True, replaygain: False

(Banshee:24873): GLib-CRITICAL **: Source ID 718 was not found when attempting to remove it

(Banshee:24873): GLib-CRITICAL **: Source ID 722 was not found when attempting to remove it

(Banshee:24873): GLib-CRITICAL **: Source ID 551 was not found when attempting to remove it

(Banshee:24873): GLib-CRITICAL **: Source ID 474 was not found when attempting to remove it

(Banshee:24873): GLib-CRITICAL **: Source ID 721 was not found when attempting to remove it
banshee: BPMDetect.cpp:134: soundtouch::BPMDetect::BPMDetect(int, int): Assertion `2048 < decimateBy * 256' failed.

Native stacktrace:

	banshee() [0x4b73d8]
	/lib/x86_64-linux-gnu/libpthread.so.0(+0x10340) [0x7fc65d526340]
	/lib/x86_64-linux-gnu/libc.so.6(gsignal+0x39) [0x7fc65d186f79]
	/lib/x86_64-linux-gnu/libc.so.6(abort+0x148) [0x7fc65d18a388]
	/lib/x86_64-linux-gnu/libc.so.6(+0x2fe36) [0x7fc65d17fe36]
	/lib/x86_64-linux-gnu/libc.so.6(+0x2fee2) [0x7fc65d17fee2]
	/usr/lib/x86_64-linux-gnu/libSoundTouch.so.0(_ZN10soundtouch9BPMDetectC2Eii+0x181) [0x7fc619da1781]
	/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstsoundtouch.so(+0x4ef1) [0x7fc619fabef1]
	/usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(+0x33960) [0x7fc64c8a3960]
	/usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(+0x340a1) [0x7fc64c8a40a1]
	/usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x60d08) [0x7fc64c5ccd08]
	/usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(+0x342a9) [0x7fc64c8a42a9]
	/usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x60d08) [0x7fc64c5ccd08]
	/usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(gst_proxy_pad_chain_default+0xbb) [0x7fc64c5bee2b]
	/usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x60d08) [0x7fc64c5ccd08]
	/usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x191fc) [0x7fc64d38f1fc]
	/usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x194b6) [0x7fc64d38f4b6]
	/usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(gst_audio_decoder_finish_frame+0x52c) [0x7fc64d393aac]
	/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstflump3dec.so(+0x2142) [0x7fc61852a142]
	/usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x1ac73) [0x7fc64d390c73]
	/usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x1b04b) [0x7fc64d39104b]
	/usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x1c036) [0x7fc64d392036]
	/usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x60d08) [0x7fc64c5ccd08]
	/usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(gst_base_parse_push_frame+0x9f9) [0x7fc64c886b09]
	/usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(gst_base_parse_finish_frame+0x633) [0x7fc64c88a1c3]
	/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstaudioparsers.so(+0x119a4) [0x7fc618f6f9a4]
	/usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(+0x141e4) [0x7fc64c8841e4]
	/usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(+0x14752) [0x7fc64c884752]
	/usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(+0x18609) [0x7fc64c888609]
	/usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x8e549) [0x7fc64c5fa549]
	/lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x6e89c) [0x7fc65a06689c]
	/lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x6df15) [0x7fc65a065f15]
	/lib/x86_64-linux-gnu/libpthread.so.0(+0x8182) [0x7fc65d51e182]
	/lib/x86_64-linux-gnu/libc.so.6(clone+0x6d) [0x7fc65d24b30d]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
No threads.

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted


```

---

### Post by mc4man on 2014-06-04
Maybe see here - 
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/1310854](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/1310854)
(- try running the suggested command, reading log & if a file(s) is mentioned removing from where banshee can find.
Myself, on Ubuntu, have no issue with the file, (.mp3) attached to bug report unless I manually try to detect bpm on that file

If you can manage to disable the bpm extension that could also help

---

### Post by tgalati4 on 2014-06-04
Try removing the BPM plug-in.  It is buggy and appears to be causing your crash.

---

### Post by cybergalvez on 2014-06-04
That worked, I turned off the auto detect bpm, and I unslected the detect BPM extension. What will leaving that off do?

---

