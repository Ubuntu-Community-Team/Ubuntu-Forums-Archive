---
title: "flash quits after a few seconds"
date: 2008-11-19
forum: Mythbuntu
---

### Post by elj4176 on 2008-11-19
mythbuntu 8.04 .21
This system has been working fine and I occassionally watch recordings through mythweb (not on local lan) using the flash player. Lately the flash will only play for a few seconds before quitting. I have tried using opera, mozilla, 
I have checked the myth logs, updated both systems and the issue persists.

Anyone have a fix or know where to look for the problem? 
Thanks!

---

### Post by pytheas22 on 2008-11-19
Which flash plugin are you using?  There should be three available: flashplugin-nonfree from Adobe, swfdec and gnash.  If you're using flashplugin-nonfree (you most likely are since it's the only one that really works), you could try reinstalling it by typing:
```

sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

Also, if you're using 64-bit Linux, Adobe just released a beta 64-bit flash plugin that you may have better luck with.  I can give you instructions on installing it if you're interested.

---

### Post by elj4176 on 2008-11-19
I was using the nonfree until I started having trouble. I am now using adobe flashplayer 10. I'll try removing it and going back to the non-free and see if it works again.

---

### Post by elj4176 on 2008-11-19
Purged all flash packages and using only flashplugin-nonfree now on the myth BE and this machine. Flash 9 is what the settings show now. 

Same problem. It shows ~16 seconds of video and then quits in botyh Firefox 3 and Opera 9.62. Could it have something to do with the version of ffmpeg on the myth BE?

---

### Post by pytheas22 on 2008-11-19
I don't think it has to do with ffmpeg, because I don't think Adobe's flashplugin uses that in any way.

Have you tried different videos with the same consistent results (crashing after 16 sesconds)?  Or is it just a certain video that's causing problems?

Also, if you create a new user account, do you by any chance have better luck with flash there?

---

### Post by elj4176 on 2008-11-19
I was guessing ffmpeg because it gets transcoded to flash on the BE and then streamed to the browser - correct? I'm grasping at straws at this point. 

I tried several different videos. Ones that I know worked previously. Transoded to nuv and mpg, They all quit at a different length of time but none goes past ~16 or 17 seconds.

I'll try from another machine on this network and then I'll try from 2 on the network local to the myth BE. 

I appreciate the help in tracking this done!

---

### Post by michande03 on 2008-11-19
had similar problem, occured when alsa was occupied in mediaplayer, pause did it aswell, but when full track stopped flash worked fine.

---

### Post by jMon54 on 2008-11-19
> **pytheas22 said:**
> Which flash plugin are you using?  There should be three available: flashplugin-nonfree from Adobe, swfdec and gnash.  If you're using flashplugin-nonfree (you most likely are since it's the only one that really works), you could try reinstalling it by typing:
```

sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

Also, if you're using 64-bit Linux, Adobe just released a beta 64-bit flash plugin that you may have better luck with.  I can give you instructions on installing it if you're interested.
I would love to know how to get flash working on a 64bit system.

---

### Post by elj4176 on 2008-11-19
ok - I tried on a freshly installed 8.04 system that has not even been on the web yet. Had to install flashplugin-nonfree. The video played for 30 seconds and then quit.

I also have a 64 install on my laptop and flash was working fine there but it is on its way to HP now to fix the dreaded hinge crack problem so I cannot test with it. I don't remember doing anything special to get flash working on it - mediabuntu repos I think.

I also have a mint system here that I could try...

edit:
Same problem on the mint system which leads me back to a problem on the myth BE while creating the flash stream.
I was watching the processes on the BE with the top command and while streaming the video ffmpeg was running as the topmost process and when ffmpeg disappeared from the top list the video stopped streaming.

---

### Post by pytheas22 on 2008-11-19
I think it's definitely fair to conclude that it has to be the BE, if you're having the same problem on multiple clients.

If you launch Firefox from a terminal, does it happen to dump anything useful?  Probably not if the problem is one the BE's side, but you never know...

> 
I would love to know how to get flash working on a 64bit system. 

Just type:
```

sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

Then restart Firefox.  This should do it.  Adobe's beta 64-bit plugin isn't necessary and is not yet that stable, although advanced users might be able to get it to work better than the 32-bit build.  But if you're new to Ubuntu and just want flash to work, go with flashplugin-nonfree.

---

### Post by elj4176 on 2008-11-20
I tested it on the local lan last night and it worked fine so it could be something with our firewall here. 

The terminal did not show any info at all and the flash stoppped streaming after a few seconds again.

I'll keep trying to figure this out and if I find something I'll post it back here in case anyone else has this issue.

---

### Post by elj4176 on 2008-11-21
This is beginning to drive me nuts. Not because I HAVE to have it working but because I seem to be the only one with the problem.
edit:
It seems that the flash streams fine if I have not transcoded the video yet. The source is .nuv and so is the result but there must be something in the transcode setup it doesn't like.

---

