---
title: "Monitor Backlight comes back on after DPMS offf"
date: 2010-12-23
forum: Multimedia Software
---

### Post by jeffhills on 2010-12-23
After upgrading to Mythbuntu 10.10 from 9.10 (clean install) on my combined front/backend I cannot get monitor (Dell 3007) to switch off from remote, I have been using simple script to DPMS force off for years with no problems, it still works, but some random time later the backlight comes back on.
I have tryed the more complex scripts that stop and start the frontend and all of the acpi_osi options. Disabling screensaver has no effect.
Any suggestions what causes this, or how to fix?
Sysem is Abit IP35e (I suspect this board is the problem)
Core 2 duo 6800
4 Gb RAM
Leadtech DVH 2000
2 off Hauppauge Nova T500
Gigabyte 9600GT

I have 2 remote frontends both upgraded OK
I have tryed installing 10.10 on a 'scrap' P4 machine, DPMS off works fine on it.
I would try another install and/or another MoBo but its the only TV system in the house now.

---

### Post by likwidoxigen on 2011-08-28
Ever find a solution?

---

### Post by likwidoxigen on 2011-08-28
I finally figured it out on mine. It seems to be a mouse issue waking up the dpms off. You'll need to find out what input to turn off to disable the mouse. 
```
xinput -list
```

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_3M             	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]

```

I use input 12 to turn off the trackpad.

Script: screenmouseoff
```
#!/bin/bash
xinput set-prop 12 "Device Enabled" 0
xscreensaver-command -lock
sleep 5
xset dpms force off
sleep 5
 STATUS=$(xset -q | grep "Monitor is" | awk '{print $3}')
 while [ $STATUS == "Off" ]
do
        sleep 7
        STATUS=$(xset -q | grep "Monitor is" | awk '{print $3}')
done
xinput set-prop 12 "Device Enabled" 1

```

I throw that script into /usr/bin

Then I modify /usr/share/acpi-support/screenblank

```
if [ `pidof xscreensaver` ]; then
        su $user -c "(xscreensaver-command -throttle)"
                if [ x$LOCK_SCREEN = xtrue ]; then
                su $user -c "(/usr/bin/screenmouseoff)" # Using the new good script
        fi
elif [ `pidof dcopserver` ]; then
        dcop kdesktop KScreensaverIface lock
fi

if [ x$RADEON_LIGHT = xtrue ]; then
    [ -x /usr/sbin/radeontool ] && radeontool light off
fi

```

---

