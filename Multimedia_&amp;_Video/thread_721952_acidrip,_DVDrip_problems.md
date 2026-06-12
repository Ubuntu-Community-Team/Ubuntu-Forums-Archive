---
title: "acidrip, DVD::rip problems"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by darksuffering on 2008-03-11
DVD::rip,
ehh I just don't know where to start, I tried figuring this out on my own and no success. Lately with DVD::rip I get a weird error when I try transcoding a movie (look at the bottom). DVD::rip use to work fine and ever since then I am not able to rip any dvds, even dvds that I ripped before using the same program.(edit) I just tried one and it seems to work but there are two movies that still don't work and one especially that I want a copy of (Jekyll + Hyde). Everything in my preferences is OK and Debug looks alright. I tried J+H with acid rip and it works fine. I just don't get it :(


there was actually more but I didnt post all of it,


Job 'Transcode video - title #1, pass 1' failed with error message:
Command exits with failure code:
Command: mkdir -m 0775 -p '/home/chris/dvdrip-data/unnamed/tmp' && cd /home/chris/dvdrip-data/unnamed/tmp && mkdir -p /home/chris/dvdrip-data/unnamed/avi/001 && execflow -n 19 transcode -H 10 -a 0 -T 1,-1,1 -x dvd -i \/dev\/hdd -w 2050,50 -b 128,0,2 --a52_drc_off -f 24,1 -M 2 -R 1 -y xvid,null -o /dev/null --print_status 25 && echo EXECFLOW_OK

/dev/hdd:1: parser error : Document is empty

^
/dev/hdd:1: parser error : Start tag expected, '<' not found

^
Invalid file format
(tcxmlcheck) Error parsing XML /dev/hdd file
*** glibc detected *** tcxmlcheck: free(): invalid pointer: 0x00002b7209eb5864 ***
======= Backtrace: =========

Aborted (core dumped)
[transcode] Error reading data from tcxmlcheck
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /dev/hdd (ok)
[transcode] V: import format    | unknown  (V=dvd|A=(null))

---

### Post by buchannon on 2008-04-16
I'm getting this same error, does anyone know how to fix it? Any ideas?

---

### Post by xc3RnbFO8P on 2008-04-17
Did you check Dvd::Rip> Preferences> Check All Settings

---

