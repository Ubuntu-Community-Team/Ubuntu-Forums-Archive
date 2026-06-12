---
title: "How to launch &amp; control videos from PC monitor to TV screen"
date: 2009-02-18
forum: Multimedia Software
---

### Post by SteveDee on 2009-02-18
This is about playing videos on your TV from your computer, when you don't have a clear view of your TV screen from your computer/monitor. I know I'm not alone in wanting to do this: [http://ubuntuforums.org/showthread.php?t=1013366](http://ubuntuforums.org/showthread.php?t=1013366)

I have been using VNC to allow me to launch videos on the TV for a few weeks, but this is not ideal as the combination of video and VNC seems to keep my cpu occupied pretty much 100% of the time.

You can launch MPlayer from command line to run on the second display like this:-
   **mplayer {path+filename} -display :0.1**

I needed a GUI way to do this, and one solution was to create a Nautilus script (see attached). 

This allows me to simply select the video in Nautilus, right click, then run the PlayMovie script.

MPlayer then runs in full screen mode on the TV, and you can use the following keys to control it:-
  <space bar>    pause/run
  <right arrow>  skip ahead
  <left arrow>   skip back
  <ESC>     close MPlayer

If you want to use this script, just add it to your nautilus-scripts directory (e.g. /home/steve/.gnome2/nautilus-scripts) then make PlayMovie.sh executable (i.e. right click the file > Properties > Permissions > Execute).

---

