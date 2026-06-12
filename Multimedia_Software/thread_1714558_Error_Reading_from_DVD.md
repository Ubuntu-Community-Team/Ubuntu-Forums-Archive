---
title: "Error Reading from DVD"
date: 2011-03-25
forum: Multimedia Software
---

### Post by RichardC400 on 2011-03-25
I have Gxine 0.5.905, Movie Player and VLC.
I am trying to play an ordinary DVD. But i keep getting Error Reading from DVD [gxine] Error reading from source [Movie Player] and VLC just doesnt come up with an error and doesn't play anyway.
I have Ubuntu 10.10 Desktop.

Any help for a newbie?

---

### Post by mc4man on 2011-03-25
you could open a terminal (Applications > Accessories > Terminal) and then copy and paste this in, press enter on keyboard
```
sudo /usr/share/doc/libdvdread4/install-css.sh 
```

====================================================================================

If you wanted to add  additional decoding support to gstreamer apps and in general then do then same with this command
```
sudo apt-get install ubuntu-restricted-addons
```

for a bit more restricted stuff inc. encoding support then this 
```
sudo apt-get install ubuntu-restricted-extras 
```

Or the various gstreamer plugins and codec related packages can be installed selectively

---

### Post by mrpenguin on 2011-03-25
I have the exact same problem, Running Ubuntu 10.10 64bit .... I have installed everything above but it did not fix the problem.

Error reading from source [Movie Player] and VLC just doesnt come up with an error and doesn't play the movie.

---

### Post by mc4man on 2011-03-25
> **mrpenguin said:**
> I have the exact same problem, Running Ubuntu 10.10 64bit .... I have installed everything above but it did not fix the problem.

Error reading from source [Movie Player] and VLC just doesnt come up with an error and doesn't play the movie.
Start vlc from a terminal, then try to play a dvd and post terminal output

---

### Post by mrpenguin on 2011-03-25
This is what I get from vlc in the terminal

This is from a store bought DVD movie

> jaques@jaques-laptop:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x253e120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7fb27f4f3b20, 0x7fb27f4f3a80)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1301072260)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:4223): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: A_TEAM
libdvdnav: DVD Serial Number: 3D375C1C
libdvdnav: DVD Title (Alternative): A_TEAM
libdvdnav: Unable to find map file '/home/jaques/.dvdnav/A_TEAM.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000689a2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00068d62
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00068e56
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0006d09a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002dbb6f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002dce4b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002ed391
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00317391
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
Warning: call to srand(283719)
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!



---

### Post by mc4man on 2011-03-25
> **mrpenguin said:**
> This is what I get from vlc in the terminal

This is from a store bought DVD movie
There is nothing remarkable about that title, no structure protection, ect.
Maybe try deleting any saved decryption keys and try again. (players always use saved keys if found even if they're no good
To do so put the dvd in the drive, close out any player that starts up ,if any.
Then in home folder delete the .dvdcss folder (hidden folder, crtl+h if you don't see any . files or folders in home
 Try vlc again.

Sometimes if there is RCE2 protection a region should be set on the drive, to ck. install regionset
Then _with a disk in the drive_ run regionset, if a region is not set then do so, (region 1 in your case I'd think), if it already is  then answer no and exit

Ex of a set drive (region 1
> doug@doug-alienware:~$ regionset /dev/sr0
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: [COLOR="Red"]SET[/COLOR]
vendor resets available: [COLOR="Red"]4[/COLOR]
user controlled changes resets available: 4
drive plays discs from region(s): [COLOR="Red"]1[/COLOR], mask=0xFE
Would you like to change the region setting of your drive? [y/n]: n


If you do set the region then again delete the .dvdcss folder before trying the disk again

---

### Post by mrpenguin on 2011-03-26
I deleted the dvdcss file but VLC still wont play the DVD

This is what i get from regionset

> jaques@jaques-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF


---

### Post by mrpenguin on 2011-03-26
Awesome, I got it working thanks :)

> jaques@jaques-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE


Does this mean I can only change the region 4 more times and then never again ??

Do I need to delete the dvdcss file everytime I want to watch a dvd ?

---

### Post by mc4man on 2011-03-26
> Does this mean I can only change the region 4 more times and then never again ??

Yes, but there is no reason you should need to change it. Linux (open source, non-licensed ) players don't enforce region coding, _just leave it as it is now._

> Do I need to delete the dvdcss file everytime I want to watch a dvd ? 
Generall speaking no, if a disk gives you trouble it's something you can always do as a trouble-shooting step
(as mentioned players (libdvdcss2) always look there first for a folder matching the volume label of the disk.
If found it will use what's inside even if corrupted, incorrect, ect.

---

### Post by mrpenguin on 2011-03-26
Thank you very much

---

### Post by srlake314 on 2011-04-05
I did all you said above, but before I could even get to the region part, I ran it to test it after all the terminal codes, and movie player froze.  It went grey, I had to force close.

arghhh....

---

