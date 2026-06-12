---
title: "Codecs for Ubuntu"
date: 2009-06-27
forum: Multimedia Software
---

### Post by jordanoff11121 on 2009-06-27
I'm sorry about my trivial question.
Where can i get codecs for Ubuntu?
I can't open .mp3, .avi, etc...

The system can't download needed codecs auto.

See this screenshots.

[[IMG]http://img189.imageshack.us/img189/238/screenshot2v.th.png[/IMG]]("http://img189.imageshack.us/i/screenshot2v.png/")

[[IMG]http://img189.imageshack.us/img189/4072/screenshot4o.th.png[/IMG]]("http://img189.imageshack.us/i/screenshot4o.png/")

[[IMG]http://img189.imageshack.us/img189/7223/screenshot1yhd.th.png[/IMG]]("http://img189.imageshack.us/i/screenshot1yhd.png/")


I'm like a indian warrior in civilization with this linux. Image that i'm idiot and post me step by step what to do. 
Thanks. :))))))))))

:popcorn:

---

### Post by kixome on 2009-06-27
on our panel>system>administration>software sources

enable all check boxes under the ubuntu tab except source code
do the same under third party tab except cdrom then close, and it will ask to reload. Press reload> then close all applications and reopen your movie/musicplayer and try to open file, it should search and find codecs for each. Otherwise add/remove  and search codec

---

### Post by jordanoff11121 on 2009-06-27
> **kixome said:**
> on our panel>system>administration>software sources

enable all check boxes under the ubuntu tab except source code
do the same under third party tab except cdrom then close, and it will ask to reload. Press reload> then close all applications and reopen your movie/musicplayer and try to open file, it should search and find codecs for each. Otherwise add/remove  and search codec

Error with add/remove and search. The system can't connect with internet and download needed codecs. It doesnt works.

Where is "our panel" or "panel"??  I'm newbie, man, please tell me.

---

### Post by kixome on 2009-06-27
The panel is the bar at the very top with the menu on it, but sounds like an internet problem. sorry i meant your panel.

Yours is at the bottom

---

### Post by kixome on 2009-06-27
open a terminal by going to Your" start button" on the panel goto accessories then select terminal and type: 
sudo dpkg --configure -a
then enter your password and close the terminal and try again.

dont mind this-@kskls

---

### Post by jordanoff11121 on 2009-06-27
> **kixome said:**
> open a terminal by going to Your" start button" on the panel goto accessories then select terminal and type: 
sudo dpkg --configure -a
then enter your password and close the terminal and try again.

dont mind this-@kskls

After that operation:

[[IMG]http://img196.imageshack.us/img196/5044/screenshot7c.th.png[/IMG]](http://img196.imageshack.us/i/screenshot7c.png/)


And now:

[[IMG]http://img23.imageshack.us/img23/2692/screenshot6lql.th.png[/IMG]](http://img23.imageshack.us/i/screenshot6lql.png/)

Where is that ? What can i do?

---

### Post by kixome on 2009-06-27
in terminal you need to fix your broken packages

type:

sudo apt-get -f install

---

### Post by kixome on 2009-06-27
then try add/remove and search for codecs, or try to open the file and see if it will auto install codecs and play, if not I cant help any further as i must to bed 5:01am here

---

### Post by jordanoff11121 on 2009-06-27
I don't know how, but my problems with codecs are fixed. Codecs are successfully downloaded.

Thanks about everything! I like people who helping. This forum is really nice!
Thanks again!

Last:

Installed updates fixed any problems ? or no ?!

For future must i install updates to my Ubuntu ? or this is not important ?

sorry about my english. :)))

I'm so happy! Thanks for 3d time!

---

