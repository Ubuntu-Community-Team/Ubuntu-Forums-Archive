---
title: "nVidia 525 update problem"
date: 2024-02-24
forum: MINT
---

### Post by Autodave on 2024-02-24
I have been getting these updates forever it seems.  They start to d-l and then it stops the same place every time. Always the same ones  and they never install.  I had these before I updated to the 535  driver, but still they persist.  What can/should I do?

They are all 525 flatpak runtime packages.  And, the install always stalls at the same place d-ling them.

org.freedesktop.platform.GL.nvidia-525-105-17
org.freedesktop.platform.GL.nvidia-525-116-04
org.freedesktop.platform.GL.nvidia-525-125-06
org.freedesktop.platform.GL.nvidia-525-78-01
org.freedesktop.platform.GL.nvidia-525-85-05
org.freedesktop.platform.GL.nvidia-525-89-02
org.freedesktop.platform.GL.nvidia-535-154-05
The 535 one appeared just today even though I upgraded to the 535 driver awhile ago.

---

### Post by #&amp;thj^% on 2024-02-24
Why keep so many?
You can remove them right?
```
flatpak remove org.freedesktop.platform.GL.nvidia-525-105-17
flatpak remove org.freedesktop.platform.GL.nvidia-525-116-04
flatpak remove org.freedesktop.platform.GL.nvidia-525-125-06
flatpak remove org.freedesktop.platform.GL.nvidia-525-78-01
flatpak remove org.freedesktop.platform.GL.nvidia-525-85-05
flatpak remove org.freedesktop.platform.GL.nvidia-525-89-02
```
now do a little House cleaning:
```
sudo flatpak repair
```

---

### Post by Autodave on 2024-02-24
I did that and we will see what happens.  For anyone else that tries this, please note that the repair takes considerable time.  Not sure what all goes on there, but I have a fast machine and extremely fast internet and it still took several minutes ti complete.  When it started, it just kinda sat there like nothing at all was happening.

---

### Post by #&amp;thj^% on 2024-02-24
Did it update correctly after the repair?
```
flatpak update
```

---

### Post by Autodave on 2024-02-24
Dunno, so I ran it and this is what I got:
$ flatpak update
Looking for updates&#8230;
Info: (pinned) org.kde.Platform.Locale//6.4 is end-of-life, with reason:
   We strongly recommend moving to the latest stable version of the Plaform and SDK
Info: (pinned) org.gnome.Platform.Locale//42 is end-of-life, with reason:
   The GNOME 42 runtime is no longer supported as of March 21, 2023. Please ask your application developer to migrate to a supported platform.
Nothing to do.

What now?

---

### Post by Autodave on 2024-02-25
So far, so good.......

---

### Post by #&amp;thj^% on 2024-02-25
You need to find why these are outdated:
```
nfo: (pinned) org.kde.Platform.Locale//6.4 is end-of-life, with reason:
We strongly recommend moving to the latest stable version of the Plaform and SDK
Info: (pinned) org.gnome.Platform.Locale//42 is end-of-life, with reason:
The GNOME 42 runtime is no longer supported as of March 21, 2023. Please ask your application developer to migrate to a supported platform.
```

I'm on Arch today so mine will look different:
```
flatpak info org.kde.Platform.Locale/
            ID: org.kde.Platform.Locale
           Ref: runtime/org.kde.Platform.Locale/x86_64/5.15-23.08
          Arch: x86_64
        Branch: 5.15-23.08
        Origin: flathub
    Collection: org.flathub.Stable
  Installation: system
     Installed: 512 bytes

        Commit: babefbdf12af4c0cf75bcfeecee1f60e872c5edf3d9b709495e58933169c43fd
        Parent: b738c155c29e3b84b12eb8bb33614e349cf2e6f9b15487ab559c246d7af1a8c3
       Subject: build of org.kde.Sdk, Sat Feb 10 17:10:37 UTC 2024 (f1f17eeb6b7b989b40ceca1d5a54c87fb8edaf55)
          Date: 2024-02-10 23:34:07 +0000
Subdirectories: /en

```
```
flatpak list --app-runtime=org.kde.Platform

```

---

### Post by Autodave on 2024-02-25
Kernel: 6.1.0-1034-oem x86_64 bits: 64 compiler: N/A Desktop: Cinnamon 5.6.8 tk: GTK 3.24.33
    wm: muffin vt: 7 dm: LightDM 1.30.0 Distro: Linux Mint 21.1 Vera base: Ubuntu 22.04 jammy

I think that the 6.1 kernel should be OK.

I had no problems at all other than it wanting to update those old drivers about once a week.  
And when I would try to let the Update Manager do its thing, the d-l would start and then just 
freeze at the same spot every time: d-l never finished.

---

### Post by MAFoElffen on 2024-02-26
So this is the OEM Kernel series on Mint? Not "Ubuntu" at all right? And you are asking about "Mint Updates" here, instead of on the Mint Forum?

I am confused by that...

---

### Post by ajgreeny on 2024-02-26
Moved to **Mint** Forum which is more appropriate for this problem.

Although based on Ubuntu, Mint is different in many ways.

---

### Post by Autodave on 2024-02-26
Well, I forgot that there was a separate Mint forum here.  I also belong to the Linux Mint Forums, and posted there first, but still haven't gotten a reply.  Sigh.

---

