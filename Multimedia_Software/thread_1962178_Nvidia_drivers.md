---
title: "Nvidia drivers"
date: 2012-04-20
forum: Multimedia Software
---

### Post by Kn13htmare on 2012-04-20
Hello all
Any help with this problem would be welcome.
After fitting an Asus GTX 560 ti graphics card and installing nvidia driver 295.40 via      sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
I have been left with no video play back for videos on hard drive in VLC and Movie player. There is sound but no picture.
I am however able to view video on websites just not in my stand alone players. All worked well before the new install.
Restricted extras is installed but when trying to play a DVD I get the could not read from resource error.
The other aspects like screen resolution and GPU rendering with Blender work fine.
So I am confused.


Well I don't know why dvd play back is working again but it is. And for the no picture display it seems the driver knocked out my screen contrast values for the media players.
All is fine 
Cheers

---

### Post by papibe on 2012-04-20
Hi Kn13htmare.

You may want to reset all VLC features by removing its config files:
```
rm -rf ~/.config/vlc
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by BicyclerBoy on 2012-04-20
If you are using VLC you might wish to look at using VA-API..

Requires packages:
libvdpau  (should already have this)
vdpau-va-driver
libva
vainfo

Then can enable GPU decoding in VLC (in a recent build)..

---

