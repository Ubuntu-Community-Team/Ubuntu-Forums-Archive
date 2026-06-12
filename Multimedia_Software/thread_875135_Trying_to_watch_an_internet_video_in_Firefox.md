---
title: "Trying to watch an internet video in Firefox"
date: 2008-07-30
forum: Multimedia Software
---

### Post by seamustry on 2008-07-30
I'm using Ubuntu hardy and latest firefox.

Usually all videos work but there is one that just won't work (i know for sure that the video is OK because i can see it in windows)...i have ubuntu restricted extras and i tried vlc player with no results.

The link for the video is: [http://idesitv.com/ibnenglish.php](http://idesitv.com/ibnenglish.php)

can someone try it out and help me as to how i can watch this video?

---

### Post by sisco311 on 2008-07-30
works for me with mozilla-mplayer

---

### Post by seamustry on 2008-07-30
hey i got the mozilla-mplayer through synaptic and now the audio is coming but there is no video, even in fullscreen...do i need any other plugins for that?

---

### Post by sisco311 on 2008-07-30
try to change the video output:
```
gedit $HOME/.mplayer/config
```and add this line:
```
vo=xv,x11
```or (if the desktop effects are enabled)
```
vo=gl2,gl,xv,x11
```EDIT:You can change the video output from the gui:
[http://mplayerplug-in.sourceforge.net/shots.php](http://mplayerplug-in.sourceforge.net/shots.php)

---

### Post by seamustry on 2008-07-30
ok so i've tried all the video output choices but nothing shows the video...and the right click menu doesn't show up also (i opened up the main application and changed the video output there)

---

### Post by tuxxy on 2008-07-30
Runs fine here too with mplayer codec I think

---

### Post by seamustry on 2008-07-30
are you watching in browser or did you get the mms:// from the page source?

i got the page source and tried to play it in mplayer and it's working but the video is really bad (seizure inducing :( )

i really wanted to be able to play it in firefox...any suggestions? what codecs do you have?

---

### Post by seamustry on 2008-07-31
OK i got it working now thanks (the website i wanted to watch was preventing right clicks so i went to another website and did the mplayer configuration there)

:)

---

### Post by Twlightz on 2008-07-31
I have a questions about Videos. I used the "how-to" to install Gnome Mplayer etc. and now everything works but when I go to the following link, the resolution was much lower than it was on my XP:

[http://broadband.nba.com/cc/playa.php?content=video&url=http://boss.streamos.com/wmedia/nba/nbacom/summer_league/top10_plays_rmr_summerleague_080730.asx&video=blank](http://broadband.nba.com/cc/playa.php?content=video&url=http://boss.streamos.com/wmedia/nba/nbacom/summer_league/top10_plays_rmr_summerleague_080730.asx&video=blank)

However, from the same website I picked another video and the resolution looked much better:

[http://broadband.nba.com/cc/playa.php?content=video&url=http://boss.streamos.com/wmedia/nba/nbacom/press_conf/pc_usab_080731.asx&video=blank](http://broadband.nba.com/cc/playa.php?content=video&url=http://boss.streamos.com/wmedia/nba/nbacom/press_conf/pc_usab_080731.asx&video=blank)


Does anyone know how I can improve the resolution on these videos? 

Again, I want to emphasize that I used the "how-to", so everything works fine except for this specific format. Also, most videos that need WMP play with low resolution.

---

