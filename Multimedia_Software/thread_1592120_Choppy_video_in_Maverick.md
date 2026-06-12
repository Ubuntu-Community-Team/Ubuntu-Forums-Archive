---
title: "Choppy video in Maverick"
date: 2010-10-10
forum: Multimedia Software
---

### Post by nechus on 2010-10-10
Everything was OK when I first installed the Maverick release candidate. After some updates, video got choppy, as if my laptop didn't have enough memory to play it. Video also gets really messed up sometimes, and the image stops for a second, and it gets pixelized, and I can hear the last words of the movie repeated. Or I start a movie, and it starts at a point that is not the beginning, or completely freezes.

Not a Compiz problem, because I disable it but I still have the problem.

What can be causing this?

My laptop is an Acer Aspire 5738
Processor: Intel Core Duo T6500 @ 2.10 GHz
RAM: 3024 MB
Intel Integrated Graphics

---

### Post by P4man on 2010-10-10
what media player are you using? Might be worth trying a few like smplayer (<- my personal favourite), VLC, etc and see if the problem is the player, or if its something else (probably video driver related?). Also try different movie formats.

Lastly,  make sure you dont have any processes that have gone out of control hogging cpu or ram. Check system monitor or top.

---

### Post by iMerlin on 2010-10-10
Also experiencing choppy video on my 64-bit Maverick. Running on i5-750 with nvidia geforce 260gtx, 8G ram.

Everything was peachy in Lucid - but now my recent machine feels like it's been thrown here from the stone age.

It happens in VLC, Totem, mplayer, smplayer. So I'm ruling out the cairo dependancy, since smplayer doesn't depend on it.

Quite possibly the nvidia drivers - I'll try to install the latest one manually when I can...

---

### Post by nechus on 2010-10-10
It happens to me in all players, from Totem, VLC, GnomePlayer, Xine, etc.

---

### Post by aeroegnr on 2010-10-10
I had a similar experience.  Actually, my audio feedback is choppy as well (using Rythmbox).  I had no problem with 10.04 and audio/video.

My system is an ASUS 1001p

---

### Post by nechus on 2010-10-10
I give up. I followed P4man's suggestion and checked several video formats but, as usual, when you try to test something everything works fine. But the choopy video seems to be more frequent in avi files, though I also had some of it with rmvb files.

Besides, I was watching an avi file and opened an srt file with the subtitles in Totem. The video messed up completely. It froze and there was a black area on the player screen.

As for CPU or RAM hogging apps, no app was doing this, except Compiz, which was using just two percent of the CPU.

---

### Post by sendblink23 on 2010-10-10
I'm using right now 9800GTX+ on my freshly installed 10.10 x64 and all my videos play 100% fine(tested also full screen) - even on the basic movie player & as well on vlc

I tested several mkv & avi movie files

The driver I used was simply: System > Administration > Additional Drivers
Nothing else was changed, just upon installing the OS I selected the option to install all the codecs

---

### Post by nechus on 2010-10-10
I was playing an avi file on Xine media player and it froze for almost a minute when I selected a subtitle file. The I got a message: The number of discarded frames is too high. Your system can be slow, inapropiately optimized or just too loaded.

Oops! The message just popped up again.

Actually, I'm running the 32 bit version of Ubuntu on a 64 bit computer. I'll give 64 bit Ubuntu a try, but then I think I'm gonna have problems with flash and some apps are not available for 64 bits. :S

---

### Post by ToastBusters on 2010-10-11
I'm having this issue too. It doesn't matter what video player I am using. Even animated gifs are choppy, and programs are occasionally unresponsive. I'm on 64bit and this is a desktop, not a laptop. My gpu is nvidia 385GTX.

I had no problems with 10.04. Any help would be appreciated.

Thanks!

---

### Post by iMerlin on 2010-10-11
Also stutters on animated gifs for me. Nice catch.

---

### Post by P4man on 2010-10-11
There doesnt seem to be a lot in common here.. nvidia and intel graphics.  Googling I came across this:
[http://andrioid.net/lucid-to-maverick-upgrade-problems](http://andrioid.net/lucid-to-maverick-upgrade-problems)

Any chance you guys here are also using Avant? Are you using compiz desktop effects or metacity with compositing, and if so, does it help if you turn it off?

---

### Post by iMerlin on 2010-10-11
Disabling composition helped. Seems to point to X11 composite rendering or graphic drivers.

Edit: I do not consider this a solution. Just a work-around until the cause can be found.

---

### Post by ToastBusters on 2010-10-11
> **P4man said:**
> There doesnt seem to be a lot in common here.. nvidia and intel graphics.  Googling I came across this:
[http://andrioid.net/lucid-to-maverick-upgrade-problems](http://andrioid.net/lucid-to-maverick-upgrade-problems)

Any chance you guys here are also using Avant? Are you using compiz desktop effects or metacity with compositing, and if so, does it help if you turn it off?

I don't know what Avant is, but I have compiz off and it didn't help. That was the first thing I tried. No compositing, nothing. And it's still choppy. I do have the nvidia driver installed, but it was choppy before I installed the driver too.

[edit] I should also point out that this is a fresh install, not an upgrade.

---

### Post by iMerlin on 2010-10-11
You sure metacity isn't doing any compositing?

In gconf-editor, under "apps" > "metacity" > 'compositing_manager'. Should be disabled.

---

### Post by P4man on 2010-10-11
Also make sure desktop effects are completely disabled, not just compiz. By default they are on. System > preferences > appearance > visual effects. Set it to NONE.

Not that this is a real solution but at least it would help identifying the problem.

---

### Post by yavez on 2010-10-11
Same problem here with 10.10 (happening since the alphas) video slowing down, playing choppily, sound messed up, skipping and garbled.  Reboot, everything working fine...for a time, and then it's back again, like the system is struggling under a heavy load, even though it's not.  Repeats in all media players (Totem, Vlc, Rhythmbox etc).   10.04 works without a hitch on the same files, same machine and specs.


Hope someone finds a fix for this (I'm too impatient.  I installed Crunchbang (Alpha 2) :) )

---

### Post by ToastBusters on 2010-10-11
Desktop effects are on "none" and metacity compositing_manager is disabled. As I said, these were the first things I tried.

If there is anything else you would like me to try please let me know. I would really like to get this working. :)

---

### Post by ModernTenshi04 on 2010-10-11
Just thought I'd throw in on this.

My machine is rocking a 2.8Ghz Core i7 and a Radeon 5770 with 1GB GDDR5 VRAM, 8GB of RAM.

I installed the RC of 10.10 Friday afternoon.  I went with the video card driver Maverick suggested upon initially booting.

While playing back some .mkv anime files I have, video playback was choppy, almost like there was a vertical sync issue of some sort.  When I boot back into Windows 7 Ultimate to play the same file, I get smooth playback without a problem.  When I play the file on my MacBook Pro (2.5Ghz Core 2, 512MB nVidia 8600M GT), playback is also fine.

I tested VLC, Totem, Miro, and Mplayer under Ubuntu 10.10, and experienced video choppiness at the same spots in each player.

VLC was used while under Windows 7 Ultimate, Mplayer OS X Extended while on my Mac.  Again, both had no issues with smooth playback of the video files I tested.

The video files were all playing off my external WD hard drive.

I've uninstalled Ubuntu, but might give it another go now that the official build is out, and moreso now that I know about Microsoft's disk utility that can be used to reclaim other partitions for the main C: partition.  Needless to say, my weekend with my desktop was sort of a pain in the ***.  :P

I was using the 64-bit version.

---

### Post by nechus on 2010-10-11
YES!!! YES!!! P4MAN IS RIGHT!!!!

AVANT IS TO BE BLAMED FOR ALL OUR MISERY!!!!

I turned Compiz off before and it didn't help. Now I turned off AWN and everything is working fine!!

We have to tell the Avant guys!

---

### Post by ToastBusters on 2010-10-11
I don't have avant installed and still slow as ever.

---

### Post by iMerlin on 2010-10-12
I've also confirmed this on my machine, without Avant running. I hate problems like this. Lacking common identifier, no bug report to file... argh!

Edit: Ended up removing my OS all together and installing Sabayon. Hated it, then installed Maverick fresh - smooth as Lucid was.

---

### Post by CarpKing on 2010-10-12
> **ModernTenshi04 said:**
> My machine is rocking a 2.8Ghz Core i7 and a Radeon 5770 with 1GB GDDR5 VRAM, 8GB of RAM.

I installed the RC of 10.10 Friday afternoon.  I went with the video card driver Maverick suggested upon initially booting.

You may not be experiencing the same problem.  The proprietary drivers for ATI cards (fglrx) have a known problem with vsync anytime compositing (desktop effects) is enabled.  Video playback is better with the open source drivers (the ones installed by default), but 3d is slower, especially on newer cards.

---

### Post by Philetjosie on 2010-10-12
Get the same problem here with a Dell 510m Inspiron laptop, with Intel graphic driver.
It is a fresh install of 10.10, previously working perfectly fine with 10.04. 
All players are having the same problem.
I just have noticed that there is a similar problem when reading an mp3 file with Rhytmbox, the sound appends to have some choppyness (very light, but real). Therefore, I'm wondering if the problem does not come from the audio decoding, rather than the video decoding ?
But I have not found any other clue. No solution seems to have been found yet, considering to reinstall 10.04 (which has other problems with intel graphic card, but with workarounds).

---

### Post by Dmck23 on 2010-10-12
Hi All, Having the same problem on a sony Vaio VGN-NS10E since the upgrade to 10.10, i've tried a couple of different players but the all seen to have chopping video and sound. I had no problem in 10.04.

I don't have compositing manager running on my machine and have tried switching of effects and AWN to no avail.

Has anyone managed to come up with a fix to problem.

---

### Post by nechus on 2010-10-12
Here are some snapshots of my system monitor while watching a video file on my laptop.

The first two snapshots show that everything is running smoothly. The video is OK.

In the last two snapshots some process is hogging the system resources and the video gets choppy. The problem is that I can't figure out what process is doing this. Whenever I clickk on the Procesess tab, all processes seem to be sound asleep, except mplayer (around 14%) and pulseaudio (around 6%). And it is the same when the video is OK and when it is choppy!!

This choppiness can come in waves, or occur since the very beginning of the movie. And I'm starting to think that AWN has nothing to do with this, because video also gets choppy when AWN is off. I also disabled all desktop effects, and the choppiness continued.

IT'S SO CONFUSING!! I DON'T KNOW WHAT TO THINK!!

---

### Post by nechus on 2010-10-12
I'm starting to download Fedora. Can anyone save me?

---

### Post by nechus on 2010-10-12
I'm serious! I have a blank CD and I'm not afraid to use it!

---

### Post by P4man on 2010-10-12
Nothing wrong with trying fedora. But to find out what causing this, make sure in process tab you look at all processes, not just your own. View > All processes. Or run top in a terminal.

---

### Post by Dmck23 on 2010-10-12
Found a solution on this thread and it seams to have fixed the problem for me.

[http://ubuntuforums.org/showthread.php?t=1588889]("http://ubuntuforums.org/showthread.php?t=1588889")

In the terminal open the /etc/pulse/default.pa file

```
Sudo gedit /etc/pulse/default.pa
```

In the text file search for the line below:

```
load-module module-udev-detect
```

edit the line to add 'tsched=0' to the end of the line like below:

```
load-module module-udev-detect tsched=0
```

Save and reboot.

Hope this helps others with this problem.

---

### Post by nechus on 2010-10-12
OK... let's see...
Everything seems to be OK so far. Even VLC, which was almost useless, is running smoothly.

I will wait for a day or two and then I'll report on this.

I just have to say that I had to re-enable desktop effects and some Compiz animations after I rebooted. But everything seems to be OK now.

Fedora will have to wait. :)

Dmck23, I owe you one.

---

### Post by xvart on 2010-10-13
This did half the trick now the visuals are ok but I consistently lose sound for 30-50 sec per video, it then seems to recover. 

I have tested this on a number of video's I have and all the same result. I know the files are ok as they play in vista.

It's almost like the sound channel is being starved of data, rewinding to the same place in a file and I get the sound. Rewinding the whole track in this case a 26mb wmv I have clean sound all the way through on the second run through.

I have had this issue since lucid, only worse, the tsched does help, but it's not the complete fix for the issue. Thinking of going back to 9.04, seems some one has changed something and it causes issues with specific harware configs.

---

### Post by Philetjosie on 2010-10-13
On my Dell 510 m, it also did only half of the trick. Video looks ok now, but the sound still has some strange features, it blocks every 30 s. The processor goes to 100 % every 30 s also, for a very narrow spike, even when nothing is running. I think I will go back to 10.04 (sniff).

---

### Post by nechus on 2010-10-14
OK. After two days and several videos without any choppiness or sound problems at all, I consider this problem solved in my case.

Thank you all guys for your help! YOU ROCK.

---

### Post by TroN-0074 on 2010-10-15
> **nechus said:**
> OK. After two days and several videos without any choppiness or sound problems at all, I consider this problem solved in my case.

Thank you all guys for your help! YOU ROCK.

Lucky you man. I didnt do it for me it is still a problem and I just wish there were a way to downgrade to 10.04 without having to set up everything the way I have now.

---

### Post by cg0191 on 2010-10-15
> **Dmck23 said:**
> Found a solution on this thread and it seams to have fixed the problem for me.

[http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

In the terminal open the /etc/pulse/default.pa file

```
Sudo gedit /etc/pulse/default.pa
```In the text file search for the line below:

```
load-module module-udev-detect
```edit the line to add 'tsched=0' to the end of the line like below:

```
load-module module-udev-detect tsched=0
```Save and reboot.

Hope this helps others with this problem.
I found choppy sound/video in Firefox & this eliminated it.
How do things like this get missed in QA?
Or is the push to release so great that deadlines are met regardless?
Seems like 10.10 is the best release yet in terms of sound & Wifi support but still problems like this left hanging... When will it ever be finished???

---

### Post by nechus on 2010-10-16
>When will it ever be finished???

Good question. I think that the answer is possibly "Never". Just see how much new hardware is produced every day, and the community has to find the way to make it work under Linux because the manufacturers won't make the drivers available! It's a never ending story.

I've had my current laptop since the times of Jaunty. I remember that there was no way to make wifi work under Jaunty in it, unless I installed Super Ubuntu (now Super OS). Same thing with Karmic.

Then came Lucid, and it was a complete fiasco for me. Video and sound, which had been working fine in previous versions of Ubuntu, were a disaster. And now, with Maverick, wifi works out of the box, even though I had this problem with video and sound that you people helped me solve.

But there are some problems that have never been solved. I have never been able to modify the brightness level of my laptop screen, for example. And this has stayed the same since Jaunty.

I think that Canonical and other Linux-based OS producers should start producing their own hardware, too, and selling computers loaded with Linux.

Imagine if we were able to buy computers as elegant and "chic" as a Mac, but running Linux, and for a fraction of the price. At least in Chile, MANY people dream of having  a Mac, but they can't because they are expensive. But they would gladly run OS-X on a PC if they could, because that's the OS of those cool computers.

And then Canonical (and others) could say "You can buy our Linux-loaded computers with the guarantee that everything will work perfectly, or you can still install this cool OS on your PC at your own risk" (the way we do now).

What do you think? Should we tell Mark?

---

### Post by Telescopic Trout on 2010-10-16
Thank you nechus for the thread and thank you Dmck23 for the help! I had similar issues with all my video players I tried and with audio files on the Rythmbox music player and so far this seems to have worked. It may be worth mentioning to those for whom this hasn't worked for that my architecture is similar, but slightly less powerful than nechus's. That may be why it has worked for me. I'll be catching up on missed time vegetating in front of my DVDs now :popcorn: 


I was considering some really drastic changes to my system but that simple addition to /etc/pulse/default.pa did the trick. I had been reading several threads on video issues in Maverick and all but one seemed to miss problems with the pulseaudio which I had a feeling it had something to do with since my /var/log/messages had so many pulseaudio errors. What I would like to know, being a Linux newbie and having no experience in programming or bash scripting other than the small amount I have read in books, how this solution works.
Any ideas? While it is a pain that things don't always work out of the box in Linux it is also a good learning experience so if anyone knows please enlighten me.

and Thanks again nechus and Dmck23 :P I can't seem to thank you enough this has worked a treat!

---

### Post by Telescopic Trout on 2010-10-16
Forgot to mention another thing I noticed. My CPU usage went right down after this change. It would go berserk before this...

---

### Post by BeckySanderlin on 2010-10-16
> **Dmck23 said:**
> Found a solution on this thread and it seams to have fixed the problem for me.

[http://ubuntuforums.org/showthread.php?t=1588889]("http://ubuntuforums.org/showthread.php?t=1588889")

In the terminal open the /etc/pulse/default.pa file

```
Sudo gedit /etc/pulse/default.pa
```

In the text file search for the line below:

```
load-module module-udev-detect
```

edit the line to add 'tsched=0' to the end of the line like below:

```
load-module module-udev-detect tsched=0
```

Save and reboot.

Hope this helps others with this problem.

This fixed my choppy and speeding video issues but it create another problem. Now I have NO audio.

I checked the audio settings under sound preferences > output and the device has changed to Dummy Output. How do I fix this so I can have sound?

---

### Post by ashish89_taurus on 2010-10-17
This fixed the problem.
Thanks [B]Dmck23
[/B]

---

### Post by Renzu Ghent on 2010-10-24
> **Dmck23 said:**
> Found a solution on this thread and it seams to have fixed the problem for me.

[http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

In the terminal open the /etc/pulse/default.pa file

```
Sudo gedit /etc/pulse/default.pa
```In the text file search for the line below:

```
load-module module-udev-detect
```edit the line to add 'tsched=0' to the end of the line like below:

```
load-module module-udev-detect tsched=0
```Save and reboot.

Hope this helps others with this problem.


This seemed to solve my sound problems ranging from Firefox to the SNES9X I had been having.  Thanks a lot!

---

### Post by abumaia on 2010-10-25
> **Dmck23 said:**
> Found a solution on this thread and it seams to have fixed the problem for me.

[http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

In the terminal open the /etc/pulse/default.pa file

```
Sudo gedit /etc/pulse/default.pa
```In the text file search for the line below:

```
load-module module-udev-detect
```edit the line to add 'tsched=0' to the end of the line like below:

```
load-module module-udev-detect tsched=0
```Save and reboot.

Hope this helps others with this problem.

You rock!  That cleared it up for me.  Well, all except for one group of MKV's from one specific source, none of them would play in smplayer.  Looks like I'll have to find a new source for those.

---

### Post by j.benes on 2010-10-28
I experienced the same problem. I tried the solution suggested by Dmck23, with slight success. In the end I noticed that the problem was mainly caused by AWN Dialect applet. Switched it off and everything is back to normal. The buggy applet was consuming huge amounts of RAM. I still use AWN and so far everything look fine.

---

### Post by iluminumx on 2010-11-04
> **Dmck23 said:**
> Found a solution on this thread and it seams to have fixed the problem for me.

[http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

In the terminal open the /etc/pulse/default.pa file

```
Sudo gedit /etc/pulse/default.pa
```In the text file search for the line below:

```
load-module module-udev-detect
```edit the line to add 'tsched=0' to the end of the line like below:

```
load-module module-udev-detect tsched=0
```Save and reboot.

Hope this helps others with this problem.

thank you so much :popcorn:

worked for me on lucid as well as on maverick.

---

### Post by rts on 2010-11-06
I'm getting this as well, and the tsched fix did nothing.

It only happens while watching DVDs; other files play fine.

While watching a dvd Totem's CPU usage will go to 125% and it will be choppy to the point of being unwatchable.

Worked fine yesterday with Lucid; upgraded this morning and boom.

This is with a generic Intel graphics chip/driver.

---

### Post by j.benes on 2010-11-11
You can also try to install newest version of VLC. Add this repository and upgrade to ver 1.2:
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

---

### Post by rts on 2010-11-14
> **j.benes said:**
> You can also try to install newest version of VLC. Add this repository and upgrade to ver 1.2:
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

For me, the version of vlc in standard repos works just fine, so it seems to specifically be a Totem issue.

---

### Post by mobislink on 2010-11-23
> **Dmck23 said:**
> Found a solution on this thread and it seams to have fixed the problem for me.

[http://ubuntuforums.org/showthread.php?t=1588889]("http://ubuntuforums.org/showthread.php?t=1588889")

In the terminal open the /etc/pulse/default.pa file

```
Sudo gedit /etc/pulse/default.pa
```

In the text file search for the line below:

```
load-module module-udev-detect
```

edit the line to add 'tsched=0' to the end of the line like below:

```
load-module module-udev-detect tsched=0
```

Save and reboot.

Hope this helps others with this problem.

I would like to try this but I don't seem to have permission to make the edit. Just started messing around with Ubutu a coupe days ago. I am logged in as the administrator.

---

### Post by madjr on 2010-11-23
this is why i keep 2 separate partitions

1 with my solid stable LTS and another one for testing new releases.

Thats the first rule: never upgrade till you tested everything you need and are ready to fully migrate.

upgrades are not default anymore for that purpose.

I never upgrade directly anymore, i had every OS break on me several times. Windows broke, mac upgrade broke (and they werent free) and ubuntu also broke some stuff on me once.

maybe the devs should disable completely the upgrade system.

---

### Post by mobislink on 2010-11-23
> **mobislink said:**
> I would like to try this but I don't seem to have permission to make the edit. Just started messing around with Ubutu a coupe days ago. I am logged in as the administrator.


I made the change an it seems to have fixed my issue. Thanks

---

### Post by P4man on 2010-11-23
> **mobislink said:**
> I would like to try this but I don't seem to have permission to make the edit. Just started messing around with Ubutu a coupe days ago. I am logged in as the administrator.

I hope you didnt unlock the root account. You (should!) never log in as root ("administrator") in ubuntu. Having an administrator account lets you use sudo and gksudo, which elevates your privileges (a bit like the windows UAC popup). Since you are new to ubuntu, please read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
It may avoid a lot of future problems.

---

### Post by droneboy on 2010-11-23
It'd be nice to take stock of this thread and see whether anything can be translated into a permanent fix so that other users can benefit. 

I have had stuttering and volatile audio with a new Lenovo Y560 with a new Maverick install. I'm not at home right now to test whether it's ok, but I applied a 'fix' from another thread this morning which involved changing pulseaudio's default sampling rate from 44100 to 48000 and tweaking the nice level, and that seemed to work.

Having read the thread, there seems to be three groups of users afflicted:
* Those afflicted by some kind of pulseaudio bug or misconfiguration, for which the tsched=0 fix works to resolve.
* Those who have otherwise working systems that are borked by avant-window-navigator, and removing it fixes the problem.
* 'Others' for whom no fix and no common problem has yet been identified. 

I'd really like to know what the proper procedure is to robustly debug these types of issues. Messing around with config files blind doesn't seem to be helpful in diagnosing the problem. 

For instance, what does adding the tsched=0 option actually _do_? If it fixes something, what would the problem therefore be? And is there a way to automatically test whether a problematic configuration exists, so that a bugfix can be applied automatically? 

And then presumably bug reports need to be filed - at the least - against pulseaudio and awn.

---

### Post by elnur on 2010-11-25
> **Dmck23 said:**
> Found a solution on this thread and it seams to have fixed the problem for me.

[http://ubuntuforums.org/showthread.php?t=1588889]("http://ubuntuforums.org/showthread.php?t=1588889")

In the terminal open the /etc/pulse/default.pa file

```
Sudo gedit /etc/pulse/default.pa
```

In the text file search for the line below:

```
load-module module-udev-detect
```

edit the line to add 'tsched=0' to the end of the line like below:

```
load-module module-udev-detect tsched=0
```

Save and reboot.

Hope this helps others with this problem.

This is a great solution. But it stopped working with upgrade from kernel 2.6.35-22 to 2.6.35-23. Any new solutions?

---

### Post by no2498 on 2010-11-25
i know im not right with the spelling 
did you put it in the mod prob files
so it loads first
is it etc mod prob ?

---

### Post by azarhal on 2010-11-28
> **elnur said:**
> This is a great solution. But it stopped working with upgrade from kernel 2.6.35-22 to 2.6.35-23. Any new solutions?

Are you sure the line is still present after the upgrade? I added the fix in kernel 2.6.35-23 and it seems to works. In fact, the choppiness appeared with that kernel, I didn't have any choppiness before the upgrade.

Now I get weird sound once in while, but at least it doesn't look like my music files are corrupted.

---

### Post by elnur on 2010-11-28
> **azarhal said:**
> Are you sure the line is still present after the upgrade? I added the fix in kernel 2.6.35-23 and it seems to works. In fact, the choppiness appeared with that kernel, I didn't have any choppiness before the upgrade.

Now I get weird sound once in while, but at least it doesn't look like my music files are corrupted.

Yea, I'm sure the line is still there. And, yea, choppiness might not be that bad as it was before I tried this solution, but obviously there is some.

My quick solution is to just use 2.6.35-22 until there is a better option.

---

### Post by Dumdideldum on 2010-12-02
I am facing different choppyness in 10.10 too. Going from flash videos in firefox to all video files using video player. Sound gets choppy, video gets asynchronous.

Adding the tsched=0 didn´t fix the thing at all, neither other kernel versions (2.6.34 and 2.6.36), I have even tried fglrx and radeon driver - same results.

But now it seems I found a solution which I think might not only help me, I hope it might help others too, as I didn´t see all the problems described above appear again.

System ---> Peferences ---> Pulseaudio-Settings

Disable all X in the checkboxes, so that no option is enabled.

---

### Post by learst on 2010-12-04
> **Dmck23 said:**
> Found a solution on this thread and it seams to have fixed the problem for me.

[http://ubuntuforums.org/showthread.php?t=1588889](http://ubuntuforums.org/showthread.php?t=1588889)

In the terminal open the /etc/pulse/default.pa file

```
Sudo gedit /etc/pulse/default.pa
```In the text file search for the line below:

```
load-module module-udev-detect
```edit the line to add 'tsched=0' to the end of the line like below:

```
load-module module-udev-detect tsched=0
```Save and reboot.

Hope this helps others with this problem.

I tried this and it didn't work for me.

ETA: I'm trying to watch youtube videos with Firefox 3.6.12. Kernel is .25

---

### Post by Chamillo on 2010-12-11
> **droneboy said:**
> It'd be nice to take stock of this thread and see whether anything can be translated into a permanent fix so that other users can benefit. 

I have had stuttering and volatile audio with a new Lenovo Y560 with a new Maverick install. I'm not at home right now to test whether it's ok, but I applied a 'fix' from another thread this morning which involved changing pulseaudio's default sampling rate from 44100 to 48000 and tweaking the nice level, and that seemed to work.

Having read the thread, there seems to be three groups of users afflicted:
* Those afflicted by some kind of pulseaudio bug or misconfiguration, for which the tsched=0 fix works to resolve.
* Those who have otherwise working systems that are borked by avant-window-navigator, and removing it fixes the problem.
* 'Others' for whom no fix and no common problem has yet been identified. 

I'd really like to know what the proper procedure is to robustly debug these types of issues. Messing around with config files blind doesn't seem to be helpful in diagnosing the problem. 

For instance, what does adding the tsched=0 option actually _do_? If it fixes something, what would the problem therefore be? And is there a way to automatically test whether a problematic configuration exists, so that a bugfix can be applied automatically? 

And then presumably bug reports need to be filed - at the least - against pulseaudio and awn.

Good point. How do we make the Ubuntu people aware of these problems? Clearly there are many who are experiencing video problems with Ubuntu 10.10. When I was running 10.04 the video was perfect. I just upgraded to 10.10. Big mistake. Now it is annoying to try to watch a movie on my laptop. The video is choppy and jittery.

I'm also reluctant to make changes to configuration files because usually those solutions are short lived or could have unexpected results. Let's hope that someone in the Ubuntu team is aware of this and that they are working on a solution.

---

### Post by sepius on 2010-12-16
> **madjr said:**
> this is why i keep 2 separate partitions

1 with my solid stable LTS and another one for testing new releases.

Thats the first rule: never upgrade till you tested everything you need and are ready to fully migrate.

upgrades are not default anymore for that purpose.

I never upgrade directly anymore, i had every OS break on me several times. Windows broke, mac upgrade broke (and they werent free) and ubuntu also broke some stuff on me once.

maybe the devs should disable completely the upgrade system.

This is a great idea, I do it with Virtualbox, but it is no good for video playback unfortunately.  I got this problem  with Lucid, however, which prompted me to upgrade, and the problem remained unfortunately.  Well still looking because someone will have a fix for me somewhere.

---

### Post by sepius on 2010-12-16
> **Dumdideldum said:**
> I am facing different choppyness in 10.10 too. Going from flash videos in firefox to all video files using video player. Sound gets choppy, video gets asynchronous.

Adding the tsched=0 didn´t fix the thing at all, neither other kernel versions (2.6.34 and 2.6.36), I have even tried fglrx and radeon driver - same results.

But now it seems I found a solution which I think might not only help me, I hope it might help others too, as I didn´t see all the problems described above appear again.

System ---> Peferences ---> Pulseaudio-Settings

Disable all X in the checkboxes, so that no option is enabled.

Thanks for this.  All I had to uncheck was Simultaneous Output and all is good.  Will be interesting to see what that upsets however, if anything comes up, I'll post back.

But, thanks to all who submitted suggestions and Ubuntu is still awesome!

---

### Post by hawkril on 2010-12-17
I couldn't find the pulseaudio settings in my Settings menu. Do I ave to install something at first? Or can I start the configuration dialog from terminal ?

hawkril

---

### Post by Dumdideldum on 2010-12-29
check if you have the package paprefs installed.

---

### Post by psychydyl on 2011-01-10
For the problem of the missing audio, I installed the **Gnome ALSA mixer**. On running it, the **PCM** channel was found muted and the **SPEAKER** channel was set to zero volume(these controls don't show up in the standard pulse audio settings). On undoing the mute and increasing the volume the sound came back.
For the choppy video in Totem and VLC, I haven't found a solution but for the time being, I installed **SMPlayer** and it works. I also installed **ffmpeg** and that works too. Open terminal, write ffplay then drag and drop the video file in front of it and hit enter. It'll look like this:
[CENTER]
*psycho@StarDuck $ ffplay '/home/psycho/Videos/DasBoot.avi' *
[/CENTER]
similarly,
[CENTER]*psycho@StarDuck $ mplayer -vo x11 '/home/psycho/Videos/DasBoot.avi'*[/CENTER]
worked too.

---

### Post by rchiossi on 2011-01-24
Tried everything on this post an still no luck... I can play simple movies with no problem, but high res movies are all choppy. I have a nvidia gts250 with the drivers properly installed.

---

### Post by skippy2007_2335 on 2011-06-19
> **azarhal said:**
> Are you sure the line is still present after the upgrade? I added the fix in kernel 2.6.35-23 and it seems to works. In fact, the choppiness appeared with that kernel, I didn't have any choppiness before the upgrade.

Now I get weird sound once in while, but at least it doesn't look like my music files are corrupted.

The **tsched=0** fix worked for me - but I'm puzzled as to what caused the issue in the first place.  I am _definitely using pulse audio_, and have to assume that one of my last upgrades introduced (or missed) a variable that introduced my choppy audio - it was working only a few weeks back.  I dual boot a desktop between Win7 and Ubuntu, so I can use a few programs natively in Win.  

I'm a big fan of Ubuntu, but the fact that these things slip and aren't automatically fixed in newer patches does make it hard for the average user to adopt Ubuntu comfortably.  

That being said, I'm probably still my own worst enemy not "getting it" completely, but thinking I do.  I say that as I believe I'm relatively current with all my upgrades, but I just noticed I'm still running kernel 2.6.32-31-generic.   This seems to be several versions behind a few of you... ;)

---

### Post by nechus on 2011-06-27
I decided to do something very simple to solve all my problems with video. I bought a new laptop!! :)

I sold the old one (Acer Aspire 5735) and bought this small 11,6" Packard Bell... with an optical drive! As far as I know, it's the smallest laptop that has an optical drive!

And Maverick runs like a charm on it. Everything works fine, even the mike, the webcam. everything except the screen bightness control. But I never change the brightness level, so it's not a problem.

Did you know that Packard Bell computers continued to be very popular in Latin America even after the company closed down in the US? PB computers are very ubiquitous down here nowadays. Actually, this my fourth PB computer. I had the first one back in the 90s and I have never had any problems with them, even though they were notorious for their poor quality in the US. I wonder if the manufacturer was the same for PB computers sold in the US and Latin America. I can't understand this difference in quality. Anyway, Packard Bell is owned by Acer now.

The thing is, I'm very happy with Maverick now. It was a very pleasant surprise.

Here's a review:
[http://www.reghardware.com/2010/07/15/review_notebook_packard_bell_butterfly_xs/](http://www.reghardware.com/2010/07/15/review_notebook_packard_bell_butterfly_xs/)

---

### Post by tuxsheadache on 2011-08-03
The fix by Dmck23 works for me on my laptop, on Ubuntu 10.04. Thank you.

---

### Post by wyrless2002 on 2012-03-29
Thanks, Dmck23. 
After receiving updates to adobe-flash-properties-gtk 11.2.202.228-0lucid1 
and adobe-flashplugin 11.2.202.228-0lucid1,
 I started getting choppy audio in YouTube, Pandora, Facebook videos... 
[CENTER][SIZE="4"]FLASH![/SIZE]
[IMG]http://photo.shockya.com/wp-content/uploads/2011/11/william-shatner-khan-scream-quote-star-trek-wrath-of-khan-500x375.jpg[/IMG][/CENTER]


Following your simple fix and a restart, Flash works as good as [S] new[/S] it ever did.

Also, I'm not in Maverick. I'm running Lucid/10.04 LTS.
Good Hack!

---

