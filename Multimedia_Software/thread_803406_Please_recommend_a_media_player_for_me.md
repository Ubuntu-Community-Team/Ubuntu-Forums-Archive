---
title: "Please recommend a media player for me"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Jiawen on 2008-05-22
I want to find a media (music) player that matches my needs. I need one that:[LIST]
[*]Is stable. Very important -- I don't want my player to crash out on me, or to crash my system. 
[*]Has intelligible playlist management. I want playlists where I can start a new list, add a bunch of things to it, then save the list. Like XMMS, in other words. 
[*]Can handle UTF-8 characters. I have a lot of music in Chinese, with both GB2312 and Big-5 data. I want to be able to see the Chinese characters any time I look at them (file navigation, playlist view, pop-up if any, etc.), not garbage. 
[*]Can manage a large collection of MP3s. In "manage" I include tag editing and display, and hopefully album covers. 
[*]Allows shuffle and repeat play.
[*]Isn't a resource hog. This kinda goes along with the "not crashing" thing, but it's important enough to note.  
[/LIST]All the players I've tried so far -- Amarok, Banshee, Beep, Exaile, XMMS, VLC, Rhythmbox & Totem -- have failed on one or more of those counts. (I will detail the ways in which they have failed if anyone wants to know.) Does anyone know a player that works on all those counts?

---

### Post by T-Virus on 2008-05-22
Well, I think Amarok is just right for your needs... You can try Songbird if you haven't yet.

[http://developer.songbirdnest.com/](http://developer.songbirdnest.com/)

---

### Post by Jiawen on 2008-05-22
As I said, Amarok fails several of the tests. It crashes; its playlist management is too complicated for my purposes; and is a resource hog. I seem to remember problems with Chinese characters, too.

Is there a .deb of Songbird anywhere?

---

### Post by Znort_Ubern00b on 2008-05-22
try to download .deb package from here [http://www.getdeb.net/app.php?name=songbird ]("http://www.getdeb.net/app.php?name=songbird")

install .deb package using the following command

sudo dpkg -i *.deb

---

### Post by Jiawen on 2008-05-22
Actually, I tried using it from the .zip file, and it worked, but there is apparently no codec available for Songbird to play MP3 files under Linux. So that is a no-go.

Can anyone suggest some other media players that meed my needs?

---

### Post by L14UX_1NS1D3 on 2008-05-22
If you want something simple I recommend Rhythembox. It comes preinstalled on ubuntu. personally I use amarok, but I can understand how amarok might give a few hiccups. Rhythembox is will handle playlist creation and will work seamlessly with a MP3 player if you have one. I don't know if it will be able to decode foreign characters. you might be able to install support for other languages.:guitar:

---

### Post by 4tro on 2008-05-22
> **Jiawen said:**
> Actually, I tried using it from the .zip file, and it worked, but there is apparently no codec available for Songbird to play MP3 files under Linux. So that is a no-go.

Can anyone suggest some other media players that meed my needs?


[http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer](http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer)

read this to set up gstreamer, mp3 support in gstreamer is easy =)

sudo apt-get install gstreamer0.10-fluendo-mp3

---

### Post by Jiawen on 2008-05-22
> **L14UX_1NS1D3 said:**
> If you want something simple I recommend Rhythembox. It comes preinstalled on ubuntu. personally I use amarok, but I can understand how amarok might give a few hiccups. Rhythembox is will handle playlist creation and will work seamlessly with a MP3 player if you have one. I don't know if it will be able to decode foreign characters. you might be able to install support for other languages.:guitar:As I said, *I've already tried* Rhythmbox and it doesn't pass my test. (For the record, its handling of Chinese characters is horrible, its playlist management is excessive for my needs and its record album handling is also less than what I want.) 
> **4tro said:**
> [http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer](http://publicsvn.songbirdnest.com/wiki/SettingUpGStreamer)

read this to set up gstreamer, mp3 support in gstreamer is easy =)

sudo apt-get install gstreamer0.10-fluendo-mp3Thank you for the pointers. I've now got Songbird playing mp3s; I'll try it for a while and see how it works. (First impressions: I'd rather have a GTK interface, and the playlist management is a little cumbersome, but still better than Rhythmbox, Banshee or Amarok. It handles Chinese characters a little strangely -- it seems to alphabetize them both before *and* after the Latin characters -- but at least it displays them properly.) Thanks again for the help.

---

### Post by esteckis on 2008-05-22
You could also try Exaile.

---

### Post by Xiong Chiamiov on 2008-05-22
Quod Libet is kinda nice, but I won't use any player that doesn't allow me to separate out compilation albums (eg, anything but amarok).

I'm curious about your amarok problems.  It never crashes on me, and, though I am on KDE, it's not a resource hog (it caches far more memory than most apps, but that's the way memory management on Linux works).  And as far as complicated playlists?
> 
I want playlists where I can start a new list, add a bunch of things to it, then save the list.

Add things to playlist, select all, right-click -> save as playlist.  If you've already got one going, just drag 'em into it in the playlists tab.  Is that what you were meaning, or were you going about it some utterly complicated way?

---

### Post by Jiawen on 2008-05-23
> **esteckis said:**
> You could also try Exaile.Now this is just getting silly...
> **Xiong Chiamiov said:**
> Quod Libet is kinda nice, but I won't use any player that doesn't allow me to separate out compilation albums (eg, anything but amarok).

I'm curious about your amarok problems.  It never crashes on me, and, though I am on KDE, it's not a resource hog (it caches far more memory than most apps, but that's the way memory management on Linux works).  And as far as complicated playlists?

Add things to playlist, select all, right-click -> save as playlist.  If you've already got one going, just drag 'em into it in the playlists tab.  Is that what you were meaning, or were you going about it some utterly complicated way?I hadn't tried Quod Libet. I'll do that now. Thanks for the pointer.

I don't remember what my specific problems with playlists in Amarok were, to be honest. It's been a year or so since I gave up on it, and I don't have any bookmarks relating to that problem.

Just the Chinese character problem and the instability (and yes, it is definitely unstable on my system -- I remember it freezing my desktop once or twice) are enough for me to not be interested in it.

---

### Post by Xiong Chiamiov on 2008-05-23
Hmm, I'll have to find some chinese music to test it out on.  It's handled kanji just fine, though I must say it doesn't stay that way for long (since I can't read kanji).

---

### Post by movd on 2008-05-23
@ Jiawen

I know you are not completely happy with any of the players, but you have to use something in the time being.  So which is your favorite out of the ones you have tried? I too am trying to find the perfect one for myself.

---

### Post by Jiawen on 2008-06-08
For the time being, I'm still using Banshee. It gets closest to ideal (while still being far from it). I tried Songbird, but it has too much stuff for my purposes. (I don't, for example, want my MP3 player to have an integrated web browser.)

---

