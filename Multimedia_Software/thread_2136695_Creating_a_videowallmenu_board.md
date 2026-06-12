---
title: "Creating a videowall/menu board"
date: 2013-04-18
forum: Multimedia Software
---

### Post by S_p_or_t_o on 2013-04-18
I was ask by a friend to make a "video wall" using an old pc and 2 TV's to play the same content (at the same time). I have the hardware all set up, i'm just tweaking my script and was hoping i could get some pointers to improve it.

i came up with 2 script: normal and "debug" (because this old P.O.S. doesn't automount usb at boot)

this is the script i placed in /usr/local/bin/
```
#!/bin/bash -l
find /video/* -type f -iname "*.mp4" > /home/user/playlist.txt
find /video/* -type f -iname "*.avi" >> /home/user/playlist.txt 
find /video/* -type f -iname "*.mov" >> /home/user/playlist.txt 
find /video/* -type f -iname "*.mpg" >> /home/user/playlist.txt
find /video/* -type f -iname "*.ogg" >> /home/user/playlist.txt
find /media/* -type f -iname "*.mp4" >> /home/user/playlist.txt
find /media/* -type f -iname "*.avi" >> /home/user/playlist.txt 
find /media/* -type f -iname "*.mov" >> /home/user/playlist.txt 
find /media/* -type f -iname "*.mpg" >> /home/user/playlist.txt
find /media/* -type f -iname "*.ogg" >> /home/user/playlist.txt
mplayer -vo xv -fs -stop-xscreensaver -loop 0 -zoom -playlist /home/user/playlist.txt
exit 1
```


the "debug" i left in the /home/user/
```
#!/bin/bash -l
echo "debugging information"
echo "--------------------------"
# check for mounted flash drives, results may vary
usbls=ls /media
echo "$usbls"
echo "--------------------------"
# check for unmounted flash drives, results may vary
usbls=ls /dev/disk/by-id/ | grep usb | grep -v 'part*'
echo "$usbls"
echo "--------------------------"
#check for mounted flash drives, actual
usbcat=cat /proc/mounts | grep '/dev/*' | grep -v '/dev/disk/by-uuid/a64xxxxxxxxx...' #the uuid of sda
echo "$usbcat"
echo "--------------------------"
if [ $usbls -gt $usbcat ]; then
echo "would you like to mount the drive to the video folder? type yes or no and then press [ENTER]"
read answer
echo "initializing"
if ["$answer" == "yes"] ; then
echo "attempting to remount the USB Drives"
# i need to remember to mkdir /video/videowall9
mount -t vfat /dev/disk/by-label/VIDWALL /video/videowall9 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
echo "mounted USB Drives to the video folder instead of the media folder"
fi
fi
echo "scanning drives and creating the playlist"
# i need to remember to keep the stable videos in /video, leave /media to temp videos
find /video/* -type f -iname "*.mp4" > /home/user/playlist.txt
find /video/* -type f -iname "*.avi" >> /home/user/playlist.txt 
find /video/* -type f -iname "*.mov" >> /home/user/playlist.txt 
find /video/* -type f -iname "*.mpg" >> /home/user/playlist.txt
find /video/* -type f -iname "*.ogg" >> /home/user/playlist.txt
echo "--------------------------"
find /media/* -type f -iname "*.mp4" >> /home/user/playlist.txt
find /media/* -type f -iname "*.avi" >> /home/user/playlist.txt 
find /media/* -type f -iname "*.mov" >> /home/user/playlist.txt 
find /media/* -type f -iname "*.mpg" >> /home/user/playlist.txt
find /media/* -type f -iname "*.ogg" >> /home/user/playlist.txt
echo "--------------------------"
echo "launching playlist"
mplayer -vo xv -fs -stop-xscreensaver -loop 0 -zoom -playlist /home/user/playlist.txt
exit 1
```

the tldr difference is the "debug" mounts the usb to the video folder, which helps if the usb doesn't automount.

for those liking the idea, i also placed this .desktop file in /home/user/.config/autostart/  so the videos would run if the usb automounted on boot
```
[Desktop Entry]Version=0.6
Name=Video Wall
Comment=Start videos
Exec=/usr/local/bin/videowall.sh
Icon=video-display
Terminal=true
Type=Application
Categories=AudioVideo;Audio;Player;
Encoding=UTF-8

```

i should totally get my friend to dump this old pc and buy a rasberry pi for this, lol.

---

