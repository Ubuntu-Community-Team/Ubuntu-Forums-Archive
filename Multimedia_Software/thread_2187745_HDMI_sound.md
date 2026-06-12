---
title: "HDMI sound"
date: 2013-11-13
forum: Multimedia Software
---

### Post by chris137 on 2013-11-13
Hi,
like many other users - as I found out after long searches - my problem is that I have no sound via HDMI output.
I know managed to make it work by doing this:
I went to additional drivers where I found two proprietary drivers. 
When I install either of them (does not matter) and restart my computer I finally get sound.
Just a 'little' problem there:
With these drivers I can only use one of my montiors.
When trying to configure them I get the following error:
> Die gewählte Bildschirmkonfiguration konnte nicht angewendet werden
Gewählte virtuelle Größe passt nicht zur verfügbaren Größe: Erwünschte=(3520, 1200), Minimum=(320, 200), Maximum=(1920, 1920)
It's German but it simply says, that the maximum size is 1920, 1920 while I want 3520, 1200.

I now know, that this problem is not easy to fix but I managed to fix it partially so I hope that the solution is not too far away.
Do I have to decide between video and audio or can someone help.

Thanks

---

### Post by Yellow Pasque on 2013-11-15
What kind of video card do you have?:
```
sudo update-pciids
lspci | grep VGA
```

---

### Post by chris137 on 2013-11-15
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Juniper PRO [Radeon HD 5750] 
=> ATI Radeon HD 5750

---

### Post by Yellow Pasque on 2013-11-15
See workaround 1 here to enable HDMI audio with open-source driver: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

---

### Post by chris137 on 2013-11-15
It worked!
Thanks a lot!
I wonder how i did not find this on google :|

---

