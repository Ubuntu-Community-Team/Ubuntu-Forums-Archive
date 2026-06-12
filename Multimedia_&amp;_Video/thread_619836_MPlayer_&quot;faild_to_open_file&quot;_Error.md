---
title: "MPlayer &quot;faild to open file&quot; Error"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by SoulScythe on 2007-11-21
Okay, this is a strange issue that has been going on for a couple of days now and I'm not 100% sure what made it end up like this. There was an mplayer listing under the auto-update a few days ago, but the change log said that there were no modifications, so I'm not sure....

Anyway, I have mplayer set as the default "Open With" option under most media files on my system. I used to be able to just double click something like an .avi and it would start up in mplayer just fine. However, every time I do it now it mplayer opens up with an error popup saying "Failed to open file [filepath here]."

If I open a file through mplayer's internal browser it will open up fine. If I change the file's option to open with the command "mplayer" it'll open as well (although the window doesn't have the information/progress bar and I can't right click it to mess with properties). I'm not sure what's keeping these things from opening up normally, and I'm almost ready to just fully uninstall + reinstall the package to see if that fixes it. Sadly, if that works I'll never know what was wrong with it and I'll never learn.

So I've finally decided it may be best to give people with a little more experience a crack at this. Does anyone know what the problem could be, how to fix it, or how to avoid making it happen? I'm running Feisty Fawn and using the most recent version of mplayer if anyone needs that info.

Thanks in advance!

---

### Post by stunner on 2007-11-21
I've had trouble double-clicking on filenames with spaces (although I was passing them through another script before sending them to xine/mplayer).  Same thing here?

Also, if re-installing works, that's great.  Re-installing programs with apt or synaptic is generally quite painless.  Might as well give it a try.

Edit: To be specific, it looks like you're having trouble with gmplayer.  gmplayer provides the gui that gives you progress windows, menus etc - just FYI.

---

### Post by SoulScythe on 2007-11-22
The listing under Synaptic is just mplayer, does that still count?

The space thing isn't the problem. I tried renaming some files to have no spaces, or using different variations, and it still gives me the error. I also marked mplayer for a complete uninstall and reinstall, and it still didn't solve it.

---

### Post by stunner on 2007-11-22
It still counts :)  The listing is mplayer, but open up a terminal and type in 'mplayer', then type in 'gmplayer' and you will see the difference.

What about the folders that the files are in (and the folders they're in, and the folders they're in, and so on)?  Any spaces in any folder names up the tree?

If it's not the space thing, then I would suggest opening a terminal, cd'ing to a directory with some files in it, and running 'gmplayer -v -v -v <nameoffile>' and looking at the error output that comes out in the terminal.

---

### Post by eggdeng on 2007-11-22
I think you might have two instances of Mplayer installed at different locations. I've seen this sort of thing happen after installing from source without removing the original package.

---

### Post by SoulScythe on 2007-11-22
Okay, so I went through and took out the spaces and that solved it on the files I tested. Is there any way to get it working with the spaces again? It was completely fine until a little while ago, and if I can't revert it there are going to be a lot of video files I'll have to rename.

---

### Post by Freiburg05 on 2007-11-22
Hi, I have a similar problem, if I try to open file which contains special characters in the filename (like [xxxx]_yy_[zzz].avi ) I'll get the error mentioned in this thread. Removing those character from the filename (rename the file to: xxxxyyzzz.avi) will solve the problem. This occurs since the last update a couple of days ago. I'm running Feisty. Anyway I'm also having problems playing .rmvb files for another reason I haven't found yet. Last update seems not very good, does someone know if it can be reverted?

---

### Post by polarbear10 on 2007-11-23
Just chiming in with the same error, completely uninstalled and re-installed no change.  Removed spaces from path and filename and whamo off we go!

Looking forward to a little fix....

---

### Post by stunner on 2007-11-23
Pretty tired right now but I will throw something out for the time being.

Make a file called opensesame.sh
```
touch opensesame.sh
```

Now we're going to open it up...
```
cat > opensesame.sh
```



Copy and paste the below, and then hit control+c
MAKE SURE YOU HAVE /usr/bin/gmplayer
```

#!/bin/bash
MPLAYER_BIN=/usr/bin/gmplayer
exec $MPLAYER_BIN "$*"
```


Make it executable
```
chmod +x ./opensesame.sh
```



And lastly set the proper file association in nautilus so that video files open with opensesame.sh.

---

### Post by SoulScythe on 2007-11-23
This seems to fix it, thanks!

As for the problem itself, how would I go about reporting the bug or checking to see if it's already a known issue? I'd assume it is, but I'd like to make sure because it seems like there are more then a few people experiencing this..

---

### Post by stunner on 2007-11-24
You can search for bugs in [launchpad]("https://launchpad.net/ubuntu/+bugs").

In this case, someone just today submitted the same bug: [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/164709]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/164709")

---

### Post by satn3ver on 2007-11-24
Everything was working fine until the mplayer update. 

Luckily the opensesame.sh fix worked, but it sucks that we need to do that.

Can't wait for the fix(hopefully).

---

### Post by stunner on 2007-11-24
I should mention that this problem doesn't occur for me on Gutsy.

---

### Post by SoulScythe on 2007-11-24
That's good to know. I've been meaning to update, but I haven't really had the time to sit down and do it. If there's no fix coming soon I may as well just go for it, huh?

---

### Post by hype on 2007-11-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/164709](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/164709) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I did this [ bug report](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/164709).
The version of mplayer that causes the prolem is the "gutsy-backports" one.

The fun thing is only gmplayer has this prolem.If i open the movie with mplayer (right click > open with > other > mplayer) it start fine, ut without the gui-bling and usefullness.

I'm considering uninstalling compiling mplayer et compile from source to see if is a packaging problem or not.

Edit: Hmm, weird, i tried removing gutsy-backports via synaptic, but afer update, it doesnt show any update available, tho the backport repos must have changed loads of apps , no?

---

### Post by Hellaxe on 2007-11-26
I Have the same stupid error but not for all files. There are files that are opened well. This happens in Feisty and in Gutsy.
Another problem is the subtitles. To see subtitles i have to load them manualy.
This sucks.

---

### Post by mmcmonster on 2007-12-04
Just wanted to chime in that I'm having the same problem on two different computers running Gutsy. :-(

---

### Post by dtfinch on 2007-12-16
To workaround the problem by making gnome pass mplayer the actual file path rather than constructing some nasty file:// url for it to choke on:

Open /usr/share/applications/mplayer.desktop in a text editor as root
change "Exec=gmplayer %U" to "Exec=gmplayer %F"

---

### Post by mattress on 2007-12-19
dtfinch's fix worked perfectly. I'm running a very bloated Gutsy system for what it's worth.

Thanks D.

-m

---

### Post by dtfinch on 2007-12-21
I guess the %f should be a %F, so that when you select multiple videos and open them all at once, it'll play them in sequence rather than spawning multiple instances.

---

### Post by kelvin spratt on 2007-12-21
I suffered this problem I removed Mplayer complete by purging it from the system, installed Mplayer but not the blue skin, Installed skin from Mplayer site now perfect again. check their site for the bug on latest version, always check the official site first before trying to fix your machines works for me 95% of the time. Better than google as most suggestions lead you up the garden path.

---

### Post by Juno on 2008-02-08
This work for me:

1. Right click on video file 
2. Choose "Properties"
3. Choose "Open with" tab
4. Choose MPlayer
5. Exit


:)

---

### Post by Tryfon on 2008-05-21
> I suffered this problem I removed Mplayer complete by purging it from the system, installed Mplayer but not the blue skin, Installed skin from Mplayer site now perfect again. check their site for the bug on latest version, always check the official site first before trying to fix your machines works for me 95% of the time. Better than google as most suggestions lead you up the garden path.

Could you be more specific? A series of commands would be welcome.

---

### Post by DasCrushinator on 2008-05-21
dtfinch;s method works for me, did you give it a try?

---

### Post by Tryfon on 2008-05-21
I tried dtfinch's method but the line in my mplayer.desktop file was already %F. I also tried changing it to %U but without any success. Any idea?

---

### Post by DasCrushinator on 2008-05-21
> **Tryfon said:**
> I tried dtfinch's method but the line in my mplayer.desktop file was already %F. I also tried changing it to %U but without any success. Any idea?

Interesting, what version of Ubuntu (Gutsy, Hardy, etc.), MPlayer, & 32bit or 64bit?

What exactly ar e you having problems with?

---

### Post by Tryfon on 2008-05-23
I'm using Hardy 32bit with mplayer installed from the synaptics manager. I've even tried to change mplayer's skin but with no success. The problem remains the same. When I try to open a file that has space in its name I get the error message: Failed to open file:///media/..... so on. It only opens through mplayer's internal browser.

---

### Post by DasCrushinator on 2008-05-23
> **Tryfon said:**
> I'm using Hardy 32bit with mplayer installed from the synaptics manager. I've even tried to change mplayer's skin but with no success. The problem remains the same. When I try to open a file that has space in its name I get the error message: Failed to open file:///media/..... so on. It only opens through mplayer's internal browser.

I really am at a loss for what to do then.  I never had to do the skin change, just the method about editing the file.

---

