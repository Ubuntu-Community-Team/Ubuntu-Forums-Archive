---
title: "Pulseaudio over LTSP with audacity"
date: 2013-08-15
forum: Multimedia Software
---

### Post by ben-Nabiy_Derush on 2013-08-15
I am posting this for the sake of anyone else who is struggling with audio issues on their thin clients under LTSP and Ubuntu 12.10+ (or debian, or linux mint ).

The symptoms are:
VLC, Totem etc. all work fine, but once you start audacity, all audio on the client dies. The only way to start the audio again is to reboot the client hardware. 

To fix the issue:

From the command line:
```
sudo ltsp-chroot --arch=<arch>[nano|vi|fav-txt-editor] /usr/share/ltsp/ltsp-init-common
```

and in the function start_sound add the line [COLOR=#ff0000]-L module-suspend-on-idle \[/COLOR]:
```
PULSE_DETECT=module-udev-detect
                PULSE_VOLUME_RESTORE=module-stream-restore
                /usr/bin/pulseaudio --system \
                --exit-idle-time=-1 \
                --disable-shm \
                --no-cpu-limit \
                --resample-method=trivial \
                --high-priority \
                --log-target=syslog \
                -L $PULSE_DETECT \
                -L "module-native-protocol-tcp auth-anonymous=1" \
                -L $PULSE_VOLUME_RESTORE \
                -L module-rescue-streams \
                -L "module-native-protocol-unix auth-anonymous=1" \
               [COLOR=#ff0000] -L module-suspend-on-idle \[/COLOR]
                -n &
                ;;
```
then save the file. 

Issue ```
$sudo ltsp-update-image
``` and reboot your thin client. Your audio should work again.

---

### Post by malangaman on 2013-08-15
Thanks

---

