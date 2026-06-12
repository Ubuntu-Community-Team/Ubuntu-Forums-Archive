---
title: "Temporary Twinview without writing to xorg Nvidia"
date: 2009-10-18
forum: Multimedia Software
---

### Post by hachel on 2009-10-18
Hi
I'm trying to set up a temporary sort of twinview/metamode, like nvidia-settings does it when not started as root.

I.e. when I start the nvidia-settings via system->administration->Nvidia X Server Settings I select my (disabled) TV-0 and click Configure. Then I select Twinview and hit apply whereupon nvidia enables my TV-out.
I deliberately don't want it to write changes to the xorg.conf, since I rarely do watch stuff on my TV and I want it to be gone when I reboot.

[[img]http://img269.imageshack.us/img269/1049/screenshot001ek.th.png[/img]](http://img269.imageshack.us/img269/1049/screenshot001ek.png)

What I'm trying to do that in a one-click-script.

I ran nvidia-settings from the terminal with the -V(erbose) option to see what it was doing but I couldn't figure out what to do with the information (1280x1024 is my monitor and 1024x768 my tv):
```
$ nvidia-settings -V
Updating Screen 0's MetaModes:
  Added   > CRT-1: nvidia-auto-select @1280x1024 +0+0, TV-0: nvidia-auto-select
  @1024x768 +1280+0
  Current mode: 1280x1024 (id: 50)
  Switching to mode: 2304x1024 (id: 51)...
  Using   > CRT-1: nvidia-auto-select @1280x1024 +0+0, TV-0: nvidia-auto-select
  @1024x768 +1280+0
  Removed > CRT-1: nvidia-auto-select @1280x1024 +0+0, TV-0: NULL
  Moved   > CRT-1: nvidia-auto-select @1280x1024 +0+0, TV-0: nvidia-auto-select
  @1024x768 +1280+0
```

and this is disabling it:
```
$ nvidia-settings -V
Updating Screen 0's MetaModes:
  Added   > CRT-1: nvidia-auto-select @1280x1024 +0+0
  Current mode: 2304x1024 (id: 51)
  Switching to mode: 1280x1024 (id: 50)...
  Using   > CRT-1: nvidia-auto-select @1280x1024 +0+0
  Removed > CRT-1: nvidia-auto-select @1280x1024 +0+0, TV-0: nvidia-auto-select
  @1024x768 +1280+0
  Moved   > CRT-1: nvidia-auto-select @1280x1024 +0+0
```
Any help or hints?
Thanks

---

