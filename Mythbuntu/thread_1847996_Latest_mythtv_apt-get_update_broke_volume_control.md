---
title: "Latest mythtv apt-get update broke volume control"
date: 2011-09-21
forum: Mythbuntu
---

### Post by bcg30506 on 2011-09-21
After doing the apt-get upgrade last night in mythbuntu 10.04 running mythtv 0.24.1-fixes, the myth volume control now always mutes the sound whenever I try to volume up, volume down, or mute.  Then I cannot get the sound unmuted unless I ssh in and run alsamixer.  Watching alsamixer while controlling the volume in mythtv now (only after last night's updates) I can see the volume of Master adjust but then also mute.

The only errors I see in mythfrontend.log are:

2011-09-21 19:36:51.020 ALSA, Error: Setting hardware audio buffer size to 8832
2011-09-21 19:36:51.020 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-09-21 19:36:51.020 ALSA, Error: Try to manually increase audio buffer with: echo 8832 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-09-21 19:36:51.020 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely

---

### Post by bcg30506 on 2011-09-21
More info:  I temporarily fixed it by running the command suggested in the log file.
```
echo 8832 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
```
Here are the permissions of the device as it currently stands. Something changed I guess during the update.
```
$ ls -l /proc/asound/card0/pcm0p/sub0/prealloc
-rw-r--r-- 1 root root 0 2011-09-21 20:11 /proc/asound/card0/pcm0p/sub0/prealloc

```
So now my remote control changes the volume in mythfrontend without muting every time, although I doubt it will survive an exit or reboot.

---

