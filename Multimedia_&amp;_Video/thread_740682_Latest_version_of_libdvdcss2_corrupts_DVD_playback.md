---
title: "Latest version of libdvdcss2 corrupts DVD playback"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by haraldmilz on 2008-03-31
If I run:

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

I get DVD playback running just fine.

If I install the latest libdvdcss2 update which pops up shortly after running the install-css.sh script, DVD playback is corrupted.

I'd like to have my computer updated but I don't know why DVD playback is not possible after updating. Anyone know? Thanks!

---

### Post by warp99 on 2008-03-31
You can lock the package libdvdcss2 so it does not update with the following command:

```
echo "libdvdcss2 hold" | sudo dpkg --set-selections
```

Now every time you update it will skip over the libdvdcss2 package useless you do a dist-upgrade, You can also lock the package through the Synaptic package manager by highlighting the package then from the menu choose Package > Lock Version.

.

---

### Post by haraldmilz on 2008-03-31
Thanks. This solved the update issue. Would be nice to know why the new version of libdvdcss2 corrupts my DVD playback. Guess I'll just have to wait until they release another version...

---

### Post by forceofnature on 2008-03-31
I dont know why but this does not work for me.  I still can't play DVD's.

---

### Post by warp99 on 2008-03-31
> **forceofnature said:**
> I dont know why but this does not work for me.  I still can't play DVD's.

Do you have the previous version of libdvdcss2 installed? Can you play the dvd in any of the players (mplayer/totem/xine/vlc)? I would go through this guide first:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28libdvdcss2%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28libdvdcss2%29)

and see if you have taken all of the correct steps.

---

### Post by forceofnature on 2008-03-31
I just redid those instructions once again and nothing it just tells me it cant decode and am I trying to run without libdvdcss.

---

### Post by warp99 on 2008-03-31
Did you get the version libdvdcss2 from the medibuntu repositories?

---

### Post by forceofnature on 2008-03-31
sure did

---

### Post by warp99 on 2008-03-31
Let's reconfigure and purge the old package and try to re-install:

```
sudo apt-get remove --purge libdvdcss2 
```

then install again

```
sudo apt-get install libdvdcss2 
```

If that's not working try this:

```
sudo dpkg-reconfigure libdvdread3
```

and if the following does not work try this:

```
sudo apt-get install --reinstall libdvdcss2 libdvdread3 libdvdnav4 libdvbpsi4 libdvbpsi3
```

---

### Post by forceofnature on 2008-03-31
Actually I must have lost my mediabuntu repository this is what I got back this time from running the command.  Notice that medibundu is missing.

kevin@dell-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
--16:15:11--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/dvdcss-zV6617/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        94.53K/s             

16:15:11 (94.25 KB/s) - `/tmp/dvdcss-zV6617/libdvdcss.deb' saved [25178/25178]

(Reading database ... 119814 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using .../dvdcss-zV6617/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Ok now this time I got medibuntu  I think I see the issue.  It is going out to the wrong depository.  Shouldnt it go to  [http://packages.medibuntu.org/](http://packages.medibuntu.org/)  instead it it going to [www.dtek.chalmers.se](www.dtek.chalmers.se) unless that is medibuntu.  Anyway even after trying to correct it the same issues happen I keep getting my install from the [www.dtek.chalmers.de](www.dtek.chalmers.de) site  unless that is where it is supposed to come from.

Now I am just rambling I have been working on this since 8am.

---

### Post by forceofnature on 2008-03-31
> **warp99 said:**
> Let's reconfigure and purge the old package and try to re-install:

```
sudo apt-get remove --purge libdvdcss2 
```

then install again


```
sudo apt-get install libdvdcss2 
```

If that's not working try this:

```
sudo dpkg-reconfigure libdvdread3
```

and if the following does not work try this:

```
sudo apt-get install --reinstall libdvdcss2 libdvdread3 libdvdnav4 libdvbpsi4 libdvbpsi3
```


After all that I get the same errors.   

kevin@dell-desktop:~$ vlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2E3580ED
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/kevin/.dvdnav/DVD_VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000200
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000200)
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000035a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000035a0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001c0c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0001c0c0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001ac360
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x001ac360)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001ac380
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x001ac380)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001c1060
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x001c1060)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001c1080
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x001c1080)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001d8a60
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x001d8a60)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001d8a80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x001d8a80)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001e4d80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x001e4d80)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001e4da0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x001e4da0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00375c60
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x00375c60)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00375c80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x00375c80)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00375e20
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x00375e20)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00375e40
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x00375e40)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0037ccc0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x0037ccc0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0037cce0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x0037cce0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003924e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x003924e0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00392500
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x00392500)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003a5e80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_0.VOB (0x003a5e80)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003a5ea0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x003a5ea0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003b0160
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_0.VOB (0x003b0160)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003b0180
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x003b0180)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x003ba520
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_0.VOB (0x003ba520)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003ba540
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_1.VOB (0x003ba540)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x003c46c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_0.VOB (0x003c46c0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003c46e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_1.VOB (0x003c46e0)!!
libdvdread: Elapsed time 0
libdvdread: Found 13 VTS's
libdvdread: Elapsed time 7
[00000281] main playlist: nothing to play

---

### Post by forceofnature on 2008-03-31
The only thing I remember that I may have done to hose this up is mess around with gpsd and try to get my earthmate GPS to funtion but I gave up since I really didn't need a GPS on my laptop.

---

### Post by warp99 on 2008-03-31
If we remove version 1.2.9 of libdvdcss2:

```
sudo apt-get remove --purge libdvdcss2
```

then install version 1.2.5-1:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Does that work? 

Edit:

Because that was the problem the original post had.

---

### Post by forceofnature on 2008-03-31
No it doesn't :(


I wonder if loading the encryption key I needed for the GPS to work caused an issue.

---

### Post by warp99 on 2008-03-31
Well the last desperate act would be to do the following:

```
sudo apt-get remove --purge libdvdcss2 libdvdread3 libdvdnav4 libdvbpsi4 libdvbpsi3
```

Then install them again:

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 libdvbpsi4 libdvbpsi3
```

This will also remove **any media application** that is dependent on these libraries such as mplayer, xine, and VLC, but you can reinstall them as needed.

---

### Post by forceofnature on 2008-03-31
tried it and the only dvd that plays is a non encrypted DVD.

---

### Post by Prefix100 on 2008-03-31
[http://ubuntuforums.org/showthread.php?t=739636](http://ubuntuforums.org/showthread.php?t=739636)

---

### Post by forceofnature on 2008-04-01
I think my issue is due to GPSD and my trying to use the earthmate USB GPS.  I spoke with a coworker who had the same issues when trying to configure the earthmate GPS he ended up having to reload the OS.

I hate to reload the OS but if that is what it takes then so be it.

---

### Post by warp99 on 2008-04-01
Let's take a break and backtrack a little since it's not a critical issue that encrypted DVDs do not play. When you tried to install GPSD what were the steps you took? If you can list them and/or point to that thread then maybe we can solve this problem.

Edit:

Because I will replicate this on one of my systems if needed since this problem is messing with my knowledge base.

---

### Post by forceofnature on 2008-04-01
Ok let me find the right web site where I downloaded the pgp key and I will post it.  I basically followed their instructions but since I deleted my firefox history on sunday I dont have the site.  Thanks for trying to trouble shoot this with me.

Do you have a USB GPS antenna you can plug in?

---

### Post by mc4man on 2008-04-01
@ force while your waiting on warp if you give me the title name I'll confirm your if extracting at right addresses and finding proper keys

---

### Post by forceofnature on 2008-04-01
Ok first things first.  I searched for instructions to use the gps receiver antenna I had on hand the Delorme Earthmate LT-20 and found these general instructions.

Linux compatibility: Being a Linux user, I ignored the included copy of StreetAtlas 2006 and tried to get the GPS working with Linux. With a little fiddling, I discovered how to get it to work:

   1. Build the cypress_m8 kernel module and load it.
   2. Plug in the GPS.
   3. Check if /dev/ttyUSB0 exists. If it does not, run mknod /dev/ttyUSB0 c 188 0
   4. Run cat /dev/ttyUSB0 and check that you can see some NMEA sentences come in.
   5. Run gpsd -f /dev/ttyUSB0 -n.

I had read you need gpsd so first this I did was sudo apt-get install gpsd

Next I searched for cypress_m8 kernel. I found this site [http://www.gelato.unsw.edu.au/lxr/source/drivers/usb/serial/cypress_m8.c](http://www.gelato.unsw.edu.au/lxr/source/drivers/usb/serial/cypress_m8.c)

After looking at the code in there I knew I was in for some stuff I didn't know about.  I looked and found another site that had some information to download.  Any way from there I stumbeld across I site I cant seem to find anymore that had me load a GPG key in terminal to decrypt his file and the tried to set up the GPS.  It did not send data back I kept trying then gave up since then no DVD playback.

I wish I could find the repository and GPG thing I needed.  I will keep looking.

OOOHHH I found it for gpsdrive  [http://www.gpsdrive.de/download.shtml](http://www.gpsdrive.de/download.shtml)

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.1 (GNU/Linux)

mQGiBENYwLARBACdOiX87kq/aAPsAsXy/jU51mN4Ed6AVHVy6Wx/Epm6pA2IEYnO
Zqlsu5ZacnTvNn/gWZYIGPZakmOzjyAHMbcBFkL5vg1oTulyvsLIhflIZHy6Pxek
/Yps/forduCqjj5LhojKnLmOdMy8Ke07M/x4p1IHaq3AR64tgYXNRKYFRwCg745w
mM19QOBGMWYrJAd2skKjxHUD/1IlvxIq6gTjiUR/p7qiRbC7Gn8oJJEJKEyIOY1f
XQC9YzYFmLa4HQ7VJHxuOUfw1WnfZwk5TNs64LAPtaJQ8Wm6W7tGX09X426Xq8x/
R/Im6KlieLuaAYpgRq+93TfO9mnoKyEqTW6TaAJafNn9Mbw+lC6KHBfnUK7jaUdp
WZwLA/96BD4k9jqaS9ClZbN55tr/XJPkYQoxcROcp0lMVggeq/9Hn0wX5uCXdGxe
z+9okGuK1nWbCr6K9xtCedj8R6OeSw/hr0SgD96eML6z1F2mBRWEJEtJyHVWOt/W
V6tAIDIeI9wgSN70l1N6rk/CPg0g9fiEcLetFLQehXDtZ8yRJLQ3Sm9lcmcgT3N0
ZXJ0YWcgKERlYmlhbiBQYWNrYWdlcykgPGRlYmlhbkBvc3RlcnRhZy5uYW1lPohe
BBMRAgAeBQJDWMCwAhsDBgsJCAcDAgMVAgMDFgIBAh4BAheAAAoJEDqDVSAiEJYw
TMEAnA3HOQrAoVPtVRKtFbzkFeczXItCAKCfmFmtcFyD9xL/GUcGU2/HIGlGdLkC
DQRDWMC5EAgAzJwypwb9JJUVyTRoA2N4MDYqFXkvl71IwomzMEQugNUTM6SabZz+
Viz2E45POHtDwfPjo4bnXUTmdeYw5ewKZrgU234qBGXehGAq6aAdiQczP8fkqlKk
okmqoVYyOqgX3vfB9sS7g8kWXhvzZI+xG9RA8xFnd0f52L9evoj0YTNk2rN9xj4k
qq1LxysGOgrNcbF1M/6RDbG0SbW6C7PahlRd5isDEsf8/sPkiCtHprNUyJjww76V
Q16YyWIstJune6eTyctdQS/RdOKSA/8ROTrEXwsrPel9thywzkIgUcRYdOWgQzMr
giq6YsBTzps2FFFYMcCLcxLqEqOwScwGOwADBgf+OTCdCmDHdltr2ky9ZGL5ujEZ
aBK+1c0NPWZOKpCVe/9qZr9hcATZyOa80fUr1PMCRn6QQ0cGc9Bpyfd1xJR4/dAZ
YADLZWX5IN4n3Wp70SquYfOohCGONOYxkZTvZ75C3eKE+xZJ2S0Tw95Ww3MLO6Js
e4JHbwBuwL4GviXzIZN80vZAztBfmhi9pGaVkbrI9hGRhCxhhfK1B2jJ9k5YPFDP
tp2y+9P/HMm1XgAk9DWaclQknI2gFTVntdymmXjeAy7K2QSF9arGgFkvL2usjfAV
KUTtniB4D04bOzY+cvasLdh7MQbp/Io8c3ZH0h+EyZfvrNY3SZZWQtAeXQw2dohJ
BBgRAgAJBQJDWMC5AhsMAAoJEDqDVSAiEJYwWpQAoKz8rlABRnSYFx7k6bBzwHej
WAn+AKCNwULHgAEWer/BwRzOvTfoEt67Kg==
=TQNn
-----END PGP PUBLIC KEY BLOCK-----

---

### Post by forceofnature on 2008-04-01
> **mc4man said:**
> @ force while your waiting on warp if you give me the title name I'll confirm your if extracting at right addresses and finding proper keys

Are you talking about the DVD title if so I tried "I SPY" and "Spiderman 2"

---

### Post by mc4man on 2008-04-01
Unfortunately i have the superbit version of spiderman2 - won't help. In lieu of any other solutions and before doing a fresh install (which will solve your issue if done right as far as dvd playback) if you want to pursue this angle let me know and I'll borrow the proper ver. Maybe 2 hrs. from now
The gist is vlc is able to parse the disk, it's just not getting the proper keys or somehow can't access them for playback - it will be easy to cross compare
let me know

---

### Post by forceofnature on 2008-04-01
Thanks That would be nice of you.  I don't want to reinstall the OS since I got it all set up for my liking.  If I have to I will.

---

### Post by mc4man on 2008-04-01
D... I borrowed it from friend but different edition - so you can see why of no use 
```
LC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread patched to play DVDs with DVD-Movie-Protect
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 311B7B6A
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/doug/.dvdnav/DVD_VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000200
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000017a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00012a90
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002df400
libdvdread: Elapsed time 0  ........  
```
ck. back in awhile I'll see about I spy

Edit: got any other titles that won't play - I have alot - if not I'll borrow I spy

---

### Post by forceofnature on 2008-04-01
Here is what I get with the Matrix

VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: THE_MATRIX_16X9LB_N_AMERICA
libdvdnav: DVD Serial Number: 27028BAA
libdvdnav: DVD Title (Alternative): THE_MATRIX_16X9LB_N_AMERICA
libdvdnav: Unable to find map file '/home/kevin/.dvdnav/THE_MATRIX_16X9LB_N_AMERICA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)

---

### Post by mc4man on 2008-04-01
Lets look at I spy !st. go into .dvdcss and find folder dvd_video 2003012116072600-73f097e32c and open these 3 files (if you can't find that folder let me know)
0000000200
00000035a0
000001c0c0
what I want is what's inside - if nothing post back, if there is a key _pm_ me with them. Do it so I know file and key - 0000000200 - xxxxxxxxxx
I 'm not sure of the advisability of posting keys so pm is better

---

### Post by forceofnature on 2008-04-01
Nothing in the folder.

---

### Post by mc4man on 2008-04-01
ck. pm

---

### Post by warp99 on 2008-04-02
I looked at the information you posted for overwritten libraries and some other issues but found nothing that would affect either libdvdread3 or libdvdcss2.

Let's check a few more things.  See if the libdvdread3 and libdvdcss2 libraries have the proper symlinks:

```
:/usr/lib$ ls -l libdvdread*
lrwxrwxrwx 1 root root     19 2008-03-31 15:31 libdvdread.so.3 -> libdvdread.so.3.2.1
-rw-r--r-- 1 root root 118432 2007-05-01 19:47 libdvdread.so.3.2.1

```

```
/usr/lib$ ls -l libdvdcss*
lrwxrwxrwx 1 root root    18 2008-03-31 15:31 libdvdcss.so.2 -> libdvdcss.so.2.0.8
-rw-r--r-- 1 root root 35496 2007-09-25 15:01 libdvdcss.so.2.0.8

```

If that checks out normal, then try to decode the DVDs with mplayer running as root:

```
sudo mplayer dvd://
```

You may have to export the variable DVDCSS_METHOD=title with libdvdcss2 if the dvd decodes running as root.

```
:/

Running lidvdcss
================

The behaviourof the library can be affected by changing two environment
variables:
  DVDCSS_METHOD={title|disc|key}: method for key decryption
    title: decrypted title key is guessed from the encrypted sectors of
           the stream. Thus it should work with a file as well as the
           DVD device. But it sometimes takes much time to decrypt a title
           key and may even fail. With this method, the key is only checked
           at the beginning of each title, so it won't work if the key
           changes in the middle of a title.
    disc: the disc key is first cracked ; then all title keys can be
           decrypted instantly, which allows us to check them often,
    key: the same as "disc" if you don't have a file with player keys at
           compilation time. If you do, the decryption of the disc key
           will be faster with this method. It is the one that was used by
           libcss.
           This is the default method,
  DVDCSS_VERBOSE={0|1|2}: libdvdcss verbosity
    0: no error messages, no debug messages (this is the default)
    1: only error messages
    2: error and debug messages

```

and finally it may be that somehow the region code on your drive is not set according to this bug:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/162485](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/162485)

If you notice the failure error is the same:

```
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
```

You can reset the region code with regionset available in the universe repositories:

```
sudo apt-get regionset
```

Another thread had the exact problem until the region code was reset:

[http://tennessee.ubuntuforums.com/showthread.php?t=609772&page=1](http://tennessee.ubuntuforums.com/showthread.php?t=609772&page=1)

notice the same error:

```
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.[
```

---

### Post by forceofnature on 2008-04-02
I can run the DVD in sudo command like you said.  Why is that?  Here is the code I got back

kevin@dell-desktop:~$ sudo mplayer dvd://
MPlayer 2:1.0~rc1-0ubuntu13.2+medibuntu1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 35 titles on this DVD.
There are 38 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Invalid title IFO (VTS_02_0.IFO).
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: ac3 (stereo) language: en aid: 130.
number of audio channels on disk: 3.
subtitle ( sid ): 0 language: en
number of subtitles on disk: 1
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
A:   0.5 V:   0.5 A-V:  0.013 ct:  0.016  15/ 12 ??% ??% ??,?% 4 0 
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.

---

### Post by forceofnature on 2008-04-02
So far it only works with mplayer with root or sudo command.  Kinda weird.  I did set region before this issue and once again since issue.  

About you commands in the first part of you message I get nothing,  unless I am doing it wrong.

---

### Post by warp99 on 2008-04-02
Try the export command, then run as a regular user:

```
export DVDCSS_METHOD=title && mplayer dvd://
```

See if that works.

Edit:

Export just sets the variable for the environment. It doesn't do anything else.

---

### Post by forceofnature on 2008-04-02
I dont know if this really matters but I have an SSD hard drive.

---

### Post by forceofnature on 2008-04-02
Holy !@#@ I think that worked.  I owe u a beer coffee or soda.  I will try some other DVDs.  The Matrix is working now!!

---

### Post by forceofnature on 2008-04-02
Spiderman 2 working also so I think it is safe to say its back in order.  For some reason Totem is the default even though I entered in the preferences for VLC.  I don't think this matters since totem is playing the dvds just fine.

---

### Post by warp99 on 2008-04-02
Now we need to set the variable DVDCSS_METHOD=title so that it will always be available because right now when you reboot the variable goes away. So do the following:

```
echo "export DVDCSS_METHOD=title" >> ~/.bashrc
```

If that does not work when you reboot then we need to set the variable system wide:

```
echo "export DVDCSS_METHOD=title" | sudo tee -a /etc/bash.bashrc
```

And yes I'll take a Heineken or Becks if you don't mind. :lolflag:

---

### Post by forceofnature on 2008-04-02
Oh yeah it works.  The first command seemed to do it.  :guitar:

---

### Post by photismos on 2008-04-28
> **forceofnature said:**
> Oh yeah it works.  The first command seemed to do it.  :guitar:

pardon my frustration, but how dumb & inconsiderate to be so vague... what "first command"???  can't you be more specific???!!!  egad!!!  

this one worked for me... kick a$$ and thank you very much  brainiacs!!!!!! Love you guys!!!  

sudo mplayer dvd://

---

