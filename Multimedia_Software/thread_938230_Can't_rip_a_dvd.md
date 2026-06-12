---
title: "Can't rip a dvd"
date: 2008-10-04
forum: Multimedia Software
---

### Post by dodle on 2008-10-04
I'm looking for a program to rip my dvd, but I can't get any of them to work.  I've tried dvd::rip, klxDVDrip, lxDVDshrink, DVDRipOMatic, kdvdbackup, and others.

Some of them I couldn't get to function at all.  Does anyone have any suggestions for me.

Also, while trying to manually compile kdvdbackup, ./configure worked fine but when I go to use make I get errors.  Here is the output if anyone wants to have a go at it.  Thanks in advance.

```

Makefile:852: warning: overriding commands for target `clean-bcheck'
Makefile:815: warning: ignoring old commands for target `clean-bcheck'
Makefile:857: warning: overriding commands for target `bcheck-am'
Makefile:820: warning: ignoring old commands for target `bcheck-am'
make  all-recursive
make[1]: Entering directory `/A/Applications/kdvdbackup'
Makefile:852: warning: overriding commands for target `clean-bcheck'
Makefile:815: warning: ignoring old commands for target `clean-bcheck'
Makefile:857: warning: overriding commands for target `bcheck-am'
Makefile:820: warning: ignoring old commands for target `bcheck-am'
Making all in doc
make[2]: Entering directory `/A/Applications/kdvdbackup/doc'
Making all in .
make[3]: Entering directory `/A/Applications/kdvdbackup/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/A/Applications/kdvdbackup/doc'
Making all in en
make[3]: Entering directory `/A/Applications/kdvdbackup/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/A/Applications/kdvdbackup/doc/en'
make[2]: Leaving directory `/A/Applications/kdvdbackup/doc'
Making all in po
make[2]: Entering directory `/A/Applications/kdvdbackup/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/A/Applications/kdvdbackup/po'
Making all in src
make[2]: Entering directory `/A/Applications/kdvdbackup/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT frmdvdinfo.o -MD -MP -MF ".deps/frmdvdinfo.Tpo" -c -o frmdvdinfo.o frmdvdinfo.cpp; \
        then mv -f ".deps/frmdvdinfo.Tpo" ".deps/frmdvdinfo.Po"; else rm -f ".deps/frmdvdinfo.Tpo"; exit 1; fi
In file included from /usr/include/dvdread/ifo_read.h:24,
                 from frmdvdinfo.h:24,
                 from frmdvdinfo.cpp:22:
/usr/include/dvdread/ifo_types.h:32:2: error: #error "Must include <inttypes.h> or <stdint.h> before any libdvdread header."
In file included from /usr/include/dvdread/ifo_read.h:24,
                 from frmdvdinfo.h:24,
                 from frmdvdinfo.cpp:22:
/usr/include/dvdread/ifo_types.h:68: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:69: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:70: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:71: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:78: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:143: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:144: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:145: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:146: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:231: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:258: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:259: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:260: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:261: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:270: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:271: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:272: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:273: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:283: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:312: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:313: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:315: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:316: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:317: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:318: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:333: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:334: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:335: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:409: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:410: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:411: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:414: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:415: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:416: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:417: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:418: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:419: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:420: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:421: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:422: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:423: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:424: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:425: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:427: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/usr/include/dvdread/ifo_types.h:437: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:447: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:448: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:457: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:458: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:459: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:468: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:469: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:470: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:471: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:480: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:481: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:482: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:491: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:492: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:493: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:494: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:495: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:502: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:503: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:504: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:513: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:514: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/usr/include/dvdread/ifo_types.h:532: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:533: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:534: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:535: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:536: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:537: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:538: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:539: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:540: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:541: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:542: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:544: error: &#8216;uint64_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:545: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:546: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:547: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:548: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:549: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:550: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:551: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:552: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:553: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:554: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:555: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:556: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:557: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:560: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:561: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:564: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:565: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:597: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:598: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:599: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:600: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:601: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:602: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:609: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:610: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:611: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:621: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:627: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:628: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:629: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:630: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:631: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/usr/include/dvdread/ifo_types.h:639: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:640: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:641: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:650: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:651: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:654: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:655: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:658: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:659: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:660: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:664: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:667: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:668: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:670: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:671: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:672: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:682: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:683: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:684: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:686: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/usr/include/dvdread/ifo_types.h:694: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:695: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:716: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:717: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:718: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:728: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:729: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:746: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:747: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:748: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:749: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:750: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:751: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:752: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:753: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:754: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:755: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:756: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:757: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:758: error: &#8216;uint64_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:759: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:760: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:761: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:762: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:763: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:764: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:765: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:766: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:767: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:768: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:769: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:770: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:771: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:772: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:773: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:776: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:777: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:780: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:781: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:784: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:787: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:788: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:790: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:791: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:793: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:802: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:803: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:810: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:818: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:819: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:820: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:822: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/usr/include/dvdread/ifo_types.h:831: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:837: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:838: error: &#8216;uint8_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:839: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:840: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/usr/include/dvdread/ifo_types.h:848: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:849: error: &#8216;uint16_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:850: error: &#8216;uint32_t&#8217; does not name a type
/usr/include/dvdread/ifo_types.h:852: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
frmdvdinfo.cpp:71: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:71: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:73: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:73: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:73: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:73: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:74: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:74: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:74: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:74: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:75: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:75: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:77: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:77: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:77: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:77: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:78: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:78: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:78: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:78: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:79: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:79: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:79: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:79: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:80: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:80: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:80: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:80: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:80: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:80: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:80: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:82: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:82: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:83: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:83: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:83: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:83: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:83: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp:85: warning: deprecated conversion from string constant to &#8216;char*&#8217;
frmdvdinfo.cpp: In member function &#8216;int threadGetDVDInfo::dvdtime2msec(dvd_time_t*)&#8217;:
frmdvdinfo.cpp:134: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;frame_u&#8217;
frmdvdinfo.cpp:136: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;hour&#8217;
frmdvdinfo.cpp:136: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;hour&#8217;
frmdvdinfo.cpp:137: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;minute&#8217;
frmdvdinfo.cpp:137: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;minute&#8217;
frmdvdinfo.cpp:138: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;second&#8217;
frmdvdinfo.cpp:138: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;second&#8217;
frmdvdinfo.cpp:141: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;frame_u&#8217;
frmdvdinfo.cpp:141: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;frame_u&#8217;
frmdvdinfo.cpp: In member function &#8216;virtual void threadGetDVDInfo::run()&#8217;:
frmdvdinfo.cpp:240: error: &#8216;struct vts_atrt_t&#8217; has no member named &#8216;nr_of_vtss&#8217;
frmdvdinfo.cpp:242: error: &#8216;struct vts_atrt_t&#8217; has no member named &#8216;nr_of_vtss&#8217;
frmdvdinfo.cpp:259: error: &#8216;struct tt_srpt_t&#8217; has no member named &#8216;nr_of_srpts&#8217;
frmdvdinfo.cpp:274: error: &#8216;struct title_info_t&#8217; has no member named &#8216;title_set_nr&#8217;
frmdvdinfo.cpp:277: error: &#8216;struct title_info_t&#8217; has no member named &#8216;title_set_nr&#8217;
frmdvdinfo.cpp:278: error: &#8216;struct title_info_t&#8217; has no member named &#8216;title_set_nr&#8217;
frmdvdinfo.cpp:280: error: &#8216;struct title_info_t&#8217; has no member named &#8216;vts_ttn&#8217;
frmdvdinfo.cpp:282: error: &#8216;struct title_info_t&#8217; has no member named &#8216;title_set_nr&#8217;
frmdvdinfo.cpp:283: error: &#8216;struct ptt_info_t&#8217; has no member named &#8216;pgcn&#8217;
frmdvdinfo.cpp:286: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;hour&#8217;
frmdvdinfo.cpp:286: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;minute&#8217;
frmdvdinfo.cpp:286: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;second&#8217;
frmdvdinfo.cpp:297: error: &#8216;struct title_info_t&#8217; has no member named &#8216;nr_of_ptts&#8217;
frmdvdinfo.cpp:297: error: &#8216;struct pgc_t&#8217; has no member named &#8216;nr_of_cells&#8217;
frmdvdinfo.cpp:300: error: &#8216;struct vtsi_mat_t&#8217; has no member named &#8216;nr_of_vts_audio_streams&#8217;
frmdvdinfo.cpp:300: error: &#8216;struct vtsi_mat_t&#8217; has no member named &#8216;nr_of_vts_subp_streams&#8217;
frmdvdinfo.cpp:309: error: &#8216;struct title_info_t&#8217; has no member named &#8216;title_set_nr&#8217;
frmdvdinfo.cpp:309: error: &#8216;struct title_info_t&#8217; has no member named &#8216;vts_ttn&#8217;
frmdvdinfo.cpp:312: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;frame_u&#8217;
frmdvdinfo.cpp:324: error: &#8216;struct title_info_t&#8217; has no member named &#8216;nr_of_angles&#8217;
frmdvdinfo.cpp:332: error: &#8216;struct vtsi_mat_t&#8217; has no member named &#8216;nr_of_vts_audio_streams&#8217;
frmdvdinfo.cpp:335: error: &#8216;struct audio_attr_t&#8217; has no member named &#8216;lang_code&#8217;
frmdvdinfo.cpp:335: error: &#8216;struct audio_attr_t&#8217; has no member named &#8216;lang_code&#8217;
frmdvdinfo.cpp:357: error: &#8216;struct audio_attr_t&#8217; has no member named &#8216;lang_extension&#8217;
frmdvdinfo.cpp:366: error: &#8216;struct pgc_t&#8217; has no member named &#8216;nr_of_programs&#8217;
frmdvdinfo.cpp:370: error: &#8216;struct pgc_t&#8217; has no member named &#8216;program_map&#8217;
frmdvdinfo.cpp:371: error: &#8216;struct pgc_t&#8217; has no member named &#8216;nr_of_programs&#8217;
frmdvdinfo.cpp:372: error: &#8216;struct pgc_t&#8217; has no member named &#8216;nr_of_cells&#8217;
frmdvdinfo.cpp:375: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;second&#8217;
frmdvdinfo.cpp:379: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;minute&#8217;
frmdvdinfo.cpp:387: error: &#8216;struct pgc_t&#8217; has no member named &#8216;program_map&#8217;
frmdvdinfo.cpp:395: error: &#8216;struct pgc_t&#8217; has no member named &#8216;nr_of_cells&#8217;
frmdvdinfo.cpp:398: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;hour&#8217;
frmdvdinfo.cpp:398: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;minute&#8217;
frmdvdinfo.cpp:398: error: &#8216;struct dvd_time_t&#8217; has no member named &#8216;second&#8217;
frmdvdinfo.cpp:405: error: &#8216;struct vtsi_mat_t&#8217; has no member named &#8216;nr_of_vts_subp_streams&#8217;
frmdvdinfo.cpp:408: error: &#8216;struct subp_attr_t&#8217; has no member named &#8216;lang_code&#8217;
frmdvdinfo.cpp:408: error: &#8216;struct subp_attr_t&#8217; has no member named &#8216;lang_code&#8217;
frmdvdinfo.cpp:420: error: &#8216;struct subp_attr_t&#8217; has no member named &#8216;lang_extension&#8217;
frmdvdinfo.cpp:430: error: &#8216;struct vts_atrt_t&#8217; has no member named &#8216;nr_of_vtss&#8217;
make[2]: *** [frmdvdinfo.o] Error 1
make[2]: Leaving directory `/A/Applications/kdvdbackup/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/A/Applications/kdvdbackup'
make: *** [all] Error 2
   
```

---

