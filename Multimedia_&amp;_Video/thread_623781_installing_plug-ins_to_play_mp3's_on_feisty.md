---
title: "installing plug-ins to play mp3's on feisty"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by feargal on 2007-11-26
i've recently changed to ubuntu, now i can't listen to my mp3  music, my computer is never connected to internet. i've a memory stick i use. so far all plugins i've tried aren't accepted. i don't know enough to dive into the software. why won't it work and what can i do? thank you for reading my ambling help message.

---

### Post by nobull on 2007-11-26
Congrats on your recent switch.  There is a restricted package that needs to be installed for mp3 playback.  I would try to get internet access at least until it operates how you want it to.  I believe the package can be found by going to system>administration>synaptic package manager then installing the ubuntu-restricted-extras package.  If the package isn't listed then the mulitverse repository needs to enable by going to settings>repositories then enabling the multiverse in the synaptic package manager.

---

### Post by nickpaton on 2007-11-26
Welcome to the forums and Ubuntu.

In addition to what Nobull has posted, go to Applications >  Add/Remove... 

When open, top right corner, Show: 'All available Applications'

In Search box type gstreamer

Tick the following:
GStreamer ffmpeg video plugin 
GStreamer extra plugins
GStreamer plugins for aac, xvid, mpeg2, faad 
GStreamer plugins for mms, wavpack, quicktime, musepack 

Search and tick:
Ubuntu restricted extras
Install by clicking Apply Changes, agreeing to all messages.  

Close Add/Remove...

This will install most of the audio multimedia plugins you need.

If you need any further information or help please ask us

Nick

---

### Post by Mudit_BITS on 2008-01-25
I too have a similar kinna problem.......I installed exaile player but moment i try to run a mp3 file ....it fades to black and then never responds.....btw im on gutsy gibbon

---

