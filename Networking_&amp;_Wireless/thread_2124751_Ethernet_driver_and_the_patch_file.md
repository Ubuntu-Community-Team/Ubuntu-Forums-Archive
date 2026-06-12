---
title: "Ethernet driver and the patch file"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by sparklyballs on 2013-03-12
hi there, i've had to go all the way up to kernel 3.8 to get my much desired hd-audio passthrough working with my intel hd4000 in a mac mini late 2012 quad core i7.

I'm on ubuntu 12.10 with kernel 3.8.0 generic.

Unfortunately it means that the fix in this thread [http://ubuntuforums.org/showthread.php?t=2078320](http://ubuntuforums.org/showthread.php?t=2078320) which worked in earlier kernels, no longer works for me, one of the devs over at xbmc gave me a patch file which he says he used to compile this very driver in 3.7 and it worked for him. 

[http://pastebin.com/ds4EB2W4](http://pastebin.com/ds4EB2W4)

and herein lies my question, i've tried patch -u makefiles.sh patch.txt and 

patch -Np1 --ignore-whitespace makefiles.sh patch.txt 


both with the two files in the same folder (patch.txt just being what i personally called the copy/pasta from the paste bin) 


both of which i've gleaned from google, but i keep getting hunk errors (i know i'm irresistible, but hunk is a little over flattering) 

can anyone please point me in the right direction please on whether i'm missing out on a naming convention, a placement of the files prior to patching or something else altogether ?

---

### Post by sanderj on 2013-03-12
Not a direct answer, but have you tried Ubuntu 13.04 daily build? Maybe it works for both your hd-audio and your ethernet hardware?

I'm running 13.04 for two weeks now, and it feels very stable. Better than 12.10.

---

