---
title: "how to get ffplay to play multiple files one after the other"
date: 2012-10-09
forum: Multimedia Software
---

### Post by shantiq on 2012-10-09
i cannot seem to manage this


it is not important but i am curious how to get ffplay to play multiple files in a folder one after the other



it wants a filename and does accept wildcard *


so i tried

```
 for in *.m4a ; do ffplay "$f" "${f%.m4a}.*" ; done

```

and 

```
while true ; do ffplay *m4a ; done
```


and no dice


would any of you who actually know how to get this to work


i just want to know if it can be done easily

---

### Post by nothingspecial on 2012-10-09
```
for f in *.m4a ; do ffplay -autoexit "$f"; done
```

---

### Post by shantiq on 2012-10-09
in the name of Ffmpeg thank you so much nothingspecial


   can see it now in the --help  but **would never have spotted it as what i was looking for**  
   this gives one yet another command-line music player in effect


may add other formats too and done


> for f in nocaseglob nullglob *.{flac,ape,wv,m4a,aac,mp4,mp3,shn,tta,wma}  ; do ffplay -nodisp -autoexit "$f"; done



> ffplay --help
ffplay version N-35917-ge4fe4d0 Copyright (c) 2003-2012 the FFmpeg developers
  built o....................
-skipframe          
-skipidct           
-idct algo          set idct algo
-ec bit_mask        set error concealment options
-sync type          set audio-video sync. type (type=audio/video/ext)
**-autoexit           exit at the end**
-exitonkeydown      exit on key down
-exitonmousedown    exit on mouse down




and multiple folders therefore  [say cd Music]



> for i in */
do
  cd "$i"
for f in nocaseglob nullglob *.{flac,ape,wv,m4a,aac,mp4,mp3,shn,tta,wma}  ; do ffplay -nodisp -autoexit "$f"; done
  cd ..
done

---

### Post by FakeOutdoorsman on 2012-10-09
Adding *-nodisp* to disable graphical display might be useful here. Otherwise the display will appear for each track and may steal focus, as in pop up in front of your current window; probably depending on your windows manager.

---

### Post by shantiq on 2012-10-09
> **FakeOutdoorsman said:**
> Adding *-nodisp* to disable graphical display might be useful here. Otherwise the display will appear for each track and may steal focus, as in pop up in front of your current window; probably depending on your windows manager.


thank you Fake   was thinking that on music files that have a picture in them it can be a pain   will add it:KS

---

### Post by shantiq on 2012-10-10
**        =================================================**


That gives us quite a ** decent ffmpeg command-line musicplayer **

FIRST  install  > sudo apt-get-install gnome-open-terminal    and /or    [**nautilus-terminal**]("https://help.ubuntu.com/community/PlayMusicFromCommandLine")


 
**TO SET UP**


enter in terminal and return


> alias ff='for f in nocaseglob nullglob *.{flac,ape,wv,m4a,aac,mp4,shn,tta,wma}  ; do ffplay -nodisp -autoexit "$f"; done'

  then

```
gedit  ~/.bashrc
```

and place 

> alias ff='for f in nocaseglob nullglob *.{flac,ape,wv,m4a,aac,mp4,shn,tta,wma}  ; do ffplay -nodisp -autoexit "$f"; done'

at the bottom of page and save


then```
 . ~/.bashrc 
``` in terminal


**From now on ** you open any music folder right-click   choose open with terminal  and enter ```
ff
```

THAT IS A QUICK MUSIC PLAYER

ctrl+c to move to next tune    ctrl+z to quit







================
Now all added to [**guide**]("https://help.ubuntu.com/community/PlayMusicFromCommandLine") on how to play music from command-line

---

### Post by shantiq on 2012-11-03
will also play AOB inside a DVDA   [as i found out also does VLC]

so you can use this for more functionality

> for f in nocaseglob nullglob *.{flac,ape,wv,m4a,aac,mp3,mp4,shn,tta,wma,AOB} ; do ffplay -nodisp -autoexit "$f"; done



read post above to trigger with    > ff

---

