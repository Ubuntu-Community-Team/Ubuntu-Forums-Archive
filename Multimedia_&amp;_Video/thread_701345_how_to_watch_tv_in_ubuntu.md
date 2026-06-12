---
title: "how to watch tv in ubuntu?"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by Phantom87 on 2008-02-19
Hello,

I have a Hauppauge Win-TV HVR-1600 (1181) High Definition TV Tuner and i was wondering how i can watch tv with this tuner. I read that it was not compartible with mythtv which is making me to consider changing it for sumthin that works on mythtv. Currently looking at getting Asus My Cinema P7131 TV Tuner.

I recently uninstalled Ubuntu however because i intend on giving it a larger partition. But until i can figure out how to watch tv on it, i wont make that transition.

---

### Post by Phantom87 on 2008-02-19
any help would be needed pls.

---

### Post by Lorenzo1985 on 2008-02-19
Was just about to open a similar sort of thread but i thought id share what little knowledge i have with you first.

So far the only program i've managed to whatch TV with is Klear

so heres what i would do 

go to a terminal and type:

[INDENT]sudo apt-get install klear[/INDENT]

then 

[INDENT]sudo apt-get install dvb-utils[/INDENT]

so you've now installed klear and DVB utils, next thing to do is start klear 
it will say things about your channels.conf and wont let you start it

next thing to do is 
cd /usr/share/doc/dvb-utils/examples/scan/dvb-t
ls
this will list a load of locations find the one that represents your nearest transmitter, for me this is uk-Hannington
the do 
scan <transmitter name found earlier> >~/.klear/channels.conf

eg 
scan uk-Hannington >~/.klear/channels.conf

then start klear again

Of course this may not work for you at which point i am no use to you

---

### Post by Phantom87 on 2008-02-19
Thanls lorenzo, will try it out once i make a fresh install.

---

### Post by artomb on 2008-06-15
There are several applications you can use to watch the TV in your ubuntu (although not all the hardware is compatible). Like Me TV, MythTV or reading with some pre-installed player reading from the standard input.

You can find some light on this post:
[http://www.harecoded.com/how-to-watch-and-record-tv-with-a-pc-ubuntu-linux/]("http://www.harecoded.com/how-to-watch-and-record-tv-with-a-pc-ubuntu-linux/")

I got my card easily working following the instructions. There is also a link to the hardware supported database.

Hope it helps.

---

