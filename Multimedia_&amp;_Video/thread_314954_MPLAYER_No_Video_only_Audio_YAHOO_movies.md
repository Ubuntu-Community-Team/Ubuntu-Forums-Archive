---
title: "MPLAYER No Video only Audio YAHOO movies"
date: 2006-12-08
forum: Multimedia &amp; Video
---

### Post by BionicBigfoot on 2006-12-08
On Dapper 6.06. Installed MPLAYER and no video displays when I visit yahoo.movies.com

I can play movie trailers fine at Apple.com and at Real.com, I can play WMV file formats but not with MPLAYER in the browser.I have all the codecs installed(currently using Firefox, but not 2.0 - using the last version 1.5.3 or something like that and MPLAYER is supposed to work fine with this version, as I checked. I tried the new version of Firefox 2.0 but I had some problems so I switched back to the previous version.

I have searched the forum and I don't really see anything that tackles the issue.

I can try and take a screen grab of what it looks like. Basically there is a gray box where the movie should be playing with the URL in the gray box. Audio works great and it it streams along with no video...

Any help would be appreciated. I am only 2 days old with Ubunto and Linux so you'll have to explain things like I am an idiot.

So far I am loving it.

---

### Post by BionicBigfoot on 2006-12-08
Hmmm. Okay been reading up on MPLAYER 4 hours straight and no one seems to have the same issue? Do you recommend I uninstall it? Is there anything I should be looking at or any codes I can paste that would assist?

---

### Post by dcroal on 2006-12-08
You might want to try a different mplayer video driver. In the mplayer gui right-click on the grey area, choose Preferences, then the Video tab and choose x11 instead of the default. In command line you can do the same thing like:
$ mplayer -vo x11 movie.avi

You could also try reducing your screen resolution via Preferences, Screen Resolution and trying the movie again

---

### Post by HeWhoE on 2006-12-10
I have a similar problem; only I don't even get audio.  I've been using Ubuntu for over two years and have become experienced with it at a user level.  The only way I've gotten yahoo movie trailers (from movies.yahoo.com) to play is by uncommenting the noembed option in the file, /etc/mplayerplug-in.conf, and setting it to 1.  

Open the mplayerplug-in conf file:
```
sudo gedit /etc/mplayerplug-in.conf
```

Uncomment the following line and set the value to 1:
```
noembed=1
```
Commented lines have a pound (#) sign in front of them.  To uncomment, just remove the pound sign.


I also can't change the video settings on yahoo's website to allow me to view the trailers in any other format but wmv.  I'd much rather play the yahoo trailers in quicktime, but the yahoo website always claims that I don't have a quicktime plugin installed.  Quicktime movies play great on apple.com/trailers, but not on yahoo.

---

### Post by frokki on 2007-12-20
I also have this same problem, it appeared in this month. It's not just YAHOO-movies, but every embedded video (except flash) in Firefox.

Thanks for the tip, HeWhoE! Thanks to you I can at least watch embedded media, even though the fix is once again a "bubble gum" -type.

---

