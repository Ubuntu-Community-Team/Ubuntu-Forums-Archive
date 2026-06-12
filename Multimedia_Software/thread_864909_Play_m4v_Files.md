---
title: "Play m4v Files?"
date: 2008-07-20
forum: Multimedia Software
---

### Post by lawrencius on 2008-07-20
Hey every1,
I have a lot of m4v files from itunes; what options do I have to play this format?

(I searched this forum and everything that people said is vlc which doesnt play them for me or xine with the same results.)

Thanks ahead,

Lawrencius

---

### Post by dexter.deepak on 2008-07-20
try reinstalling vlc...it SHOULD play them.

---

### Post by lawrencius on 2008-07-21
I tried it but it didnt work. Is there anything in the syn. package manager that could help?

---

### Post by Bachstelze on 2008-07-21
Try renaming them to .mp4

---

### Post by dexter.deepak on 2008-07-21
yes..renaming to .mp4 should work.
if this isnt working ,get the restricted-drivers, open up a terminal and try:
```
sudo apt-get install ubuntu-restricted-extras
``` 

if even this doesnt work ,then you can install miro; its not in the repos, so u need to edit the /etc/apt/sources.list :
```

sudo gedit /etc/apt/sources.list
```
paste this line over there :(i assume you are on hardy)
```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/
```
and then update
```
sudo apt-get update
```
and finally open up synaptic , search for miro and install the required stuff.

---

### Post by zetskee on 2008-07-22
You say these files are from itunes? Do they have DRM on them?

---

### Post by wolfen69 on 2008-07-22
> **dexter.deepak said:**
> yes..renaming to .mp4 should work.
if this isnt working ,get the restricted-drivers, open up a terminal and try:
```
sudo apt-get install ubuntu-restricted-extras
``` 

if even this doesnt work ,then you can install miro; its not in the repos, so u need to edit the /etc/apt/sources.list :
```

sudo gedit /etc/apt/sources.list
```
paste this line over there :(i assume you are on hardy)
```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/
```
and then update
```
sudo apt-get update
```
and finally open up synaptic , search for miro and install the required stuff.

installing mozilla-mplayer and vlc using the medibuntu repos gives me all the codecs. and of course, libdvdcss2. everything works. oh, and i get rid of totem first. (imo, it's junk and interferes)

no need for ubuntu restricted extras. flash and java can be installed seperately. alot of people add too much junk.

---

### Post by lawrencius on 2008-08-06
I'm sorry to sound like hopeless but I did all the mentioned methods and I still get errors/movies not playing

---

### Post by Ehtetur on 2008-08-18
> **lawrencius said:**
> I'm sorry to sound like hopeless but I did all the mentioned methods and I still get errors/movies not playing

Unless I'm mistaken, renaming .m4v to mp4 should allow vlc, mplayer, etc. to play the file... unless, it's infected with DRM (i.e. encrypted).

Ehtetur

---

### Post by cor2y on 2008-08-18
If its from the Itunes store then chances are the itunes drm is on them.
And i know of no method to remove the drm off of Itunes video.
So there it is sorry to say.

---

### Post by daniel_w93 on 2010-05-02
Well I get a pretty clear Error output in VLC

> VLC doesn't support the audio/videoformat "drmi".
Unfortunately you can't do anything about it.

So yeah iTunes stuff is DRM encrypted and can't be played by VLC,Totem,Xine etc. :(

unless ofcourse you run iTunes in a virtualbox or Wine...but that's a whole different chapter......

---

### Post by ierpe on 2010-07-28
I have a similar problem, except I have no error message.

I hear the audio of a m4v file, but the video is not displayed... that in vlc or in the movie player...

Any idea?

---

### Post by parsama on 2010-07-28
en...it looks very good .........

---

### Post by ierpe on 2010-07-28
> **parsama said:**
> en...it looks very good .........

??? you trying to say something...?

---

### Post by MorrisseyJ on 2010-07-28
I am not sure about this but i think that you should be able to RIP your itunes stuff to a DVD/CD and then reimport with the DRM stuff switched off. From there you can convert the files to another formta .vogg or .mp3

As i understand it you can only do this 5 times - i.e. make 5 CDs. 

If you are reimporting i would take the files out of MP4 format and import them as .vogg or .mp3.

---

