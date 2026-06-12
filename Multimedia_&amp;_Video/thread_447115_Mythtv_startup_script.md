---
title: "Mythtv startup script"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by rpr on 2007-05-17
Hi,

I was a gentoo user before using ubuntu. I am now replacing my gentoo mythtv by a ubuntu one.
I used a very good bootscript in gentoo which allowed me to boot directly to mythtv without the use of gdm (better transition from bootscreen to mythtv)

Could anybody help me to convert this script to Ubuntu

/etc/init.d/mythfrondend
```

#!/sbin/runscript
# Copyright 1999-2006 Gentoo Foundation
# Distributed under the terms of the GNU General Public License v2
# $Header: $

depend() {
        use net irexec mythbackend
}

start() {

        ebegin "Starting MythTV Frontend"

        start-stop-daemon --start --quiet --background \
                --chuid ${MYTH_UID} \
                --exec /usr/bin/startx \
                -- -- ${MYTH_XOPTS} vt${MYTH_VT}
        eend $?

}

stop() {

        ebegin "Stopping MythTV Frontend"

        # Make an assumption here: if there are any of these programs running
        # under MYTH_UID, then this script started them, and now needs to kill
        # them.

        if [ "$(pgrep -u ${MYTH_UID} xinit)" ]; then
                start-stop-daemon --stop --name xinit \
                        --user ${MYTH_UID} --quiet
                eend $?
        fi

}
```

/etc/conf.d/mythfrondend
```
# User id that all the processes should run as.
MYTH_UID="mythtv"

# HOME directory.  Needed to find .xinitrc file and .mythtv directory.
HOME="/home/${MYTH_UID}"

# X runs on the first VT available.  At the point this script runs during
# system start-up, the gettys haven't started yet, so the first available VT is
# VT2.  Then, when the getty on VT2 starts, it grabs the keyboard away from X.
# To avoid having to turn off gettys in /etc/inittab, tell X where to find an
# "unreserved" VT.
MYTH_VT="7"

# If there are any other X server options you want to use, set them here.
MYTH_XOPTS="-nolisten tcp -br -dpi 100"
```


/home/mythtv/.xinitrc
```
/usr/local/bin/xwarppointer abspos 720 480
/usr/bin/xset -dpms s off
while :; do
        /usr/bin/mythfrontend -v important,general -l /var/log/mythtv/mythfrontend.log
done
```

The person who can help me will be rewarded my pocket money of the week (10€) using a paypal transcription but I am desprate to do this :(

---

### Post by rpr on 2007-05-18
Anyone?

---

### Post by rpr on 2007-05-18
Anyone? Really need help :(

---

### Post by rpr on 2007-05-19
Solved it myself. Needed to allow x to be started by everyone instead of console.

---

