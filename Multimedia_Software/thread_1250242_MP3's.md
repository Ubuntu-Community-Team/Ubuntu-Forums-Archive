---
title: "MP3's"
date: 2009-08-26
forum: Multimedia Software
---

### Post by tienigami on 2009-08-26
I recently switched from XP to Ubuntu. I put a new, larger hard drive in along with the switch and took my old hard drive and made it into a slave drive. I had a lot of files on the old hard drive and I copied all of the mp3's onto the new drive. 

I then decided I wanted to listen to some music and so I downloaded Exaile music player because a friend of mine who had been using Ubuntu for a while uses it. When I try and play music in Exaile or Rhythmbox they can recognize that there are mp3's to play, the titles are there, but when I double click to play something it just doesn't play. (Amarok just doesn't open when I click on it in Applications>Sound & Video)

Next I tried to just open the songs with whatever Ubuntu had as its default, which turned out to be MPlayer Movie Player. They can not be played and there is a pop up message saying

'An error occured

Failed to connect stream: Invalid argument'.

And that's what's going on. If you can help, that'd be great.

---

### Post by x33a on 2009-08-26
you probably are missing some gstreamer plugins.

first, try playing the mp3s in vlc, if it plays them well, we'll try to fix the plugin issue.

---

### Post by HappyFeet on 2009-08-26
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by caravena on 2009-08-26
You on repository universe and multiverse update list of package and intall 

$sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3

---

### Post by tienigami on 2009-09-05
Alright. I've done all of what you've said and now have come across more inconsistent problems. I've been playing my music in Rhythmbox (because exaile really confused me), and it works the majority of the time, although every so often it just stops and I have to restart and then it'll play music again.

The same is true of YouTube, which works a lot of the time but sometimes doesn't.

Thanks a lot though, inconsistent music is better than a silent world.

---

### Post by tienigami on 2009-09-08
Bump? Help please? Youtube died on me... It plays the video but is muted.

---

