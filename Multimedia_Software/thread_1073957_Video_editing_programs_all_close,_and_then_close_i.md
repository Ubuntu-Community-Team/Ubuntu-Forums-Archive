---
title: "Video editing programs all close, and then close immediately. after opening"
date: 2009-02-18
forum: Multimedia Software
---

### Post by nicklikesfire on 2009-02-18
So I've tried three video editing programs so far, and the end result has been the same for all of them. Kino, kdenlive, and open movie editor. They all work for a few minutes, and then close. After that they all close immediately after opening.

Any ideas for getting a video editor to work? I'm running Ubuntu 8.10 - the Intrepid Ibex, and a GNOME desktop. I'm also not really great at this, so if you do happen to be able to, and nice enough to help me out, simple directions are better.

Thanks so much.

---

### Post by nicklikesfire on 2009-02-20
Bump...

---

### Post by Eddie Wilson on 2009-02-20
What kind of media are you trying to edit. I've found that for me the video editing programs would close if it discovered defective media. I don't know if that is your case but that's the only time I've had any problems.

---

### Post by nicklikesfire on 2009-02-20
Hmm, I don't think that's it. I've been trying to edit a .mov file that has no trouble opening otherwise, but it doesn't really matter, the programs will not stay open long enough for me to open anything. All three pretty much just flash the program on the screen, and then close right away.

Thanks though, any other ideas?

---

### Post by cotcot on 2009-02-20
Start the editors from command line (type 'kino' or 'kdenlive' in terminal). This will should hopefully an error message. Kino crashing is not normal.

---

### Post by nicklikesfire on 2009-02-20
> **cotcot said:**
> Start the editors from command line (type 'kino' or 'kdenlive' in terminal). This will should hopefully an error message. Kino crashing is not normal.

I ran both programs from the command line, and this is whatn I got. I don't know what any of it means, but maybe someone can make sense of it? Thanks, I'm glad this looks like something is going somewhere.


```
(kino:7876): Gdk-WARNING **: /build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkproperty-x11.c:318 invalid X atom: 344
The program 'kino' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1291 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```


```
nick@burn-desktop:~$ kdenlive
kbuildsycoca running...
Reusing existing ksycoca
KCrash: Application 'kdenlive' crashing...
Unable to start Dr. Konqi
DCOP aborting while waiting for answer from 'klauncher'
nick@burn-desktop:~$ DCOPServer::DCOPReply for unknown connection.
Could not find 'drkonqi' executable.
ICE default IO error handler doing an exit(), pid = 8164, errno = 11

nick@burn-desktop:~$ 


```

---

### Post by cotcot on 2009-02-21
For kino it seems to be an issue with Xvideo. There are some bug reports on it but I could not get much info from it. Xvideo is a tool for faster showing video. Check in synaptic if you have [COLOR="Blue"]libxv[/COLOR]. You can also check this in terminal with : ```
xvinfo
``` If you do not have it install it. If you have it reinstall it.

You could try to open kino and change the display method in --> edit --> preferences --> display to [COLOR="Blue"]gdk[/COLOR] instead of [COLOR="Blue"]xvideo[/COLOR]. This does not solve the problem but will at least allow you to go on with kino. As the error message explain you will probably get more info when starting kino like this :
```
kino --sync
```

The kdenlive error message does not tell a lot. It cannot start the debugging tool.
However kdenlive crashes are not unusual (i guess you run kdenlive 0.5 from the repos and not 0.7)
What about open movie error messages ?

As a summary i do not think that there is something wrong with the video editor rather with the graphics performance to show video. What hardware chipset do you have ? There are some bug reports on the GMA3100 chipset and the xserver-xorg-video-intel package.

---

### Post by nicklikesfire on 2009-02-21
Thanks for the help so far!

I reinstalled everything having to do with libxv through synaptic.

```
nick@burn-desktop:~$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Radeon Textured Video"
    number of ports: 16
    port base: 57
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 1
      "XV_BICUBIC" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
    maximum XvImage size: 4096 x 4096
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
nick@burn-desktop:~$ 

```

I still can not open kino. Here's the readout from trying with kino--sync:

```
nick@burn-desktop:~$ kino --sync
> help language code en
> Kino Common being built
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating ExportMJPEG Page
/usr/share/kino/scripts/dvdauthor/dvdauthor.sh
/usr/share/kino/scripts/dvdauthor/dvdauthor-k3b.sh
/usr/share/kino/scripts/dvdauthor/growisofs.sh
/usr/share/kino/scripts/dvdauthor/qdvdauthor.sh
/usr/share/kino/scripts/dvdauthor/none.sh
> Initializing MJPEG Export Page settings from Preferences
> Creating ExportPipe Page
/usr/share/kino/scripts/exports/ffmpeg_mp4_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_mov.sh
/usr/share/kino/scripts/exports/ffmpeg_divx.sh
/usr/share/kino/scripts/exports/ffmpeg_flv.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd.sh
/usr/share/kino/scripts/exports/ffmpeg2theora.sh
/usr/share/kino/scripts/exports/ffmpeg_mp3.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid.sh
/usr/share/kino/scripts/exports/mencoder.sh
/usr/share/kino/scripts/exports/ffmpeg_3gp.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
/usr/share/kino/scripts/exports/ffmpeg_utils.sh
/usr/share/kino/scripts/exports/extract_chapters
/usr/share/kino/scripts/exports/ffmpeg_divx_dual.sh
/usr/share/kino/scripts/exports/gstreamer_utils.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_xvid_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_vcd.sh
/usr/share/kino/scripts/exports/gstreamer_theora.sh
/usr/share/kino/scripts/exports/rawplay.sh
> Creating page trim
>>> Image Create: Colour Range
>>> Image Create: Fixed Colour
>>> Image Create: From File
>>> Image Create: Gradient
>>> Image Create: Random noise
>>> Image Filter: No Change
>>> Image Filter: Black & White
>>> Image Filter: Kaleidoscope
>>> Image Filter: Fade In
>>> Image Filter: Fade Out
>>> Image Filter: Flip
>>> Image Filter: Mirror
>>> Image Filter: Reverse Video
>>> Image Filter: Sepia
>>> Image Transition: Dissolve
>>> Image Transition: Barn Door Wipe
>>> Image Transition: Differences
>>> Image Transition: No Change
>>> Image Transition: Push Wipe
>>> Image Transition: Switch
>>> Audio Filter: No Change
>>> Audio Filter: Dub
>>> Audio Filter: Fade In
>>> Audio Filter: Fade Out
>>> Audio Filter: Gain
>>> Audio Filter: Mix
>>> Audio Filter: Silence
>>> Audio Transition: Cross Fade
>>> Audio Transition: No Change
> Creating Magick Page
>> Searching /usr/lib/kino-gtk2 for plugins

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
>>> Registering plugin /usr/lib/kino-gtk2/libtimfx.so
>>> Registering plugin /usr/lib/kino-gtk2/libdvtitler.so

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
>>> Registering plugin /usr/lib/kino-gtk2/libkinoplus.so
>>> Image Filter: Blur
>>> Image Filter: Colour Hold
>>> Image Filter: Soft Focus
>>> Image Transition: Luma Wipe

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
>>> Image Filter: Superimpose

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
>>> Image Filter: Titler
>>> Image Filter: Colour Average
>>> Image Filter: Charcoal
>>> Image Filter: Jerky
>>> Image Filter: Levels
>>> Image Filter: Pan and Zoom
>>> Image Filter: Pixelate
>>> Image Transition: Composite
>>> Image Transition: Blue Chroma Key
>>> Image Transition: Green Chroma Key

(kino:6978): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
>> Starting Editor
>> Creating undo/redo buffer
>>> Received playlist to store at position 0
>>>> Adding to end
>>> Received request to undo from position 0
>> Trying XVideo at 720x480
>>> XvQueryAdaptors count: 1
>>> Xv: Radeon Textured Video: ports 57 - 72
>>> formats supported: 4
>>>     0x32595559 (YUY2) packed
>>>     0x32315659 (YV12) planar
>>>     0x30323449 (I420) planar
>>>     0x59565955 (UYVY) packed
>>> 0: XV_IMAGE, 4096x4096 rate = 1/1
The program 'kino' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1489 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
nick@burn-desktop:~$ 

```

Sorry, I know that's a lot of stuff.

Would it be possible to change from xvideo to gdk using the terminal, without opening kino?

Open movie editor works when I open it through the terminal or app menu, but the sound is static.

```
nick@burn-desktop:~$ openmovieeditor
When submitting a BUG report, or SUPPORT request, please include the following information:
----8<-----------------------
Libquicktime Version: 1.0.2
Libquicktime API Version: 9
libavcodec Version: Lavc51.50.0
libavformat Version: Lavf52.7.0
/etc/debian_version:
lenny/sid
/etc/lsb-release:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
----8<-----------------------
could not connect to jack.
When submitting a BUG report, or SUPPORT request, please include the following information:
----8<-----------------------
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 TCL
OpenGL version string: 1.3 Mesa 7.2
GL_MAX_TEXTURE_SIZE = 4096
----8<-----------------------
mdb:269, lastbuf:0 skipping granule 0
mdb:269, lastbuf:0 skipping granule 0
mdb:269, lastbuf:0 skipping granule 1
mdb:269, lastbuf:0 skipping granule 0
mdb:269, lastbuf:0 skipping granule 0
mdb:269, lastbuf:0 skipping granule 1
mdb:273, lastbuf:0 skipping granule 0
mdb:273, lastbuf:0 skipping granule 0
mdb:273, lastbuf:0 skipping granule 1
mdb:269, lastbuf:0 skipping granule 0
mdb:269, lastbuf:0 skipping granule 0
mdb:269, lastbuf:0 skipping granule 1
nick@burn-desktop:~$ 


```

As for hardware:

Asus A8N-SLI SE Motherboard
AMD Athlon 64 X2 3800+ Processor ADA3800DAA5CD - 2.0GHz
2GB (4 x 512MB) 184-Pin DDR SDRAM DDR 400
SAPPHIRE 100164DDR2L Radeon X1650PRO 256MB 128-bit GDDR2 PCI Express x16 Videocard

Also, I have not activated the "ATI/AMD proprietary FGLRX graphics driver" Should I do that?

---

### Post by cotcot on 2009-02-21
Sorry, I cannot find something new in the outputs. I do not see command allowing to start kino from terminal without xv. But according to the outputs it does not look like xv is the problem.

And yes install the proprietary ATI driver. It is a pity not to use it with such a card.

---

