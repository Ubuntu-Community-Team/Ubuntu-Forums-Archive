---
title: "Console based music players"
date: 2011-03-22
forum: Multimedia Software
---

### Post by cheflo on 2011-03-22
Hello,

I wonder which are the main disadvantages of using console based music players like cmus. I was looking around for reviews and comparisons with GUI music players but didn't find a lot of information which, to me, is a sign that console based players are so much worse off that there is no need to even compare them to their graphical relatives.

However, as I see it, I gain both speed and free up system resources by running a light weight music player in the terminal rather than one with a GUI. Then, I'm not at all very knowledgeable when it comes to audio players and music files so I'm thinking I'm missing something here. But what? Do I lose some tagging functionality, playlist or equalizer options or maybe even sound quality due to different usage of sound drivers or something? Or do people simply stay away from players like cmus just because they can't point and click with the mouse? (I guess it might be hard to get them to work intuitively with USB-attached mp3-players, but that's not a probelm for me.)


Regards,

Joel

---

### Post by andrew.46 on 2011-03-22
Hi Joel,

I agree with you completely although my own personal preference is for MPlayer :).

Andrew

---

### Post by mcduck on 2011-03-22
disadvantages? There are none, apart from missing the obviously graphical stuff like album art etc...

The user interface puts no limitations on sound quality, it's not like the sound processing parts of GUI music players would be in any way related to the graphical user interface. Actually most CLI music players use exactly the same libraries to handle sound production and audio file decoding that tour GUI apps are using.

What comes to playlists, tagging and so on, that simply depends on you getting a music player that has such features. Just like with GUI applications, actually. :D

And my preferred music player? [MPD]("http://en.wikipedia.org/wiki/Music_Player_Daemon"), of course. :D I use [ncmpc++]("http://unkart.ovh.org/ncmpcpp/") as the CLI interface, and [Sonata]("http://sonata.berlios.de/") as GUI interface if I have some friends around who might want to use the music player but aren't comfortable with the ncmpc++ interface.

---

### Post by nothingspecial on 2011-03-22
I like using aliases with mplayer. To play my entire collection on random, I just type ```
ran
```

To enable that, open up your ~/.bashrc with a text editor and put this at the end

```
alias ran='mplayer -quiet -shuffle -playlist <(find -L ~/Music -type f)'
```

That assumes all your music is in ~/Music, also if you have videos in there it will play them too.

or to connect to a stream from my server that I can control through a web interface I just type ```
sq
```

```
alias sq='mplayer http://192.168.1.10:9000/stream.mp3'
```

or to listen to my favourite punk shoutcast radio ```
punk
```

```
alias punk='mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &'
```

That < /dev/null & bit at the end can be appended to any of the aliases, it gives you back control of the terminal.

Don't worry, the -quiet and -really-quiet options suppress output to the terminal,  you can still play it loud.

---

### Post by deconstrained on 2011-03-22
> **cheflo said:**
> cmus
KILL IT WITH FIRE.

Command line is fine, and I use it all the time. But media players for the command line ONLY...booooring.

Set up MPD and you'll have far more choices with how you view, tag, browse and control the playback of your music (hell you can even stream it over a network, natively) because you can take your pick of which client programs to use for interfacing with the daemon. It rarely uses more than 5% of the CPU of the machine on which it runs (an Intel E3200 @ 2.40GHz), and it takes up that much only because I give it a generous read-ahead buffer for extended crossfading.

---

### Post by nothingspecial on 2011-03-22
> **deconstrained said:**
> KILL IT WITH FIRE.

 media players for the command line ONLY...booooring.



I disagree, I want my music straight away. I don't want to have to click this and click that and blah, blah, blah, boring, boring ,boring.

You can use functions in your .bashrc to make use of variables. So all my music is in ~/Music/Artist/Album/Songs

```
ply() { rm ~/tmp.m3u && find ~/Music/"$1" -type f > ~/tmp.m3u && mplayer -quiet -shuffle -playlist ~/tmp.m3u; }
```

That creates a temporary playlist in ~ based on which artist you specify as an argument to ply then plays it shuffled after removing the last temporary playlist.

So you type ```
ply John_Coltrane
``` or ```
ply Grateful_Dead
```
or whatever. Of course speed results vary between Kiss The_Red_Hot_Chilli_Peppers but it depends how fast you can type.

---

### Post by cheflo on 2011-03-22
Wow... a lot of very nice suggestions here. And I definitely like hearing that I don't lose anything apart from the obvious when using the terminal.

It's hard to choose what to use though, I really like all the mplayer commands utilized through the use of aliases, but I think I need to read up some on MPD as well since I dont really know how it works or exactly.

I'm not sure whether I want a front end GUI or not. It's probably nice to have though, especially since I'm not that confident with the command line yet. But still... command line just feels so responsive so I wanna use it all the time.

Right now, I came across two players I have never seen before. [DeaDBeef]("http://deadbeef.sourceforge.net/") which is a foobar clone and [Guayadeque]("http://guayadeque.org/forums/index.php?p=/wiki/page/home") which looks really good as well. I think both can be controlled through the command line as well, but probably not as extensively as mplayer.

But keep the intuitive suggestions coming, I'm learning a lot!

---

### Post by mcduck on 2011-03-22
> **cheflo said:**
> 
I'm not sure whether I want a front end GUI or not. It's probably nice to have though, especially since I'm not that confident with the command line yet. But still... command line just feels so responsive so I wanna use it all the time.


That's the nice thing about MPD, you don't have to choose between one UI or other, you can have all of them with the same music player (the player itself runs as a daemon in the background and therefore is independent of your user account, so it doesn't stop playing if you log out or close the client, only if you tell it to stop) and control it with commands, CLI user interfaces, graphical clients, web-based clients or even even clients running on Windows, OSX or Android. Or all at the same time. :D

So you don't need to choose which kind of interface you want to use, and can instead play around with different ways of controlling it based on what you happen to feel and what new interfaces you find.

..and it's very fast, and lightweight. Actually that's why I'm using it, I've yet to find another player that would handle my +70GB music collection as easily and quickly as MPD does.

It's a bit strange to set up, at least compared to normal music player programs, but luckily the default setup works fine for most people so you can just install MPD, link your music collection into it's default music directory (var/lib/mpd) and fire up whatever client you want to use.

(some more advanced options MPD has would be streaming it's PulseAudio output to other computers on local network, allowing you to keep your music on one computer but play it back and control it from any computer in your LAN, or set it to work with IceCast server and a web-based interface giving you a personal web radio you can control and listen to on any computer in the world as long as you have Internet connection, web broswer and some music player capable of listening to Internet radio. But it's still pretty cool even if you just use it to play music on a single computer)

---

### Post by deconstrained on 2011-03-22
> **nothingspecial said:**
> I disagree, I want my music straight away. I don't want to have to click this and click that and blah, blah, blah, boring, boring ,boring.
You missed my point. If the command line is the **only** way you can control your music, or if other ways require ad-hoc hackery, you're missing out.

ncmpcpp FTW

---

### Post by tgalati4 on 2011-03-22
sudo apt-get install moc
mocp

---

