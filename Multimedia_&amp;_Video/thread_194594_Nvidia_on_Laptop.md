---
title: "Nvidia on Laptop"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by Cyfr on 2006-06-11
Hi I have a toshiba laptop, I tried using the manual method and automatix to install the nvidia drivers for my 5700fx-go card. When dapper boots up it just hangs on the Nvidia Logo.

The log produced is at [http://abarrett.ath.cx/dapper/xorg.log](http://abarrett.ath.cx/dapper/xorg.log)

Thanks!

---

### Post by Cyfr on 2006-06-12
Anyone?

---

### Post by tseliot on 2006-06-12
Try disabling the AGP:
1)Boot in Recovery Mode (select it from the Grub menu almost as soon as you turn on your computer)

2) Type:
```
nano -w /etc/X11/xorg.conf
```

3) Add this line to the Section Device:
```
Option "NvAgp" "0"
```

4) Save and exit:
press CTRL+X

5) Reboot:
```
reboot
```


If the suggestion above doesn't work:
Boot in Recovery mode and type:
```
dpkg-reconfigure xserver-xorg
```

and set the Driver to "vesa" or "nv" when it asks you. If you don't know the answers to the other questions just press ENTER.
Then reboot

---

### Post by Cyfr on 2006-06-12
[QUOTE=tseliot]Try disabling the AGP:
1)Boot in Recovery Mode (select it from the Grub menu almost as soon as you turn on your computer)

2) Type:
```
nano -w /etc/X11/xorg.conf
```

3) Add this line to the Section Device:
```
Option "NvAgp" "0"
```

4) Save and exit:
press CTRL+X

5) Reboot:
```
reboot
```


If the suggestion above doesn't work:
Boot in Recovery mode and type:
```
dpkg-reconfigure xserver-xorg
```

and set the Driver to "vesa" or "nv" when it asks you. If you don't know the answers to the other questions just press ENTER.
Then reboot[/QUOTE]


Tried the NoApg thing but it still freezes on the Nvidia Logo.

Currently back with nv driver... any other ideas? :)

---

### Post by tseliot on 2006-06-12
Try this other option then:
```
Option "RenderAccel" "False"
```

---

