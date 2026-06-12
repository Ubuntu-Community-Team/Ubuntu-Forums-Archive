---
title: "unmounting cifs shares when switching wireless networks"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by sbjaved on 2012-12-05
I run a script named 02cifs.sh (placed in /etc/NetworkManager/dispatcher.d/) to mount and unmount cifs shares when wireless network goes up or down.

```
#!/bin/bash

IF=$1
STATUS=$2

if [ "$IF" == "wlan0" ]
then
    case "$2" in
        up)
        logger -s "Network File Systems mounted"
        /etc/mountcifs.sh #contains mount commands for all shares
        ;;
        down)
        logger -s "Network File Systems unmounted"
        umount -a -t cifs
        ;;
        *)
        ;;
    esac
fi

```

Mounting works fine but all shares do not unmount when wireless disconnects. I have 3 cifs shares. Only 1 unmounts and the rest get stuck because the network is already disconnected.

Running **umount -a -t cifs** from  command line while the network is connected works well. Anybody got a working solution?

---

