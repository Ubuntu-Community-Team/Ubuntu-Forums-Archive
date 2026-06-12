---
title: "Strange VDPAU / Composite Problem with mythfrontend on 9.10"
date: 2009-11-28
forum: Multimedia Software
---

### Post by hirnwurscht on 2009-11-28
Hello Community,

I updated my hardy (was 7.10) to karmic through adept two weeks ago.
[https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04]("https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04")

Worked really well, only had problems with the nvidia driver and lirc (since no more /dev/input/by-path/pci*event-ir for my hauppauge nova-s). 
the kernel doesn't create /dev/input/by-path/pci*event-ir for my hauppauge anymore. changing my existing udev rule and changing /lirc/hardware.conf helped (SUBSYSTEMS=="input", ATTRS{name}=="cx88 IR (Hauppauge Nova-S-Plus ", SYMLINK+="input/hauppauge_nova_s").


But i somehow messed up the nvidia driver /libvdpau install.

I had the cool avenard repo activated with hardy.
Something went wrong through the update and i re-enabled the repo, now everything works EXCEPT:

video playback

1) mplayer with vdpau plays only audio but no video "Error opening/initializing the selected video_out (-vo) device."

2) mythtv plays fine...although it is transparent/has no background color. while transparency can be fun this is not since the underlying windows shine through. (screenshot attached)

  workarounds for this:

   a) deactivate composite

   b) in compiz -> rules for windows set noargb visuals for  mythtv = heavy tearing
   
   c) start mythtv with a black background window
   
3) vdpauinfo (attached) says everything is fine




i tried (re-/un)installing different combinations of libvdpau/nvidia-glx without making it better (no problem to make it worse,tho). i had to delete /lib/*vdpau* as suggested somewhere on nvnews.com to even make it install at first.

can someone point me in the right direction?

My System:

Core 2 Quad Q6600 @ 3.0ghz
Zotac Geforce 9800GT Eco

Ubuntu 9.10 amd64
nvidia-glx 195.22


maybe this helps some poor soul having trouble with the nvidia-driver:

i had an /etc/modprobe.d/lrm-video that i had to manually delete to succesfully get the nvidia driver loaded at reboots/reinstalls.

---

### Post by hirnwurscht on 2009-11-29
OK, doesn't seem to be only VDPAU. I also have this transparency problem with some presets (who use a "wrong" background color?) of libvisual-projectm.

(bump)
Found out that vdpau is working correctly.
Even mythfrontend is alright, if I start it soon enough.
When I start mythfrontend after compiz and cairo-dock, I get the transparency problem.
Mplayer with vdpau works ok...
If I deactivate argb-visuals for mythfrontend in csm, it works but has heavy tearing.

Knowing it worked with Hardy stinks...
Can someone point me in the right direction to fix this?

---

### Post by malnon on 2010-05-12
Hi,
Did you ever get this fixed? I had it last year also and found a fix but I have rebuilt my pc and now its happening again and I cant remember what I did to fix it, also this is the only post I have found on the subject.

Thanks,

Mal

---

### Post by malnon on 2010-05-12
Just to add some more information, I am running Karmic with an Nvidia card using the latest nvidia drivers, using gnome-composting and cairo dock. When I enter mythfrontend menus display correctly, but when I watch a recording the screen is semo transparent, by this I mean the program plays but the desktop is visible as well, very strange. I did have a fix on a previous build but have lost the notes and fix is not in my favourites. I am sure the fix was more to do with running a dpkg command rather than a compiz or cairo setting. Any help would be appreciated, as a side note if I use Boxee to watch the mythtv recording it plays flawlessly !!

---

### Post by cross157 on 2010-05-12
malnon, I deal with this issue on a regular basis because mythtv is always updating. The issue, as I understand it, is with Cairo Dock. The work-around I have been using is to add the following code to /usr/bin/mythfrontend

```
export XLIB_SKIP_ARGB_VISUALS=1
```

I wrote a very simple shell script to do this because I have to do it almost daily:

```
#!/bin/sh
#Fix for QT in mythtv from using Cairo Dock

sudo cp /usr/bin/mythfrontend ~/Desktop/mythfrontend-Backup

sudo chmod -x /usr/bin/mythfrontend

sudo sed '4 i\ \
#Fix for QT from using Cairo Dock \
export XLIB_SKIP_ARGB_VISUALS=1 \
' /usr/bin/mythfrontend > ~/Desktop/secondFile

sudo cp ~/Desktop/secondFile /usr/bin/mythfrontend2

sudo mv /usr/bin/mythfrontend2 /usr/bin/mythfrontend

sudo chmod +x /usr/bin/mythfrontend

sudo rm ~/Desktop/secondFile
```

This shell script creates a backup on the Desktop, inserts the code then removes the intermediate files it created. I can't promise this will work, as I'm using Lucid

---

### Post by malnon on 2010-05-12
thx cross157 I will give that a go and see if it works, I have been experimenting and have found that if I quit cairo dock the problem persists but if I disable gnome-composting the problem goes away, but I do like my docks and I know their is a fix. 

Will try your script and report back !!

---

### Post by malnon on 2010-05-12
Big Thanks cross157 that did the trick !! I will mark thread as solved, in record time I may add :)

---

### Post by chainsawbike on 2011-05-17
maybe place the fixed "/usr/bin/mythfrontend" somewhere "in-front" of /usr/bin/ in your path then you dont need to "fix" it on every update

---

