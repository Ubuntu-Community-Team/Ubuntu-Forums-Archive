---
title: "Vdpau video artifacts fix upgrade howto!"
date: 2011-03-21
forum: Mythbuntu
---

### Post by allram on 2011-03-21
Hi!
Here comes the fix for the artifacts problem for vdpau.
I will clearify the background problem for the artifacts. Artifacts has been seen in mythtv vesion 0.24 (and probably 0.23). 
The problem has not been nvidia and theres vdpau function, that let user to hardware decode video material. 
The problem has been the ffmpeg/libmpeg2(against the vdpau api) version that mythtv uses in there 0.24 version.
In mythtv 0.25 version they have what i think removed libmpeg2, and only uses ffmpeg(probably newer version).
I will warn you this is just a development version of mythtv and all function may not work as opposed to, so I take no responsible for what this will cause for you.
I can only say that it worked for me.
Here's the fix(or should i call it for upgrade to mythtv 0.25):
First you have to remove your current version of mythtv(0.24 probably):
sudo apt-get purge mythtv*

Now you haft to fix your sources.list file, you can read about it here.
[https://launchpad.net/~mythbuntu/+archive/0.25/+index?field.series_filter=lucid]("https://launchpad.net/~mythbuntu/+archive/0.25/+index?field.series_filter=lucid")

Simplest way is to use this line:
sudo add-apt-repository ppa:mythbuntu/0.25

Update your apt:
sudo apt-get update

if update complain about a letter "n": /etc/apt/sources.list.d/mythbuntu-0_25-maverick.list
open the file:
sudo pico -w /etc/apt/sources.list.d/mythbuntu-0_25-maverick.list
and remove "n" and uncomment the two lines above the "n" letter.
save the file

try update again and no problem should not occur.
sudo apt-get update

You need to install an extra missing packet(for me it was missing, mabe not for you) that you can download from here:
[http://launchpadlibrarian.net/43535484/libdirectfb-1.2-0_1.2.8-5ubuntu2_i386.deb]("http://launchpadlibrarian.net/43535484/libdirectfb-1.2-0_1.2.8-5ubuntu2_i386.deb")
install it:
sudo dpkg -i ......


because this library missing package dependecies(or what the problem is), so you haft to tell the apt every package to install:

sudo apt-get install mythtv mythtv-database mythtv-frontend mythtv-backend mythtv-themes mythtv-dbg mythtv-common mythtv-transcode-utils mythtv-theme-childish mythtv-theme-mythbuntu mythtv-theme-metallurgy libmyth-0.24

(you haft to add mythtv-mythvideo, etc. if you want that to be installed too, but you can install it later)

Now you can reboot(recomended) and use mythtv 0.25. 

To setup vdpau in mythtv use this setup in Video/Playback settings:
Remove all resolution settings under Profile normal.
Create two new resolution settings. One for HD materials and one for lower resolution for mpeg2 video(i have just picked two resolution interwalls).
so this is an example:
1. res <= 1920 1088 & res >= 1200 650 decoder: vdpau video:vdpau ,vdpau 
    Deinterlacer: Advanced 2x hardware filter: vdpaubuffersize=32
2. res < 1200 650 & res > 0 0 decoder: Standard video:vdpau  ,vdpau 
   Deinterlacer: Advanced 2x hardware filter: vdpaubuffersize=32

vdpaubuffer fixes the small artifacts that still remain in some hd playback (if you would not run with the vdpaubuffersize filter)

Standard decoder fixes the big artifacts squares at some mpeg2 materials/tv-channels.

This worked for me,,,, but I can't promise that it would work for you.

---

### Post by allram on 2011-03-22
Has this been any help for someone?
For me it worked great and I have a nice and smooth picture without a single artifact in any materials.

---

