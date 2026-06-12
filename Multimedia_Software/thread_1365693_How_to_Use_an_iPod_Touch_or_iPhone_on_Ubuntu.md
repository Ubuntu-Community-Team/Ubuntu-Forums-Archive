---
title: "How to Use an iPod Touch or iPhone on Ubuntu"
date: 2009-12-27
forum: Multimedia Software
---

### Post by 22flames on 2009-12-27
**What this is About**

For the past couple of days I have been working a little script that allows you to use your iPod Touch or iPhone on Ubuntu in Rythmbox or Banshee. I will post the source of the script and a download link to it as well below please give me credit if you steal this and if you want to know more about the process go to my site ianmarmour.com and read the post. 

**How to Use**

[COLOR="Red"]PSSSSSSSSSSSSSSSSSSSSSS - THERE WILL BE AN ERROR AT START JUST PRESS ENTER [/COLOR]

Copy the script below into your terminal or click the download link below and download it from the file sharer of your choice. Once you have it downloaded save it into your home folder than go into a Applications/Accessories/Terminal and run the command ```
chmod +x IpodTouch3gInstaller.sh
``` Than type ```
./IpodTouch3gInstaller.sh
``` That will initiate the installer.

```


#!/bin/bash
# init
function pause(){
   read -p “$*”
}
# other stuff
pause 'Press any key to continue…'
# other stuff

#Tells the user why they need to enter password.
echo Please type in your password so the installer can run as Root.

#Add's ifuse dev repo.
sudo add-apt-repository ppa:pmcenery/ppa

#Updates your sources.
sudo apt-get update

#Installs all needed dependancys and packages
sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1** usbmuxd

#Make the iPod's mount directory
sudo mkdir /mnt/ipod

#Gets the custom fuse.conf file from my webserver.
sudo wget http://22flames.sqweebs.com/fuse.conf 

#Moves the custom fuse.conf file to your etc folder.
sudo mv fuse.conf /etc/

#Tells the User what to do
echo Please click on system than administrator than users and groups than click the lock than mange groups than find fuse and tick the box next to your name and close the user settings box.

#reads and gives the option to reboot than waits for input
read -p "When your ready to restart your computer press enter."

#Reboots the computer

sudo reboot 


```

!!Click Here to Download the Script and Run it Easily[http://www.multiupload.com/3SHEQB4A53]("http://www.multiupload.com/3SHEQB4A53")!!

---

