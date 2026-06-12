---
title: "gstreamer0.10-pitfdll"
date: 2009-09-11
forum: Multimedia Software
---

### Post by mike67114 on 2009-09-11
Will someone please tell me where I can find [SIZE=1]gstreamer0.10-pitfdll
for the _AMD64._
[/SIZE] [B]
[/B]

---

### Post by mc4man on 2009-09-11
So you don't waste any time on this, you can't find it for amd_64 because it's use is for some of the w32codecs.

for example this is what it'll provide here on hardy, none of which are available in an amd_64 install

> doug@doug-laptop:~$ gst-inspect pitfdll
Plugin Details:
  Name:			pitfdll
  Description:		DLL-loader elements
  Filename:		/usr/lib/gstreamer-0.10/libpitfdll.so
  Version:		0.9.1.1
  License:		GPL
  Source module:	pitfdll
  Binary package:	PitfDLL
  Origin URL:		[http://ronald.bitfreak.net/pitfdll/](http://ronald.bitfreak.net/pitfdll/)

  dshowdec_ir50_32v5: DS ir50_32 decoder version 5
  dshowdec_ir41_32v4: DS ir41_32 decoder version 4
  dmodec_wmv9dmodv3: DMO wmv9dmod decoder version 3
  dmodec_wmvdmodv1: DMO wmvdmod decoder version 1
  dmodec_wmvdmodv2: DMO wmvdmod decoder version 2
  dmodec_wmvdmodv3: DMO wmvdmod decoder version 3
  dmodec_wmadmodv1: DMO wmadmod decoder version 1
  dmodec_wmadmodv2: DMO wmadmod decoder version 2
  dmodec_wmadmodv3: DMO wmadmod decoder version 3
  dmodec_wmspdmodv1: DMO wmspdmod decoder version 1
  qtadec_bin: quicktime binary audio decoder


---

