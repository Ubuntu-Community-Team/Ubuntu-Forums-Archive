---
title: "Play DVD **codecs** Ubuntu 9.10"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Cuansf on 2009-11-19
Hello I'm trying to watch DVDs in my computer with VLC and after install everything about codecs, medibuntu and all those things I cannot play the DVD because there's something that doesn't work properly because the VLC close down suddenly.

Can anybody help me with this trouble? I hope so!!

Thank you very much for your attention.

Bye!

---

### Post by ilil on 2009-11-19
Please read [Here](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by wojox on 2009-11-19
And here [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Cuansf on 2009-11-19
Thank you, i'll read that and I'll tell you later.

---

### Post by andrew.46 on 2009-11-19
Hi Cuansf,

> **Cuansf said:**
> Hello I'm trying to watch DVDs in my computer with VLC and after install everything about codecs, medibuntu and all those things I cannot play the DVD because there's something that doesn't work properly because the VLC close down suddenly.

Could you attempt to play the DVD via the vlc commandline and report the terminal output here? The syntax is:
```

cvlc -v dvd://
```

This should give a few hints about any video out problems, dvd decryption problems etc.

All the best,

Andrew

---

### Post by Cuansf on 2009-11-20
> **andrew.46 said:**
> Hi Cuansf,



Could you attempt to play the DVD via the vlc commandline and report the terminal output here? The syntax is:
```

cvlc -v dvd://
```This should give a few hints about any video out problems, dvd decryption problems etc.

All the best,

Andrew


Hi Andrew,

this is what appears when I did that:

VLC media player 1.0.2 Goldeneye
[0x93e9e40] main demux warning: no access_demux module matching "file" could be loaded
[0x93fbe38] main interface error: no interface module matched "globalhotkeys,none"
[0x93fbe38] main interface error: no suitable interface module
[0x934f140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x93fbe80] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: LO20EUF1
libdvdnav: DVD Serial Number: 34fb492d
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/cuansf/.dvdnav/LO20EUF1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000191
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000026b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000031e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000031e)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00014b1d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00014cc9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00014e70
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x00014e70)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00014f23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000154ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00015560
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x00015560)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0001661a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x0001661a)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000166cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0009936f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00099422
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x00099422)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00176256
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x00176256)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00176309
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00188d70
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x00188d70)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00188e23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x00197b80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x00197b80)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00197c33
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x001e716a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_0.VOB (0x001e716a)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x001e721d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x001f7df1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x001f7ea4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x001f7ea4)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x001fbfa5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x001fc058
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_1.VOB (0x001fc058)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x002056a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00205756
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_1.VOB (0x00205756)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x0021fcca
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_14_0.VOB (0x0021fcca)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x0021fd7d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x0024a39e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_15_0.VOB (0x0024a39e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x0024a451
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x0028b2fc
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_16_0.VOB (0x0028b2fc)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x0028b3af
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x002bae7f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x002baf32
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_17_1.VOB (0x002baf32)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x002bb021
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x002bb0d4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_18_1.VOB (0x002bb0d4)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_0.VOB at 0x00324f06
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_19_0.VOB (0x00324f06)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x00324fb9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_0.VOB at 0x00359cee
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_20_0.VOB (0x00359cee)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x00359da1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_0.VOB at 0x00360c70
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_21_0.VOB (0x00360c70)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x00360d23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_0.VOB at 0x00367bd2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_22_0.VOB (0x00367bd2)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_1.VOB at 0x00367c85
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_0.VOB at 0x0036ec03
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_1.VOB at 0x0036ecb6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_23_1.VOB (0x0036ecb6)!!
libdvdread: Elapsed time 0
libdvdread: Found 23 VTS's
libdvdread: Elapsed time 3

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
[0xb7400648] main input error: ES_OUT_RESET_PCR called
[0xb7400648] main input error: ES_OUT_RESET_PCR called
[0x93fdd78] dvdnav demux warning: cannot get next block (Error reading NAV packet.)


THANK YOU VERY MUCH FOR YOUR HELP!!!

Cuansf

---

### Post by mc4man on 2009-11-20
A few things to try

First go into home folder and delete the .dvdcss folder ( a hidden  folder, view -> show hidden files if need be.

Then go ahead and try vlc again as you normally would.

If no good, close vlc, then again **delete the .dvdcss folder** and open a terminal.

run these 2 commands, (will set up libdvdcss2 debugging and use a different key cracking method

```
export DVDCSS_VERBOSE=2
```
followed by

```
export DVDCSS_METHOD=title && vlc dvd:// > vlc_output.log 2>&1
```

If still no good look in home folder for vlc_output.log and post the contents.

Also at this point maybe ck. that a region has been set on the drive ( only needs to be set **once**

To do so install regionset
```
sudo apt-get install regionset
```

And with a dvd in the drive run in terminal 
regionset

Look on line 4, if it says None then answer y and set to your region ( 2 is Europe, 4 is Australia, if unsure ck. 1st.
If line 4 says Set then answer n and exit.

If there was no region set than after doing again delete .dvdcss and try again.



just in case you need to set region

1 = North America (USA and Canada)
2 = Europe, Middle East, South Africa and Japan
3 = Southeast Asia, Taiwan, Korea
4 = Latin America, Australia, New Zealand
5 = Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
6 = China

---

### Post by Cuansf on 2009-11-20
> **mc4man said:**
> A few things to try

First go into home folder and delete the .dvdcss folder ( a hidden  folder, view -> show hidden files if need be.

Then go ahead and try vlc again as you normally would.

If no good, close vlc, then again **delete the .dvdcss folder** and open a terminal.

run these 2 commands, (will set up libdvdcss2 debugging and use a different key cracking method

```
export DVDCSS_VERBOSE=2
```followed by

```
export DVDCSS_METHOD=title && vlc dvd:// > vlc_output.log 2>&1
```If still no good look in home folder for vlc_output.log and post the contents.

Also at this point maybe ck. that a region has been set on the drive ( only needs to be set **once**

To do so install regionset
```
sudo apt-get install regionset
```And with a dvd in the drive run in terminal 
regionset

Look on line 4, if it says None then answer y and set to your region ( 2 is Europe, 4 is Australia, if unsure ck. 1st.
If line 4 says Set then answer n and exit.

If there was no region set than after doing again delete .dvdcss and try again.



just in case you need to set region

1 = North America (USA and Canada)
2 = Europe, Middle East, South Africa and Japan
3 = Southeast Asia, Taiwan, Korea
4 = Latin America, Australia, New Zealand
5 = Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
6 = China

Hello mc4man, I've tried all those that you told me before but nothing happened. At least, now the VLC doesn't close down and reports several errors. This is what the terminal shows:


cuansf@JUAN:~$ cvlc -v dvd://
VLC media player 1.0.2 Goldeneye
[0x9d52fd8] main demux warning: no access_demux module matching "file" could be loaded
[0x9d60ef0] main interface error: no interface module matched "globalhotkeys,none"
[0x9d60ef0] main interface error: no suitable interface module
[0x9cb8140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9d60f30] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: LO20EUF1
libdvdnav: DVD Serial Number: 34fb492d
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/cuansf/.dvdnav/LO20EUF1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000191
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000026b
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0000026b)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000031e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000031e)!!
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00014b1d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00014cc9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00014e70
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x00014e70)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00014f23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000154ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00015560
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x00015560)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0001661a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x0001661a)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000166cd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0009936f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00099422
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x00099422)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00176256
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x00176256)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00176309
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00188d70
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x00188d70)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x00188e23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x00197b80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x00197b80)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x00197c33
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x001e716a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_0.VOB (0x001e716a)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x001e721d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x001f7df1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x001f7ea4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x001f7ea4)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x001fbfa5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x001fc058
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_1.VOB (0x001fc058)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x002056a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00205756
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_1.VOB (0x00205756)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x0021fcca
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_14_0.VOB (0x0021fcca)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x0021fd7d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x0024a39e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_15_0.VOB (0x0024a39e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x0024a451
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x0028b2fc
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_16_0.VOB (0x0028b2fc)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x0028b3af
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x002bae7f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x002baf32
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_17_1.VOB (0x002baf32)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_0.VOB at 0x002bb021
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_18_1.VOB at 0x002bb0d4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_18_1.VOB (0x002bb0d4)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_0.VOB at 0x00324f06
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_19_0.VOB (0x00324f06)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_19_1.VOB at 0x00324fb9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_0.VOB at 0x00359cee
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_20_0.VOB (0x00359cee)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_20_1.VOB at 0x00359da1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_0.VOB at 0x00360c70
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_21_0.VOB (0x00360c70)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_21_1.VOB at 0x00360d23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_22_0.VOB at 0x00367bd2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_22_0.VOB (0x00367bd2)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_22_1.VOB at 0x00367c85
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_0.VOB at 0x0036ec03
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_23_1.VOB at 0x0036ecb6
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_23_1.VOB (0x0036ecb6)!!
libdvdread: Elapsed time 0
libdvdread: Found 23 VTS's
libdvdread: Elapsed time 7
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
[0x9d62698] dvdnav demux error: cannot set title (can't decrypt DVD?)
[0x9d62698] main demux error: Playback failure
[0x9d62698] main demux error: VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
[0x9d62698] dvdread demux error: fatal error in vts ifo
[0x9d62698] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[0x9d62698] main demux warning: no access_demux module matching "dvd" could be loaded
[0x9d758a8] main access error: no access module matched "dvd"
[0x9d61dd8] main input error: open of `dvd://' failed: no access module matched "dvd"
[0x9d61dd8] main input error: Your input can't be opened
[0x9d61dd8] main input error: VLC is unable to open the MRL 'dvd://'. Check the log for details.


Thank you for your help.

Cuansf

---

### Post by mc4man on 2009-11-20
It **may** have been more useful to see the dvdcss debug log instead of the vlc terminal output. As mentioned it is only useful when produced in the absence of an existing .dvdcss folder (actually a folder inside matching the volume label of disk, but deleting the .dvdcss folder itself is easier.

If wished, then refer back to previous post (delete .dvdcss and run the 2 commands, find and post the log.

Other than that maybe try a different disk, while rare, there are a handful of dvd titles that cannot be played in linux with unlicensed players, maybe you have one

---

### Post by Cuansf on 2009-11-21
> **mc4man said:**
> It **may** have been more useful to see the dvdcss debug log instead of the vlc terminal output. As mentioned it is only useful when produced in the absence of an existing .dvdcss folder (actually a folder inside matching the volume label of disk, but deleting the .dvdcss folder itself is easier.

If wished, then refer back to previous post (delete .dvdcss and run the 2 commands, find and post the log.

Other than that maybe try a different disk, while rare, there are a handful of dvd titles that cannot be played in linux with unlicensed players, maybe you have one

Is that .log what you need?

---

### Post by mc4man on 2009-11-22
> Is that .log what you need? 
Well that's a bit unusual, does this happen with other dvd's? (if you have others to test


what would be interesting is to try to take the drive out of the equation and see if libdvdcss has any better luck.

If you wish, because the drive appears to be  getting authenticated, is to try this ( should work, though not 100% sure.

If so..
```
sudo apt-get install dvdisaster
```
Then put the dvd in the drive, open vlc and let it try to play.

(technically dvdisaster won't read encrypted disks, but if the drive is authenticated first it will - opening the disk first in a player should do that.

After vlc fails/hangs, whatever, then open up dvdiaster ( Applications -> System Tools) and click on the read button in the side right panel.

If the drive has been properly authenticated then shortly you'll get an encrypted .iso in your home folder ( by default named medium.iso

If so, then again **delete the .dvdcss folder**, and try to play that medium.iso in vlc 

note - when you first use dvdisaster you'll get a pop up, check the disable box and click on the 'skip RS02 test'

[here's]("http://ubuntuforums.org/showthread.php?p=8352411#post8352411") what dvdisaster looks like from recent post

---

### Post by Cuansf on 2009-11-22
> **mc4man said:**
> Well that's a bit unusual, does this happen with other dvd's? (if you have others to test


what would be interesting is to try to take the drive out of the equation and see if libdvdcss has any better luck.

If you wish, because the drive appears to be  getting authenticated, is to try this ( should work, though not 100% sure.

If so..
```
sudo apt-get install dvdisaster
```Then put the dvd in the drive, open vlc and let it try to play.

(technically dvdisaster won't read encrypted disks, but if the drive is authenticated first it will - opening the disk first in a player should do that.

After vlc fails/hangs, whatever, then open up dvdiaster ( Applications -> System Tools) and click on the read button in the side right panel.

If the drive has been properly authenticated then shortly you'll get an encrypted .iso in your home folder ( by default named medium.iso

If so, then again **delete the .dvdcss folder**, and try to play that medium.iso in vlc 

note - when you first use dvdisaster you'll get a pop up, check the disable box and click on the 'skip RS02 test'

[here's]("http://ubuntuforums.org/showthread.php?p=8352411#post8352411") what dvdisaster looks like from recent post

That's a good idea but it doesn't look like to be very fast to watch a DVD. Don't you think must exits any other solution to this issue?

Any other idea from someone? Please help!!!!

Thank you for your time, mc4man!!!;)

---

### Post by ilil on 2009-11-26
What is the name of DVD you try to watch? And what region?
Have you tried other ciphered/not-ciphered DVD to watch?

---

### Post by m4tic on 2009-11-26
I installed restricted-extras from hacktolive, i can play an DVD with totem

---

