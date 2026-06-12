---
title: "Easytag Album art problem"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by akshayas1986 on 2007-11-18
Hi all,

I have a small problem with Easytag. Well before Ubuntu 7.10, I used to tag album arts in Ubuntu 7.04 and it used to work damn well. But ever since the Gutsy upgrade, whenever I add album art the following crazy things happen-

1. The album art is just a major mess on Amarok. All other album arts are visible but the latest edited album arts after gutsy upgrade are just a mess on screen.

2. The song size increases atleast by 3 or 4 times. A 3.5MB song becomes 11.7MB!!!

3. The song length also inceases. A 3 and half minute song is now 8 mintes!!!

Is this a bug with easytag and Gutsy??

Thanks

---

### Post by akshayas1986 on 2007-11-19
Anyone who has an answer for this??

If not is there any other software that can embed album arts into an MP3 file?

Thanks

---

### Post by Prediger on 2007-11-24
Had the same problem, posted here, got no answer and can't find my original post :-(

looks like noone is interested.

---

### Post by deeptingler on 2007-11-24
I Gotta say, I love Easytag but notice the same thing with corrupt album art on the latest version...  I did a clean install at some point and got some updates and it seems to have settled down so not sure what had caused this originally? eg upgrade instead of clean install?  However, I have to say, I didnt realise or notice any song files had increased in size, so I will have to monitor that as I am a very heavy user of the program for keeping my media centre updated (all laptops and pcs in the house are ubuntu apart from vista media centre in living room :()

---

### Post by Prediger on 2007-12-04
Anything new?

Just installed from scratch and without and after updating this problem remains for me.

This is forcing me to use windows, so it would be nics ti give that spot on my HD to e better use.

Please help someone!

---

### Post by oceanfree17 on 2008-03-07
Hi All,

I've fixed this one! well I had all the problems mentioned above and now Album Art appears perfectly.

I used the Synaptic Package Manager (via System > Administration) searched for 'libid3' then installed the 'lib3-3.8.3-dev' file that it finds.

Easytag then worked perfectly, I'm now watching all the tags perfectly through my media server, Amarock etc.

Hope it works for y'all too!

---

### Post by starpause on 2008-04-17
a command line tool to get the job done is  [eyeD3]("http://eyed3.nicfit.net/")

here's an example usage (which assumes you are in the directory containing all the mp3s for an album and cover.jpg):

```
eyeD3 --add-image=cover.jpg:FRONT_COVER *.mp3;
```

search the net and read the man pages for more ideas :)

however, my favorite tag editor right now is [kid3]("http://kid3.sourceforge.net/") ... quite amazing how easy it is to use, simply highlight a track and drag an image into the kid3 window.

---

### Post by warp99 on 2008-04-17
> **Prediger said:**
> Anything new?

Just installed from scratch and without and after updating this problem remains for me.

This is forcing me to use windows, so it would be nics ti give that spot on my HD to e better use.

Please help someone!

Did you remove the local configuration files for easytag in your home directory? It may be that new ones need to be generated since you updated. Just remove the directory ~/.easytag and a new one will be generated.

---

