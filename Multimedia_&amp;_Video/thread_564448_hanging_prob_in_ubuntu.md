---
title: "hanging prob in ubuntu"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by sanjay_ahuja on 2007-10-01
hi friend!
anybody pls help me
i m new at ubuntu nd using feisty.
it was working all fine before i installed automatrix..it gave some error message nd after tht whn i updated my ubuntu,it gave following error msg
w:duplicate entry in source list
deb://http:[www.automatrix.org](www.automatrix.org)
some thing like this 
nw i m not able top update ..nd whn i use any music player it hang after its login screen
nd also whn i give sudo gedit sources.list source list open bt hangs

pls can anybody help me to solve this bug
thnks in advance

---

### Post by jonathanmotes on 2007-10-01
Well, the sources.list file is in /etc/apt/, so you will have to enter:
```
sudo gedit /etc/apt/sources.list
```
to edit your software sources list.

You can also go to system>administration>software sources and see if you have multiple sources for the same software.

Also, did you try uninstalling Automatix? What programs did you use Automatix to install? I recommend not using Automatix unless you have to. I don't know of any sources to refer you to at the moment, but Automatix can cause problems itself and many of the programs that Automatix offers can be installed using safer methods.

Hope this helps,
Jonathan

---

