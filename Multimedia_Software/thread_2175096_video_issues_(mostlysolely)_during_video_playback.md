---
title: "video issues (mostly/solely?) during video playback"
date: 2013-09-17
forum: Multimedia Software
---

### Post by Martin_Mucha on 2013-09-17
Hi, 
I've got some video issues during video playback. It looks like some codec issue, since when there is some bigger movement in movie, image tears, and horizontal edge(s) appears for few ms.
I've already tried to solve this issues on czech forum, but we did not came to solution. 
This initial post's going to be a little bit longer, and I'm sorry for that, but I want to provide ALL things we've checked, ALL things we've installed, and ALL logs we've examined.
[COLOR=#000000][FONT=Verdana]Thanks in advance for any help.[/FONT][/COLOR]
----------------
PC configuration:
cpu:i7 3770K, 
graphics: integrated HD4000
hdd: intel SSD.
----------------
OS: xubuntu 12.04, amd64. Also tested in KDE, booted from "live USB", after updates, *-restricted-extras etc installed. Same problem.
----------------
Installed sw:
purge all configuration of all players.

[COLOR=#000000][FONT=Verdana]sudo apt-get install xubuntu-restricted-extras xubuntu-restricted-addons non-free-codecs[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]sudo apt-get install libva-intel-vaapi-driver vainfo gstreamer0.10-vaapi xbmc [/FONT][/COLOR]libva1 i965-va-driver  vainfo[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]sudo apt-get install linux-headers-$(uname -r)
[/FONT][/COLOR]-------------------
logs:

[COLOR=#000000][FONT=Verdana]dmesg | grep -iE "drm|vesa|intel"
[/FONT][/COLOR]```
[COLOR=#000000][FONT=dejavu sans mono][    0.000000]   Intel GenuineIntel[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    0.000000] ACPI: DMAR 00000000bd8d4430 000B8 (v01 INTEL      SNB  00000001 INTL 00000001)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    0.172522] smpboot: CPU0: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz (fam: 06, model: 3a, stepping: 09)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    0.172529] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, Intel PMU driver.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    0.575618] intel_idle: MWAIT substates: 0x1120[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    0.575619] intel_idle: v0.4 model 0x3A[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    0.575620] intel_idle: lapic_timer_reliable_states 0xffffffff[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    0.966035] ata2.00: ATA-9: INTEL SSDSC2BW180A3, 400i, max UDMA/133[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    0.976217] scsi 1:0:0:0: Direct-Access     ATA      INTEL SSDSC2BW18 400i PQ: 0 ANSI: 5[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    1.295448] [drm] Initialized drm 1.1.0 20060810[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    1.307592] [drm] Memory usable by graphics device = 2048M[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    1.307600] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    1.343201] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    1.343202] [drm] Driver supports precise vblank timestamp query.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    1.847510] fbcon: inteldrmfb (fb0) is primary device[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.079953] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.081666] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.081693] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.081758] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104255] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card1/input6[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104322] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card1/input7[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104365] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104394] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104424] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104457] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104483] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104510] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104537] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.104564] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][    2.735480] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off[/FONT][/COLOR]

```[COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]cat /var/log/Xorg.0.log | grep -E "err|warn|WW|EE"
[/FONT][/COLOR]```
[COLOR=#000000][FONT=dejavu sans mono](WW) warning, (EE) error, (NI) not implemented, (??) unknown.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.051] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.051] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.051] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.051] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.051] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.051] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.053] (II) Loading extension MIT-SCREEN-SAVER[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.060] (WW) Falling back to old probe method for vesa[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.060] (WW) Falling back to old probe method for fbdev[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     3.876] (II) intel(0): First detailed timing is preferred mode[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][     4.091] (WW) evdev: A4Tech USB Full Speed: ignoring absolute axes.[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR]glxinfo |grep -E ^[A-Z][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]```

[COLOR=#000000][FONT=dejavu sans mono]GLX version: 1.4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]GLX extensions:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]OpenGL vendor string: Tungsten Graphics, Inc[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Desktop [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]OpenGL version string: 3.0 Mesa 8.0.4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]OpenGL shading language version string: 1.30[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]OpenGL extensions:[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR]cat ~/.xsession-errors[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]```

[COLOR=#000000][FONT=dejavu sans mono]openConnection: connect: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]cannot connect to brltty at :0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-boXiPB/pkcs11: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xfce4-settings-helper: Another instance is already running. Leaving...[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-boXiPB/pkcs11: No such file or directory[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](polkit-gnome-authentication-agent-1:2524): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](polkit-gnome-authentication-agent-1:2524): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X Error of failed request:  BadWindow (invalid Window parameter)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]  Major opcode of failed request:  20 (X_GetProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]  Resource id in failed request:  0x2400001[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]  Serial number of failed request:  76[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]  Current serial number in output stream:  76[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](xfce4-indicator-plugin:2566): libindicator-WARNING **: IndicatorObject class does not have an accessible description.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](xfce4-indicator-plugin:2566): libindicator-WARNING **: IndicatorObject class does not have an accessible description.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]** Message: applet now removed from the notification area[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]** Message: applet now embedded in the notification area[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]** Message: applet now removed from the notification area[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](xfce4-indicator-plugin:2566): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-boXiPB/pkcs11: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Conky: desktop window (1600003) is subwindow of root window (b4)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Conky: window type - normal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Conky: drawing to created window (0x3e00001)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Conky: drawing to single buffer[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]ATTENTION: default value of option force_s3tc_enable overridden by environment.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][267:273:0910/193436:ERROR:platform_thread_linux.cc(99)] Failed to set nice value of thread to -10[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/180128:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/180328:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/180528:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/180728:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/180928:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/181128:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/181328:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/181528:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/181728:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/181928:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/182128:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/182328:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/182528:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][3093:3093:0910/182728:ERROR:vsync_provider.cc(70)] glXGetSyncValuesOML should not return TRUE with a media stream counter of 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][2783:2822:0910/202903:ERROR:download_updates_command.cc(187)] PostClientToServerMessage() failed during GetUpdates[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](gcalctool:7353): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You can apply tags and insert marks without invalidating your iterators,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]will invalidate all outstanding iterators[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](gcalctool:7353): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You can apply tags and insert marks without invalidating your iterators,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]will invalidate all outstanding iterators[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](gcalctool:7353): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You can apply tags and insert marks without invalidating your iterators,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]will invalidate all outstanding iterators[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](gcalctool:7353): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You can apply tags and insert marks without invalidating your iterators,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]will invalidate all outstanding iterators[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](gcalctool:7353): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You can apply tags and insert marks without invalidating your iterators,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]will invalidate all outstanding iterators[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](gcalctool:7353): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]You can apply tags and insert marks without invalidating your iterators,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]will invalidate all outstanding iterators[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][1275:1282:0910/221956:ERROR:platform_thread_linux.cc(99)] Failed to set nice value of thread to -10[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono](xfce4-terminal:2572): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR]uname -r
```
[COLOR=#000000][FONT=dejavu sans mono]3.10.11-031011-generic[/FONT][/COLOR]
```

mplayer playing some video
```

[COLOR=#000000][FONT=dejavu sans mono]martin@MM-PC:~/Downloads$ mplayer Louis-C-K-Hilarious-2010-HDTV-XviD-FQM.avi [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]mplayer: could not connect to socket[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]mplayer: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Failed to open LIRC support. You will not be able to use your remote control.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Playing Louis-C-K-Hilarious-2010-HDTV-XviD-FQM.avi.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libavformat version 53.21.1 (external)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Mismatching header version 53.19.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]AVI file format detected.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][aviheader] Video stream found, -vid 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][aviheader] Audio stream found, -aid 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1015.4 kbps (123.9 kbyte/s)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Clip info:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] Software: transcode-1.0.4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Load subtitles in ./[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][vdpau] Error when calling vdp_device_create_x11: 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]==========================================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libavcodec version 53.35.0 (external)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Mismatching header version 53.32.2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Unsupported PixelFormat 61[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Unsupported PixelFormat 53[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Unsupported PixelFormat 81[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]==========================================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]==========================================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Requested audio codec family [mpg123] (afm=mpg123) not available.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Enable it at compilation.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]AUDIO: 48000 Hz, 2 ch, floatle, 128.0 kbit/4.17% (ratio: 16000->384000)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]==========================================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Starting playback...[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]VO: [xv] 624x352 => 624x352 Planar YV12 [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]A:  56.7 V:  56.7 A-V: -0.006 ct: -0.048 1361/1361  2%  0%  0.3% 0 0 [/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Exiting... (Quit)[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Verdana]Xorg.0.log
[/FONT][/COLOR]```
[COLOR=#000000][FONT=dejavu sans mono][ 2.963][/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X.Org X Server 1.11.3[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Release Date: 2011-12-16[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] X Protocol Version 11, Revision 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] Current Operating System: Linux MM-PC 3.8.0-25-generic #37~precise1-Ubuntu SMP Fri Jun 7 16:27:35 UTC 2013 x86_64[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=075b0efb-01cb-4cf9-a3d3-7c59b5dbc247 ro quiet splash vt.handoff=7[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] Build Date: 11 April 2013 01:05:39PM[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] Current version of pixman: 0.24.4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] Before reporting problems, check http://wiki.x.org[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]to make sure that you have the latest version.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] Markers: (--) probed, (**) from config file, (==) default setting,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono](++) from command line, (!!) notice, (II) informational,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono](WW) warning, (EE) error, (NI) not implemented, (??) unknown.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.963] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 11 19:50:28 2013[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.967] (==) Using system config directory "/usr/share/X11/xorg.conf.d"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.969] (==) No Layout section. Using the first Screen section.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.969] (==) No screen section available. Using defaults.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.969] (**) |-->Screen "Default Screen Section" (0)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.969] (**) | |-->Monitor "<default monitor>"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.970] (==) No monitor specified for screen "Default Screen Section".[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Using a default monitor configuration.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.970] (==) Automatically adding devices[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.970] (==) Automatically enabling devices[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] Entry deleted from font path.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] Entry deleted from font path.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] Entry deleted from font path.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] Entry deleted from font path.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] Entry deleted from font path.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] Entry deleted from font path.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (==) FontPath set to:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]/usr/share/fonts/X11/misc,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]/usr/share/fonts/X11/Type1,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]built-ins[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (II) The server relies on udev to provide the list of input devices.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]If no devices become available, reconfigure udev or disable AutoAddDevices.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (II) Loader magic: 0x7f8efad19b00[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (II) Module ABI versions:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] X.Org ANSI C Emulation: 0.4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] X.Org Video Driver: 11.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] X.Org XInput driver : 16.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] X.Org Server Extension : 6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (--) PCI:*(0:0:2:0) 8086:0162:1458:d000 rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (II) Open ACPI successful (/var/run/acpid.socket)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.972] (II) LoadModule: "extmod"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Module extmod: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] compiled for 1.11.3, module version = 1.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] Module class: X.Org Server Extension[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] ABI class: X.Org Server Extension, version 6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Loading extension MIT-SCREEN-SAVER[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Loading extension XFree86-VidModeExtension[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Loading extension XFree86-DGA[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Loading extension DPMS[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Loading extension XVideo[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Loading extension XVideo-MotionCompensation[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Loading extension X-Resource[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) LoadModule: "dbe"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.974] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.975] (II) Module dbe: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.975] compiled for 1.11.3, module version = 1.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.975] Module class: X.Org Server Extension[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.975] ABI class: X.Org Server Extension, version 6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.975] (II) Loading extension DOUBLE-BUFFER[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.975] (II) LoadModule: "glx"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.975] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.976] (II) Module glx: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.976] compiled for 1.11.3, module version = 1.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.976] ABI class: X.Org Server Extension, version 6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.976] (==) AIGLX enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] (II) Loading extension GLX[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] (II) LoadModule: "record"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] (II) Module record: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] compiled for 1.11.3, module version = 1.13.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] Module class: X.Org Server Extension[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] ABI class: X.Org Server Extension, version 6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] (II) Loading extension RECORD[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] (II) LoadModule: "dri"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.977] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (II) Module dri: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] compiled for 1.11.3, module version = 1.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] ABI class: X.Org Server Extension, version 6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (II) Loading extension XFree86-DRI[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (II) LoadModule: "dri2"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (II) Module dri2: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] compiled for 1.11.3, module version = 1.2.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] ABI class: X.Org Server Extension, version 6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (II) Loading extension DRI2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (==) Matched intel as autoconfigured driver 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (==) Matched vesa as autoconfigured driver 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (==) Matched fbdev as autoconfigured driver 2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (==) Assigned the driver to the xf86ConfigLayout[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (II) LoadModule: "intel"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.978] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] (II) Module intel: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] compiled for 1.11.3, module version = 2.17.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] Module class: X.Org Video Driver[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] ABI class: X.Org Video Driver, version 11.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] (II) LoadModule: "vesa"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] (II) Module vesa: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] compiled for 1.11.3, module version = 2.3.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] Module class: X.Org Video Driver[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] ABI class: X.Org Video Driver, version 11.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] (II) LoadModule: "fbdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.980] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.981] (II) Module fbdev: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.981] compiled for 1.11.3, module version = 0.4.2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.981] ABI class: X.Org Video Driver, version 11.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.981] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Ivybridge Server (GT2)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.981] (II) VESA: driver for VESA chipsets: vesa[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.981] (II) FBDEV: driver for framebuffer: fbdev[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.981] (++) using VT number 7[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (WW) Falling back to old probe method for vesa[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (WW) Falling back to old probe method for fbdev[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (II) Loading sub module "fbdevhw"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (II) LoadModule: "fbdevhw"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (II) Module fbdevhw: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] compiled for 1.11.3, module version = 0.0.2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] ABI class: X.Org Video Driver, version 11.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] drmOpenDevice: node name is /dev/dri/card0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] drmOpenDevice: open result is 9, (OK)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] drmOpenByBusid: Searching for BusID pci:0000:00:02.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] drmOpenDevice: node name is /dev/dri/card0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] drmOpenDevice: open result is 9, (OK)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] drmOpenByBusid: drmOpenMinor returns 9[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (II) intel(0): Creating default Display subsection in Screen section[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]"Default Screen Section" for depth/fbbpp 24/32[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (==) intel(0): Depth 24, (--) framebuffer bpp 32[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (==) intel(0): RGB weight 888[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (==) intel(0): Default visual is TrueColor[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (II) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Desktop (GT2)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (--) intel(0): Chipset: "Ivybridge Desktop (GT2)"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (**) intel(0): Relaxed fencing enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (**) intel(0): Wait on SwapBuffers? enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (**) intel(0): Triple buffering? enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (**) intel(0): Framebuffer tiled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (**) intel(0): Pixmaps tiled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (**) intel(0): 3D buffers tiled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (**) intel(0): SwapBuffers wait enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.982] (==) intel(0): video overlay key set to 0x101fe[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 2.996] (II) intel(0): Output VGA1 has no monitor section[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.300] (II) intel(0): Output HDMI1 has no monitor section[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.348] (II) intel(0): Output DP1 has no monitor section[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.364] (II) intel(0): Output HDMI2 has no monitor section[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.380] (II) intel(0): Output HDMI3 has no monitor section[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.428] (II) intel(0): Output DP2 has no monitor section[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.476] (II) intel(0): Output DP3 has no monitor section[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.492] (II) intel(0): EDID for output VGA1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): EDID for output HDMI1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Manufacturer: DEL Model: a07a Serial#: 842026579[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Year: 2013 Week: 3[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): EDID Version: 1.3[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Digital Display Input[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Max Image Size [cm]: horiz.: 52 vert.: 32[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Gamma: 2.20[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): DPMS capabilities: StandBy Suspend Off[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): First detailed timing is preferred mode[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): redX: 0.640 redY: 0.330 greenX: 0.300 greenY: 0.600[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): blueX: 0.150 blueY: 0.060 whiteX: 0.313 whiteY: 0.329[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Supported established timings:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 720x400@70Hz[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 640x480@60Hz[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 800x600@60Hz[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 1024x768@60Hz[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Manufacturer's mask: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Supported standard timings:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): #0: hsize: 1280 vsize 960 refresh: 60 vid: 16513[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): #1: hsize: 1280 vsize 1024 refresh: 60 vid: 32897[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): #2: hsize: 1600 vsize 1200 refresh: 60 vid: 16553[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): #3: hsize: 1680 vsize 1050 refresh: 60 vid: 179[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): #4: hsize: 1920 vsize 1080 refresh: 60 vid: 49361[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Supported detailed timing:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): clock: 154.0 MHz Image Size: 518 x 324 mm[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): h_active: 1920 h_sync: 1968 h_sync_end 2000 h_blank_end 2080 h_border: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): v_active: 1200 v_sync: 1203 v_sync_end 1209 v_blanking: 1235 v_border: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Serial No: 0FFXD31I20NS[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Monitor name: DELL U2412M[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Ranges: V min: 50 V max: 61 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): EDID (in hex):[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 00ffffffffffff0010ac7aa0534e3032[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 0317010380342078eaee95a3544c9926[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 0f5054a1080081408180a940b300d1c0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 010101010101283c80a070b023403020[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 360006442100001a000000ff00304646[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 584433314932304e530a000000fc0044[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 454c4c2055323431324d0a20000000fd[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): 00323d1e5311000a2020202020200056[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Printing probed modes for output HDMI1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Modeline "1920x1200"x60.0 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync (74.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Modeline "1600x1200"x60.0 162.00 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync (75.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Modeline "1680x1050"x59.9 119.00 1680 1728 1760 1840 1050 1053 1059 1080 +hsync -vsync (64.7 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Modeline "1280x1024"x60.0 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync (64.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Modeline "1280x960"x60.0 108.00 1280 1376 1488 1800 960 961 964 1000 +hsync +vsync (60.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Modeline "1024x768"x60.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Modeline "800x600"x60.3 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Modeline "640x480"x60.0 25.20 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.796] (II) intel(0): Modeline "720x400"x70.1 28.32 720 738 846 900 400 412 414 449 -hsync +vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.844] (II) intel(0): EDID for output DP1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.860] (II) intel(0): EDID for output HDMI2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.876] (II) intel(0): EDID for output HDMI3[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.924] (II) intel(0): EDID for output DP2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): EDID for output DP3[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Output VGA1 disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Output HDMI1 connected[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Output DP1 disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Output HDMI2 disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Output HDMI3 disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Output DP2 disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Output DP3 disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Using exact sizes for initial modes[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Output HDMI1 using initial mode 1920x1200[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) intel(0): Kernel page flipping support detected, enabling[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (==) intel(0): DPI set to (96, 96)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) Loading sub module "fb"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) LoadModule: "fb"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.972] (II) Loading /usr/lib/xorg/modules/libfb.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) Module fb: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] compiled for 1.11.3, module version = 1.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] ABI class: X.Org ANSI C Emulation, version 0.4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) Loading sub module "dri2"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) LoadModule: "dri2"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) Module dri2: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] compiled for 1.11.3, module version = 1.2.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] ABI class: X.Org Server Extension, version 6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) UnloadModule: "vesa"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) Unloading vesa[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) UnloadModule: "fbdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) Unloading fbdev[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) UnloadModule: "fbdevhw"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) Unloading fbdevhw[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (==) Depth 24 pixmap format is 32 bpp[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) intel(0): [DRI2] Setup complete[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) intel(0): [DRI2] DRI driver: i965[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.973] (II) intel(0): Allocated new frame buffer 1920x1200 stride 7680, tiled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.975] (II) UXA(0): Driver registered support for the following operations:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.975] (II) solid[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.975] (II) copy[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.975] (II) composite (RENDER acceleration)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.975] (II) put_image[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.975] (II) get_image[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.975] (==) intel(0): Backing store disabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.975] (==) intel(0): Silken mouse enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.975] (II) intel(0): Initializing HW Cursor[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (==) intel(0): DPMS enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (==) intel(0): Intel XvMC decoder enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) intel(0): Set up textured video[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) intel(0): [XvMC] xvmc_vld driver initialized.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) intel(0): direct rendering: DRI2 Enabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (==) intel(0): hotplug detection: "enabled"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (--) RandR disabled[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension Generic Event Extension[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension SHAPE[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension MIT-SHM[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension XInputExtension[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension XTEST[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension BIG-REQUESTS[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension SYNC[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension XKEYBOARD[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension XC-MISC[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension SECURITY[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension XINERAMA[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension XFIXES[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension RENDER[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension RANDR[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension COMPOSITE[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 3.996] (II) Initializing built-in extension DAMAGE[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.007] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.007] (II) AIGLX: enabled GLX_INTEL_swap_event[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.007] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.007] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.007] (II) AIGLX: Loaded and initialized i965[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.007] (II) GLX: Initialized DRI2 GL provider for screen 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.008] (II) intel(0): Setting screen physical size to 508 x 317[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.014] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.016] (II) config/udev: Adding input device Power Button (/dev/input/event1)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.016] (**) Power Button: Applying InputClass "evdev keyboard catchall"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.016] (II) LoadModule: "evdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.016] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) Module evdev: vendor="X.Org Foundation"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] compiled for 1.11.3, module version = 2.7.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] Module class: X.Org XInput Driver[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] ABI class: X.Org XInput driver, version 16.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) Using input driver 'evdev' for 'Power Button'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Power Button: always reports core events[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) evdev: Power Button: Device: "/dev/input/event1"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (--) evdev: Power Button: Vendor 0 Product 0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (--) evdev: Power Button: Found keys[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) evdev: Power Button: Configuring as keyboard[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Option "xkb_rules" "evdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Option "xkb_model" "pc105"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Option "xkb_layout" "us"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) config/udev: Adding input device Video Bus (/dev/input/event5)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Video Bus: Applying InputClass "evdev keyboard catchall"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) Using input driver 'evdev' for 'Video Bus'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Video Bus: always reports core events[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) evdev: Video Bus: Device: "/dev/input/event5"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (--) evdev: Video Bus: Vendor 0 Product 0x6[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (--) evdev: Video Bus: Found keys[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) evdev: Video Bus: Configuring as keyboard[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Option "xkb_rules" "evdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Option "xkb_model" "pc105"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.017] (**) Option "xkb_layout" "us"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) config/udev: Adding input device Power Button (/dev/input/event0)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (**) Power Button: Applying InputClass "evdev keyboard catchall"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) Using input driver 'evdev' for 'Power Button'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (**) Power Button: always reports core events[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (**) evdev: Power Button: Device: "/dev/input/event0"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (--) evdev: Power Button: Vendor 0 Product 0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (--) evdev: Power Button: Found keys[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) evdev: Power Button: Configuring as keyboard[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (**) Option "xkb_rules" "evdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (**) Option "xkb_model" "pc105"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (**) Option "xkb_layout" "us"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event10)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event12)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.018] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event13)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event14)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event15)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event6)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event7)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.019] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) config/udev: Adding input device A4Tech USB Full Speed (/dev/input/event3)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) A4Tech USB Full Speed: Applying InputClass "evdev pointer catchall"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) Using input driver 'evdev' for 'A4Tech USB Full Speed'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) A4Tech USB Full Speed: always reports core events[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) evdev: A4Tech USB Full Speed: Device: "/dev/input/event3"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Vendor 0x9da Product 0x8090[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found 20 mouse buttons[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found scroll wheel(s)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found relative axes[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found x and y relative axes[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) evdev: A4Tech USB Full Speed: Configuring as mouse[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) evdev: A4Tech USB Full Speed: Adding scrollwheel support[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) evdev: A4Tech USB Full Speed: YAxisMapping: buttons 4 and 5[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) evdev: A4Tech USB Full Speed: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/usb5/5-1/5-1.1/5-1.1:1.0/input/input3/event3"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) XINPUT: Adding extended input device "A4Tech USB Full Speed" (type: MOUSE, id 9)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) evdev: A4Tech USB Full Speed: initialized for relative axes.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) A4Tech USB Full Speed: (accel) keeping acceleration scheme 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) A4Tech USB Full Speed: (accel) acceleration profile 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) A4Tech USB Full Speed: (accel) acceleration factor: 2.000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) A4Tech USB Full Speed: (accel) acceleration threshold: 4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) config/udev: Adding input device A4Tech USB Full Speed (/dev/input/mouse0)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) config/udev: Adding input device A4Tech USB Full Speed (/dev/input/event4)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) A4Tech USB Full Speed: Applying InputClass "evdev keyboard catchall"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) Using input driver 'evdev' for 'A4Tech USB Full Speed'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) A4Tech USB Full Speed: always reports core events[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) evdev: A4Tech USB Full Speed: Device: "/dev/input/event4"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Vendor 0x9da Product 0x8090[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found 1 mouse buttons[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found scroll wheel(s)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found relative axes[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found absolute axes[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found absolute multitouch axes[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found x and y absolute axes[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (--) evdev: A4Tech USB Full Speed: Found keys[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) evdev: A4Tech USB Full Speed: Configuring as mouse[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) evdev: A4Tech USB Full Speed: Configuring as keyboard[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) evdev: A4Tech USB Full Speed: Adding scrollwheel support[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) evdev: A4Tech USB Full Speed: YAxisMapping: buttons 4 and 5[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) evdev: A4Tech USB Full Speed: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/usb5/5-1/5-1.1/5-1.1:1.1/input/input4/event4"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (II) XINPUT: Adding extended input device "A4Tech USB Full Speed" (type: KEYBOARD, id 10)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) Option "xkb_rules" "evdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) Option "xkb_model" "pc105"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.020] (**) Option "xkb_layout" "us"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (II) evdev: A4Tech USB Full Speed: initialized for relative axes.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (WW) evdev: A4Tech USB Full Speed: ignoring absolute axes.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) A4Tech USB Full Speed: (accel) keeping acceleration scheme 1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) A4Tech USB Full Speed: (accel) acceleration profile 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) A4Tech USB Full Speed: (accel) acceleration factor: 2.000[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) A4Tech USB Full Speed: (accel) acceleration threshold: 4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (II) config/udev: Adding input device A4Tech USB Full Speed (/dev/input/js0)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (II) No input driver specified, ignoring this device.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (II) This device may have been added with another device file.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) AT Translated Set 2 keyboard: always reports core events[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (--) evdev: AT Translated Set 2 keyboard: Found keys[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) Option "xkb_rules" "evdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) Option "xkb_model" "pc105"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.021] (**) Option "xkb_layout" "us"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 4.098] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.117] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): EDID vendor "DEL", prod id 41082[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Using EDID range info for horizontal sync[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Using EDID range info for vertical refresh[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Printing DDC gathered Modelines:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "1920x1200"x0.0 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync (74.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "800x600"x0.0 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "640x480"x0.0 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "720x400"x0.0 28.32 720 738 846 900 400 412 414 449 -hsync +vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "1024x768"x0.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "1280x960"x0.0 108.00 1280 1376 1488 1800 960 961 964 1000 +hsync +vsync (60.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "1280x1024"x0.0 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync (64.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "1600x1200"x0.0 162.00 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync (75.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "1680x1050"x0.0 119.00 1680 1728 1760 1840 1050 1053 1059 1080 +hsync -vsync (64.7 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 195.536] (II) intel(0): Modeline "1920x1080"x60.0 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -hsync +vsync (67.1 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): EDID vendor "DEL", prod id 41082[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Using hsync ranges from config file[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Using vrefresh ranges from config file[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Printing DDC gathered Modelines:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "1920x1200"x0.0 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync (74.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "800x600"x0.0 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "640x480"x0.0 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "720x400"x0.0 28.32 720 738 846 900 400 412 414 449 -hsync +vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "1024x768"x0.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "1280x960"x0.0 108.00 1280 1376 1488 1800 960 961 964 1000 +hsync +vsync (60.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "1280x1024"x0.0 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync (64.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "1600x1200"x0.0 162.00 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync (75.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "1680x1050"x0.0 119.00 1680 1728 1760 1840 1050 1053 1059 1080 +hsync -vsync (64.7 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.032] (II) intel(0): Modeline "1920x1080"x60.0 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -hsync +vsync (67.1 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): EDID vendor "DEL", prod id 41082[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Using hsync ranges from config file[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Using vrefresh ranges from config file[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Printing DDC gathered Modelines:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "1920x1200"x0.0 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync (74.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "800x600"x0.0 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "640x480"x0.0 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "720x400"x0.0 28.32 720 738 846 900 400 412 414 449 -hsync +vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "1024x768"x0.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "1280x960"x0.0 108.00 1280 1376 1488 1800 960 961 964 1000 +hsync +vsync (60.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "1280x1024"x0.0 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync (64.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "1600x1200"x0.0 162.00 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync (75.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "1680x1050"x0.0 119.00 1680 1728 1760 1840 1050 1053 1059 1080 +hsync -vsync (64.7 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 196.700] (II) intel(0): Modeline "1920x1080"x60.0 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -hsync +vsync (67.1 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): EDID vendor "DEL", prod id 41082[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Using hsync ranges from config file[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Using vrefresh ranges from config file[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Printing DDC gathered Modelines:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "1920x1200"x0.0 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync (74.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "800x600"x0.0 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "640x480"x0.0 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "720x400"x0.0 28.32 720 738 846 900 400 412 414 449 -hsync +vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "1024x768"x0.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "1280x960"x0.0 108.00 1280 1376 1488 1800 960 961 964 1000 +hsync +vsync (60.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "1280x1024"x0.0 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync (64.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "1600x1200"x0.0 162.00 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync (75.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "1680x1050"x0.0 119.00 1680 1728 1760 1840 1050 1053 1059 1080 +hsync -vsync (64.7 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.208] (II) intel(0): Modeline "1920x1080"x60.0 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -hsync +vsync (67.1 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): EDID vendor "DEL", prod id 41082[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Using hsync ranges from config file[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Using vrefresh ranges from config file[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Printing DDC gathered Modelines:[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "1920x1200"x0.0 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync (74.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "800x600"x0.0 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "640x480"x0.0 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "720x400"x0.0 28.32 720 738 846 900 400 412 414 449 -hsync +vsync (31.5 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "1024x768"x0.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "1280x960"x0.0 108.00 1280 1376 1488 1800 960 961 964 1000 +hsync +vsync (60.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "1280x1024"x0.0 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync (64.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "1600x1200"x0.0 162.00 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync (75.0 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "1680x1050"x0.0 119.00 1680 1728 1760 1840 1050 1053 1059 1080 +hsync -vsync (64.7 kHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][ 197.712] (II) intel(0): Modeline "1920x1080"x60.0 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -hsync +vsync (67.1 kHz)[/FONT][/COLOR]

```[COLOR=#000000][FONT=Verdana]

glmark
[/FONT][/COLOR]```
[COLOR=#000000][FONT=dejavu sans mono]glmark2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]=======================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    glmark2 2011.09[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]=======================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    OpenGL Information[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    GL_VENDOR:     Tungsten Graphics, Inc[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    GL_RENDERER:   Mesa DRI Intel(R) Ivybridge Desktop [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    GL_VERSION:    3.0 Mesa 8.0.4[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]=======================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][build] use-vbo=false:  FPS: 1617[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][build] use-vbo=true:  FPS: 1972[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][texture] texture-filter=nearest:  FPS: 2255[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][texture] texture-filter=linear:  FPS: 2212[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][texture] texture-filter=mipmap:  FPS: 2378[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][shading] shading=gouraud:  FPS: 1510[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][shading] shading=blinn-phong-inf:  FPS: 1523[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][shading] shading=phong:  FPS: 1483[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][bump] bump-render=high-poly:  FPS: 764[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][bump] bump-render=normals:  FPS: 2229[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][effect2d] kernel=0,1,0;1,-4,1;0,1,0;:  FPS: 1099[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;:  FPS: 489[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][pulsar] light=false:quads=5:texture=false:  FPS: 1790[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4:  FPS: 474[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][conditionals] fragment-steps=0:vertex-steps=0:  FPS: 1807[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][conditionals] fragment-steps=5:vertex-steps=0:  FPS: 1820[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][conditionals] fragment-steps=0:vertex-steps=5:  FPS: 1820[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][function] fragment-complexity=low:fragment-steps=5:  FPS: 1819[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][function] fragment-complexity=medium:fragment-steps=5:  FPS: 1815[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][loop] fragment-loop=false:fragment-steps=5:vertex-steps=5:  FPS: 1823[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5:  FPS: 1821[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono][loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5:  FPS: 1671[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]=======================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]                                  glmark2 Score: 1645 [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]=======================================================[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Verdana]

vainfo
[/FONT][/COLOR]```
[COLOR=#000000][FONT=dejavu sans mono]vainfo[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libva: VA-API version 0.32.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libva: va_getDriverName() returns 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libva: va_openDriver() returns 0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]vainfo: VA-API version: 0.32 (libva 1.0.15)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]vainfo: Driver version: Intel i965 driver - 1.0.15[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]vainfo: Supported profile and entrypoints[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileMPEG2Simple            :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointVLD[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileMPEG2Main              :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointVLD[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileH264Baseline           :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointVLD[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileH264Baseline           :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointEncSlice[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileH264Main               :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointVLD[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileH264Main               :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointEncSlice[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileH264High               :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointVLD[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileH264High               :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointEncSlice[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileVC1Simple              :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointVLD[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileVC1Main                :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointVLD[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]      VAProfileVC1Advanced            :[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]VAEntrypointVLD[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Verdana]
I've also tried to change xubuntu window compositor to compton(I've found some thread with hint that this could help). I'm not absolutely positive, but MAYBE there was a slight improvement, but problem was still visible.

So that's it. I hope I did not forget anything.
Thanks in advance for any help.

Martin.
[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2013-09-17
> mplayer playing some video
The last time I checked, mplayer didn't support va-api without some patching, so it's probably not the best choice for an Intel GPU.

---

### Post by Martin_Mucha on 2013-09-18
the same problems occurs in vlc, so it's not directly related to mplayer.
It's integrated graphics on processor. Intel CPU is, by my opinion, better than nowadays AMD. And decision NOT TO buy GPU was quite rational too -- I do not need it, since I do just non-graphics related programming and watch films, no games.
---
But to the point. How to play movies without problems? Buy a GPU? Only possibility?

---

### Post by qyot27 on 2013-09-18
[http://mpv.io/](http://mpv.io/)

It benefits from the improved A/V sync that mplayer2 added, and in this case, also from native VAAPI support.  And tons of other fixes and improvements.

---

### Post by Yellow Pasque on 2013-09-18
> Also tested in KDE, booted from "live USB", after updates,
What version? Also 12.04 or something more recent?

> [http://mpv.io/](http://mpv.io/)
mpv's a nice little player, but if OP says it's happening with other programs, I doubt it will help here.

---

### Post by Martin_Mucha on 2013-09-19
KDE version: most recent, amd64.

ad mpv.io: Thanks for hint. I tried it immediately.
But it seems that compilation is not going to be easy. I've tried this command to configure it
```
./configure --prefix=/home/martin/mpv
```

but opengl is disabled, vaapi is disabled (probably bad autodetect), even JACK is disabled. So I run it once again with modified command, and start JACK server for him as a "subtle" hint

```
./configure --prefix="/home/martin/mpv" --enable-gl --enable-vaapi
```
still no OPENGL, vaapi YES, no JACK, no alsa, no pulse audio... weird stuff.

And configuration process fails, due to unsatisfied dependencies, which I do not know what to do with. In repository I do not have newer version and in this case it's always like if I download newer one from somewhere it usually requires to remove the old one first and forces of removal of all system. I do not have knowledge to do that. If you have link where I can learn that, I'll be thankful.

---

### Post by Yellow Pasque on 2013-09-19
> still no OPENGL, vaapi YES, no JACK, no alsa, no pulse audio... weird stuff.
You need the corresponding -dev packages.
This could help too: [http://packages.debian.org/source/sid/mpv](http://packages.debian.org/source/sid/mpv)

---

### Post by qyot27 on 2013-09-19
> **Temüjin said:**
> mpv's a nice little player, but if OP says it's happening with other programs, I doubt it will help here.
That really depends on what the real source of the problem is.  Just because it happens in more than one player doesn't necessarily mean all players are affected by it.  All I can say is that I have personally not experienced issues with tearing in mpv when running it with the intent of testing that functionality, whereas I did used to have that problem in mplayer and mplayer2 (although I'm also on a GeForce 6200, but even on an ancient computer like mine, there was a dramatic drop, if not complete elimination, in the amount of tearing after switching to mpv, purely through software...the 6200 has no hardware accelerated decoding).

The most likely explanations are that either the video driver has issues, the frame rendering stuff has bugs in need of fixing, or that having a compositor enabled is interfering with any or all of this.  I may run Compton for normal usage, but if I was going to do some serious media watching, I'd kill it before watching anything and simply restart it afterward if it's that important.

---

### Post by Martin_Mucha on 2013-09-19
well I tried to work with provided link. I've failed :)
decomposition is definitely good thing, but this is mental.

To install mpv I miss libass4 (not proper version) for that i miss libfontconfig1, for that i miss fontconfig-config and when tried to install this I reached terminal state: "Breaks existing package libfontconfig1 dependency fontconfig-config". Because when I tried to uninstall that, the rest of system would go with it.

It is definitely my fault, that I do not know how to manage library dependencies, but for me it's like when it's not available in distribution repository, it cannot be installed. You "have to" help me with that dependency hell -- I'm not able to do that.

---

### Post by Yellow Pasque on 2013-09-19
I gave the link as a reference of which packages you need to install using apt-get (because mpv is not in the Ubuntu repo yet). Please tell me you didn't try to download and install Debian packages...

---

### Post by Martin_Mucha on 2013-09-20
well ... Ok, I'm maybe stupid -- just as I said - I do not know, how to properly install that. And there is not clear way from "next, next, linux installed" to I know how to properly build unknown sw. That path is rather pretty steep.

So. *What* is the proper way how to do that then? Since in ubuntu repository there aren't libraries of need version, I assume, that one need to install all dev packages (hoping that all of them will be present there in sufficient version), than download sources of player and build it?

---

### Post by qyot27 on 2013-09-20
Dependencies:
```
sudo apt-get -y install build-essential subversion checkinstall git-core yasm \
docbook-xml docbook-xsl xsltproc libxml2-utils libaa1-dev libasound2-dev libcaca-dev libcdparanoia-dev libdca-dev \
libdirectfb-dev libenca-dev libesd0-dev libfontconfig1-dev libfreetype6-dev \
libfribidi-dev libgif-dev libgl1-mesa-dev libjack-jackd2-dev libopenal-dev libpulse-dev \
libsdl1.2-dev libsvga1-dev libvdpau-dev libxinerama-dev libxv-dev libxvmc-dev libxxf86dga-dev \
libxxf86vm-dev librtmp-dev libsctp-dev libsmbclient-dev libtheora-dev \
libogg-dev libxvidcore-dev libspeex-dev libvpx-dev libschroedinger-dev libdirac-dev libdv4-dev \
libopencore-amrnb-dev libopencore-amrwb-dev libmp3lame-dev libtwolame-dev \
libmad0-dev libgsm1-dev libbs2b-dev liblzo2-dev ladspa-sdk libopenjpeg-dev libfaad-dev \
libmpg123-dev libopus-dev libbluray-dev libaacs-dev libgtk2.0-dev
```

x264
```
git clone git://git.videolan.org/x264.git
cd x264
./configure --enable-static --enable-strip --enable-pic
make
sudo checkinstall --pkgname=x264 --pkgversion="3:$(./version.sh | awk -F'[" ]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes --fstrans=no --default
```

FFmpeg
```
git clone git://source.ffmpeg.org/ffmpeg.git
cd ffmpeg
./configure --enable-gpl --enable-version3 --enable-pic --enable-libxvid --enable-libx264 --enable-libtwolame --enable-libmp3lame --enable-libvorbis --enable-libschroedinger --enable-libspeex --enable-libopus --enable-libvpx --enable-libtheora --enable-avisynth
make
sudo checkinstall --pkgname=ffmpeg --pkgversion="7:$(date +%Y%m%d%H%M)-git" --backup=no --deldoc=yes --fstrans=no --default
hash x264 ffmpeg ffplay ffprobe
```

libass
```
git clone git://repo.or.cz/libass.git
cd libass
./autogen.sh --disable-shared
make
sudo checkinstall --pkgname=libass --pkgversion="1:$(grep Version libass.pc | sed 's/: /\t/g' | cut -f2)" --backup=no --deldoc=yes --fstrans=no --default
```

mpv
```
git clone git://github.com/mpv-player/mpv.git
cd mpv
./configure --disable-vdpau --disable-debug
make
sudo checkinstall --pkgname=mpv-player --pkgversion="3:$(git rev-list --count HEAD)" --backup=no --deldoc=yes --fstrans=no --default
```

---

### Post by Martin_Mucha on 2013-09-20
Thank you for your significant effort. I would not probably came up with all that. 
I tried that, but from first command package libopus-dev cannot be found.

I've ignored that and tried to pull sources from git a build them using second command, which failed also:

```

======================= Installation results ===========================
Makefile:3: config.mak: No such file or directory
./configure
Found yasm 1.1.0.2352
Minimum version is yasm-1.2.0
If you really want to compile without asm, configure with --disable-asm.
make: *** [config.mak] Error 1


****  Installation failed. Aborting package creation.


Cleaning up...OK


Bye

```

I know it's really hard to compile from distance like you did using me as a (stupid) opeartor. So what can be done next? Should I disable yasm (whatever it is). And I do not know what to do about missing makefile part (config.mak).

---

### Post by Yellow Pasque on 2013-09-20
Forget about it. Precise isn't up-to-date enough to easily build mpv from source.

---

### Post by qyot27 on 2013-09-21
> **Martin_Mucha said:**
> I know it's really hard to compile from distance like you did using me as a (stupid) opeartor. So what can be done next? Should I disable yasm (whatever it is). And I do not know what to do about missing makefile part (config.mak).
YASM handles the assembly code.  If you disable it, the result will be slow, so it needs to be built also.

Compile YASM:
```
wget http://www.tortall.net/projects/yasm/releases/yasm-1.2.0.tar.gz -O - | tar xzvf -
cd yasm-1.2.0
./configure
make
sudo checkinstall --pkgname yasm --pkgversion "1.2.0" --fstrans=no --backup=no --deldoc=yes --default
```

Compile Opus:
```
git clone git://git.opus-codec.org/opus.git
cd opus
autoreconf -fiv
./configure --disable-shared --disable-doc --enable-custom-modes
make
sudo checkinstall --pkgname=libopus --pkgversion="1:$(grep Version opus.pc | sed 's/Version: //g')-git" --backup=no --deldoc=yes --fstrans=no --default
```

---

