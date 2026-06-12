---
title: "Screen Position on Samsung 960BF"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by lipin on 2007-03-29
Hello everybody :).
I i have got finally Internet running on my Xubuntu (i have changed my Internet provider to not wifi one :) ). So i began my Linux adventure once again.

After installing Xubuntu everything looked fine. But as soon as i installed nvidia driver for my GeForce 2 MX 32MB card my screen position went to the left. And i can't fix it in monitor settings because i have got only power button. 
Here are steps that i did perform to fix it but it doesn't help at all:
I changed my Monitor section:
Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
    Option         "UseEdidFreqs" "no"  // this thing i added later after reading forum
    HorizSync      30-81
    VertRefresh    56-75
EndSection

I also try to put modeline but this generator:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) 
Puke out with some errors:
# Horizontal sync frequency below minimum of 81kHz!
# Horizontal sync frequency above maximum of 30kHz!
# Refresh rate below minimum of 75Hz!
# Refresh rate above maximum of 56Hz!
And created modeline for wrong resolution "1360x1024@60" instead of "1280x1024"

Anybody can help ?? 
I guess that changing refresh rate to 60Hz could help (now is 75Hz only in menu).
Expect 1280x1024 all other resolutions look fine and display position is correct.

Thanks in advance
Lipin

PS. Sorry for my English i usually use Polish forum and my English is far from perfect.

---

### Post by lipin on 2007-03-29
Problem solved by installing nvidia legacy drivers.

---

