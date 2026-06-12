---
title: "&quot;login screen ready&quot; sound problem"
date: 2009-03-22
forum: Multimedia Software
---

### Post by cripou on 2009-03-22
I changed the desktop login sound through preferences>sound and it works perfectly. Now, when I try to change the "login screen ready" sound through login window preferences (by selecting the ogg I want to play) and press play it doesn't work, it plays something but it's all noise, it's not the sound it's supposed to be.

anyone has an idea?

---

### Post by Jn1 on 2009-03-24
I'm having the same problem too. When I select an ogg and press play, I get the noise(while Rhythmbox can play it). wav-files play fine though.

---

### Post by Jn1 on 2009-03-24
The problem is that gdmsetup uses aplay which doesn't support.You could solve it by editing /usr/lib/gdmplay and replace aplay by another player. gnome-sound-properties doesn't have this problem


****      8408  0.2  0.7 183116 29436 ?        S    19:51   0:00 gksu /usr/sbin/gdmsetup
root      8409  2.4  0.8 195708 31524 ?        Ss   19:51   0:07 /usr/sbin/gdmsetup
root      8462  0.0  0.0   4020   576 ?        S    19:56   0:00 /bin/sh /usr/lib/gdmplay /usr/share/sounds/ubuntu/stereo/bell.ogg
root      8463  0.0  0.0  49588  2220 ?        Sl   19:56   0:00 /usr/bin/aplay -q -N /usr/share/sounds/ubuntu/stereo/bell.ogg

/usr/lib/gdmplay :
#!/bin/sh
/usr/bin/aplay -q -N $@ 2> /dev/null

aplay: 
File type (voc, wav, raw or au).  If this parameter  is  omitted
              the WAVE format is used.

---

### Post by natrik on 2009-04-17
It seems GDM uses /usr/lib/gdmplay to play audio files.  That simply calls /usr/bin/aplay.   But what happens when you type this in a terminal:

```
aplay /usr/share/sounds/ubuntustudio/stereo/desktop-login.ogg
```    Try that with any ogg file, and you get static.  Specify ogg file type -- "-t ogg" -- and it will complain.  

[size=3]**[color=#33aa00]Here is one solution: Get yourself 'sox' and all its formats ... [/color]**[/size]
```
sudo apt-get install sox libsox-fmt-all
```


[size=3]**[color=#33aa00]... Edit the file [FONT="Courier New"][COLOR="Black"]/usr/lib/gdmplay[/COLOR][/FONT] [/color]**[/size]
```
#!/bin/sh
/usr/bin/aplay -q -N $@ 2> /dev/null

```

[size=3]**[color=#33aa00]...to look like this: [/color]**[/size]
```
#!/bin/sh
#/usr/bin/aplay -q -N $@ 2> /dev/null
/usr/bin/sox -q $@ -t alsa default 2> /dev/null
```

All I did is comment out the call to 'aplay' and use a reasonable player 'sox'

**HOW could it have been overlooked that gdmplay can't play oggs?!?**  Most of the gnome sounds are oggs now right?

Anyway, I have No More Static.

-- Nate

[size=3]**[color=#33aa00]See also:  [THIS COMPREHENSIVE GUIDE]("http://ubuntuforums.org/showthread.php?t=205449") [/color]**[/size]

---

