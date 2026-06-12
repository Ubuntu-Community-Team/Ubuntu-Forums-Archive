---
title: "[SOLVED] My Holy Grail! Use nVidia to enable external screen without X restart!"
date: 2008-10-07
forum: Multimedia Software
---

### Post by nickzeff on 2008-10-07
OK. This has been quite a big thing for me.

I often startup and use my laptop around the house. However, I have a replication port, and I like to dock my computer and then use the laptop's internal screen and an external screen sitting side by side. If I start up Ubuntu undocked, it is impossible to then dock my laptop and enable the external screen without mucking around in nvidia-settings and manually detecting and enabling the monitor and switching it on through the GUI.

But now I have worked out how to simplify this process using a bash script, and would be delighted if others benefited from my hard work late the other night!

This only works for laptops using the nvidia drivers... so all you Dell latitude owners might be interested.

**Staying clear of the xorg.conf**

My xorg.conf is pretty pristine. It allows the nvidia driver to do all the configuration. My Intrepid upgrade cleaned it up for me, but you could do the same by typing:

```

sudo cp /etc/X11/xorg.conf xorg.conf.backup
sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig
```

This basically backs up your xorg and then allows nvidia-xconfig to update a fresh version with the directives needed to use the nvidia driver etc.

**Building nv-control-dpy**

nvidia-settings is a cool GUI which allows you to control many aspects of your displays. In fact, you can save your settings and then request that they be executed at the start of every session with a simple bash command:

```
nvidia-settings --load-config-only
```

Unfortunately, this technique does not load any external screen enabling you've done. nVidia have listed this in their TODO section. Perhaps the next version of nvidia-settings will render my script obsolete.

Currently, you'll need to build an application available from nvidia to do the work for you. Redmoskito did all the hard work in working this out, so kudos to him. Follow his instructions at:

[http://ubuntuforums.org/showthread.php?p=5809670](http://ubuntuforums.org/showthread.php?p=5809670)

And stop once nv-control-dpy is built and placed in a convenient place.

Rather than use his PHP script, I wrote bash script which does the hard work. This is my first ever bash script, so apologies if it could be done a much easier way!

```
#!/bin/sh

# Set the display we are looking for here.
# I am interested in a CRT monitor being attached, but this could be TV-0 or something

DISPLAY_TARGET="CRT-0"

# Ensure that desired display is attached by probing the currently connected displays
# and seeing if GREP has failed or not

nv-control-dpy --probe-dpys | grep $DISPLAY_TARGET > /dev/null 2>&1
if [ $? -gt 0 ] ; then
  echo 1>&2 'Error: Could not discover the display "'$DISPLAY_TARGET'"'
  exit 1
fi


# Since display exists, we need to build the modepool for all displays, if this has not been done already

nv-control-dpy --build-modepool > /dev/null 2>&1
if [ $? -gt 0 ] ; then
  echo 1>&2 'Error: Could not build modepools'
  exit 1
fi


# See if device is currently enabled
# nv-control-dpy basically returns a list of the associated displays as bitwise values
# Then outputs a final device mask which indicates which of those displays are being used
# So if my CRT-0 has a value of 0x00000001 and internal display DFP-0 is 0x00010000
# then a device mask of 0x00010000 would indicate the CRT is not enabled, but 0x00010001
# means they're both enabled.
 
NVOUTPUT=`nv-control-dpy --get-associated-dpys`
DISPLAY_TARGET_BITMASK=`expr "$NVOUTPUT" : ".*$DISPLAY_TARGET (\(..........\)"`
DISPLAY_ALLOLD_BITMASK=`expr "$NVOUTPUT" : ".*device mask: \(..........\)"`
DISPLAY_ALLNEW_BITMASK=$(($DISPLAY_ALLOLD_BITMASK | $DISPLAY_TARGET_BITMASK))

if [ $DISPLAY_ALLNEW_BITMASK = $(($DISPLAY_ALLOLD_BITMASK)) ] ; then
  echo 1>&2 'Error: The display is already enabled'
  exit 1
fi

nv-control-dpy --set-associated-dpys $DISPLAY_ALLNEW_BITMASK > /dev/null 2>&1


if [ $? -gt 0 ] ; then
  echo 1>&2 'Error: There was a problem enabling the display'
  exit 1
fi

# I have my laptop display (DFP-0) on the left, and I want it to be the 'primary' display
# then CRT, then TV. This way, when I enable the screen, the gnome panel won't jump over to the CRT
# as a new primary monitor
nv-control-dpy --assign-twinview-xinerama-info-order 'DFP,CRT,TV' > /dev/null 2>&1

# The way we can enable the screen is to add the display as a metamode and get xrandr to switch to it
# Any display with a value of 'nvidia-auto-select' means it is part of the mode
# Any display set to NULL means it is not part of the mode
# This line needs to be modified for every user's particular needs,
# especially the coordinates.
NVOUTPUT=`nv-control-dpy --add-metamode "DFP: nvidia-auto-select +0+0, $DISPLAY_TARGET: nvidia-auto-select +1680+0"`

if [ $? -gt 0 ] ; then
  echo 1>&2 'Error: Could not add metamode'
  exit 1
fi

# The output from nv-control-dpy includes the refresh rate of the new mode.
# This acts as a kind of unique id for the entry
REFRESHID=`expr "$NVOUTPUT" : ".*$id=\([0-9]*\)"`

# Now we have the id, we just need to get the list of available modes from xrandr
# and extract the new resolution of all of the enabled displays which can be identified alongside the refresh rate 
MODES=`xrandr`
RESOLUTION=`expr "$MODES" : ".* \([0-9]*x[0-9]*\)[ ]*$REFRESHID"`

# Now activate it!
xrandr -s "$RESOLUTION@$REFRESHID"
```

**I don't understand the script!**

Actually, have a play around with the nv-control-dpy command until you're happy you understand it. Then alter my script accordingly. A brilliant introduction is here:

[http://www.stuvel.eu/archive/75/selecting-nvidia-screens-on-commandline](http://www.stuvel.eu/archive/75/selecting-nvidia-screens-on-commandline)


**Automating the script**

I saved the script above as ~/.script/detect-external-monitor.sh after making it executable with chmod 755 <filename>

Now I have it loading up by adding it to my startup progs in sessions. However, you could call it from within, say /etc/X11/xinit/xinitrc so that when X starts, it automatically enables the screen when plugged in.

But, the most important thing I did was bind it to the WINDOWS+D key combination on my keyboard. Now if I dock, I just press this, and my screen turns on. Plenty of tutorials around showing you how to do this!


**What next?**
 
Well, I could learn to write a daemon that checks every second or so to see if my laptop has docked, or rig the script up some other way to respond to the dock action. If anyone out there knows how to do this, let me know... or I'll investigate myself.

---

### Post by ZManODS on 2008-10-10
This works great but after changing my display resolution with xrandr the gnome-panel will stretch across both monitors. Also, If I maximize a window it will stretch across both screens!

Is there anyway to have gnome-panel just stretch across the main monitor? If I save my configuration and reboot my computer I will have both monitors working AND the gnome-panel will be correctly on just one screen. 

Is there anyway I can have this behave after using xrandr?

---

### Post by nickzeff on 2008-10-12
> **ZManODS said:**
> This works great but after changing my display resolution with xrandr the gnome-panel will stretch across both monitors. Also, If I maximize a window it will stretch across both screens!

Is there anyway to have gnome-panel just stretch across the main monitor? If I save my configuration and reboot my computer I will have both monitors working AND the gnome-panel will be correctly on just one screen. 

Is there anyway I can have this behave after using xrandr?

The instructions I have provided should officially create a "twinview" config, which is what you're getting. But for some reason when I swap resolutions with randr on my setup it actually provides me with 2 separate X screens without restarting, which is exactly what I want. So my panel is on one screen, and windows maximize only to the one screen they are currently on.

I have no idea why you should get crappy Twinview, and I should get the two X screens when we're both using similar setups.

What PC are you using? What is your screen configuration (ie. DFP, CRT etc.)?

---

### Post by ZManODS on 2008-10-12
I am running a Dell Inspiron 9300 with a GeForce 6800 video card.

Both my devices are DFP's with a resolution of 1920x1200

```

Using NV-CONTROL extension 1.14 on :0.0
Connected Display Devices:
  DFP-0 (0x00010000): Sharp
  DFP-1 (0x00020000): DELL E248WFP

```

My laptop monitor DFP-0 is on the left.

It's strange because if I configure the setup in with xrandr or I configure it with nvidia-settings I always get the undesired behavior of the toolbar and windows stretching across both screens. However if I save my xorg.conf with the twinview setup and restart my computer it will load correctly, ie maximized windows will be across only one screen.

Have any clue? Thanks.

---

### Post by dasheep on 2008-10-20
LOL Thats really funny. I've also spent at least 2 Evenings for almost the same purpose. My aim was to toggle between an internal and external monitor over a Hot-Key. Unfortunately the function-keys (like Fn+F7) can't be assigned for this since they are addressed with root rights. Reading your post a had a second try with a simple user key (win+...) and success!! it works ;-)

Here an alternative with a slightly different approach just for completeness sake. I already integrated two of your elements as well.

```

#!/bin/bash

#first use nvidia-settings to create 3 metamodes:
# 1 with internal screen only
# 2 with both screen active
# 3 with only external screen

external_attached=$(/home/myhome/.scripts/nv-control-dpy --probe-dpys|grep DFP-1)
if [ -z "$external_attached" ]; then
	screen_internal;
	exit;
fi

# Sincedisplay exists, we need to build the modepool for all displays, if this has not been done already
#/home/myhome/.scripts/nv-control-dpy --build-modepool > /dev/null 2>&1




# displays=$(/home/myhome/.scripts/nv-control-dpy --print-metamodes | egrep "\(0x[01]*" |awk '{print $1 " "}' | tr -d '\n')

min_res=$(xrandr | grep minimum| sed -e 's/.*minimum //'| sed -e 's/,.*//'| sed -e 's/ //g')
max_res=$(xrandr | grep maximum| sed -e 's/.*maximum //'| sed -e 's/,.*//'| sed -e 's/ //g')

#Gets the ids of the respective metamodes
external_mode=$(/home/myhome/.scripts/nv-control-dpy --print-metamodes| grep "DFP-0: NULL" |grep "id=" | sed -e 's/.*id=\([[:digit:]]*\).*/\1/g')
internal_mode=$(/home/myhome/.scripts/nv-control-dpy --print-metamodes| grep "$max_res" | grep "DFP-1: NULL" |grep "id=" |sed -e 's/.*id=\([[:digit:]]*\).*/\1/g')
mirror_mode=$(/home/myhome/.scripts/nv-control-dpy --print-metamodes| grep -v "NULL" |grep "id=" |sed -e 's/.*id=\([[:digit:]]*\).*/\1/g')
current_mode=$(/home/myhome/.scripts/nv-control-dpy --print-current-metamode | grep "id=" | sed -e 's/.*id=\([[:digit:]]*\).*/\1/g')

#  	echo $current_mode
#  	echo $mirror_mode
#  	echo $internal_mode
#  	echo $external_mode


#Hack from Nvidia: rate encodes the id of the metamode

function screen_external(){
  xrandr --output default --mode $min_res --rate $external_mode
}

function screen_internal(){
	xrandr --output default --mode $max_res --rate $internal_mode
}

function screen_mirror(){
	if [ -z "$external_attached" ]; then exit; fi
	xrandr --output default --mode $max_res --rate $mirror_mode
}


function screen_toggle(){
# 	echo $current_mode
# 	echo $mirror_mode
# 	echo $internal_mode
# 	echo $external_mode

	case "$current_mode" in
					$internal_mode)
									screen_mirror
									;;
					$mirror_mode)
									screen_external
									;;
					$external_mode)
									screen_internal
									;;
					*)
									#screen_internal
									;;
	esac
}

#What should we do?
 DO="$1"
 if [ -z "$DO" ]; then
       DO="toggle"

 fi

case "$DO" in
        toggle)
                screen_toggle
                ;;
        internal)
                screen_internal
                ;;
       external)
               screen_external
               ;;
       mirror)
               screen_mirror
               ;;
#        both)
#                screen_both
#                ;;
       status)
               echo "Current Fn-F7 state is: $current_mode"
               echo
               echo "Attached monitors:"
               xrandr | grep "\Wconnected" | sed "s/^/ /"
               ;;
       *)
               echo "usage: $0 <command>" >&2
               echo >&2
               echo "  commands:" >&2
               echo "          status" >&2
               echo "          internal" >&2
               echo "          external" >&2
               echo "          mirror" >&2
               #echo "          both" >&2
               echo "          toggle" >&2
               echo >&2
               ;;
esac

```

---

### Post by swatkins on 2009-01-02
I found a very easy way to switch between both monitors to a single monitor, using xorg.conf and xrandr. It's described here:

[http://ubuntuforums.org/showthread.php?p=6480694](http://ubuntuforums.org/showthread.php?p=6480694)

Sam

---

### Post by Jenster112 on 2009-01-15
Wow, thank you so much!  This is exactly what I've been looking for and I appreciate your share.  I owe you man.

---

### Post by ldrn on 2009-05-23
Thank you, this is perfect; I was trying to be able to switch between combinations among three displays (laptop, VGA and DVI) with my Dell D830 laptop, and this works! Very smooth, too.

Kind of ironic, since Nvidia's GUI tool crashes with the same setup when I go to hit "Okay" after changing which monitors are off and so on.

---

