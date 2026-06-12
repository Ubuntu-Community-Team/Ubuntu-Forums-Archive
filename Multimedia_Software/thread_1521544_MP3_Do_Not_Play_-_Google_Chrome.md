---
title: "MP3 Do Not Play - Google Chrome"
date: 2010-06-30
forum: Multimedia Software
---

### Post by nnard1616 on 2010-06-30
Hello all,

I am just reporting something weird I have been experiencing, of which I have a "simple" solution (I am running Lucid Lynx, 10.04).

About a week or so ago, I started having problems with Rhythmbox playing music(same with other music players, such as banshee, etc.)  Every so often, when I clicked on a song to play, it just locked up, and would crash.  This didn't occur 100% of the time, usually a restart would fix the problem momentarily.  Until recently, however, I discovered something that seems to be the source of the problem.  

The music player with which I am playing my music with only locks up if, and only if, I start up the program <<with>> a Google Chrome window open.  After pressing play, when a chrome browser window is open upon startup of the music player, the application remains frozen, until I close the chrome web browser.  Upon closing the chrome browser, the music starts playing. 

If I open the music player before opening a chrome web browser, the music player works just fine, and continues to work fine after pressing play and then opening a chrome web browser.  


Not sure what's with this, but it seems minor to me (and I am a linux noob), so I am not gonna pursue trying to fix it.  However, I felt I should document this "bug", for whoever experiences this weird thing or whoever is interested in trying to find a fix.

Laterz

---

### Post by ofir_k on 2010-07-07
Laterz, you are my angel!

I searched for a reason why Banshee crashes when I try to play music. I didn't think that Chrome can prevent Banshee from playing music.

Anyway, the solution is:
[LIST=1]
[*]Open Banshee
[*]then, Open Chrome
[/LIST]

---

### Post by Yellow Pasque on 2010-07-07
@Laterz: Chrome is an ALSA app, and is probably grabbing your sound device directly, locking out pulseaudio and all the apps that use it. Solution is to route ALSA apps through pulseaudio so everything mixes properly: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816) I'm not sure this fix works too well with Kubuntu/KDE though.

---

