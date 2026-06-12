---
title: "To get a podcast in mp3 format on get-iplayer"
date: 2012-07-20
forum: Multimedia Software
---

### Post by shantiq on 2012-07-20
the default here on get-iplayer leaves you with a file in aac format which cannot be handled by many mp3 players; of course there is always the pssibility of converting afterwards with ffmpeg   but it is easier to do it straight off in get-iplayer itself


this does it


```
get-iplayer --mode=flashaacstd --aactomp3 --mp3vbr 2 --get 12220
```


the --mp3vbr modifier runs from 0 to 9 ; 9 being the lowest 

>  --mp3vbr                         Set LAME VBR mode to N (0 to 9) for AAC transcoding. 0 = target bitrate 245 Kbit/s, 9 = target bitrate 65 Kbit/s (requires --aactomp3)




since radio 3 has a high 320k format the best one for a radio 3 program is 



```
get-iplayer --mode=flashaacstd --aactomp3 --mp3vbr [COLOR="Red"]0[/COLOR] --get 12220
```

which gives a 245k mp3  [makes for very little loss on an mp3 player]

---

### Post by shantiq on 2012-07-20
**Also this to make radio program download so much easier**


 1. in terminal enter 
> alias getradio='get-iplayer -o ~/Music   --mode=flashaacstd --aactomp3 --mp3vbr 2 --get'

then again open 

```
gedit ~/.bashrc
```

 and enter at bottom

> alias getradio='get-iplayer -o ~/Music   --mode=flashaacstd --aactomp3 --mp3vbr 2 --get'

 and save

 2.    now to update your bashrc

```
. ~/.bashrc
```

3. From now on all you need is this



```
getradio   13434
```

 or whatever number you seek to download

 goes to your music folder as an mp3   [   change your 0-9 in --mp3vbr to suit your needs ]

**PS**   if you wish to keep the aac and not go to mp3    simply shorten the line above to

>  alias getradio='get-iplayer -o ~/Music --mode=flashaacstd  --get'

---

