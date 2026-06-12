---
title: "Update broke my ..."
date: 2012-03-11
forum: Multimedia Software
---

### Post by Otto-C on 2012-03-11
I did a virgin install of Ubuntu 10.04 on my
laptop.
From time to time I listen to a radio program
airing on  'www.1240news.com'. After doing the
base install and going to the site, upon clicking
'Listen Live' the program played as expected.
I then did a full update.  Following the update the
program does not play.
When the program works the address bar shows:
[http://stream.mediatechusa.com:8080/WFOY](http://stream.mediatechusa.com:8080/WFOY)
When not working the address bar shows:
stream.mediatechusa.com:8080/WFOY with 'stream and
:8080/WFOY' grayed out and 'mediatechusa.com' in black.
Is this a bug or is there a workaround.
Thanks in advance
Otto-c

---

### Post by ajgreeny on 2012-03-11
> **Otto-C said:**
> I did a virgin install of Ubuntu 10.04 on my
laptop.
From time to time I listen to a radio program airing on  'www.1240news.com'. After doing the base install and going to the site, upon clicking 'Listen Live' the program played as expected.
I then did a full update.  Following the update the program does not play.
When the program works the address bar shows:
[http://stream.mediatechusa.com:8080/WFOY](http://stream.mediatechusa.com:8080/WFOY)
When not working the address bar shows:
stream.mediatechusa.com:8080/WFOY with 'stream and
:8080/WFOY' grayed out and 'mediatechusa.com' in black.
Is this a bug or is there a workaround.
Thanks in advance
Otto-c
What plugin are you using to play this stream in Firefox?  I assume you are using Firefox.

I have just this second tried the site, which shows exactly the same stream addresses as you show, and it plays wonderfully using **gecko-mediaplayer** as the plugin; I never liked **totem-mozilla** so always removed that and use the gecko-mediaplayer instead, which itself uses **gnome-mplayer**.

As you can see I am also using 10.04, fully updated and with all the [medibuntu]("http://www.medibuntu.org/") repository codecs that I always add to my systems.

Worth a try!

---

### Post by Otto-C on 2012-03-11
Reply to post #2.

Using Firefox 10.0.2

Removed the totem-mozilla plugin and
added gecko-mediaplayer.

I restarted and the result was same as in
original post.

tia
Otto-C

---

### Post by ajgreeny on 2012-03-12
I still wonder if it is a codec problem if you can not get things working.

Enable the [medibuntu]("http://www.medibuntu.org/") repos as I mentioned in my first post and see if installing **w32codecs** package from there helps.  Also ensure youi have the **ubuntu-restricted-extras** and all the universe and multiverse **gstreamer** bad and ugly plugin packages installed.

---

### Post by Otto-C on 2012-03-12
I too wonder.  It worked just fine before the
update.
w32codecs and ubuntu-restricted-extras and all the universe and multiverse gstreamer are installed.

Thanks so much for your help.
Otto-C

---

### Post by ajgreeny on 2012-03-12
> **Otto-C said:**
> I too wonder.  It worked just fine before the
update.
w32codecs and ubuntu-restricted-extras and all the universe and multiverse gstreamer are installed.

Thanks so much for your help.
Otto-C
So is it now working OK on that site?

---

### Post by Otto-C on 2012-03-12
Still not working.

Will be busy this week but may take time to do
another install. But first do your gecko-mediaplayer
change before doing update.
Will post outcome on weekend.
Thanks again.
Otto-C

---

### Post by Otto-C on 2012-03-13
I checked with a friend who also has 10.04 on his
desktop. He had not tried to listen to the radio
station. We checked his system and it was fully up
to date.  The result was the same as described.
***
I listen to a radio program airing on 'www.1240news.com'. 
clicking 'Listen Live' the program played as expected.
Following the update the program does not play.
When the program works the address bar shows:
[http://stream.mediatechusa.com:8080/WFOY](http://stream.mediatechusa.com:8080/WFOY)
When not working the address bar shows:
stream.mediatechusa.com:8080/WFOY with 'stream and
:8080/WFOY' grayed out and 'mediatechusa.com' in black.
***
1. Should a bug report be made?
2. Not to get hammered but I would be curious if
   others using 10.04 have the same result?
Thanks
Otto-C

---

