---
title: "Best Video Editor?"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by Rev. Nathan on 2007-03-20
I use Final Cut Pro and Avid at school, would like a nice parallel for Linux at home. Simple cut-and-dry editing would suffice, although I would like it if I found a familiar set of features and interface.

What say you, Ubuntusers?

---

### Post by Repabil on 2007-03-20
I've got no experience with these sorts of applications but I do know of [PiTiVi](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=pitivi).

---

### Post by bloodniece on 2007-03-20
Kino is like iMovie in functionality
But
Cinelerra is a full featured editor much like Final Cut Pro.  Many post-production houses use Cinelerra and Shake (both run on Linux, though Apple owns Shake now)

Linux.com [article on Cinelerra.]("http://applications.linux.com/article.pl?sid=07/03/05/1949213&tid=39&tid=13")

Add Cinelerra to apt repository.
```
sudo gedit /etc/apt/sources.list
```At the bottom of the file add
```
 #ubuntu edgy
deb http://giss.tv/~vale/ubuntu32 ./
deb-src http://giss.tv/~vale/ubuntu32 ./
```Save
```
sudo apt-get update
```In order to use the mirror you need to add in your gpg keyring marillat's gpg-key
```
    gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 1F41B907
    gpg --armor --export 1F41B907 | sudo apt-key add - 
```   If you don't use sudo, do the following under root :
```
    gpg --armor --export 1F41B907 | apt-key add -
```
```
sudo apt-get install cinelerra
```

---

### Post by jkwarras on 2007-03-20
I also recommend cinelerra. I've also worked with Final Cut Pro, and even if cinelerra is the closest to a pro application, the GUI is not as intuitive and as user friendly as the Apple application. So take your time to learn the usage.

---

### Post by bloodniece on 2007-03-21
Yeah, the UI is lacking.  And no drag and drop from Nautilus into the library/resources folders.  That is my biggest beef, since importing assets can take some time.

---

### Post by Naegling23 on 2007-03-21
kdenlive is my choice

cinnelerra is too professional (read: confusing) for my tastes
lives has the same problem
kino and the avidemux one are too minimal.
pitv wouldnt install for me, so I have no opinion.

---

### Post by Rev. Nathan on 2007-03-21
Everything looks good! BTW if any of you are screenwriters, check out Celtx; it will change your life!

---

### Post by jkwarras on 2007-03-22
> **Rev. Nathan said:**
> Everything looks good! BTW if any of you are screenwriters, check out Celtx; it will change your life!

Yeah, I use this too. Great replacement for Final Draft.

---

### Post by kenmiles on 2007-03-27
I have tried to install Cinelerra but get the following message
as root type 
echo "0x7fffffff" >/proc/sys/kernel/shmmax
but I get a permission denied when I try.
Any help please.
Regards, Kenneth.

---

### Post by jpolega on 2007-03-28
> **kenmiles said:**
> I have tried to install Cinelerra but get the following message
as root type 
echo "0x7fffffff" >/proc/sys/kernel/shmmax
but I get a permission denied when I try.
Any help please.
Regards, Kenneth.
you need to "sudo /bin/bash" to get a root shell first.

---

### Post by kenmiles on 2007-03-28
Thanks fot that

---

### Post by sk8dork on 2007-03-28
so, i've never heard of pitivi, but i saw it referenced here and on the list for ubuntustudio, so i thought i'd try it (it's in the repos for feisty)...i gotta say...wow. it seems to be pretty stable, and it seems to be easy, but that's it. it doesn't really seem very featurful, even less features than kino and avidemux, which i didn't think was possible (although both very good programs in their own right). hopefully pitivi will advance over time. if there's one thing that bugs me about linux video editing software it's the stability thus far. so in all seriousness i look forward to the advancement of pitivi.

---

### Post by sk8dork on 2007-05-01
by the way, i was having issues with cinelerra not responding to any input after i installed it last. i noticed that the version was 20070221. i also noticed that the community version cinelerra site now has ubuntu repos with far more updated versions (20070424 as of this writing). [check it out.]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu")

---

### Post by sk8dork on 2007-05-15
after watching some video tutorials and playing around in cinelerra after installing it into ubuntu studio, i've decided that it's the best offering in the realm of video editors on linux. go to their [docs page]("http://cvs.cinelerra.org/docs.php") to find lengthy text documentation and some links to some video tutorials. the two video tutorials from the_source are nice, and very helpful, but they're about 10-20 minute segments ( IIRC ) nested inside each hour+ long episode. some people won't want to download the 300+MB videos, so i suggest watching the first one on google video with the link they provide and skipping ahead somewhere around 45 minutes in to see the tutorial. i also found a couple really bad tutorials [on youtube]("http://youtube.com/results?search_query=cinelerra&search=Search") that are only helpful after you watch the ones from the_source. the youtube tuts have bad quality and no narration or titles explaining anything, so you have to just figure it out from what's there.

---

