---
title: "Check if flash is running"
date: 2011-03-10
forum: Multimedia Software
---

### Post by cbob on 2011-03-10
Hello,
Anyone know a way to check if flash is running? From command line or script.
I've tried 
```
grep flashplayer /proc/`pgrep plugin-containe`/maps
```But it also gives output if flash is blocked(by flashblock in firefox).

/cbob

---

### Post by no2498 on 2011-03-10
adobe has a test flash on its site

---

### Post by cbob on 2011-03-10
Sure, but this if for a script. Trying to expand this script to not suppress screen saver if flash is blocked i firefox.
```
#!/bin/bash

# Cleanup any bad state we left behind if the user exited while flash was
# running
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true

we_turned_it_off=0

while true; do
    sleep 60
    flash_on=0

    for pid in `ps -eaf | grep "plugin-container" | grep -v 'grep' | awk '{print $2}'` ; do
        if grep 'flashplayer' /proc/$pid/maps > /dev/null ; then
            flash_on=1
        fi

        ss_on=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`

        if [ "$flash_on" = "1" ] && [ "$ss_on" = "true" ]; then
            gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled \
            --type bool false
            we_turned_it_off=1
        elif [ "$flash_on" = "0" ] && [ "$ss_on" = "false" ] \
        && [ "$we_turned_it_off" = "1" ]; then
            gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled \
            --type bool true
            we_turned_it_off=0
        fi
    done
done

```

---

