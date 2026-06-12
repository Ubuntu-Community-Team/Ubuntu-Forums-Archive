---
title: "totem, vlc not working, mplayer has issues..."
date: 2008-08-09
forum: Multimedia Software
---

### Post by shadarack on 2008-08-09
Okay, I can't find a thread that covers my problem, so I'm going to post a new one.

Totem does not work for me - apparently, it cannot find any of it's codecs? Which is odd, because it was working just fine one day, then I ran a system update, and suddenly, no codecs, nothing will play through Totem. When I try to open a video file with totem, I get the following message, more or less:

Video codec 'Advanced Video Coding (H264)' is not handled. You might need to install additional plugins to be able to play some types of movies

This message varies in small ways, depending on the type of video encoding of the file I'm trying to open.

VLC has not been working since I upgraded to hardy. I've fiddled around with a few things and now VLC will open, but when I try to play a file with it, I only get sound.

Mplayer will only work when I use the -vo x11 option, and then it refuses to play fullscreen - when I use the fullscreen option, it does not size the video up, and fills the rest of the screen with black.

I've tried uninstalling and reinstalling all of these programs and many of their supporting packages, but still Mplayer is the only one that even slightly works. I suspect I may have made things worse, but I'm at my wits end - could someone who knows more about this help me please? I just want to watch my videos...

---

### Post by pjhudson on 2008-09-13
I wish someone would answer because I have the same issue-- totem has not worked once for me, not even a simple mp3 file plays in it.... it doesn't work as a plugin in firefox either.. I'm trying to figure out how to uninstall it but not having any luck--  I'd rather go with mplayer, vlc and real.

---

### Post by markbuntu on 2008-09-13
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

If you just want the plugins and w32codecs and libdvdcss2 to play restricted formats follow this guide:

[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

