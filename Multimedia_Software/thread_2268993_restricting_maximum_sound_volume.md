---
title: "restricting maximum sound volume"
date: 2015-03-12
forum: Multimedia Software
---

### Post by GwibberFooey on 2015-03-12
Is there a way to set a maximum sound volume? 

Here is the situation I am in: certain family members continuously turn the volume up too loud. So I want to restrict certain users from making the volume go up to 100%. 

*I am using the 64 bit version of Ubuntu 14.04.

:!:

---

### Post by v3.xx on 2015-03-13
You can try Alsamixer, a terminal sound control.
[ATTACH=CONFIG]260590[/ATTACH]
It will not be in the menu and must be brought up thru command line and I think will override other sound controls.  The command
```
alsamixer
```
Should already be installed.

---

### Post by GwibberFooey on 2015-03-13
Alsamixer seems to do the same thing as the pactl and pacmd commands can do. That is, adjusting the same sound-volume control setting as the physical button on the keyboard and the sound slider in the Ubuntu title bar beside the Classic Menu Indicator icon. 

What I want to achieve is me, using root privileges, enable a guest account that has permissions allowing the user to increase the sound volume only a reduced, limited amount.


Also note,
[ATTACH=CONFIG]260605[/ATTACH]  <--- The Sound Slider icon, as it appears on the Ubuntu title bar.

---

### Post by Pinoy Tux on 2015-03-15
Can be automated with a shell script

```
#! /bin/bash

THRESHOLD='50'     # Restrict maximum volume to this number %, change this to your preference


while [ true ]
do
  CURRENT_VOLUME=$(awk -F"[][]" '/dB/ { print $2 }' <(amixer sget Master) | cut -d'%' -f1)
  if [ "$CURRENT_VOLUME" -gt "$THRESHOLD" ]
  then
    amixer -q sset Master "$THRESHOLD"%     # You shall not pass!
  fi
  sleep 2     # Change this to a lower number / decimal fraction if you want a more instantaneous response
done
```

---

