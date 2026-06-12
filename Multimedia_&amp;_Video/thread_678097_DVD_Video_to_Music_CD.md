---
title: "DVD Video to Music CD?"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by liquidfunk on 2008-01-25
Is it possible to rip the sound from a DVD Movie, and put it onto a CD to listen to the dialogue and soundtrack. 

 We fancied listening to something new at work, I thought this may be interesting. 

 Any thoughts ?

---

### Post by yabbies on 2008-01-25
it sure is
and very easy from the command line
you will need ffmpeg

make sure all repos are open: check [here]("https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto") if you don't know what that is
open a terminal

```
sudo apt-get update

sudo apt-get install ffmpeg
```

put your video-needs to be mpg  in a folder on your desktop and call it audio_rip

in a terminal 

```
cd Desktop

cd audio_rip
```

this will change directories to where your video is located
you can type ls to get a list of everything in the directory to make sure your video is there

now just type to extract the audio and make it a mp3

```
ffmpeg -i YOURVID.mpg -f mp3 NEWMP3_FILE.mp3
```

---

### Post by liquidfunk on 2008-01-25
Thanks a lot, your a genius!

 Hope I can get Lord of the rings onto one disc... :P


 :lolflag:

---

