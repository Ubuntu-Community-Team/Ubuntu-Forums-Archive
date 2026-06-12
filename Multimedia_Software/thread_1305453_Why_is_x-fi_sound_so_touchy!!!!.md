---
title: "Why is x-fi sound so touchy?!!?!?!"
date: 2009-10-29
forum: Multimedia Software
---

### Post by Man with Hat on 2009-10-29
I have had so many problems running my X-Fi sound card since installing Ubuntu. I always seem to get it to a point where I think everything is working fine. I am even of the minority who have had a decent phone call over skype (I used the magic of ticking the digital switch I/O box in the ALSA mixer and then unticking it to get my mic to work. Makes perfect sense right?). I had problems before of having everything running great, but with no Ubuntu sounds. I finally solved that problem. Now I noticed that there is no sound in my media player. I was wondering if I just needed to tick or untick mute boxes etc. seeing as it solvd my mic problem (I still don't understand that). So I opened the mixer and all I did was move sliders and press mute buttons. Now there is no sound anywhere! WHY? WHY? WHY? Sound Card you are a pain! Does anyone own a hammer they can lend me, or at least have a tech answer to what on earth is going on here?

And yes I have left the sliders on a reasonable volume level and things are not muted. However it seems to have a mind of its own. I noticed that if I unmute things, the speaker in the system tray shows muted. I click on it and look at the ALSA mixer and the master is not muted!

---

### Post by Man with Hat on 2009-11-02
Ahhh 40 views and no replies. Does no one out there love me? :cry:

---

### Post by Webe12 on 2009-11-07
I have been running Ubuntu since version 6. And I have used Creative labs since the original Sound Blaster. They have always worked wonderfully for me. But I built a new machine when version 9.04 came out. All again worked well except for my sound. I have the Creative Labs X-Fi. It remains mute to this day.  I have tried both the 64 and the 32 bit versions, all the suggestions I can find, and nothing has made any difference. LSPCI shows that it sees the card but it keeps trying to use the hdmi from my ATI radeon cards for the audio using hda intel drivers. Unfortunately, I don't have the time to troubleshoot it between work, and school, and kids. May end up going to another sound card that is supported. From what I have been seeing for the last few years, if Creative can't support it's user community well I am quite able to take my money elsewhere. I'm needing midi support anyway with my video and audio work and Creative has all but cut that feature from their cards anyway. It is just a shame that they are treating their long term customers so. But then, it seems a lot of businesses are doing that now. Seems they have forgotten that repeat business will keep in business while one time sales are a flash in the pan and seldom let a business thrive. But then, that is just my humble opinion. That and 2 bucks may get you a cup of coffee.


Webe

---

### Post by Man with Hat on 2009-11-07
That sounds like my life story really. I used sound blaster ever since it made great noises on wolfenstein 3d :)

I stayed with Creative as they were crowned 'the best' and same as you, I needed the MIDI stuff for my music. I can't imagine using Sibelius without having my keyboard plugged in. 

Don't know if you have tried it, but 

[http://www.moobash.com/Blog/?p=611](http://www.moobash.com/Blog/?p=611)

worked for me, until the most recent bount of mute! 

I'm thinking of switching sound cards when I can afford to do it. I'm not into gaming as I was in the past, but the annoying thing is that if I didn't need the MIDI, I would just use the onboard sound. How bad can it be?

---

### Post by Webe12 on 2009-11-08
HI no I hadn't but from reading, it sounds like an exercise in futility. I have installed the latest version of alsa and it still doesn't work. It at least sees the card now and identifies it, no errors are occurring when sound is suppose to be happening, but not a peep is coming from it.  And yes it is not muted anywhere that I can find. I do sound and video editing as a hobby and I need midi or I would just in the ole Sound Blaster from another machine. It still may come down to that. I have not been very impressed with the X-Fi. But then I am not really pushing it at all. Matter of fact I have just made up my mind to do just that and pull the SB live from another machine. My M-Audio has the midi and the sound should work.

:lolflag:

---

### Post by Webe12 on 2009-11-08
Just checked the LSPCI and it is stil trying to use the snd-hda-intel kernel instead of the ctxfi kernel.

---

### Post by Webe12 on 2009-11-08
Well the SB Live works great under Ubuntu 9.10 not worth a **** under Windows Vista. Guess I'll have to run both cards, X-FI for Vista and SB Live for Ubuntu.

---

### Post by Man with Hat on 2009-11-08
> **Webe12 said:**
> HI no I hadn't but from reading, it sounds like an exercise in futility.



I know exactly what you mean, that's what's so frustrating though. I have installed my x-fi drivers through 3 different install blogs/threads. Each one essentially did the same thing, but had a different effect on my x-fi. This last one was the last one that I used and all my sound worked afterwards. Up until I dared to click on boxes in the mixer!

I know that you've already switched cards (I think I my ex-wife has my audigy somewhere around her place, so I'll try sometime too) but did you turn off the on-board audio in bios? That may have stopped it trying to use that. Might even be worth it for your live card, assuming that you haven't done this already :)

---

### Post by Webe12 on 2009-11-08
My motherboard doesn't have a built in sound card so I don't have to contend with that. Since the Vista only sees the X-FI and Ubuntu only sees the SBLive, I only have to move the audio speaker cable between them. I'll get or build me a combo cable so I don't have to do that anymore either.

---

### Post by Man with Hat on 2009-11-18
Thought I'd just mention if you're still reading these, I just upgraded to Karmic Koala and the sound card is working great. Didn't have to do anything. Mind you its still early days, but its nice that it just worked!

---

### Post by Webe12 on 2009-11-21
I'm glad yours is working. I checked further and my version is X-FI extreme. It is covered. If I had the platinum or one of the others it would probably work. But I have sound no matter which  OS I boot in.


Thanks for checking back. I was wondering.

---

### Post by Man with Hat on 2009-11-21
No worries, I hope it all works out for you. Mine is the X-Fi Extreme gamer I think. It has only loaded the drivers to work 2 speaker though, not 5. Seeing as I currently am just using the crappy little speakers in my monitor, that doesn't currently bother me. I don't think I have ever felt the need to plug 5 in, I just got too old to hard core game like that anymore. I don't know if your message means that you checked Karmic out by loading it, but for some reason it seems to start up with the volume on 0. I had to move the slider...

---

### Post by Webe12 on 2009-11-23
Okay, I just did the update and now my sound is gone again. This is just too weird!

---

### Post by Webe12 on 2009-11-23
I'm sorry, I'm running version 9.10 Karmic 64 bit. After the upgrade, it says it is muted but moving the slider has no effect. Gonna have to check the pulseaudio settings again. That was the problem last time.

---

### Post by Webe12 on 2009-11-23
I have unmute it in two places. First the General mute, and then the pulseaudio has to be unmuted as well.

---

### Post by Man with Hat on 2009-11-23
> **Webe12 said:**
> I have unmute it in two places. First the General mute, and then the pulseaudio has to be unmuted as well.


So its working now? I miss having a mixer to look at for all of the different functions, but I'm too scared to install one!! :icon_frown:


I have only had one problem where it muted itself for some unknown reason, but that was a simple fix!

---

### Post by Man with Hat on 2009-11-24
ARRGHHH!!!

Spoke too soon. Now I have started the same problems that I was having with Jaunty!! I now have sound in media player, but the ubuntu sounds have disappeared. I'll see if I can't do anything about it. Damn you creative!! Why won't you just make these cards good for linux?

---

### Post by Man with Hat on 2009-11-24
:cry: AND NOW I'VE LOST EVERYTHING :cry:

---

### Post by Webe12 on 2009-11-24
I feel your pain!  I trust you'll figure it out.

---

### Post by Webe12 on 2009-11-30
Well did more research and found that if I install OSS4, it will run my X-FI Extreme card. So I did just that. Followed these Ubuntu directions at [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) and let it install using the deb file and all started working again. Not sure what all works with it because I have found that OSS isn't supported by all the programs. But I check this site when I run into a problem. [http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4)

Cheers;)

---

### Post by Man with Hat on 2009-12-01
Thanks mate. I had someone else suggest OSS4 because I have been thinking of throwing my X-fi on the road and using my on board audio for sound. I'll give this a crack first though. I really think that Freedoom has something to do with my problems. I think it is causing some irreparable fault somewhere.:)

---

### Post by cascade9 on 2009-12-01
> **Webe12 said:**
> My motherboard doesn't have a built in sound card so I don't have to contend with that. Since the Vista only sees the X-FI and Ubuntu only sees the SBLive, I only have to move the audio speaker cable between them. I'll get or build me a combo cable so I don't have to do that anymore either.

*grumbles at creative* There is this you can try-

[http://www.softwarepatch.com/utilities/creative-live-driver-vista.html](http://www.softwarepatch.com/utilities/creative-live-driver-vista.html)

> **Man with Hat said:**
> ARRGHHH!!!

Spoke too soon. Now I have started the same problems that I was having with Jaunty!! I now have sound in media player, but the ubuntu sounds have disappeared. I'll see if I can't do anything about it. Damn you creative!! Why won't you just make these cards good for linux?

Creative *grumble grumble* just got worse the more they dominated the market. I've had issues with creative stuff even under windows- my old SBlive card had issues with even XP. I got around the issues in the end, but it left such a bad taste that I decided to avoid creative from then on. 

Its just a pity that chaintech left the sound card busines, the chaintech AV-510 and av-710 were really nice, cheap soundcards. 

Just out of intrest, have you tried getting the linux drivers from creative?

---

### Post by Man with Hat on 2009-12-01
Yes, this was one of the things that worked for me. I have had times where my sound card was working perfectly. Then for reasons beyond my understanding..... BAM...... No sound. It seems to disappear over a couple of hours or days. I can get sound in Guest login and then not. I don't understand    ](*,)

---

### Post by Man with Hat on 2009-12-01
The more I think about it, the more I hunger for the Windows update driver function. Whenever I had driver issues, I could always just re-install them with a click and then it was fine. Linux makes me research someone's guide with a bunch of code that I don't understand and just have to trust.

---

### Post by cascade9 on 2009-12-01
> **Man with Hat said:**
> Yes, this was one of the things that worked for me. I have had times where my sound card was working perfectly. Then for reasons beyond my understanding..... BAM...... No sound. It seems to disappear over a couple of hours or days. I can get sound in Guest login and then not. I don't understand    ](*,)

I am guessing..but possibly a kernel update? I have to reinstall my sound drivers when I update my kernel. (not using creative but realtech here) If creative actually opened the code for the X-Fi, I think you wouldn't have a problem, but thats not going to happen any time soon....

As for windows driver update, I've tried that and some other 3rd party drive update software a few times, and generally got 'what a mess. Its downloaded a heap of windows crap I have removed for a reason, and it got the wrong drivers for my video card' (they worked, sort of, but were ancient).  

I've heard of the window driver update doing mean things like removing that hack driver for the SBlive on vista/win7 as well. If it actually replaced the driver with a working one, fair enough, but it doesnt. I simply dont trust it, its one of the things thats made me move from microsoft to linux. 

I can see why you would want it though, I guess you've tried a million and one things to fix your problem. The 1st time I lost my realtech I did that, but ended up just reinstalling the driver and that worked. I guess 95/98/2K/XP did teach me something, if in doubt reinstall the driver/hardware/OS. In that order. LMAO

---

### Post by Man with Hat on 2009-12-01
> **cascade9 said:**
>  I guess 95/98/2K/XP did teach me something, if in doubt reinstall the driver/hardware/OS. In that order. LMAO


Haha exactly what I am thinking!! I never upgraded higher than XP sp3. I just changed the order one day and went OS/driver/hardware and that was how linux was born on my computer!! Mind you it was a problem that was going to require me to reinstall windows as I had messed my registry a bit. I thought I'd give linux a go. It still impresses me, but there are just those little niggling things I wish weren't there.

I have to say that I love all of the new Windows 7 TV commercials we get:
"you can open two windows side by side!"
"You can tell it not to go to this website again"

I'm sure windows 7 is more sophisticated than this, but its target market apparently isn't

BTW, how do you update the kernal? I have just updated to Karmic, so I thought everything was up to date. Also isn't update manager supposed to handle 'everything'?

---

### Post by cascade9 on 2009-12-03
Updatingthe kernel in ubuntu is done by both GUI and command line. From command, 'sudo apt-get update' will get all the updates for your system, including kernel updates. As for the GUI tool, thats the update manager. Same thing, different interface. 

No idea if there has been kernel updates for 9.10 yet, I havent installed it. Its also possible that other updates are killing your x-fi sound. Next time you update, have a check of the things is updating.

---

### Post by Webe12 on 2009-12-05
> **cascade9 said:**
> *grumbles at creative* There is this you can try-

[http://www.softwarepatch.com/utilities/creative-live-driver-vista.html](http://www.softwarepatch.com/utilities/creative-live-driver-vista.html)



Creative *grumble grumble* just got worse the more they dominated the market. I've had issues with creative stuff even under windows- my old SBlive card had issues with even XP. I got around the issues in the end, but it left such a bad taste that I decided to avoid creative from then on. 

Its just a pity that chaintech left the sound card busines, the chaintech AV-510 and av-710 were really nice, cheap soundcards. 

Just out of intrest, have you tried getting the linux drivers from creative?

I tried that patch a while ago but no success. But thanks for the thought. As to the latest patch from creative, yes and I get an error about not being apple to find some file. I don't remember which so i gave that up. But I have it working under OSS so I am back to one audio card, the X-FI Extreme and running under both Vista 64 and Ubuntu 64 version 9.10 gnome and KDE.

Now to just get more familiar with how OSS works. So far everything I have found for it runs from the command line. Bit of a bother but it works. Found some other links as well to get it to work with ALSA apps and pulseaudio. 

[http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4)

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

