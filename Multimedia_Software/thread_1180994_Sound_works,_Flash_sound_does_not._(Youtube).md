---
title: "Sound works, Flash sound does not. (Youtube)"
date: 2009-06-07
forum: Multimedia Software
---

### Post by NovaKnowledgeNow on 2009-06-07
Ok, before anyone else bashes me, I did some searching on the issue, and I have tried a couple things first and so this was the next resort.

I tried 
[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)
 
It did not work for me...

When I get to the 3rd step, there is no 'FIREFOX_DSP=”none” 			 		'   for me to delete. The file is simply blank and empty.


I'm running Ubuntu 9.04
I do not believe I have a sound card. Instead I'm running USB speakers off my USB drive.
I get sound when I try to play audio over my Rythembox music player, but not when watching flashvideos such as Youtube. I can see the video, but can't hear the audio.

Any ideas?

---

### Post by NovaKnowledgeNow on 2009-06-07
Well, after hours of pouring into, I think I'm just going to wipe the hard drive and try hardy haron and if not there, go back to free spire or windows(ehh)...

---

### Post by Ed_Ziffel on 2009-06-07
I already did that: reinstalled 8.04 lts and still have the same problem.  That is not going to help.  

I got the same results as you did with all the other links some of which asked you to install various updates and patches as well as different codecs which I did. Same issue with no such file as you mentioned.  

After a day of on and off trying, it seems the best option is to use a windows machine to view flash files.  That is a real downer considering I'm trying to view tutorials for linux.

---

### Post by NovaKnowledgeNow on 2009-06-13
Sigh, Well i guess on the one hand, it's nice knowing I'm not the only one with this problem.  I've tried everything else I can think of. I'm going to put a different sound card in and try different speakers.

Unfortunately, I'm trying to set up my system with 2 striped 80GB drives. I don't think it's possible to have 2 RAID drives and still split them so I can have 2 OS on there...


Even if I COULD, it still REALLY defeats the purpose of having Linux. I don't want to use it as that "oh hey guys you want to see something really neat?!" When my friends come over. I just want to set up and have it do everything Windows can, but faster/quicker!

I watch a lot of flash videos(YouTube). If I can't get it to work, it's almost pointless to have Linux.

:(


I never got around to trying out FreeSpire again, but i did try 8.04. It too, had the same issue with the Flash audio. 

I'm really hoping one of the Guru's here can help us out.

---

### Post by xc3RnbFO8P on 2009-06-13
Uninstall **Swfdec** (if you got it installed)
and install **Adobe flash**
[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

---

### Post by meho_r on 2009-06-13
> **NovaKnowledgeNow said:**
> Ok, before anyone else bashes me, I did some searching on the issue, and I have tried a couple things first and so this was the next resort.

I tried 
[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)
 
It did not work for me...

When I get to the 3rd step, there is no 'FIREFOX_DSP=&#8221;none&#8221; 			 		'   for me to delete. The file is simply blank and empty.


I'm running Ubuntu 9.04
I do not believe I have a sound card. Instead I'm running USB speakers off my USB drive.
I get sound when I try to play audio over my Rythembox music player, but not when watching flashvideos such as Youtube. I can see the video, but can't hear the audio.

Any ideas?

That's an old link. You don't even have integrated sound? Don't get it. However, problems only in flash. Which Ubuntu, 32bit or 64bit? From where did you install flash and which one (Adobe?) What about other browsers, Epiphany, Opera, maybe Midori etc.? These are some infos you should post so people can provide an answer. 

BTW, I wouldn't go with Freespire, rather try some other distros like Mandriva, Linux Mint, Fedora etc. if Ubuntu fails you.

---

### Post by kostkon on 2009-06-13
> **NovaKnowledgeNow said:**
> Ok, before anyone else bashes me, I did some searching on the issue, and I have tried a couple things first and so this was the next resort.

I tried 
[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)
 
It did not work for me...

When I get to the 3rd step, there is no 'FIREFOX_DSP=”none” 			 		'   for me to delete. The file is simply blank and empty.


I'm running Ubuntu 9.04
I do not believe I have a sound card. Instead I'm running USB speakers off my USB drive.
I get sound when I try to play audio over my Rythembox music player, but not when watching flashvideos such as Youtube. I can see the video, but can't hear the audio.

Any ideas?
Basically, the solution is simple. You need to install the *PulseAudio Device Chooser* (using *Synaptic*).

Run it and it will put its icon in your system tray. Left-click on it and select *Volume Control*. Then select the *Playback* tab.

Put a flash video playing (for example a YoutTube one, one with sound of course) in *Firefox* and you should see its audio stream listed in the *Playback* tab. Right-click on this stream and select *Move Stream...* and in the list that will appear select your USB speakers. Hopefully, *PulseAudio* will remember your choice from now on and thus you will not need to do this again.

You can set your USB speakers as the default output device in your system by selecting the *Output Devices* tab, right-clicking on your speakers entry there, and enabling the *Default* option.

For more info regarding sound check [this helpful thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

Hope that helps.

---

