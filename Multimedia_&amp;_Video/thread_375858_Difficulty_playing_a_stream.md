---
title: "Difficulty playing a stream"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by maxwas on 2007-03-04
Hello,

I am trying to open up a stream url to an internet radio station and it does not want to work. The extension is of type .nsc. In Window$, media player is embedding itself into the page, i suspect it may be some sort of flash thingy.

Is there anything on Linux that would play this for me??

If anyone wants to test, the stream url is:
[http://mediaweb.musicradio.com/nsc/PlanetRock_Multicast.nsc](http://mediaweb.musicradio.com/nsc/PlanetRock_Multicast.nsc)

The site url is: [http://www.planetrock.com](http://www.planetrock.com)

(And no im not trying to plug :) )

Many thanks

---

### Post by Spin Doctor on 2007-03-04
Why dont you try to install the streamtuner and xmms application. This will give you massive amounts of live internet radiostations to listen to. I use this all the time! Excellent apps!

Search for streamtuner in your synaptic, which is the directory which lists all the internet radiostations, and XMMS which is used to play the streamed media.

Hope this is a help for ya!

---

### Post by SPr on 2007-03-04
I would like to listen to PlanetRock as well. I've heard it on digital radio here in the UK and they play some excellent music. 

I haven't been able to find anything to play .nsc streams though :(

StreamTuner/xmms looks good but PlanetRock doesn't play on there either.

---

### Post by maxwas on 2007-03-04
Yeah it's a bummer. It is a fab station. I normally listen to it through my cable box at home, but i hate the fact that i am forced to use window$ to listen to it on the PC. 

I have tried streamtuner/xmms and quite a few others with no joy.

:guitar:  :(

---

### Post by Kuoi on 2007-03-05
Hello Spin Doctor ,

Thanks for the streamtuner xmms tip !
Now I can listen to my EBM radios without any error.
Thanks !

Kuoi

---

### Post by GaryUK on 2008-06-14
Dear All,

I have managed to get the Planet Rock stream working in Hardy. I am using the gecko-mplayer plug-in with Firefox 3 - see this thread on how to install [http://ubuntuforums.org/showthread.php?t=661833&highlight=uninstall+flash&page=1]("http://ubuntuforums.org/showthread.php?t=661833&highlight=uninstall+flash&page=1")

All you need to do is to go to the Planet Rock site, click on "Listen Now" and it will detect that you are on Linux but ask you to "Click Here" if you have a compatible music player (which you do have). If you do have the FF mplayer plug-in correctly installed, then mplayer will open and play the stream.

If you wish to play via Streamtuner, then I have found that I can do it in Amarok but first you will need to change the default playback command in Streamtuner (Edit/Preferences and change all "Listen to" options except the Realplayer one) to the Amarok one:

> amarok %q -p

The stream URL I am using in Streamtuner is

> mms://mediasrv-the.musicradio.com/PlanetRock?MSWMExt=.asf

It takes a little while but the stream seems to play from Streamtuner via Amarok. The same set-up also streams Virgin Classic Rock from Streamtuner via Amarok.

I also tried to use Audacious, VLC and mplayer as the playback application for Planet Rock in Streamtuner but none of them worked.

Hope this helps....8-)

Gary.

---

### Post by SPr on 2008-06-19
Rock and Roll. Your God given right to express yourself at 30,000 watts.:guitar:

Long Live Planet Rock :D

---

