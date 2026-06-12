---
title: "Need help with Songbird"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by tstormdamage on 2007-08-25
As recommended as an iTunes alternative, I've downloaded Songbird. The first thing I've noticed when I've attempted to  import  songs into my music library is that songs purchased from the iTunes Music Store do no appear. Secondly, each time I go to play an audio track, I get the message "Error". Any suggestions.  I'm a complete newbie to Linux.

---

### Post by nkessler2000 on 2007-09-09
AFAIK you can't play iTunes Store bought tracks in any Linux media player. They just don't support the DRM that iTunes uses. Now I hear there are ways to strip the DRM, but I don't know much about that. 

As for files not playing at all... well have you installed mp3 support? It doesn't come standard with Ubuntu because mp3 isn't a free codec. It's easy enough to install though. Try looking at the Ubuntu Guide: [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by j3ro on 2007-10-17
I had the same problem with playback, this seemed to fix it for me though:

sudo aptitude install gstreamer0.10-plugins-ugly

---

### Post by lunamystry on 2007-10-17
I can't find songbird after installing it using instructions from psychocats

> Installing Songbird on Ubuntu

Here's a little script to install the latest Songbird (which, right now, is version 0.2.5, so don't expect much) on Ubuntu. If 0.2.5 is no longer the latest version, please let me know in this thread. 

Installing Songbird
Step 1: Download this script to your desktop. 

Step 2: Paste these commands in the terminal:
cd ~/Desktop
chmod +x installsongbird.sh
./installsongbird.sh 

That's it. Keep in mind that the launcher for Songbird will be the word Songbird with a capital S.

I am running gutsy KDE and also have gnome desktop installed. Songbird does not appear in the menu, and when i run try to run Songbird i'm told the command does not exist. How do I install Songbird for Gutsy?

---

