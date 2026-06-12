---
title: "No Sound With Games"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by LiquidFlame on 2006-07-29
Ok, so I have sound working with everything else, video, music, flash, etc.  The only thing that I don't have sound working for is games.  I have read through the forums for a long time and I have not found an answer that has helped.  I've tried disabling the systems sounds, I've killed esd from command, made sure that alsa is installed, etc, but no luck.  I'm using Dapper right now and I'm trying to get sound to work with America's Army.  Granted that this is the only game that I have installed on my computer I want to get the sound to work with this because I figure that if the sound doesn't work with this game I won't be able to get the sound to work with other games.  My sound card is Sound Blaster Audigy 2 ZS Pro and I realize that there are a lot of problems with this sound card with Linux.  Any help would be great, but please do not post unless what you have tried has actually worked.  Thanks

---

### Post by CameronCalver on 2006-07-30
did you restart esd after
try this
```
killall esd
```
then ```
esd
``` if it worked it will do some weird sounds
If that works i can make a script for you so you just click on the icon and it will
go ```
killall esd
         esd&/home/username/path/todir/american/armyetc
```

---

### Post by LiquidFlame on 2006-07-30
Wow, I feel really stupid, that worked, could you show me the script to use please.

---

### Post by CameronCalver on 2006-07-30
Yes it is easy isnt it ok where is the game file eg
if the game is in /home/username/games/thegame
and the file is game
can you tell me the path to it and do you know about chmod and stuff like that 
if you dont ill tell you but once i have the patch i will write u a script which you can save in gedit and chmod +x it then save it somewhere then use Alacarte menu editor to put it where you want Easy

---

### Post by LiquidFlame on 2006-08-01
The path to the game is /usr/local/games/armyops/armyops
I don't really know any of the chmod stuff, sorry.  Thanks for the help.

---

