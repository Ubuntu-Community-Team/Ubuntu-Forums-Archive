---
title: "Internet Radio Options"
date: 2010-08-05
forum: Multimedia Software
---

### Post by alanwalterthomas on 2010-08-05
What are my options for listening to radio streams over the Internet using Ubuntu?
I know of:

Rhythmbox - It lets me (makes me) input a URL to be streamed. May be good if I know what station I want, & didn't work the one time I tried it.

Browser-based websites.

MiroTV - has an audio section but not what I'm looking for.

What I would like to find is something like Wunder Radio as it works on the iPhone. It lets me search by genre, language, etc. so I can find an interesting station from France or some other place in the world without having to know beforehand what the exact station is. I'll have a list of suggestions to select from. Is there nothing like that?

---

### Post by marl30 on 2010-08-05
There is Exaile Music Player, which has Shoutcast radio that comes in Winamp. It's the best I've found so far.

---

### Post by benerivo on 2010-08-05
I also like exaile. As a standalone internet stream player, the best i've seen is streamtuner. Version 1 is in the repositories and V2 is [http://milki.erphesfurt.de/streamtuner2/](http://milki.erphesfurt.de/streamtuner2/)

---

### Post by Deadite81 on 2010-08-05
There is a Rhythmbox Shoutcast/Icecast radio plugin, which works fine for me.  Exale's ok, but Rhythmbox, as much as I dislike it's inability to do certain things, has been the most stable for me (after updating to 0.13 anyway).  Also, you don't have to install a whole new music player if you don't want to.

The simplest way to install it is to use the ppa on the Launchpad page here: [https://launchpad.net/~segler-alex/+archive/ppa](https://launchpad.net/~segler-alex/+archive/ppa)

---

### Post by alanwalterthomas on 2010-08-05
I found that rhythmbox has a radio browser plugin in synaptic which makes it more useful. The user interface could be a little better, but I'll use it since it's integrated with Rhythmbox & Exaile seems to do the same thing.
I downloaded the streamtuner2 debs from its website but when I start the program it begins to load some modules then dies.
Thanks for the suggestions!

---

### Post by bluewanders on 2010-08-05
I am on Lucid... downloaded adobe air from synaptic and the Pandora One desktop app... thats what I listen to the most.

---

### Post by Linuxforall on 2010-08-05
Added shoutcast script on Amarok with Kubuntu here, shoutcast has the best variety among the internet radios out there.

---

### Post by alanwalterthomas on 2010-10-05
Time to revive this thread for just a little longer - really.

I saw that the iPhone app (wunder radio) used a service called radiotime to get its (vastly superior to shoutcast/shoutcast) list of stations, so I went to the website, [www.radiotime.com](www.radiotime.com)

I think I'm close to getting what I wanted & can listen to the various stations at radiotime's website (for free), but I'm a noob & unsure of how I can move the stations I want into rhythmbox's radio or something else like radiotray so I don't need to use a browser.

I tried copying [http://radiotime.com/WebTuner.aspx?StationId=24670&](http://radiotime.com/WebTuner.aspx?StationId=24670&) (the url up top while listening to a station) to add to rhythmbox, but was told that gstreamer lacked a plugin (text/html decoder), it tried to look for one, & failed.

What should I do now?

---

### Post by Rasa1111 on 2010-10-05
I use Pandora,
and use the Pandora applet in my AWN dock for it.
then i never have to visit the site even,
i just open it from my desk. no browser or anything else needed. :D

---

### Post by alanwalterthomas on 2010-10-07
Pandora only works in the US. I'm not in the US.
I'd just like to know what I have to do to get the radiotime sites into rhythmbox, if that's possible.

---

### Post by alanwalterthomas on 2010-10-14
bump  ... help please ...

Take a look at post #8.

---

### Post by perspectoff on 2010-10-14
Shoutcast generally streams MP3 (sometimes AAC). It is by far my favorite. Thousands of stations.

I like to play my streams using Audacious (an efficient fork of the venerable XMMS player).

Audacious is very much like XMMS (and the venerable Winamp of Windows). 

Fast, efficient. (Amarok is bulky and balky in comparison, but nevertheless is my second choice). Install

 sudo apt-get install audacious

(or install from a Package Manager).

I then set up a menu item / desktop shortcut to start Shoutcast from Firefox:

 firefox [http://classic.shoutcast.com](http://classic.shoutcast.com)

which brings up Shoutcast's browser-based menu of radio stations. When I click on a radio station, it starts the .pls stream, which I then merely associate with Audacious (so that Audacious always plays .pls streams from then on).

Note: Internet Radio streams are often served on a variety of random ports. It is difficult to know which ports need to be open, so I have often had to allow a range of ports to be open in my firewall to allow Internet Radio streaming.  

(PS At work, some Windows users got a virus from their Pandora installation. Be careful.)

---

### Post by ron999 on 2010-10-14
> **alanwalterthomas said:**
> bump  ... help please ...

Take a look at post #8.

Hi
If you want to listen to FM 103.3 CHAA-FM with Rhythmbox, this is the URL to use:-
```
http://stream02.ustream.ca:8000/fm1033128.mp3
```

---

### Post by alanwalterthomas on 2010-10-15
ron999, thanks, but where did you get that url (so I can get others I'd want)?
I looked at the radiotime website but couldn't find that anywhere. I didn't even find that from the station's website, although it would be easier if it's possible to just get the urls from radiotime.

---

### Post by ron999 on 2010-10-15
[COLOR="White"]ll[/COLOR]

---

### Post by ell02 on 2010-11-15
To get a http stream id. that you can use try right clicking and select properties.Might have to do this a couple of times depending on what player you'r using.

---

