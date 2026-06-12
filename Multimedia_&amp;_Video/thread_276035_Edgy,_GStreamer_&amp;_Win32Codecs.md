---
title: "Edgy, GStreamer &amp; Win32Codecs"
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by Danny-919 on 2006-10-12
Hi There,
i am having a problem with Edgy multimedia playback. I try opening files using totem (gstreamer), having w32codecs & gstreamer0.10-pitfdll installed. Error is: "You do not have a decoder installed to handle this file. You might need to install the necessary plugins." Maybe gst-inspect output helps here...

> danny@lmac2:~$ gst-inspect-0.10 pitfdll
Plugin Details:
  Name:                 pitfdll
  Description:          DLL-loader elements
  Filename:             /usr/lib/gstreamer-0.10/libpitfdll.so
  Version:              0.9.1.1
  License:              GPL
  Source module:        pitfdll
  Binary package:       PitfDLL
  Origin URL:           [http://ronald.bitfreak.net/pitfdll/](http://ronald.bitfreak.net/pitfdll/)

  qtadec_bin: quicktime binary audio decoder
  dmodec_wmspdmodv1: DMO wmspdmod decoder version 1
  dmodec_wmadmodv3: DMO wmadmod decoder version 3
  dmodec_wmadmodv2: DMO wmadmod decoder version 2
  dmodec_wmadmodv1: DMO wmadmod decoder version 1
  dmodec_wmvdmodv3: DMO wmvdmod decoder version 3
  dmodec_wmvdmodv2: DMO wmvdmod decoder version 2
  dmodec_wmvdmodv1: DMO wmvdmod decoder version 1
  dmodec_wmv9dmodv3: DMO wmv9dmod decoder version 3
  dshowdec_ir41_32v4: DS ir41_32 decoder version 4
  dshowdec_ir50_32v5: DS ir50_32 decoder version 5

  11 features:
  +-- 11 elements


i know there used to be some gst-register, or sth. like that, but i heared it is not necessary anymore. However i fail trying to play any media with totem. Any help highly appreciated. :confused: 

Best regards,
Danny

PS: Installation is out of the box edgy. No discussion "it's still a beta" please.

---

### Post by tseliot on 2006-10-12
Make sure that all your repositories are enabled (universe and multiverse) and type:
```
sudo aptitude install totem-xine
```

this will remove totem-gstreamer (say yes)

---

