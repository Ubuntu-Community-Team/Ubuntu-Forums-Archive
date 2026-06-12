---
title: "i am not able to install Adobe flashplayer????"
date: 2010-12-20
forum: Multimedia Software
---

### Post by scott_tiger on 2010-12-20
i downloaded the .tar.gz file of flash player from Adobe website.
unpacked it using tar cmd,but i am not able to set up/install the flash player..After unpacking i got **_libflashplayer.so_**..
friendz plz tell how to install the flash player???

---

### Post by scott_tiger on 2010-12-20
i downloaded the .tar.gz file of  flash player from Adobe website.
unpacked it using tar cmd,but i am not able to set up/install the flash  player..After unpacking i got **_libflashplayer.so_**..
friendz plz tell how to install the flash player???

---

### Post by karthick87 on 2010-12-20
Move the extracted file to it's proper place,thats it..
```
 sudo mv libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by gobbles414 on 2010-12-20
You don't have to install Flash Player from Adobe's website, you can do it directly from Ubuntu Software Center, Synaptic Package Manager, or by using the apt command in the command line...

Installing the adobe-flashplugin package will add Flash Player only. Installing the ubuntu-restricted-extras package will add many other useful features in addition to Flash Player (though you may wish to install a different version of Java than the one which is included in the restricted extras).

---

### Post by howefield on 2010-12-20
Threads merged, one really is sufficient. ;-)

---

