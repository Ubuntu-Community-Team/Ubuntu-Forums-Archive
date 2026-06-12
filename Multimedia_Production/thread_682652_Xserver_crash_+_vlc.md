---
title: "Xserver crash + vlc"
date: 2008-01-30
forum: Multimedia Production
---

### Post by analyzer on 2008-01-30
Hello everybody

I have an Ubuntu Gutsy Gibbon installation. Unfortunately there is a problem to play DVDs with VLC. Each DVD judders extremely. I found out that to unset the advanced option under Video -> Output Modules -> XVideo -> Use Shared Memory solves the jerking. 

While I am watching DVDs there are a lot of crash of the Xserver. The Xserver restarts.

syslog:
```
gdm[5867]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
kernel: [  764.840000] [fglrx] PCIe has already been initialized. Reinitializing ... 
kernel: [  764.860000] [fglrx] total      GART = 130023424 
kernel: [  764.860000] [fglrx] free       GART = 114032640 
kernel: [  764.860000] [fglrx] max single GART = 114032640 
kernel: [  764.860000] [fglrx] total      LFB  = 134086656 
kernel: [  764.860000] [fglrx] free       LFB  = 114143232 
kernel: [  764.860000] [fglrx] max single LFB  = 114143232 
kernel: [  764.860000] [fglrx] total      Inv  = 0 
kernel: [  764.860000] [fglrx] free       Inv  = 0 
kernel: [  764.860000] [fglrx] max single Inv  = 0 
kernel: [  764.860000] [fglrx] total      TIM  = 0
```
Does anybody have an idea how to prevent these crashes? Thanks a lot.

---

### Post by analyzer on 2008-02-01
If somebody want more information like (Xorg Logs or the xorg.conf) please let me know. However, I will open a bug report at the weekend. Unfortunately I can't reproduce this issues at a similar system with an other graphic adapter.

Thanks

EDIT: My system is a Lenovo ThinkPad T60 with an ATI Mobility Radeon X1400 adapter.

---

