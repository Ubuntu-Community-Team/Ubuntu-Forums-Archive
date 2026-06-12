---
title: "Script to set s-video input on Hauppauge win-tv-pvrusb2 mpeg encoder"
date: 2008-10-24
forum: Multimedia Software
---

### Post by LarryJ2 on 2008-10-24
For reasons, I don't understand, when I leave mythbuntu,  the s-video input (which receives input from my satellite receiver) is deselected. Result, I miss recordings from the satellite receiver. When I investigate, I find the  Television input seems to be  selected by default instead of the s-video input.

This script will force the input back to s-video. Note that you must execute
   chmod o+w /sys/class/pvrusb2/sn-#######/ctl_input/cur_val
from a terminal else the script will fail complaining of "no permission".  This is because, in mythbuntu at least, the file cur_val containing  "television", "composite" or "s-video" is owned by root and it's group is root.   So the chmod above allows anyone to write to this file.   Not perhaps the most secure method, but I couldn't figure out any other scheme.  sudo su works but not from a script. And you can't "chmod +s /path" in a script so the suid trick doesn't work either.

The sn-xxxxx number is the serial number of my pvrusb2 device.  Use 
ls /sys/class/pvrusb2/  
to determine the appropriate sn####### for your device.

I put the script in with the boot init of the mythbuntu PC so it runs whenever the mythtv PC is booted.

```
#!/bin/bash
# change the selected input on a Hauppauge  Wintv PVR USB 2 to s-video 
#

# write the value "s-video" into the file "cur_val"
echo s-video > /sys/class/pvrusb2/sn-8504958/ctl_input/cur_val

# check that the value was written.
cat /sys/class/pvrusb2/sn-8504958/ctl_input/cur_val

# Other parameters of the pvrusb2 can be controlled using this same technique.
# Please see this reference:  http://www.isely.net/pvrusb2/usage.html#sysfs
exit
```

---

### Post by LarryJ2 on 2008-10-25
Attached as pvrUsbInfo.py is a python script which interrogates your /sys/class/pvrusb2/sn* directory to produce a list of all ctl* variables, their type, and possible values.  pvrUsbInfo.txt shows the full output for my pvrusb2 device.  Here's a short sample output from the script:

> The enum control named "Median Filter Type" has a current value of "Off"
Allowed values are:
Off  
Horizontal  
Vertical  
Horizontal/Vertical  
Diagonal 

The boolean control "Video GOP Closure" has a current value of "true"

The integer control named "Tuner Frequency (Hz)" has a current value of "175250000"
The minimum value allowed is 44000000, the maximum is 958000000


The bit mask control named "Video Standards Available Mask" shows a bitmasked value of "PAL-M PAL-N PAL-Nc NTSC-M NTSC-Mj NTSC-Mk
"
Allowed values are:

PAL-B  
PAL-B1  
PAL-G  
PAL-H  
PAL-I  
PAL-D  
PAL-D1  
PAL-K  
PAL-M  
PAL-N  
PAL-Nc  
PAL-60  
NTSC-M  
NTSC-Mj  
NTSC-443  
NTSC-Mk  
SECAM-B  
SECAM-D  
SECAM-G  
SECAM-H  
SECAM-K  
SECAM-K1  
SECAM-L  
SECAM-LC 

Note:  python script changed Nov 2, 2008 to show the directory where the
cur_val is located.

---

