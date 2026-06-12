---
title: "Can't read copyrighted DVD's on ubuntu 14.04"
date: 2015-01-18
forum: Multimedia Software
---

### Post by Laura_Nbl on 2015-01-18
Hi :) 
I am unable to play DVD's on my laptop, even though I downloaded libdvdccs2 and restricted extras.
It will just show the title of the dvd for a split second when I open VLC, but it wont play.
I have read about this problem for hours, but the only answer I found was to install libdvdccs2 and then it will work.... well, it doesn't.
Also, I am a noob, so I can't post any feedback from the terminal, I don't even know what most of the codes mean :). 
Anyway, thank you for helping!

---

### Post by bytr on 2015-01-18
Please try to run the following commands in the terminal:
```
sudo apt-add-repository 'deb http://download.videolan.org/pub/debian/stable/ /' && wget -O - http://download.videolan.org/pub/debian/videolan-apt.asc | sudo apt-key add -
sudo apt-get update
sudo apt-get install libdvdcss2

```

---

### Post by ajgreeny on 2015-01-18
Have a read through the info at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) which shows how to get DVDs playing without the need to add the videolan repository and do it manually.

The package libdvdread4 now includes a script that downloads and installs libdvdcss2 for you.

---

### Post by Laura_Nbl on 2015-01-18
Thank you for your answers, but aren't you just telling me to re-install the libdvdcss2 file again?
I have downloaded the libdvdread4, libdvdnav4 and libdvdcss2. I have also installed restricted extras and checked the region code, nothing is working.

---

### Post by SeijiSensei on 2015-01-18
Is this true for all your DVDs, or just certain ones?  If the latter, which?

---

### Post by mc4man on 2015-01-18
You could try this - 
Insert a dvd, close any player or prompt pop up.
Open your home folder > delete the .dvdcss folder (go ctrl+h if . (hidden) files aren't seen

Then open a terminal & run this - 
```
export DVDCSS_METHOD=title && export DVDCSS_VERBOSE=2
```
followed by this in *same terminal *  (- assumes dvd is in your default dvd drive - 
```
vlc dvd://  > vlc_output.log 2>&1
```
Post the contents of the log which will be in your home folder.

Note: if using some other drive & above vlc command fails then instead go (using same terminal the export commands were run in,  - 
```
vlc  > vlc_output.log 2>&1
```
Then in vlc > Media > Open Disc > ect.

Also please show the results of this, the  *-cdrom section(s)
```
sudo lshw -C disk
```

---

### Post by Laura_Nbl on 2015-01-19
Thank you for your help, I believe this is the log?  [0x2518118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface. libdvdnav: Using dvdnav version 4.2.1 libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss debug: disc reports copyright information 0x1 libdvdcss debug: drive region mask 0xff, RPC-II, no region code set libdvdcss error: css error: drive will prevent access to scrambled data libdvdcss debug: scrambled disc on a region-free RPC-II drive: possible failure, but continuing anyway libdvdcss debug: requesting AGID libdvdcss debug: drive authenticated, using variant 0 libdvdcss debug: authentication established libdvdcss debug: GetASF authenticated, ASF=1 libdvdcss debug: disc key needs not be decrypted libdvdcss debug: using CSS key cache dir: /home/laura/.dvdcss/CAPTAIN_AMERICA-2011091611593400-0000000000/ libdvdnav: DVD Title: CAPTAIN_AMERICA libdvdnav: DVD Serial Number: 3F305ED1 libdvdnav: DVD Title (Alternative): CAPTAIN_AMERICA libdvdnav: Unable to find map file '/home/laura/.dvdnav/CAPTAIN_AMERICA.map' libdvdnav: DVD disk reports itself with Region mask 0x00ed0000. Regions: 2 5  libdvdread: Attempting to retrieve all CSS keys libdvdread: This can take a _long_ time, please be patient  libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001b5 libdvdcss debug: cracking title key at block 437 libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2000 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 2 libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000012d4 libdvdcss debug: cracking title key at block 4820 libdvdcss error: read error libdvdcss debug: read error at block 4820, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000012d4) libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00001814 libdvdcss debug: cracking title key at block 6164 libdvdcss error: read error libdvdcss debug: read error at block 6164, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00001814)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00001836 libdvdcss debug: cracking title key at block 6198 libdvdcss error: read error libdvdcss debug: read error at block 6200, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000018b9 libdvdcss debug: cracking title key at block 6329 libdvdcss error: read error libdvdcss debug: read error at block 6330, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000019e2 libdvdcss debug: cracking title key at block 6626 libdvdcss error: read error libdvdcss debug: read error at block 6626, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x000019e2)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000019e2 libdvdcss debug: cracking title key at block 6626 libdvdcss error: read error libdvdcss debug: read error at block 6626, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x000019e2)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000019e2 libdvdcss debug: cracking title key at block 6626 libdvdcss error: read error libdvdcss debug: read error at block 6626, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x000019e2)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000019e2 libdvdcss debug: cracking title key at block 6626 libdvdcss error: read error libdvdcss debug: read error at block 6626, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x000019e2)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00041a35 libdvdcss debug: cracking title key at block 268853 libdvdcss error: read error libdvdcss debug: read error at block 268854, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 1 libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00041a35 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00041a35 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00041a35 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0004da59 libdvdcss debug: cracking title key at block 318041 libdvdcss error: read error libdvdcss debug: read error at block 318042, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0004da59 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0004da59 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x00054b09 libdvdcss debug: cracking title key at block 346889 libdvdcss error: read error libdvdcss debug: read error at block 346890, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x0005c4d7 libdvdcss debug: cracking title key at block 378071 libdvdcss error: read error libdvdcss debug: read error at block 378072, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x00054b09 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x0005c4d7 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x00054b09 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x0005c4d7 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x00381c6c libdvdcss debug: cracking title key at block 3677292 libdvdcss error: read error libdvdcss debug: read error at block 3677294, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003843c6 libdvdcss debug: cracking title key at block 3687366 libdvdcss error: read error libdvdcss debug: read error at block 3687368, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Found 17 VTS's libdvdread: Elapsed time 3 [0x7f6c740009b8] main input error: ES_OUT_RESET_PCR called [0x7f6c740009b8] main input error: ES_OUT_RESET_PCR called libdvdcss error: read error libdvdcss error: read error [0x7f6c740009b8] main input error: ES_OUT_RESET_PCR called [0x7f6c740009b8] main input error: ES_OUT_RESET_PCR called libdvdcss debug: cracking title key at block 6164 libdvdcss error: read error libdvdcss debug: read error at block 6164, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdcss error: read error

---

### Post by Laura_Nbl on 2015-01-19
Eish, it doesn't look as fancy as when you guys post codes. :)  Also, I can play DVD's with no copyright.

---

### Post by lisati on 2015-01-19
> **Laura_Nbl said:**
> Eish, it doesn't look as fancy as when you guys post codes. :) 
Pasting the information between [noparse]```
 and 
```[/noparse] usually does the trick.

---

### Post by Laura_Nbl on 2015-01-19
Ok, but it's all in one line now.  ```
 [0x2518118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface. libdvdnav: Using dvdnav version 4.2.1 libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss debug: disc reports copyright information 0x1 libdvdcss debug: drive region mask 0xff, RPC-II, no region code set libdvdcss error: css error: drive will prevent access to scrambled data libdvdcss debug: scrambled disc on a region-free RPC-II drive: possible failure, but continuing anyway libdvdcss debug: requesting AGID libdvdcss debug: drive authenticated, using variant 0 libdvdcss debug: authentication established libdvdcss debug: GetASF authenticated, ASF=1 libdvdcss debug: disc key needs not be decrypted libdvdcss debug: using CSS key cache dir: /home/laura/.dvdcss/CAPTAIN_AMERICA-2011091611593400-0000000000/ libdvdnav: DVD Title: CAPTAIN_AMERICA libdvdnav: DVD Serial Number: 3F305ED1 libdvdnav: DVD Title (Alternative): CAPTAIN_AMERICA libdvdnav: Unable to find map file '/home/laura/.dvdnav/CAPTAIN_AMERICA.map' libdvdnav: DVD disk reports itself with Region mask 0x00ed0000. Regions: 2 5  libdvdread: Attempting to retrieve all CSS keys libdvdread: This can take a _long_ time, please be patient  libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001b5 libdvdcss debug: cracking title key at block 437 libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2000 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 2 libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000012d4 libdvdcss debug: cracking title key at block 4820 libdvdcss error: read error libdvdcss debug: read error at block 4820, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000012d4) libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00001814 libdvdcss debug: cracking title key at block 6164 libdvdcss error: read error libdvdcss debug: read error at block 6164, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00001814)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00001836 libdvdcss debug: cracking title key at block 6198 libdvdcss error: read error libdvdcss debug: read error at block 6200, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000018b9 libdvdcss debug: cracking title key at block 6329 libdvdcss error: read error libdvdcss debug: read error at block 6330, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000019e2 libdvdcss debug: cracking title key at block 6626 libdvdcss error: read error libdvdcss debug: read error at block 6626, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x000019e2)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000019e2 libdvdcss debug: cracking title key at block 6626 libdvdcss error: read error libdvdcss debug: read error at block 6626, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x000019e2)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000019e2 libdvdcss debug: cracking title key at block 6626 libdvdcss error: read error libdvdcss debug: read error at block 6626, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x000019e2)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000019e2 libdvdcss debug: cracking title key at block 6626 libdvdcss error: read error libdvdcss debug: read error at block 6626, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x000019e2)!! libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00041a35 libdvdcss debug: cracking title key at block 268853 libdvdcss error: read error libdvdcss debug: read error at block 268854, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 1 libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00041a35 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00041a35 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00041a35 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0004da59 libdvdcss debug: cracking title key at block 318041 libdvdcss error: read error libdvdcss debug: read error at block 318042, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0004da59 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0004da59 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x00054b09 libdvdcss debug: cracking title key at block 346889 libdvdcss error: read error libdvdcss debug: read error at block 346890, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x0005c4d7 libdvdcss debug: cracking title key at block 378071 libdvdcss error: read error libdvdcss debug: read error at block 378072, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/1 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x00054b09 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x0005c4d7 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x00054b09 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x0005c4d7 libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x00381c6c libdvdcss debug: cracking title key at block 3677292 libdvdcss error: read error libdvdcss debug: read error at block 3677294, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x003843c6 libdvdcss debug: cracking title key at block 3687366 libdvdcss error: read error libdvdcss debug: read error at block 3687368, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/2 libdvdcss debug: no scrambled sectors found libdvdcss debug: title key is 00:00:00:00:00 libdvdcss debug: unencrypted title libdvdread: Elapsed time 0 libdvdread: Found 17 VTS's libdvdread: Elapsed time 3 [0x7f6c740009b8] main input error: ES_OUT_RESET_PCR called [0x7f6c740009b8] main input error: ES_OUT_RESET_PCR called libdvdcss error: read error libdvdcss error: read error [0x7f6c740009b8] main input error: ES_OUT_RESET_PCR called [0x7f6c740009b8] main input error: ES_OUT_RESET_PCR called libdvdcss debug: cracking title key at block 6164 libdvdcss error: read error libdvdcss debug: read error at block 6164, resorting to secret arcanes to recover libdvdcss debug: opening target `/dev/sr0' libdvdcss debug: using libc for access libdvdcss error: read error libdvdcss debug: end of title reached libdvdcss debug: successful attempts 0/0, scrambled blocks 0/0 libdvdcss debug: title key is 00:00:00:00:00 libdvdcss error: fatal error in VTS CSS key libdvdcss error: read error 
```

---

### Post by mc4man on 2015-01-19
Well that posted log is a mess - somehow you got it on one line. 
(if there is a next time then put it in **quote **box or just compress log to a .gz & attach as a file.

Anyway what stands out is it seems to report that  no region is set - 
> libdvdcss debug: drive region mask 0xff, RPC-II, no region code set
libdvdcss error: css error: drive will prevent access to scrambled data 
libdvdcss debug: scrambled disc on a region-free RPC-II drive: possible failure, but continuing anyway
....

Put a cd or dvd in the drive & run 
```
regionset /dev/sr0

```
Post results in a quote box. Example here where region is set to 1 (N. America
> .$ regionset /dev/sr0
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n



Edit: your disk in log was a region 2, are you in Europe?

---

### Post by mc4man on 2015-01-19
Plus would still be useful to see as previously asked - 
> Also please show the results of this, the *-cdrom section(s)


```
sudo lshw -C disk
```


---

### Post by Laura_Nbl on 2015-01-19
Ok, sorry about the messed up code :). Here is the one for the DVD drive.
```
laura@laura-Aspire-E5-511:~$ sudo lshw -C disk
[sudo] password for laura: 
  *-disk                  
       description: ATA Disk
       product: ST500LT012-1DG14
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0001
       serial: W3P5XW9M
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=4096 signature=000442c7
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ8E2Q
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       logical name: /media/laura/CAPTAIN_AMERICA
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/laura/CAPTAIN_AMERICA
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       size: 57GiB (61GB)
       capabilities: partitioned partitioned:dos
       configuration: sectorsize=512 signature=8a3479cf
laura@laura-Aspire-E5-511:~$ 


```

---

### Post by Laura_Nbl on 2015-01-19
And here is the region code one.
My Laptop came from germany, but I live in south africa.

```
laura@laura-Aspire-E5-511:~$ regionset /dev/sr0
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:^C
laura@laura-Aspire-E5-511:~$ 

```

---

### Post by mc4man on 2015-01-19
> product: DVD-RAM UJ8E2Q
       vendor: MATSHITA

A matshita dvd drive will - 
1.  only allow access to a commercial css encrypted disk when a region is set on the drive
2. will only allow access to dvd's from the same region as the drive is set to. There is no workaround for this.

So for example if the drive is set to region 2 (Europe) then you'll only be able to play region 2 disks, any dvd's from other regions will not work.
Seeing as there are only 5 'sets' allowed on a drive before it's locked it's not possible to keep switching regions so -

Set the drive to whatever region you are in or whatever region you'll have the most dvd's from using regionset.

Edit: after setting region best to delete the .dvdcss folder before trying playback again

---

### Post by Laura_Nbl on 2015-01-19
Yesssss! It worked! You are awesome, and deserve a virtual cookie. Is there any way to 'like' on this page?

---

### Post by SeijiSensei on 2015-01-19
Just a warning that many DVD drives have a limit on the number of times you can change their region coding.  I think five is a common maximum.

---

