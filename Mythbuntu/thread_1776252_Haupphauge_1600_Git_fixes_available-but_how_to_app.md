---
title: "Haupphauge 1600 Git fixes available-but how to apply them?"
date: 2011-06-05
forum: Mythbuntu
---

### Post by fireflymoon on 2011-06-05
Hi,
I have A Hauppehauge 1600 card with an analog chip that won't work until I can get the latest fixes shown in the link below applied. I can get some video but no sound when the card is picking up a signal from the tv cable provider. The fixes in the link are supposed to solve the issue I am having and also to improve the device's functionality. I haven't been able to install the patches though. If I run make I get an error that is shown below but the real question is:

What would normally be required to apply fixes like this? Am I getting an error because I am missing steps, dependencies, something else. Just a note-I've tried two distributions in the hope of getting enlightenment...I like both.;)

List of Patches
[http://www.mail-archive.com/mythbuntu-bugs@lists.launchpad.net/msg04630.html](http://www.mail-archive.com/mythbuntu-bugs@lists.launchpad.net/msg04630.html)

Linux TV site
[http://git.linuxtv.org/awalls/media_tree.git?a=commit;h=bb4307140fc3e91ca2d36d6bb54dc3f0266ec481](http://git.linuxtv.org/awalls/media_tree.git?a=commit;h=bb4307140fc3e91ca2d36d6bb54dc3f0266ec481)

Error

make
make -C lib all
make[1]: Entering directory `/home/mark/Downloads/src2/v4l-utils/lib'
make -C libv4lconvert all
make[2]: Entering directory `/home/mark/Downloads/src2/v4l-utils/lib/libv4lconvert'
cc -Wp,-MMD,"libv4lconvert.d",-MQ,"libv4lconvert.o",-MP -c -I../include -fvisibility=hidden -fPIC -DLIBDIR=\"/usr/local/lib\" -DLIBSUBDIR=\"libv4l\" -I../../include -I../../lib/include -D_GNU_SOURCE -DV4L_UTILS_VERSION='"0.8.4"' -g -O1 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -o libv4lconvert.o libv4lconvert.c
In file included from libv4lconvert.c:26:
libv4lconvert-priv.h:25:21: warning: jpeglib.h: No such file or directory
In file included from libv4lconvert.c:26:
libv4lconvert-priv.h:53: error: field ‘jerr’ has incomplete type
libv4lconvert-priv.h:56: error: field ‘cinfo’ has incomplete type
libv4lconvert.c: In function ‘v4lconvert_destroy’:
libv4lconvert.c:185: warning: implicit declaration of function ‘jpeg_destroy_decompress’
make[2]: *** [libv4lconvert.o] Error 1
make[2]: Leaving directory `/home/mark/Downloads/src2/v4l-utils/lib/libv4lconvert'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/mark/Downloads/src2/v4l-utils/lib'

---

### Post by ian dobson on 2011-06-06
Hi,

Your make eror comes from a missing header, maybe try installing the libjpeg development package (libjpeg62-dev?)

Regards
Ian Dobson

---

### Post by fireflymoon on 2011-06-06
Hi Ian,
Ok, Thank You, I guess " warning: [COLOR=DarkOrange]jpeglib.[/COLOR]h: No such file or directory" indicates this. I'll try it next time. I wonder how much you can screw up "guessing" which is what I would be doing. Is there another easy way of determining which headers are missing?
Thanks again...

---

### Post by ian dobson on 2011-06-06
Hi,

The easiest way is just to wait until the ubuntu team update the kernel....

Trial and error is the only way I know of when trying to backport patches. Not nice and can take sometime to get right, but "No pain, no gain"

Regards
Ian Dobson

---

