---
title: "issue with libavdevice58 for video editor"
date: 2022-02-15
forum: Multimedia Software
---

### Post by alain.roger on 2022-02-15
Hi,

After updating packages under ubuntu 21.10 I get the following issue:
```
[FONT=monospace][COLOR=#000000]Reading package lists... Done [/COLOR]
Building dependency tree... Done 
Reading state information... Done 
Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable 
distribution that some required packages have not yet been created 
or been moved out of Incoming. 
The following information may help to resolve the situation: 

The following packages have unmet dependencies: 
 kdenlive : Depends: ffmpeg 
 libmlt7 : Depends: libavdevice58 (>= 7:4.4) but it is not installable 
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Unable to correct problems, you have held broken packages.[/COLOR][/FONT]
```

I had previously KDEnLive installed and I have to reinstall it as update remove it from my computer.
I can not install ffmpeg using apt-get so I installed it using snap which I did not want.
for unknown reason I'm not able to install libavdevices58 with v7.4.4 at least

Any help would be appreciated.
thx

---

### Post by alain.roger on 2022-02-15
I solved my problem installing one by one all missing dependencies. For unknown reason system installed obsolete packages

---

