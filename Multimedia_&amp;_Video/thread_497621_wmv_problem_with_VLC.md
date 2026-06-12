---
title: "wmv problem with VLC"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by tkrisz on 2007-07-10
Using MediaPlayerConnectivity i tried to play  wmv files with VLC. (Many thread says, that it plays such files without any problems.) Problem: no enjoyable video, btw no problem with audio (attached screenshot) 
I think i installed all the needed packages.
What can the problem be? Is it a setting?

---

### Post by tgoose on 2007-07-10
How fast is your connection? It looks like it's streamed, and if you don't have a very fast Internet connection the video will suffer. Although, really it should suffer more gracefully than that if te audio is fine.

---

### Post by tkrisz on 2007-07-10
I think there's no problem with my internet connection:

A result of a speedtest: 	
   bits per second  	 (bytes per second)
Download speed: 	3,250,320 	(406,290)
Upload speed: 	423,608 	(52,951)
Surfspeed Average: 	132,137 	(16,517)

I tried the mplayer plugin before, and it sometimes gave me a video, altough sometimes there it was squared, too. (much better than this one). But sometimes it gave only audio, so i thought to try VLC.

---

### Post by Bablefish on 2007-07-10
Simple fix download,install and run Automatrix  [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by tkrisz on 2007-07-10
Tried Automatix, no improvement.
totem now does not even play the sound. (complains now about a wc1 codec), kaffeine only sound after a delay, vlc shows only these colorful squares, sound ok. mplayer is the best, now less unwanted squares (that was experienced even before the automatix), sound ok, but video clugs up. amplayer gui produces an error message and does not even start.

---

### Post by Matakoo on 2007-07-10
Do you get that all the time and no matter what file? I get that occasionally, and it is only in some specific files and briefly at that. I get the squares for a few seconds and then it's back to normal video. Weirdly enough, I get that no matter what player I'm using (VLC, Kaffeine, Mplayer, whatever) if I view the file in the standalone player. If viewed through a Mozilla-plugin, the artifacts are gone.

If you get that all the time, I'm wondering if the w32codecs are properly installed.

---

### Post by tkrisz on 2007-07-10
You are right, i tested some wmv's and all worked.

I would be glad if some people were test this site's embedded video (video length about 2 min) and write here the experiences. It's about a mountain-bike race, quite good music and some Hungarian sentences about the race. 
[http://www.nemzetisport.hu/Stream_player_index.php?stream_id=2286](http://www.nemzetisport.hu/Stream_player_index.php?stream_id=2286)

---

### Post by Matakoo on 2007-07-10
> **tkrisz said:**
> 
I would be glad if some people were test this site's embedded video (video length about 2 min) and write here the experiences. It's about a mountain-bike race, quite good music and some Hungarian sentences about the race. [http://www.nemzetisport.hu/Stream_player_index.php?stream_id=2286](http://www.nemzetisport.hu/Stream_player_index.php?stream_id=2286)



Works fine here, using Firefox + mplayer-plugin + the w64codecs. It refused to play at all at first, but since I can't read Hungarian I don't know if it's because the site was overloaded or whether me forcing Firefox to identify itself as Internet Explorer is what did the trick.

Still, the video played as it should. It looked the way it should and no problems with sound either.

---

### Post by tkrisz on 2007-07-11
Thx, that inspired me to search more intensively the error in my settings.
I've found out the problem with my mplayer engine. It came with a too low cache setting (128kb). Do someone know how to set systemwide the mplayer cache?
Still no idea what is wrong with my xine engine (no video output, sound is ok).
It would be nice to know, but anyway, finally i have a solution. :)

---

