---
title: "XBMC uPnP to Xbox 360...help"
date: 2009-03-10
forum: Multimedia Software
---

### Post by x C0MMAND0 x on 2009-03-10
So I have XBMC installed,  I enabled the uPnP settings, and my xbox 360 can not connect to it at all.  Any thoughts?  Has anyone gotten this to work?

---

### Post by x C0MMAND0 x on 2009-03-10
Anybody?  Help would GREATLY be appreciated.

---

### Post by omegamike3 on 2009-03-10
As in streaming content from XBMC to the 360? That's not what XBMC is really meant for...

---

### Post by x C0MMAND0 x on 2009-03-11
> **omegamike3 said:**
> As in streaming content from XBMC to the 360? That's not what XBMC is really meant for...

[http://xbmc.org/wiki/index.php?title=UPnP_Sharing](http://xbmc.org/wiki/index.php?title=UPnP_Sharing)

One of the big features is "supposed" to be uPnP sharing, and I really want to get it set up for my Xbox 360 just like Zune used to do back when I used Windows.

---

### Post by x C0MMAND0 x on 2009-03-12
Anybody?  There has to be someone who has gotten this to work, and others who would like to get it to work.

---

### Post by x C0MMAND0 x on 2009-03-18
Help...please...

---

### Post by x C0MMAND0 x on 2009-03-27
Windows Vista works so seamlessly with the 360 media sharing...and I loath Vista with such...passion :-).

There has never been anything I haven't been able to get working in Linux and be satisfied with, and I really would not like for this to be the first.  Anybody?

---

### Post by x C0MMAND0 x on 2009-04-06
I apologize to keep bumping, but I have done research, searched for other threads. tried uShare and geebox and nothing works well.

---

### Post by fishtek on 2009-05-01
> **x C0MMAND0 x said:**
> So I have XBMC installed,  I enabled the uPnP settings, and my xbox 360 can not connect to it at all.  Any thoughts?  Has anyone gotten this to work?

Hey I recently have tried this same thing and think I have gotten slightly further, but did hit a bump eventually.  As some background I was using Fuppes [http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/) back when I was using Ubuntu 8.04, however after installing Jaunty I wanted to use a upnp server that was a little nicer looking and had a better user interface.  Fuppes is a pain to get working and has some nasty bugs, but it does work most of the time.

So on to XBMC after getting it installed I was able to enable the upnp server under network settings, the next step is to add your library paths to your different content Music, Video, Pictures.  The final thing I did which took me a bit to figure out was to actualy right click on the folder after you add it and tell it to "scan item to library".  After doing that my 360 was able to see the XBMC Media server and I can browse around the folders and see the content.

The part them I'm now stuck on is that whenever I actually try to play a video (haven't tried music, or pictures yet), the 360 does the confirmation beep like it is going to play it, however it just sits there.  I can click play over and over but nothing actually happens.

From reading other posts, it sounds like people have gotten this working so I know it is possible.  Anyone have any ideas?

---

### Post by s3lekta on 2009-05-01
use ushare,

[http://ubuntuforums.org/showthread.php?t=848144&highlight=ultimate+xbox](http://ubuntuforums.org/showthread.php?t=848144&highlight=ultimate+xbox)

works perfectly thanks to the original poster and those on the thread

---

### Post by fishtek on 2009-05-02
So I actually got this working, turns out the 360 will only play video from XBMC if you added the video and set the content as "movies" to your library.  If you choose either of the other two "music video's" or "tv" it seems the 360 won't play it for some reason.  Also music is working as well.

---

### Post by phazixc on 2011-03-09
you may now know the answer to this question if not, what I did was and the folder in samba with a user and password and only visable...

then on the folder right click it and share the folder..

then in xbmc...  and the music folder source from the smp area (i.e on the network) 

what it does then is asks for a username and password which you enter and selected remember...

once thats done right click in xbmc on the music folder you just add and tell it to scan into your lib....

once completed you'll find all your music pops up no problem on your xbox 360


good luck

---

### Post by phazixc on 2011-03-09
LOL SORRY ABOUT THE MISS TYPOS ABOVE BEEN A LONG NIGHT

I RETYPED IT.....



lol


After some hours I came up with this.,.... and its quick and easy


download xbmc... you can install it from the "Tweak Ubuntu" software program...

once install --- system-----network---service--

select---- share videos and music upnp

NOW THATS DONE YOUR XBOX360 CAN SEE YOUR UBUNTU IT'LL SHOW AS 

XBMC: MEDIA SEVER ON YOUR XBOX360

now

install samba if you dont know how to google it, its simple or type it in the software center.

now

what I did was add the folders which i want sharing in samba with a username and password and only visable...

then on the folder its self right click it and share the folder..

then in xbmc... add the music folder source from the smp area (i.e on the network) 

what it does then is asks for a username and password which you enter and selected remember...

once thats done right click in xbmc on the music folder you just added and tell it to scan into your lib....

once completed you'll find all your music pops up no problem on your xbox 360


good luck

---

