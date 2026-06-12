---
title: "Problem building DRI"
date: 2005-10-22
forum: Multimedia &amp; Video
---

### Post by the_naib on 2005-10-22
I recently upgraded my Dell Inspiron 4100 laptop to Breezy from Hoary by just completely reinstalling everything from the Kubuntu CD.  This went beautifully until I tried to install DRI for my 'ATI Technologies Inc Radeon Mobility M6 LY' card which I had done before on Hoary.  I followed the instructions here:  [http://dri.freedesktop.org/wiki/Building]("http://dri.freedesktop.org/wiki/Building").
I was able to download the source but quickly realized that many tools were not installed for some reason (gcc,make,many development libraries, etc.).

 I was finally able to get through at least some of the compilation of the x.org source when I reached this error:
```
In file included from lnx_agp.c:24:
/usr/include/linux/agpgart.h:55: error: syntax error before &#8216;__u16&#8217;
/usr/include/linux/agpgart.h:60: error: field &#8216;version&#8217; has incomplete type
/usr/include/linux/agpgart.h:61: error: syntax error before &#8216;__u32&#8217;
/usr/include/linux/agpgart.h:68: error: syntax error before &#8216;}&#8217; token
/usr/include/linux/agpgart.h:71: error: syntax error before &#8216;__u32&#8217;
/usr/include/linux/agpgart.h:92: error: syntax error before &#8216;__u32&#8217;
/usr/include/linux/agpgart.h:106: error: syntax error before &#8216;__u32&#8217;
lnx_agp.c: In function &#8216;GARTInit&#8217;:
lnx_agp.c:65: error: storage size of &#8216;agpinf&#8217; isn&#8217;t known
lnx_agp.c:65: warning: unused variable &#8216;agpinf&#8217;
lnx_agp.c: In function &#8216;xf86GetAGPInfo&#8217;:
lnx_agp.c:129: error: storage size of &#8216;agpinf&#8217; isn&#8217;t known
lnx_agp.c:129: warning: unused variable &#8216;agpinf&#8217;
lnx_agp.c: In function &#8216;xf86AllocateGARTMemory&#8217;:
lnx_agp.c:221: error: storage size of &#8216;alloc&#8217; isn&#8217;t known
lnx_agp.c:221: warning: unused variable &#8216;alloc&#8217;
lnx_agp.c: In function &#8216;xf86UnbindGARTMemory&#8217;:
lnx_agp.c:324: error: storage size of &#8216;unbind&#8217; isn&#8217;t known
lnx_agp.c:324: warning: unused variable &#8216;unbind&#8217;
lnx_agp.c: In function &#8216;xf86EnableAGP&#8217;:
lnx_agp.c:356: error: syntax error before &#8216;setup&#8217;
lnx_agp.c:361: error: &#8216;setup&#8217; undeclared (first use in this function)
lnx_agp.c:361: error: (Each undeclared identifier is reported only once
lnx_agp.c:361: error: for each function it appears in.)
make[7]: *** [lnx_agp.o] Error 1
make[7]: Leaving directory `/home/doug/xc/programs/Xserver/hw/xfree86/os-support/linux'
make[6]: *** [linux] Error 2
make[6]: Leaving directory `/home/doug/xc/programs/Xserver/hw/xfree86/os-support'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/doug/xc/programs/Xserver/hw/xfree86'
make[4]: *** [hw/xfree86] Error 2
make[4]: Leaving directory `/home/doug/xc/programs/Xserver'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/doug/xc/programs'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/doug/xc'
make[1]: *** [World] Error 2
make[1]: Leaving directory `/home/doug/xc'
make: *** [World] Error 2

```

Can anyone tell me what i'm missing now? Or is there some other problem?

---

### Post by tastefulasever on 2005-11-18
the_naib, I was wondering if you got anywhere on this, I tried to compile X.org from CVS yesterday and came up with the exact same errors.

I'm going to try the fix given in this bug report [http://bugzilla.ubuntu.com/show_bug.cgi?id=18157](http://bugzilla.ubuntu.com/show_bug.cgi?id=18157)

I found it linked to this thread
[http://lists.freedesktop.org/pipermail/xorg/2005-October/010693.html](http://lists.freedesktop.org/pipermail/xorg/2005-October/010693.html)

I'll share the results in a bit.

---

### Post by tastefulasever on 2005-11-18
So that fix I linked to solved the problem for me.

Just save the following code as /usr/include/sys/kd.h
This code is the complete kd.h file.
```
/* Copyright (C) 1996, 1997 Free Software Foundation, Inc.
   This file is part of the GNU C Library.

   The GNU C Library is free software; you can redistribute it and/or
   modify it under the terms of the GNU Lesser General Public
   License as published by the Free Software Foundation; either
   version 2.1 of the License, or (at your option) any later version.

   The GNU C Library is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
   Lesser General Public License for more details.

   You should have received a copy of the GNU Lesser General Public
   License along with the GNU C Library; if not, write to the Free
   Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA
   02111-1307 USA.  */

#ifndef _SYS_KD_H
#define _SYS_KD_H	1

/* Make sure the <linux/types.h> header is not loaded.  */
#ifndef _LINUX_TYPES_H
# define _LINUX_TYPES_H	1

/* I ADDED THIS */
# define __undef_LINUX_TYPES_H
/* END MY ADD */

#endif

#include <linux/kd.h>

/* I ADDED THIS */
#ifdef __undef_LINUX_TYPES_H
# undef _LINUX_TYPES_H
# undef __undef_LINUX_TYPES_H
#endif
/* END MY ADD */

#endif	

/* sys/kd.h */
```

---

