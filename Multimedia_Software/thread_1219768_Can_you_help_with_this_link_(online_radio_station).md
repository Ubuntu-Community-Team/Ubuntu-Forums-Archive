---
title: "Can you help with this link (online radio station)?"
date: 2009-07-22
forum: Multimedia Software
---

### Post by kokonobs on 2009-07-22
Hi,
This link is an online radio station which i've been trying to get to work on Hardy Heron for sometime now. I have downloaded and removed several players in the hope of making this work. Has anyone got a solution?

[http://news.myjoyonline.com/radio/joy.asp](http://news.myjoyonline.com/radio/joy.asp)

Thanks in advance. 
NB: I'm still a newbie

---

### Post by sisco311 on 2009-07-22
Do you have ubuntu-restricted-extras installed?

I can play the stream with the mozilla-mplayer plugin, with mplayer from a terminal:
```
mplayer http://76.73.4.74:8004
```
and with rhythmbox and totem as well.

With the totem-mozilla plugin i get an error message like:
*Stream contains no data* or *Could not determine type of stream*
but if i right click on the plugin and select *Open with "Media Player"* the stream plays in totem.

So try to uninstall totem-mozilla and install mozilla-mplayer or mozilla-plugin-vlc.

---

### Post by kokonobs on 2009-07-23
Wow, thats real great. Thanks so much sisco311. It works now. 

What happened to the 'thanks button'. Btw an idea how to mark this thread solved?

---

### Post by Bucky Ball on 2009-07-23
```
mplayer [http://76.73.4.74:8004]("http://76.73.4.74:8004/")
```

... works fine for me. Haven't tried the others yet.

---

### Post by sisco311 on 2009-07-23
> **kokonobs said:**
> Wow, thats real great. Thanks so much sisco311. It works now.


Cool! 

> **kokonobs said:**
> 
What happened to the 'thanks button'. Btw an idea how to mark this thread solved?

The thanks and solved options were disabled.

Go to your first post > edit > advanced > type [SOLVED] in front of your thread title > save. You can also add a 'solved' tag as well.

[Where are the "Thank you" and "solved" features]("http://ubuntuforums.org/showthread.php?t=1044714")?
[How do I mark my thread as solved?]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6")

---

### Post by kokonobs on 2009-07-23
Smashing. Thanks guys :) :) Now i can stay in Hardy and no go to windows just to listen to that station :)

---

### Post by Bucky Ball on 2009-07-27
You can add the Medibuntu repository to your sources also which adds a whole bunch of codecs and other things media. Be warned: there is a lot of third-party stuff in there so if you are looking to go OSS only, this is not for you.

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

Don't forget to add the key as the last step. :)

---

