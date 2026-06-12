---
title: "sdlmame on 10.04 problem"
date: 2010-10-25
forum: Mythbuntu
---

### Post by rlongfield on 2010-10-25
I am having a problem with sdlmame 0.136-0ubuntu2 on Mythbuntu 10.04.
When I try to run sdlmame from the command line I get an error message stating 'No games found. Please check the Rom path specified in the mame.ini file.'

I have updated the Rom path in /.mame/mame.ini to look like this:
rompath           $HOME/.mame/roms;/usr/local/share/games/sdlmame/roms;/media/Media/Roms/mame/roms

I have also tried just:
rompath           /media/Media/Roms/mame/roms 
As this is the location of my roms.

Regardless of what I set the rompath too I get the same error message.

However when I use the gmameui front-end I am able to play the games I want.

But I want to launch sdlmame from Mythtv so I kinda need the command line to work.

---

### Post by chipppy on 2010-10-25
Good Morning

> rompath $HOME/.mame/roms;/usr/local/share/games/sdlmame/roms;/media/Media/Roms/mame/roms
why the semicolouns? eg
> roms;
I will have a look at my machine when I get home to see if I can help you out some more.

In the meantime have a look through this older thread and see if there is anything in there to help
[HTML]http://ubuntuforums.org/showthread.php?t=1340191[/HTML]
specifically look at step 3 and 4 for where to put your ROMS and how to edit the sdlmame.inin file to tell sdlamae where the ROMs are located.  MythTV doesn't search for them like some gui's, it needs to be told.

Post your findings and I will try to help.

Cheers
chipppy

---

### Post by rlongfield on 2010-10-25
Thanks for the link. I'll take a look at it.

The first semicoloun was there so I put in the second semicoloun for my actual rom location. I did try the rom path with just my rom location but it made no difference.

---

### Post by rlongfield on 2010-10-26
So I checked out the link and everything is kosher that way. I have the rom directory setup in Myth properly and it sees the game roms just fine.

When I try to launch a game in myth it flashes the loading screen and then drops back into myth. I get the same response when I try to launch sdlmame from the command prompt telling sdlmame where the game rom is.

Example:
bert@myth-box:~$ sdlmame /media/Media/Roms/mame/roms/1944

I get this error output:

nffu.03 NOT FOUND
nff.04 NOT FOUND
nffu.05 NOT FOUND
nff.13m NOT FOUND
nff.15m NOT FOUND
nff.17m NOT FOUND
nff.19m NOT FOUND
nff.14m NOT FOUND
nff.16m NOT FOUND
nff.18m NOT FOUND
nff.20m NOT FOUND
nff.01 NOT FOUND
nff.11m NOT FOUND
nff.12m NOT FOUND
ERROR: required files are missing, the game cannot be run.
Ignoring MAME exception: ERROR: required files are missing, the game cannot be run.

To me it looks like sdlmame is unable to unzip the rom's zip file. Does that make sense? I know the rom works because I can run the game (in this case 1944) using the GmameUI front end without a problem.
I imagine this is the same problem that myth is running into when I try to launch a game from within myth


My original problem still exists where just running sdlmame still give me the can't find game roms error.

---

### Post by chipppy on 2010-11-06
Good Morning

Can you please attached a copy of your mame.ini file (should be located /etc/sdlmame/mame.ini

In the following part of Mythtv (Utilities/Setup ==> Setup ==> Media Settings ==> Game Settings ==> Game Players) can you tell me what is the setting for 
Player Name: ?????   (eg SDLMAME)
Type: ??????         (eg MAME)
Command: ????????    (eg /usr/games/sdlmame %s)
ROM Path: ???????    (eg /var/lib/mythtv/mythgame/sdlmame/roms)
has the tick the box for 'Allow games to span multiple roms/disks been ticked????

Cheers
chipppy

---

### Post by rlongfield on 2010-11-06
Hey Chippy,

Actually last night I was able to figure out the problem. The path was incorrect in the /etc/sdlmame/mame.ini file. I was making changes to ~/.mame/mame.ini

Now I have a completely unrelated problem but that is for another thread.

Thanks though, hopefully someone else with the same problem will find this and you answer.

---

### Post by chipppy on 2010-11-07
Good Evening

LOL its an easy one to make.  I still do it every now and then when setting up boxes.

Cheers
chipppy

---

