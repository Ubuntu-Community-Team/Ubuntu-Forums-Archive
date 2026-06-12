---
title: "mp3s are not working&gt;&gt;&gt;"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by hashil on 2007-12-14
hi all. i am a  new user of ubuntu and it seems that i cant 

open any file of mp3 format.... and also no video formats are working


any help?

---

### Post by elliotjreed on 2007-12-14
run the following command:

sudo apt-get install ubuntu-restricted-extras kubuntu-restricted-extras xubuntu-restricted-extras w32codecs libcss2

That should make all of your problems go away

Do that in the Terminal, if not, find the packages in Synaptic using search!

Good luck

---

### Post by seshomaru samma on 2007-12-14
you need to install codecs for them 
it's easy
read [here]("https://help.ubuntu.com/community/RestrictedFormats")

elliotjreed's method is good as well
however, please notice that you do not need to install ubuntu-restricted-extras **and ** kubuntu-restricted-extras **and ** xubuntu-restricted-extras
one is enough depending on whether you are running ubuntu , kubuntu or xubuntu (if you don't know then you are probably running ubuntu)

---

### Post by daengbo on 2007-12-14
I have a owto on my blog for Gutsy
[http://ibeentoubuntu.blogspot.com/2007/10/worried-about-how-to-play-mp3-and-divx.html](http://ibeentoubuntu.blogspot.com/2007/10/worried-about-how-to-play-mp3-and-divx.html)

---

### Post by hashil on 2008-03-24
> **elliotjreed said:**
> run the following command:

sudo apt-get install ubuntu-restricted-extras kubuntu-restricted-extras xubuntu-restricted-extras w32codecs libcss2

That should make all of your problems go away

Do that in the Terminal, if not, find the packages in Synaptic using search!

Good luck

i tried that and it gave me this result


ricted-extras xubuntu-restricted-extras w32codecs libcss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
kamil@kamil-laptop:~$ 

i dont get it :(

---

### Post by hashil on 2008-03-24
> **daengbo said:**
> I have a owto on my blog for Gutsy
[http://ibeentoubuntu.blogspot.com/2007/10/worried-about-how-to-play-mp3-and-divx.html](http://ibeentoubuntu.blogspot.com/2007/10/worried-about-how-to-play-mp3-and-divx.html)

not working too!!!
:(

---

