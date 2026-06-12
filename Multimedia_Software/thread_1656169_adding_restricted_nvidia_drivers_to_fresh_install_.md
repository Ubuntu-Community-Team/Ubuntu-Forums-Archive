---
title: "adding restricted nvidia drivers to fresh install script"
date: 2010-12-30
forum: Multimedia Software
---

### Post by industrialphreak on 2010-12-30
Hey guys,

Just wondering how i could add a entry into a restore script i would run after doing a fresh install of #! Crunch bang. 

going to be using a base script from [http://ubuntuforums.org/showthread.php?t=290764&page=2](http://ubuntuforums.org/showthread.php?t=290764&page=2) 

to do the basics replacing the aptitude thing with apt-get of course

What i will be using is as follows

#!/bin/bash
#
# This script is the first in a series of setup scripts for gnome

# Check for admin rights. If user is not an admin user, exit the script
if [ $UID != 0 ]
then
echo "You need to be root to run this script! Exiting.."
exit
fi

#backup of old sources.list and xorg.conf
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bu
cp /etc/apt/sources.list /etc/X11/xorg.conf.bu


# Update the system sources and software
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean

#install my applications
sudo apt-get install firestarter sudo apt-get

# Cleanup after install
sudo apt-get clean

exit

I do understand since i threw sudo in their before the apt-get command this nullify s the need for lines #2-#10
:confused:
 :?

---

### Post by wojox on 2010-12-30
What are you asking?

---

### Post by industrialphreak on 2010-12-30
> **wojox said:**
> What are you asking?

Instead of having to manually set-up/click to dl and activate your NVIDIA v173 drivers via restricted drivers window. 

What would be the KIS method terminal command to include in the above script?

;)

---

