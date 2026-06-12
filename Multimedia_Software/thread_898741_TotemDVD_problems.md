---
title: "Totem/DVD problems"
date: 2008-08-23
forum: Multimedia Software
---

### Post by jarg on 2008-08-23
I'm having a problem playing dvds since I updated to 8.04.

Whenever I try to play a dvd in totem it crashes.

I started totem through the terminal and got this error

```

jared@terminal-jared:~$ totem
** (totem:7251): DEBUG: Init of Python module
** (totem:7251): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7251): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7251): DEBUG: Creating Python plugin instance
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 56 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

If I open a dvd and quickly pull another window up I can hear the dvd's audio in the background, but if i attempt to change to totem in order to watch it it will crash.

Any suggestions would be greatly appreciated.

---

### Post by jarg on 2008-11-25
Well I never got that fixed in 8.04, now I'm using 8.10 and have the same problem.
```

jared@jared-desktop:~$ totem dvd://
** (totem:6846): DEBUG: Init of Python module
** (totem:6846): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:6846): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:6846): DEBUG: Creating Python plugin instance
** (totem:6846): DEBUG: Init of Python module
** (totem:6846): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:6846): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:6846): DEBUG: Creating Python plugin instance
** Message: no file info
libdvdnav: Using dvdnav version 1.1.15 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda1 with libdvdcss.
libdvdread: Can't open /dev/sda1 for reading
libdvdread: Device /dev/sda1 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/jared/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.15 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: CLERKS
libdvdnav: DVD Serial Number: 26aea538
libdvdnav: DVD Title (Alternative): CLERKS
libdvdnav: Unable to find map file '/home/jared/.dvdnav/CLERKS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000128
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00004ea5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00005157
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0021d8ea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0021d8ee
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
**The error was 'BadAlloc (insufficient resources for operation)'.**
  (Details: serial 167 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
I'm pretty sure thats the problem, whatever that means. Hopefully I get help before the next version of ubuntu comes out.

---

### Post by jarg on 2008-12-04
Bump. Any help out there?

---

### Post by mc4man on 2008-12-04
Use ANY player other than totem (gstreamer) and you'll be fine.
(with libdvdcss2 installed, ( for totem-xine and or kaffeine, libxine1-ffmpeg is also required

Probably back in 8.04 installing ubuntu-restricted-extras may have helped, in 8.10 totem (gstreamer) is fairly broken as far as dvd movies from disc.

Many players default to /dev/dvd to access dvd disc's. Check that is where your drive is linked to.

Look for *-cdrom entry(s)

```
sudo lshw -C disk
```

---

### Post by jarg on 2008-12-04
Using Totem-xine
```
The program 'totem-xine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 88 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
Using VLC
```
BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86

```

Both Programs are able to get the disk's name (CLERKS) so I know they're reading the right place, but then crash.

---

### Post by mc4man on 2008-12-04
Try changing your video output and possibly your audio outputs. Vlc is set in it's preferences, totem in the system settings.

see here for short how to.

X11 probably will be your best bet for video

[http://ubuntuforums.org/showthread.php?p=6285279#post6285279](http://ubuntuforums.org/showthread.php?p=6285279#post6285279)

It wouldn't hurt to set both as default choices for Dvd Video if not already, see here at end of post

[http://ubuntuforums.org/showthread.php?p=6223490#post6223490](http://ubuntuforums.org/showthread.php?p=6223490#post6223490)

---

### Post by jarg on 2008-12-06
> **mc4man said:**
> Try changing your video output and possibly your audio outputs. Vlc is set in it's preferences, totem in the system settings.

see here for short how to.

X11 probably will be your best bet for video

[http://ubuntuforums.org/showthread.php?p=6285279#post6285279](http://ubuntuforums.org/showthread.php?p=6285279#post6285279)

It wouldn't hurt to set both as default choices for Dvd Video if not already, see here at end of post

[http://ubuntuforums.org/showthread.php?p=6223490#post6223490](http://ubuntuforums.org/showthread.php?p=6223490#post6223490)

Setting X11 as the video option in VLC worked, thank you.

---

