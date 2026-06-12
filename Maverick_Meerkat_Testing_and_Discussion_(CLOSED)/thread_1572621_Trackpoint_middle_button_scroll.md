---
title: "Trackpoint middle button scroll"
date: 2010-09-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2010-09-11
Has anyone out there gotten the middle button trackpoint scrolling to work on Maverick? When I upgraded from 10.04 yesterday, my file in xorg.conf.d that I had set up was preserved, but scrolling isn't working.  I used the guide here to set it up: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#xorg.conf.d](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#xorg.conf.d)

Interestingly, middle button scrolling does seem to work when my mouse is hovering over the scroll bar. Just not over the main window.

---

### Post by jblackhall on 2010-09-12
Nevermind. I see this feature is now built into Preferences -> Pointing Devices. Awesome!  Now if I could just adjust the sensitivity and speed from that menu, I'd be all set.

---

### Post by wulfman on 2010-09-13
Does scrolling still work for you after you wake the machine up from standby? 

I have a T400 here that forgets the scrolling-setting after standby, and neither the rmmod / modprobe psmouse method (just doesn't change anything) nor the ```
# reload psmouse to reactivate trackpoint scrolling SUSPEND_MODULES="${SUSPEND_MODULES:+$SUSPEND_MODULES }psmouse"
``` file in config.d (laptop hangs when going into standby) solves the problem.

Any ideas?

Thanks,
W

---

### Post by Untitled_No4 on 2010-09-13
I have T500 and I'm using the xinput method to activate middle button scroll and it doesn't seem to be affected when waking up from standby. What I did was:

1. Create a file name trackpoint in /usr/bin with the following content:
```
#!/bin/sh
xinput list | sed -ne 's/^[^ ][^V].*id=\([0-9]*\).*/\1/p' | while read id
do
        case `xinput list-props $id` in
        *"Middle Button Emulation"*)
                xinput set-int-prop $id "Evdev Wheel Emulation" 8 1
                xinput set-int-prop $id "Evdev Wheel Emulation Button" 8 2
                #xinput set-int-prop $id "Evdev Wheel Emulation Timeout" 8 200
                xinput set-int-prop $id "Evdev Wheel Emulation Axes" 8 6 7 4 5
                xinput set-int-prop $id "Evdev Middle Button Emulation" 8 0
                ;;
        esac
done
```

Run it when you log in and it will activate scrolling. I use KDE so I created a trackpoint.sh file in ~/.kde/Autostart which contains the following:
```
#! /bin/bash
trackpoint

```
I guess there is a way to set it up in Gnome as well, I don't know how though.

---

### Post by hugmenot on 2010-09-13
This works for me:

```
$ cat /etc/X11/xorg.conf.d/03-dualpoint.conf
Section "InputClass"
	Identifier "Nipple Mouse options"
	MatchIsPointer "on"
	MatchProduct "DualPoint Stick"
	Driver "evdev"
	Option "EmulateWheel" "1"
	Option "EmulateWheelButton" "2"
	Option "EmulateWheelInertia" "5"
	Option "EmulateWheelTimeout" "200"
	Option "Sensitivity" "5"
	Option "XAxisMapping" "7 6"
	Option "YAxisMapping" "4 5"
	Option "Emulate3Buttons" "0"
	Option "AccelerationProfile" "0"
EndSection
```

You have to be aware that in newer Thinkpads the device names are different.

What I can’t figure out is how to specify this xinput line in xord.conf.d. The nipple is much too slow for me and that setting works. Anyone know how to map that to xorg.conf?
```
xinput set-ptr-feedback "DualPoint Stick" 0 3.7 1
```

---

### Post by wulfman on 2010-09-13
I'll give it a try. Still, the gpointing-tool actually should work - time to file a bug report, I guess.

Will report back,
W

---

### Post by Chenzo on 2010-09-21
[https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/508754](https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/508754)

this might be the bug your looking for. I have the same problem on a T410 and the process he describes in the bug report (disable emulation, re-enable emulation w/ different button, enable emulation w/ appropriate button) works for me.

---

### Post by Chenzo on 2010-09-21
Sorry, that is a duplicate of this bug:

[https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/489830](https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/489830)

---

