---
title: "Ubunutu Feisty odd video"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by myname on 2007-06-21
I have an odd video problem...  

I've finally had a chance to install the multimedia codecs in a fresh install of Ubuntu Feisty, via this page:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

When I watch an mpg video clip, the colors are not right, they are blue tones, and the color of skin is grey. 

First I added Movie Player totem (xine backend), then none of my movie players would load.  So I removed both, and just installed Movie Player Totem (xine backend).  that player won't load up, the window opens, then immediately closes.

My system has an ATI Radeon x1600, and latest drivers installed with envy.  My Ubuntu box with an nvidia card plays the same video correctly.  Is this a driver issue, or a codec issue?

When I had ubuntu Edgy Eft installed with the Kubuntu desktop, the same thing would happen with movie player, but Kaffeine played it fine.

Has anyone had this problem?

--Kevin

---

### Post by Gremlinzzz on 2007-06-21
try smplayer  [http://smplayer.sourceforge.net/linux/index_en.php](http://smplayer.sourceforge.net/linux/index_en.php)  click download and get the deb package
if your going to watch movies on line uninstall totem pluging and use mplauer pluging
i get my codecs from  
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
just paste commands in terminal.

---

### Post by Gremlinzzz on 2007-06-21
To setup your mplayer plugin right click on the online video screen and choose  X11 for video & ASLA  audio
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
these commands made it so i can watch divxs on line

---

### Post by myname on 2007-06-21
thanx for the help, however, these are all MPG's that I have on my hard drive.  Is there a codec I'm missing between my two systems, or is it the video card and the player conflict?

--Kevin

---

### Post by myname on 2007-06-22
I just tried a DVD, after following the steps to get DVD working, and the video in DVD is all blue.  I think this may be due to the ATI Proprietary drivers, unless there is a setting in the xorg.conf that will take care of this.

has anyone else had similar behaver?  I don't remember this happening before I installed the drivers.

any help on this would be most appreciated.

--Kevin

---

### Post by myname on 2007-06-22
I solved the problem... Did a search on something, can't remember what, and I noticed there is a gstreamer-properties command, I made a change from that window, not sure what it was set to and changed to what, but the video is picture perfect now.

--Kevin

---

### Post by shaggly on 2007-06-22
It would be most helpful if you could go back and find what you changed Kevion, for the rest of us that are having similiar problems.

I just changed out my card today from an Nvidia card to an Ati, and now all of my video playbacks are scr#wed

---

### Post by myname on 2007-06-25
> **shaggly said:**
> It would be most helpful if you could go back and find what you changed Kevion, for the rest of us that are having similiar problems.

I just changed out my card today from an Nvidia card to an Ati, and now all of my video playbacks are scr#wed

I am not at home so I can't test this for sure, but will do so when I get home this evening.  

However, IIRC, open a terminal and type:

sudo gstreamer-properties

Then, in the video dropdown, I changed it to Hc <something>.

Again, if I had an Ubuntu box in front of me, I would know the names of the options, but it was one of the video options.

--Kevin

---

### Post by myname on 2007-06-25
> **shaggly said:**
> It would be most helpful if you could go back and find what you changed Kevion, for the rest of us that are having similiar problems.

I just changed out my card today from an Nvidia card to an Ati, and now all of my video playbacks are scr#wed

open up a terminal,
type in gstreamer-properties

Select the Video tab

in the default output area (top area), I selected X Window System (no Xv)for plugin.

Hope this helps.

--kevin

---

### Post by jerrykun on 2007-06-26
hehe this is funny, my only problem comes when i have beryl on i found that i cant play videos on my labtop. But if i turn off beryl i can see them in all players.

when i have beryl on i get this messege when i run vlc from the terminal
[php]X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
[/php] 

But it so happens that when i switch my window manager to metacity it plays vidoes just find. btw when i have beryl on the only way for me to see play videos is with mplayer by putting this codec X11( XImage/shm )to make it able to go full screen i had to add this to my Mplayer-config: zoom=yes in the end i found wierd how my Mplayer-config looks all thought im a newby in the linux comminty. this is how it looks after adding the line in the bottom: 
[php]
# Write your default config options here!

zoom=yes
[/php]
 
Any help at with this problem i would gladly apreciate thanks

---

