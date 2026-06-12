---
title: "Video/audio downloading and editing and playing"
date: 2022-03-20
forum: Multimedia Software
---

### Post by bjngchn on 2022-03-20
Main question (avidemux): 
Ok, for audio editing we have audacity. It is in repository, so no problem there.
(any better choice?)
In the past there was avidemux for video editing. It doesn't appear on
repository anymore and 
sudo apt-get install avidemux
doesn't work.
There are complicated alternatives, but they sound untrustable, plus they don't work.
What are we supposed to do do get basic avidemux from a trustable source
(no plan to upgrade), or any other alternatives in repository?
There must be an easy command line install option.
......................
Now there are many video networks. They use various embeddings.
How many embeddings are there. There is html5, what else.
Can I locate actual url of a video easily?
Right click doesn't seem to work.
Can we  download any video? : assuming we can watch...
Can downloading be prevented (for audio or video).
I mean , there are external methods of course, but it would reduce quality.
Some sites (such as brighteon. maybe also rumble)  allow slow and fast watching.
Can we do it for downloaded videos on our desktiop as well? 
I mean,. in the past kaffeine has fast play option, why not now.
(Life is short so we want to save time by fast watching/listening sometimes.)
.....................
(even) Partial answers can be very helpful and appreciated in advance.

---

### Post by Dennis N on 2022-03-20
> In the past there was avidemux for video editing. It doesn't appear on
repository anymore and
sudo apt-get install avidemux
doesn't work.

Avidemux is available for Ubuntu (see image &#8595;) as a Flatpak. It can be installed from gnome-software with the gnome-software-flatpak-plugin. Ubuntu software does not offer or support Flatpaks. Ubuntu Software can be replaced by gnome-software which offers all types of packages. (For Kubuntu, you can use the 2nd method).

1) For Ubuntu only:

_Install:_
gnome-software
gnome-software-plugin-flatpak
gnome-software-plugin-snap

_Remove:_
snap-store (the snap package which provides Ubuntu Software)

2) For Ubuntu Flavors: 

You can install Flatpaks directly from flathub.org. Follow the directions on the website under "Quick Setup".

---

### Post by bjngchn on 2022-03-20
Ok, thanks new questions then.

-Why is avidemux not in repository anymore?

-Can we trust flatmak.
 I mean,
-can it potentially create new problems
-can we trust it, in security and privacy sense.
-can we remove it later.
-how do we update it, or do we have to update flatpak or avidemux.
But I prefer not to update. 
?

-what would be the command to install avidemux then, or
is it added as a program for each user separately?

---

### Post by TheFu on 2022-03-20
There are lots of video editors on Linux.
You can use ffmpeg or mkvmerge to edit videos if you want a CLI method. I use this a bunch.  mplayer can create an EDL using human input for the location of the cuts, then that can be massaged into an mkvmerge script.   

**LosslessCut** is a non-transcoding video editor that will accept an mplayer EDL file. The main downside to  LosslessCut is that it is a bloated, slow, electron application. It has an AppImage for distribution, but appimages don't notify of available updates. Also, I find some of the keyboard shortcuts to be really poorly thought out.  Movement inside the video should be with 1 hand and marking cut locations should use the other hand, for example. As commonly happens, the developer seems to be all about the mouse, which is about the least efficient way to cut videos. Electron also doesn't seem to work until the window has focus. Since it is so slow, I usually want to work in other programs rather than wait for a slow process to finish.  Plus it doesn't work over the network if the client is a laptop with an intel iGPU.  The window gets displayed, but never filled in. Between my Ryzen desktop systems, this problem doesn't happen, though the remote machine is 6 inches away from the other one.

There are lots of video editors if you need transitions or track controls. Visit alternativeTo.net for those. Most will be in the Canonical repos - like **KDenLive** or **Shotcut** or the other 10 programs.

I haven't used avidemux in about a decade. The main thing I liked about it was the ability to convert subtitle glyphs into SRT captions. It always wants to transcode the input video, which I want to avoid.

Can we trust anything?  That's a very personal question.

How to use flatpaks or snaps or appimages is best answered by doing a little online reading.  Snaps update without our permission. Flatpaks has an update all command.  AppImages don't update - they are mostly like the old setup.exe from MS-Windows - and bring the non-updated security whole from Windows to Linux.  AppImages don't bring any constraints, whereas both snaps and flatpaks have constraints on the environment that each program runs inside. I find that snap package constraints generally are too strict and prevent the programs from actually working in my environment.
For example, I have a system with these snaps:
```
$ snap list
Name      Version   Rev    Tracking       Publisher     Notes
core18    20220309  2344   latest/stable  canonical&#10003;    base
core20    20220304  1376   latest/stable  canonical&#10003;    base
lxd       4.24      22678  latest/stable  canonical&#10003;    -
snapd     2.54.4    15177  latest/stable  canonical&#10003;    snapd
wormhole  0.12.0    349    latest/stable  snapcrafters  -
```
I'd love to use lxd and wormhole, but neither will work ... due to Canonical's overzealous constraints:
```
$ wormhole
Command 'wormhole' is available in '/snap/bin/wormhole'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
wormhole: command not found
$ /snap/bin/wormhole
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.
$ /snap/bin/lxc 
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.
```
No work. No plans to allow it to work either.

---

### Post by Dennis N on 2022-03-20
> **bjngchn said:**
> Ok, thanks new questions then.

-Why is avidemux not in repository anymore?

-Can we trust flatmak.
 I mean,
-can it potentially create new problems
-can we trust it, in security and privacy sense.
-can we remove it later.
-how do we update it, or do we have to update flatpak or avidemux.
But I prefer not to update. 
?

-what would be the command to install avidemux then, or
is it added as a program for each user separately?

If you are curious about Flatpak packages there is a lot of information on the web about them. Just googling "what is Flatpak" will give a lot of hits. All your questions will be answered with a bit of reading.

As to why Ubuntu does not have it in the repository, It's a mystery to me, since just about every other Linux distro in the Universe makes it available in their repositories. I think it's available for Windows as well?

I like the Flatak of Avidemux because it is maintained at the latest stable release regardless of what Linux distro you are using. And it works fine in Ubuntu.

---

### Post by bjngchn on 2022-03-21
Thanks a lot. 

I installed kdenlive, it is too complicated plus gives errors, and doesn't work at all,
and can't even play a video. So I want to uninstall it . 
How can I uninstall kdenlive? (and course without hurting something else)
..........................
Looks like I must install avidemux. It may not be in repository, but
still there must an easy way to install it from a trusted source.
How,... I mean , looking for a few click solution.
And also, can I install it only for 1 user, or does it have to be system wide
(this last question is a general question, for example can be asked about firefox also).
I don't want or  need updates.
............................
And audacity.. I'm familiar with audacity, Is there equally simple but better
program for sound editing? 
For example when tempo is slowed down (lower speed, same pitch),
quality of music is decreased, totally understandable, but there could be an AI type fix
with another program.

---

### Post by bjngchn on 2022-04-02
Ok, looks like I have Avidemux now. How did I install it, tried more than one thing, install uninstall, anyway it is here.....  PROBLEM: I can't make avidemux window small. It is too big, I can't move it up or down, and bottom part is invisible. So practically it is not usable. I can't see play button, although from menu I can choose play option.   ......... And in general why do things have to get worse and worse always, hardware, software. ......... What else..is there a way to make sure Avidemux doesn't connect to internet? I dont plan to update it at all.

---

### Post by Holger_Gehrke on 2022-04-02
> **bjngchn said:**
> PROBLEM: I can't make avidemux window small. It is too big, I can't move it up or down, and bottom part is invisible. So practically it is not usable. I can't see play button, although from menu I can choose play option.   ......... And in general why do things have to get worse and worse always, hardware, software. ......... What else..is there a way to make sure Avidemux doesn't connect to internet? I dont plan to update it at all.

Alt-Drag (position the mouse pointer in the window you want to move, hold Alt on the keyboard and the left button on the mouse, move the mouse) should allow you to reposition the window so you can reach its lower right corner to resize it. On XFCE there's also Alt-Right-Drag (same procedure but using the right mouse button) which will allow you to resize a window without having to reposition it first, but I don't know if your DE has that. Alternatively you can try whether avidemux will respond to the standard X11 options for setting window position and size (-geometry widthxheight+xpos+ypos ; width, height, xpos, and ypos should be replaced with numbers giving size and position in pixels).

Holger

---

### Post by hk42 on 2022-04-02
For video downloading there is a nice Firefox add-on called:
Video downloadhelper.
Just make sure to have a big swapfile and  /tmp directory

---

### Post by bjngchn on 2022-04-03
Thanks to all. NEW AVIDEMUX IS WORSE. In a previous Avidemux I'm familiar with, there was, CROP, REVERSE, ROTATE, APPEND, SPEED-UP/DOWN, chroma, etc options. These are the most fundamental options anyone may want to use. But new Avidemux doesn't have any of these. DO they still exist and maybe I don't see them? ............ ALSO still wondering whether avidemux connects to internet (with or without user consent/knowledge), and whether it can potentially steal user data in the name of crash reporting or update.

---

### Post by mIk3_08 on 2022-04-03
> **bjngchn said:**
> 
In the past there was avidemux for video editing. 
I prefer the kdenlive for video editing but get the lower version of kdenlive coz there are bugs to be fix in the latest version of kdenlive. Regards and cheers.

---

### Post by SeijiSensei on 2022-04-03
I don't know what kind of editing you need to do, but for a lot of tasks the command-line ffmpeg can often do the trick. No help if you need a GUI, of course.

---

### Post by Holger_Gehrke on 2022-04-04
> **bjngchn said:**
> In a previous Avidemux I'm familiar with, there was, CROP, REVERSE, ROTATE, APPEND, SPEED-UP/DOWN, chroma, etc options. These are the most fundamental options anyone may want to use. But new Avidemux doesn't have any of these. DO they still exist and maybe I don't see them?

Exactly, they are still there and you have missed them. Load your video, select a Video-Codec other than copy (you can't change the video if you just pass the unchanged video through - which is what the 'copy' pseudo codec does), and then hit the filter button which only becomes  available after you change the codec. There's about 80 filters in 10 categories.

Holger

---

### Post by Kanehekili on 2022-05-01
I've written [VideoCut]("https://github.com/kanehekili/VideoCut") for fast cutting (similar to VidCutter) supporting Kubuntu (QT). A [private ppa]("https://launchpad.net/~jentiger-moratai/+archive/ubuntu/mediatools") for "focal" and "jammy" can be installed . It supports many codecs, is based on mpv and ffmpeg and has its own fast muxer (which makes smoother cuts than ffmepg)

A direct install can be used for "bionic" with the "opencv" backend.

---

