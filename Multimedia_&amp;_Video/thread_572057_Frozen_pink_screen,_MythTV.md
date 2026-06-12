---
title: "Frozen pink screen, MythTV"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by dwf_starband on 2007-10-10
Usually the first time I watch live tv in Mythtv everything works good. If I have viewed any other videos though (rather mythtv recordings in mythtv or other videos with other video players) Then live tv doesnt work.  Sometimes it is colored fuzz with sound, in which case I can exit out, other times it is solid pink and locks up the comptuer and I have to push the reset button.  If its just the colored fuzz and I exit out then any video (rather mythtv recordings in mythtv or other videos with other video players) show the same colored fuzz.

I reinstalled the latest nvidia drivers hoping that would help, and at first I thought it did, I opened lots of different videos in different players and live tv in mythtv and recordings and did that all several times without problems.  Then I did a little browsing on the internet and turned mythtv back on to live tv and froze up the sustem with the pink screen again.

Does anyone have any ideas what may be wrong?

A guy on the ubuntu irc channel had me try mplayer with different outputs and when the defaults didnt work the x11 output did.  He told me that this ment it was something wrong with the video card.  Thats why I reinstalled the drivers.

Any ideas?

dennis

---

### Post by dwf_starband on 2007-10-10
I unselected "Enable OpenGL vertical sync for timing" in playback options and that seems to have fixed my problem. 

I have thought it wasfixed before and then it came back to bite me.  So ill post any updates if this problem returns.

dennis

---

### Post by oobe-feisty on 2007-10-14
I have had the exact same problem your the first person i have come across with the same problem 
the trouble with this prob is exactly what you described its hard to re produce and define what causes it if i played back video in various players sometimes it would happen other times it wouldn't

i have had the rainbow and and pink screen of death many times. I messed around with a lot of settings and couldnt find anything in /var/log dmesg or mythbackend.log i dont know how to enable mythfrontend log but apperently it uses a lot of disk space. 

im using a DViCO FusionHDTV DVB-T Dual Digital 4 tuner just so you know. I don't  think its specific to hardware though i tried recompiling my drivers with various patches and firmware versions but that didnt help i also compiled a new kernel etc. none of that seemed to work although it has helped overall perfermance. 

anyway it went away  after i setup xvmc and put a 2 sec delay on my tuners found in mythtv-setup 
section 2 i the green spotchy ness does come back does come back when the card is first initialized if i have opengl vsync enabled i turned it off and have deinterlacing enabled set to  one field im not happy about the limitations of xvmc however it is a great work around. 

although what i just mentioned above has helped 99% i did get the pink screen this morning thats how i found your post googleing afterwards this is the first time in a week and it used to happen more than once a day mind you this was after deleting my channels and rescanning as i messed them up adding my pvr-250 to the mix which made some dvb channels messy at first now everything seems fine again let me know how you get on with this prob and it would be nice to know what hardware you are using.

P.S this is definatly not a Ubuntu specific issue i have reproduced this bug on slackware fedora and debian

---

### Post by dwf_starband on 2007-10-15
Im pretty sure its frontend related and not with the backend.  I had a seperate frontend for a couple of days and didnt have that problem using the same backend.

Im at work so I dont have all the specifics on my hardware but here is what I can remember.

P4 3.2
WinTV PVR-150 w/ usb remote/transceiver
Nvidia 7300 (I think)
2g of ram

Im using feisty fawn and myth tv from the repositories, I dont remember what version.

dennis

---

### Post by ///MVinny on 2007-10-19
Same here, I'll try that option and see if that does the trick.  

In the meantime, I found that opening an ssh shell to the box from another workstation seem to wake the machine up from it's pink-coma.  MythTV would stop but at least I got control of the machine back before even thinking about hard booting it.  All I wanted to do was remote shell in and halt the machine gracefully, lucky me.

GeForce 7900 GS, AGP 8X, DVI to HDMI, AMD64, Ubuntu Fiesty.

---

### Post by ///MVinny on 2007-10-19
Oh yeah btw~ the x86_64 nv driver version 100.14.19.  I've never seen this problem before until I started using this driver.

---

### Post by ///MVinny on 2007-10-23
Found this posted as a bugfix here:

[https://bugs.launchpad.net/ubuntu/+bug/155618](https://bugs.launchpad.net/ubuntu/+bug/155618)

---

### Post by frokki on 2007-10-24
I am suffering from this same problem. First playback always works, but if I play videos outside MythTV and then go back to watch livetv, there's a good chance that it goes pink. It's really annoying since I only have one machine and am forced to hardboot it when this pink lockup occurs.

Oh, and I use Gutsy with latest restricted drivers and latest mythtv from repos.

---

### Post by dwf_starband on 2007-10-25
Have you tried the mythbuntu control center in gutsy?  Im just getting it ready on a fresh install of gutsy so ill find out if it has the same problems or not.

If anyone has had this problem and starts using the control center let us know rather that makes a difference or not.

dennis

---

### Post by vika on 2007-10-26
> **///MVinny said:**
> Found this posted as a bugfix here:

[https://bugs.launchpad.net/ubuntu/+bug/155618](https://bugs.launchpad.net/ubuntu/+bug/155618)

Works great with player using gstreamer but doesn't help with Livetv.

I did a bit research and found out that it's a bug in nvidia driver version 100.14.19. NVidia has annouced that the cause of this problem has been identified and it should be fixed in a future driver release. So it seems we either have to downgrade to previous version or just wait for the next driver release.

---

### Post by dwf_starband on 2007-10-26
Is there a driver version that is known to work?  And if so where could it be found?

thanks

dennis

---

### Post by ///MVinny on 2007-10-26
There's a beta available, 100.14.23 over on the nv archives page:

[http://www.nvidia.com/object/linux_display_ia32_100.14.23.html](http://www.nvidia.com/object/linux_display_ia32_100.14.23.html)
 - and -
[http://www.nvidia.com/object/linux_display_amd64_100.14.23.html](http://www.nvidia.com/object/linux_display_amd64_100.14.23.html)

I don't see the pink screen of death addressed, so it may or may not I'll see when I get home.  Some guys say it fixed the compiz problem switching between VT's as nv states on the page.

---

### Post by ///MVinny on 2007-10-26
I installed the beta 100.14.23 driver, I've been trying and can't seem to reproduce the frozen pink screen.  8)

---

### Post by axelsvag on 2007-10-27
I got the same problem as everyone else here. Maybe it seems like a stupid question, but how did you upgrade as the driver seems  very integrated in the gutsy/propriarity set up. Do you have to uninstall/disable first?

---

### Post by frokki on 2007-10-27
> **///MVinny said:**
> I installed the beta 100.14.23 driver, I've been trying and can't seem to reproduce the frozen pink screen.  8)The beta driver didn't do the trick for me. Pink screen and lockups still occur, even though they haven't been so common now I think.

---

### Post by fain on 2007-10-27
i had this problem and it went away completely when i used the envy script. I couldn't get the .23 driver to install right all i would get was friggen bullet proof x. that was sooooo annoying. envy worked great though funny thing is envy got the .19 driver lol. seems like it might be in the deb?? But I read in the nvidia forums that this is a known bug (happens on SUSE as well) and will be fixed in an upcoming release.......

also mythtv seems to lag alot more when starting now than with feisty :( but it does work at least!!!

---

### Post by dwf_starband on 2007-10-29
So am I understanding ypu right, envy instals an older driver which is more stable and doesnt cause the "pink screen of death"?

I was wanting to keep this install of gutsy as "fresh" as possible, but if this is a sure fix ill do it.

Can any one else confirm that this worked for them?

dennis

---

### Post by oobe-feisty on 2007-10-29
> **fain said:**
>  

its not a bug with the deb im experiencing same prob with binary driver from nvidias site

[QUOTE=fain;3650112.  couldn't get the .23 driver to install right all i would get was friggen bullet proof x. that was sooooo annoying  ! 

gdm is hard to kill i dont know an option to shut it down so i do ps -A | grep gdm 
then kill -9 until all spawns are dead somtimes i need to re kill 

> **frokki said:**
> The beta driver didn't do the trick for me. Pink screen and lockups still occur, even though they haven't been so common now I think.
im running the new .23 driver and getting the same probs just less often using my old xorg.conf from feisty 


> **dwf_starband said:**
> So am I understanding ypu right, envy instals an older driver which is more stable and doesnt cause the "pink screen of death"?

I was wanting to keep this install of gutsy as "fresh" as possible, but if this is a sure fix ill do it.

Can any one else confirm that this worked for them?

dennis

no envy install the .19 driver which has caused all the problems its just coincedence he hasnt yet experienced same pink screen probs like when i messed around with settings that i posted earlier

also is anyone else getting this message during tv playback VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8

---

### Post by dwf_starband on 2007-10-29
Is it possible to set myth-frontend and other video players to not use the "buggy" parts of the video card if the computers processor is fast enough?

Ive set up a seperate mythtv frontend for my livingroom which I will do most of my video viewing from(this frontend doesnt have this problem) but i still want to be able to view videos from time to time on my backend/desktop.

Suggestions?

thanks
dennis

---

### Post by adrigmail on 2007-10-29
> **dwf_starband said:**
> Ive set up a seperate mythtv frontend for my livingroom which I will do most of my video viewing from(this frontend doesnt have this problem) but i still want to be able to view videos from time to time on my backend/desktop.

Suggestions?

thanks
dennis


It just takes one change in configuration like "refresh rate" and you have the picture back.
It's not that bad.

---

### Post by dwf_starband on 2007-10-29
> **adrigmail said:**
> It just takes one change in configuration like "refresh rate" and you have the picture back.
It's not that bad.

It seems there are several people having this problem.  

You seem to know how to fix this problem, but your answer is to ambiguous to be of any help to someone like me who is new to Linux.

Would you be willing to specifically write down the steps to change the configuration to fix this problem?

thanks for your help,

Dennis

---

### Post by adrigmail on 2007-10-29
I don't have a fix, just a temporary solution.
so if you go to menu, preferences, screen resolution, you can switch resolution or refresh rate.
par example I change the refresh rate to get rid of the scrambled video.
Just change something and you can watch mythtv or mplayer again...temporarly
when the bug shows up again you have to do this again, so voila
It will do for me while waiting for a fix from nvidia

hope this will help you..

---

### Post by oobe-feisty on 2007-10-29
> **adrigmail said:**
> I don't have a fix, just a temporary solution.
so if you go to menu, preferences, screen resolution, you can switch resolution or refresh rate.
par example I change the refresh rate to get rid of the scrambled video.
Just change something and you can watch mythtv or mplayer again...temporarly
when the bug shows up again you have to do this again, so voila
It will do for me while waiting for a fix from nvidia

hope this will help you..

that would be great except the actual problem people in this thread have is that the whole computer freezes  so this fix that you suggest is not even possible

---

### Post by dwf_starband on 2007-10-29
> **oobe-feisty said:**
> that would be great except the actual problem people in this thread have is that the whole computer freezes  so this fix that you suggest is not even possible

I agree, that solution will not work once the screen is frozen.

dennis

---

### Post by williammanda on 2007-10-29
I just wanted to post the same problem on another post:
[http://ubuntuforums.org/showthread.php?p=3653358#post3653358](http://ubuntuforums.org/showthread.php?p=3653358#post3653358)

Thanks

---

### Post by adrigmail on 2007-10-30
> **oobe-feisty said:**
> that would be great except the actual problem people in this thread have is that the whole computer freezes  so this fix that you suggest is not even possible

Maybe this sounds stupid, but try to switch refresh rate before you start watching a video
I don't know if it will help you (most likely you have a different video-card) but give it a try.
My screen doesn't freeze, so I can do this afterwards

---

### Post by coreyva on 2007-10-30
While I haven't gotten the pink screen, I constantly get the garbled screen after a few moments. Yet another link with this issue. [http://ubuntuforums.org/showthread.php?t=597618]("http://ubuntuforums.org/showthread.php?t=597618")

---

### Post by jba6511 on 2007-10-31
add me to the list of users with this issue.

2007-10-31 12:07:54.198 VideoOutputXv: XvMCTex: Init failed
2007-10-31 12:07:54.199 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  142
  Minor opcode:  14
  Resource id:  0x291

---

### Post by coreyva on 2007-10-31
It's an [nvidia bug]("http://www.nvnews.net/vbulletin/showthread.php?t=98852"). I tried downgrading with envy, but had lockup issues. I grabbed 100.14.11 from the nvidia website and all is well now.

---

### Post by williammanda on 2007-10-31
Please list how to install the other driver.
Thanks

---

### Post by fain on 2007-10-31
when i installed the .11 driver i kept getting low res mode :( even when i uninstalled it and reinstalled the repo i still got low res mode??? The only thing that worked for me was envy. But the problem still comes back and i rerun envy reboot and all is well again.

---

### Post by coreyva on 2007-11-01
Were you using the nvidia driver vs nv? That was the only time a had a "lower resolution. I'm running at 1920x1200, but with the nv driver I could only get 1680x1050.

---

### Post by vika on 2007-11-02
As I previously said, you need to **downgrade** your driver eg. to version 100.14.11. **Not upgrade** as many of you have done, especially no to any beta drivers.

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html")    - for 32bit
[http://www.nvidia.com/object/linux_display_amd64_100.14.11.html]("http://www.nvidia.com/object/linux_display_amd64_100.14.11.html") - for 64bit

This driver works perfectly on my Gutsy.

If you don't know how, just search the forum for proper howto.

---

### Post by coreyva on 2007-11-02
> **vika said:**
> As I previously said, you need to **downgrade** your driver eg. to version 100.14.11. **Not upgrade** as many of you have done, especially no to any beta drivers.

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html")    - for 32bit
[http://www.nvidia.com/object/linux_display_amd64_100.14.11.html]("http://www.nvidia.com/object/linux_display_amd64_100.14.11.html") - for 64bit

This driver works perfectly on my Gutsy.

If you don't know how, just search the forum for proper howto.

That helped with the distortion, but now I'm back to the jerky video and lockups. :(

---

### Post by williammanda on 2007-11-05
I tried the downgrade, see this post:
[http://ubuntuforums.org/showthread.php?t=597618&page=3](http://ubuntuforums.org/showthread.php?t=597618&page=3)

---

### Post by jba6511 on 2007-11-10
any updates from nvidia?

---

### Post by Mellon on 2007-11-10
what i did to live with this bug was to setup my mplayer with X11 video output and followed this post 
[http://ubuntuforums.org/showthread.php?t=77329&highlight=mplayer+config+ultimate](http://ubuntuforums.org/showthread.php?t=77329&highlight=mplayer+config+ultimate)
to make it look better 

see the results 

[[IMG]http://thumbnails.imajr.com/Pantallazo_453217.png[/IMG]](http://imajr.com/Pantallazo_453217)

---

### Post by oobe-feisty on 2007-11-15
im using nvidia 6600gt and suffered probs bigtiime with mythtv and other media players i.e frozen pink screen needing hard reboot and distortion in other media player hard reboot only needed for mythtv i didnt relise it was the nvidia drivers refer to my post at the beginning of this thread 
i tried the beta driver but still did not get resovled. 

so i installed this driver [http://www.nvnews.net/vbulletin/showthread.php?t=99186](http://www.nvnews.net/vbulletin/showthread.php?t=99186)

i been using it for over 2 weeks with no problems now everything seems perfect and probably is 
i used envy i dont think that matters i tried envy with the other drivers to no avail i hope this helps someone as i have gone through a lot of pain trying to resolve this issue

---

### Post by williammanda on 2007-11-22
I have used another post to solve this problem : [http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)
It is the 169.04 beta driver from Nvidia. So far it has solved two problems: 1. freeze / lockups. 2. Pink screen.
Thanks

---

### Post by Joco on 2007-11-24
My findings posted in this thread:

[forum-post]("http://ubuntuforums.org/showthread.php?p=3832583&posted=1#post3832583")

---

### Post by frokki on 2007-12-20
I wonder how often are new glx drivers released by nvidia?

btw I succesfully downgraded to 96.43.01 and got rid of the pink.

---

### Post by fain on 2007-12-20
> **frokki said:**
> I wonder how often are new glx drivers released by nvidia?

btw I succesfully downgraded to 96.43.01 and got rid of the pink.


Seems like friggen forever. Some times this bug doesn't exist for some time after i do a envy run. Then the slightest thing like play a dvd or play a video file, boom, I have p.s.o.d. :( looks like I'm doin another envy install today,.

btw the computer in my sig is not the computer i get this problem from...

---

### Post by fain on 2007-12-21
Looks like they just released a new driver :) rejoice.

[http://www.phoronix.com/scan.php?page=article&item=946&num=1]("http://www.phoronix.com/scan.php?page=article&item=946&num=1")

---

### Post by fain on 2007-12-24
Any one try the new driver?

---

### Post by frokki on 2007-12-24
> **fain said:**
> Any one try the new driver?Can't be bothered, since 96.43.01works fine for me. 

Offtopic: What's the thing with nVidia driver naming, 96 -> 104 -> 169 ?

---

### Post by fain on 2007-12-25
Not really sure, i was wondering this my self.

---

### Post by williammanda on 2007-12-26
The 169.07 drivers works fine with gusty 64 bit. I have 7300 LE & 7300 GT.
Thanks

---

### Post by fain on 2007-12-27
> **williammanda said:**
> The 169.07 drivers works fine with gusty 64 bit. I have 7300 LE & 7300 GT.
Thanks

It fixed the pink screen of death?

---

### Post by williammanda on 2008-01-04
> **fain said:**
> It fixed the pink screen of death?

Yes it did! I have no issues.
Thanks

---

### Post by fain on 2008-01-04
awesome thanks

---

### Post by DStensland on 2008-01-20
Another confirmation of repair. The nvidia 169.07 driver solved my pink screen TV lockups, too. I'm using Gutsy Gibbon 7.10 and an nvidia 6200 AGP with a KWorld VS-L883D (looks like a  KWorld LTV883RF since it has a remote input and FM antenna connector-- unlike what's on the cover of the box). Anyway, prior to installing the 169.07 drivers the lockups happened in both tvtime or MythTV with the older 100.14.191 nvidia driver enabled.

In case anyone else reads this and wonders how I got the KWorld working, I had to downgrade the kernel to 2.6.22-14-386 to avoid a high CPU usage problem. Works fine now.

---

### Post by jonno on 2008-01-29
I have had the same pink screen issue in Mythbuntu and have been trying to upgrade to the latest Nvidia driver (now 169.09). I have logged out of X and am trying to use the method suggested on the Nvidia site:
**sh NVIDIA-Linux-x86_64-169.09-pkg2.run**
but the installer complains that I don't have a **precompiled kernel interface**. It tries to download one from nvidia.com - no joy - then it tries to build one but finds that either I **don't have gcc installed or cc is not in my path**!
I'm pretty clueless on this. What do I need to do (Linux noob).

I'm running Mythbuntu 7.10 install, kernel is 2.6.22-14-generic

---

### Post by jonno on 2008-01-29
Someone on the Mythtv-Users list suggested I uninstall nvidia-glx-new and install nvidia-glx which is a bit older. Was simple enough via Synaptic. Since the pink screen was intermittent I can't say it's fixed yet but I'll update if not.

---

### Post by fain on 2008-01-30
Just install gcc from the synaptic package manager you will also need the kernel headers for your kernel to build the nvidia module.

```
uname -r
```

will get your kernel.

---

### Post by Joco on 2008-03-20
At the risk of restating something if you want to get the latest released  nVidia drivers onto 7.10 then I found Envy ([http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")) to be the easiest way to achieve this.  The Envy installer script deals with all the kernel and driver source downloading, compiling etc.

After I used this on all my 7.10 frontends all those evil lockups and pink screens went away.

---

### Post by thealphamale05 on 2008-03-30
I have had this issue since my first install of of linux which just so happens to be an amd64 with integrated nvidia. I am not actually using ubuntu on this computer but the same issue exitsts, _**in kaffeine when i change the "xine Engine parameters"  for the video playback from "auto" to opengl it fixes the pink screen immediately in mid playback**._ I also wanted to add that I notice this problem more so when I also have a flash video open in something like youtube or college humor (in firefox x86_64 version) also when I have seen this issue more so while playing music in amarok while trying to watch a movie. I bring multimedia to its knees. I have seen some people attribute this issue to bery/compiz and I can discredit the myth, even when I dont have compiz_fusion running i would get the problems.  Keep hacking guys and remember you can always go back to windows.... not

---

