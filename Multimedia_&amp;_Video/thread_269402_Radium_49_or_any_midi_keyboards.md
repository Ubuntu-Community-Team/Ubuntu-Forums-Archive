---
title: "Radium 49 or any midi keyboards"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by jdh01 on 2006-10-01
Hi, how does one get a midi keyboard to speak to linux?  Do I need special drivers? I can't find a linux driver for my Radium 49 but obviously it can be done.

I've hooked the virtual keyboard through Jack to ZynAddSubFX as per the "QjackCtl - Connections" tutorial and it works so at leastpartof mysetup is ok.

Any help would be appreciated.  --John

---

### Post by christhemonkey on 2006-10-01
If you plug it into your computers midi port, and then connect your midi port to zyn or whatever with qjackctls midi connections tab.

I take it that it is not a usb midi keyboard?

---

### Post by jdh01 on 2006-10-01
No, it is a usb midi keyboard. --John

---

### Post by christhemonkey on 2006-10-02
The Radium49 needs a firmware loaded to it before it will work.

Get it here:
[http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/)

You will need the fxload utility as well:
```
sudo apt-get install fxload 
```

Then extract the archive (double click on it and select extract files.

Then go to a terminal and type:
```
cd ~/midisport-firmware-1.2/ 
```
Replacing with the actual directory.

Then:
```
./configure 
```

Then do:
```
make 
```

and finally:
```
sudo make install
```

To remove this program later (for whatever reason!) you will need to keep this folder and then type:
```
sudo make uninstall 
```

Then if you reboot your Radium 49 should "just work".

---

