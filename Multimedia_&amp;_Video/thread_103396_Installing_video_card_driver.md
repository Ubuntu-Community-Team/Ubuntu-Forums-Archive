---
title: "Installing video card driver"
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by lucidity on 2005-12-14
I am trying to install drivers for my video card. It is an Intel 82845g. 
As expected, Intel's website has limited resources for Linux. :rolleyes:.

Here is the page with drivers: [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I downloaded the first one and extracted it. I have no idea what to do next.

Thanks for any help :)

---

### Post by afhp on 2005-12-14
Based on other forums, this chip should be supported by the i810 driver which comes with xorg. 
```
Driver "i810"
``` in the "Device" section of xorg.conf.

[http://www.linuxquestions.org/questions/showthread.php?t=352262]("http://www.linuxquestions.org/questions/showthread.php?t=352262")
[http://www.ubuntuforums.org/showthread.php?t=51954]("http://www.ubuntuforums.org/showthread.php?t=51954")

---

### Post by lucidity on 2005-12-14
[QUOTE=afhp]Based on other forums, this chip should be supported by the i810 driver which comes with xorg. 
```
Driver "i810"
``` in the "Device" section of xorg.conf.

[http://www.linuxquestions.org/questions/showthread.php?t=352262]("http://www.linuxquestions.org/questions/showthread.php?t=352262")
[http://www.ubuntuforums.org/showthread.php?t=51954]("http://www.ubuntuforums.org/showthread.php?t=51954")[/QUOTE]

Thanks :)

I took at my xorg.conf file and the line "Driver "i810" was already there. Does this mean this is the best I can do?

---

### Post by afhp on 2005-12-15
[QUOTE=lucidity]Thanks :)

I took at my xorg.conf file and the line "Driver "i810" was already there. Does this mean this is the best I can do?[/QUOTE]

Well, your initial message only referred to being stuck after unpacking the Intel tgz -- what do you mean by "the best I can do" ? What problem are you facing with the existing i810 driver ?

---

