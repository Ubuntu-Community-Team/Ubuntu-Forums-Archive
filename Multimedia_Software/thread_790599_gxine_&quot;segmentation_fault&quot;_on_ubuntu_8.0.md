---
title: "gxine &quot;segmentation fault&quot; on ubuntu 8.04"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Zizo on 2008-05-11
Hi,

I run **gxine song.mp3** in the terminal. gxine freezes and gives the following output:

[B]bind: No such file or directory
warning: configuration item media.audio_cd.cddb_cachedir points to a non-existent location /home/localhost/.xine/cddbcache
warning: configuration item media.capture.save_dir points to a non-existent location 
warning: configuration item media.dvd.raw_device points to a non-existent location /dev/rdvd
warning: configuration item media.dvd.css_cache_path points to a non-existent location /home/localhost/.dvdcss/
warning: configuration item media.video4linux.radio_device points to a non-existent location /dev/radio0
warning: configuration item media.video4linux.video_device points to a non-existent location /dev/video0
warning: configuration item media.wintv_pvr.device points to a non-existent location /dev/video0
warning: configuration item subtitles.separate.font_freetype points to a non-existent location 
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
CDROMREADTOCHDR: No medium found
WARN: open (/dev/cdrom): No medium found[/B]

when I close it, the following output pops up:
[B]
gxine has suffered a fatal internal error.
To get a backtrace, run gxine in a debugger such as gdb.
Then, when the error occurs:
  (gdb) thread apply all bt
gxine: error: Fatal error: Segmentation fault[/B]

I previously tried: **touch /etc/ld.so.nohwcap** it worked for few times and then crashed again like explained above.

Any solution? I am not able to use any other player as well.

---

