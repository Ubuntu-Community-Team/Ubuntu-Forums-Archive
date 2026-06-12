---
title: "How to make VLC the default DVD player"
date: 2008-07-25
forum: Multimedia Software
---

### Post by Ghuloomo on 2008-07-25
Guys, how to make VLC the default DVD player in Ubuntu 8.4? Whenever I insert a DVD or VCD Totem player starts.
I guess VLC's sound volume is better. :guitar:

---

### Post by niyonk on 2008-07-25
The Only way i know would be system->preferences->preferred applications.

I do not use VLC, so I can only tell you that :)

---

### Post by Midgetprawn on 2008-07-25
I may be struggling to get VLC to play DVD but here is how to make VLC default:

taken from [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


UBUNTU 8.04 HARDY HERON USERS ONLY


To change the default DVD player in Hardy Heron to VLC (not Kubuntu, issues with Xubuntu), copy and paste this command into the terminal:

gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to Places > Computer > Edit > Preferences > Media > DVD Video and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD. If playback doesn't work properly, navigate to Video > Deinterlace within VLC and select mode "Blend". If that still doesn't solve your issue, or you just want more features enabled upon launch (such as fullscreen upon launch), follow the intructions in the next paragraph.

Right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties" and change the launch command from "wxvlc %F" to:

vlc --volume 512 %m

or to have DVD playback automatically launch in fullscreen:

vlc --volume 512 --fullscreen %m

Close the VLC properties dialog and exit the menu editor.

Note: Remember to enable deinterlacing in VLC > Video > Deinterlace if you see any artifacts during playback, or if playback doesn't work correctly (the same is true with some AVI files also). To exit and enter fullscreen in VLC, just press the "f" key.

---

### Post by Ghuloomo on 2008-07-25
Thank you Midgetprawn .. Done..!

---

### Post by Ghuloomo on 2008-07-25
> **niyonk said:**
> The Only way i know would be system->preferences->preferred applications.

I do not use VLC, so I can only tell you that :)
What u use then? :p

---

### Post by niyonk on 2008-07-25
I use MPlaya :cool:

It's good enough for me. I plays all media that i currently have ;)

---

### Post by Ghuloomo on 2008-07-26
> **niyonk said:**
> I use MPlaya :cool:

It's good enough for me. I plays all media that i currently have ;)
Mplayer is good too.. I was using it for a period of time. For windows users, it's the best choice.

Thanks for sharing niyonk

---

### Post by markbuntu on 2008-07-26
The easiest way to change any defaults for files/drives is in Nautilus.

---

