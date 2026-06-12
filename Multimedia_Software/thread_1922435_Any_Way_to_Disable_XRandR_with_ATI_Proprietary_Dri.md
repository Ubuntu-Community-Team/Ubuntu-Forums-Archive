---
title: "Any Way to Disable XRandR with ATI Proprietary Driver?"
date: 2012-02-08
forum: Multimedia Software
---

### Post by fortitude on 2012-02-08
Hi! I'd like to disable XRandR so that the ATI proprietary driver can control switching monitors. 

The reason I need to do this is because XRandR does not support multiple graphics adapters, whereas the ATI driver does.

For example, the following switching scripts:

This one won't work because the command "aticonfig --query-monitor" is not supported when XRandR is enabled:

```

#!/bin/bash
#
# Script to switch displays, e.g. by pressing Fn-F7 on Thinkpad Laptops.
# Uses aticonfig from the ATI fglrx driver for dynamic switching, and
# xrandr for resolution changing. OSD done with xosd.sh, which uses
# osd_cat from Xosd.
#
# Author: Armin Hornung  --  www.arminhornung.de
# Date: 2008-05-01
#
# Partly based on a display switching script from SuSE 10.1
# 

# path to xosd.sh, change to "echo" if not installed
xosd=echo

# path to xrandr
xrandr="/usr/bin/xrandr"

INTERNAL="CRT2" # internal LCD of Laptop
EXTERNAL="DFP1" # external monitor, CRT or TFT


# Determine X user, script usually runs as root:

getXuser() {
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`

        if [ x"$user" = x"" ]; then
                user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XAUTHORITY=$userhome/.Xauthority
        else
                export XAUTHORITY=""
        fi
}

for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser
    if [ x"$XAUTHORITY" != x"" ]; then
        # extract current state
    export DISPLAY=":$displaynum"
    _enabled_monitors=`su $user -c "aticonfig --query-monitor | grep Enabled"`
    _connected_monitors=`su $user -c "aticonfig --query-monitor | grep Connected"`
    fi
done


# determine if internal is active
echo "${_enabled_monitors}" | grep $INTERNAL > /dev/null 2>&1 
if [ $? -eq 0 ]; then
  _internal_enabled=yes
else
  _internal_enabled=no
fi

# determine if external is connected 
# (LVDS always assumed to be connected)
echo "${_connected_monitors}" | grep $EXTERNAL > /dev/null 2>&1 
if [ $? -eq 0 ]; then
  _external_connected=yes
else
  _external_connected=no
fi

# determine if external is active
_external_enabled=no
echo "${_enabled_monitors}" | grep $EXTERNAL > /dev/null 2>&1 
if [ $? -eq 0 ]; then
  _external_enabled=yes
fi


#### display switching part ####

if [ "${_internal_enabled}" = "yes" ]; then
  if [ "${_external_connected}" = "yes" ]; then
    if [ "${_external_enabled}" = "yes" ]; then
      # switch to external only, after both enabled:
      $xosd "Enabling $EXTERNAL" &
      su $user -c "aticonfig --enable-monitor $EXTERNAL"
      # adjust resolution back to standard:
      $xrandr -s 1280x720 -r 60
    else
      # switch to both enabled, after external only
      $xosd "Enabling $INTERNAL & $EXTERNAL" &
      su $user -c "aticonfig --enable-monitor $INTERNAL,$EXTERNAL"
      # adjust resolution:
      $xrandr -s 1280x720 -r 60
    fi
  else
    $xosd "No external display connected" &
    if [ "${_external_enabled}" = "yes" ]; then
      # switch back just if external display got disconnected
      su $user -c "aticonfig --enable-monitor $INTERNAL"
      $xrandr -s 1920x1080 -r 60
    fi
  fi
else
  # switch back to internal only, after external enabled:
  $xosd "Enabling $INTERNAL" &
  su $user -c "aticonfig --enable-monitor $INTERNAL"
  # adjust resolution back to standard:
  $xrandr -s 1920x1080 -r 60
fi

exit 0

```This one won't work because XRandR does not support multiple GPU's:

```

#!/bin/bash
# Author: Andrew Martin
# Credit: http://ubuntuforums.org/showthread.php?t=1309247
echo "Enter the primary display from the following:"            # prompt for the display
xrandr --prop | grep "[^dis]connected" | cut --delimiter=" " -f1    # query connected monitors
 
read choice                                # read the users's choice of monitor
 
xrandr --output $choice --primary                    # set the primary monitor

```And, this one won't work, again, because the aticonfig --query-monitor and --enable-monitor commands won't work with XRandR enabled:

```

#!/bin/sh

CONNECTED=`aticonfig --query-monitor |grep Connected |sed -e 's/.*: //;s/,//'`
ENABLED=`aticonfig --query-monitor |grep Enabled |sed -e 's/.*: //;s/,//'`

if [ "$CONNECTED" = "CRT2" ]; then
        # We have only the internal display, don't do anything
        exit 0
elif [ "$CONNECTED" = "DFP1 CRT2" ]; then
        # We have the internal and external display, let's swicth
        # LVDS -> CRT1,LVDS -> CRT1
        if [ "$ENABLED" = "CRT2" ]; then
                SWITCH="CRT2,DFP1"
        elif [ "$ENABLED" = "DFP1 CRT2" ]; then
                SWITCH="DFP1"
        else
                SWITCH="CRT2"
        fi

        echo "Enabling $SWITCH"
        /usr/bin/aticonfig --effective=now --enable-monitor=$SWITCH
fi

```Are there any currently working methods of toggling between monitors at different resolutions? I don't need three monitors on at once, just one at a time. So, some fancy conf file trickery is not needed, just a way to toggle the active monitor between heads on multiple GPU's.

This all seems to point toward disabling XRandR as the solution (I don't need the system settings/displays dialog as it does not show monitors connected to anything but the primary graphics card.). Any way to do that in Ubuntu 11.10?

---

### Post by fortitude on 2012-02-08
I just tried one of the suggested fixes from long ago:

> Edit /etc/ati/amdpcsdb
In the section labeled [AMDPCSROOT/SYSTEM/DDX]
add this:
 	
 	EnableRandR12=Sfalse 

Also, in /etc/X11/xorg.conf in the "Device" section add:
 	
 	Option      "EnableRandR12" "false"

This did not make any difference. The aticonfig commands are still locked out. In fact, upon reboot, the edit to amdpcsdb was undone.

I think that old solutions to this problem no longer work with the latest versions of Ubuntu/ATi driver/RandR. So, I am hoping for some current info! :)

---

### Post by fortitude on 2012-02-09
I tried this:

disabled lightdm with sudo stop lightdm
opened a terminal with control-alt-F1
sudo aticonfig --set-pcs-str="DDX,EnableRandR12,FALSE"
sudo aticonfig --set-pcs-str="DDX,EnableRandR13,FALSE"
sudo grep RandR /etc/ati/amdpcsdb

Found two entries....good....rebooted....entries are still there. So far so good.

Added....

Option      "EnableRandR12" "false"
Option      "EnableRandR13" "false"

...to all four device sections in xorg.conf.

Did not work. aticonfig --query-monitor still echoes the error message.

---

### Post by fortitude on 2012-02-10
I conclude that it is impossible (or at least very hard) to disable XRandR in Ubuntu 11.10, and therefore I went a different way to solve my original problem by using a simple multi-seat configuration (lightdm.conf and xorg.conf) to switch virtual desktops between GPU's. It was not well documented, but I figured it out after trial and error. So, I am marking this thread as solved.

---

