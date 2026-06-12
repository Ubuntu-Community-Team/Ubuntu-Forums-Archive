---
title: "Streaming Video"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by CheeseQueen452 on 2006-11-29
The streaming videos at etonline.com & news.yahoo.com don't work. What can I do?

---

### Post by CheeseQueen452 on 2006-11-30
Anyone?

---

### Post by CheeseQueen452 on 2006-11-30
A little help, please? 

I installed real player & mplayer, but it still doesn't work.

---

### Post by madmetal on 2006-11-30
try to install MediaPlayerConnectivity for FireFox and give a try to watch the videos with VCL player..

---

### Post by CheeseQueen452 on 2006-11-30
Where do I find that?

> **madmetal said:**
> try to install MediaPlayerConnectivity for FireFox and give a try to watch the videos with VCL player..

---

### Post by madmetal on 2006-11-30
MediaPlayerConnectivity 
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
and you can get VLC from synaptic (altough i think needs some repos enabled)

---

### Post by crazedgremlin on 2006-11-30
How about playing videos on CNN?  That doesn't work for me and it makes me angry.. rawr

um...

It says something like, "Couldn't find windows media player."

I find that very upsetting because I know that I could play the file if I could bypass the wmp checkpoint thingy.

---

### Post by CheeseQueen452 on 2006-11-30
Thanx. I'm a little disappointed in how it works, though. Is there any way I can get the videos to play in the browser like they're supposed to?

> **madmetal said:**
> MediaPlayerConnectivity 
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
and you can get VLC from synaptic (altough i think needs some repos enabled)

---

### Post by CheeseQueen452 on 2006-12-01
The MplayerConnectivity extension is not working that well for me. Is there anything I can do to play the videos in Firefox as they normally should?

---

### Post by CheeseQueen452 on 2006-12-01
Any help would be appreciated!

---

### Post by CheeseQueen452 on 2006-12-02
Anyone?

---

### Post by dalani on 2006-12-02
Did you try realplayer for linux? I installed recently on my machine though I haven't been able to find a video to view with it yet.

---

### Post by CheeseQueen452 on 2006-12-02
Yes. As I said earlier in this thread, it didn't help. The videos at etonline.com don't work. Also, the videos at news.yahoo.com don't work even though I have mplayer installed.

> **dalani said:**
> Did you try realplayer for linux? I installed recently on my machine though I haven't been able to find a video to view with it yet.

---

### Post by dvarsam on 2006-12-02
> **madmetal said:**
> MediaPlayerConnectivity 
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
and you can get VLC from synaptic (altough i think needs some repos enabled)

I managed to make "Media Player Connectivity" work for the following Sites:

2. [http://news.yahoo.com/](http://news.yahoo.com/)

3. [http://www.pixar.com/featurefilms/ts/theater/index.html](http://www.pixar.com/featurefilms/ts/theater/index.html)

The #1. ([http://etonline.com/](http://etonline.com/)) was NOT successful!

What I did was the following:

1. I visited the above Site #3 & opened a link containing a "Video Stream" window.

2. I right-click on the Video & select "Media Player Connectivity\Configure...".

3. I change the following:

a. Real Media          (from the default "/usr/bin/X11/gmplayer" to "/usr/bin/vlc")
b. Windows Media       (from the default "/usr/bin/X11/gmplayer" to "/usr/bin/vlc")
c. QuickTime           (from the default "/usr/bin/X11/gmplayer" to "/usr/bin/vlc")
d. Playlist (pls/m3u)  (from the default "/usr/bin/X11/gmplayer" to "/usr/bin/vlc")
e. MP3/AAC Files       (from the default "/usr/bin/X11/gmplayer" to "/usr/bin/vlc")
f. Wave/Midi/Au/Aif    (from the default "/usr/bin/X11/gmplayer" to "/usr/bin/vlc")
g. OGG/Theora          Same
h. Flash               Same
i. NullSoft Video      Same
j. Shockwave           Same
k. Authorwave          Same
l. DivX                Same
m. Podcast             Same
n. ViewPoint           Same

4. Then I double-clicked on the Video Stream & I could then see it inside my VLC Player.

I don't know how I could make the case #1 to work though...

Thanks.

---

### Post by drphilngood on 2006-12-02
Try this: [MultimediaCustomizationGuide]("http://doc.gwos.org/index.php/MultimediaCustomizationGuide#SECOND_STAGE_:_MULTIMEDIA_AND_PROPRIETARY.2FRESTRICTED_FORMATS").

Hope this helps.

---

### Post by CheeseQueen452 on 2006-12-02
I already tried the MediaPlayerConnectivity extension, & although I'm able to watch the videos, it doesn't work the way I want it to. I want to play the videos in Firefox, as I should be able to. I'm not sure why the extension doesn't work for you, maybe you need to change the settings?

> **dvarsam said:**
> The Media Player Connectivity does NOT also work for me either!!!

I tried visiting the following Sites (some of which you suggested):

1. [http://etonline.com/](http://etonline.com/)

2. [http://news.yahoo.com/](http://news.yahoo.com/)

3. [http://www.pixar.com/featurefilms/ts/theater/index.html](http://www.pixar.com/featurefilms/ts/theater/index.html)

And NONE of them works after the "Media Player Connectivity" was installed...

I have an Ubuntu v6.10 installation & it doesn't work.

You have to provide more info on how you put it to work on your Ubuntu.

Thanks.

---

### Post by CheeseQueen452 on 2006-12-02
It didn't work. Thanx, anyway....

> **drphilngood said:**
> Try this: [MultimediaCustomizationGuide]("http://doc.gwos.org/index.php/MultimediaCustomizationGuide#SECOND_STAGE_:_MULTIMEDIA_AND_PROPRIETARY.2FRESTRICTED_FORMATS").

Hope this helps.

---

### Post by dvarsam on 2006-12-03
> **CheeseQueen452 said:**
> I already tried the MediaPlayerConnectivity extension, & although I'm able to watch the videos, it doesn't work the way I want it to.

You can't have everything...

> I want to play the videos in Firefox, as I should be able to.

I'm not sure why the extension doesn't work for you, maybe you need to change the settings?

Well playing those from inside Firefox, I would like to do it too!

This was _only_ possible to me in Ubuntu v6.06.

Ubuntu v6.10 is a little bit worse in some things...

But at least I provided you with a workaround to fix this...

It should work in 2/3 of the above links provided...

Thanks.

---

### Post by CheeseQueen452 on 2006-12-03
Well, I guess I'll just have to put up with it until the next release.... IF it gets fixed.

> **dvarsam said:**
> This was _only_ possible to me in Ubuntu v6.06.

Ubuntu v6.10 is a little bit worse in some things...

---

### Post by CheeseQueen452 on 2006-12-23
I installed the mplayer plugin, & I get an error message that says:
> Video codec 'Windows Media Video 9' is not handled. You might need to install additional plugins to be able to play some types of movies
I close the error message, & a minute or so later the video plays!! Any ideas how to stop the error message from popping up?

---

### Post by jake3988 on 2006-12-24
You don't have the required codec.  Find a repository with the w32codecs (find my only thread, someone posted amazing details of how to get them) and you'll be set.

---

