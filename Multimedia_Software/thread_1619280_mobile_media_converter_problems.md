---
title: "mobile media converter problems"
date: 2010-11-11
forum: Multimedia Software
---

### Post by kevinorourke2008 on 2010-11-11
Hello everybody, I have just updated mobile media converter and have bumped into a problem when I try to convert .avi to mpeg I get the following message "failed to convert", and the description is as follows,
>> Command executed:
"/opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg" -y -i "/home/kevino/Videos/The.Sum.Of.Us.(1994).FS.DVDRip.DivX3LM.avi" -f mpeg -vcodec mpeg1video -r 25 -b 1100k -acodec libmp3lame -ac 2 -ar 44100 -ab 128k -map_meta_data "/home/kevino/Videos/The.Sum.Of.Us.(1994).FS.DVDRip.DivX3LM.mpg":"/home/kevino/Videos/The.Sum.Of.Us.(1994).FS.DVDRip.DivX3LM.avi" "/home/kevino/Videos/The.Sum.Of.Us.(1994).FS.DVDRip.DivX3LM.mpg"

>> Result: 
/opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by /opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg)
----------------------------

it's probably something simple like I haven't downloaded a codec or something.

Please help  Kevino

---

### Post by aljones15 on 2011-03-09
have the same problem:

/opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by /opt/MIKSOFT/MobileMediaConverter/lib/ffmpeg)

I might add spending 3 days trying to convert amr files to mp3 is uber-frustrating.

---

### Post by johntaylor1887 on 2011-03-10
Have you tried WinFF or Handbrake for conversions? Both work great for me.

---

