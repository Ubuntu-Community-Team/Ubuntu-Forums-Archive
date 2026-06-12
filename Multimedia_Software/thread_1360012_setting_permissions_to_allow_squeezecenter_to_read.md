---
title: "setting permissions to allow squeezecenter to read my music files"
date: 2009-12-20
forum: Multimedia Software
---

### Post by ashrob on 2009-12-20
Hi there,

I would really appreciate some help with this.

I have a USB drive attached to my pc that Ubuntu has called 2F44C6573806B572, which is helpful but anyway I am trying to get Squeezecenter to scan it. Squeezecenter returns the error 'Invalid value "media/2F44C6573806B572/music" for audiodir. 

Now I Googled this and someone said that it's a permissions problem. That I need to change permissions on the folder to allow Squeezecenter to scan it. That seems logical enough. 

I have tried to change them through the 'properties' tab but that's not working. I have now set up a user called squeezecenter and a group called squeezecenter but I have no idea how to link them to the USB drive folder where my music is.

Could anyone give me a clue?

Thanks.

---

### Post by maddogmadigan on 2010-10-30
I am an utter novice to ubuntu, but a die hard fan of slimserver - I had the same problem as you - my music was on an external drive (NFTS formatted) - and even though ubuntu mounted the drive, slimserver would not see it, and I was unable to change any file permissions through the properties tab.

It seems it is necessary to mount the drive on system boot and set the permissions at that time.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

As per Dapper, create a mount point (/media/windows) for your drive at startup

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

in the text editor, add to the bottom the line
UUID=YOUR DRIVE NUMBER     /media/windows       ntfs          dmask=000,fmask=111        0        0

the UUID number for your drive can be found using the command

sudo blkid

change "ntfs" to your drives format (or use "auto")

other permissions can be set besides the above, but this is beyond me...

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)  is also a great help re negotiating with fstab

save the text editor and close

reboot, relaunch slimserver, and you should now be able to browse to /media/windows under the Music Folder to specify your library, which should be within...

worked for me anyway

Good luck!

maddog

---

