---
title: "libdvdcss etc...."
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by apollo13 on 2007-03-05
Hi there,

I have got a little problem with libdvdcss and my new laptop. (It is installed correctly, at least I hope so, but the necessary files are where they should be)
First I got encryption errors, but setting the region to Europe (instead of 0) helped.
Now I can't watch the film cause xine is telling me that it seems as if libdvdcss is not installed :( (Same Problems for other players, but xine is telling me nearly the same as totem....)

Device is /dev/scd0 and funny or not, hdparm isn't working either....
Any ideas?

Thanks apollo13

---

### Post by apollo13 on 2007-03-06
Push, I really need help :(
Don't tell me to use Wind00$

---

### Post by floke on 2007-03-06
I got mine from medibuntu.sos-sts.com

Usual disclaimers about 3rd party repos apply.

---

### Post by apollo13 on 2007-03-06
Hmm, didn't help either:
```
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000271
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00007cdc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003345d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00279003
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00279008
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e0947
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e094c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003705b1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003705b6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00374e82
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00374e87
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00374f29
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00374f2e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0038df2a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0038df2f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0038fc97
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0038fc9c
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0

```

And then xine tells me: libdvdcss not found :(

P.S.: If it does not work in Feisty I will try Debian :icon_frown:

---

### Post by floke on 2007-03-06
This works for me.
You could also try this - just saw it.

[http://ubuntuforums.org/showthread.php?t=377784](http://ubuntuforums.org/showthread.php?t=377784)

** EDIT ** this is rubbish - try using VLC instead - sudo apt-get install vlc

---

### Post by panch0 on 2007-03-07
Or MPlayer/KPlayer, there's Feisty packages out there. Never had a DVD decryption problem in KPlayer.

---

### Post by floke on 2007-03-07
Yeah, I tried Mplayer and Totem and both were chucking up codec errors, even with the libdvdcss2 - VLC was the only one that pulled it off for me.

---

### Post by panch0 on 2007-03-07
Please post the MPlayer output.

---

### Post by apollo13 on 2007-03-07
Neither vlc nor mplayer, totem etc... helped

vlc didn't wrote anything to stdout, seemed to play the dvd, but without the movie, sound only and it seemed as dma was not enabled (hdparm does not work, so no idea how to check it...)

mplayer, hmmm don't have a dvd here to try now, everyone else in the house is sleeping ;)

---

### Post by panch0 on 2007-03-09
Have you had a chance to try with MPlayer? If it still doesn't work, post the output.

---

### Post by apollo13 on 2007-03-10
The full log is located here:
[http://media.apolloner.eu/stuff/log.txt](http://media.apolloner.eu/stuff/log.txt)

2000+ lines :)

Thx, apollo13

---

### Post by nero_86 on 2007-03-10
I think is a libdvdcss problem... Have tou tried to reinstall libdvdread and then 

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

to reinstall libdvdcss? Is the simplest thing but maybe...

---

### Post by apollo13 on 2007-03-10
Wtf, I am using edgy so install-css.sh was not in the subfolder examples, but one level higher.
The funny thing is that the dvd now works in vlc and mplayer, but still does not work in xine and totem^^

Thx, apollo13

P.S.: I don't now how often I installed libdvdcss yet using this script, but this time I purged the installed version reinstalled every libdvd* package and even installed -dev packages (although I don't think the -dev were the reason...)

---

