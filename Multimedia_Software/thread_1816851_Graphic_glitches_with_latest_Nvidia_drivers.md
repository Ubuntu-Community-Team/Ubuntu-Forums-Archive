---
title: "Graphic glitches with latest Nvidia drivers"
date: 2011-08-02
forum: Multimedia Software
---

### Post by fizikz on 2011-08-02
I'm running the latest version (x86 275.21) of nVidia's drivers and I've noticed some frequent and annoying graphic glitches. When scrolling through websites or documents, sometimes parts of the page temporarily "stick" and don't scroll, while other parts do. At first I thought this was an issue with Firefox, but it happens in evince and other applications. Another example is switching tabs in Firefox, but the image remains fixed on the (fake) image of the previous tab until I mouse over active portions of the new tab. 

Have others encountered this?

---

### Post by Eromatic on 2011-08-03
Just with flash content when using its hardware acceleration with VDPAU.

---

### Post by fizikz on 2011-08-03
Any solutions?

---

### Post by fizikz on 2011-08-03
It's strange to see my older office computer with Intel integrated graphics on Ubuntu performing  better on web pages that my home laptop with a discrete nVidia graphics card. Now what can I do to change this?

---

### Post by overdrank on 2011-08-03
Hi and I assume you are using Ubuntu 10.04 Lucid Lynx. What is the model of the graphics card?
You can use the command ```
lspci | grep VGA
``` to identify your hardware.
Have you tried changing any settings in 
```
nvidia-settings
```

---

### Post by fizikz on 2011-08-03
I'm using Ubuntu 11.04. I updated that information in my profile. 
```
lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce Go 7700] (rev a1)
```

What options in nvidia-settings would be applicable to this problem?

---

### Post by overdrank on 2011-08-03
> **fizikz said:**
> I'm using Ubuntu 11.04. I updated that information in my profile. 
```
lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce Go 7700] (rev a1)
```

What options in nvidia-settings would be applicable to this problem?

Hi and I have not had the chance to use 11.04 but you may try the performance level  under Powermizer. Sorry I could not be of more help. :)

---

### Post by fizikz on 2011-08-03
The performance level is not manually configurable. Also, I'm not sure that would really do anything since it's not performance that's lacking. I don't have reason to believe this issue is specific to 11.04, so whatever you would know for 10.04 might still be useful. Thanks.

---

### Post by beew on 2011-08-04
> I'm running the latest version (x86 275.21) of nVidia's drivers and I've  noticed some frequent and annoying graphic glitches. When scrolling  through websites or documents, sometimes parts of the page temporarily  "stick" and don't scroll, while other parts do. At first I thought this  was an issue with Firefox, but it happens in evince and other  applications. Another example is switching tabs in Firefox, but the  image remains fixed on the (fake) image of the previous tab until I  mouse over active portions of the new tab. 

How did you install the Nvidia driver? The latest stable version is 280.13, not 275.21. 

I installed it from the x-swat ppa.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

Since I have upgraded from either 275.09 or 275.19 (can't remember) I haven't used 275.21. I have never encountered the problem you described.

---

### Post by fizikz on 2011-08-04
Oh, you're right about 280.13. I had not seen that yet. I installed the nVidia drivers manually, as I have for years now. I tried using the x-swat ppa and uninstalling my current drivers, but this causes my computer to lock up on boot. I'm running in recovery mode now. I recall that I had this same issue in the past when I tried using x-swat. What could be wrong?

EDIT: I've played around with it some more and now I have it so that it boots and jockey shows the nvidia drives as activated, but not in use. Also, things like glxinfo and glxgears will not run. I get errors such as: Error: couldn't find RGB GLX visual or fbconfig

---

### Post by fizikz on 2011-08-04
From what I can tell, the nVidia drivers are installed, since I see the nVidia splash screen when booting and nvidia-settings shows the newest driver version. However, anything needing OpenGL fails to run, such as glxinfo, glxgears, globs benchmark tool, and games. Any help?

---

