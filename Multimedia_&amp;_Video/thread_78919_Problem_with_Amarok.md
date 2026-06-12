---
title: "Problem with Amarok"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by ziobilly on 2005-10-19
After installing Breezy with Amarok 1.3, when I try to play a Mp3, Amarok quit. I can't understand why. Any idea?

---

### Post by stuporglue on 2005-10-19
Did you install the gstreamer mp3 plugins? I think it might be gstreamer0.8-mad.

If that doesn't work, try running it from the command line, it'll probably spit out some more information for you.

---

### Post by ziobilly on 2005-10-19
Everything installed. If I start it from the command line I receive that:

 X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x4000037


I can't understand it. What does it means? What can I do?

---

### Post by skoal on 2005-10-19
Everything installed? Did you configure the engine though in Amarok settings? I use xine engine myself. For some reason, I got that weird "this engine cannot plae mp3's" too until I switched to either esd or xine, I think...

By the way, launching amarok from a term will give you such an error.  I think it has something to do with running in a systray and checking it's PPID, which in this case isn't the root window but a bash session.

\\//_

---

### Post by xwm on 2006-09-14
Hey,

 I'm a new Ubuntu user. I've just installed amarok and when I try to listen to the musics in my Collection...well I press play and all the tracks are played in seconds.... I can't listen any music...

 May someone help me?????:roll: :( :mad: #-o

---

### Post by timfitz on 2006-09-14
xwm, I am getting the same thing too.

I think I have gstreamer installed, does anyone know how I could tell?

---

### Post by xwm on 2006-09-15
Well...

 Iknow I have gstreamer08.mad installed........:( :confused: :frown: :confused:

---

### Post by Aravind Kumar on 2007-04-02
I you use gstreamer then install the following plugin and start a new session. It worked for me.
gstreamer0.10-fluendo-mp3

---

### Post by Juremah on 2008-04-13
Hello..i'm  new user of ubuntu..i'm having some problems with amarok, i want to add some  music to the collection, but when i try that, the program automatically add a nem folder in my music documents...](*,)](*,)what can i do??? :confused:

---

### Post by nickdngr on 2008-04-13
I'm having the same issue. it happened after i updated Amarok today (13 April). 

The output of it is as follows:

abel@imogen:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8365bb8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8365bb8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

Basically Amarok loads perfectly, but once I hit play, it gives me the OSD and never starts playing the track. Locking it up, so i have to kill the process. I've seen several people with the same problem, but no one posting the output. Any ideas on a fix anyone?

---

### Post by nickdngr on 2008-04-14
ok...i woke up this morning feeling a little enthused and did the following:

sudo apt-get remove amarok
sudo apt-get autoremove amarok
sudo apt-get install amarok

now, it doesn't load...argh. i'll work on it more after work.

---

### Post by nickdngr on 2008-04-14
I know I know I know, i'm thread-whoring....but I did fix the issue.

Basically, I just removed amarok, rebooted and reinstalled. That took care of the problem and I should have thought of it earlier. Maybe it will work for someone else.

---

### Post by Jonne on 2008-04-14
I've seen Amarok do that for me too, sometimes, but just killing it (and all related processes) and restarting it usually fixes the problem.

Maybe it has to do with my music being on a cifs share or something.

---

### Post by Juremah on 2008-04-15
I've fixed the first problem,now there's another one..when i try to add music to my collection, i'm noticed that the files can't be organized..and i don't understand why...help?:confused:

---

