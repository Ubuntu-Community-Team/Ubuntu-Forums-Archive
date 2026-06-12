---
title: "DVDstyler Crashes when rendering ISO."
date: 2011-11-01
forum: Multimedia Software
---

### Post by Topazkitty on 2011-11-01
Hi, I'm trying to render a dvd i've made in DVDstyler. Every time I render an iso it crashes during the encoding stage and I need help with it so any help would be appreciated. My problem looks like this in the terminal below and I am using ubuntu 11.10

amanda@Amanda-1525:~$ dvdstyler

(dvdstyler:2422): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:2422): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:2422): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:2422): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[ac3 @ 0xda6020] max_analyze_duration reached
[ac3 @ 0xda6020] Estimating duration from bitrate, this may be inaccurate
[ac3 @ 0x1299a20] max_analyze_duration reached
[ac3 @ 0x1299a20] Estimating duration from bitrate, this may be inaccurate
Output #0, mpeg2video, to '/tmp/dvd-tmp/menu1-0.mpg_bg.m2v':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
[mpeg2video @ 0x128f000] rc buffer underflow
[mpegvideo @ 0xb34a00] max_analyze_duration reached
[mpegvideo @ 0xb34a00] Estimating duration from bitrate, this may be inaccurate
[ac3 @ 0xb34a00] max_analyze_duration reached
[ac3 @ 0xb34a00] Estimating duration from bitrate, this may be inaccurate
Segmentation fault
amanda@Amanda-1525:~$

---

### Post by Statik on 2011-11-01
I too am having a segfault with dvdstyler but not the same one. Here is my output:
```
statik@statik-laptop:~$ dvdstyler

(dvdstyler:4160): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:4160): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:4160): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:4160): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[mpeg @ 0x29edea0] max_analyze_duration reached
Output #0, dvd, to '/home/statik/Templates/dvd-tmp/menu1-0.mpg_bg.mpg':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 2 channels, s16, 64 kb/s
[ac3 @ 0x2258da0] Specified sample_fmt is not supported.
Segmentation fault

```

Definitely need this fixed. I have a project to output! :)

Statik

---

### Post by Topazkitty on 2011-11-01
> **Statik said:**
> I too am having a segfault with dvdstyler but not the same one. Here is my output:
```
statik@statik-laptop:~$ dvdstyler

(dvdstyler:4160): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:4160): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:4160): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(dvdstyler:4160): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[mpeg @ 0x29edea0] max_analyze_duration reached
Output #0, dvd, to '/home/statik/Templates/dvd-tmp/menu1-0.mpg_bg.mpg':
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 2 channels, s16, 64 kb/s
[ac3 @ 0x2258da0] Specified sample_fmt is not supported.
Segmentation fault

```Definitely need this fixed. I have a project to output! :)

Statik

I also get that error sometimes too I wish they would fix this program it was fine in 11.04 and 10.10.

---

### Post by Sharpie1 on 2011-11-08
I have the same error when trying to make an ISO, a workaround is to convert the audio track to stereo MP2(Twolame)
But its an annoying bug as AC3 5.1 should be dvd compatible

Sharpie1

---

### Post by Statik on 2011-11-08
There is no reason for this error. Either the program should detect the fault and recode, or it should accept it as working.

Statik

---

