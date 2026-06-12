---
title: "BBC radio stream capture"
date: 2010-05-01
forum: Multimedia Software
---

### Post by sebald on 2010-05-01
Anybody know of Linux tools that can *directly* capture the kind of aac audio via Flash that the BBC uses? So far all I've found is the Replay Media Catcher for Windows, but surely there's a way within Ubuntu! 

Don't bother replying with audio *recording* solutions, since I know how to do that. Only solutions that capture the *original* stream, please.

---

### Post by ron999 on 2010-05-01
...

---

### Post by nothingspecial on 2010-05-01
[HELP]
get-iplayer still works (for now).

development on it has ceased and it will not work forever.

```
sudo apt-get install get-iplayer
```

To search for all radio programmes

```
get_iplayer --type radio
```

if you know what you want to listen to use a keyword  - for example, if you want Front Row
```

get_iplayer --type radio Front
```

each search result is prefixed by a number, to download the stream

```

get_iplayer --get [COLOR="Red"]number[/COLOR]
```

[/HELP]

[RANT]I like to download the punk show to listen to in the gym and a few radio 4 programmes to listen to in the car/ walking to pick the kids up from school.

The BBC are against this sort of thing for fear of people like me file sharing their content - which I can understand - but I don`t and would not.

Filesharers ruin the capabilities of the internet.[/RANT]

---

