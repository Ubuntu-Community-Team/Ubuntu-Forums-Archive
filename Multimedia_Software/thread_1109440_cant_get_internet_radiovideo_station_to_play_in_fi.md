---
title: "cant get internet radio/video station to play in firefox"
date: 2009-03-28
forum: Multimedia Software
---

### Post by snypercore on 2009-03-28
i just reinstalled the new ubuntu beta today after not using ubuntu for a while and my problem is when trying to to view/listen to this internet radio station
[http://www.phatbeats.co.uk/drumandbass_studio/](http://www.phatbeats.co.uk/drumandbass_studio/)
FF says it needs the MMS plugin, i have read many posts on the forums before posting but cant seem to solve it on my own.
so far ive tried to install w32codecs and Mplayer with plugin, not sure if either has been installed correctly as im a beginer at ubnuntu still by the way :)

thanks

---

### Post by PhrankDaChickenGeek on 2009-03-29
If you can get the MMS stream link, you can copy and paste it into VLC media player to stream it.
Install VLC (if you haven't)
```
sudo apt-get install vlc
```

Open VLC, and go to "Media -> Open Network..." and paste the URL into the address box, then hit play.

You can try Firefox Extension "mediaplayerconnectivity" to automate this proccess

---

### Post by jo4hnc on 2009-03-29
You might try going to Add/Remove and look for GStreamer plugins for mms wavepack quicktime, etc..

Not sure if will solve the problem but it's worth a try.

---

### Post by snypercore on 2009-03-29
ok thanks for the replys but:

when entering the URL which is [http://www.phatbeats.co.uk/drumandbass_studio/](http://www.phatbeats.co.uk/drumandbass_studio/) and obviously links you to the page in which the media player is on not the actual URL of the streamed video it doesnt work in VLC n i cant seem to get any other URL for the vid


and when i search GStreamer in add/remove it find nothing and i have selected all available to

---

### Post by jo4hnc on 2009-03-29
> **snypercore said:**
> ok thanks for the replys but:




and when i search GStreamer in add/remove it find nothing and i have selected all available to

Did you look in Synaptic?

---

### Post by snypercore on 2009-03-29
> **jo4hnc said:**
> Did you look in Synaptic?


just did and installed every plugin i could see on the list lol, still nothing :( .

---

### Post by jo4hnc on 2009-03-29
I just tried the site. It didn't work for me either and provided the message, "Could not open the file, you may not have permission to open the file". When the player opens it simply shows a box with a red X. I don't think that the problem is with your computer, I think that it's the website. Garage TV worked just fine. Dance TV worked fine as well.
You may want to check with the web site to see if the problem is actually on their end. Maybe they're not streaming Drum Beats at this time.

---

### Post by snypercore on 2009-03-29
hmm see when i try the other ones (garage/dance) i still get the FF search for MMS plugin prompt and then nothing.

---

### Post by jo4hnc on 2009-03-29
Hmmmmmmm indeed. I've run out of ideas of my own. I did a search of the forum and found this How-to.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=streaming+video+problem+firefox](http://ubuntuforums.org/showthread.php?t=766683&highlight=streaming+video+problem+firefox)

Hope it helps.

John

---

### Post by PhrankDaChickenGeek on 2009-03-29
Install VLC and use this addon:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Set it to use VLC for all players - /usr/bin/X11/vlc

Looks like you might have to be logged in to listen to some content, although the above worked for me

---

### Post by snypercore on 2009-03-29
> **PhrankDaChickenGeek said:**
> Install VLC and use this addon:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Set it to use VLC for all players - /usr/bin/X11/vlc

Looks like you might have to be logged in to listen to some content, although the above worked for me

ok that worked for the video i just get no audio but im not sure if thats the website or me, so ill have a look and see if i can solve that and post back but thanks for the help.

---

### Post by trueno on 2009-04-06
This worked for me for all UK radios such as heart and kiss...

I installed the codecs available with this install manager:

Automatix install manager: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Instructions
------------

1. Add this to synaptics:
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
2. Install automatix2
3. After installation you should see a new entry in your menu for automatix2, so start it and install "Ubuntu Restricted Extras and Multimedia Codecs"
4. Last install "W32-DVD Codecs"

Now go to FF and hopefully the internet radio now works.

---

### Post by markbuntu on 2009-04-07
That station works for me with Totem/gstreamer plugins.

---

