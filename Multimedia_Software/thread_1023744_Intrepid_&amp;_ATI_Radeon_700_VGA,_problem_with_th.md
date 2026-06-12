---
title: "Intrepid &amp; ATI Radeon 700 VGA, problem with the X server"
date: 2008-12-28
forum: Multimedia Software
---

### Post by eyden on 2008-12-28
Hallo everybody, 
I'm running Ubuntu 8.10. I've got a serious annoying issue: my screen becomes black after I choose Ubuntu from the grub's list. I always run the X server by CTR+ALT+Backspace (sometimes I do it several times :s )!!
I've tried to edit my xorg.conf but the result was that the X server failed!
I have an ATI Radeon 7000 VGA. 
the result of lspci | grep "VGA" :

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
```

my Default xorg.conf :
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```

Thanks for helping me resolve this issue =)

eYden

---

