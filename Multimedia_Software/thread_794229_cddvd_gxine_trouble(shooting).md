---
title: "cd/dvd gxine trouble(shooting)"
date: 2008-05-14
forum: Multimedia Software
---

### Post by maclenin on 2008-05-14
Essentially, I am unable to play either CDs or DVDs* in my (Feisty - HP 6910p - with fglrx) combo drive using gxine.

Background:

1. I've run the "gxine setup wizards" and configured /etc/modules to look like this (primarily, to address DMA-related issues)...

```
piix
ide-core
ide-cd
ide-disk
ide-generic
lp
sbp2
```

2. The gxine "system configuration check" shows all "green".

3. However, when I insert a CD into the drive and start gxine (via the terminal), I receive the following stream of announcements... 

```
xxx@xxx:~$ gxine
gtkvideo: failed to get a proxy for gnome-screensaver
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
  sysname: Linux
  release: 2.6.20-16-generic
  machine: i686
X-Video Extension version 2.2
video_out_xv: Xv image format: 0x32315659 (YV12) planar
video_out_xv: this adaptor supports the yv12 format.
video_out_xv: Xv image format: 0x30323449 (I420) planar
video_out_xv: Xv image format: 0x41424752 (RGBA) packed
received X error event: BadMatch (invalid parameter attributes)
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 410 error_code 8 request_code 141 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
xxx@xxx:~$
```

...any thoughts?

Thanks for whatever guidance anyone can send along!

*The DVD errors are listed in the follow-up post....

---

### Post by maclenin on 2008-05-16
3a. After installing the following (in an attempt to get a test DVD to play)...

**sudo aptitude install gxine libxine1-ffmpeg**
 
**sudo aptitude install libdvdcss2 libdvdread3 libdvdnav4 build-essential debhelper fakeroot**

**sudo /usr/share/doc/libdvdread3/install-css.sh**

...I receive the following error messages... 

```
xxx@xxx:~$ gxine dvd:/
gtkvideo: failed to get a proxy for gnome-screensaver
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
  sysname: Linux
  release: 2.6.20-16-generic
  machine: i686
X-Video Extension version 2.2
video_out_xv: Xv image format: 0x32315659 (YV12) planar
video_out_xv: this adaptor supports the yv12 format.
video_out_xv: Xv image format: 0x30323449 (I420) planar
video_out_xv: Xv image format: 0x41424752 (RGBA) packed
libdvdnav: Using dvdnav version 1.1.4 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: RETURN_OF_THE_JEDI
libdvdnav: DVD Serial Number: 34de1e63
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/xxx/.dvdnav/RETURN_OF_THE_JEDI.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00017dea
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000750e5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000751a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000751a0)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0007526d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00075328
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x00075328)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0007edc8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x0007edc8)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000818a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x000818a0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003d6e14
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x003d6e14)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003d6ecf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003d8b3a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x003d8b3a)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003d8c06
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x003d8c06)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003d8ce4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x003d8ce4)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003d8d9f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003d9a7b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003d9b36
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x003d9b36)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003d9c03
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003d9cbe
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x003d9cbe)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003d9e49
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003d9e4e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x003d9e4e)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003dc22b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003dc230
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x003dc230)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003dc6c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003dc6ca
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x003dc6ca)!!
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 3
xine-lib: error: Read error from::  Error reading from DVD.
received X error event: BadMatch (invalid parameter attributes)
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 419 error_code 8 request_code 141 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
xxx@xxx:~$
``` 

I'll check back as I continue to trouble-shoot.

Thanks for any suggestions!

---

### Post by maclenin on 2008-05-17
Any thoughts?

---

### Post by mc4man on 2008-05-17
the first thing to ck. is that you have a region set on drive, if you know it's set then ignore this (in your case region 1), if not install regionset and with a _dvd in the driv_e run regionset. here is ex. of a set drive
```
doug@doug-desktop:~$ regionset 
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET     [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]: n
```
If it wasn't set then set it, clear the .dvdcss folder and try gxine again. If it was set then answer no and try below or if playback still fails after setting the region, then try below also.
Note ; everytime you try something new it's good to go into home dir., find  .dvdcss (hidden) and delete all the folders _inside_, this eliminates possibility of corrupted decryption keys.
With a dvd in the drive run 
```
export DVDCSS_METHOD=title && gxine dvd://
``` and see if you get playback. If that happens to work post back and there's a couple of ways to make parameter  permanent.

---

### Post by maclenin on 2008-05-17
**mc4man:**

Thanks for the guidance. Before I address your suggestions, I have a couple of additional gxine-related observations:

1. gxine closes, automatically, after it completes its "gxine setup wizards" routine - even when I am not asking it to play any media. It opens (if I call it up via the menu or terminal),  runs through it's diagnostic cycle and terminates (after I close its completed diagnostics window). Seems an unusual behavior to me.

2. I am not able to play mp3s from my hard drive using gxine. The same start-up, diagnose and terminate behavior is observed.

3. The messages/errors I observe when opening gxine (without media) - are the same as those observed when I opened gxine to play the CD (audio). Incidentally, the results of the gxine self-diagnostics/setup wizards routine are always "green" (positive).

As for your suggestions:

4. I installed and ran an initial "test" using regionset, here's the output...

```
xxx@xxx:~$ regionset /dev/hda
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:
```

...it seems I do not have a "regionset" for this drive.

5. I have been able to play DVDs using gxine (oddly enough, given the other troubles I am having with gxine) - though, the DVDs I've been able to play are not "Hollywood" pieces - so probably not encrypted to withstand the coming apocalypse.

6. I find it odd, as well, that I am not able to play store-bought audio CDs using gxine. Could region settings affect this behavior?

That's it, for now....

I'd like to get your sense of the "new" gxine issues I've addressed, before I jump into the regionset process. Perhaps there's something even more fundamentally wrong going on?

Thanks, again!

---

### Post by mc4man on 2008-05-18
> before I jump into the regionset process.
There is no 'downside' to having a region set. If you want to play most css encrypted titles and all rce protected ones _then it's a must_.
so set the region to 1, clear out the contents of .dvdcss and check for playback. 
> I find it odd, as well, that I am not able to play store-bought audio CDs using gxine. Could region settings affect this behavior?
There is no connection between region settings and cd's. Whether there's a common cause between no cd playback and no dvd playback remains to be seen. What I mentioned in previous post is only concerning / affecting dvd playback.

---

### Post by maclenin on 2008-05-19
**mc4man:**

**1. DVD playback!**

Regionset (without the need for **export DVDCSS_METHOD=title && gxine dvd://**) seems to have cleared up the DVD playback issue - for the most part (...there is one DVD - a supplemental materials "disc 2" that will not play - though "disc 1" of the set will play) - thanks for that.... This issue has been back-burnered, for now!

**2. CD playback.**

Still not happening.

See **4.**, for Errors.

**3. MP3 playback.**

Still not happening.

**4. Gxine start-up (without media).**

Still not happening.

Errors:

```
xxx@xxx:~$ gxine
gtkvideo: failed to get a proxy for gnome-screensaver
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
  sysname: Linux
  release: 2.6.20-16-generic
  machine: i686
X-Video Extension version 2.2
video_out_xv: Xv image format: 0x32315659 (YV12) planar
video_out_xv: this adaptor supports the yv12 format.
video_out_xv: Xv image format: 0x30323449 (I420) planar
video_out_xv: Xv image format: 0x41424752 (RGBA) packed
received X error event: BadMatch (invalid parameter attributes)
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 411 error_code 8 request_code 141 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
xxx@xxx:~$ 
```

Thanks for the regionset clue.

Still not certain how to proceed re: the other playback issues....

---

### Post by mc4man on 2008-05-19
> there is one DVD - a supplemental materials "disc 2" that will not play Look in .dvdcss for a folder specific to that title and delete it. If not apparent you can safely delete all the folders in .dvdcss. (they are rebuilt next time you playback any particular title)
I'm not up on gxine but I'll fool around a bit
Can you playback cd's with the default player (totem ?)
for mp3 the easiest would be r. click on the mp3 and choose open with movie player. Totem should open and offer to shearch,  install suitable codecs. If that doesn't happen the install GStreamer extra plugins and GStreamer ffmpeg video plugin. wouldn't hurt to also install w32codecs from medibuntu repo

---

### Post by maclenin on 2008-05-21
**mc4man:**

1. **re: .dvcss contents deletion** - been there and done that and still receive the following error - ONLY with "disc 2" ("disc 2" plays in other DVD players - the disc, itself, seems fine): 

```
xxx@xxx:~$ gxine dvd://
gtkvideo: failed to get a proxy for gnome-screensaver
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
libdvdnav: Using dvdnav version 1.1.4 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda1 with libdvdcss.
libdvdread: Can't open /dev/sda1 for reading
libdvdread: Device /dev/sda1 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/xxx/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.4 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: MY_FAIR_LADY_DISC_2
libdvdnav: DVD Serial Number: 2F829535
libdvdnav: DVD Title (Alternative): MY_FAIR_LADY_DISC_2
libdvdnav: Unable to find map file '/home/xxx/.dvdnav/MY_FAIR_LADY_DISC_2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
libdvdnav: Suspected RCE Region Protection!!!

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001e8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000008f2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001d640d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001da682
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00218069
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0022716c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00231e40
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
xine-lib: error: Read error from::  Error reading from DVD.
received X error event: BadMatch (invalid parameter attributes)
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 422 error_code 8 request_code 141 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
xxx@xxx:~$
``` 

2. **gxine is the default and seemingly only player installed - for audio and/or video.** When I run "totem" from the terminal, I receive the following:

```
xxx@xxx:~$ totem
The program 'totem' can be found in the following packages:
 * totem-gstreamer
 * totem-xine
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: totem: command not found
xxx@xxx:~$ 
```

3. **Still unable (via gxine) to play CDs (audio) and MP3s or start-up gxine, independently.**

Thanks for your guidance.

---

### Post by mc4man on 2008-05-21
In the long run why don't you install a better player than gxine. For movies totem-xine or vlc. 
As far as mp3's I'm not to sure gxine will play them and again better to use a music player. There are many choices -  Audacious, Banshee, Exaile, Rhythmbox, ect.
1 of many threads in archives from feisty time frame
[http://ubuntuforums.org/archive/index.php/t-522954.html](http://ubuntuforums.org/archive/index.php/t-522954.html)

---

### Post by maclenin on 2008-05-22
**mc4man:**

Do these errors mean anything to you?

...in **GXINE:**
```
**xine-lib: error: Read error from::  Expected NAV packet but none found.**
```

...in **VLC:**
```
**libdvdnav: demux error! 04 00 05 (should be 0x000001)**
```

...happened upon these errors at the (seemingly) exact same point about 9 chapters into the same DVD. The error message(s) appears and the DVD shuts down.

Merrily we roll along....

---

### Post by mc4man on 2008-05-22
What it means is that at the layer break transition the player isn't receiving info in a timely manner (or at all). You could test if it's confined to the layer break or layer1 in general by using vlc to start or jump ahead to chapter 10 or so. You may want to check the condition of the disk, the layer break area is towards the outside edge, fingerprints ect. More than likely this is a drive issue, as drives get older they may have problems reading layer1 particularly at the layer break. 
You could try a cd/dvd cleaning disk (Maxwell makes one) but I certainly wouldn't over use it.

edit; 2 other possibilities are stamping defects of the disk itself, or while very unlikely, ubuntu itself. That could only be tested with a dual boot set up. If you recently purchased that title I'd try to return it as defective and get a new copy.

---

### Post by maclenin on 2008-05-23
**mc4man:**

**Hmmmm...**

The drive (as well as the laptop and the rest of its innards) is not yet a year old.

The disc I am playing is a about 2 years old, but runs without error in other non-linux-driven DVD drives/players.

I have never run windows on this laptop - linux only.

I was able to ffwd over the place it breaks - i.e. could see the "breaking place" zoom by as I ffwd to a few frames after the break - and it would play from beyond the break (i.e. chapter 10). There was a second break - a few scenes later. Again, I can skip around to other parts of the disk - there are just very specific points at which the "NAV" error occurs....

**A few momnents later...**

So...I polished the disc and the problem seems to have gone away (in both gxine and vlc and at both breaking places)....

Again, I have NEVER had this issue with other non-linux-driven drives.

**Bottom line....**

Is the linux-driven drive a more "sensitive" drive, for some reason (don't see how software could make a drive more susceptible to these types of "errors")? Or could it be that the drive, itself, is more sensitive, somehow?

Thanks, again - for the house-cleaning advice....

---

