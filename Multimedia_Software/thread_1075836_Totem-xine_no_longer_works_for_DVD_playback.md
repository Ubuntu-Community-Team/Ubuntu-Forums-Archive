---
title: "Totem-xine no longer works for DVD playback"
date: 2009-02-20
forum: Multimedia Software
---

### Post by pmendham on 2009-02-20
I used to be able to play DVDs (with menus) through Totem-Xine but all of a sudden it has stopped working. It gets through the intro (pre-encryption, I guess) and then says "The source seems encrupted and can't be read.  Are you trying to play an encrypted DVD without libdvdcss?"  The answer to that question is "no", I have libdrdread, libdvdnav, libdvdcss all installed.  What's more, I can play the DVD fine with MPlayer and VLC, but not with Totem-Xine and Ogle.  I'm not sure when I last played a DVD, it may have been a month or so back.

```

$ uname -a
Linux eris 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
```

Any ideas, anyone?

TIA

---

### Post by mc4man on 2009-02-20
Check and see if libxine1-ffmpeg is installed, if not do so.

---

### Post by pmendham on 2009-02-21
Yes, libxine1-ffmpeg is already installed, but thanks for the suggestion.

What I don't get is that this all used to work, but not anymore.  I have no idea what has changed.  The only thing that I can think of that I've installed since the last time I used Xine is VirtualBox (for running Doze).  Are there any known issues with compatibility between VirtualBox and Xine?  Google's not showing me anything for this one.

---

### Post by mc4man on 2009-02-21
There were some recent updates to libxine1* that didn't cause any issues here but who knows (I was hesitant to install them but did.

You could try this (can't hurt, may help

Go to ~/.xine and inside will be a file 'catalog.cache'
Delete it and start up totem-xine or any xine engine app to rebuild it.

---

### Post by pmendham on 2009-02-22
Thanks for the suggestion, but unfortunately no joy, same problem (no change). I tend to install all updates suggested to me (perhaps naively) so I'm fairly sure I'm up to date with the libxine stuff.

---

### Post by mc4man on 2009-02-22
Now that I'm thinking about it in ubuntu that error message for xine engine players is usually very specific. In kubuntu it's a generic error when somethings wrong (wrong device, no libdvdcss2, no libxine1-ffmpeg, ect.

Why don't you try to get some better info. Run these one at a time 

 ```
export DVDCSS_VERBOSE=2
```

```
totem-xine > totem-xine_output 2>&1
```

Once totem opens go movie -> and pick the dvd (play disc ...)
Let it do whatever it's going to do and then look in home folder for a file "totem-xine_output" and see what it says

---

### Post by pmendham on 2009-02-22
Thanks for your reply.  I've attached the output from totem-xine as you suggested.  It doesn't seem to scream anything to me, what am I missing?

---

### Post by mc4man on 2009-02-22
Not sure, this is when the movie should start playing (in red
> ** (totem-xine:29373): DEBUG: Init of Python module
** (totem-xine:29373): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem-xine:29373): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem-xine:29373): DEBUG: Creating Python plugin instance
** (totem-xine:29373): DEBUG: Init of Python module
** (totem-xine:29373): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem-xine:29373): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem-xine:29373): DEBUG: Creating Python plugin instance
** Message: no file info
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdcss debug: opening target `///dev/scd0'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key with player keys
libdvdcss debug: decrypted disc key is 00:1b:e9:96:f9
libdvdcss error: failed opening raw device, continuing
libdvdcss debug: using CSS key cache dir: /home/peter/.dvdcss//THE_WIRE_SEASON_1_DISC_1/

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000f9a0
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000ffb0
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00045d85
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003a9f0e
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003a9f13
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: THE_WIRE_SEASON_1_DISC_1
libdvdnav: DVD Serial Number: 325173CA
libdvdnav: DVD Title (Alternative): THE_WIRE_SEASON_1_DISC_1
libdvdnav: Unable to find map file '/home/peter/.dvdnav/THE_WIRE_SEASON_1_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
[COLOR="Red"]demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.[/COLOR]
[COLOR="Blue"]libdvdcss error: read error
libdvdcss error: read error
libdvdcss error: read error
libdvdcss error: read error[/COLOR]
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdcss debug: opening target `///dev/scd0'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key with player keys
libdvdcss debug: decrypted disc key is 00:1b:e9:96:f9
libdvdcss error: failed opening raw device, continuing
libdvdcss debug: using CSS key cache dir: /home/peter/.dvdcss//THE_WIRE_SEASON_1_DISC_1/

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000f9a0
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000ffb0
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00045d85
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003a9f0e
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003a9f13
libdvdcss debug: key found in cache
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: THE_WIRE_SEASON_1_DISC_1
libdvdnav: DVD Serial Number: 325173CA
libdvdnav: DVD Title (Alternative): THE_WIRE_SEASON_1_DISC_1
libdvdnav: Unable to find map file '/home/peter/.dvdnav/THE_WIRE_SEASON_1_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
** (totem-xine:29373): DEBUG: Finalizing Python plugin instance
** (totem-xine:29373): DEBUG: Finalizing Python plugin instance

Then it repeats the process and I gather fails with the error message? Note that the first time right after the red it reports libdvdcss read errors.

You are using an older version of libdvdcss2 (1.2.5) though I'm gathering it's not a problem with vlc, ect.

You could try upgrading your libdvdcss2, then going into your home folder and deleting the .dvdcss folder (hidden folder) and then repeating the process.
Do you have the same totem-xine issue with disks other than 'the wire'? (great show imo)

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

---

