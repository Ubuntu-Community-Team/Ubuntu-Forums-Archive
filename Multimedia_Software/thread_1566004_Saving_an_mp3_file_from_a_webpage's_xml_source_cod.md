---
title: "Saving an mp3 file from a webpage's xml source code"
date: 2010-09-01
forum: Multimedia Software
---

### Post by Gr3ghammett on 2010-09-01
I listen to a radio show that broadcasts online a lot named ChatterBox Video Game Radio, and when i e-mailed one of the hosts about retrieving archived shows since the site didn't have any archiving of old shows or a link to it. Alon was nice enough to send me one of their old web pages with a HUGE list of archives but it's only the xml source code of the page. since the page isn't live of course, and because of the how he had to send me the code for the page and not a hyperlink to the page, i have the source code. now going through the source code of the page he emailed to me, i can find links to .mp3 files and i can open them and listen to the shows in web browsers, but i was hoping to save them to my computer for future listening.

     so far when i use the media address of wwww.chatterbox'ssite.com/whatever/anotherfolder/showiwanttosave.mp3 in firefox quicktime comes in and lets me listen (as long as my internet connection is active) but wont enable me to save because i dont have the pro version of quicktime. quicktime is good, but i dont use it enough to actually buy the product, and i'm not going to buy the product for just a one time use. is there another way to where i can save this file using the address from the source code (and the ChatterBox allows listeners to save their shows to computer for free, so it not some work around to rob them of money. i fully support them) without having to buy quicktime 7 pro(a product i never really use)?

---

### Post by andrew.46 on 2010-09-01
Hi Gr3ghammett,

Can you give an example, by which I mean the address, of one of these streams? An mp3 stream should be pretty straightforward to save I suspect.

Andrew

---

### Post by Gr3ghammett on 2010-09-01
[http://www.chatterboxgameshow.com/archives/Show79_07-17-2005.mp3](http://www.chatterboxgameshow.com/archives/Show79_07-17-2005.mp3)

from the line in the xml source code:

<media:content url="http://www.chatterboxgameshow.com/archives/Show79_07-17-2005.mp3" fileSize="16201728" type="audio/mpeg">

---

### Post by Gr3ghammett on 2010-09-01
HAHAHAHAHA ok i get it now. i'll just have to build a local web server, build the links from the source code and save them that way. I was so stupid lol. thanks for the help.

---

### Post by andrew.46 on 2010-09-01
Hi Gr3ghammett,

> **Gr3ghammett said:**
> i'll just have to build a local web server, build the links from the source code and save them that way.

Perhaps an easier way is to simply use wget:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]wget http://www.chatterboxgameshow.com/archives/Show79_07-17-2005.mp3[/COLOR]**
--2010-09-02 12:07:09--  http://www.chatterboxgameshow.com/archives/Show79_07-17-2005.mp3
Resolving www.chatterboxgameshow.com (www.chatterboxgameshow.com)... 174.133.174.138
Connecting to www.chatterboxgameshow.com (www.chatterboxgameshow.com)|174.133.174.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16201728 (15M) [audio/mpeg]
Saving to: `Show79_07-17-2005.mp3'

100%[==============================================================>] 16,201,728   153K/s   in 1m 42s  

2010-09-02 12:08:52 (155 KB/s) - `Show79_07-17-2005.mp3' saved [16201728/16201728]

```

Works well enough on my system :).

Andrew

---

