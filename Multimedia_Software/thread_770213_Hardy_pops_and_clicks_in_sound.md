---
title: "Hardy: pops and clicks in sound"
date: 2008-04-27
forum: Multimedia Software
---

### Post by svaens on 2008-04-27
Hi guys, 

I wondered if I could ask if anyone else has had this problem, and if there is a solution?

My symptoms are: 

playing sound via any program, be it Rhythmbox playing mp3, or vlc playing .avi, gives me problems. The problem being that any activity in the operating system; minimizing windows, browsing internet, and worse, viewing the System Monitor causes pops and clicks in the sound. Very annoying and not something you want to listen to. Which means that if you want to listen to music or watch a video, you have to make sure you don't do anything else with your computer at the time. And even then, you get the occasional small pop or click. 

anyone know what could be causing this? I have only noticed this since installing Hardy yesterday. I installed it clean after having before had Gutsy on my machine (without the said problem). 
I must say, my only let down with hardy. Besides the sound problem, it has been an improvement over gutsy for me. But this sound problem is not so very nice. 

Thanks in advance for any replies and/or info!

---

### Post by svaens on 2008-04-27
Actually, I wonder if it couldn't be a case of something taking all my CPU. 
Although I don't quite understand what I'm seeing when I look at the CPU history in the System Monitor, I find this strange:

Note: I can see what I see through the panel little panel System Monitor Applet.

1. Opening the application System->Administration->System Monitor
increases my cpu usage from a normal 18% to 100%
What is the use of looking at system resources through this application if by doing so you distort the cpu usage out to the max! And it MUST use so much, because this app is the one which causes so much damage to my sound!

2. when I look at the Processes list, I don't find any process taking up 100%. Does the System Monitor exclude itself from this list?

3. I notice Pulseaudio has had a very large amount of CPU Time. Which is strange, because as it sounds so bad, I've only had it on for 2 minutes or so whilst testing, then turn it off. And it is up there with firefox usage. 
firefox 35 minutes
pulseaudio 20 minutes

4. I have metacity running (not compiz, as I turned it off via the appearance Preferences->Visual Effects dialog) and I can't see compiz running somehow... so that is not taking needed cpu cycles. 

5. I tested this using the Ubuntu Hardy Live CD, and having the System Monitor open and viewing the CPU History only showed it running at a smooth 30%.  Playing an MP3 using RhythmBox was mostly fine, except if i really moved things around on the desktop vigourously did I get some sound disturbance. 

I guess I am kind of grasping at straws... I would like something to blame, as then I could just remove it.

---

### Post by mcwizard on 2008-04-27
I'm having a similar problem.  It seemed to be related to compiz at first so I disabled it. it doesn't pop/click as much now but I suppose that's related to using less cpu cycles. Is the sound buffer to small maybe? This didn't happen in hardy beta, but I was using alsa then, now I have to use the pulseaudio sound system.

---

### Post by svaens on 2008-04-27
Another update, 

I have noticed that there is no problem with Totem Movie Player. 
Usually I use VLC. And there is still a problem with this, in that there are pops and pauses when I am doing something. Minimizing etc. 

However, I have modified my xconfig a bit, and there is maybe less of a problem now. But, like i said, there is still a bit of a problem which seems to show itself more if i use vlc. I wouldn't however say this is strictly a vlc problem, as this problem has been showing itself also with RhythmBox.

---

### Post by BattlePanic on 2008-04-27
I have noticed a significant amount of popping and clicking when playing sound under Hardy.

The event-triggered sounds in Pidgin seem to pop and click every time they're played.  I've also noticed it under the Totem media player.  Rhythmbox seems to suffer no problems, however.

I don't listen to much music while using Ubuntu so my experience is limited and I only really notice this problem when system sounds are played, such as in the case of Pidgin.  Although I would notice the occasional popping and clicking under Gutsy, the issue is much worse under Hardy and seems to happen every single time Pidgin plays a sound.

If I go to System -> Preferences -> Sound all the sound output settings are set to 'Autodetect' and if I test each there is a noticeable pop as soon as the test tone is played.  While there are other options aside from 'Autodetect' for sound playback, the only ones that are currently selectable are "ESD - Enlightened Sound Daemon" and "PulseAudio Sound Server"  If "ESD - Enligtened Sound Daemon" is selected, the test tone doesn't produce any pops or clicking but if using the "PulseAudio Sound Server" there again is a click as the test tone begins to play.  This leads me to believe there is a issue with PulseAudio.

****** UPDATE ******
I just realized that I might not have been able to select the other sound playback options because I had Rhythmbox open with playback paused.  I just tried it again and now I'm able to select the other playback options including ALSA.  I also came across [this post]("http://ubuntuforums.org/showthread.php?p=4787472") which suggested reverting to the ALSA setting.  I tried switching to ALSA and now I don't seem to get any pops or clicking.  I'd still like to see if there's another solution to this problem by reconfiguring PulseAudio.

---

### Post by spodesabode on 2008-04-30
Hello All. I'm having the same problem. However, to my (partly) trained ear, the clicks and pops are associated with minor pitch distortion too. This suggests a timing issue too.

Could there be an underlying issue with the timing mechanism in use for the sounds cards?

I'm using an Intel 81801G (ICH7) HD Audio, on a Realtek ALC882 PHY. This is onboard my Shuttle. It was working fine under 7.10 and I did an upgrade rather than a clean install.

I vaguely recall having a simular problem with Fedora 8, which had PulseAudio, and the problem was solved when I killed PulseAudio. I *think* I've killed it on this Ubuntu install, but still have problems :)

I hope this helps, I use this machine for a lot of media, so I'll be annoyed if I have to revert.

---

### Post by teseglet on 2008-04-30
Never had a problem before Hardy and have the same crackling and popping and jerky screen transitions as other are having now.  I had to disable all ALSA and PulseAudio access via System/Preferences/Sound and strictly use OSS and all problems have disappeared.  A side benefit I noticed is that even with Gutsy and Amarok the first song I would play after opening the program would always have a slight stutter at startup.  With OSS (have to change it in Amarok/Settings/Configure Amarok/Engine/Output plugin) even that problem has disappeared.

---

### Post by Teloid on 2008-05-01
I have same problem after upgrade from 6.06 to 8.04. First I seen, that default Xserver is Xgl, not Xorg, In my case Xgl take to much CPU for drawing widnows, and sound goes realy baaad. Then I remove package xserver-xgl, and Xorg back, but sound problems still alive, at any graphical work, such window drowing, animation at browser and etc. I'm using ALSA(I beleave that :) ) and don't use compiz(I beleave that :) ).

---

### Post by mivo on 2008-05-01
This fixes it:

In *System -> Preferences -> Sound*, change everything to ALSA. Then start VLC and go to *Settings -> Preferences -> Audio* and check "Advanced Options" (right lower corner). Then choose "ALSA audio output".

That fixes the stuttering. If you have a problem with sound only working for one application at a time, download the **alsa-oss** package and add aoss before the command in the appropriate application launcher.

---

### Post by spodesabode on 2008-05-02
That doesn't fix it for me. Doing the test sound (that high pitched noise) on OSS/ALSA etc. gives me the same results, lots of pops and crackles. No difference with Compiz off.

I am using 64-Bit here. I've got the 32-Bit Hardy Live CD - I'm tempted to boot up and see if I get the same problems.

---

### Post by spodesabode on 2008-05-02
I've just booted the machine up using the 32-bit AND 64-Bit LiveCD's and they all have the same problem, even on ALSA. :(

I'm beginning to wish I hadn't upgraded now.

---

### Post by rolandixor on 2008-05-02
well, I have a similar issue. It's like this. I have C-media card, and it shows up as 3. I have gotten on of these to work, but only for playing music etc. System sounds are ignored an I'm wondering if it's ESD? but then if pulseaudio is installed, shouldn't ESD at least be disabled?

---

### Post by Happibun on 2008-05-03
My problem is that I have no sound playback from any of the multimedia programs. My sound card is working, I can hear system beeps and stuff streamed online through firefox.

I've just upgraded to Hardy Heron from Gutsy, and I had no problem in Gutsy.

Thanks

---

### Post by Teloid on 2008-05-03
Maybe clicks coused by non-realtime priority of sound server? But how to check it and change if it possible? I figured out that Xorg's field "PR" at **ps** or **top** output changed from 15 at Dapper to 20 at Hardy.

---

### Post by Teloid on 2008-05-03
Yeah, I solved my problem! I don't use Pulseaudio, because it isn't worked after update, and fails when, I try to use it, therefore I use ALSA.
But today I tried to reanimate pulseaudio, by reading logs and googling. When I make pulseaudio as prefered sound system all clicks go away.
Solving for M-Audio Audiophile 2496 - [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

**update**
Not at all. Amount of clicks went down, but not disappear.

---

### Post by rolandixor on 2008-05-05
Well, seems pulseaudio has killed my sound.

---

### Post by rolandixor on 2008-05-05
and I should point out, I had it working partially before. one of the C-media options was loud and FULL of static. The two others worked all fine if used together in sound options... but system sounds didn't work. It gave a system beep for errors, and totem could play wav files, but yet none of the system sounds worked!!!

frustrating...

---

### Post by Teloid on 2008-05-05
Selected sound system is pulseaudio?

---

### Post by rolandixor on 2008-05-05
Nope. Pusleaudio didn't work, but I've got a feeling it's confusing things...

---

### Post by PARO on 2008-05-06
I was having the same skippy, poppy, sound, but it's 100% better for me now.  "End process" to pulseaudio in system monitor and restart your application and see if that's your problem.  If that works you can uninstall pulseaudio or remove it from your sessions start up and set OSS or ALSA as your default for playback as mentioned before.  Hope this helps.

---

### Post by tetsuc on 2008-05-06
Hmmmm.... I have the same issue but nothing that I have tried (all from this thread) has helped. Removing pulseaudio means that I can't hear anything at all. Pops/clicks in sound with VLC but not with movie player... when I try to play the test sound in sound preferences i get the following error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

any ideas...?
Cheers

---

### Post by deformlux on 2008-05-07
> **PARO said:**
> I was having the same skippy, poppy, sound, but it's 100% better for me now.  "End process" to pulseaudio in system monitor and restart your application and see if that's your problem.  If that works you can uninstall pulseaudio or remove it from your sessions start up and set OSS or ALSA as your default for playback as mentioned before.  Hope this helps.
I was having the same issue with skippy sound, with a variety of applications, and switching playback devices to ALSA (or anything else) didn't work until I terminated the pulseaudio process.  Seems obvious, I know, but I guess that's what I get for being a noob.  Anyways, killing pulseaudio and restarting applications with ALSA for everything fixes everything.

---

### Post by locketine on 2008-05-07
pulseaudio was working ok for me but after grabbing some 50 updates that appeared today it started causing horrendous popping noises as described. Minimizing windows or even sometimes just dragging them is enough to cause the distortion in music playback. I switched amarok over to alsa and the problem hasn't come back at all.

---

### Post by carpex on 2008-05-08
I had the same problem with clicks and pops after upgrading to Hardy. Selecting OSS for EVERYTHING in preferences->sound fixed it for me. It definitely has something to do with Pulseaudio.

---

### Post by spodesabode on 2008-05-09
Well,

I tried increasing buffers in ALSA, but to no avail.

I've tried fiddling with pretty much everything under the sun. In the end, I realised I had a spare Creative Live! Value sound card in my cupboard, so I've plugged this in and PulseAudio is working a charm, with no skips, pops or crackles.

ALC882 on this Shuttle? Just doesn't work :(

---

### Post by ginbuntu on 2008-05-10
I also think it is Pulseaudio's fault. I changed everything to esd and sound worked great, Without any glitches or clicks.

good luck

---

### Post by Cornova on 2008-05-10
The steps on the post in the link below worked for me.

[http://ubuntuforums.org/showpost.php?p=4830940&postcount=16](http://ubuntuforums.org/showpost.php?p=4830940&postcount=16)

---

### Post by Chief_Frankus on 2008-06-02
I had downloaded and tried Ubuntu Studio and the clicking and popping was horendous. I installed regular Ubuntu and the problem was gone. Using WINE, ive been trying to get ASIO to work under Jeskola Buzz, but as soon as I installed the wineasio driver my ol friend click'n'pop came back. Under Buzz, he clicking and popping goes away when I dont use ASIO.

EDIT: and I tried doing everything the post above me said, and I tried switching to all possible drivers. No luck,

---

### Post by svaens on 2008-06-02
I still have some popping and clicking.... It really seems to depend on cpu usage, and pulseaudio is probably the cause. 
However, there have been fixes posted for this (which I have not fully tried out) including the install of the newest kernel. though by the way, replacing the kernel (upgrading to 2.6.24-17) doesn't fix this problem completely (for me). I installed this via the ubuntu auto-update feature just last week, and it didn't make much of a difference in that respect.
see link:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

As it wasn't guaranteed to fix things completely, I didn't bother with it yet. 

I have just read today though, that there is going to be some new fangled functionality in PulseAudio, and though there is no mention to this bug that we have all seen, the name of this new functionality is promising. Glitch-Free! Good eh! Apparently will be in the next release of PulseAudio, being 0.9.11. 

read here:
[http://0pointer.de/blog/projects/pulse-glitch-free.html](http://0pointer.de/blog/projects/pulse-glitch-free.html)

I look forward to the new update (whenever that may be) of PulseAudio, and hopefully no more problems...

---

### Post by leifjonny on 2008-07-18
WORKAROUND: Disabling the 3D-driver gets rid of this problem for me, sound is perfect again. I have a "EVGA GeForce 8400GS 256MB DDR2" graphics card.  System/admin/Hardware Drivers and disable the NVIDIA driver or uninstall nvidia-glx-new.

---

### Post by lintoon on 2008-08-21
Hi everyone, I stumbled on this post while looking for an answer to the popping/clicking noise in Hardy.  I think I've found a solution.

-Go to System - Preferences - Power Management
-Select the General tab
-Untick "Use sound to notify in event of an error"

Hope this helps.

---

### Post by eitama on 2008-09-11
Killing pulsound did it for me.

---

### Post by svaens on 2008-09-11
yeah well.. i'd like to stick with pulseaudio. It promises a new future for sound in linux ;) Who knows if it will be, but things could definitely be better. Perhaps it makes it! 
When we get the gitch-free in Ubuntu (intrepid will get it i think, and hopefully soon hardy)  and it is configured correctly, i'm betting things will be looking (sounding) good!
see here for more details:
[http://ph.ubuntuforums.com/showthread.php?t=866965](http://ph.ubuntuforums.com/showthread.php?t=866965)

see section "Q. If PulseAudio is already installed, why do I need this guide?"

perhaps that explains why so many of us have had problems.

---

### Post by svaens on 2008-09-11
Actually.... i just decided to act as I say, and install the rest of pulseaudio, and configure it properly. 

So i did this (according to the instructions i posted above):

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

and checked out what the results were... 

1. My skype no longer worked at all
2. My flash sound no longer worked at all. 

Before, at least, I could use skype if not using any other sound apps. 

"Bummer" I thought. 

But i continued, to see if i could find solutions for this. And I did. 

This flash fix, one can find in the repositories:

**libflashsupport**

This immediately fixed my flash. No restart or relogin required. 

Then, to fix my skype, make sure that alsa was being routed through pulse, and set skypes configurations to use 'pulse'. 

I followed the instructions here:

[http://www.pulseaudio.org/wiki/PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup")

That fixed my skype!!!


Not only that, for the first time, I can use every application using sound at the same time!!! I can call out with skype while having firefox open that had a flash page (i had to close firefox before now to use skype).

A Big improvement!!

I'm liking pulse so far!

---

