---
title: "please suggest any software to download streaming video in ubuntu"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by cyneuron on 2007-07-01
hello there

i have just switched from windows xp. i have got almost all application in ubuntu except one: a streaming video downloader for real media and windows media format. i used to use Net Transport in windows xp.

i use Mplayer in ubuntu. i have nstalled all codecs, and my system is fully updated.

please suggest one. after i get this i will be able to make complete switch over to ubuntu.

---

### Post by snoop on 2007-07-01
Usually there are online things that will let you download streaming video. Ex: google "download youtube video"

---

### Post by wolfen69 on 2007-07-02
Democracy Player is something you might be interested in. for streamed content i use VLC and streamtuner.

---

### Post by Gremlinzzz on 2007-07-02
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

---

### Post by cyneuron on 2007-07-02
thanks to all for replyin 

guys what you are telling is to play the streaming video. thats ok. but i want some software which may allow me to download the streaming video to hard disk. useful in conditions where slow speed connection is the problem or where you want to see the streaming video online. and i am not talking about you tube video. usually real media or windows media format are streamed.

---

### Post by randcoop on 2007-07-05
You can download video streams in real time using mplayer.  Just use the command ```
mplayer -dumpstream -dumpfile "[name of file to create from download]" "[name of streaming url]" 
```

You must use quotes around both names.  

The download will be in real time; so a two hour stream takes two hours to record.

---

### Post by zachthejones on 2007-07-29
Hey, thought I'd add another option to the discussion.  I downloaded the MediaPlayerConnectivity plugin for Firefox to stream video, and it allows you to open streaming files with whatever player you would like. I open it through VLC, and then go to File > Open Capture Device...

Then you select the File tab, and at the bottom (in Advanced Options) you put the URL of the vile you want to download and select the Stream/Save option.  Then click the Settings button for that section and in the new window that opens up, under the Outputs section, select the File checkbox and designate the file name and where you want VLC to put the file. Click OK on that window and then OK on the other one, and it should start streaming it to a file (it didn't play the file for me while it downloaded it, though).  When it was done, I found the file exactly where I had told it to save it, and it played perfectly!

Hope this helps!

---

