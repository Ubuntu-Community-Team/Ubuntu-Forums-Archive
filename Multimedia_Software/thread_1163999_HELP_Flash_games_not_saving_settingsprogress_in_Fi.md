---
title: "HELP: Flash games not saving settings/progress in Firefox"
date: 2009-05-19
forum: Multimedia Software
---

### Post by squeakyneb on 2009-05-19
I am having trouble with many (if not all) Flash games saving progress, settings etc.

If I save the game, navigate away from the page then come back later, any save files have gone. One example is the game ["Sonny 2"]("http://armorgames.com/play/2900/sonny-2"). If I play up to the first save point, then go to the menu, the save is there. If I leave the page, and return later, all my progress is lost.

I tried downloading the game (in swf format) and opening with Firefox from the hard drive, but the same thing happens.

Opinions? Anybody else having this problem?

Thanks,
-Benny

---

### Post by squeakyneb on 2009-05-19
Bumpity

---

### Post by lovinglinux on 2009-05-19
Flash settings are stored under ~/.macromedia/Flash_Player/ and use the extension ".sol".

Launch a game, play it a little bit and close it, then check if the settings are saved there.

Most of the time I don't have issues with games settings on Intrepid, but some games uses some obscure method of saving it's settings, maybe using cookies.

---

### Post by lovinglinux on 2009-05-19
Please wait at least 24 hours to bump your thread. Bumping every hour will not help and is considered impolite. It wasn't the bump that made me reply. I was typing while you bumped. 

Anyways, check my previous post.

---

### Post by squeakyneb on 2009-05-19
I found them at ~/.macromedia/Flash_Player/#SharedObjects/S38DQMUE/cache.armorgames.com (for armorgames.com) and some other games have folders there, but not sonny. Im gonna play a bit, and experiment with manual file replacement if needed.

One idea I have come up with: What if it is not actually writing the save to disk? It would still appear as saved while in-game, as it is in RAM, but once you leave, it gets lost.

UPDATE:
After saving progress in Sonny 2, I could find no files referring to sonny in ~/.macromedia/Flash_Player or any sub-directories. I believe that it is not actually saving the game, or it is saving it to the wrong place.

Ideas?

---

### Post by lovinglinux on 2009-05-19
> **squeakyneb said:**
> I found them at ~/.macromedia/Flash_Player/#SharedObjects/S38DQMUE/cache.armorgames.com (for armorgames.com) and some other games have folders there, but not sonny. Im gonna play a bit, and experiment with manual file replacement if needed.

One idea I have come up with: What if it is not actually writing the save to disk? It would still appear as saved while in-game, as it is in RAM, but once you leave, it gets lost.

As I said, some games use different methods of saving settings and sometimes is really hard to find the file. I think is the case with this particular game or maybe the game is messed up or poorly coded. I doubt is a matter of not being able to save the settings, otherwise you would have problems with other games. Nevertheless you could try running Firefox from terminal and check if you get any errors while playing the game.

---

### Post by squeakyneb on 2009-05-19
> **lovinglinux said:**
> I think is the case with this particular game or maybe the game is messed up or poorly coded.
In the game comments, no one else has complained about save errors, and the game does otherwise seem very well made.

> **lovinglinux said:**
> Nevertheless you could try running Firefox from terminal and check if you get any errors while playing the game.
If I run 'firefox', FF opens up as expected, and the terminal goes back to waiting for another command, rather than waiting for the program to finish executing.

Thanks for the help, I have to go. I'll be back in this thread sometime tomorrow.

Cya
-Benny

---

### Post by squeakyneb on 2009-05-20
Bump from page 8

Still no progress with problem :(

---

### Post by squeakyneb on 2009-05-22
Bumping again.

Still no progress. I have avoided deleting cookies/cache/everything else, and it doesn't help at all. I tested the game on a mates Windoze machine, and it worked fine even after reboot.

I am now upset, as Windoze can do something Ubuntu can't :(

---

### Post by lovinglinux on 2009-05-22
> **squeakyneb said:**
> Bumping again.

Still no progress. I have avoided deleting cookies/cache/everything else, and it doesn't help at all. I tested the game on a mates Windoze machine, and it worked fine even after reboot.

I am now upset, as Windoze can do something Ubuntu can't :(

You could try playing the game with the standalone flash player

Version 9
[http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz)

Version 10
[http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz)

Extract the file somewhere and then look for the flashplayer archive under /flash_player_10_linux_dev/standalone/release/ and extract it to get the standalone player.

---

### Post by squeakyneb on 2009-05-23
I have downloaded and tried this with the standalone (version 10). It still had the same problem.

I am going to try version 9, just to be sure, but I don't think it will make a difference.

---

### Post by squeakyneb on 2009-05-25
BUMPing for flash games.

---

