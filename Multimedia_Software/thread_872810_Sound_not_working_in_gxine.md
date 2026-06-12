---
title: "Sound not working in gxine"
date: 2008-07-28
forum: Multimedia Software
---

### Post by theophiles on 2008-07-28
I will give the readout for gxine
```
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier `tooltip_bg_color', expected valid identifier
bind: No such file or directory
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/bcline/.xine/cddbcache
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvd.raw_device points to a non-existent location /dev/rdvd
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0
warning: configuration item decoder.external.real_codecs_path points to a non-existent location 
warning: configuration item decoder.external.win32_codecs_path points to a non-existent location /usr/lib/codecs
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?

```
when I choose an audio file I get
```
CDROMREADTOCHDR: No medium found
WARN: open (/dev/cdrom): No medium found
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier `tooltip_bg_color', expected valid identifier
```
I get nothing. No sound.
Note: I am not choosing a file from a CD
after closing I get:
```
gxine has suffered a fatal internal error.
To get a backtrace, run gxine in a debugger such as gdb.
Then, when the error occurs:
  (gdb) thread apply all bt
gxine: error: Fatal error: Segmentation fault
```

Can someone help me?

---

