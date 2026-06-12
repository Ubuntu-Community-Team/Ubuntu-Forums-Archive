---
title: "making totem default within firefox and for all video"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by alexvd on 2007-01-30
Hi apologize if this was posted somewhere already but I just can't seem to find it.

I am running 6.10 with firefox 2.0.1 .    Initially I had just totem installed for all media however I needed to view .wmv and other formats.  So I used automatix to get all the additional codecs. 

My issue was then trying to open .wmv within firefox.  So I installed xine.  I also messed with some of the settings in firefox options config.  It works but its a pain because I get a dialog box that opens and asks me the application to view the file (xine default) every time.  Even though I have selected do this automatically.

I am aware that their is a gstreamer and gxine.   I believe what I want is to have totem open everything either in firefox or independent for full movies and clips and use xine as backend.  

What do I need to do set this up.   It appears to work for everything except wmv9 or 10.  I think.


What logs or configuration do I need to post or change?

---

### Post by alexvd on 2007-01-30
So  no one is using Totem as the default player for all videos?

---

### Post by RomeReactor on 2007-01-30
Hi. I use Totem to view most of my videos; make sure you have Mozilla-Totem and Totem-Xine, and that you don't have **any** other firefox video plugin installed and search for w32codecs. Look at my post in [this]("http://www.ubuntuforums.org/showthread.php?p=2048056") thread for more details.

EDIT: I haven't used Automatix, but too many people seem to have mixed results with it; hrrmmm...

---

### Post by alexvd on 2007-01-30
Hi I believe I have those, however where do I need to check to see if they are installed?

Do I check in synaptic 

Is thier a command I can run.

Should I look in a folder?

Do I check the config files for firefox?

---

### Post by RomeReactor on 2007-01-30
Look for "mozilla" in Synaptic and see what's installed; make sure there's no "mozilla-mplayer", "mozilla-plugin-vlc",  or "mozilla-helix-player". If there are, uninstall them.

---

### Post by alexvd on 2007-01-31
None of these are installed currently.  

I noticed something called mozplugger is not installed right now.  It says this launches external viewers within mozilla.

---

### Post by alexvd on 2007-01-31
I am kinda of suprised to not be getting more responses.  Thier a 30 page threads on totem vs mplayer and vlc.

I know I have seen many posts saying I use totem fine for all my videos.  

All I want to do is just use totem.  Thanks for all the help so far.

---

