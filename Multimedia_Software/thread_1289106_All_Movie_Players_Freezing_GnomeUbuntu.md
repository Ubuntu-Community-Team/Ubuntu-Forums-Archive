---
title: "All Movie Players Freezing Gnome/Ubuntu"
date: 2009-10-12
forum: Multimedia Software
---

### Post by Lavahead on 2009-10-12
All movie players that I have installed (Mplayer, VLC, Totem) have caused Gnome to completely lockup except for the mouse cursor (I am assuming that it is the Gnome desktop and not X.org that is locking up) when I attempt to open any movie file (avi, wmv, mpg). VLC and Mplayer simply show a bright blue screen. Totem screen remains black. Nothing on Gnome is operational once the freeze occurs. I can move the mouse cursor around, but it can't do anything. None of the [ctrl][alt][Fn] combinations work.

I must use [alt][sysreq]REISUB to reboot the computer. After about two to four restarts, the movie player will finally play the video file. Does anyone have a fix for this extremely annoying problem?

I am using Ubuntu 8.04LTS (no kernel upgrades) on a Toshiba Satellite P105-S6147 notebook with Intel 94x graphics. I've been searching the forums, but I am apparently the only one with this problem. Thanks in advance.

---

### Post by Lord_ on 2009-10-12
Have you got all the non-free codecs installed? on 9.04 you can do sudo apt-get install non-free-codecs. I dont think this is the same on 8.04 but installing them could help with AVI issues. Also I had some trouble with VNC until I changed the from the default Video and Audio outputs in preferences. 

I set the sound to ALSA, I can remember what I changed the Video to but its worth checking these.

---

### Post by Lavahead on 2009-10-13
Yes, I have all the codecs installed for Totem. The necessary codecs for VLC and Mplayer apparently are included in the installation. I have played around with the various preferences. However, either the change does nothing, or it completely screws up the video.

Is there any way to make the players save the crash/freeze information to a log file?

---

### Post by vinutux on 2009-10-13
open media players from terminal..........

---

### Post by Lord_ on 2009-10-13
Ok I have a toshiba satellite m40 which had alot of trouble with the sound and wireless card. It started after I ran the upgrades, the vanilla install was ok.

My kernel was upgraded from 2.6.28-11-generic to 2.6.28-15-generic. I normally load 11 from GRUB as it is more stable in my experience. If you have an older kernel in GRUB it might be worth checking if you get the same problems when you load it.

The other thing I did was to recompile the ASLA kernel modules according to [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) if you search the site it should give you exact compile options for your laptop and is not too dificult. If you get errors when running ./configure you can google them as you may need a couple of extra packages. Once I had completed this it has stabilised things.

Good luck!

---

### Post by Lavahead on 2009-10-14
Thanks for the help! I read all of the replies and was curious about the mention of audio drivers, so I did more searching. I found an interesting article on the Freshmeat.net site. An excerpt for the record in case anyone else has this problem:
[INDENT]**Sound drivers**

You're probably curious why I start with this. It's because it's the most common cause of performance problems. The reason is not obvious. Playing only audio (for example, .mp3 files) differs greatly from playing movies. In the latter case, the player has to synchronize audio and video. Since all sound cards/drivers have some kind of buffering, this delay has to be compensated. It's not a big issue at first look; both the ALSA and OSS APIs have functions to query the buffer status, the current audio delay. Unfortunately, many of the sound drivers (mainly the OSS drivers included in the kernel) don't implement these extra (driver authors seem to take everything not needed for .mp3 playback as extra...) functions or, even worse, implement them in broken/buggy ways, reporting false values. I've even heard some drivers crash the kernel when one queries the delay!

So, as you can see, I (sadly) take up the sound drivers as the No. 1 issue on Linux. It is not only MPlayer's problem; it effects most players and games (!). MPlayer may be more sensitive, since it synchronizes everything to the audio, so broken sound drivers may cause jerky playback, hangs, or even crashes. Jerky playback (caused by inaccurate buffer delay reporting in the driver) can be worked around with the new -autosync option of MPlayer, but for more seriously broken drivers, you have to fix the driver itself. I strongly recommend using ALSA 0.9; it has turned out to be much more reliable than the in-kernel OSS drivers, even with their OSS emulation layer.[/INDENT]
I then experimented by setting default values in the ~/.mplayer/config file, specifically targeting audio parameters. One of the first things that I did notice was that mplayer was set for Pulse Audio. I changed both the value in Preferences and set the default in the config file. Mplayer started up right away with no freezing today. I'm not sure if the problem is cured yet.

As for Totem, I ran gstreamer-properties from the terminal and it is already set for Alsa, so I am not certain about what is causing Totem to freeze the entire Gnome desktop.

---

### Post by Lavahead on 2009-10-15
Well, in the end, the freezing problem still persists. I guess that I will just wait until Ubuntu 10.04 LTS come out and hope that all issues are resolved in that version.

---

