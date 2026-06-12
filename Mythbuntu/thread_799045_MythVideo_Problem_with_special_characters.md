---
title: "MythVideo: Problem with special characters"
date: 2008-05-18
forum: Mythbuntu
---

### Post by the[V]oid on 2008-05-18
Hello, I have a problem with (german) special characters in MythVideo. Although they are displayed correctly I cannot watch a video that contains such characters (eg. 'ü', 'ä' or 'ö') in it's filename. The logfile says:
```
Playing /var/lib/mythtv/videos/Simpsons/staffel12/S12E05 Homer und das Geschenk der WÃ¼rde.avi.
File not found: '/var/lib/mythtv/videos/Simpsons/staffel12/S12E05 Homer und das Geschenk der Würde.avi'
Failed to open /var/lib/mythtv/videos/Simpsons/staffel12/S12E05 Homer und das Geschenk der Würde.avi.
```
I am trying to avoid UTF8 where ever it is possible: My database's collation is "latin1_swedish_ci", the output of "locale" tells me:
```
LANG=de_DE@euro
LC_CTYPE="de_DE@euro"
LC_NUMERIC="de_DE@euro"
LC_TIME="de_DE@euro"
LC_COLLATE="de_DE@euro"
LC_MONETARY="de_DE@euro"
LC_MESSAGES="de_DE@euro"
LC_PAPER="de_DE@euro"
LC_NAME="de_DE@euro"
LC_ADDRESS="de_DE@euro"
LC_TELEPHONE="de_DE@euro"
LC_MEASUREMENT="de_DE@euro"
LC_IDENTIFICATION="de_DE@euro"
LC_ALL=
```
Anyone have a clue what I could do in order to fix this? :cry:

In case there's no possibility I could still switch back to UTF8, but I have read somewhere that MythTV is not working good with UTF8.

---

