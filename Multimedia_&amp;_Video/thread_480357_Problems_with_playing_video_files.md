---
title: "Problems with playing video files"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by freak_lick on 2007-06-21
Hi,
I have a problem w/ playing video files on Ubuntu 7.04
When i play movie i can see first 5secs and than i see black screen on every player i tried even with VLC.
And when on black screen i hit double-click for full screen i see picture for just 1 sec and again black screen, same happens w/ double-click for reverting to non-full-screen.
I even added repositories from mediabuntu.org and still i have black screen..
Audio is OK.

Plz help..

---

### Post by Gremlinzzz on 2007-06-21
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/Re...t=%28codecs%29](https://help.ubuntu.com/community/Re...t=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.
This works for me you can only use one plugin for online video so uninstall any other plugins

---

### Post by freak_lick on 2007-06-22
thx but i also found out that when i have enabled "Desktop effects" none of the players except Smplayer will play video files..
Is there any bug with "desktop effects" - cuz i found this one...

---

### Post by tylermoody on 2007-06-22
I am running into this too - videos only work when desktop effects are disabled. I am running 7.04 on a Macbook C2D.

---

### Post by Gremlinzzz on 2007-06-22
you will need to change video driver from xv to x11

---

### Post by Gremlinzzz on 2007-06-22
It is a known bug and there is a workaround by changing the video output device on your video player.

    * GStreamer (The default video player in Ubuntu, totem-gstreamer, and any video player that is based on the gstreamer backend)
          o Open a terminal and type "gstreamer-properties". Press Enter.
          o Click the Video tab.
          o Under Default Video Plugin select "X Window System (No Xv)".
          o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
          o Click Close 

    * VLC (VLC is not installed by default; you need to search in the package manager, then install)
          o Start VLC and click on Settings, then Preferences.
          o Expand Video and then expand Output modules. You will notice several options for output device.
          o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
          o Pick X11 video output
          o Click on Save and you are set! 

    * MPlayer (Mplayer is not installed by default)
          o Start Mplayer
          o Right-click on the screen and select Preferences
          o Select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
          o Click Save and restart the program for the setting to take effect.
                + Some users reported that MPlayer may not be able to show videos in full screen. 

    * Xine
          o Start xine
          o Click File, then Configure and then Preferences
          o In experience_level select "Master Of The Known Universe" so that all available settings are visible.
          o Select the tab for video.
          o Under Driver select "xshm".
          o Restart xine.
                + The same process enables Totem that has the totem-xine backend configured.

---

### Post by freak_lick on 2007-06-23
Thanx very much it worked 4 me!!:D

---

### Post by jerrykun on 2007-06-26
hehe this is funny my only problem comes when i have beryl on i found that i cant play videos on my labtop. But if i turn off beryl i can see them in all players.

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

### Post by hedonist on 2007-06-28
HI!](*,)
I m a dapper  user (Kubuntu 6.06). I face the same full screen problem in mplayer and have tried the zoom=yes option in mplayer config file but when the video plays full screen the audio and video go out of sync. Also i m using the x11 Ximage/shm driver. Plz help!!!!!!!](*,)[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by coolen on 2007-09-01
Hey, I'm wondering if you could help me out here.
I'm setting up Feisty on my brother-in-law's laptop. I want things to just work for him, and nicely.
To that end, I've installed Compiz Fusion, and totem-xine (who doesn't love menus and subtitles, eh?).
I'm having this problem whenever I play video. I fixed it in both xine-ui and gxine, but the changes don't seem to be carrying over into totem. I can't find any obvious configuration file, and nothing in gconf-editor. I logged out in the hopes that gnome would reload the backend or something, but alas, to no avail.
I know I'm a centimetre away from solving this. I just need this last piece of the puzzle.

---

### Post by Maeggoel on 2007-09-14
> **Gremlinzzz said:**
> It is a known bug and there is a workaround by changing the video output device on your video player.

    * GStreamer (The default video player in Ubuntu, totem-gstreamer, and any video player that is based on the gstreamer backend)
          o Open a terminal and type "gstreamer-properties". Press Enter.
          o Click the Video tab.
          o Under Default Video Plugin select "X Window System (No Xv)".
          o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
          o Click Close 



Maybe a silly question, but where is the Video tab? I can't find it anywhere in the player.

---

### Post by venator260 on 2007-09-16
I took Gremlinzzz's advice, and it worked. 

I had to restart my computer before it to work. Before I restarted, I had spotty audio, and the video was unviewable.

---

### Post by knowledge_is_power on 2008-03-25
dont know if this is relevant, but i had a problem where video would appear for a very short time, then flicker, then dissapear.  i went into system->pref->multimedia system selector and changed my video out to X window system (no Xv).  this solved problem.  however the xvideo extension will no longer be enabled.  this may cause video to sloww down sometimes, but i havent noticed a difference yet.

---

