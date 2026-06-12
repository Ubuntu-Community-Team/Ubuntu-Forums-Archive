---
title: "persisting problems with 8.10"
date: 2008-12-14
forum: Mythbuntu
---

### Post by wayover13 on 2008-12-14
8.10 seems to be the buggiest mythbuntu I've used so far. This is on a system that started with 7.04 and was dist-ugrade(d - to use the old Debian-speak) several times to what is now 8.10.

Video playback has been horrible after the upgrade to 8.10. Lots of stuttering, screen flashing momentarily to something other than the recording/video I was watching. What a disappointment after the way things seemed to be working so well in previous releases.

I tried several different video cards in this machine, including the onboard, thinking this could be a hardware problem. I had essentially the same video corruption problems with all cards I tried. Now I'm back to my avi PCI card.

Two main problems make the system almost unusable at the moment. First is that when I try to watch recordings or live TV the frontend dies. I see OpenGLVideoSync problems atthe end of the myth frontend logs. I have no idea how to diagnose that. I did some internet searching and turned up very little (someone suggested a NoDRI option in xorg.conf--about the only relevant thing a cursory search turned up).

So I can't watch TV or my recordings now. In addition, the system is simply freezing up from time to time. Keystrokes to try and go to a VT don't work, I  can't ping the machine. It's truly locked up. Nothing but a hard reboot is possible. Last time this happened (couple of hours ago) I see in /var/log/messages that mythfrontend segfaulted.

Not sure what to do here. I've even begun to contemplate such severe measures as doing a fresh install of mythbuntu (a huge headache since I'd have to reconfigure everything, rescue various media files, etc.) Suggestions for troubleshooting the problems will be appreciated.

I should mention that I've just now tried playing a recently-made recording under XFCE using both VLC and mplayer. The playback seems to be fine in both, even when I go fullscreen. This really does seem to have something to do with the frontend.

In closing, lemme just ask what is the protocol for reconfiguring the xserver these days? I started with Debian several years ago when it was dpkg-reconfigure xserver-xfree86. Then, under Ubuntu it changed to dkpg-reconfigure xserver-xorg. I'm reading things now that suggest that manual configuration is no longer the way to go, and that xorg is supposed to configure everything for you. Is it worht my while to try reconfiguring the xserver to see if this might have some effect? If so, how's it done these days?

Thanks,
James

---

### Post by frankleeee on 2008-12-14
You might list your complete setup and the extra cards you have for help. If it was me I would backup what you want to save and do a fresh install.

---

### Post by wayover13 on 2008-12-15
Below is some relevant info about the cards. I had an older nvidia agp card in there and that was working just fine for ca. 1.5 years. Once I upgraded to 8.10 I started having the video problems and decided to try the other cards listed below (the ATI and SIS: you'll undoubtedly understand that the Brooktree refs are for my capture card).

VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

On the NoDRI option to be added to xorg.conf, information about which I found while researching this problem. With that option, playback of recording does work. The video actually even looks much improved over what it has been since I upgraded to 8.10. But if I try to watch live TV with that option in xorg.conf, the system will show a small amount of the program with increasing picture distortion until the system finally locks up hard (requires hitting the power button to power off the machine, which is frozen and impervious to any input).

James

PS This is a P4 2.0Ghz with 1 GB RAM and 2 IDE hard drives (@ 80 GB and 160 GB).

---

### Post by Poyntz on 2008-12-15
two things that would help us help you:
1. change the topic of this thread to the name of your problem. ie, **[intrepid ibex] poor video playback** or something similar. 
2. pastebin your /var/log/Xorg.log file and put the link here
Type ls /var/log/Xorg* to find the name of this log file.

To me your issue seems to be graphic driver related. Try **System -> Administration -> Hardware Drivers** and see if the latest driver for your card is listed.

---

### Post by wayover13 on 2008-12-15
A cursory inspection doesn't reveal any way for me to change the topic of this thread. Isn't that typically something only forum mods can do? If the thread's title were to be changed along the lines you've suggested I'd want to make it something like "[intrepid ibex] poor video playback, etc" or something like that since I am unable to make a solid connection between the playback problems and the system lock-ups I've seen.

I've been using online help, including this forum, for my Linux problems for well over 6 years now and this is the first time I've seen the verb "pastebin." I'll have to look further into what that means. I of course have web pages where I could post the referenced output and to which I could provide a link, but it seems you may be referring to something else. Anyway, I'll take a look at Xorg.log output to see if there's anything relevant there.

A look under Applications > Administration > Hardware Drivers reveals that no proprietary drivers are in use on this system. That doesn't surprise me at all since both ATI and SIS video drivers for Linux have long ago been developed and seem to work effectively (unlike, e.g., the community-developed nvidia drivers). Incidentally, I am currently using the ATI video card for playback/live TV.

I should also mention that I've been updating the system not less than weekly since I upgraded to 8.10 in hopes that fixes for my system's problems might appear in the repositories. So all modules should be up to date.

Thanks,
James

---

### Post by wayover13 on 2008-12-15
[http://wayover13.pastebin.com/m30b2f5ba](http://wayover13.pastebin.com/m30b2f5ba)

I should mention that this is the content of /var/log/Xorg.0.log _after_ I deleted the file /etc/xorg.conf and rebooted (to see what, if any, effect, that would have). The fronted still crashes whenever I try to play recordings or watch live TV.

James

---

### Post by tgm4883 on 2008-12-15
It may be worth using mythbuntu-log-grabber to get some logs and post them, then give us the link here.

---

### Post by wayover13 on 2008-12-15
Ok. I've just tried reverting to the onboard SIS for video output. The frontend now doesn't exit unceremoniously when I try to watch recordings or live TV. I'll have to see what effect, if any, this will have on the system lock-ups I've been seeing.

I consider this a temporary resolution to my problem. It's temporary because the onboard video output looks pretty lousy compared to the output of either the ATI card I've been trying to use or the older nvidia card I had in there when display problems began.

My preference would be to use the ATI card since the driver support for these seems better than for nvidia cards--especially older cards like the one I've been trying to use. Any further suggestions on diagnosing the problem with the ATI card?

I'll look into mythbuntu-log-grabber. Hadn't heard of it until now.

Thanks,
James

PS I did a system update just prior to switching from the ATI add-in card back to the onboard video output. The bit of viewing I've done so far indicates that there may be some improvement in playback. More on that later. But as I said, the picture quality of this onboard video stinks as compared with the add-in cards I've used (when they're working).

---

### Post by wayover13 on 2008-12-15
Just threw in a different nvidia agp card I had laying around (geforce2 MX 400). Still some problems with video corruption on playback of recordings (horizontal streaking across the screen every so often). But again the frontend doesn't just die when I try to playback recordings or watch TV. I'll see what happens with lock-ups with this. Picture looks better than it did under the onboard SIS video.

James

---

### Post by wayover13 on 2008-12-16
So far the system is performing almost as well as it did when I first set up Mythbuntu about 1.5 years ago. I do still see some glitches in the playback, but it's not nearly as bad as it was immediately after I upgraded to 8.10. No hard lock-ups since I swapped out the ATI card yesterday either.

Why things finally seem to be resolving is a bit of a mystery. I had initially decided the poor quality of playback was related to the legacy nvidia agp video card (geforce2 mx 200) I had in there. I swapped that one out for the ATI card. The video had the same poor playback quality with the ATI card. Then I tried the onboard SIS video. Same poor playback quality with the onboard card. So trying 3 different video cards had no effect on the poor video quality. They all had pretty much the same video output glitches.

I finally decided to have another go at using the ATI card, since, on top of the unwanted video effects (regular momentary screen flashing, some stuttering) the SIS video quality was lowest of the 3. That's when I started to see the hard system lock-ups, i.e., when I shut off the onboard video and tried again using the ATI card.

Why putting in another legacy nvidia card should resolve anything is beyond me. The agp card I dropped in yesterday is not much different from the original one I swapped out when I first started having problems (it is geforce2 mx 400 as opposed to the original mx 200 card). Maybe some fixes or updates to the nv driver were made in the interim?

I can only guess. I'm just going to go on the assumption that computer gremlins wanted to wreak havoc with me for a couple of weeks, and that now they've decided to leave me so they can go torment some other poor soul. I hope it's not you.

Thanks,
James

---

### Post by RedMD on 2008-12-21
wayover13,
It is interesting that we've tried the exact same thing.  I've spent way too much time (>5hrs) experimenting with ways to get my geforce2 MX200 to work with intrepid (it had resolution issues), only to finally give up and try a spare radeon 7000/VE card.  Needless to say, the radeon card has different problems (framerate, inc CPU usage, etc).  I've tried everything from compiling binaries for the nvidia card (i.e. from the nvidia site) to modifying my xorg.conf file.  Thanks to your experience, I'm going to try yet another graphics card.  Hopefully, one that works. 

For anyone else reading this post the bottom line:
**The geforce2 MX200 and the radeon 7000/VE have some serious driver issues in ubuntu intrepid (8.10).**  I suggest you try a different video card and don't waste your time (I've lost nearly a day trying a host of "solutions."

---

### Post by davidgeeee on 2008-12-23
Wow, I have been beating my head against the wall for a week now since the last updates.  It worked fine before that.

I don't show anything in my "Administration/Hardware Drivers" utility.  Does that mean I don't have a driver?  

This is a Mythbuntu setup and I could send my log grabber logs if someone could tell me how the upload or attach them.

Thanks in advance...

---

### Post by davidgeeee on 2008-12-23
Hey TGM4883,

     I have alot of similar hardware and setup you have can you help me?

> **tgm4883 said:**
> It may be worth using mythbuntu-log-grabber to get some logs and post them, then give us the link here.

---

### Post by tgm4883 on 2008-12-24
> **davidgeeee said:**
> Wow, I have been beating my head against the wall for a week now since the last updates.  It worked fine before that.

I don't show anything in my "Administration/Hardware Drivers" utility.  Does that mean I don't have a driver?  

This is a Mythbuntu setup and I could send my log grabber logs if someone could tell me how the upload or attach them.

Thanks in advance...

Once you gather the logs with mythbuntu log grabber, click the button to submit the logs, then post the link here that you get from the program.

---

### Post by davidgeeee on 2008-12-25
> **tgm4883 said:**
> Once you gather the logs with mythbuntu log grabber, click the button to submit the logs, then post the link here that you get from the program.

Well, I think I have more problems now.  My Mythwelcome won't show the Mythfrontend anymore and I can't get to the Mythbackend setup anyway that I have tried.  I can run the frontend on a different computer though and the Mythbackend IS working.  Hmmmm....

Here is the link to the logs...

[http://mythbuntu.pastebin.com/f5dc5459c](http://mythbuntu.pastebin.com/f5dc5459c)

Hope you or someone can help.

---

