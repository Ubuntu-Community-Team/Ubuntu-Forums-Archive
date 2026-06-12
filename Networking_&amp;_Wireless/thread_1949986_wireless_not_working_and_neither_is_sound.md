---
title: "wireless not working and neither is sound"
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by chrisd313 on 2012-03-31
Well, I am in a bind. My wireless is not working at all and my button isn't working either. Can anyone help please. It used to work with a version of ubuntu I was running and even lubuntu. I had to reinstall lubuntu and it is not working again. My sound also went out too for some reason. I start school on Monday and would like to be able to take this machine with me if need be. 

Thanks
Chris

---

### Post by josephmills on 2012-03-31
hello there and welcome to ubuntu forums ! 

could you please open you terminal (ctrl+alt+t)and enter in 
```
lspci -nn && lsmod && rfkill list all 
```
then paste that here. 

could you also paste a ```
aplay -l 
```

thanks and again welcome to the forums !

Joseph

---

### Post by tehchibipanda on 2012-03-31
Welcome aboard! In addition to what joseph said, can your wireless card be disabled in the BIOS? Something worth checking, because I've read numerous reports that it will disable it to save power when running on battery.

---

