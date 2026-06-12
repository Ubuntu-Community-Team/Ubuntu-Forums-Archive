---
title: "Video play back is stuck at 1.5-2x playback speed"
date: 2013-09-19
forum: Multimedia Software
---

### Post by Donnald_Heckelmoser on 2013-09-19
Hello all, 

I recently downloaded Ubuntu 12.04 to my Nokia Booklet 3G RX-75 Netbook style laptop.  I love it, and think it works great.  It has worked wonders for the speed and efficiency of a netbook that was bogged down and slow with windows 7.  On to my issue

I have been searching through this forum for 3 days know, trouble shooting a variety of different posts, and other websites potential resolutions to the issue of video playback. 

PROBLEM: video playback, for all browsers (web-based video playback) is at at least 1.5x spead, and i can not figure out how to resolve the issue

WHAT I HAVE TRIED:  
[LIST=1]
[*]I started with firefox as my browser. I removed it, added Chrome and tried again. the problem was not resolved.
[*]I added chromium, removed chrome, and tried again to play a video and the issue persisted.
[*]I added chrome back, and started playing around with the plugins. I would enable and disable different plugins and refresh the brownser, and none of the combinations solved the problem
[*]I started this process with the stock ubuntu video player setting (flash i guess), as a lot of the potential solutions I read talked about pulse audio, smplayer, vlc player, etc.  However, i did not have any of those downloaded at the time, so i could bot adjust the settings or kill the application in the terminal
[*]In turn, I added them, and tried to adjust the video playback none of it worked
[*]I started to check the bios screen in order to turn of the sound board, and put in a code within the terminal,but my bios screen (when i press f2) does not reference any audio sections.
[*]when I go into setting>sounds the only option to choose is the speaker *built in audio*
[LIST=1]
[*]I never thought it was a sound issue, the sound has always sounded fine, the only reason it is choppy is because it was playing at 1.5 speed
[/LIST]

[*]I want to say i tried a few more things, but there have been so many that I can't remember all the threads I read.
[*]I just tried ryhthmbox and it plays at 1.5 times speed as well.
[*]I tried Pandora Radio and it plays at 1.5x speed
[*]I noticed also, in rythym box that the sound cuts out at anywhere from 5-30 seconds of play.
[LIST=1]
[*]this does not happen in any of the other mediums mentioned above
[/LIST]
[/LIST]

Anyway, please help, I would like to be able to listen to music and or watch video because ubuntu has been so great otherwise. i should mention when I was using windows 7 this was not an issue with video (it would buffer from time to time, but not this)

---

### Post by peertje on 2013-09-25
Is this also the issue with movies on youtube? Maybe it helps installing/updating the flashplugin
```
sudo apt-get update
sudo apt-get install adobe-flashplugin
```
It can also be that it has to do with the plugin used by the browser. A quick google resulted into this suggestion:
[http://askubuntu.com/questions/141692/youtube-movies-are-playing-too-fast-with-chrome](http://askubuntu.com/questions/141692/youtube-movies-are-playing-too-fast-with-chrome)

---

### Post by Bucky Ball on 2013-09-25
*Thread moved to **Multimedia & Video**.*

Welcome. You might have more luck here. We'll be gentle. ;)

PS: You've gone from slow-motion Win to fast motion Ubuntu in more ways than one!

---

### Post by Donnald_Heckelmoser on 2013-10-01
Thank you for the response.  The problem I have when opening the terminal, at least in this case, as soon as I press enter after enetering in your text, it asks for the password for Donnald.  i am not sure what to type here, but in trouble shooting (i.e. my log in password) everytime I type something it immediately rejects it and asks me to try again.  I typically just kill the terminal and try again, with the same result.  

Any advice?

---

### Post by Donnald_Heckelmoser on 2013-10-01
Thank you, yes it seems like you were right, I got a response.  I hope this forum can help me.

---

### Post by Donnald_Heckelmoser on 2013-10-01
also, I linked to your article about the plugins, and i do not have the same three plugins that the user had.  i only have two.  one is the ppapi (out of process) and the other is the npapi. I have enabled and disabled them in every way imaginable with no results.  

Where would I go to get the third plugin?

---

