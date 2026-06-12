---
title: "wget bbc video"
date: 2010-04-09
forum: Multimedia Software
---

### Post by namluc on 2010-04-09
I want to download the video embedded on bbc pages

for example:

[http://news.bbc.co.uk/2/hi/science/nature/8609545.stm](http://news.bbc.co.uk/2/hi/science/nature/8609545.stm)

the wget -O /tmp/page.tmp command does not seem to save the video id.


Thanx

---

### Post by ron999 on 2010-04-09
Hi
wget won't do it.
It's not a file you're linking to, it's a stream. So you need a program that will capture the stream and save it as a file.
Look in Ubuntu's repository for a program named '**get-iplayer**'.
When you've installed it use a command like this:-
```
get-iplayer --get --url=<URL>
```

So to download the video that you linked, the command is:-
```
get-iplayer --get --url=http://news.bbc.co.uk/1/hi/sci/tech/8609545.stm
```

---

### Post by andrew.46 on 2010-04-09
As a side note it appears that BBC policy has meant the end of development of this program:


get_iplayer dropped in response to BBC’s lack of support for open source
[http://linuxcentre.net/get_iplayer-dropped-in-response-to-bbcs-lack-of-support-for-open-source](http://linuxcentre.net/get_iplayer-dropped-in-response-to-bbcs-lack-of-support-for-open-source)

Andrew

---

### Post by namluc on 2010-04-14
thanks for the replies, looks like i'm out of luck with this one, especially as i don't live in the uk at the moment.

---

### Post by zigmond on 2010-04-19
Hi 
I am tyring to download a forum web page using Wget but all I get is a partial HTML without people's comments
The address I am trying to download is: [http://www.tapuz.co.il/Forums2008/ForumPage.aspx?ForumId=337&PageNumber=2](http://www.tapuz.co.il/Forums2008/ForumPage.aspx?ForumId=337&PageNumber=2)
 
my code is: 
 
wget output-document=1.txt [http://www.tapuz.co.il/Forums2008/ForumPage.aspx?ForumId=337^&PageNumber=2](http://www.tapuz.co.il/Forums2008/ForumPage.aspx?ForumId=337^&PageNumber=2)
 
Can anyone help me pleas?

---

### Post by pacman869 on 2011-10-11
Awesome tip, THANKS HEAPS!!!

worked fine for me in Australia, made an avi

---

### Post by nothingspecial on 2011-10-11
Necromancy.

Closed.

---

