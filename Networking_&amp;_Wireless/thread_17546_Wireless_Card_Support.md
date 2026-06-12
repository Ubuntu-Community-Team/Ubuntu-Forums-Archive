---
title: "Wireless Card Support"
date: 2005-03-01
forum: Networking &amp; Wireless
---

### Post by bigjt11 on 2005-03-01
I've just bought a new wireless network card, It's an ASUS WL-107G 11g, comprising of a RT2500 chipset, I was wondering whether anyone can shed some light on whether it's supported on Ubuntu. It does say that it's supported on Red hat 7 and above and other versions provided it has a 2.4.3 kernel and above 

Any help would be much appreciated

john

---

### Post by scoon on 2005-03-01
[QUOTE=bigjt11]I've just bought a new wireless network card, It's an ASUS WL-107G 11g, comprising of a RT2500 chipset, I was wondering whether anyone can shed some light on whether it's supported on Ubuntu. It does say that it's supported on Red hat 7 and above and other versions provided it has a 2.4.3 kernel and above 

Any help would be much appreciated

john[/QUOTE]

Hey there, 

If that is the RaLink rt2500 chipset you are sort of in luck.  With a little bit of work, you will not need to use ndiswrapper.  Here are some links to help you out: 

forums: [http://61.222.76.235/phpbb2/index.php](http://61.222.76.235/phpbb2/index.php)
open source dev: [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

An interesting note.  I have a linksys wireless card that uses that chipset and only version 1.4.2 works without crashing my box.  I have tried the other versions and none of them worked at all for me.  As soon as the other versions of the module get loaded, my box crashes.  Be patient and try a version lower than the current one if you run into the same problem.  The forums have been extremely helpful to me but the open source page has not been all that helpful.  Good luck. 


scoon

---

