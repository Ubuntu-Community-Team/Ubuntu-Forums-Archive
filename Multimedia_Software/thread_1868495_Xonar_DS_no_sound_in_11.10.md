---
title: "Xonar DS no sound in 11.10"
date: 2011-10-24
forum: Multimedia Software
---

### Post by netmunky on 2011-10-24
recently installed 11.10, hardware shows up fine in sounds prefs, but test speakers produces no sound, and media players (vlc, mplayer, banshee, chrome/flash) produce no sound.

```

ghanover@whiteflyer:~$ uname -a
Linux whiteflyer 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
ghanover@whiteflyer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DS [Xonar DS], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: DS [Xonar DS], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ghanover@whiteflyer:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.24.

```

levels are up and not muted in alsamixer. using analog stereo output.

one thing i do notice is in many forum posts, there are /proc/asound/card*/codec#* files, and i have none.

i also have onboard audio, but that never worked in windows either (which is why i have the xonar ds).

ideas?

---

### Post by blackmail on 2011-10-24
Please try the following:

install aptitude
```
sudo apt-get install aptitude
```

and then search for gnome alsa mixer

```
sudo aptitude search gnome | grep alsa
```

it should ive you back the alsa mixer, try to reinstall it, I think this sghould help, it helped me many times when i have had trouble.

---

### Post by netmunky on 2011-10-24
gnome-alsamixer fails with a whole slew of errors and a segfault

```

(gnome-alsamixer:24224): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_icon_theme_has_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(gnome-alsamixer:24224): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(gnome-alsamixer:24224): GLib-CRITICAL **: g_hash_table_insert_internal: assertion `hash_table != NULL' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_icon_theme_has_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_icon_theme_has_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_icon_theme_has_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gdk-CRITICAL **: IA__gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gdk-CRITICAL **: IA__gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gdk-CRITICAL **: IA__gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gdk-CRITICAL **: IA__gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gdk-CRITICAL **: IA__gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gdk-CRITICAL **: IA__gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gdk-CRITICAL **: IA__gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(gnome-alsamixer:24224): Pango-CRITICAL **: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

** (gnome-alsamixer:24224): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "ADC Filter"!

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

** (gnome-alsamixer:24224): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Level Control"!

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(gnome-alsamixer:24224): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

** (gnome-alsamixer:24224): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Stereo Upmixing"!

(gnome-alsamixer:24224): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-alsamixer:24224): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-alsamixer:24224): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(gnome-alsamixer:24224): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(gnome-alsamixer:24224): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(gnome-alsamixer:24224): GLib-CRITICAL **: g_hash_table_insert_internal: assertion `hash_table != NULL' failed

(gnome-alsamixer:24224): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed
Segmentation fault


```

---

### Post by dumpster25 on 2011-10-27
Netmunky, I also own a Xonar DS. I recently installed it and sound works.
What happens if you type lspci on the terminal?

---

### Post by netmunky on 2011-10-27
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600 Series]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b1)
**07:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]**
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]

```

---

### Post by netmunky on 2011-10-27
i unplugged the internal wire that connects the front audio panel, and now the back audio plugs works. go figure.

now to figure out why the second video card isn't working...

---

### Post by Ranger21 on 2011-10-28
Omg, i need front panel and back panel for work. Bug is not solved

---

### Post by netmunky on 2011-10-28
When I used the card in win7, I had to manually select the output (front or back) using the Asus installed software. My guess is it is not being selected properly when both are available (though I'm pretty sure I tested the front panel and got no audio when it was plugged in).

---

### Post by Ranger21 on 2011-10-28
Yes, yes... i can understand all of that.

But i need front panel and back panel both in linux.

There was a patch in a forum, which worked for older kernel. Why they don't put new bugfixes in new alsa/kernel?

---

### Post by matiasw on 2011-11-24
There's a patched version linked to [this discussion]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=646559"), available as [Debian packages]("http://adn.diwi.org/tmp/0.9.7~cvs.20060916.ds.1-3/"). It fixed gnome-alsamixer for me, but I've still got no sound with a 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Launching gnome-alsamixer gives
```
** (gnome-alsamixer:11893): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

```

Used to work in 11.04. Also, I got some crackles and intermittently, the sound will work perfectly, only to be muted once again (no, mute mode does not turn on on its own, the sound just goes away). Also, see [https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/849415](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/849415) for a different but similar problem.

---

