---
title: "No dvd play even with libdvdcss installed"
date: 2012-11-17
forum: Multimedia Software
---

### Post by chavodel8 on 2012-11-17
I've searched the web over. I've followed the "New Instructions" in the sticky thread at the top of this forum. I have the restricted extras installed. I have libdvdcss2 installed. I've installed libdvdnav4 and run the install_css script. I've tried everything I've been able to find, and I still can't play a dvd. Grrr.

Ubuntu 12.04, Unity UI, Gnome.

Totem: Gives me the classic "Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed." But libdvdcss2 is installed all right.

VLC: When I use "Open Disc" and select it, it outright crashes. I've tried using the default /dev/dvd as well as selecting the VIDEO_TS directory.

I'm outright frustrated and stumped. I've tried uninstalling libraries and reinstalling them to no avail. Anyone have any brilliant ideas out there?

Much thanks,
 -El Chavo

---

### Post by carl4926 on 2012-11-17
It's a fact that some dvd's just will not play.

You need to see if it affects all dvd's. If it does, then you have a problem with the installed codecs. I know you said you have libdvdcss, OK, can we assume you installed the restricted extras package?

On one machine I have I had to boot to windows to set the DVD region on the dvd drive, then dvd's worked.

---

### Post by monkeybrain2012 on 2012-11-17
Try vlc again and choose disc instead of /dev/dvd, try /dev/sr0 and see what happens

---

### Post by Yellow Pasque on 2012-11-17
> **chavodel8 said:**
> Anyone have any brilliant ideas out there?

Start VLC from the terminal to see why it crashes. ;-)

---

### Post by chavodel8 on 2012-11-17
Thank you for your responses!

Carl: I do have the restricted extras installed, yes. I've tried at least 4 different dvds if not more without luck.


MonkeyBrain: Tried with sr0, same result. Also, the following looks right to me.
$ls -l /dev/dvd
lrwxrwxrwx 1 root root 3 Nov 17 08:40 /dev/dvd -> sr0


Temujin: Good idea. Below is the output. It looks like it failed cracking some of the css keys, but in the end it just segfaults. I'm afraid I have little domain knowledge here and don't know what I should do with this information... if anything can be done.


$ vlc
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x117a108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 4498F0F1 (GEAR):
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/mparks/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000002d6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00037069
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0004eb6c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0004eb6c)!!
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fb8b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fbb13
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001fbcc8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x001fbcc8)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001fbd83
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001fbf50
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x001fbf50)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001fc00b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001fcab2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x001fcab2)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001fcb6d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x001fe797
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001fe852
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x001fe852)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x001fea16
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x001fea16)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x001fead1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0022b544
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x0022b544)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0022b6ba
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x0022b6ba)!!
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 4
No VTS_TMAPT available - skipping.
Segmentation fault (core dumped)
$

---

### Post by carl4926 on 2012-11-17
Did you check the region setting on your hardware? Do you even have windows?

I know this prol sounds crazy, but I have even had such DVD issues in the past and found k9copy will rip it! Totally crazy eh!

---

### Post by robbie 348 on 2012-11-17
In synaptic, make sure "non-free codecs" are installed.

---

### Post by chavodel8 on 2012-11-17
Robbie, I did not have those installed, but I do now and am still facing the same symptoms though.

Carl, I don't have a copy of Windows, and I'm in utter ignorance regarding your question "did [I] check the region setting on [my] hardware."

I have noticed that I don't have one library that I have seen mentioned, which is gstreamer0.10-plugins-ugly-multiverse. I do have gstreamer0.10-plugins-ugly, but the multiverse package does not seam to be available in the repo for 12.04, or perhaps I'm missing a source somewhere. I do have gstreamer0.10-plugins-bad-multiverse. Anyway, not sure if this could be related, but it seemed relevant.

Thank you still for your support and insights!
-El Chavo

---

### Post by pqwoerituytrueiwoq on 2012-11-17
did you run this:
sudo /usr/share/doc/libdvdread4/install-css.sh

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Yellow Pasque on 2012-11-17
Maybe you need to set the region on your drive?
```
sudo apt-get install regionset
sudo regionset
```

---

### Post by chavodel8 on 2012-11-17
psuperlongnameq - Yup, tried that.

Temujin - Getting closer I hope! I did that and set it to 1. It now prints the line below when I run regionset, which it did not do the first time.
```
drive plays discs from region(s): 1, mask=0xFE
```

**Totem** now gives me no error, but it doesn't really do anything. It spins up the disc, then nothing happens and the disc spins down again. And that's it.

**VLC** still crashes, but with different output now, as seen below. Perhaps I chose the wrong option? (I set it to 1 since I live in the U.S. and from what I've understood, that's the North America option. Or something like that.)

```

$ vlc
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x2456108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 4498F0F1 (GEAR):
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/mparks/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000002d6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00037069
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0004eb6c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fb8b5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fbb13
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001fbcc8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001fbd83
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001fbf50
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001fc00b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001fcab2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001fcb6d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x001fe797
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x001fe852
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x001fea16
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x001fead1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0022b544
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0022b6ba
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
No VTS_TMAPT available - skipping.
Segmentation fault (core dumped)

```

---

### Post by mc4man on 2012-11-17
You shouldn't need to run regionset as root (sudo
After installing regionset - to use
Put any disk in your drive, doesn't have to be a dvd
After the drive settles open a terminal & run
```
regionset
```

Look at line 4 of the result, if it says "Set"  then a region has been set, just exit out .with a n (line 5 will show region

EX.
```
doug@doug-XPS-M1330:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
[COLOR="Navy"]type: SET[/COLOR]
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n
```

If it hasn't been set then set to your region - 1 for N. America, 2 for Europe, ask if elsewhere

Edit - missed your post - do the below
**Then before trying a dvd again** open your home folder & delete the .dvdcss folder
(.dvdcss is a hidden folder, if you don't see any . files or folders go ctrl+h to expose

---

### Post by chavodel8 on 2012-11-17
YAY!!!!

Temujin and Mc4Man, THANK YOU!

Setting the region then deleting that .dvdcss folder worked! Totem now plays! I'm thrilled!

Interestingly, vlc still seg faults, but I'm not too worried about it. I'll verify that Totem will get through a whole film tonight, but it made it through the DVD menu and got the movie started. :popcorn:

Thank you so much for everyone's help!

---

### Post by mc4man on 2012-11-17
> **chavodel8 said:**
> 

Interestingly, vlc still seg faults, 
There may be some structure protection that is tripping up vlc
(didn't recognize the title from "DVD Serial Number: 4498F0F1 (GEAR):" & no Title: was shown

You could always try vlc in dvdsimple mode - see screen - No dvd menus option

---

