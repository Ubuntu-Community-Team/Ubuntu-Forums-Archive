---
title: "gnome-mplayer stops working"
date: 2011-04-27
forum: Multimedia Software
---

### Post by beew on 2011-04-27
Hello,

I am using Ubuntu 10.10. At some point gnome-mplayer (and gecko-player) have stopped working. Try open any audio or video file there is nothing (the progress bar just shows "stopped"). However, Smplayer is working flawlessly for both video and audio files so I am sure it is not a mplayer problem

I have delete the folder .conf/gnome-mplayer but nothing changes.

gnome-mplayer version 0.9.9.2

mplayer version 2.0 

Help would be much appreciated.

---

### Post by beew on 2011-04-28
Bump!

---

### Post by Yellow Pasque on 2011-04-28
Start gnome-mplayer from terminal, try to play a video, and post terminal output.

---

### Post by beew on 2011-04-28
> **Temüjin said:**
> Start gnome-mplayer from terminal, try to play a video, and post terminal output.

Tried that, there was no output. The status of the gui simply said "stopped"

---

### Post by lovinglinux on 2011-04-28
> **beew said:**
> At some point gecko-player stops working. Gnome-mplayer cannot open any file, the status bar always says "stopped" and gecko-player behaves the same when trying to access web media content via Firefox.  

This doesn't seem to be a mplayer problem because Smplayer works flawlessly. 

I am wondering what are other options besides gecko-player for FF  multimedia plugin in case gnome-player doesn't get fixed. Would they work as well as gecko-player? I need gnome-player only for the gecko-player plugin  as mplayer works well otherwise.

Edited: I have started a thread in the multimedia forum but there is no response. [URL="http://ubuntuforums.org/showthread.php?t=1741277"]http://ubuntuforums.org/showthread.php?t=1741277
[/URL]
I have removed ~/.conf/gnome-mplayer but that doesn't work, actually that doesn't change gnome-mplayer's settings so I think maybe the configuration file is located somewhere else.

Try deleting ~/.mplayer/config. That file stores important config options for gnome-mplayer and gecko.

I have tested gecko-mediaplayer here with Kubuntu 11.04 and it is working fine.

Besides gecko, which I think is the best player, there is:

[LIST]
[*]totem-mozilla
[*]xine-plugin
[*]mozplugger
[*]gxineplugin
[*]kaffeine
[*]vlc
[/LIST]

Some of these plugins are just connectors to external players and so far the best I tried were gecko, followed by totem. 
I wouldn't bother with vlc and mozplugger.

---

### Post by beew on 2011-04-28
Hi, Lovinglinux,

Removing ~/.mplayer works. Thanks! I thought configuration for gnome-mplayer should be stored in ~/.config/gnome-mplayer.:confused:

---

### Post by beew on 2011-04-28
I think I have figured out what happens. 

Apparently there is a bug in gnome-mplayer. It would not play any file if  the box under  Preference > Player > Video Output is not left blank. If I leave  the box blank, it works but if I put in either xv or vdpau it stops  working. This is strange because in Smplayer and Umplayer (another front  end to mplayer) I choose video output to VDPAU and they work  flawlessly. 

In particular, gnome-mplayer cannot be configured to use VDPAU so it plays the same mp4 file with 50% cpu while Smplayer uses only ~10%. This is also the reason why FlashVideoReplacer on this machine is not using VDPAU (I posted this question before on the flashvideoreplacer thread and thought that it was a Firefox problem)
This is no longer a problem because Flash now uses vdpau when it is avaliable and on machines that need the FlashVideoReplacer there is no VDpau, but it is good to finally figure out why.

---

### Post by lovinglinux on 2011-04-28
Interesting findings. Thanks for sharing.

---

