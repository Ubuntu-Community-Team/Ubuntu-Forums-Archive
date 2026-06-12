---
title: "Installed everything, but still can't watch DVDS"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by defenestratos on 2008-01-19
I have installed everything I need; 
gxine
 libdvdcss2 
libdvdnav4
Iibdvdplay0
libdvdread3
but when I run Gxine I get;
> hugo@hugo-laptop:~$ gxine -S dvd:/
gtkvideo: failed to get a proxy for gnome-screensaver
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
libdvdnav: Using dvdnav version 1.1.4 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: IM_ALAN_PARTRIDGE
libdvdnav: DVD Serial Number: 2d5b8efb
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/hugo/.dvdnav/IM_ALAN_PARTRIDGE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001a6c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00042f3d
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
xine-lib: error: The xine engine failed to start.: No demuxer found - stream format not recognised.
server: client disconnected
libdvdnav: Using dvdnav version 1.1.4 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: IM_ALAN_PARTRIDGE
libdvdnav: DVD Serial Number: 2d5b8efb
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/hugo/.dvdnav/IM_ALAN_PARTRIDGE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001a6c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00042f3d
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
xine-lib: error: The xine engine failed to start.: No demuxer found - stream format not recognised.

What is going on?

---

### Post by Riverside on 2008-01-19
Possibly:

[http://ubuntuforums.org/showpost.php?p=4162727](http://ubuntuforums.org/showpost.php?p=4162727)

---

### Post by defenestratos on 2008-01-23
Its something to do with my setup because I have watched this DVD before on my computer before I did a reinstall. Totem always gives me grief.

---

### Post by defenestratos on 2008-01-26
Is anybody there? I am dying to know what a demuxer is. Also, how do I disable programs from starting automatically when I put discs in?
OK so Gxine says..
The xine engine failed to start.
No demuxer found - stream format not recognised.

Totem says:
Totem could not play 'dvd:/'.
There is no plugin to handle this movie.

Mplayer says 
Error opening/initializing the selected video_out (-vo) device.

Ideas?

---

### Post by cotcot on 2008-01-26
I have put VLC as default.

I installed dvd play back with this command :

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse libdvdcss2
```

---

