---
title: "Nero AAC (Linux Native Executable)"
date: 2008-10-14
forum: Multimedia Software
---

### Post by tuddy24 on 2008-10-14
Hi everyone!

Boy I'm loving Linux. It has been a pain in the rear learning new terminology and how Linux functions but I have hit a wall here and hope someone can help me. I realize that many people will not like the fact that I am attempting to use a proprietary codec to create my music but I've liked nero under windows because a) great sound quality for the file size -q 0.45, gapless playback on the ipod, and compatibility. I would absolutely love to use ogg vorbis but barely anyone supports it and I hate to say it but the ipod is a well engineered and designed little device that I want to continue to use.

Anyway, I download the newest version of nero's linux codec and learn the hard way that the executable files need to be in /usr/bin and have read write access. My question is how can I incorporate the codec with sound juicer? I have no idea how the gstreamer programing works. I've seen a how to on incorporating the win32 equivalents of the Nero codec with k3b using a wrapper script but this new nero codec is native to linux and I would like to use it. I'd be willing to make an addition to a wiki with all the details also if someone could help me get it going. Has anyone done this successfully? I have also tried without success to encode a .wav from the commandline just to see if I can get it to work but I got some sort of .wav error. I didn't write it down. I'm at work writing this.

I have tried the FAAC encoder under sound juicer and get strange warbling sounds so that is not an option. If mp3 had better sound quality and gapless playback I'd use that. And please no grip how to's, it doesn't recognize my cd-rom for some reason. Thanks!

Pete

---

### Post by cariboo on 2008-10-14
I found this post:

> BinaryMadman said

For the time being i'm using Grip with it, but of course there isn't a way to get tagging - think. Under encoder i chose 'Other', enter the neroAacEnc path, enter the encoder commandline '-if %w -of %m -br 256000 -2pass', and set the file type to m4a'.

Yes, that's a high bitrate and i have no clue if 2pass even makes a difference at that rate. :P It's so great that they finally brought a version out for Linux! 

In my opinion grip is a better cd ripper then sound juicer, as sound juicer is quite limited. Grip is available in the repositories.

Jim

---

### Post by mc4man on 2008-10-14
Here's several options for aac, either faac or neroAacEnc. I think the best use is nero with rubyripper (accepts -q settings, excellent naming, ect.

From what I've seen trying to change faac parameters for gstreamer is not to easy, defaults at 128k, main profile.

[http://ubuntuforums.org/showthread.php?p=5915181#post5915181](http://ubuntuforums.org/showthread.php?p=5915181#post5915181)

---

