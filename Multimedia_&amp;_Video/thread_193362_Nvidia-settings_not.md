---
title: "Nvidia-settings not"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by mirai on 2006-06-09
I run nvidia-settings and it comes up but only with the base menu. I cant change any of the settings like color or radiance or any of the real settings. All I get is the one that says enable tooltips, display status bar, slider text entries, etc.

Where did the other parts go? Dont think it makes a difference but im running xgl

ERROR: NV-CONTROL extension not found on this Display.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

---

### Post by bluevoodoo1 on 2006-06-09
[QUOTE=mirai]Dont think it makes a difference but im running xgl[/QUOTE]

Yup, that's the reason.

---

### Post by Muzzled on 2006-06-10
[QUOTE=mirai]
ERROR: NV-CONTROL extension not found on this Display.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.[/QUOTE]

I don't want to mislead you as I know nothing about xgl, but I had the same problem under XFCE and I fixed it by doing what codejunie said [here]("http://www.ubuntuforums.org/showthread.php?t=178569&highlight=xfce+nvidia").

---

### Post by tseliot on 2006-07-04
Try opening Nvidia settings in this way:
```
nvidia-settings -c :0
```

---

