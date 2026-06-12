---
title: "Flash Player Alternative"
date: 2016-02-20
forum: Multimedia Software
---

### Post by angel mike on 2016-02-20
What is the easist way to watch videos without the Flash Player banner particularly on the BBC web site. Is there a default process with Firefox.

---

### Post by coldraven on 2016-02-20
At the moment you have to use Flash on the BBC site but they are planning to stop using it at some point. The sooner the better as far as I'm concerned!
 I just found this so maybe you could alter you user agent to spoof an Android device. (I just noticed that this story is 4 years old)
[http://www.bbc.com/news/technology-19648600](http://www.bbc.com/news/technology-19648600)

---

### Post by shantiq on 2016-02-20
well a great way I found is this  ;  takes a minute and the video DOES NOT ever check something no browser ever does it seems

copy the video URL open your terminal

```
 get_iplayer --stream  [COLOR=#800000] URL[/COLOR]   --player="mplayer -cache 512 -"
```

for example:


```
 get_iplayer --stream  http://www.bbc.co.uk/iplayer/episode/p00sydsh/a-city-crowned-with-green   --player="mplayer -cache 512 -"
```

---

### Post by coldraven on 2016-02-21
> **shantiq said:**
> well a great way I found is this  ;  takes a minute and the video DOES NOT ever check something no browser ever does it seems

copy the video URL open your terminal

```
 get_iplayer --stream  [COLOR=#800000] URL[/COLOR]   --player="mplayer -cache 512 -"
```

for example:


```
 get_iplayer --stream  http://www.bbc.co.uk/iplayer/episode/p00sydsh/a-city-crowned-with-green   --player="mplayer -cache 512 -"
```

Yes that is a nice way to view the iPlayer site but unfortunately all the news articles are still using Flash.
This is the only reason that I do not un-install Flash :(

---

### Post by kc1di on 2016-02-21
[this article ]("http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html")may be of help , though it's a year old now, I haven't tried it just use chromium with pepper flash.

---

### Post by angel mike on 2016-02-23
Sorry about slow reponse - thanks for everyones comments - very useful. Mike

---

