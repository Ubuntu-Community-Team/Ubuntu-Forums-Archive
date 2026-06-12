---
title: "Multimonitor xorg.conf help for Ubuntu 7.10!"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by DawgSoldier on 2008-03-27
I am fairly new to the Ubuntu environment and I am trying to get my dual monitors to work so that it is like one large monitor.  Similar to running dual monitors in Windows where you have two separate windows open at the same time.  I currently have an output to both monitors but it is in clone mode and I have tried changing the xorg.conf file as mentioned in  [http://ubuntuforums.org/showpost.php?p=1182999&postcount=25](http://ubuntuforums.org/showpost.php?p=1182999&postcount=25) but it doesn't seem to have an effect on the display.  I tried to manually run the script from the terminal and I get the following error:

root@ubuntu:~# cd /etc/X11
root@ubuntu:/etc/X11# ./multimon.sh
-e 
        Usage: multimon.sh [1|2]
                1 = single monitor
                2 = multimonitor

exit: 18: Illegal number: -1
root@ubuntu:/etc/X11# 


My script currently reads as follows:

#!/bin/sh
#
#
# this is a script to switch between single and multiple monitor
# mode for my computer. It relies on two files being in the
# /etc/X11 directory.
# xorg.conf.singlemonitor is the singular monitor configuration
# xorg.conf.multimonitor is the multi monitor configuration.
# This script copies the selected configuration over xorg.conf
# so that it will get used during the next reboot/reload of X.

cmd=${0##*/} # Command's basename
msg="\n\tUsage: $cmd [1|2]\n\t\t1 = single monitor\n\t\t2 = multimonitor\n"

if [ $# -lt 1 ]; then
echo -e $msg
exit -1
fi

if [ $1 = "2" ]; then
echo -e "\nChanging to multi monitor mode"
sudo cp /etc/X11/xorg.conf.Xinerama /etc/X11/xorg.conf
echo
exit 2
elif [ $1 = "1" ]; then
echo -e "\nChanging to single monitor mode"
sudo cp /etc/X11/xorg.conf.singlemonitor /etc/X11/xorg.conf
echo
exit 1
else
echo -e $msg
exit -2
fi

any help would be appreciated.

---

