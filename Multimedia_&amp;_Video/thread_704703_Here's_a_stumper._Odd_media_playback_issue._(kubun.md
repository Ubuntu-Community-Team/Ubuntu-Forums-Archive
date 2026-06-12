---
title: "Here's a stumper. Odd media playback issue. (kubuntu)"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by kaens on 2008-02-22
Alright, let me background this by saying that I've searched all over the place, can't find anything, and I'm looking for places to start looking just as much as solutions.

So earlier I was messing around with X11 forwarding with ssh, figured I'd try running amarok off my machine that is currently acting as a fileserver. Didn't work too well, so I thought I would try sshfs. I accidentally hit usermod -G kaens fuse instead of usermod -a -G kaens fuse and lost all my groups.

Whoops.

So, quick reboot into recovery mode, check roots groups, add myself to all of those (except root), and back to trying things again.

Mount the remote machine through sshfs, put the music directory in my amarok collection, and try to play a song. It plays what sounds like aboud 64k (frame size?) repeatedly. The sound continues after I quit amarok,  and amarok's process didn't hang.

kmplayer will do the same thing with video (play a little audio on repeat while the video continues). gmplayer and mplayer will both play the audio fine with the video, until I quit.

Firefox will now only play flash videos for about 3 seconds before the playback freezes. 

If I start and stop video playback (or audio playback in amarok), it will layer the sound bite with whatever short clip would be at the new position in the file.

Sound will stop if I issue an artsshell terminate. Problem persists when artsd is restarted - not the same sound, but the symptom happens again as soon as I try to play anything.

I can't find any relevant logs, tried grepping through the output of lsof, etc. Reboot does not affect the symptom. 

If anyone wants some output put here or pastebinned, or thinks I should try something, or has any sort of clue what could be up please let me know. It almost seems like I have a blocked interrupt or something, which I'm not sure if that even makes any sense but seems to describe what's going on.

At least I like learning....

---

### Post by kaens on 2008-02-24
Maybe I should rephrase:

The strange problems started after trying to play a song in amarok over an sshfs mount.

Does anyone have any idea what I should be checking to find out what has gone awry?

---

