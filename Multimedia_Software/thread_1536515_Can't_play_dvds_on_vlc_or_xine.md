---
title: "Can't play dvds on vlc or xine"
date: 2010-07-22
forum: Multimedia Software
---

### Post by mi_di on 2010-07-22
I'm trying to watch a dvd on Lucid, but not vlc or xine can open it.

I have the libdvdnav, libdvdcss and libdvdcss libraries from the medibuntu repositories installed.

Here is the log I gget from vlc when I try to play the dvd. It seems as if cannot decode the format.

```

libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: WATCHMEN
libdvdnav: DVD Serial Number: 3AB68B78
libdvdnav: DVD Title (Alternative): WATCHMEN
libdvdnav: Unable to find map file '/home/sur/.dvdnav/WATCHMEN.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
Warning: call to srand(414440)
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0x9317564] main input error: ES_OUT_RESET_PCR called

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000148ea
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000148ea)
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000304a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003b5c74
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x003b5c74)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003bad20
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x003bad20)!!
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 3
[0x9317564] main input error: ES_OUT_RESET_PCR called
[0x9317564] main input error: ES_OUT_RESET_PCR called
[0x9317564] main input error: ES_OUT_RESET_PCR called

```

---

### Post by cchhrriiss121212 on 2010-07-22
This is copy protection which Linux has not been able to keep up with:
[http://ubuntuforums.org/showthread.php?t=1533129](http://ubuntuforums.org/showthread.php?t=1533129)

---

### Post by mi_di on 2010-07-25
This is sad, do you think that changing the dvd region might help?

---

