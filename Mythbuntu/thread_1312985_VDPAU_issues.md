---
title: "VDPAU issues?"
date: 2009-11-03
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-11-03
I have not been able to get vdpau working in a decent fashion under myth.  I added the repsoitory under .21 and had lots of "artifacts" under vdpau that were not present under any other display modes.  

The best way of describing these artifacts is that the more rapidly things move on the screen the more pixelated the image would become.  At the time i was using 180.60 nvidia drivers and (64bit) 9.04.

Since then i have fully reinstalled my machine from scratch with (64bit) 910 and installed the latest nvidia drivers 190.42 and still have the same artifact issues under myth .22 and vdpau.  

Has anyone else experienced this problem?  I would really like to have vdpau working but the image isnt fit for watching currently.

(Video card wise i have an 8300 chipset on my asus M3N78-EM board).

Thanks

---

### Post by geekyhawkes on 2009-11-04
Anyone experiancing the same?

---

### Post by johnnybirdman on 2009-11-04
> **geekyhawkes said:**
> Anyone experiancing the same?

I have a fresh 9.10 install and tried all the VDPAU profiles but got bad results with all of them when trying to watch 720p mkv.  Standard Def avi and DVD's are fine.  
I have an 8600gt xxx and am running the nvidia 185 drivers.  I tried to install the 190 driver but had that pesky problem of it wanting to uninstall everything myth.  I haven't tried the manual install.
I'm currently running the C+ profile for 720p mkv which is most of what I'm watching.
This doesn't help you but it does confirm that you don't seem to be the only person having this problem.
J.

---

### Post by laffinet on 2009-11-04
> **geekyhawkes said:**
> Anyone experiancing the same?

Not sure if it's the same, but I'm experiencing "random blocks" during mpeg2 playback (eg live TV).

Have a look [here]("http://ubuntuforums.org/showthread.php?t=1063102&page=13") starting with post #129 and the links I posted there.

Haven't been able to fix the issue so far, tried lots, including fresh 9.10 install, no change. 

Can't run vdpau decoding :(

---

### Post by xinix on 2009-11-04
I've had abysmal results using the nvidia driver lately and for a little while now.  I disabled the driver completely and I'm just using the 'nv' driver.  It has had good playback, even with hd recordings.  Before, I was being plagued by lots of freezing, not just with playback, even outside of Mythtv.  Often, during playback, the image would artifact into little green squares.  The behaviour was erratic too.  I could watch a recording with no trouble.  Later I wouldn't get the same recording to play more than 2 seconds.

Now it just plays the recording like it should.  No tearing, skipping, freezing or anything like that.  I have a 6200 card so vdpau is not an option.  But then any card that is vdpau capable has more power than mine.

Having said all of that,  I have the same nvidia driver installed on a laptop and have not had a single issue.  Strange.

---

### Post by suffice on 2009-11-05
I've been using mythtv for a few years, but I'm totally new to this vdpau stuff. I got a new GT220 installed karmic clean and mythbuntu-desktop.  

How do i even know if its working?  It Seems to be playing videos fine, but when i read about all of this it seemed that the phoronix test guys had a super low cpu usage, while mine seems to be at about 40%.  Which makes me think that its not working at all, even though the videos are playing ok.

---

### Post by Dewey_Oxberger on 2009-11-05
I have the same MB (M3N78 with the nvidia 8300).  VDPAU isn't working for me either.

To be a bit clearer.  You install mythbuntu, then go into setup and set the video profile to one of the three that use vdpau (slim, normal, and some deluxe something) - or - you make your own profile that uses vdpau.

I've tinkered for hours and I can't find a combo that will play both DVD (with the internal player) and recordings and livetv (with an HDHomeRun).

The problem I'm having is the framerate goes too fast and gets ahead of the audio, then it seems to bog down and lets the audio catch up, then it goes too fast again.  It does that over and over.  The cycle takes a several seconds.  On DVDs the framerate must be 10x what it should be.  It's kind of funny to watch - super fast motion.

I'm going to try vdpau in xbmc next and see if it's an internal player problem (for the dvd).

---

### Post by Dewey_Oxberger on 2009-11-05
I forgot to mention: I use top to check cpu usage from an ssh session from one of my other pcs.  It shows about 100% without vdpau displaying hdtv.  It shows about 15% with vdpau.

As for dvd it's about 20% without and about 4% with vdpau.

Nice.  If only it worked for me.

---

### Post by hackmeister on 2009-11-05
> **johnnybirdman said:**
> I have a fresh 9.10 install and tried all the VDPAU profiles but got bad results with all of them when trying to watch 720p mkv.  Standard Def avi and DVD's are fine.  
I have an 8600gt xxx and am running the nvidia 185 drivers.  I tried to install the 190 driver but had that pesky problem of it wanting to uninstall everything myth.  I haven't tried the manual install.
I'm currently running the C+ profile for 720p mkv which is most of what I'm watching.
This doesn't help you but it does confirm that you don't seem to be the only person having this problem.
J.

I have the same 8600GT card. Try playing with the de-interlacers in your playback profiles. I got the best results using vdpau-normal, bob 2x de-interlacer. Using bob made a huge difference. Bob is also working best on my Nvidia Ion frontend box. I suggest people ssh into their Myth systems when playing back HD video and running top to monitor their cpu load. With the 185 driver it seems my CPU will spike to about 40% with HD video (h264 & mpeg2) during the first 30 seconds or so then settle down below 6% for the rest. My capture devices are a PVR-1212 and an HDHomerun. I do hope the packages for the Nvidia 190 driver becomes available as it has a bunch of performance improvements and bug fixes. Before doing a clean install of 9.10 I was running 9.04 with the Avenard packages (VDPAU backported for Myth 0.21).

---

### Post by Dewey_Oxberger on 2009-11-05
Oops, I failed to mention that it's the deinterlacers that I tinkered with.  I tried them all.  I can get livetv and tv recordings to almost work - but then dvd is totally screwed.  I can get dvd to almost work - but then tv is screwed.  I couldn't find any combo where both worked.

---

### Post by David Grigor on 2009-11-05
> **geekyhawkes said:**
> Has anyone else experienced this problem?  I would really like to have vdpau working but the image isnt fit for watching currently.

(Video card wise i have an 8300 chipset on my asus M3N78-EM board).

Thanks


I have the M3N78-VM board with the 8200 chipset. 

You likely need to play with the cpufreq.  Mine was set to 1000mhz for the low. Changing to 18000mhz as it was described to me, increases the speed of the memory that yours onboard chipset is running. 

Do some searches for "cpufreq m3n78" to find more info and technical specifics. 

Easiest way to monitor and change the settings is to install cpufrequtils and cpufreq-selector packages. 

It certainly improved things to an acceptable level for me. I'm still going to eventually add a seperate video card because I can only run the lower interlace settings.

---

### Post by geekyhawkes on 2009-11-05
Interesting, how do i actually change the cpu freq?  I had seen some people talking about under clocking the gpu to try and solve artifacts, but i am confused exactly what changing the cpu freq does?  Are you suggesting i should overclock something from 1000mhz to 1800mhz?  I am using an amd 64 chip which in none vdpau rarly gets over 40% (although with vdpau its more like 4%).

---

### Post by johnnybirdman on 2009-11-09
> **hackmeister said:**
> I have the same 8600GT card. 

thanks, worked like a charm.
J.

---

### Post by Dewey_Oxberger on 2009-11-09
I was having inconsistent frame rates and occasional blocky display.  I tried the cpufrequtils and the cpufreqd stuff.  That seems to have fixed it.

I installed cpufreqd.  Then changed the cpufreq.conf to set the min freq for the AC=on profile to 1.8G.  Works fine now.

---

### Post by cubdukat on 2009-11-12
I have not been able to get ANYTHING working reliably in Mythbuntu Karmic. I can't install the restricted Nvidia 185 driver without things becoming completely borked. All it does for bootup is flash the shell login constantly. Sometimes if I hit Ctrl-Alt-Del, I can shut things down, but that's not always guaranteed.

In addition, after adding the Avenard repository, I can't completely upgrade to the latest version. It always stops on libvdpau1. After that, no matter what I tell it to do in apt-get to repair the broken packages it creates, it refuses to cooperate. If I try to uninstall it, it wants to take all of MythTV with it.

To say I'm seriously disappointed with Mythbuntu would be a complete understatement. Even Vista was better behaved than this. 

Right now my main questions are these"

1. Should I allow it to uninstall all of the parts of MythTV it wants, then reinstall them separately;

2. If so, would simply reinstalling mythbuntu-desktop fix that?

3. And finally, would installing regular Ubuntu, getting the NVidia driver and libvdpau1 working, then installing mythbuntu-desktop work?

In the past three days, I have reinstalled Mythbuntu no less than 25 times! Needless to say, that is completely unacceptable for any software, all the more so for Linux. I want to stay with Mythbuntu because out of all the Myth-based distros I've dealt with, it's the most polished out of the box. But if I have to, I'll go to Mythdora or one of the others. My patience is rapidly running out with Mythbuntu. Karmic in general is making me lose faith in Ubuntu, and this definitely doesn't help.

---

### Post by nickrout on 2009-11-12
> **cubdukat said:**
> I have not been able to get ANYTHING working reliably in Mythbuntu Karmic. I can't install the restricted Nvidia 185 driver without things becoming completely borked. All it does for bootup is flash the shell login constantly. Sometimes if I hit Ctrl-Alt-Del, I can shut things down, but that's not always guaranteed.

In addition, after adding the Avenard repository, I can't completely upgrade to the latest version. It always stops on libvdpau1. After that, no matter what I tell it to do in apt-get to repair the broken packages it creates, it refuses to cooperate. If I try to uninstall it, it wants to take all of MythTV with it.

To say I'm seriously disappointed with Mythbuntu would be a complete understatement. Even Vista was better behaved than this. 

Right now my main questions are these"

1. Should I allow it to uninstall all of the parts of MythTV it wants, then reinstall them separately;

2. If so, would simply reinstalling mythbuntu-desktop fix that?

3. And finally, would installing regular Ubuntu, getting the NVidia driver and libvdpau1 working, then installing mythbuntu-desktop work?

In the past three days, I have reinstalled Mythbuntu no less than 25 times! Needless to say, that is completely unacceptable for any software, all the more so for Linux. I want to stay with Mythbuntu because out of all the Myth-based distros I've dealt with, it's the most polished out of the box. But if I have to, I'll go to Mythdora or one of the others. My patience is rapidly running out with Mythbuntu. Karmic in general is making me lose faith in Ubuntu, and this definitely doesn't help.

Have you read this?

[http://avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html](http://avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html)

---

### Post by cubdukat on 2009-11-12
Actually, I did, and the results were exactly the same.

The only question I have is can this be done from within a fresh Mythbuntu install, or do I have to install regular Ubuntu, do this, then install mythbuntu-desktop?

Basically the way I've been handling things is like this"

Install Mythbuntu Karmic from CD
reboot
add Avenard repo
sudo apt-get update
DISASTER, as it refuses to upgrade libvdpau1 and breaks two packages.

Note that I have not set up the backend yet. I hold off on doing that until after I've compiled the drivers for the Hauppauge HVR-2250. Should I have set this up before I did apt-get update, because I recalled seeing it say that I had not set up the backend and the frontend yet.

---

### Post by nickrout on 2009-11-13
> **cubdukat said:**
> Actually, I did, and the results were exactly the same.

The only question I have is can this be done from within a fresh Mythbuntu install, or do I have to install regular Ubuntu, do this, then install mythbuntu-desktop?

Basically the way I've been handling things is like this"

Install Mythbuntu Karmic from CD
reboot
add Avenard repo
sudo apt-get update
DISASTER, as it refuses to upgrade libvdpau1 and breaks two packages.

Note that I have not set up the backend yet. I hold off on doing that until after I've compiled the drivers for the Hauppauge HVR-2250. Should I have set this up before I did apt-get update, because I recalled seeing it say that I had not set up the backend and the frontend yet.

did you read the page i pointed to?

```
sudo apt-get update

sudo apt-get install nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source

sudo apt-get install libvdpau1
```

and yes, can be done from mythbuntu

---

### Post by cubdukat on 2009-11-13
Again, that is exactly what I did, and it STILL didn't work.

Not to mention that I also got the flashing shell again, and was forced to reinstall everything again.

I even tried it by installing regular Ubuntu, attempting this, then installing mythbuntu-desktop, but sadly, it just refuses to cooperate with me.

I don't know what the problem is, but I have given up on it entirely. The system's entire intention is to serve as a backup in case Windows 7 goes down while I'm at work. Everything that Windows Media Center is set to record is mirrored in MythTV so that I don't miss anything. Right now Mythbuntu is entirely too borked for me to use it as my primary HTPC software. Just so long as it can function adequately as a backup, it stays, but I just reinstalled it for the absolute last time. 

I have been a fairly loyal Ubuntu user, but this is giving me pause. I don't know if this is a quirk unique to Ubuntu or Linux, or whether this is NVidia being difficult, and quite frankly, I don't care anymore. Someone needs to fix this. If I had even rudimentary programming skills, I would, but sadly I don't--certainly not skills enough to achieve a fix like this.

---

### Post by korgman on 2009-11-13
> **cubdukat said:**
> In addition, after adding the Avenard repository, I can't completely upgrade to the latest version. 

I didn't have to add that repository and VDPAU is working on my 8300 IGP.  I had done a clean install of Mythbuntu 9.04 (with fixes) last month, and upgraded to 9.10 a few nights ago.  The VDPAU options were suddenly available and I selected VDPAU SLIM profile.  Things have been working fine.

---

### Post by cubdukat on 2009-11-13
I just had an idea. Not to sound like a noob, but I have both the standard Mythbuntu and Avenard's repos activated at the same time. Would this work if I deactivated the standard Mythbuntu one? I'm going to try this, and if it doesn't work, I'll just reinstall it for the last time and not tinker with it until they get it right.

---

### Post by cubdukat on 2009-11-14
Okay, scratch that, it didn't work. The hell with it. I'll just make do without VDPAU.

---

### Post by nickrout on 2009-11-14
> **cubdukat said:**
> Okay, scratch that, it didn't work. The hell with it. I'll just make do without VDPAU.


Why do you want the avenard repos? you don't need them with 0.22 to have vdpau enabled?

---

### Post by 365nice on 2009-11-14
> Why do you want the avenard repos? you don't need them with 0.22 to have vdpau enabled? 	

That doesn't seem to be the case for me either? I installed a clean 9.10 (32 bit) on a system with an 8200 chipset with the NVidia 185 drivers activated, and when I try to use the VDPau playback options in the log I get an error that VDPau can't be detected and my frontend freezes with the Waiting... message on the playback screen.

I assumed I had to do something extra to add VDPau support - so had been reading about the Avenard stuff to see if that would make a difference.

Tim

---

### Post by jyavenard on 2009-11-14
> **Dewey_Oxberger said:**
> I have the same MB (M3N78 with the nvidia 8300).  VDPAU isn't working for me either.

To be a bit clearer.  You install mythbuntu, then go into setup and set the video profile to one of the three that use vdpau (slim, normal, and some deluxe something) - or - you make your own profile that uses vdpau.



*none* of those profiles uses VDPAU..
so not the best advice of all if you want vdpau

> I've tinkered for hours and I can't find a combo that will play both DVD (with the internal player) and recordings and livetv (with an HDHomeRun).

The problem I'm having is the framerate goes too fast and gets ahead of the audio, then it seems to bog down and lets the audio catch up, then it goes too fast again.  It does that over and over.  The cycle takes a several seconds.  On DVDs the framerate must be 10x what it should be.  It's kind of funny to watch - super fast motion.


nothing to do with vdpau, it's a bug in mythtv and dvd playback.

I'm going to try vdpau in xbmc next and see if it's an internal player problem (for the dvd).[/QUOTE]

Jean-Yves

---

### Post by jyavenard on 2009-11-14
> **cubdukat said:**
> 

In addition, after adding the Avenard repository, I can't completely upgrade to the latest version. It always stops on libvdpau1. After that, no matter what I tell it to do in apt-get to repair the broken packages it creates, it refuses to cooperate. If I try to uninstall it, it wants to take all of MythTV with it.



[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html)

BTW, those steps will be the same if you are installing the mythbuntu weekly build repo, which now uses libvdpau1 package too...

---

### Post by jyavenard on 2009-11-14
> **cubdukat said:**
> Again, that is exactly what I did, and it STILL didn't work.

Not to mention that I also got the flashing shell again, and was forced to reinstall everything again.

I even tried it by installing regular Ubuntu, attempting this, then installing mythbuntu-desktop, but sadly, it just refuses to cooperate with me.

I don't know what the problem is, but I have given up on it entirely. The system's entire intention is to serve as a backup in case Windows 7 goes down while I'm at work. Everything that Windows Media Center is set to record is mirrored in MythTV so that I don't miss anything. Right now Mythbuntu is entirely too borked for me to use it as my primary HTPC software. Just so long as it can function adequately as a backup, it stays, but I just reinstalled it for the absolute last time. 

I have been a fairly loyal Ubuntu user, but this is giving me pause. I don't know if this is a quirk unique to Ubuntu or Linux, or whether this is NVidia being difficult, and quite frankly, I don't care anymore. Someone needs to fix this. If I had even rudimentary programming skills, I would, but sadly I don't--certainly not skills enough to achieve a fix like this.

What you posted before suggest that you didn't follow those steps *exactly*. Because the error you are getting is precisely why I wrote those instructions to start with.

libvdpau1 isn't compatible with ubuntu's nvidia 185.18.36 which are the default nvidia drivers installed.
You *must* (with emphasis on the must) upgrade the nvidia drivers first, and only those... *then* and only then can you perform a full upgrade.

if you don't do it that way, it will fail... guaranteed

---

### Post by Dewey_Oxberger on 2009-11-14
> **jyavenard said:**
> *none* of those profiles uses VDPAU..
so not the best advice of all if you want vdpau


Oops - my bad, I didn't notice there were "near dups" in the names.

When I said Normal, Slim, High Quality I ment:

On a fresh 9.10 install:

Navigate to Utilities/Setup - Setup - TV Settings - Playback
Then work your way to the Playback profiles (3/9) screen

Then set Current Playback Profile to one of:

VDPAU High Quality,
VDPAU Normal
or VDPAU Slim

A quick check shows all of those profiles use VDPAU.  The key difference is what resolutions use what deinterlacers.

For these 8200 and 8300 based cards Bob2X is about all they can handle.

---

### Post by Dewey_Oxberger on 2009-11-14
> **jyavenard said:**
> 
I'm going to try vdpau in xbmc next and see if it's an internal player problem (for the dvd).

Just a follow up:

DVD playback with VPDAU on a clean install of mythbuntu 9.10 with the stock 185 restricted drivers with cpufreqd keeping the clock above 1.8G on a Asus M3N78-EM (8300 based) board with a dual core 2.8G Amd processor with a custom profile that is doing all resolutions= vdpau, vdpau with Bob2X (whew...):

in mythtv - internal player: doesn't work so well (fast then slow video, odd pauses every few seconds) - I can't handle trying to watch it, it's too disturbing.

in xbmc: works good, I see some slight blurring every few seconds that makes me wonder if it has the same problem as mythtv-internal.  Very watchable.

in vlc: spot on perfect.  Zero defects.

---

### Post by jyavenard on 2009-11-14
> **Dewey_Oxberger said:**
> Just a follow up:

DVD playback with VPDAU on a clean install of mythbuntu 9.10 with the stock 185 restricted drivers with cpufreqd keeping the clock above 1.8G on a Asus M3N78-EM (8300 based) board with a dual core 2.8G Amd processor with a custom profile that is doing all resolutions= vdpau, vdpau with Bob2X (whew...):

in mythtv - internal player: doesn't work so well (fast then slow video, odd pauses every few seconds) - I can't handle trying to watch it, it's too disturbing.


Once again, this isn't related to VDPAU ; a fix made in mythtv shortly before 0.22-fixes was released; broke something with DVD playback..
[http://svn.mythtv.org/trac/ticket/7067](http://svn.mythtv.org/trac/ticket/7067)

Note that the patch provided to fix doesn't work for everyone

---

### Post by Dewey_Oxberger on 2009-11-14
> **jyavenard said:**
> Once again, this isn't related to VDPAU ; a fix made in mythtv shortly before 0.22-fixes was released; broke something with DVD playback..
[http://svn.mythtv.org/trac/ticket/7067](http://svn.mythtv.org/trac/ticket/7067)

Note that the patch provided to fix doesn't work for everyone

Relax.  It wasn't my intent to implicate vdpau.  I'm just trying to be clear and let the other 8200 and 8300 owners know what to expect as of today.

Minor note: The dvd playback defect I'm talking about isn't the "about 2x" playback issue.  It's a more subtle frame skip and pause issue that has existed since 8.04.  That issue has nothing to do with vdpau.

---

### Post by cubdukat on 2009-11-15
> **jyavenard said:**
> What you posted before suggest that you didn't follow those steps *exactly*. Because the error you are getting is precisely why I wrote those instructions to start with.

libvdpau1 isn't compatible with ubuntu's nvidia 185.18.36 which are the default nvidia drivers installed.
You *must* (with emphasis on the must) upgrade the nvidia drivers first, and only those... *then* and only then can you perform a full upgrade.

if you don't do it that way, it will fail... guaranteed

Okay, here is exactly what I am doing:

Install Mythbuntu 9.10
Activate Avenard repo
sudo apt-get install nvidia* as per instructions
IT REFUSES TO COOPERATE!!!!

So, yes, I am following the instructions exactly as they are written, but something is not working. As far as I know Mythbuntu is not installing any other NVidia drivers other than the "nv" one. 

So the only other alternative I see is uninstalling everything Nvidia, and along with it all of Mythtv, or just hang it all and get along without VDPAU, and right now that's the way I'm leaning. I have already had to fiddle with this entirely too much. Everyone keeps telling me it should work, and it's not. 

In addition, I checked the logs from the last four or five times I attempted to install the Nvidia drivers, and it says that they taint the kernel. 

So I guess I would need a step-by-step list of what to do, because something is going wrong somewhere. I am not a noob by any stretch of the imagination, but I have absolutely no more patience for this.

---

### Post by nickrout on 2009-11-15
> **cubdukat said:**
> Okay, here is exactly what I am doing:

Install Mythbuntu 9.10
Activate Avenard repo
sudo apt-get install nvidia* as per instructions
IT REFUSES TO COOPERATE!!!!



Perhaps if you post the exact error message someone can help you. > 
In addition, I checked the logs from the last four or five times I attempted to install the Nvidia drivers, and it says that they taint the kernel. 


Yes they will taint the kernel, as they are not open source. Unless you are really determined to have an entirely open source system, this need not worry you. > 
So I guess I would need a step-by-step list of what to do, because something is going wrong somewhere. I am not a noob by any stretch of the imagination, but I have absolutely no more patience for this.

Yes we can tell that...

But the step by step instructions have been pointed to. Beyond saying it doesn't work, you give us no error messages. Please do and we will try to help.

---

### Post by cubdukat on 2009-11-15
> **nickrout said:**
> Perhaps if you post the exact error message someone can help you. 

Yes they will taint the kernel, as they are not open source. Unless you are really determined to have an entirely open source system, this need not worry you. 

Yes we can tell that...

But the step by step instructions have been pointed to. Beyond saying it doesn't work, you give us no error messages. Please do and we will try to help.

I'll dig through them. The two ones I looked at were whatever logs Mythbuntu pulls up when you run the log gatherer and kern.log, which is where I got the tainted kernel message.

Are there any other logs I would need? I should be able to dig them up presently. Right now it's recording something in Win7, but it should be done soon.

---

### Post by nickrout on 2009-11-15
> **cubdukat said:**
> I'll dig through them. The two ones I looked at were whatever logs Mythbuntu pulls up when you run the log gatherer and kern.log, which is where I got the tainted kernel message.

Are there any other logs I would need? I should be able to dig them up presently. Right now it's recording something in Win7, but it should be done soon.

When you run ```
sudo apt-get install nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source 
```as per the instructions, what is the output at your terminal?

---

### Post by pootle1 on 2009-11-17
I've already moved to Nvidia drivers 190.42 on one system (I need at least 190.3x for my GT200 card).

is it practical to hook up with latest myth through this repo, or will it all fall apart??

I'm keen to get fixes for vdpau in dvd player for example - but if it's likely to be painful, I'll just hang around until things have stabilized a bit more.

I'm on a front end only karmic clean install with nvidia drivers the only non-standard element.

---

### Post by cubdukat on 2009-11-18
> **nickrout said:**
> When you run ```
sudo apt-get install nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source 
```as per the instructions, what is the output at your terminal?

This is what I get:

cubdukat@cubdukat-desktop:~$ sudo apt-get install nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source
Reading package lists... 0%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-185 is already the newest version.
nvidia-185-libvdpau is already the newest version.
nvidia-185-kernel-source is already the newest version.
nvidia-185-kernel-source set to manually installed.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libmyth-0.22-0: Depends: libvdpau1 (>= 0.2) but it is not going to be installed
  mplayer: Depends: libvdpau1 (>= 0.2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
cubdukat@cubdukat-desktop:~$ 
cubdukat@cubdukat-desktop:~$ 


That is the exact same thing I keep getting every single time I try to update. It's holding back other packages as well. And when I follow its advice and do "sudo apt-get 0f install," I get this:

cubdukat@cubdukat-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libvdpau1
The following NEW packages will be installed:
  libvdpau1
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
17 not fully installed or removed.
Need to get 0B/23.2kB of archives.
After this operation, 131kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 87106 files and directories currently installed.)
Unpacking libvdpau1 (from .../libvdpau1_0.2.1-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libvdpau1_0.2.1-0ubuntu3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libvdpau.so.1', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9
Errors were encountered while processing:
 /var/cache/apt/archives/libvdpau1_0.2.1-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
cubdukat@cubdukat-desktop:~$ 

So, as you can see, I am following the instructions exactly as given. Maybe there's something I'm missing, but I'm not going to waste any more time on it. As long as it records my programs when Windows 7 restarts itself, I really don't care anymore.

---

### Post by jyavenard on 2009-11-19
> **cubdukat said:**
> This is what I get:

cubdukat@cubdukat-desktop:~$ sudo apt-get install nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source
Reading package lists... 0%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-185 is already the newest version.
nvidia-185-libvdpau is already the newest version.
nvidia-185-kernel-source is already the newest version.
nvidia-185-kernel-source set to manually installed.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libmyth-0.22-0: Depends: libvdpau1 (>= 0.2) but it is not going to be installed
  mplayer: Depends: libvdpau1 (>= 0.2) but it is not going to be 

You have started an earlier upgrade which you have interrupted and left it in a broken state.

So you have to go in synaptic ; disable the avenard repo ; repair packages ; re-enable avenard repo then install the nvidia drivers only first, then do a full upgrade

> So, as you can see, I am following the instructions exactly as given. Maybe there's something I'm missing

No you haven't.
Otherwise when trying to install the nvidia drivers it wouldn't try to finish an earlier mythtv update

The other possibility, is uninstall all mythtv packages as well as nvidia drivers ; then re-install..

---

### Post by orduek on 2009-11-19
> **David Grigor said:**
> I have the M3N78-VM board with the 8200 chipset. 

You likely need to play with the cpufreq.  Mine was set to 1000mhz for the low. Changing to 18000mhz as it was described to me, increases the speed of the memory that yours onboard chipset is running. 

Do some searches for "cpufreq m3n78" to find more info and technical specifics. 

Easiest way to monitor and change the settings is to install cpufrequtils and cpufreq-selector packages. 

It certainly improved things to an acceptable level for me. I'm still going to eventually add a seperate video card because I can only run the lower interlace settings.

Will it help to a 9400GT card also?
I also experience frequent freezing and pixelations.

---

### Post by Dewey_Oxberger on 2009-11-19
> **orduek said:**
> Will it help to a 9400GT card also?
I also experience frequent freezing and pixelations.

It's easy enough to try.

```
sudo apt-get install cpufrequtils
```  I think that's what it's called - then do a ```
cpufreq-info
``` and see what it says.  Then try a ```
cpufreq-set -d 1.8G
```  -- all this is from memory but it should be close to what you need.

It will set cpufreq-min to 1.8G but the change won't survive a reboot.  Then pop over to mythfrontend and try it again.

I'd guess you need to edit your profile and drop the deinterlacer down a notch but try the cpufreq thing first and report back if it works - Thanks

---

### Post by cubdukat on 2009-11-19
> **jyavenard said:**
> You have started an earlier upgrade which you have interrupted and left it in a broken state.

So you have to go in synaptic ; disable the avenard repo ; repair packages ; re-enable avenard repo then install the nvidia drivers only first, then do a full upgrade



No you haven't.
Otherwise when trying to install the nvidia drivers it wouldn't try to finish an earlier mythtv update

The other possibility, is uninstall all mythtv packages as well as nvidia drivers ; then re-install..

I think that's what I'm going to try. The only problem is that the nvidia drivers bork the system. I've been scouring the other sections of the forum about this and it seems there's a problem with either the kernel itself or Nvidia's driver, or both. But here goes again. I should be back in about an hour with the end results...

I'll be starting with a clean Mythbuntu install because my previous attempt to get both VDPAU and the Nvidia drivers to cooperate borked my system, and I couldn't even boot into recovery mode.

---

### Post by rodercot on 2009-11-20
> **orduek said:**
> Will it help to a 9400GT card also?
I also experience frequent freezing and pixelations.


 I run two P5N7A-VM boards one with a 7300 Overclocked to 3 from 2.6 or 2.8 stock and the other with a 7400 stepped up to 3 from stock. 

 I am running the latest update myth 55829 .22 and both have the 190.42 drivers installed I have to run mine on VDPAU slim to get good playback. Normal and HQ both cause the same freezing, pausing but not much pixelation. 

 Slim mode unfortunately gives me a very washed out look on still images with things like DVD Menus, it's like the sharpness is maxed one way or the other. 

 But playback DVD and AVI is perfect no freezing at all, I have not tried HD, I use XBMC for that using the livetv.pl switch script so myth is shutdown while xbmc is running I am on XBMC Alpha2 testing on one machine and the most recent stable version before the svn path switch on the other, they play all just fine. 

 Regards,

 Dave

---

### Post by jMon54 on 2009-11-20
I am having an issue where when I record programs while not in frontend, for example in mythwelcome, I get tons of errors and recordings stop within minutes.  The errors are similar to what you get when you have a poor signal.  But if I have my frontend running (like if I am actually watching the program being recorded) and record that way, all is fine.  Anyone have a clue why this would be the case? I am using the VDPAU high and tried the VDPAU normal with the same results.

---

### Post by cubdukat on 2009-11-21
> **cubdukat said:**
> I think that's what I'm going to try. The only problem is that the nvidia drivers bork the system. I've been scouring the other sections of the forum about this and it seems there's a problem with either the kernel itself or Nvidia's driver, or both. But here goes again. I should be back in about an hour with the end results...

I'll be starting with a clean Mythbuntu install because my previous attempt to get both VDPAU and the Nvidia drivers to cooperate borked my system, and I couldn't even boot into recovery mode.

Turns out I solved part of my problem. It apparently involves not adding the Avenard repository. Unfortunately, it still doesn't resolve the issue of Nvidia's drivers borking the system, but from what I'm reading this is a kernel issue. Apparently that problem also happens with ATI's binary driver too. So I'll just wait until the next kernel update to see if that fixes it, and in the meantime, I'll just have to make do with jerky TV playback. Like I said before, the Mythbuntu install's main purpose is to be a contingency plan for when Win7 decides to restart itself while I'm at work. I'd like it to become my primary OS eventually, but right now that's a non-starter because of all these problems. 

Maybe one day I'll pick it up again, but for the time being I'll just leave things as they are. It seems the more I tinker, the more likely I'll end up reinstalling things.

---

### Post by perveilerj on 2009-12-01
I'm having the same problems as cubdukat.  Here I am starting from scratch (well, "scratch" is pre-avenard repo from an up-to-date mythbuntu):

(Skip to SKIP TO HERE if you don't want a rehash of what cubdukat said, more or less)

First get the key:
```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key
--2009-12-01 19:32:49--  http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key
Resolving www.avenard.org... 88.191.110.21
Connecting to www.avenard.org|88.191.110.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1743 (1.7K) [application/pgp-keys]
Saving to: `ubuntu-repos.key'

100%[======================================>] 1,743       --.-K/s   in 0s      

2009-12-01 19:32:49 (176 MB/s) - `ubuntu-repos.key' saved [1743/1743]

OK
```

Then add the repo list:
```
echo "deb http://www.avenard.org/files/ubuntu-repos karmic release" | sudo tee /etc/apt/sources.list.d/avenard.list
deb http://www.avenard.org/files/ubuntu-repos karmic release
```

Then start cutting-and-pasting from [http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html)

```
sudo apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release.gpg                  
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US       
Hit http://www.avenard.org karmic Release.gpg                        
Ign http://www.avenard.org karmic/release Translation-en_US          
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://www.avenard.org karmic Release                           
Hit http://us.archive.ubuntu.com karmic Release                     
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://www.avenard.org karmic/release Packages                   
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://security.ubuntu.com karmic-security/restricted Packages  
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done
```

And...
```

sudo apt-get install nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-185 is already the newest version.
nvidia-glx-185 set to manually installed.
nvidia-185-libvdpau is already the newest version.
nvidia-185-libvdpau set to manually installed.
nvidia-185-kernel-source is already the newest version.
nvidia-185-kernel-source set to manually installed.
The following packages were automatically installed and are no longer required:
  binutils-static
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
```

And...

```
sudo apt-get install libvdpau1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  binutils-static
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  vdpau-driver-all
The following NEW packages will be installed:
  libvdpau1 vdpau-driver-all
0 upgraded, 2 newly installed, 0 to remove and 40 not upgraded.
Need to get 32.2kB of archives.
After this operation, 168kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://www.avenard.org karmic/release vdpau-driver-all 0.3-0ubuntu3 [4,550B]
Get:2 http://www.avenard.org karmic/release libvdpau1 0.3-0ubuntu3 [27.6kB]
Fetched 32.2kB in 0s (54.5kB/s)  
Selecting previously deselected package vdpau-driver-all.
(Reading database ... 105281 files and directories currently installed.)
Unpacking vdpau-driver-all (from .../vdpau-driver-all_0.3-0ubuntu3_all.deb) ...
Selecting previously deselected package libvdpau1.
Unpacking libvdpau1 (from .../libvdpau1_0.3-0ubuntu3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libvdpau1_0.3-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libvdpau.so.1', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9
Errors were encountered while processing:
 /var/cache/apt/archives/libvdpau1_0.3-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I didn't try upgrading nvidia-anything in the past, etc.  Just plain mythbuntu karmic with whatever updates have come from the usual channels.  Nothing special, and nothing reporting broken.

SKIP TO HERE

I notice that synaptic says I have 2 versions of nvidia-glx-185 available though:

185.18.36-0ubuntu9 (karmic)
185.18.36-0ubuntu3 (karmic)

apt-cache says that the 0ubuntu9 comes from:
```
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_restricted_binary-amd64_Packages
```

And 0ubuntu3 from:
```
/var/lib/apt/lists/www.avenard.org_files_ubuntu-repos_dists_karmic_release_binary-amd64_Packages
```

Is the problem just that ubuntu is providing a bigger version number than the JYA repo, resulting in no upgrade?  Seems like forcing the 0ubuntu3 version should do the trick, but unfortunately my machine is recording for the night now so I can't test until tomorrow.

--Jack

---

### Post by perveilerj on 2009-12-02
Not surprisingly, forcing nvidia-glx-185, nvidia-185-libvdpau, and nvidia-185-kernel-source to the 0ubuntu3 version did the trick.

JYA, I don't suppose you could up the version number on your packages so your instructions on [http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html) "just work" again?  It might save you some questions in the future.

--Jack

---

### Post by cubdukat on 2009-12-07
Well, I believe I have solved my problem once and for all.

The solution: Install the 64-bit version.

Turns out that the PAE kernel and the NVidia driver were the culprits. Apparently it has issues with PAE and -RT kernels.

Right now I'm still setting up the system, so I haven't gotten a chance to test anything yet, but I bet it'll work quite well.

Guess it really does pay to install 64-bit after all...

---

### Post by cubdukat on 2009-12-07
> **cubdukat said:**
> Right now I'm still setting up the system, so I haven't gotten a chance to test anything yet, but I bet it'll work quite well.


It did. 1080i was infinitely watchable in VDPAU High Quality, and the processor didn't even belch. 

Hopefully when I add the Avenard repos, things will continue to work correctly, but if I were to stop right now, I'd be happy with the way the system's behaving.

I am now firmly back in the Ubuntu camp again. I wonder how come the 32-bit versions have so many issues.

---

### Post by brplut40 on 2009-12-12
I am still having problems getting upgraded to the newer nvidia drivers. Ultimately I would like to be running nvidia 190 drivers with mythbuntu 9.10 and mythtv .22. I have tried many times to follow jyavenard directions, but still cannot get them to work. I thought I was in luck when I saw what perveilerj posted, I am having the same problem. Can you please explain in detail how you forced those three packages to be installed from 0ubuntu3 and not 0ubuntu9. I will include all the problems I am having, in case what you did may not apply.

I start with a fresh install of mythbuntu 9.10 with the open source nvidia driver. I get the key for the Avenard repo and add the repo. At that point I look in the Synaptic package manager for nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source from 0ubuntu3, but they are not in there. I reload several times and run apt-get update from the command line, but they are not in there. The 190 and 195 version are all there, but not 185. since the package manager does not see them, I try to install them manually by using wget to download them and 

```
dpkg -i nvidia-glx-185_185.18.36-0ubuntu2_amd64.deb
Selecting previously deselected package nvidia-glx-185.
dpkg: regarding nvidia-glx-185_185.18.36-0ubuntu2_amd64.deb containing nvidia-glx-185:
 xserver-xorg-core conflicts with xserver-xorg-video-4
  nvidia-glx-185 provides xserver-xorg-video-4 and is to be installed.
dpkg: error processing nvidia-glx-185_185.18.36-0ubuntu2_amd64.deb (--install):
 conflicting packages - not installing nvidia-glx-185
Errors were encountered while processing:
 nvidia-glx-185_185.18.36-0ubuntu2_amd64.deb
```That does not work either. I am able to load the packages from the 0ubuntu9 repo just fine

```
apt-get install nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
nvidia-185-libvdpau is already the newest version.
The following extra packages will be installed:
  dkms fakeroot nvidia-settings patch
Suggested packages:
  diff-doc
The following NEW packages will be installed:
  dkms fakeroot nvidia-185-kernel-source nvidia-glx-185 nvidia-settings patch
0 upgraded, 6 newly installed, 0 to remove and 129 not upgraded.
Need to get 16.1MB/20.6MB of archives.
After this operation, 67.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com karmic/restricted nvidia-glx-185 185.18.36-0ubuntu9 [16.1MB]
Fetched 14.8MB in 1min 15s (195kB/s)
Selecting previously deselected package dkms.
(Reading database ... 83968 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.0.1-0ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.4ubuntu1_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_amd64.deb) ...
Selecting previously deselected package nvidia-185-kernel-source.
Unpacking nvidia-185-kernel-source (from .../nvidia-185-kernel-source_185.18.36-0ubuntu9_amd64.deb) ...
Unpacking nvidia-glx-185 (from .../nvidia-glx-185_185.18.36-0ubuntu9_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_190.36-0ubuntu6_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up dkms (2.1.0.1-0ubuntu1) ...
 * Running DKMS auto installation service for kernel 2.6.31-14-generic   [ OK ]

Setting up fakeroot (1.12.4ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up patch (2.5.9-5) ...
Setting up nvidia-185-kernel-source (185.18.36-0ubuntu9) ...
Loading new nvidia-185.18.36 DKMS files...
First Installation: checking all kernels...
Building for architecture x86_64
Building initial module for 2.6.31-14-generic
Done.

nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-14-generic/updates/dkms/

depmod.......

DKMS: install Completed.

Setting up nvidia-glx-185 (185.18.36-0ubuntu9) ...

Setting up nvidia-settings (190.36-0ubuntu6) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```Even though the Avenard repo is loaded, it will not pull the files from there. If I try to install the 190 packages from the Avenard repo, it will not let me do it without installing libvdpau1 at the same time, which yields the error:

```
dpkg: error processing /var/cache/apt/archives/libvdpau0_0.2-0ubuntu11_amd64.deb (--unpack):

                  trying to overwrite '/usr/lib/libvdpau_trace.so', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9
```Can someone please help me get the Avenard repo working with the 190 nvidia drivers.

---

### Post by brplut40 on 2009-12-13
SOLVED

I have fixed my own problem. Please see previous post for a description of the problem. Below is the solution.

After a fresh install of Mythbuntu 9.10 with the nvidia drivers add Avenard repo key 
```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo 
apt-key add ubuntu-repos.key && rm ubuntu-repos.key

--2009-12-13 18:31:16--  
http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key
Resolving www.avenard.org... 88.191.110.21
Connecting to www.avenard.org|88.191.110.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1743 (1.7K) [application/pgp-keys]
Saving to: `ubuntu-repos.key'

100%[======================================>] 1,743       --.-K/s   in 0.001s
2009-12-13 18:31:17 (1.22 MB/s) - `ubuntu-repos.key' saved [1743/1743]

OK
```add the repo
```
echo "deb http://www.avenard.org/files/ubuntu-repos karmic release" | 
sudo tee /etc/apt/sources.list.d/avenard.list

```manually download the libvdpau package from the Avenard repo
```
wget http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu
1_amd64.deb

--2009-12-13 18:32:49--  

http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu
1_amd64.deb
Resolving www.avenard.org... 88.191.110.21
Connecting to www.avenard.org|88.191.110.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27468 (27K) [application/x-debian-package]
Saving to: `libvdpau1_0.3-0ubuntu1_amd64.deb'

100%[======================================>] 27,468       127K/s   in 0.2s

2009-12-13 18:32:50 (127 KB/s) - `libvdpau1_0.3-0ubuntu1_amd64.deb' 
saved [27468/27468]
```manually install this package
```
sudo dpkg --force-all -i libvdpau1_0.3-0ubuntu1_amd64.deb
Selecting previously deselected package libvdpau1.
(Reading database ... 84179 files and directories currently installed.)
Unpacking libvdpau1 (from libvdpau1_0.3-0ubuntu1_amd64.deb) ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/lib/libvdpau.so.1', which is also in package 

nvidia-185-libvdpau 0:185.18.36-0ubuntu9
dpkg: libvdpau1: dependency problems, but configuring anyway as you 

requested:
 libvdpau1 depends on vdpau-driver-all; however:
  Package vdpau-driver-all is not installed.
Setting up libvdpau1 (0.3-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```This is a good time to update the repos
```
sudo apt-get update
Get:1 http://www.avenard.org karmic Release.gpg [189B]
Ign http://www.avenard.org karmic/release Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Get:2 http://www.avenard.org karmic Release [14.3kB]
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Get:3 http://www.avenard.org karmic/release Packages [102kB]
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Fetched 116kB in 11s (10.5kB/s)
Reading package lists... Done

```Now you have to fix the dependencies for the package you just installed
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  vdpau-driver-all
The following NEW packages will be installed:
  vdpau-driver-all
0 upgraded, 1 newly installed, 0 to remove and 131 not upgraded.
Need to get 4,550B of archives.
After this operation, 41.0kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://www.avenard.org karmic/release vdpau-driver-all 
0.3-0ubuntu3 [4,550B]
Fetched 4,550B in 0s (14.6kB/s)
Selecting previously deselected package vdpau-driver-all.
(Reading database ... 84188 files and directories currently installed.)
Unpacking vdpau-driver-all (from 
.../vdpau-driver-all_0.3-0ubuntu3_all.deb) ...
Setting up vdpau-driver-all (0.3-0ubuntu3) ...
```Now you can upgrade to the newer nvidia packages.
```
sudo apt-get install nvidia-glx-190 nvidia-190-libvdpau nvidia-190-kernel-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libmyth-0.22-0
The following packages will be REMOVED:
  nvidia-185-kernel-source nvidia-185-libvdpau nvidia-glx-185
The following NEW packages will be installed:
  nvidia-190-kernel-source nvidia-190-libvdpau nvidia-glx-190
The following packages will be upgraded:
  libmyth-0.22-0
1 upgraded, 3 newly installed, 3 to remove and 130 not upgraded.
Need to get 31.2MB of archives.
After this operation, 7,143kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://www.avenard.org karmic/release libmyth-0.22-0 

2:0.22.0-fixes22952-0ubuntu2 [9,392kB]
Get:2 http://www.avenard.org karmic/release nvidia-190-kernel-source 

190.42-0ubuntu3 [3,391kB]
Get:3 http://www.avenard.org karmic/release nvidia-190-libvdpau 

190.42-0ubuntu3 [1,503kB]
Get:4 http://www.avenard.org karmic/release nvidia-glx-190 

190.42-0ubuntu3 [16.9MB]
Fetched 31.2MB in 26s (1,178kB/s)
(Reading database ... 84193 files and directories currently installed.)
Removing nvidia-glx-185 ...
Removing nvidia-185-kernel-source ...
Removing all DKMS Modules
Done.
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 84096 files and directories currently installed.)
Preparing to replace libmyth-0.22-0 0.22.0+fixes22594-0ubuntu1 (using 

.../libmyth-0.22-0_2%3a0.22.0-fixes22952-0ubuntu2_amd64.deb) ...
Unpacking replacement libmyth-0.22-0 ...
(Reading database ... 84096 files and directories currently installed.)
Removing nvidia-185-libvdpau ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package nvidia-190-kernel-source.
(Reading database ... 84080 files and directories currently installed.)
Unpacking nvidia-190-kernel-source (from 

.../nvidia-190-kernel-source_190.42-0ubuntu3_amd64.deb) ...
Selecting previously deselected package nvidia-190-libvdpau.
Unpacking nvidia-190-libvdpau (from 

.../nvidia-190-libvdpau_190.42-0ubuntu3_amd64.deb) ...
Selecting previously deselected package nvidia-glx-190.
Unpacking nvidia-glx-190 (from 

.../nvidia-glx-190_190.42-0ubuntu3_amd64.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', 

please use '--print-architecture' instead.
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up libmyth-0.22-0 (2:0.22.0-fixes22952-0ubuntu2) ...

Setting up nvidia-190-kernel-source (190.42-0ubuntu3) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 190.42
Doing initial module build
Installing initial module
Done.

Setting up nvidia-190-libvdpau (190.42-0ubuntu3) ...
Setting up nvidia-glx-190 (190.42-0ubuntu3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```If you get a no screen found error on boot, run "nvidia-xconfig" from the command line and reboot.

---

### Post by geekyhawkes on 2009-12-15
So can you confirm that if the above is followed everyone is finding no issues with "artifacts / pixcelation" with vdpau?  I am still having issues on mythbuntu 910 (64bit) with the latest kernal and nvidiea 190 drivers.

(Sorry as per the first post Video card wise i have an 8300 chipset on my asus M3N78-EM board with 2gb of ram and 3.2ghz 64bit amd processor)

---

### Post by nickrout on 2009-12-15
what video card? how much ram? what playback settings?

---

### Post by Damnatus on 2009-12-20
hi,
i have exactly the same problem as [brplut40]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=976381").
i spend hours trying to solve it.... without any success.
so naturally i was really happy when i read his last post.
i followed all the steps just as described on page 5 but wenn i enter 

```
wget http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu
```i get the following message: 

```
damnatus@AsusPundit:~$ wget http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu
--2009-12-20 19:10:34--  http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu
Auflösen des Hostnamen »www.avenard.org«.... 88.191.110.21
Verbindungsaufbau zu www.avenard.org|88.191.110.21|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 404 Not Found
2009-12-20 19:10:34 FEHLER 404: Not Found.
```has anyone encountered similar errors or can tell me if i did something wrong ?
could really use some help with this one !!

---

### Post by nickrout on 2009-12-20
> **Damnatus said:**
> hi,
i have exactly the same problem as [brplut40]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=976381").
i spend hours trying to solve it.... without any success.
so naturally i was really happy when i read his last post.
i followed all the steps just as described on page 5 but wenn i enter 

```
wget http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu
```i get the following message: 



run the command that is given in the instructions, ie ```
wget http://www.avenard.org/files/ubuntu-repos/release/libvdpau1_0.3-0ubuntu1_amd64.deb

```

you were missing "1_amd64.deb" from the end of the line.

---

### Post by zorro07 on 2009-12-20
Hi,
 
I think you are asking just a little too much from the 8300 video card.  From my understanding its an early implimentation of VDPAU.  The 9400 seems to be a good entry point for really good VDPAU playback.  onbaord 8300 vid cards tend to lack dedicated vid ram using shared memory.  This acts as a bottleneck as far as vid perforance goes.  you may need to bump up the shared memory to as high as it will let you.  
 
If you can use a dedicated vid card get a 9500 or a gf220 1G card they rock!
 
regards
 
Paul

---

### Post by nickrout on 2009-12-20
qvdpautest is a good test for your card. google it, its not hard to find.

If you have an on_motherboard video card, allocate at least 512M RAM to it. 

Also ensure that frequency scaling is not slowing down the whole system, I think this is a problem particularly on AMD CPU's/chipsets.

---

### Post by nickrout on 2009-12-20
Herer is a sample output from qvdpautest

>  ./qvdpautest
./qvdpautestIntel(R) Pentium(R) 4 CPU 2.80GHz
30:42 NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:1:0:0 (GPU-0)

VDPAU API version : 0
VDPAU implementation : NVIDIA VDPAU Driver Shared Library  190.42  Tue Oct 20 20:55:52 PDT 2009

SURFACE GET BITS: 517.409 M/s
SURFACE PUT BITS: 331.357 M/s

MPEG DECODING (1920x1080): 75 frames/s
MPEG DECODING (1280x720): 170 frames/s
H264 DECODING (1920x1080): 65 frames/s
H264 DECODING (1280x720): 130 frames/s
VC1 DECODING (1440x1080): 85 frames/s

MIXER WEAVE (1920x1080): 222 frames/s
MIXER BOB (1920x1080): 333 fields/s
MIXER TEMPORAL (1920x1080): 71 fields/s
MIXER TEMPORAL + SKIP_CHROMA (1920x1080): 98 fields/s
MIXER TEMPORAL_SPATIAL (1920x1080): 25 fields/s
MIXER TEMPORAL_SPATIAL + SKIP_CHROMA (1920x1080): 27 fields/s

MIXER TEMPORAL_SPATIAL (720x576 video to 1920x1080 display): 95 fields/s


---

### Post by cozmicharlie on 2010-01-26
I had the same problem trying to install the NVIDIA 195.30 drivers in karmic from the NVIDIA package maintainers PPA.  I used a slight modification of the method outlined by brplut40 in post #50.  I added the repos to synaptic and tried to install libvdpau1 and like everyone else on this thread I received the conflict error.  However, I went to the cache (var/cache/apt/archives/var/cache/apt/archives/)
and found the nvidia-195-libvdpau_195.30-0ubuntu0~ppa1_i386.deb.  I copied it to my home folder and ran the command:

```
sudo dpkg --force-all -i nvidia-195-libvdpau_195.30-0ubuntu0~ppa1_i386.deb
```

I got the error messages just as brplut40 posted but it did install.  When I went into synaptic it showed libvdpau1 was installed correctly.  I then installed nvidia-195-libvdpau from synaptic and it installed without any problems.  I did not have to do the other steps.  I have not tested it yet but at least it hasn't hosed my system.

Couldn't have done it without brplut40's help.

Thanks

---

### Post by cedyathome on 2010-01-27
> **brplut40 said:**
> SOLVED

I have fixed my own problem. Please see previous post for a description of the problem. Below is the solution.

....

Thank you! The forced install solved it for me & I have a functioning mythtv system with the Nvidia 190.x drivers.

---

