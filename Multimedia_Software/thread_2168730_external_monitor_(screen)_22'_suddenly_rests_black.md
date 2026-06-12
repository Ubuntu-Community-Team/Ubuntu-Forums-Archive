---
title: "external monitor (screen) 22' suddenly rests black"
date: 2013-08-19
forum: Multimedia Software
---

### Post by egerlach on 2013-08-19
Hi, 
after xubuntu 12.04 on my  lenovo B560  (intel graphics) worked fine for some months now the external monitor/ screen rests black! BIOS and Grub are shown but with the apperance of the graphical login of XFCE the monitor claims: "no input signal". Windows7 on same laptop works fine. Please help, I need the external monitor 22' urgently because of video recordings with LibreOffice impress. 

Last time  I worked with my laptop and external monitor / screen I started the laptop with power button and closed the lid directly after. The the external monitor displayed 1024x768px. I set in settings -> display  the mode to 1650x1050 like xubuntu suggested and all worked fine a whole day. Next day I can't get the external monitor worked like described! Please help!  Last months I didn't close the lid an all worked fine. Xubuntu seem to be very sensitive once the lid is closed while booting. I didn't expect that behaviour, I will never close the lid again ....! I hope I have not to install Xubuntu again ....

@ I installed xubuntu 12.04 on another partition completely new. And the external monitor NOT works either!! Same behaviour! I installed all offered update. But no success. I have two 22' and one 17' monitor with serveral cables.Win7 on this laptop work fine with 22' external monitor, I tested it again just 1 minute ago! Even extendet Deskop. So it's a xubuntu problem. The resolution must be some configuration I lost in xubuntu. Xubuntu seems not be able to run a external monitor out of the box. Have you ideas? 

```

Xorg.log.0

[  2862.968] (II) intel(0): EDID vendor "HSD", prod id 19321
[  2862.968] (II) intel(0): Using hsync ranges from config file
[  2862.968] (II) intel(0): Using vrefresh ranges from config file
[  2862.968] (II) intel(0): Printing DDC gathered Modelines:
[  2862.968] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  2862.968] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2862.968] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  2862.968] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2862.968] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2862.968] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  2862.968] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2862.968] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2862.968] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2862.968] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2862.968] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2862.968] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2862.968] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  2862.968] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2862.968] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2862.968] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  2862.968] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[  2862.968] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[  2862.968] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2862.968] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  2862.968] (II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[  2862.968] (II) intel(0): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
[  2863.054] (II) intel(0): EDID vendor "AUO", prod id 8940
[  2863.054] (II) intel(0): Printing DDC gathered Modelines:
[  2863.054] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[  2863.281] (II) intel(0): EDID vendor "AUO", prod id 8940
[  2863.281] (II) intel(0): Printing DDC gathered Modelines:
[  2863.281] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)

```

```
# lshw -C video
  *-display               
       Beschreibung: VGA compatible controller
       Produkt: Core Processor Integrated Graphics Controller
       Hersteller: Intel Corporation
       Physische ID: 2
       Bus-Informationen: pci@0000:00:02.0
       Version: 02
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: msi pm vga_controller bus_master cap_list rom
       Konfiguration: driver=i915 latency=0
       Ressourcen: irq:42 memory:f2000000-f23fffff memory:d0000000-dfffffff ioport:1800(Größe=8)

```

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3920
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```

```
 xrandrScreen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected (normal left inverted right x axis y axis)
   1680x1050      60.0 +
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     66.0     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
 
```

```
 $ cat .xsession-errorsopenConnection: connect: Datei oder Verzeichnis nicht gefunden
cannot connect to brltty at :0
xfce4-settings-helper: Another instance is already running. Leaving...


(polkit-gnome-authentication-agent-1:3098): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed


(polkit-gnome-authentication-agent-1:3098): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(xfce4-indicator-plugin:3143): libindicator-WARNING **: IndicatorObject class does not have an accessible description.


(xfce4-indicator-plugin:3143): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-bmrs8o/pkcs11: Datei oder Verzeichnis nicht gefunden


(xfce4-indicator-plugin:3143): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** Message: applet now removed from the notification area
[3120:3366:0819/082442:ERROR:object_proxy.cc(627)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[3120:3366:0819/082442:ERROR:object_proxy.cc(627)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[3120:3120:0819/082443:ERROR:object_proxy.cc(532)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files


(xfce4-display-settings:20115): xfconf-WARNING **: No bindings were found on the channel
[3120:3364:0819/084530:ERROR:native_backend_gnome_x.cc(448)] Keyring save failed: 


(xfce4-terminal:3117): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
Error: No running window found
[3949:3990:0819/085755:ERROR:object_proxy.cc(627)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[3949:3990:0819/085755:ERROR:object_proxy.cc(627)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[3949:3949:0819/085755:ERROR:object_proxy.cc(532)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files

```

tia 
Eckard

---

