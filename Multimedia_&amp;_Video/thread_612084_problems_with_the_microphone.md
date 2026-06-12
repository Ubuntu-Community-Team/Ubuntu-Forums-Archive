---
title: "problems with the microphone"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by dmanbuhnik on 2007-11-13
Hi,
i have a strange problem:
i'm using ubuntu 7.10 since the day it got out (almost a month now) all this time the sound was working great (hear and capture) but since today there is a problem with the microphone (i test is with my dual-boot on windows and everything is working)
i think it began after i installed vmware server.
when i try to do:
System -> preferences -> sound preferences
everything is working in the test but the sound capture test which gives me this error:
```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.
```

lspci:
```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
```

alsamixer:
```
Card: NVidia CK804                                                                                                              
Chip: Realtek ALC655 rev 0
```

pls help!
(i need this for everyday use - skype mainly)
Thx in advance for the help

---

### Post by dmanbuhnik on 2007-11-14
bump

help pls!
i don't won't to reinstall ubuntu due to this problem only....

---

