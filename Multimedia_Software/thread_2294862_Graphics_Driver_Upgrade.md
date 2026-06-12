---
title: "Graphics Driver Upgrade"
date: 2015-09-14
forum: Multimedia Software
---

### Post by garyt53 on 2015-09-14
Hi Folks -

Perhaps this is not the right SubForum but **running win7 dualboot 14.04LTS at current update (k63) on AMD64 with NVIDIA GeForce9100integratedSSE2 and sometimes a Quadro FX card** (yes, sometimes....when performing intensive renderings) and according to NVIDIA both cards require the 340 driver, not the 304.  But I have been using the 304 as provided and updated by xorg/edgers, with no apparent problems as yet except for overheating of the 9100 onboard since the last xorg driver update.  Kinda afraid to plug in the Quadro card at this point.  I know, don't fix what's not broke (like the planned obsolescence going on right now), but after the last driver update it might be broke. ha   

**My question is simply how do I safely change GPU drivers from NVIDIA 304 to 340, step by step.**  I have found much material on the web regarding updating/upgrading graphics drivers but the instructions conflict.  Even having found what I considered to be credible information that I would be best served by applying the 340 driver published on the NVIDIA site as opposed to the xorg/edgers version with automatic updates.

I have a really well-built system that is Clonezilla-backed but really don't want to go through all that restoration again if it can be avoided.

I have both 62 and 63 latest kernels available on my system now if regressing is necessary, so whatever happens I promise I won't get mad at you. ha  Proof is, I haven't bothered you much and then only on deep issues.

Thank ya....in advance.

gt

---

### Post by Bucky Ball on 2015-09-14
*Thread moved to **Multimedia Software**.*

Do an update. Open Additional Drivers. Is the 340 in there? If so, enable it. :)

---

### Post by garyt53 on 2015-09-14
Wow, Bucky....pretty fast return!

Yes, the latest version is available in synaptic in addl-drivers.  Now, if you could please expand on whether I would be best served by the propitiatory or open source versions I can sleep well tonight.

gt

don't do win10

---

### Post by CitadelUniversal on 2015-09-14
You can use the latest nvidia-355 update via adding the ppa:graphics-drivers/ppa - this is the latest ppa which one of the main developers hope will eventually be implemented in the additional softwares  to add it in the terminal just do the following:

sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
sudo apt-get install nvidia-355 
sudo nvidia-xconfig

The latest 355 nvidia drivers is needed to run some of the latest steam games (example: Shadow of Mordor) & I've installed mine via the instructions which I've provided - it is perfectly safe to use and had no issues on my system......

---

### Post by Bucky Ball on 2015-09-14
@CitadelUniversal: Do you have the same graphics card as the OP? If not, it may not be safe for them to use at all.

---

### Post by Bucky Ball on 2015-09-14
> **garyt53 said:**
> Yes, the latest version is available in synaptic in addl-drivers.  Now, if you could please expand on whether I would be best served by the propitiatory or open source versions I can sleep well tonight.

Unfortunately, I can't advise one way or the other as to which you should use. I use the open-source one myself. Don't game so don't need anything else. I can watch HD TV and YouTube stuff so I'm happy.

If NVidia is telling you the 340 is the latest and functional/stable driver for your card, guess they'd know. :)

---

### Post by garyt53 on 2015-09-14
for BuckyBall -
Well Bucky, your last advice is likely the best.....but I was going to suggest this thread be relocated to "gamers" because I often construct elaborate and highly accurate 3D renderings in Rhino as well as a coupla other CADD programs and I suspect that is similar to gaming on the GPU.  But then I noticed Citadel's input and Citadel sounds like a gamer, or at least game-hip, so after one more question for Citadel we can close this effort.

for CitadelUniversal:
Checked NVIDIA again and 340.93 is suggested for both cards. Ubuntu 14 addl drivers indicates 340.73 as latest available. Being older cards, I suspect it would be best for me to not advance my update beyond what is indicated by NVIDIA.  A bit of input on this would be great.

Also, is it best to just use the Additional Drivers utility inside synaptic and without even purging NVIDIA first (since I am running 304 with many updates right now) or should I "compile" a manual install of driver 355 following all the steps indicated at official info central here?:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

A short concise response is OK as I understand this is a complicated issue.  I would have suspected Bucky's unusually short answer to just use the addl drivers utility but I value all your input and imagine the addl drivers utility probably does complete all the steps to uninstall/reinstall in effective automated fashion.

Thank you both.

gt

I should have said "win10 ***is*** for dummies" (ha)

---

### Post by Yellow Pasque on 2015-09-14
> **garyt53 said:**
>  I have found much material on the web regarding updating/upgrading graphics drivers but the instructions conflict. Even having found what I considered to be credible information that I would be best served by applying the 340 driver published on the NVIDIA site as opposed to the xorg/edgers version with automatic updates.

Do not try to install a driver directly from nvidia site or xorg-edgers PPA. If you must have latest 340 driver (340.93), see: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
(The authors of this PPA are trying to get it integrated directly into "Additional Drivers" screen, so the latest stable driver will be available throughout the life cycle of a release).

That being said, I'm not sure a video driver is going to fix the overheating issue.
> with no apparent problems as yet except for overheating of the 9100 onboard since the last xorg driver update

Can you be more specific? Are you saying that 304.125-0ubuntu0.0.2 overheats, but 304.125-0ubuntu0.0.1 does not?

---

### Post by garyt53 on 2015-09-14
Hi Tem -

The overheating issue is not due to dust and if you believe overheating has nothing to do with the driver than I just made a false diagnosis based on the coincidence of the timing of the 304 driver update from xorg-edgers.  Happens when we're more ignorant of a science than not....like me. ha  So maybe the integral nvidia 9100 is going. 
**Q: do integral graphics drivers usually take the motherboard with them when they go? ** Maybe I should just be using the Quadro all the time now huh.

**So what I will do is simply (and elegantly I might add) check the 340 open source updates driver in Additional Drivers and just reboot after purging the xorg-edgers PPA.  Right?**  How cool is that!

Will wait for your OK on this incredibly convenient means of changing graphics drivers, embarrassed that I am not participating in the Launchpad PPA effort, but only because I am still too much of a newb.  Fraid I would be more trouble than my data would be worth. ha

Thank you....all of you, for your consideration of my dilemma, and it's great news that the UbuntuGraphicsDriverPPA and will be incorporated into the Synaptic Additional Drivers utility.

gt

After getting an OK to simply check nvidia open source updates in additional drivers and reboot and go with a little earlier but stable driver, we can consider this thread closed.

.....except that I do recall there being a lot of issues with installing the AMD64 version of nvidia340 on ubuntu14.04 late last year

---

### Post by Yellow Pasque on 2015-09-14
> **garyt53 said:**
> if you believe overheating has nothing to do with the driver
The video driver is responsible for power management on the GPU, but the changes to 304.125-0ubuntu0.0.2 as compared to the previous version (304.125-0ubuntu0.0.1) were very minor. They came down to adding support for newer kernels. It should not have affected your system since you're still using the original Trusty 3.13 kernel series.

> So maybe the integral nvidia 9100 is going. 
It's possible. That generation of nvidia GPU's was known to have manufacturing material problems, which were aggravated by high temperatures. The mobile/integrated GPU's were the worst offenders since they were designed to operate at the higher temperatures that laptops and integrated GPU's endure.

> Q: do integral graphics drivers usually take the motherboard with them when they go?
It's possible. I don't know about "usually" or have any hard statistics.

> we can consider this thread closed.
Mark the thread as solved if you're satisfied with the result.

---

### Post by garyt53 on 2015-09-14
OK Folks -

I tried the simple Additional Drivers method, both for open source nvidia340.76 and for the propitiatory updates version and what happens is the progress bar jumps a quarter inch and thennothing else happens.  Used the sys monitor to detect any activity and none.

So, what am I missing here?

gt

---

### Post by Yellow Pasque on 2015-09-14
The bar tells us nothing. Try this in terminal:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-340
```

---

### Post by garyt53 on 2015-09-14
Shall I purge the xorg-edgers PPA first?  after?  after rebooting?  at all?

I understand purging PPAs removes everything sent to me from xorg-edgers.....all the updates and, it is rumoured, unrelated stuff that has been provided with updates.  Let me reiterate that I have had no driver related problems from xorg that I know of, but in my research on this I have been repeatedly exposed to rumor.  Probably just the nature of the WWW ya know.

gt

---

### Post by Yellow Pasque on 2015-09-15
> Shall I purge the xorg-edgers PPA first?
Yes, do that first. I didn't even know you had it installed..

---

### Post by garyt53 on 2015-09-15
OK Tem, will do and will close this thread as solved again, coming back, probably from win7 (ha), if the new PPA fails.....somehow.

Thanks for the help and don't be staying up all night.  Not consecutively anyway. ha

gt

MS wants to bill us monthly for the win10 trap.

Failed 340 install.  Everything went well until I clicked on a launcher icon and it began cycling horizontal hold......rebooted to same thing with blackscreen......rebooted with same thing with whitescreen.  Hey, at least I didn't get a bluescreen. haha

Any ideas?  No error messages on purge of xorg-edgers or install of nvidia304.  Unmet dependencies?  Overmet dependencies?  Won't sleep well because I made changes since I backed up.

I promise I won't get mad if you don't get scared. haha

gt

---

### Post by Bucky Ball on 2015-09-15
Try nomodeset. Boot, highlight the kernel you want and hit 'e'. End of the kernel line, make it look like:

```
quiet splash nomodeset
```

Follow instructions at the bottom of that screen to continue with boot. Any different? Might get you back to a desktop.

---

### Post by Yellow Pasque on 2015-09-15
Sudden overheating and striped video? It really sounds like your GPU failed (probably because of the aforementioned defective material issue).

---

### Post by Bucky Ball on 2015-09-15
> **Temüjin said:**
> Sudden overheating and striped video? It really sounds like your GPU failed (probably because of the aforementioned defective material issue).

When you put it together like that, distinct possibility.

---

### Post by garyt53 on 2015-09-15
Well, I didn't get mad.....I got sick. ha  No voice, which is kinda cool.

reboots failed with and without the orig syntax of .....quiet splash [B][I]$vt_handof\
f[/I][/B] [as it appeared in grub with the \ being immovable and at the end of the line]

in other words, I tried inserting "nomodeset" after quiet splash and before @vt_... and without the $vt and both failed as per notes on attachment

please examine all the printing on the attachment as I found indication that modeset=0 may be required but I haven't tried that yet as it requires all instances of nomodeset be adjusted to modeset=0 (check opensuse.org link for credibility)

gt[ATTACH=CONFIG]264433[/ATTACH]

Hi Folks -

Just to admit my mistake and save you a coupla min, the opensuse post regarding modeset=0 replacing nomodeset is over 2yrs old.....which is on the borderline of indicating current credibility.  Just misread the date the first time I was there.

And tried all iterations of the nomodeset and modeset=0, that is with and without the extraneous text following "quiet splash" ( $vt_handoff) and all failed to 1) fast-cycling horiz hold and 2) shortly after, blackscreen.

There were no errors while purging/installing.  I watched closely.  Most of the time I get to the desktop but can't even Cntrl+t the terminal without driver failure.  And can't get in to the older kernel either.

gt

Should I restore the latest BU, wait to have my hand held thru this as is, or just restore and forget about it......or walk thru this, putting off the new PPA until they are better prepared there:
[https://elementaryforums.com/index.php?threads/howto-install-latest-nvidia-driver-on-linux-without-getting-black-screen.7/](https://elementaryforums.com/index.php?threads/howto-install-latest-nvidia-driver-on-linux-without-getting-black-screen.7/)

You know, though no errors made themselves evident (I watched closely), it just kinda 'feels' like the xorg-edgers PPA purge didn't go well.  Rumor is a lotta stuff is sent with driver updates that often establishes unnecessary dependencies.

And ya know, if the purge was incomplete (used PPAManager's purge) then I'm just stuck with 304 huh.

Thanks.

gt

---

### Post by Bucky Ball on 2015-09-16
Issue this command:

```
sudo apt-get autoremove
```

Does it show it is going to remove anything related to the xorg edgers? Any dependencies or anything else no longer required? Hit 'y' for yes.

---

### Post by garyt53 on 2015-09-16
Managed to get in thru RecoveryModeResume and yup.....libcuda-304.  Let it go but still fails.  Can't even get in thru kernel RM now.

Hey, forgot my login for Cntrl+Alt+F1 login.  Got pwd OK but forgot login.  How do I get it?  If I can get in again I can do an apt-get update & upgrade.  Could that fix the driver?  Haven't done it since before reinstall.  

gt

managed to get in again, after having entered the correct login username and having that curiously fail (it was typed correctly - I don't like anomalous behavior cause it almost always means corrupt code) and ran update/upgrade several times till it washed out clear.  A lotta stuff happened, almost 2hrs scrolling over a solid ISP.  But.....well, shall I say it again?  It's whitescreen though these times.

Any graphics driver savvy ideas?  Still fails when going in thru kernel recovery mode and resume, resume supposedly running noveau instead of nvidia.

Shall I restore and reboot between every operation, using the Cntrl+Alt+F1 shell terminal to issue subsequent operation commands?  Get new driver from xorg?.....from Nvidia and do a manual install as/per [https://elementaryforums.com/index.p...lack-screen.7/](https://elementaryforums.com/index.p...lack-screen.7/) obtaining the latest available 340 driver (.93 I believe)?  Or do you have any more code sequences that will likely get the UbuntuPPA driver340 (the one I tried to install) working.  Perhaps I require the "open source" version as opposed to "updates".  But then the open source version is probably all that is available from the new UbuntuPPA.  Hell, I don't know.  And I'm talking to the whole open-source world out there and you don't?  Maybe I'm in the wrong sub-forum.  Perhaps gaming?  The only thin I know is I don't know.

gt

oh yeah, no errors encountered in the update/upgrade process

and ran autoremove again after failure

discovered both my cards are "Legacy" (dinosaurs) and what you said about the GEForce 9100 integral was quite right from 2 sources (for typ office use and not rendering or gaming)

will be using the Quadro full time, but still would rather the 340 driver, or is there a driver better suited to the framework of 14.04.1 ?

---

### Post by Bucky Ball on 2015-09-17
> **garyt53 said:**
> ... would rather the 340 driver, or is there a driver better suited to the framework of 14.04.1 ?

Perhaps not, which is why it's using a different one. Maybe that's the correct one for 14.04.1 on your machine. Does it use the other in 15.04 or will it be implemented in 15.10, 16.04 LTS?

If this is a low-end, old card, is there any diff between performance of open-source noveau driver and the third-party one? You possibly won't get a lot out of it either way.

---

### Post by Yellow Pasque on 2015-09-17
> **garyt53 said:**
> will be using the Quadro full time, but still would rather the 340 driver, or is there a driver better suited to the framework of 14.04.1 ?

It depends on which Quadro model you have.

---

### Post by garyt53 on 2015-09-17
my instruction has been ya go to nvidia and they have matched the driver to the card, not matching the OS to the driver....and this protocol has been consistent across the web

however, with all the issues with 14.04.1 and AMD64 [intentional? oh yeah, that's MS (ha)] perhaps with AMD64 we should be mating the OS to the driver - I have no idea but I would prefer to be using the driver indicated by nvidia for obvious reasons

then again, since my QuadroFX is not a high end card but still requiring the 340 driver, perhaps one of you have the overview knowledge to suggest *with confidence* that the open-source nouveau driver would be an improvement over the xorg 304 I have been using for a long time, that maybe the 14.04.1 framework is not compatible with the 304 driver

Q1) so are these annoying wasteful install issues I and many others with 14.04.1 and AMD64 due to the OS framework being incompatible with certian drivers?
Q2) would I get comparable or better performance say with OpenGL on open-source noveau than the 304 or even the 340.73 driver indicated by nvidia? 
Q3) and if so, would I install noveau from the new UbuntuPPA or just from synaptic....and perhaps I should purge nvidia* and reinstall 340.73, or even .93 (latest, if present) from synaptic after restoring from latest backup?  I suspect I should just try to use the driver nvidia indicates, but then I know little of this, except that I'm not going to go out and spend hundreds on new stuff that goes right to mfg reps and their unbelievable markups exploiting Mexican and Chinese slave labor in this Age of Plunder when what I have is working.  You do know the new stuff is intentionally designed now not to work out of warranty.  What happens when there's nothing left for central banksters to steal.  Sadly you may want to censor the last coupla lines even though you can't disagree.

Nvidia says 340, been using 304, want to use 340 unless you can confidently tell me to use another and confidently indicate which (331 has been indicated to work on 14.04).

gt

from mid last post:
"that maybe the 14.04.1 framework is not compatible with the 304 driver"
should be:
or that maybe the 14.04.1 framework is not compatible with the 340 driver

humbled, I thank you
gt

and to more clearly and completely answer your question regarding later versions of the OS and driver compatibility, the nvidia 340.73 is available in my apparently dysfunctional synaptic Additional Drivers, both proprietary updates and open source

remember when I tried to use it and SystemMonitor indicated no activity for over 15min when trying to install the updates version?  curious, huh.

---

### Post by Yellow Pasque on 2015-09-17
> **garyt53 said:**
> 
"that maybe the 14.04.1 framework is not compatible with the 304 driver"
or that maybe the 14.04.1 framework is not compatible with the 340 driver


Both drivers support the kernel and Xserver found in 14.04.1

> remember when I tried to use it and SystemMonitor indicated no activity for over 15min when trying to install the updates version?

It would be better if you used the terminal when trying to install a driver. It might give a more specific error. For example:
```
sudo apt-get install nvidia-340
```

> then again, since my QuadroFX is not a high end card but still requiring the 340 driver, perhaps one of you have the overview knowledge to suggest with confidence that the open-source nouveau driver would be an improvement over the xorg 304 I have been using for a long time

Once again.... What model of QuadroFX specifically? There are a bunch of them spanning several generations: [https://en.wikipedia.org/wiki/Nvidia_Quadro#PCI_Express](https://en.wikipedia.org/wiki/Nvidia_Quadro#PCI_Express)
Use lspci if you're not sure:
```
lspci
```

---

### Post by Yellow Pasque on 2015-09-17
> **garyt53 said:**
> Sadly you may want to censor the last coupla lines even though you can't disagree

I don't think they warrant deleting/censorship, but try to refrain from such rants and stick to the topic. You stand a better chance of people wanting to help you if you can keep the signal/noise ratio up...

---

### Post by garyt53 on 2015-09-18
"signal to noise"....that's cool

I just want to install 340, preferably from the new PPA if they are prepared.  

I will reiterate that I'm on 14.04.1 AMD64 and my primary card is integral GEForce9100 but my primary will soon be QuadroFX380, only a hundred dollar card but amazing bang for the buck.  Nvidia documents 340 as the appropriate card for both but have been using 304 from xorgPPA for over a year.....mostly on the 9100 onboard but has worked for both cards.

Look, I know you juggle much more difficult and challenging issues than mine, but I am feeling that you all just want me to go away, so I will reiterate once more that I want to install nvidia 340 on my 14.04.1 amd64 system.  It's good to know both 304 and 340 are compatible with my OS.  So my first attempt with your guidance was with the Additional Drivers utility in synaptic with which I waited over 15min with a stuck progress bar and no activity registering in system monitor.  I then proceeded to purge all the stuff xorg-edgers has sent using the YPPA utility and without reboot installed the new UbuntuPPA and again without reboot installed the driver 340 as per your code.  Throughout this lengthly process I watch the scroll closely and no errors evident.  However I went back in thru the Cntrl+Alt+F1 prompt to update/upgrade/dist-upgrade and autoremove with very heavy activity on update&upgrade, very light activity on dist-upgrade (nope, not a kernel, only a file I don't recall) and autoremove taking out libcuda1-304. 

That's it!  Can ya help me folks or should I go to gamers.  Gamers hate newbs don't they? haha  Oops, startin to rant. ha

gt

---

### Post by Bucky Ball on 2015-09-18
> **garyt53 said:**
> 
I will reiterate that I'm on 14.04.1 AMD64 and my primary card is integral GEForce9100 but my primary will soon be QuadroFX380 ...

Do you actually have the card in the machine yet? If not the help we can give here is limited. You have been asked several times for the exact card as there are several versions of it and they are, apparently, different in one way or another.

When it is in there, run:

```
sudo lshw -C video
```

... and post the results here. 

No, don't duplicate post in Gamers or anywhere else. And no, we don't want you to go away, but for us to help you, you need to help us by providing whatever information you can when asked. As there is little you can provide us if you don't actually have the card, there is little we can do because we have no idea if you are going to have the same problems with that as you are having with the one you are using now. 

I suggest getting the card, putting it in, going through the advice you've gotten here so far, and posting if you hit a brickwall. Anything else is theoretical. You may plop it in and it works perfectly with the 340. If it is in Additional Drivers, all you need to do is click and enable the 340. Who knows, it may want that one by default and it will be the only one there. As I said, theoretical from here without a card and at least the output of the command above. :)

---

### Post by garyt53 on 2015-09-18
OK Folks -

Let me be as clear an concise as I can for you, with your understanding that I can't tell my senior moments from my medicated moments anymore (ha).....

Forget everything previous in thread except the results of my 2 attempts to install 340 - failures
Am simply running 14.04.1 amd 64 with an nvidia GEForce 9100 integral card that has been working on xorg-edgers 304 updated without incident for 2yrs.
And I wish to change drivers to new UbuntuPPA 340 propitiatory updates.
I tried the first time checking 340PU in Additional Drivers and it just sat there with nothing happening in system monitor.
I then tried, with your guidance, to purge xorgPPA, install newUbuntuPPA, install 340 thru terminal and watching closely to all scrolling there were no errors.
Have even got in thru the shell and updated/upgraded with much activity and no errors until everything was clear and still driver 340 fails.
All the time I have continued my investigations on the web finding much conflicting info and issues with 64bit 14.04.
You got the ball. 

gt

---

### Post by Bucky Ball on 2015-09-18
Ok, great. It's in there, integrated. Now could you run 

```
sudo lshw -C video
```

... and post the result here. Thanks.

---

### Post by garyt53 on 2015-09-18
got into the xpVM so I could scan and here are the results for lshw, attached

the "-C" in the command you listed, I applied -c

---

### Post by Yellow Pasque on 2015-09-18
> install 340 thru terminal and watching closely to all scrolling there were no errors.

I think the next step would be to look at the Xorg log.

You install the nvidia-340 driver and boot with it. If it fails, reboot into the last working configuration and look at the /var/log/Xorg.0.log.old (and copy/paste contents here).

---

### Post by garyt53 on 2015-09-18
so how do I get into the last known config when I can't even get in thru the recovery kernels or the older kernel 62

and you want me to reinstall 304 thru the new Ubuntu ppa first?  if I can get in?  Or will I have to restore from backup first?  yikes

gt

have tried every possible iteration of editing the boot sequence with nomodeset (post 21) and every recovery option for both kernels and always fails

I believe your suggestion to boot into "last configuration that worked" is a MSwindows option.  You guys as overloaded as my doctor? ha

The only thing left I know about is using the liveCD to access the xorg log file.  I have windows utilities installed that are supposed to access ext3 but I am running ext4 on Ubuntu only running ext3 on some external HDD.

Tell me how to get in and I can retrieve the log.  Look, I will restore a backup before I will write down an entire logfile, and I.....no, my laptop is dualboot xp & 14.04.  Whew.

What should I do to access the logfile.  I just informed you of the only choices I have that I know about.

whew, goterdone - with ext3Explore (win utility) and my 14.04 laptop, that I now need to make into 14.04.1. ha
couldn't upload file, was invalid, even after dropping the .old extention

contents of xorg.0.log.old -

```

[    64.450] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    64.450] X Protocol Version 11, Revision 0
[    64.450] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    64.450] Current Operating System: Linux gary-p6313w 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:29:36 UTC 2015 x86_64
[    64.450] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-62-generic root=UUID=6ec8ff03-b545-4ce4-91e6-931ecd6dcfe7 ro recovery nomodeset resume=UUID=77227c76-4f93-4085-900a-ec6173e04307
[    64.450] Build Date: 12 February 2015  02:49:29PM
[    64.450] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    64.450] Current version of pixman: 0.30.2
[    64.450] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    64.450] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    64.450] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 18 12:03:33 2015
[    64.450] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    64.451] (==) No Layout section.  Using the first Screen section.
[    64.451] (==) No screen section available. Using defaults.
[    64.451] (**) |-->Screen "Default Screen Section" (0)
[    64.451] (**) |   |-->Monitor "<default monitor>"
[    64.451] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    64.451] (==) Automatically adding devices
[    64.451] (==) Automatically enabling devices
[    64.451] (==) Automatically adding GPU devices
[    64.451] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    64.451] 	Entry deleted from font path.
[    64.451] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    64.451] 	Entry deleted from font path.
[    64.451] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    64.451] 	Entry deleted from font path.
[    64.451] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    64.451] 	Entry deleted from font path.
[    64.451] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    64.451] 	Entry deleted from font path.
[    64.451] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    64.451] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    64.451] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    64.451] (II) Loader magic: 0x7f66a300fd40
[    64.451] (II) Module ABI versions:
[    64.451] 	X.Org ANSI C Emulation: 0.4
[    64.451] 	X.Org Video Driver: 15.0
[    64.451] 	X.Org XInput driver : 20.0
[    64.451] 	X.Org Server Extension : 8.0
[    64.453] (--) PCI:*(0:2:0:0) 10de:0847:103c:2a9e rev 162, Mem @ 0xfd000000/16777216, 0xe8000000/134217728, 0xe6000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[    64.453] Initializing built-in extension Generic Event Extension
[    64.453] Initializing built-in extension SHAPE
[    64.453] Initializing built-in extension MIT-SHM
[    64.453] Initializing built-in extension XInputExtension
[    64.453] Initializing built-in extension XTEST
[    64.453] Initializing built-in extension BIG-REQUESTS
[    64.453] Initializing built-in extension SYNC
[    64.453] Initializing built-in extension XKEYBOARD
[    64.453] Initializing built-in extension XC-MISC
[    64.453] Initializing built-in extension SECURITY
[    64.453] Initializing built-in extension XINERAMA
[    64.453] Initializing built-in extension XFIXES
[    64.453] Initializing built-in extension RENDER
[    64.453] Initializing built-in extension RANDR
[    64.453] Initializing built-in extension COMPOSITE
[    64.453] Initializing built-in extension DAMAGE
[    64.453] Initializing built-in extension MIT-SCREEN-SAVER
[    64.453] Initializing built-in extension DOUBLE-BUFFER
[    64.453] Initializing built-in extension RECORD
[    64.453] Initializing built-in extension DPMS
[    64.453] Initializing built-in extension Present
[    64.453] Initializing built-in extension DRI3
[    64.453] Initializing built-in extension X-Resource
[    64.453] Initializing built-in extension XVideo
[    64.453] Initializing built-in extension XVideo-MotionCompensation
[    64.453] Initializing built-in extension SELinux
[    64.453] Initializing built-in extension XFree86-VidModeExtension
[    64.453] Initializing built-in extension XFree86-DGA
[    64.453] Initializing built-in extension XFree86-DRI
[    64.453] Initializing built-in extension DRI2
[    64.453] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    64.453] (II) "glx" will be loaded by default.
[    64.453] (WW) "xmir" is not to be loaded by default. Skipping.
[    64.453] (II) LoadModule: "glx"
[    64.453] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    64.468] (II) Module glx: vendor="NVIDIA Corporation"
[    64.468] 	compiled for 4.0.2, module version = 1.0.0
[    64.468] 	Module class: X.Org Server Extension
[    64.468] (II) NVIDIA GLX Module  340.93  Wed Aug 19 16:23:51 PDT 2015
[    64.468] Loading extension GLX
[    64.468] (==) Matched nvidia as autoconfigured driver 0
[    64.468] (==) Matched nouveau as autoconfigured driver 1
[    64.469] (==) Matched modesetting as autoconfigured driver 2
[    64.469] (==) Matched fbdev as autoconfigured driver 3
[    64.469] (==) Matched vesa as autoconfigured driver 4
[    64.469] (==) Assigned the driver to the xf86ConfigLayout
[    64.469] (II) LoadModule: "nvidia"
[    64.469] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    64.469] (II) Module nvidia: vendor="NVIDIA Corporation"
[    64.469] 	compiled for 4.0.2, module version = 1.0.0
[    64.469] 	Module class: X.Org Video Driver
[    64.469] (II) LoadModule: "nouveau"
[    64.469] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    64.470] (II) Module nouveau: vendor="X.Org Foundation"
[    64.470] 	compiled for 1.15.0, module version = 1.0.10
[    64.470] 	Module class: X.Org Video Driver
[    64.470] 	ABI class: X.Org Video Driver, version 15.0
[    64.470] (II) LoadModule: "modesetting"
[    64.470] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    64.470] (II) Module modesetting: vendor="X.Org Foundation"
[    64.470] 	compiled for 1.15.0, module version = 0.8.1
[    64.470] 	Module class: X.Org Video Driver
[    64.470] 	ABI class: X.Org Video Driver, version 15.0
[    64.470] (II) LoadModule: "fbdev"
[    64.470] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    64.470] (II) Module fbdev: vendor="X.Org Foundation"
[    64.470] 	compiled for 1.15.0, module version = 0.4.4
[    64.470] 	Module class: X.Org Video Driver
[    64.470] 	ABI class: X.Org Video Driver, version 15.0
[    64.470] (II) LoadModule: "vesa"
[    64.470] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    64.470] (II) Module vesa: vendor="X.Org Foundation"
[    64.470] 	compiled for 1.15.0, module version = 2.3.3
[    64.470] 	Module class: X.Org Video Driver
[    64.470] 	ABI class: X.Org Video Driver, version 15.0
[    64.470] (II) NVIDIA dlloader X Driver  340.93  Wed Aug 19 16:01:53 PDT 2015
[    64.470] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    64.470] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    64.470] (II) NOUVEAU driver for NVIDIA chipset families :
[    64.470] 	RIVA TNT        (NV04)
[    64.470] 	RIVA TNT2       (NV05)
[    64.470] 	GeForce 256     (NV10)
[    64.470] 	GeForce 2       (NV11, NV15)
[    64.470] 	GeForce 4MX     (NV17, NV18)
[    64.470] 	GeForce 3       (NV20)
[    64.470] 	GeForce 4Ti     (NV25, NV28)
[    64.470] 	GeForce FX      (NV3x)
[    64.470] 	GeForce 6       (NV4x)
[    64.470] 	GeForce 7       (G7x)
[    64.471] 	GeForce 8       (G8x)
[    64.471] 	GeForce GTX 200 (NVA0)
[    64.471] 	GeForce GTX 400 (NVC0)
[    64.471] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    64.471] (II) FBDEV: driver for framebuffer: fbdev
[    64.471] (II) VESA: driver for VESA chipsets: vesa
[    64.471] (++) using VT number 7

[    64.472] (II) Loading sub module "fb"
[    64.472] (II) LoadModule: "fb"
[    64.472] (II) Loading /usr/lib/xorg/modules/libfb.so
[    64.472] (II) Module fb: vendor="X.Org Foundation"
[    64.472] 	compiled for 1.15.1, module version = 1.0.0
[    64.472] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    64.472] (WW) Unresolved symbol: fbGetGCPrivateKey
[    64.472] (II) Loading sub module "wfb"
[    64.472] (II) LoadModule: "wfb"
[    64.472] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    64.472] (II) Module wfb: vendor="X.Org Foundation"
[    64.472] 	compiled for 1.15.1, module version = 1.0.0
[    64.472] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    64.472] (II) Loading sub module "ramdac"
[    64.473] (II) LoadModule: "ramdac"
[    64.473] (II) Module "ramdac" already built-in
[    64.475] (EE) NVIDIA: Failed to initialize the NVIDIA kernel module. Please see the
[    64.475] (EE) NVIDIA:     system's kernel log for additional error messages and
[    64.475] (EE) NVIDIA:     consult the NVIDIA README for details.
[    64.475] (EE) [drm] KMS not enabled
[    64.475] (EE) open /dev/dri/card0: No such file or directory
[    64.475] (WW) Falling back to old probe method for modesetting
[    64.475] (EE) open /dev/dri/card0: No such file or directory
[    64.475] (II) Loading sub module "fbdevhw"
[    64.475] (II) LoadModule: "fbdevhw"
[    64.476] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    64.476] (II) Module fbdevhw: vendor="X.Org Foundation"
[    64.476] 	compiled for 1.15.1, module version = 0.0.2
[    64.476] 	ABI class: X.Org Video Driver, version 15.0
[    64.476] (EE) open /dev/fb0: No such file or directory
[    64.476] (WW) Falling back to old probe method for fbdev
[    64.476] (II) Loading sub module "fbdevhw"
[    64.476] (II) LoadModule: "fbdevhw"
[    64.476] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    64.476] (II) Module fbdevhw: vendor="X.Org Foundation"
[    64.476] 	compiled for 1.15.1, module version = 0.0.2
[    64.476] 	ABI class: X.Org Video Driver, version 15.0
[    64.476] (EE) open /dev/fb0: No such file or directory
[    64.476] (EE) Screen 0 deleted because of no matching config section.
[    64.476] (II) UnloadModule: "modesetting"
[    64.476] (EE) Screen 0 deleted because of no matching config section.
[    64.476] (II) UnloadModule: "fbdev"
[    64.476] (II) UnloadSubModule: "fbdevhw"
[    64.476] (II) Loading sub module "vbe"
[    64.476] (II) LoadModule: "vbe"
[    64.476] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    64.476] (II) Module vbe: vendor="X.Org Foundation"
[    64.476] 	compiled for 1.15.1, module version = 1.1.0
[    64.476] 	ABI class: X.Org Video Driver, version 15.0
[    64.476] (II) Loading sub module "int10"
[    64.476] (II) LoadModule: "int10"
[    64.476] (II) Loading /usr/lib/xorg/modules/libint10.so
[    64.476] (II) Module int10: vendor="X.Org Foundation"
[    64.476] 	compiled for 1.15.1, module version = 1.0.0
[    64.476] 	ABI class: X.Org Video Driver, version 15.0
[    64.477] (II) VESA(0): initializing int10
[    64.478] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    64.518] (II) VESA(0): VESA BIOS detected
[    64.518] (II) VESA(0): VESA VBE Version 3.0
[    64.518] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    64.518] (II) VESA(0): VESA VBE OEM: NVIDIA
[    64.518] (II) VESA(0): VESA VBE OEM Software Rev: 98.119
[    64.518] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    64.518] (II) VESA(0): VESA VBE OEM Product: MCP77 Board - mcp78ovo
[    64.518] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    64.592] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    64.592] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    64.592] (==) VESA(0): RGB weight 888
[    64.592] (==) VESA(0): Default visual is TrueColor
[    64.592] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    64.592] (II) Loading sub module "ddc"
[    64.592] (II) LoadModule: "ddc"
[    64.592] (II) Module "ddc" already built-in
[    64.594] (II) VESA(0): VESA VBE DDC supported
[    64.594] (II) VESA(0): VESA VBE DDC Level none
[    64.594] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    64.767] (II) VESA(0): VESA VBE DDC read failed
[    64.767] (II) VESA(0): Searching for matching VESA mode(s):
[    64.768] Mode: 100 (640x400)
[    64.768] 	ModeAttributes: 0x3bf
[    64.768] 	WinAAttributes: 0x7
[    64.768] 	WinBAttributes: 0x0
[    64.769] 	WinGranularity: 64
[    64.769] 	WinSize: 64
[    64.769] 	WinASegment: 0xa000
[    64.769] 	WinBSegment: 0x0
[    64.769] 	WinFuncPtr: 0xc000964c
[    64.769] 	BytesPerScanline: 640
[    64.769] 	XResolution: 640
[    64.769] 	YResolution: 400
[    64.769] 	XCharSize: 8
[    64.769] 	YCharSize: 16
[    64.769] 	NumberOfPlanes: 1
[    64.769] 	BitsPerPixel: 8
[    64.769] 	NumberOfBanks: 1
[    64.769] 	MemoryModel: 4
[    64.769] 	BankSize: 0
[    64.769] 	NumberOfImages: 14
[    64.769] 	RedMaskSize: 0
[    64.769] 	RedFieldPosition: 0
[    64.769] 	GreenMaskSize: 0
[    64.769] 	GreenFieldPosition: 0
[    64.769] 	BlueMaskSize: 0
[    64.769] 	BlueFieldPosition: 0
[    64.769] 	RsvdMaskSize: 0
[    64.769] 	RsvdFieldPosition: 0
[    64.769] 	DirectColorModeInfo: 0
[    64.769] 	PhysBasePtr: 0xe7000000
[    64.769] 	LinBytesPerScanLine: 640
[    64.769] 	BnkNumberOfImagePages: 14
[    64.769] 	LinNumberOfImagePages: 14
[    64.769] 	LinRedMaskSize: 0
[    64.769] 	LinRedFieldPosition: 0
[    64.769] 	LinGreenMaskSize: 0
[    64.769] 	LinGreenFieldPosition: 0
[    64.769] 	LinBlueMaskSize: 0
[    64.769] 	LinBlueFieldPosition: 0
[    64.769] 	LinRsvdMaskSize: 0
[    64.769] 	LinRsvdFieldPosition: 0
[    64.769] 	MaxPixelClock: 229500000
[    64.770] Mode: 101 (640x480)
[    64.770] 	ModeAttributes: 0x3bf
[    64.770] 	WinAAttributes: 0x7
[    64.770] 	WinBAttributes: 0x0
[    64.770] 	WinGranularity: 64
[    64.770] 	WinSize: 64
[    64.770] 	WinASegment: 0xa000
[    64.770] 	WinBSegment: 0x0
[    64.770] 	WinFuncPtr: 0xc000964c
[    64.770] 	BytesPerScanline: 640
[    64.770] 	XResolution: 640
[    64.770] 	YResolution: 480
[    64.770] 	XCharSize: 8
[    64.770] 	YCharSize: 16
[    64.770] 	NumberOfPlanes: 1
[    64.770] 	BitsPerPixel: 8
[    64.770] 	NumberOfBanks: 1
[    64.770] 	MemoryModel: 4
[    64.770] 	BankSize: 0
[    64.770] 	NumberOfImages: 10
[    64.770] 	RedMaskSize: 0
[    64.770] 	RedFieldPosition: 0
[    64.770] 	GreenMaskSize: 0
[    64.770] 	GreenFieldPosition: 0
[    64.770] 	BlueMaskSize: 0
[    64.770] 	BlueFieldPosition: 0
[    64.770] 	RsvdMaskSize: 0
[    64.770] 	RsvdFieldPosition: 0
[    64.770] 	DirectColorModeInfo: 0
[    64.770] 	PhysBasePtr: 0xe7000000
[    64.770] 	LinBytesPerScanLine: 640
[    64.770] 	BnkNumberOfImagePages: 10
[    64.770] 	LinNumberOfImagePages: 10
[    64.770] 	LinRedMaskSize: 0
[    64.770] 	LinRedFieldPosition: 0
[    64.770] 	LinGreenMaskSize: 0
[    64.770] 	LinGreenFieldPosition: 0
[    64.770] 	LinBlueMaskSize: 0
[    64.770] 	LinBlueFieldPosition: 0
[    64.770] 	LinRsvdMaskSize: 0
[    64.770] 	LinRsvdFieldPosition: 0
[    64.770] 	MaxPixelClock: 229500000
[    64.771] Mode: 102 (800x600)
[    64.771] 	ModeAttributes: 0x33f
[    64.771] 	WinAAttributes: 0x7
[    64.771] 	WinBAttributes: 0x0
[    64.771] 	WinGranularity: 64
[    64.771] 	WinSize: 64
[    64.771] 	WinASegment: 0xa000
[    64.771] 	WinBSegment: 0x0
[    64.771] 	WinFuncPtr: 0xc000964c
[    64.771] 	BytesPerScanline: 100
[    64.771] 	XResolution: 800
[    64.771] 	YResolution: 600
[    64.771] 	XCharSize: 8
[    64.771] 	YCharSize: 16
[    64.771] 	NumberOfPlanes: 4
[    64.771] 	BitsPerPixel: 4
[    64.771] 	NumberOfBanks: 1
[    64.771] 	MemoryModel: 3
[    64.771] 	BankSize: 0
[    64.771] 	NumberOfImages: 2
[    64.771] 	RedMaskSize: 0
[    64.771] 	RedFieldPosition: 0
[    64.771] 	GreenMaskSize: 0
[    64.771] 	GreenFieldPosition: 0
[    64.771] 	BlueMaskSize: 0
[    64.771] 	BlueFieldPosition: 0
[    64.771] 	RsvdMaskSize: 0
[    64.771] 	RsvdFieldPosition: 0
[    64.771] 	DirectColorModeInfo: 0
[    64.771] 	PhysBasePtr: 0x0
[    64.771] 	LinBytesPerScanLine: 100
[    64.771] 	BnkNumberOfImagePages: 2
[    64.771] 	LinNumberOfImagePages: 2
[    64.771] 	LinRedMaskSize: 0
[    64.771] 	LinRedFieldPosition: 0
[    64.771] 	LinGreenMaskSize: 0
[    64.771] 	LinGreenFieldPosition: 0
[    64.771] 	LinBlueMaskSize: 0
[    64.771] 	LinBlueFieldPosition: 0
[    64.771] 	LinRsvdMaskSize: 0
[    64.771] 	LinRsvdFieldPosition: 0
[    64.771] 	MaxPixelClock: 108500000
[    64.772] Mode: 103 (800x600)
[    64.772] 	ModeAttributes: 0x3bf
[    64.772] 	WinAAttributes: 0x7
[    64.772] 	WinBAttributes: 0x0
[    64.772] 	WinGranularity: 64
[    64.772] 	WinSize: 64
[    64.772] 	WinASegment: 0xa000
[    64.772] 	WinBSegment: 0x0
[    64.772] 	WinFuncPtr: 0xc000964c
[    64.772] 	BytesPerScanline: 800
[    64.772] 	XResolution: 800
[    64.772] 	YResolution: 600
[    64.772] 	XCharSize: 8
[    64.772] 	YCharSize: 16
[    64.772] 	NumberOfPlanes: 1
[    64.772] 	BitsPerPixel: 8
[    64.772] 	NumberOfBanks: 1
[    64.772] 	MemoryModel: 4
[    64.772] 	BankSize: 0
[    64.772] 	NumberOfImages: 6
[    64.772] 	RedMaskSize: 0
[    64.772] 	RedFieldPosition: 0
[    64.772] 	GreenMaskSize: 0
[    64.772] 	GreenFieldPosition: 0
[    64.772] 	BlueMaskSize: 0
[    64.772] 	BlueFieldPosition: 0
[    64.772] 	RsvdMaskSize: 0
[    64.772] 	RsvdFieldPosition: 0
[    64.772] 	DirectColorModeInfo: 0
[    64.772] 	PhysBasePtr: 0xe7000000
[    64.772] 	LinBytesPerScanLine: 800
[    64.772] 	BnkNumberOfImagePages: 6
[    64.772] 	LinNumberOfImagePages: 6
[    64.772] 	LinRedMaskSize: 0
[    64.772] 	LinRedFieldPosition: 0
[    64.772] 	LinGreenMaskSize: 0
[    64.772] 	LinGreenFieldPosition: 0
[    64.772] 	LinBlueMaskSize: 0
[    64.772] 	LinBlueFieldPosition: 0
[    64.772] 	LinRsvdMaskSize: 0
[    64.772] 	LinRsvdFieldPosition: 0
[    64.772] 	MaxPixelClock: 229500000
[    64.773] Mode: 104 (1024x768)
[    64.773] 	ModeAttributes: 0x33f
[    64.773] 	WinAAttributes: 0x7
[    64.773] 	WinBAttributes: 0x0
[    64.773] 	WinGranularity: 64
[    64.773] 	WinSize: 64
[    64.773] 	WinASegment: 0xa000
[    64.773] 	WinBSegment: 0x0
[    64.773] 	WinFuncPtr: 0xc000964c
[    64.773] 	BytesPerScanline: 128
[    64.773] 	XResolution: 1024
[    64.773] 	YResolution: 768
[    64.773] 	XCharSize: 8
[    64.773] 	YCharSize: 16
[    64.773] 	NumberOfPlanes: 4
[    64.773] 	BitsPerPixel: 4
[    64.773] 	NumberOfBanks: 1
[    64.773] 	MemoryModel: 3
[    64.773] 	BankSize: 0
[    64.773] 	NumberOfImages: 1
[    64.773] 	RedMaskSize: 0
[    64.773] 	RedFieldPosition: 0
[    64.773] 	GreenMaskSize: 0
[    64.773] 	GreenFieldPosition: 0
[    64.773] 	BlueMaskSize: 0
[    64.773] 	BlueFieldPosition: 0
[    64.773] 	RsvdMaskSize: 0
[    64.774] 	RsvdFieldPosition: 0
[    64.774] 	DirectColorModeInfo: 0
[    64.774] 	PhysBasePtr: 0x0
[    64.774] 	LinBytesPerScanLine: 128
[    64.774] 	BnkNumberOfImagePages: 1
[    64.774] 	LinNumberOfImagePages: 1
[    64.774] 	LinRedMaskSize: 0
[    64.774] 	LinRedFieldPosition: 0
[    64.774] 	LinGreenMaskSize: 0
[    64.774] 	LinGreenFieldPosition: 0
[    64.774] 	LinBlueMaskSize: 0
[    64.774] 	LinBlueFieldPosition: 0
[    64.774] 	LinRsvdMaskSize: 0
[    64.774] 	LinRsvdFieldPosition: 0
[    64.774] 	MaxPixelClock: 108500000
[    64.775] Mode: 105 (1024x768)
[    64.775] 	ModeAttributes: 0x3bf
[    64.775] 	WinAAttributes: 0x7
[    64.775] 	WinBAttributes: 0x0
[    64.775] 	WinGranularity: 64
[    64.775] 	WinSize: 64
[    64.775] 	WinASegment: 0xa000
[    64.775] 	WinBSegment: 0x0
[    64.775] 	WinFuncPtr: 0xc000964c
[    64.775] 	BytesPerScanline: 1024
[    64.775] 	XResolution: 1024
[    64.775] 	YResolution: 768
[    64.775] 	XCharSize: 8
[    64.775] 	YCharSize: 16
[    64.775] 	NumberOfPlanes: 1
[    64.775] 	BitsPerPixel: 8
[    64.775] 	NumberOfBanks: 1
[    64.775] 	MemoryModel: 4
[    64.775] 	BankSize: 0
[    64.775] 	NumberOfImages: 3
[    64.775] 	RedMaskSize: 0
[    64.775] 	RedFieldPosition: 0
[    64.775] 	GreenMaskSize: 0
[    64.775] 	GreenFieldPosition: 0
[    64.775] 	BlueMaskSize: 0
[    64.775] 	BlueFieldPosition: 0
[    64.775] 	RsvdMaskSize: 0
[    64.775] 	RsvdFieldPosition: 0
[    64.775] 	DirectColorModeInfo: 0
[    64.775] 	PhysBasePtr: 0xe7000000
[    64.775] 	LinBytesPerScanLine: 1024
[    64.775] 	BnkNumberOfImagePages: 3
[    64.775] 	LinNumberOfImagePages: 3
[    64.775] 	LinRedMaskSize: 0
[    64.775] 	LinRedFieldPosition: 0
[    64.775] 	LinGreenMaskSize: 0
[    64.775] 	LinGreenFieldPosition: 0
[    64.775] 	LinBlueMaskSize: 0
[    64.775] 	LinBlueFieldPosition: 0
[    64.775] 	LinRsvdMaskSize: 0
[    64.775] 	LinRsvdFieldPosition: 0
[    64.775] 	MaxPixelClock: 229500000
[    64.776] Mode: 106 (1280x1024)
[    64.776] 	ModeAttributes: 0x33f
[    64.776] 	WinAAttributes: 0x7
[    64.776] 	WinBAttributes: 0x0
[    64.776] 	WinGranularity: 64
[    64.776] 	WinSize: 64
[    64.776] 	WinASegment: 0xa000
[    64.776] 	WinBSegment: 0x0
[    64.776] 	WinFuncPtr: 0xc000964c
[    64.776] 	BytesPerScanline: 160
[    64.776] 	XResolution: 1280
[    64.776] 	YResolution: 1024
[    64.776] 	XCharSize: 8
[    64.776] 	YCharSize: 16
[    64.776] 	NumberOfPlanes: 4
[    64.776] 	BitsPerPixel: 4
[    64.776] 	NumberOfBanks: 1
[    64.776] 	MemoryModel: 3
[    64.776] 	BankSize: 0
[    64.776] 	NumberOfImages: 1
[    64.776] 	RedMaskSize: 0
[    64.776] 	RedFieldPosition: 0
[    64.776] 	GreenMaskSize: 0
[    64.776] 	GreenFieldPosition: 0
[    64.776] 	BlueMaskSize: 0
[    64.776] 	BlueFieldPosition: 0
[    64.776] 	RsvdMaskSize: 0
[    64.776] 	RsvdFieldPosition: 0
[    64.776] 	DirectColorModeInfo: 0
[    64.776] 	PhysBasePtr: 0x0
[    64.776] 	LinBytesPerScanLine: 160
[    64.776] 	BnkNumberOfImagePages: 1
[    64.776] 	LinNumberOfImagePages: 1
[    64.776] 	LinRedMaskSize: 0
[    64.776] 	LinRedFieldPosition: 0
[    64.776] 	LinGreenMaskSize: 0
[    64.776] 	LinGreenFieldPosition: 0
[    64.776] 	LinBlueMaskSize: 0
[    64.776] 	LinBlueFieldPosition: 0
[    64.776] 	LinRsvdMaskSize: 0
[    64.776] 	LinRsvdFieldPosition: 0
[    64.776] 	MaxPixelClock: 108500000
[    64.777] Mode: 107 (1280x1024)
[    64.777] 	ModeAttributes: 0x3bf
[    64.777] 	WinAAttributes: 0x7
[    64.777] 	WinBAttributes: 0x0
[    64.777] 	WinGranularity: 64
[    64.777] 	WinSize: 64
[    64.777] 	WinASegment: 0xa000
[    64.777] 	WinBSegment: 0x0
[    64.777] 	WinFuncPtr: 0xc000964c
[    64.777] 	BytesPerScanline: 1280
[    64.777] 	XResolution: 1280
[    64.777] 	YResolution: 1024
[    64.777] 	XCharSize: 8
[    64.777] 	YCharSize: 16
[    64.777] 	NumberOfPlanes: 1
[    64.777] 	BitsPerPixel: 8
[    64.777] 	NumberOfBanks: 1
[    64.777] 	MemoryModel: 4
[    64.777] 	BankSize: 0
[    64.777] 	NumberOfImages: 1
[    64.777] 	RedMaskSize: 0
[    64.777] 	RedFieldPosition: 0
[    64.777] 	GreenMaskSize: 0
[    64.777] 	GreenFieldPosition: 0
[    64.777] 	BlueMaskSize: 0
[    64.777] 	BlueFieldPosition: 0
[    64.777] 	RsvdMaskSize: 0
[    64.777] 	RsvdFieldPosition: 0
[    64.777] 	DirectColorModeInfo: 0
[    64.777] 	PhysBasePtr: 0xe7000000
[    64.777] 	LinBytesPerScanLine: 1280
[    64.777] 	BnkNumberOfImagePages: 1
[    64.777] 	LinNumberOfImagePages: 1
[    64.777] 	LinRedMaskSize: 0
[    64.777] 	LinRedFieldPosition: 0
[    64.777] 	LinGreenMaskSize: 0
[    64.777] 	LinGreenFieldPosition: 0
[    64.777] 	LinBlueMaskSize: 0
[    64.777] 	LinBlueFieldPosition: 0
[    64.777] 	LinRsvdMaskSize: 0
[    64.777] 	LinRsvdFieldPosition: 0
[    64.777] 	MaxPixelClock: 229500000
[    64.778] Mode: 10e (320x200)
[    64.778] 	ModeAttributes: 0x3bf
[    64.778] 	WinAAttributes: 0x7
[    64.778] 	WinBAttributes: 0x0
[    64.778] 	WinGranularity: 64
[    64.778] 	WinSize: 64
[    64.778] 	WinASegment: 0xa000
[    64.778] 	WinBSegment: 0x0
[    64.778] 	WinFuncPtr: 0xc000964c
[    64.778] 	BytesPerScanline: 640
[    64.778] 	XResolution: 320
[    64.778] 	YResolution: 200
[    64.778] 	XCharSize: 8
[    64.778] 	YCharSize: 8
[    64.778] 	NumberOfPlanes: 1
[    64.778] 	BitsPerPixel: 16
[    64.778] 	NumberOfBanks: 1
[    64.778] 	MemoryModel: 6
[    64.778] 	BankSize: 0
[    64.778] 	NumberOfImages: 30
[    64.778] 	RedMaskSize: 5
[    64.778] 	RedFieldPosition: 11
[    64.778] 	GreenMaskSize: 6
[    64.778] 	GreenFieldPosition: 5
[    64.778] 	BlueMaskSize: 5
[    64.778] 	BlueFieldPosition: 0
[    64.778] 	RsvdMaskSize: 0
[    64.778] 	RsvdFieldPosition: 0
[    64.778] 	DirectColorModeInfo: 0
[    64.778] 	PhysBasePtr: 0xe7000000
[    64.778] 	LinBytesPerScanLine: 640
[    64.778] 	BnkNumberOfImagePages: 30
[    64.778] 	LinNumberOfImagePages: 30
[    64.778] 	LinRedMaskSize: 5
[    64.778] 	LinRedFieldPosition: 11
[    64.778] 	LinGreenMaskSize: 6
[    64.778] 	LinGreenFieldPosition: 5
[    64.778] 	LinBlueMaskSize: 5
[    64.778] 	LinBlueFieldPosition: 0
[    64.778] 	LinRsvdMaskSize: 0
[    64.779] 	LinRsvdFieldPosition: 0
[    64.779] 	MaxPixelClock: 229500000
[    64.779] *Mode: 10f (320x200)
[    64.779] 	ModeAttributes: 0x3bf
[    64.779] 	WinAAttributes: 0x7
[    64.779] 	WinBAttributes: 0x0
[    64.779] 	WinGranularity: 64
[    64.780] 	WinSize: 64
[    64.780] 	WinASegment: 0xa000
[    64.780] 	WinBSegment: 0x0
[    64.780] 	WinFuncPtr: 0xc000964c
[    64.780] 	BytesPerScanline: 1280
[    64.780] 	XResolution: 320
[    64.780] 	YResolution: 200
[    64.780] 	XCharSize: 8
[    64.780] 	YCharSize: 8
[    64.780] 	NumberOfPlanes: 1
[    64.780] 	BitsPerPixel: 32
[    64.780] 	NumberOfBanks: 1
[    64.780] 	MemoryModel: 6
[    64.780] 	BankSize: 0
[    64.780] 	NumberOfImages: 14
[    64.780] 	RedMaskSize: 8
[    64.780] 	RedFieldPosition: 16
[    64.780] 	GreenMaskSize: 8
[    64.780] 	GreenFieldPosition: 8
[    64.780] 	BlueMaskSize: 8
[    64.780] 	BlueFieldPosition: 0
[    64.780] 	RsvdMaskSize: 8
[    64.780] 	RsvdFieldPosition: 24
[    64.780] 	DirectColorModeInfo: 0
[    64.780] 	PhysBasePtr: 0xe7000000
[    64.780] 	LinBytesPerScanLine: 1280
[    64.780] 	BnkNumberOfImagePages: 14
[    64.780] 	LinNumberOfImagePages: 14
[    64.780] 	LinRedMaskSize: 8
[    64.780] 	LinRedFieldPosition: 16
[    64.780] 	LinGreenMaskSize: 8
[    64.780] 	LinGreenFieldPosition: 8
[    64.780] 	LinBlueMaskSize: 8
[    64.780] 	LinBlueFieldPosition: 0
[    64.780] 	LinRsvdMaskSize: 8
[    64.780] 	LinRsvdFieldPosition: 24
[    64.780] 	MaxPixelClock: 229500000
[    64.781] Mode: 111 (640x480)
[    64.781] 	ModeAttributes: 0x3bf
[    64.781] 	WinAAttributes: 0x7
[    64.781] 	WinBAttributes: 0x0
[    64.781] 	WinGranularity: 64
[    64.781] 	WinSize: 64
[    64.781] 	WinASegment: 0xa000
[    64.781] 	WinBSegment: 0x0
[    64.781] 	WinFuncPtr: 0xc000964c
[    64.781] 	BytesPerScanline: 1280
[    64.781] 	XResolution: 640
[    64.781] 	YResolution: 480
[    64.781] 	XCharSize: 8
[    64.781] 	YCharSize: 16
[    64.781] 	NumberOfPlanes: 1
[    64.781] 	BitsPerPixel: 16
[    64.781] 	NumberOfBanks: 1
[    64.781] 	MemoryModel: 6
[    64.781] 	BankSize: 0
[    64.781] 	NumberOfImages: 4
[    64.781] 	RedMaskSize: 5
[    64.781] 	RedFieldPosition: 11
[    64.781] 	GreenMaskSize: 6
[    64.781] 	GreenFieldPosition: 5
[    64.781] 	BlueMaskSize: 5
[    64.781] 	BlueFieldPosition: 0
[    64.781] 	RsvdMaskSize: 0
[    64.781] 	RsvdFieldPosition: 0
[    64.781] 	DirectColorModeInfo: 0
[    64.781] 	PhysBasePtr: 0xe7000000
[    64.781] 	LinBytesPerScanLine: 1280
[    64.781] 	BnkNumberOfImagePages: 4
[    64.781] 	LinNumberOfImagePages: 4
[    64.781] 	LinRedMaskSize: 5
[    64.781] 	LinRedFieldPosition: 11
[    64.781] 	LinGreenMaskSize: 6
[    64.781] 	LinGreenFieldPosition: 5
[    64.781] 	LinBlueMaskSize: 5
[    64.781] 	LinBlueFieldPosition: 0
[    64.781] 	LinRsvdMaskSize: 0
[    64.781] 	LinRsvdFieldPosition: 0
[    64.781] 	MaxPixelClock: 229500000
[    64.782] *Mode: 112 (640x480)
[    64.782] 	ModeAttributes: 0x3bf
[    64.782] 	WinAAttributes: 0x7
[    64.782] 	WinBAttributes: 0x0
[    64.782] 	WinGranularity: 64
[    64.782] 	WinSize: 64
[    64.782] 	WinASegment: 0xa000
[    64.782] 	WinBSegment: 0x0
[    64.782] 	WinFuncPtr: 0xc000964c
[    64.782] 	BytesPerScanline: 2560
[    64.782] 	XResolution: 640
[    64.782] 	YResolution: 480
[    64.782] 	XCharSize: 8
[    64.782] 	YCharSize: 16
[    64.782] 	NumberOfPlanes: 1
[    64.782] 	BitsPerPixel: 32
[    64.782] 	NumberOfBanks: 1
[    64.782] 	MemoryModel: 6
[    64.782] 	BankSize: 0
[    64.782] 	NumberOfImages: 1
[    64.782] 	RedMaskSize: 8
[    64.782] 	RedFieldPosition: 16
[    64.782] 	GreenMaskSize: 8
[    64.782] 	GreenFieldPosition: 8
[    64.782] 	BlueMaskSize: 8
[    64.782] 	BlueFieldPosition: 0
[    64.782] 	RsvdMaskSize: 8
[    64.782] 	RsvdFieldPosition: 24
[    64.782] 	DirectColorModeInfo: 0
[    64.782] 	PhysBasePtr: 0xe7000000
[    64.782] 	LinBytesPerScanLine: 2560
[    64.782] 	BnkNumberOfImagePages: 1
[    64.782] 	LinNumberOfImagePages: 1
[    64.782] 	LinRedMaskSize: 8
[    64.782] 	LinRedFieldPosition: 16
[    64.782] 	LinGreenMaskSize: 8
[    64.782] 	LinGreenFieldPosition: 8
[    64.782] 	LinBlueMaskSize: 8
[    64.782] 	LinBlueFieldPosition: 0
[    64.782] 	LinRsvdMaskSize: 8
[    64.782] 	LinRsvdFieldPosition: 24
[    64.782] 	MaxPixelClock: 229500000
[    64.783] Mode: 114 (800x600)
[    64.783] 	ModeAttributes: 0x3bf
[    64.783] 	WinAAttributes: 0x7
[    64.783] 	WinBAttributes: 0x0
[    64.783] 	WinGranularity: 64
[    64.783] 	WinSize: 64
[    64.783] 	WinASegment: 0xa000
[    64.783] 	WinBSegment: 0x0
[    64.783] 	WinFuncPtr: 0xc000964c
[    64.783] 	BytesPerScanline: 1600
[    64.783] 	XResolution: 800
[    64.783] 	YResolution: 600
[    64.783] 	XCharSize: 8
[    64.783] 	YCharSize: 16
[    64.783] 	NumberOfPlanes: 1
[    64.783] 	BitsPerPixel: 16
[    64.783] 	NumberOfBanks: 1
[    64.783] 	MemoryModel: 6
[    64.783] 	BankSize: 0
[    64.783] 	NumberOfImages: 2
[    64.783] 	RedMaskSize: 5
[    64.783] 	RedFieldPosition: 11
[    64.783] 	GreenMaskSize: 6
[    64.783] 	GreenFieldPosition: 5
[    64.783] 	BlueMaskSize: 5
[    64.783] 	BlueFieldPosition: 0
[    64.783] 	RsvdMaskSize: 0
[    64.783] 	RsvdFieldPosition: 0
[    64.783] 	DirectColorModeInfo: 0
[    64.783] 	PhysBasePtr: 0xe7000000
[    64.783] 	LinBytesPerScanLine: 1600
[    64.783] 	BnkNumberOfImagePages: 2
[    64.783] 	LinNumberOfImagePages: 2
[    64.783] 	LinRedMaskSize: 5
[    64.783] 	LinRedFieldPosition: 11
[    64.783] 	LinGreenMaskSize: 6
[    64.783] 	LinGreenFieldPosition: 5
[    64.783] 	LinBlueMaskSize: 5
[    64.783] 	LinBlueFieldPosition: 0
[    64.783] 	LinRsvdMaskSize: 0
[    64.783] 	LinRsvdFieldPosition: 0
[    64.783] 	MaxPixelClock: 229500000
[    64.784] *Mode: 115 (800x600)
[    64.784] 	ModeAttributes: 0x3bf
[    64.784] 	WinAAttributes: 0x7
[    64.784] 	WinBAttributes: 0x0
[    64.784] 	WinGranularity: 64
[    64.784] 	WinSize: 64
[    64.784] 	WinASegment: 0xa000
[    64.784] 	WinBSegment: 0x0
[    64.784] 	WinFuncPtr: 0xc000964c
[    64.784] 	BytesPerScanline: 3200
[    64.784] 	XResolution: 800
[    64.784] 	YResolution: 600
[    64.784] 	XCharSize: 8
[    64.784] 	YCharSize: 16
[    64.784] 	NumberOfPlanes: 1
[    64.784] 	BitsPerPixel: 32
[    64.784] 	NumberOfBanks: 1
[    64.784] 	MemoryModel: 6
[    64.784] 	BankSize: 0
[    64.784] 	NumberOfImages: 1
[    64.784] 	RedMaskSize: 8
[    64.784] 	RedFieldPosition: 16
[    64.784] 	GreenMaskSize: 8
[    64.784] 	GreenFieldPosition: 8
[    64.784] 	BlueMaskSize: 8
[    64.784] 	BlueFieldPosition: 0
[    64.784] 	RsvdMaskSize: 8
[    64.784] 	RsvdFieldPosition: 24
[    64.785] 	DirectColorModeInfo: 0
[    64.785] 	PhysBasePtr: 0xe7000000
[    64.785] 	LinBytesPerScanLine: 3200
[    64.785] 	BnkNumberOfImagePages: 1
[    64.785] 	LinNumberOfImagePages: 1
[    64.785] 	LinRedMaskSize: 8
[    64.785] 	LinRedFieldPosition: 16
[    64.785] 	LinGreenMaskSize: 8
[    64.785] 	LinGreenFieldPosition: 8
[    64.785] 	LinBlueMaskSize: 8
[    64.785] 	LinBlueFieldPosition: 0
[    64.785] 	LinRsvdMaskSize: 8
[    64.785] 	LinRsvdFieldPosition: 24
[    64.785] 	MaxPixelClock: 229500000
[    64.786] Mode: 117 (1024x768)
[    64.786] 	ModeAttributes: 0x3bf
[    64.786] 	WinAAttributes: 0x7
[    64.786] 	WinBAttributes: 0x0
[    64.786] 	WinGranularity: 64
[    64.786] 	WinSize: 64
[    64.786] 	WinASegment: 0xa000
[    64.786] 	WinBSegment: 0x0
[    64.786] 	WinFuncPtr: 0xc000964c
[    64.786] 	BytesPerScanline: 2048
[    64.786] 	XResolution: 1024
[    64.786] 	YResolution: 768
[    64.786] 	XCharSize: 8
[    64.786] 	YCharSize: 16
[    64.786] 	NumberOfPlanes: 1
[    64.786] 	BitsPerPixel: 16
[    64.786] 	NumberOfBanks: 1
[    64.786] 	MemoryModel: 6
[    64.786] 	BankSize: 0
[    64.786] 	NumberOfImages: 1
[    64.786] 	RedMaskSize: 5
[    64.786] 	RedFieldPosition: 11
[    64.786] 	GreenMaskSize: 6
[    64.786] 	GreenFieldPosition: 5
[    64.786] 	BlueMaskSize: 5
[    64.786] 	BlueFieldPosition: 0
[    64.786] 	RsvdMaskSize: 0
[    64.786] 	RsvdFieldPosition: 0
[    64.786] 	DirectColorModeInfo: 0
[    64.786] 	PhysBasePtr: 0xe7000000
[    64.786] 	LinBytesPerScanLine: 2048
[    64.786] 	BnkNumberOfImagePages: 1
[    64.786] 	LinNumberOfImagePages: 1
[    64.786] 	LinRedMaskSize: 5
[    64.786] 	LinRedFieldPosition: 11
[    64.786] 	LinGreenMaskSize: 6
[    64.786] 	LinGreenFieldPosition: 5
[    64.786] 	LinBlueMaskSize: 5
[    64.786] 	LinBlueFieldPosition: 0
[    64.786] 	LinRsvdMaskSize: 0
[    64.786] 	LinRsvdFieldPosition: 0
[    64.786] 	MaxPixelClock: 229500000
[    64.787] *Mode: 118 (1024x768)
[    64.787] 	ModeAttributes: 0x3bf
[    64.787] 	WinAAttributes: 0x7
[    64.787] 	WinBAttributes: 0x0
[    64.787] 	WinGranularity: 64
[    64.787] 	WinSize: 64
[    64.787] 	WinASegment: 0xa000
[    64.787] 	WinBSegment: 0x0
[    64.787] 	WinFuncPtr: 0xc000964c
[    64.787] 	BytesPerScanline: 4096
[    64.787] 	XResolution: 1024
[    64.787] 	YResolution: 768
[    64.787] 	XCharSize: 8
[    64.787] 	YCharSize: 16
[    64.787] 	NumberOfPlanes: 1
[    64.787] 	BitsPerPixel: 32
[    64.787] 	NumberOfBanks: 1
[    64.787] 	MemoryModel: 6
[    64.787] 	BankSize: 0
[    64.787] 	NumberOfImages: 1
[    64.787] 	RedMaskSize: 8
[    64.787] 	RedFieldPosition: 16
[    64.787] 	GreenMaskSize: 8
[    64.787] 	GreenFieldPosition: 8
[    64.787] 	BlueMaskSize: 8
[    64.787] 	BlueFieldPosition: 0
[    64.787] 	RsvdMaskSize: 8
[    64.787] 	RsvdFieldPosition: 24
[    64.787] 	DirectColorModeInfo: 0
[    64.787] 	PhysBasePtr: 0xe7000000
[    64.787] 	LinBytesPerScanLine: 4096
[    64.787] 	BnkNumberOfImagePages: 1
[    64.787] 	LinNumberOfImagePages: 1
[    64.787] 	LinRedMaskSize: 8
[    64.787] 	LinRedFieldPosition: 16
[    64.787] 	LinGreenMaskSize: 8
[    64.787] 	LinGreenFieldPosition: 8
[    64.787] 	LinBlueMaskSize: 8
[    64.787] 	LinBlueFieldPosition: 0
[    64.787] 	LinRsvdMaskSize: 8
[    64.787] 	LinRsvdFieldPosition: 24
[    64.787] 	MaxPixelClock: 229500000
[    64.788] Mode: 11a (1280x1024)
[    64.788] 	ModeAttributes: 0x3bf
[    64.788] 	WinAAttributes: 0x7
[    64.788] 	WinBAttributes: 0x0
[    64.788] 	WinGranularity: 64
[    64.788] 	WinSize: 64
[    64.788] 	WinASegment: 0xa000
[    64.788] 	WinBSegment: 0x0
[    64.788] 	WinFuncPtr: 0xc000964c
[    64.788] 	BytesPerScanline: 2560
[    64.788] 	XResolution: 1280
[    64.788] 	YResolution: 1024
[    64.788] 	XCharSize: 8
[    64.788] 	YCharSize: 16
[    64.788] 	NumberOfPlanes: 1
[    64.788] 	BitsPerPixel: 16
[    64.788] 	NumberOfBanks: 1
[    64.788] 	MemoryModel: 6
[    64.788] 	BankSize: 0
[    64.788] 	NumberOfImages: 1
[    64.788] 	RedMaskSize: 5
[    64.788] 	RedFieldPosition: 11
[    64.788] 	GreenMaskSize: 6
[    64.788] 	GreenFieldPosition: 5
[    64.788] 	BlueMaskSize: 5
[    64.788] 	BlueFieldPosition: 0
[    64.788] 	RsvdMaskSize: 0
[    64.788] 	RsvdFieldPosition: 0
[    64.788] 	DirectColorModeInfo: 0
[    64.788] 	PhysBasePtr: 0xe7000000
[    64.788] 	LinBytesPerScanLine: 2560
[    64.788] 	BnkNumberOfImagePages: 1
[    64.788] 	LinNumberOfImagePages: 1
[    64.788] 	LinRedMaskSize: 5
[    64.788] 	LinRedFieldPosition: 11
[    64.788] 	LinGreenMaskSize: 6
[    64.788] 	LinGreenFieldPosition: 5
[    64.788] 	LinBlueMaskSize: 5
[    64.788] 	LinBlueFieldPosition: 0
[    64.788] 	LinRsvdMaskSize: 0
[    64.788] 	LinRsvdFieldPosition: 0
[    64.788] 	MaxPixelClock: 229500000
[    64.789] *Mode: 11b (1280x1024)
[    64.789] 	ModeAttributes: 0x3bf
[    64.789] 	WinAAttributes: 0x7
[    64.789] 	WinBAttributes: 0x0
[    64.789] 	WinGranularity: 64
[    64.789] 	WinSize: 64
[    64.789] 	WinASegment: 0xa000
[    64.789] 	WinBSegment: 0x0
[    64.789] 	WinFuncPtr: 0xc000964c
[    64.789] 	BytesPerScanline: 5120
[    64.789] 	XResolution: 1280
[    64.789] 	YResolution: 1024
[    64.789] 	XCharSize: 8
[    64.789] 	YCharSize: 16
[    64.789] 	NumberOfPlanes: 1
[    64.789] 	BitsPerPixel: 32
[    64.789] 	NumberOfBanks: 1
[    64.789] 	MemoryModel: 6
[    64.789] 	BankSize: 0
[    64.789] 	NumberOfImages: 1
[    64.789] 	RedMaskSize: 8
[    64.789] 	RedFieldPosition: 16
[    64.789] 	GreenMaskSize: 8
[    64.789] 	GreenFieldPosition: 8
[    64.789] 	BlueMaskSize: 8
[    64.789] 	BlueFieldPosition: 0
[    64.789] 	RsvdMaskSize: 8
[    64.789] 	RsvdFieldPosition: 24
[    64.789] 	DirectColorModeInfo: 0
[    64.789] 	PhysBasePtr: 0xe7000000
[    64.789] 	LinBytesPerScanLine: 5120
[    64.789] 	BnkNumberOfImagePages: 1
[    64.789] 	LinNumberOfImagePages: 1
[    64.789] 	LinRedMaskSize: 8
[    64.789] 	LinRedFieldPosition: 16
[    64.789] 	LinGreenMaskSize: 8
[    64.789] 	LinGreenFieldPosition: 8
[    64.789] 	LinBlueMaskSize: 8
[    64.789] 	LinBlueFieldPosition: 0
[    64.789] 	LinRsvdMaskSize: 8
[    64.789] 	LinRsvdFieldPosition: 24
[    64.789] 	MaxPixelClock: 229500000
[    64.790] Mode: 130 (320x200)
[    64.790] 	ModeAttributes: 0x3bf
[    64.790] 	WinAAttributes: 0x7
[    64.790] 	WinBAttributes: 0x0
[    64.790] 	WinGranularity: 64
[    64.790] 	WinSize: 64
[    64.790] 	WinASegment: 0xa000
[    64.791] 	WinBSegment: 0x0
[    64.791] 	WinFuncPtr: 0xc000964c
[    64.791] 	BytesPerScanline: 320
[    64.791] 	XResolution: 320
[    64.791] 	YResolution: 200
[    64.791] 	XCharSize: 8
[    64.791] 	YCharSize: 8
[    64.791] 	NumberOfPlanes: 1
[    64.791] 	BitsPerPixel: 8
[    64.791] 	NumberOfBanks: 1
[    64.791] 	MemoryModel: 4
[    64.791] 	BankSize: 0
[    64.791] 	NumberOfImages: 62
[    64.791] 	RedMaskSize: 0
[    64.791] 	RedFieldPosition: 0
[    64.791] 	GreenMaskSize: 0
[    64.791] 	GreenFieldPosition: 0
[    64.791] 	BlueMaskSize: 0
[    64.791] 	BlueFieldPosition: 0
[    64.791] 	RsvdMaskSize: 0
[    64.791] 	RsvdFieldPosition: 0
[    64.791] 	DirectColorModeInfo: 0
[    64.791] 	PhysBasePtr: 0xe7000000
[    64.791] 	LinBytesPerScanLine: 320
[    64.791] 	BnkNumberOfImagePages: 62
[    64.791] 	LinNumberOfImagePages: 62
[    64.791] 	LinRedMaskSize: 0
[    64.791] 	LinRedFieldPosition: 0
[    64.791] 	LinGreenMaskSize: 0
[    64.791] 	LinGreenFieldPosition: 0
[    64.791] 	LinBlueMaskSize: 0
[    64.791] 	LinBlueFieldPosition: 0
[    64.791] 	LinRsvdMaskSize: 0
[    64.791] 	LinRsvdFieldPosition: 0
[    64.791] 	MaxPixelClock: 229500000
[    64.792] Mode: 131 (320x400)
[    64.792] 	ModeAttributes: 0x3bf
[    64.792] 	WinAAttributes: 0x7
[    64.792] 	WinBAttributes: 0x0
[    64.792] 	WinGranularity: 64
[    64.792] 	WinSize: 64
[    64.792] 	WinASegment: 0xa000
[    64.792] 	WinBSegment: 0x0
[    64.792] 	WinFuncPtr: 0xc000964c
[    64.792] 	BytesPerScanline: 320
[    64.792] 	XResolution: 320
[    64.792] 	YResolution: 400
[    64.792] 	XCharSize: 8
[    64.792] 	YCharSize: 16
[    64.792] 	NumberOfPlanes: 1
[    64.792] 	BitsPerPixel: 8
[    64.792] 	NumberOfBanks: 1
[    64.792] 	MemoryModel: 4
[    64.792] 	BankSize: 0
[    64.792] 	NumberOfImages: 30
[    64.792] 	RedMaskSize: 0
[    64.792] 	RedFieldPosition: 0
[    64.792] 	GreenMaskSize: 0
[    64.792] 	GreenFieldPosition: 0
[    64.792] 	BlueMaskSize: 0
[    64.792] 	BlueFieldPosition: 0
[    64.792] 	RsvdMaskSize: 0
[    64.792] 	RsvdFieldPosition: 0
[    64.792] 	DirectColorModeInfo: 0
[    64.792] 	PhysBasePtr: 0xe7000000
[    64.792] 	LinBytesPerScanLine: 320
[    64.792] 	BnkNumberOfImagePages: 30
[    64.792] 	LinNumberOfImagePages: 30
[    64.792] 	LinRedMaskSize: 0
[    64.792] 	LinRedFieldPosition: 0
[    64.792] 	LinGreenMaskSize: 0
[    64.792] 	LinGreenFieldPosition: 0
[    64.792] 	LinBlueMaskSize: 0
[    64.792] 	LinBlueFieldPosition: 0
[    64.792] 	LinRsvdMaskSize: 0
[    64.792] 	LinRsvdFieldPosition: 0
[    64.792] 	MaxPixelClock: 229500000
[    64.793] Mode: 132 (320x400)
[    64.793] 	ModeAttributes: 0x3bf
[    64.793] 	WinAAttributes: 0x7
[    64.793] 	WinBAttributes: 0x0
[    64.793] 	WinGranularity: 64
[    64.793] 	WinSize: 64
[    64.793] 	WinASegment: 0xa000
[    64.793] 	WinBSegment: 0x0
[    64.793] 	WinFuncPtr: 0xc000964c
[    64.793] 	BytesPerScanline: 640
[    64.793] 	XResolution: 320
[    64.793] 	YResolution: 400
[    64.793] 	XCharSize: 8
[    64.793] 	YCharSize: 16
[    64.793] 	NumberOfPlanes: 1
[    64.793] 	BitsPerPixel: 16
[    64.793] 	NumberOfBanks: 1
[    64.793] 	MemoryModel: 6
[    64.793] 	BankSize: 0
[    64.793] 	NumberOfImages: 14
[    64.793] 	RedMaskSize: 5
[    64.793] 	RedFieldPosition: 11
[    64.793] 	GreenMaskSize: 6
[    64.793] 	GreenFieldPosition: 5
[    64.793] 	BlueMaskSize: 5
[    64.793] 	BlueFieldPosition: 0
[    64.793] 	RsvdMaskSize: 0
[    64.793] 	RsvdFieldPosition: 0
[    64.793] 	DirectColorModeInfo: 0
[    64.793] 	PhysBasePtr: 0xe7000000
[    64.793] 	LinBytesPerScanLine: 640
[    64.793] 	BnkNumberOfImagePages: 14
[    64.793] 	LinNumberOfImagePages: 14
[    64.793] 	LinRedMaskSize: 5
[    64.793] 	LinRedFieldPosition: 11
[    64.793] 	LinGreenMaskSize: 6
[    64.793] 	LinGreenFieldPosition: 5
[    64.793] 	LinBlueMaskSize: 5
[    64.793] 	LinBlueFieldPosition: 0
[    64.793] 	LinRsvdMaskSize: 0
[    64.793] 	LinRsvdFieldPosition: 0
[    64.793] 	MaxPixelClock: 229500000
[    64.794] *Mode: 133 (320x400)
[    64.794] 	ModeAttributes: 0x3bf
[    64.794] 	WinAAttributes: 0x7
[    64.794] 	WinBAttributes: 0x0
[    64.794] 	WinGranularity: 64
[    64.794] 	WinSize: 64
[    64.794] 	WinASegment: 0xa000
[    64.794] 	WinBSegment: 0x0
[    64.794] 	WinFuncPtr: 0xc000964c
[    64.794] 	BytesPerScanline: 1280
[    64.794] 	XResolution: 320
[    64.794] 	YResolution: 400
[    64.794] 	XCharSize: 8
[    64.794] 	YCharSize: 16
[    64.794] 	NumberOfPlanes: 1
[    64.794] 	BitsPerPixel: 32
[    64.794] 	NumberOfBanks: 1
[    64.794] 	MemoryModel: 6
[    64.794] 	BankSize: 0
[    64.794] 	NumberOfImages: 6
[    64.794] 	RedMaskSize: 8
[    64.794] 	RedFieldPosition: 16
[    64.794] 	GreenMaskSize: 8
[    64.794] 	GreenFieldPosition: 8
[    64.794] 	BlueMaskSize: 8
[    64.794] 	BlueFieldPosition: 0
[    64.794] 	RsvdMaskSize: 8
[    64.794] 	RsvdFieldPosition: 24
[    64.794] 	DirectColorModeInfo: 0
[    64.794] 	PhysBasePtr: 0xe7000000
[    64.794] 	LinBytesPerScanLine: 1280
[    64.794] 	BnkNumberOfImagePages: 6
[    64.794] 	LinNumberOfImagePages: 6
[    64.794] 	LinRedMaskSize: 8
[    64.794] 	LinRedFieldPosition: 16
[    64.794] 	LinGreenMaskSize: 8
[    64.794] 	LinGreenFieldPosition: 8
[    64.794] 	LinBlueMaskSize: 8
[    64.794] 	LinBlueFieldPosition: 0
[    64.794] 	LinRsvdMaskSize: 8
[    64.794] 	LinRsvdFieldPosition: 24
[    64.794] 	MaxPixelClock: 229500000
[    64.795] Mode: 134 (320x240)
[    64.795] 	ModeAttributes: 0x3bf
[    64.795] 	WinAAttributes: 0x7
[    64.795] 	WinBAttributes: 0x0
[    64.795] 	WinGranularity: 64
[    64.795] 	WinSize: 64
[    64.795] 	WinASegment: 0xa000
[    64.795] 	WinBSegment: 0x0
[    64.795] 	WinFuncPtr: 0xc000964c
[    64.795] 	BytesPerScanline: 320
[    64.795] 	XResolution: 320
[    64.795] 	YResolution: 240
[    64.795] 	XCharSize: 8
[    64.795] 	YCharSize: 8
[    64.795] 	NumberOfPlanes: 1
[    64.795] 	BitsPerPixel: 8
[    64.795] 	NumberOfBanks: 1
[    64.795] 	MemoryModel: 4
[    64.795] 	BankSize: 0
[    64.795] 	NumberOfImages: 30
[    64.795] 	RedMaskSize: 0
[    64.795] 	RedFieldPosition: 0
[    64.795] 	GreenMaskSize: 0
[    64.795] 	GreenFieldPosition: 0
[    64.795] 	BlueMaskSize: 0
[    64.795] 	BlueFieldPosition: 0
[    64.795] 	RsvdMaskSize: 0
[    64.795] 	RsvdFieldPosition: 0
[    64.795] 	DirectColorModeInfo: 0
[    64.795] 	PhysBasePtr: 0xe7000000
[    64.795] 	LinBytesPerScanLine: 320
[    64.795] 	BnkNumberOfImagePages: 30
[    64.795] 	LinNumberOfImagePages: 30
[    64.795] 	LinRedMaskSize: 0
[    64.795] 	LinRedFieldPosition: 0
[    64.795] 	LinGreenMaskSize: 0
[    64.795] 	LinGreenFieldPosition: 0
[    64.795] 	LinBlueMaskSize: 0
[    64.795] 	LinBlueFieldPosition: 0
[    64.795] 	LinRsvdMaskSize: 0
[    64.795] 	LinRsvdFieldPosition: 0
[    64.795] 	MaxPixelClock: 229500000
[    64.796] Mode: 135 (320x240)
[    64.796] 	ModeAttributes: 0x3bf
[    64.796] 	WinAAttributes: 0x7
[    64.796] 	WinBAttributes: 0x0
[    64.796] 	WinGranularity: 64
[    64.796] 	WinSize: 64
[    64.796] 	WinASegment: 0xa000
[    64.797] 	WinBSegment: 0x0
[    64.797] 	WinFuncPtr: 0xc000964c
[    64.797] 	BytesPerScanline: 640
[    64.797] 	XResolution: 320
[    64.797] 	YResolution: 240
[    64.797] 	XCharSize: 8
[    64.797] 	YCharSize: 8
[    64.797] 	NumberOfPlanes: 1
[    64.797] 	BitsPerPixel: 16
[    64.797] 	NumberOfBanks: 1
[    64.797] 	MemoryModel: 6
[    64.797] 	BankSize: 0
[    64.797] 	NumberOfImages: 19
[    64.797] 	RedMaskSize: 5
[    64.797] 	RedFieldPosition: 11
[    64.797] 	GreenMaskSize: 6
[    64.797] 	GreenFieldPosition: 5
[    64.797] 	BlueMaskSize: 5
[    64.797] 	BlueFieldPosition: 0
[    64.797] 	RsvdMaskSize: 0
[    64.797] 	RsvdFieldPosition: 0
[    64.797] 	DirectColorModeInfo: 0
[    64.797] 	PhysBasePtr: 0xe7000000
[    64.797] 	LinBytesPerScanLine: 640
[    64.797] 	BnkNumberOfImagePages: 19
[    64.797] 	LinNumberOfImagePages: 19
[    64.797] 	LinRedMaskSize: 5
[    64.797] 	LinRedFieldPosition: 11
[    64.797] 	LinGreenMaskSize: 6
[    64.797] 	LinGreenFieldPosition: 5
[    64.797] 	LinBlueMaskSize: 5
[    64.797] 	LinBlueFieldPosition: 0
[    64.797] 	LinRsvdMaskSize: 0
[    64.797] 	LinRsvdFieldPosition: 0
[    64.797] 	MaxPixelClock: 229500000
[    64.798] *Mode: 136 (320x240)
[    64.798] 	ModeAttributes: 0x3bf
[    64.798] 	WinAAttributes: 0x7
[    64.798] 	WinBAttributes: 0x0
[    64.798] 	WinGranularity: 64
[    64.798] 	WinSize: 64
[    64.798] 	WinASegment: 0xa000
[    64.798] 	WinBSegment: 0x0
[    64.798] 	WinFuncPtr: 0xc000964c
[    64.798] 	BytesPerScanline: 1280
[    64.798] 	XResolution: 320
[    64.798] 	YResolution: 240
[    64.798] 	XCharSize: 8
[    64.798] 	YCharSize: 8
[    64.798] 	NumberOfPlanes: 1
[    64.798] 	BitsPerPixel: 32
[    64.798] 	NumberOfBanks: 1
[    64.798] 	MemoryModel: 6
[    64.798] 	BankSize: 0
[    64.798] 	NumberOfImages: 10
[    64.798] 	RedMaskSize: 8
[    64.798] 	RedFieldPosition: 16
[    64.798] 	GreenMaskSize: 8
[    64.798] 	GreenFieldPosition: 8
[    64.798] 	BlueMaskSize: 8
[    64.798] 	BlueFieldPosition: 0
[    64.798] 	RsvdMaskSize: 8
[    64.798] 	RsvdFieldPosition: 24
[    64.798] 	DirectColorModeInfo: 0
[    64.798] 	PhysBasePtr: 0xe7000000
[    64.798] 	LinBytesPerScanLine: 1280
[    64.798] 	BnkNumberOfImagePages: 10
[    64.798] 	LinNumberOfImagePages: 10
[    64.798] 	LinRedMaskSize: 8
[    64.798] 	LinRedFieldPosition: 16
[    64.798] 	LinGreenMaskSize: 8
[    64.798] 	LinGreenFieldPosition: 8
[    64.798] 	LinBlueMaskSize: 8
[    64.798] 	LinBlueFieldPosition: 0
[    64.798] 	LinRsvdMaskSize: 8
[    64.798] 	LinRsvdFieldPosition: 24
[    64.798] 	MaxPixelClock: 229500000
[    64.799] Mode: 13d (640x400)
[    64.799] 	ModeAttributes: 0x3bf
[    64.799] 	WinAAttributes: 0x7
[    64.799] 	WinBAttributes: 0x0
[    64.799] 	WinGranularity: 64
[    64.799] 	WinSize: 64
[    64.799] 	WinASegment: 0xa000
[    64.799] 	WinBSegment: 0x0
[    64.799] 	WinFuncPtr: 0xc000964c
[    64.799] 	BytesPerScanline: 1280
[    64.799] 	XResolution: 640
[    64.799] 	YResolution: 400
[    64.799] 	XCharSize: 8
[    64.799] 	YCharSize: 16
[    64.799] 	NumberOfPlanes: 1
[    64.799] 	BitsPerPixel: 16
[    64.799] 	NumberOfBanks: 1
[    64.799] 	MemoryModel: 6
[    64.799] 	BankSize: 0
[    64.799] 	NumberOfImages: 6
[    64.799] 	RedMaskSize: 5
[    64.799] 	RedFieldPosition: 11
[    64.799] 	GreenMaskSize: 6
[    64.799] 	GreenFieldPosition: 5
[    64.799] 	BlueMaskSize: 5
[    64.799] 	BlueFieldPosition: 0
[    64.799] 	RsvdMaskSize: 0
[    64.799] 	RsvdFieldPosition: 0
[    64.799] 	DirectColorModeInfo: 0
[    64.799] 	PhysBasePtr: 0xe7000000
[    64.799] 	LinBytesPerScanLine: 1280
[    64.799] 	BnkNumberOfImagePages: 6
[    64.799] 	LinNumberOfImagePages: 6
[    64.799] 	LinRedMaskSize: 5
[    64.799] 	LinRedFieldPosition: 11
[    64.799] 	LinGreenMaskSize: 6
[    64.799] 	LinGreenFieldPosition: 5
[    64.799] 	LinBlueMaskSize: 5
[    64.799] 	LinBlueFieldPosition: 0
[    64.799] 	LinRsvdMaskSize: 0
[    64.799] 	LinRsvdFieldPosition: 0
[    64.799] 	MaxPixelClock: 229500000
[    64.800] *Mode: 13e (640x400)
[    64.800] 	ModeAttributes: 0x3bf
[    64.800] 	WinAAttributes: 0x7
[    64.800] 	WinBAttributes: 0x0
[    64.800] 	WinGranularity: 64
[    64.800] 	WinSize: 64
[    64.800] 	WinASegment: 0xa000
[    64.800] 	WinBSegment: 0x0
[    64.800] 	WinFuncPtr: 0xc000964c
[    64.800] 	BytesPerScanline: 2560
[    64.800] 	XResolution: 640
[    64.800] 	YResolution: 400
[    64.800] 	XCharSize: 8
[    64.800] 	YCharSize: 16
[    64.800] 	NumberOfPlanes: 1
[    64.800] 	BitsPerPixel: 32
[    64.800] 	NumberOfBanks: 1
[    64.800] 	MemoryModel: 6
[    64.800] 	BankSize: 0
[    64.800] 	NumberOfImages: 2
[    64.800] 	RedMaskSize: 8
[    64.800] 	RedFieldPosition: 16
[    64.800] 	GreenMaskSize: 8
[    64.800] 	GreenFieldPosition: 8
[    64.800] 	BlueMaskSize: 8
[    64.800] 	BlueFieldPosition: 0
[    64.800] 	RsvdMaskSize: 8
[    64.800] 	RsvdFieldPosition: 24
[    64.800] 	DirectColorModeInfo: 0
[    64.800] 	PhysBasePtr: 0xe7000000
[    64.800] 	LinBytesPerScanLine: 2560
[    64.800] 	BnkNumberOfImagePages: 2
[    64.800] 	LinNumberOfImagePages: 2
[    64.800] 	LinRedMaskSize: 8
[    64.800] 	LinRedFieldPosition: 16
[    64.800] 	LinGreenMaskSize: 8
[    64.800] 	LinGreenFieldPosition: 8
[    64.800] 	LinBlueMaskSize: 8
[    64.800] 	LinBlueFieldPosition: 0
[    64.800] 	LinRsvdMaskSize: 8
[    64.800] 	LinRsvdFieldPosition: 24
[    64.800] 	MaxPixelClock: 229500000
[    64.801] Mode: 160 (1280x800)
[    64.801] 	ModeAttributes: 0x3bf
[    64.801] 	WinAAttributes: 0x7
[    64.801] 	WinBAttributes: 0x0
[    64.801] 	WinGranularity: 64
[    64.801] 	WinSize: 64
[    64.801] 	WinASegment: 0xa000
[    64.801] 	WinBSegment: 0x0
[    64.801] 	WinFuncPtr: 0xc000964c
[    64.801] 	BytesPerScanline: 1280
[    64.801] 	XResolution: 1280
[    64.801] 	YResolution: 800
[    64.801] 	XCharSize: 8
[    64.801] 	YCharSize: 16
[    64.801] 	NumberOfPlanes: 1
[    64.801] 	BitsPerPixel: 8
[    64.801] 	NumberOfBanks: 1
[    64.801] 	MemoryModel: 4
[    64.801] 	BankSize: 0
[    64.801] 	NumberOfImages: 2
[    64.801] 	RedMaskSize: 0
[    64.801] 	RedFieldPosition: 0
[    64.801] 	GreenMaskSize: 0
[    64.801] 	GreenFieldPosition: 0
[    64.801] 	BlueMaskSize: 0
[    64.801] 	BlueFieldPosition: 0
[    64.801] 	RsvdMaskSize: 0
[    64.801] 	RsvdFieldPosition: 0
[    64.801] 	DirectColorModeInfo: 0
[    64.801] 	PhysBasePtr: 0xe7000000
[    64.802] 	LinBytesPerScanLine: 1280
[    64.802] 	BnkNumberOfImagePages: 2
[    64.802] 	LinNumberOfImagePages: 2
[    64.802] 	LinRedMaskSize: 0
[    64.802] 	LinRedFieldPosition: 0
[    64.802] 	LinGreenMaskSize: 0
[    64.802] 	LinGreenFieldPosition: 0
[    64.802] 	LinBlueMaskSize: 0
[    64.802] 	LinBlueFieldPosition: 0
[    64.802] 	LinRsvdMaskSize: 0
[    64.802] 	LinRsvdFieldPosition: 0
[    64.802] 	MaxPixelClock: 229500000
[    64.803] *Mode: 161 (1280x800)
[    64.803] 	ModeAttributes: 0x3bf
[    64.803] 	WinAAttributes: 0x7
[    64.803] 	WinBAttributes: 0x0
[    64.803] 	WinGranularity: 64
[    64.803] 	WinSize: 64
[    64.803] 	WinASegment: 0xa000
[    64.803] 	WinBSegment: 0x0
[    64.803] 	WinFuncPtr: 0xc000964c
[    64.803] 	BytesPerScanline: 5120
[    64.803] 	XResolution: 1280
[    64.803] 	YResolution: 800
[    64.803] 	XCharSize: 8
[    64.803] 	YCharSize: 16
[    64.803] 	NumberOfPlanes: 1
[    64.803] 	BitsPerPixel: 32
[    64.803] 	NumberOfBanks: 1
[    64.803] 	MemoryModel: 6
[    64.803] 	BankSize: 0
[    64.803] 	NumberOfImages: 1
[    64.803] 	RedMaskSize: 8
[    64.803] 	RedFieldPosition: 16
[    64.803] 	GreenMaskSize: 8
[    64.803] 	GreenFieldPosition: 8
[    64.803] 	BlueMaskSize: 8
[    64.803] 	BlueFieldPosition: 0
[    64.803] 	RsvdMaskSize: 8
[    64.803] 	RsvdFieldPosition: 24
[    64.803] 	DirectColorModeInfo: 0
[    64.803] 	PhysBasePtr: 0xe7000000
[    64.803] 	LinBytesPerScanLine: 5120
[    64.803] 	BnkNumberOfImagePages: 1
[    64.803] 	LinNumberOfImagePages: 1
[    64.803] 	LinRedMaskSize: 8
[    64.803] 	LinRedFieldPosition: 16
[    64.803] 	LinGreenMaskSize: 8
[    64.803] 	LinGreenFieldPosition: 8
[    64.803] 	LinBlueMaskSize: 8
[    64.803] 	LinBlueFieldPosition: 0
[    64.803] 	LinRsvdMaskSize: 8
[    64.803] 	LinRsvdFieldPosition: 24
[    64.803] 	MaxPixelClock: 229500000
[    64.804] Mode: 162 (768x480)
[    64.804] 	ModeAttributes: 0x3bf
[    64.804] 	WinAAttributes: 0x7
[    64.804] 	WinBAttributes: 0x0
[    64.804] 	WinGranularity: 64
[    64.804] 	WinSize: 64
[    64.804] 	WinASegment: 0xa000
[    64.804] 	WinBSegment: 0x0
[    64.804] 	WinFuncPtr: 0xc000964c
[    64.804] 	BytesPerScanline: 768
[    64.804] 	XResolution: 768
[    64.804] 	YResolution: 480
[    64.804] 	XCharSize: 8
[    64.804] 	YCharSize: 16
[    64.804] 	NumberOfPlanes: 1
[    64.804] 	BitsPerPixel: 8
[    64.804] 	NumberOfBanks: 1
[    64.804] 	MemoryModel: 4
[    64.804] 	BankSize: 0
[    64.804] 	NumberOfImages: 8
[    64.804] 	RedMaskSize: 0
[    64.804] 	RedFieldPosition: 0
[    64.804] 	GreenMaskSize: 0
[    64.804] 	GreenFieldPosition: 0
[    64.804] 	BlueMaskSize: 0
[    64.804] 	BlueFieldPosition: 0
[    64.804] 	RsvdMaskSize: 0
[    64.804] 	RsvdFieldPosition: 0
[    64.804] 	DirectColorModeInfo: 0
[    64.804] 	PhysBasePtr: 0xe7000000
[    64.804] 	LinBytesPerScanLine: 768
[    64.804] 	BnkNumberOfImagePages: 8
[    64.804] 	LinNumberOfImagePages: 8
[    64.804] 	LinRedMaskSize: 0
[    64.804] 	LinRedFieldPosition: 0
[    64.804] 	LinGreenMaskSize: 0
[    64.804] 	LinGreenFieldPosition: 0
[    64.804] 	LinBlueMaskSize: 0
[    64.804] 	LinBlueFieldPosition: 0
[    64.804] 	LinRsvdMaskSize: 0
[    64.804] 	LinRsvdFieldPosition: 0
[    64.804] 	MaxPixelClock: 229500000
[    64.805] Mode: 164 (1440x900)
[    64.805] 	ModeAttributes: 0x3bf
[    64.805] 	WinAAttributes: 0x7
[    64.805] 	WinBAttributes: 0x0
[    64.805] 	WinGranularity: 64
[    64.805] 	WinSize: 64
[    64.805] 	WinASegment: 0xa000
[    64.805] 	WinBSegment: 0x0
[    64.805] 	WinFuncPtr: 0xc000964c
[    64.805] 	BytesPerScanline: 1440
[    64.805] 	XResolution: 1440
[    64.805] 	YResolution: 900
[    64.805] 	XCharSize: 8
[    64.805] 	YCharSize: 16
[    64.805] 	NumberOfPlanes: 1
[    64.805] 	BitsPerPixel: 8
[    64.805] 	NumberOfBanks: 1
[    64.805] 	MemoryModel: 4
[    64.805] 	BankSize: 0
[    64.805] 	NumberOfImages: 1
[    64.805] 	RedMaskSize: 0
[    64.805] 	RedFieldPosition: 0
[    64.805] 	GreenMaskSize: 0
[    64.805] 	GreenFieldPosition: 0
[    64.805] 	BlueMaskSize: 0
[    64.805] 	BlueFieldPosition: 0
[    64.805] 	RsvdMaskSize: 0
[    64.805] 	RsvdFieldPosition: 0
[    64.805] 	DirectColorModeInfo: 0
[    64.805] 	PhysBasePtr: 0xe7000000
[    64.805] 	LinBytesPerScanLine: 1440
[    64.805] 	BnkNumberOfImagePages: 1
[    64.805] 	LinNumberOfImagePages: 1
[    64.805] 	LinRedMaskSize: 0
[    64.805] 	LinRedFieldPosition: 0
[    64.805] 	LinGreenMaskSize: 0
[    64.805] 	LinGreenFieldPosition: 0
[    64.805] 	LinBlueMaskSize: 0
[    64.805] 	LinBlueFieldPosition: 0
[    64.805] 	LinRsvdMaskSize: 0
[    64.805] 	LinRsvdFieldPosition: 0
[    64.805] 	MaxPixelClock: 229500000
[    64.806] *Mode: 165 (1440x900)
[    64.806] 	ModeAttributes: 0x3bf
[    64.806] 	WinAAttributes: 0x7
[    64.806] 	WinBAttributes: 0x0
[    64.806] 	WinGranularity: 64
[    64.806] 	WinSize: 64
[    64.806] 	WinASegment: 0xa000
[    64.806] 	WinBSegment: 0x0
[    64.806] 	WinFuncPtr: 0xc000964c
[    64.806] 	BytesPerScanline: 5760
[    64.806] 	XResolution: 1440
[    64.806] 	YResolution: 900
[    64.806] 	XCharSize: 8
[    64.806] 	YCharSize: 16
[    64.806] 	NumberOfPlanes: 1
[    64.806] 	BitsPerPixel: 32
[    64.806] 	NumberOfBanks: 1
[    64.806] 	MemoryModel: 6
[    64.806] 	BankSize: 0
[    64.806] 	NumberOfImages: 1
[    64.806] 	RedMaskSize: 8
[    64.806] 	RedFieldPosition: 16
[    64.806] 	GreenMaskSize: 8
[    64.806] 	GreenFieldPosition: 8
[    64.807] 	BlueMaskSize: 8
[    64.807] 	BlueFieldPosition: 0
[    64.807] 	RsvdMaskSize: 8
[    64.807] 	RsvdFieldPosition: 24
[    64.807] 	DirectColorModeInfo: 0
[    64.807] 	PhysBasePtr: 0xe7000000
[    64.807] 	LinBytesPerScanLine: 5760
[    64.807] 	BnkNumberOfImagePages: 1
[    64.807] 	LinNumberOfImagePages: 1
[    64.807] 	LinRedMaskSize: 8
[    64.807] 	LinRedFieldPosition: 16
[    64.807] 	LinGreenMaskSize: 8
[    64.807] 	LinGreenFieldPosition: 8
[    64.807] 	LinBlueMaskSize: 8
[    64.807] 	LinBlueFieldPosition: 0
[    64.807] 	LinRsvdMaskSize: 8
[    64.807] 	LinRsvdFieldPosition: 24
[    64.807] 	MaxPixelClock: 229500000
[    64.808] *Mode: 17b (1280x720)
[    64.808] 	ModeAttributes: 0x3bf
[    64.808] 	WinAAttributes: 0x7
[    64.808] 	WinBAttributes: 0x0
[    64.808] 	WinGranularity: 64
[    64.808] 	WinSize: 64
[    64.808] 	WinASegment: 0xa000
[    64.808] 	WinBSegment: 0x0
[    64.808] 	WinFuncPtr: 0xc000964c
[    64.808] 	BytesPerScanline: 5120
[    64.808] 	XResolution: 1280
[    64.808] 	YResolution: 720
[    64.808] 	XCharSize: 8
[    64.808] 	YCharSize: 16
[    64.808] 	NumberOfPlanes: 1
[    64.808] 	BitsPerPixel: 32
[    64.808] 	NumberOfBanks: 1
[    64.808] 	MemoryModel: 6
[    64.808] 	BankSize: 0
[    64.808] 	NumberOfImages: 1
[    64.808] 	RedMaskSize: 8
[    64.808] 	RedFieldPosition: 16
[    64.808] 	GreenMaskSize: 8
[    64.808] 	GreenFieldPosition: 8
[    64.808] 	BlueMaskSize: 8
[    64.808] 	BlueFieldPosition: 0
[    64.808] 	RsvdMaskSize: 8
[    64.808] 	RsvdFieldPosition: 24
[    64.808] 	DirectColorModeInfo: 0
[    64.808] 	PhysBasePtr: 0xe7000000
[    64.808] 	LinBytesPerScanLine: 5120
[    64.808] 	BnkNumberOfImagePages: 1
[    64.808] 	LinNumberOfImagePages: 1
[    64.808] 	LinRedMaskSize: 8
[    64.808] 	LinRedFieldPosition: 16
[    64.808] 	LinGreenMaskSize: 8
[    64.808] 	LinGreenFieldPosition: 8
[    64.808] 	LinBlueMaskSize: 8
[    64.808] 	LinBlueFieldPosition: 0
[    64.808] 	LinRsvdMaskSize: 8
[    64.808] 	LinRsvdFieldPosition: 24
[    64.808] 	MaxPixelClock: 229500000
[    64.808] 
[    64.808] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    64.808] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    64.808] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    64.808] (II) VESA(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    64.808] (WW) VESA(0): Unable to estimate virtual size
[    64.808] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "1440x900" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "1280x720" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    64.808] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    64.808] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    64.808] (II) VESA(0): <default monitor>: Using hsync range of 31.50-48.00 kHz
[    64.808] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    64.808] (II) VESA(0): <default monitor>: Using maximum pixel clock of 65.00 MHz
[    64.808] (WW) VESA(0): Unable to estimate virtual size
[    64.808] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[    64.808] (II) VESA(0): Not using built-in mode "1440x900" (hsync out of range)
[    64.808] (II) VESA(0): Not using built-in mode "1280x800" (hsync out of range)
[    64.808] (II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
[    64.808] (II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
[    64.808] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    64.808] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    64.808] (--) VESA(0): Virtual size is 1280x768 (pitch 1280)
[    64.808] (**) VESA(0): *Built-in mode "1280x720"
[    64.808] (**) VESA(0): *Built-in mode "1024x768"
[    64.808] (**) VESA(0): *Built-in mode "800x600"
[    64.808] (**) VESA(0): *Built-in mode "640x480"
[    64.808] (==) VESA(0): DPI set to (96, 96)
[    64.808] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    64.809] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    64.809] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    64.809] (**) VESA(0): Using "Shadow Framebuffer"
[    64.809] (II) Loading sub module "shadow"
[    64.809] (II) LoadModule: "shadow"
[    64.809] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    64.809] (II) Module shadow: vendor="X.Org Foundation"
[    64.809] 	compiled for 1.15.1, module version = 1.1.0
[    64.809] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    64.809] (II) Loading sub module "fb"
[    64.809] (II) LoadModule: "fb"
[    64.809] (II) Loading /usr/lib/xorg/modules/libfb.so
[    64.809] (II) Module fb: vendor="X.Org Foundation"
[    64.810] 	compiled for 1.15.1, module version = 1.0.0
[    64.810] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    64.810] (==) Depth 24 pixmap format is 32 bpp
[    64.810] (II) Loading sub module "int10"
[    64.810] (II) LoadModule: "int10"
[    64.810] (II) Loading /usr/lib/xorg/modules/libint10.so
[    64.810] (II) Module int10: vendor="X.Org Foundation"
[    64.810] 	compiled for 1.15.1, module version = 1.0.0
[    64.810] 	ABI class: X.Org Video Driver, version 15.0
[    64.810] (II) VESA(0): initializing int10
[    64.810] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    64.850] (II) VESA(0): VESA BIOS detected
[    64.850] (II) VESA(0): VESA VBE Version 3.0
[    64.850] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    64.850] (II) VESA(0): VESA VBE OEM: NVIDIA
[    64.850] (II) VESA(0): VESA VBE OEM Software Rev: 98.119
[    64.850] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    64.850] (II) VESA(0): VESA VBE OEM Product: MCP77 Board - mcp78ovo
[    64.850] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    64.850] (II) VESA(0): virtual address = 0x7f669800c000,
	physical address = 0xe7000000, size = 14680064
[    64.866] (II) VESA(0): Setting up VESA Mode 0x17B (1280x720)
[    64.985] (==) VESA(0): Default visual is TrueColor
[    64.985] (==) VESA(0): Backing store enabled
[    64.985] (==) VESA(0): DPMS enabled
[    64.985] (==) RandR enabled
[    64.990] (II) SELinux: Disabled on system
[    64.991] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    65.000] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    65.003] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    65.003] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    65.003] (II) LoadModule: "evdev"
[    65.003] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    65.003] (II) Module evdev: vendor="X.Org Foundation"
[    65.003] 	compiled for 1.15.0, module version = 2.8.2
[    65.003] 	Module class: X.Org XInput Driver
[    65.003] 	ABI class: X.Org XInput driver, version 20.0
[    65.003] (II) Using input driver 'evdev' for 'Power Button'
[    65.003] (**) Power Button: always reports core events
[    65.003] (**) evdev: Power Button: Device: "/dev/input/event1"
[    65.003] (--) evdev: Power Button: Vendor 0 Product 0x1
[    65.003] (--) evdev: Power Button: Found keys
[    65.003] (II) evdev: Power Button: Configuring as keyboard
[    65.003] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    65.003] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    65.003] (**) Option "xkb_rules" "evdev"
[    65.003] (**) Option "xkb_model" "pc105"
[    65.003] (**) Option "xkb_layout" "us"
[    65.003] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    65.005] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    65.005] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    65.005] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    65.005] (II) Using input driver 'evdev' for 'Video Bus'
[    65.006] (**) Video Bus: always reports core events
[    65.006] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    65.006] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    65.006] (--) evdev: Video Bus: Found keys
[    65.006] (II) evdev: Video Bus: Configuring as keyboard
[    65.006] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:16/LNXVIDEO:00/input/input9/event6"
[    65.006] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    65.006] (**) Option "xkb_rules" "evdev"
[    65.006] (**) Option "xkb_model" "pc105"
[    65.006] (**) Option "xkb_layout" "us"
[    65.006] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    65.006] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    65.006] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    65.006] (II) Using input driver 'evdev' for 'Power Button'
[    65.006] (**) Power Button: always reports core events
[    65.006] (**) evdev: Power Button: Device: "/dev/input/event0"
[    65.006] (--) evdev: Power Button: Vendor 0 Product 0x1
[    65.006] (--) evdev: Power Button: Found keys
[    65.006] (II) evdev: Power Button: Configuring as keyboard
[    65.006] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    65.006] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    65.006] (**) Option "xkb_rules" "evdev"
[    65.006] (**) Option "xkb_model" "pc105"
[    65.006] (**) Option "xkb_layout" "us"
[    65.006] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    65.007] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1020 (/dev/input/event2)
[    65.007] (**) Logitech Unifying Device. Wireless PID:1020: Applying InputClass "evdev pointer catchall"
[    65.007] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1020'
[    65.007] (**) Logitech Unifying Device. Wireless PID:1020: always reports core events
[    65.007] (**) evdev: Logitech Unifying Device. Wireless PID:1020: Device: "/dev/input/event2"
[    65.007] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Vendor 0x46d Product 0xc52b
[    65.007] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Found 20 mouse buttons
[    65.007] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Found scroll wheel(s)
[    65.007] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Found relative axes
[    65.007] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Found x and y relative axes
[    65.007] (II) evdev: Logitech Unifying Device. Wireless PID:1020: Configuring as mouse
[    65.007] (II) evdev: Logitech Unifying Device. Wireless PID:1020: Adding scrollwheel support
[    65.007] (**) evdev: Logitech Unifying Device. Wireless PID:1020: YAxisMapping: buttons 4 and 5
[    65.007] (**) evdev: Logitech Unifying Device. Wireless PID:1020: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    65.007] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.2/3-2.2:1.2/0003:046D:C52B.0003/input/input5/event2"
[    65.007] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1020" (type: MOUSE, id 9)
[    65.007] (II) evdev: Logitech Unifying Device. Wireless PID:1020: initialized for relative axes.
[    65.007] (**) Logitech Unifying Device. Wireless PID:1020: (accel) keeping acceleration scheme 1
[    65.007] (**) Logitech Unifying Device. Wireless PID:1020: (accel) acceleration profile 0
[    65.007] (**) Logitech Unifying Device. Wireless PID:1020: (accel) acceleration factor: 2.000
[    65.007] (**) Logitech Unifying Device. Wireless PID:1020: (accel) acceleration threshold: 4
[    65.007] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1020 (/dev/input/mouse0)
[    65.007] (II) No input driver specified, ignoring this device.
[    65.007] (II) This device may have been added with another device file.
[    65.008] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4004 (/dev/input/event3)
[    65.008] (**) Logitech Unifying Device. Wireless PID:4004: Applying InputClass "evdev keyboard catchall"
[    65.008] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:4004'
[    65.008] (**) Logitech Unifying Device. Wireless PID:4004: always reports core events
[    65.008] (**) evdev: Logitech Unifying Device. Wireless PID:4004: Device: "/dev/input/event3"
[    65.008] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Vendor 0x46d Product 0xc52b
[    65.008] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found 1 mouse buttons
[    65.008] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found scroll wheel(s)
[    65.008] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found relative axes
[    65.008] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Forcing relative x/y axes to exist.
[    65.008] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found absolute axes
[    65.008] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Forcing absolute x/y axes to exist.
[    65.008] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found keys
[    65.008] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Configuring as mouse
[    65.008] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Configuring as keyboard
[    65.008] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Adding scrollwheel support
[    65.008] (**) evdev: Logitech Unifying Device. Wireless PID:4004: YAxisMapping: buttons 4 and 5
[    65.008] (**) evdev: Logitech Unifying Device. Wireless PID:4004: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    65.008] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.2/3-2.2:1.2/0003:046D:C52B.0003/input/input6/event3"
[    65.008] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:4004" (type: KEYBOARD, id 10)
[    65.008] (**) Option "xkb_rules" "evdev"
[    65.008] (**) Option "xkb_model" "pc105"
[    65.008] (**) Option "xkb_layout" "us"
[    65.008] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    65.008] (II) evdev: Logitech Unifying Device. Wireless PID:4004: initialized for relative axes.
[    65.008] (WW) evdev: Logitech Unifying Device. Wireless PID:4004: ignoring absolute axes.
[    65.008] (**) Logitech Unifying Device. Wireless PID:4004: (accel) keeping acceleration scheme 1
[    65.008] (**) Logitech Unifying Device. Wireless PID:4004: (accel) acceleration profile 0
[    65.008] (**) Logitech Unifying Device. Wireless PID:4004: (accel) acceleration factor: 2.000
[    65.008] (**) Logitech Unifying Device. Wireless PID:4004: (accel) acceleration threshold: 4
[    65.008] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101f (/dev/input/event4)
[    65.008] (**) Logitech Unifying Device. Wireless PID:101f: Applying InputClass "evdev pointer catchall"
[    65.008] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101f'
[    65.009] (**) Logitech Unifying Device. Wireless PID:101f: always reports core events
[    65.009] (**) evdev: Logitech Unifying Device. Wireless PID:101f: Device: "/dev/input/event4"
[    65.009] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Vendor 0x46d Product 0xc52b
[    65.009] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Found 20 mouse buttons
[    65.009] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Found scroll wheel(s)
[    65.009] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Found relative axes
[    65.009] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Found x and y relative axes
[    65.009] (II) evdev: Logitech Unifying Device. Wireless PID:101f: Configuring as mouse
[    65.009] (II) evdev: Logitech Unifying Device. Wireless PID:101f: Adding scrollwheel support
[    65.009] (**) evdev: Logitech Unifying Device. Wireless PID:101f: YAxisMapping: buttons 4 and 5
[    65.009] (**) evdev: Logitech Unifying Device. Wireless PID:101f: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    65.009] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.2/3-2.2:1.2/0003:046D:C52B.0003/input/input7/event4"
[    65.009] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101f" (type: MOUSE, id 11)
[    65.009] (II) evdev: Logitech Unifying Device. Wireless PID:101f: initialized for relative axes.
[    65.009] (**) Logitech Unifying Device. Wireless PID:101f: (accel) keeping acceleration scheme 1
[    65.009] (**) Logitech Unifying Device. Wireless PID:101f: (accel) acceleration profile 0
[    65.009] (**) Logitech Unifying Device. Wireless PID:101f: (accel) acceleration factor: 2.000
[    65.009] (**) Logitech Unifying Device. Wireless PID:101f: (accel) acceleration threshold: 4
[    65.009] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101f (/dev/input/mouse1)
[    65.009] (II) No input driver specified, ignoring this device.
[    65.009] (II) This device may have been added with another device file.
[    65.009] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    65.009] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    65.009] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    65.009] (**) Logitech USB Receiver: always reports core events
[    65.009] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event5"
[    65.009] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc51b
[    65.009] (--) evdev: Logitech USB Receiver: Found 12 mouse buttons
[    65.009] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    65.009] (--) evdev: Logitech USB Receiver: Found relative axes
[    65.009] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    65.009] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    65.009] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    65.009] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    65.009] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    65.009] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input8/event5"
[    65.010] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 12)
[    65.010] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    65.010] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    65.010] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    65.010] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    65.010] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    65.010] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse2)
[    65.010] (II) No input driver specified, ignoring this device.
[    65.010] (II) This device may have been added with another device file.
[    65.010] (II) config/udev: Adding input device HDA NVidia Front Mic (/dev/input/event14)
[    65.010] (II) No input driver specified, ignoring this device.
[    65.010] (II) This device may have been added with another device file.
[    65.010] (II) config/udev: Adding input device HDA NVidia Rear Mic (/dev/input/event13)
[    65.010] (II) No input driver specified, ignoring this device.
[    65.010] (II) This device may have been added with another device file.
[    65.011] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event12)
[    65.011] (II) No input driver specified, ignoring this device.
[    65.011] (II) This device may have been added with another device file.
[    65.011] (II) config/udev: Adding input device HDA NVidia Line Out Front (/dev/input/event11)
[    65.011] (II) No input driver specified, ignoring this device.
[    65.011] (II) This device may have been added with another device file.
[    65.011] (II) config/udev: Adding input device HDA NVidia Line Out Surround (/dev/input/event10)
[    65.011] (II) No input driver specified, ignoring this device.
[    65.011] (II) This device may have been added with another device file.
[    65.011] (II) config/udev: Adding input device HDA NVidia Line Out CLFE (/dev/input/event9)
[    65.011] (II) No input driver specified, ignoring this device.
[    65.011] (II) This device may have been added with another device file.
[    65.011] (II) config/udev: Adding input device HDA NVidia Line Out Side (/dev/input/event8)
[    65.011] (II) No input driver specified, ignoring this device.
[    65.011] (II) This device may have been added with another device file.
[    65.011] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event7)
[    65.011] (II) No input driver specified, ignoring this device.
[    65.011] (II) This device may have been added with another device file.
[    77.068] (II) evdev: Logitech USB Receiver: Close
[    77.068] (II) UnloadModule: "evdev"
[    77.068] (II) evdev: Logitech Unifying Device. Wireless PID:101f: Close
[    77.068] (II) UnloadModule: "evdev"
[    77.068] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Close
[    77.068] (II) UnloadModule: "evdev"
[    77.068] (II) evdev: Logitech Unifying Device. Wireless PID:1020: Close
[    77.068] (II) UnloadModule: "evdev"
[    77.068] (II) evdev: Power Button: Close
[    77.068] (II) UnloadModule: "evdev"
[    77.068] (II) evdev: Video Bus: Close
[    77.068] (II) UnloadModule: "evdev"
[    77.068] (II) evdev: Power Button: Close
[    77.068] (II) UnloadModule: "evdev"
[    77.291] (EE) Server terminated successfully (0). Closing log file.
```

shoulda done this days ago, huh

---

### Post by Yellow Pasque on 2015-09-18
```
[ 64.475] (EE) NVIDIA: Failed to initialize the NVIDIA kernel module. Please see the
[ 64.475] (EE) NVIDIA: system's kernel log for additional error messages and
[ 64.475] (EE) NVIDIA: consult the NVIDIA README for details.
```

That's not good. What happens when you try to manually load it?:
```
sudo modprobe -v nvidia
```

Are there any logs in /var/lib/dkms/nvidia-current/ ?
If you have a /var/lib/dkms/nvidia-current/340.93/build/make.log file, please post it.

---

### Post by QIII on 2015-09-18
Please use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by garyt53 on 2015-09-18
aaw, I got caught.....didn't know, do now

thanks Qlll

OK Tem -

Here's the results of modprobe:
#lnsmod /lib/modules/3.13.0-63-generic/updates/dkms/nvidia-340.ko#

and the contents of dkms are viewed in tree from win7, attached

gt

should I now try to reinstall 340 from the new Ubuntu PPA and resend all requested info?
would be my 2nd attempt to install 340 and will have to do it from the shell terminal as cannot access OS 

I may have screwed it up way more when I entered shell terminal and updated/upgraded with a lotta activity huh

no errors though

no dkms logs so shall I just attempt nvidia purge and reinstall of 340 driver from new UbuntuPPA?

probably did that "#" thing wrong somehow, huh

in the future will just paste into QuickReply.....I understand what QIII told me to do there

or maybe the Addl Drivers synaptic utility (formerly jockey) was actually processing my request to change from 304 to 340 even though system monitor indicated no activity for over 15min

in which case a simple but time consuming restoration from BU and patient retry with addl drivers would work

do you think addl drivers was really processing when sys monitor indicated no activity?  the led on the cpu was not flickering either.  and the progress bar just hung at 1/6th, like it didn't even get my command after unchecking the 304 and checking the 340.  

As I've said earlier, while I know I have a clean system with very few PPAs and installed most everything thru the software sources or synaptic, I hate anomalous behavior like that cause it usually indicates running on corrupt code.

---

### Post by blm-ubunet on 2015-09-20
FYI: if you use kernel boot option "nomodeset" then the nVidia kernel module must fail to load.

---

### Post by garyt53 on 2015-09-20
I used nomodeset from the grub2 grubcustomizer linux boot line (next to last after hitting "e") adding nomodeset after quiet splash, all this both with and without the text that was following quiet splash ($vt_handoff) and horiz-hold failures turning to black or white screen always

you will find that I provided that info in post 21, page 3

none of the customary options work now to get in but I have terminal access with Cntrl+Alt+F1

try to purge and reinstall from there?  give me your step by step

system restored successfully
shall I again attempt AdditionalDrivers to switch from 304 to 340 even though I experienced inactivity last time, in other words, wait for more than 15 minutes with sysmonitor showing zero activity
if so, please list step by step - in other words, when to purge the xorg-edgers PPA, ect

Hi Folks -

It's become apparent, both from all the conflicting information on the web as well as how this thread has developed, that this graphics driver issue has no solution here.  I'm just thankful I was able to restore my system, albeit from a BU lacking recent changes.  Don't they always.

Will continue to take a few more stabs at this (nvidia 304 to 340) referencing material of dubious credibility before I bring this restoration back up to date.  Will let you know if I succeed.  But for now, just mark this thread unsolved, unless anybody has anything relevant and promising to add. 

I just won't submit to do a fresh install when this system has been so well-developed, as I won't submit to win10 that won't even support VM or older CADD.  Watch your MSUpdates real close folks.

gt

---

### Post by garyt53 on 2015-10-04
Back again, having past diminishing returns a week ago.  Here's the contents of the Xorg.0.log.old from my latest attempt to just install 340 thru xorg-edgers after all the required cleanup:

```

[   718.187] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   718.188] X Protocol Version 11, Revision 0
[   718.188] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[   718.188] Current Operating System: Linux gary-p6313w 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64
[   718.188] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=5af48839-2770-47f0-8cd3-346bd101ddb3 ro quiet splash
[   718.188] Build Date: 30 July 2014  12:21:54AM
[   718.188] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[   718.188] Current version of pixman: 0.30.2
[   718.188] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   718.188] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   718.188] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Oct  4 22:30:53 2014
[   718.188] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   718.188] (==) No Layout section.  Using the first Screen section.
[   718.188] (==) No screen section available. Using defaults.
[   718.188] (**) |-->Screen "Default Screen Section" (0)
[   718.188] (**) |   |-->Monitor "<default monitor>"
[   718.188] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   718.188] (==) Automatically adding devices
[   718.188] (==) Automatically enabling devices
[   718.188] (==) Automatically adding GPU devices
[   718.188] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   718.188] 	Entry deleted from font path.
[   718.188] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   718.188] 	Entry deleted from font path.
[   718.188] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   718.188] 	Entry deleted from font path.
[   718.188] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   718.188] 	Entry deleted from font path.
[   718.188] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   718.188] 	Entry deleted from font path.
[   718.188] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   718.188] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   718.188] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   718.188] (II) Loader magic: 0x7fd50b191d40
[   718.188] (II) Module ABI versions:
[   718.188] 	X.Org ANSI C Emulation: 0.4
[   718.188] 	X.Org Video Driver: 15.0
[   718.188] 	X.Org XInput driver : 20.0
[   718.188] 	X.Org Server Extension : 8.0
[   718.190] (--) PCI:*(0:2:0:0) 10de:0847:103c:2a9e rev 162, Mem @ 0xfd000000/16777216, 0xe8000000/134217728, 0xe6000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[   718.190] Initializing built-in extension Generic Event Extension
[   718.190] Initializing built-in extension SHAPE
[   718.190] Initializing built-in extension MIT-SHM
[   718.190] Initializing built-in extension XInputExtension
[   718.190] Initializing built-in extension XTEST
[   718.190] Initializing built-in extension BIG-REQUESTS
[   718.190] Initializing built-in extension SYNC
[   718.190] Initializing built-in extension XKEYBOARD
[   718.190] Initializing built-in extension XC-MISC
[   718.190] Initializing built-in extension SECURITY
[   718.190] Initializing built-in extension XINERAMA
[   718.190] Initializing built-in extension XFIXES
[   718.190] Initializing built-in extension RENDER
[   718.190] Initializing built-in extension RANDR
[   718.190] Initializing built-in extension COMPOSITE
[   718.190] Initializing built-in extension DAMAGE
[   718.190] Initializing built-in extension MIT-SCREEN-SAVER
[   718.190] Initializing built-in extension DOUBLE-BUFFER
[   718.190] Initializing built-in extension RECORD
[   718.190] Initializing built-in extension DPMS
[   718.190] Initializing built-in extension Present
[   718.190] Initializing built-in extension DRI3
[   718.190] Initializing built-in extension X-Resource
[   718.190] Initializing built-in extension XVideo
[   718.190] Initializing built-in extension XVideo-MotionCompensation
[   718.190] Initializing built-in extension SELinux
[   718.190] Initializing built-in extension XFree86-VidModeExtension
[   718.190] Initializing built-in extension XFree86-DGA
[   718.190] Initializing built-in extension XFree86-DRI
[   718.190] Initializing built-in extension DRI2
[   718.190] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   718.190] (II) "glx" will be loaded by default.
[   718.190] (WW) "xmir" is not to be loaded by default. Skipping.
[   718.190] (II) LoadModule: "glx"
[   718.190] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   718.202] (II) Module glx: vendor="NVIDIA Corporation"
[   718.202] 	compiled for 4.0.2, module version = 1.0.0
[   718.202] 	Module class: X.Org Server Extension
[   718.202] (II) NVIDIA GLX Module  304.117  Tue Nov 26 21:45:09 PST 2013
[   718.202] Loading extension GLX
[   718.202] (==) Matched nvidia as autoconfigured driver 0
[   718.202] (==) Matched nouveau as autoconfigured driver 1
[   718.202] (==) Matched modesetting as autoconfigured driver 2
[   718.202] (==) Matched fbdev as autoconfigured driver 3
[   718.202] (==) Matched vesa as autoconfigured driver 4
[   718.202] (==) Assigned the driver to the xf86ConfigLayout
[   718.202] (II) LoadModule: "nvidia"
[   718.202] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   718.203] (II) Module nvidia: vendor="NVIDIA Corporation"
[   718.203] 	compiled for 4.0.2, module version = 1.0.0
[   718.203] 	Module class: X.Org Video Driver
[   718.203] (II) LoadModule: "nouveau"
[   718.203] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   718.203] (II) Module nouveau: vendor="X.Org Foundation"
[   718.203] 	compiled for 1.15.0, module version = 1.0.10
[   718.203] 	Module class: X.Org Video Driver
[   718.203] 	ABI class: X.Org Video Driver, version 15.0
[   718.203] (II) LoadModule: "modesetting"
[   718.204] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   718.204] (II) Module modesetting: vendor="X.Org Foundation"
[   718.204] 	compiled for 1.15.0, module version = 0.8.1
[   718.204] 	Module class: X.Org Video Driver
[   718.204] 	ABI class: X.Org Video Driver, version 15.0
[   718.204] (II) LoadModule: "fbdev"
[   718.204] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   718.204] (II) Module fbdev: vendor="X.Org Foundation"
[   718.204] 	compiled for 1.15.0, module version = 0.4.4
[   718.204] 	Module class: X.Org Video Driver
[   718.204] 	ABI class: X.Org Video Driver, version 15.0
[   718.204] (II) LoadModule: "vesa"
[   718.204] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   718.204] (II) Module vesa: vendor="X.Org Foundation"
[   718.204] 	compiled for 1.15.0, module version = 2.3.3
[   718.204] 	Module class: X.Org Video Driver
[   718.204] 	ABI class: X.Org Video Driver, version 15.0
[   718.204] (II) NVIDIA dlloader X Driver  304.117  Tue Nov 26 21:27:08 PST 2013
[   718.204] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   718.204] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[   718.204] (II) NOUVEAU driver for NVIDIA chipset families :
[   718.204] 	RIVA TNT        (NV04)
[   718.204] 	RIVA TNT2       (NV05)
[   718.204] 	GeForce 256     (NV10)
[   718.204] 	GeForce 2       (NV11, NV15)
[   718.204] 	GeForce 4MX     (NV17, NV18)
[   718.204] 	GeForce 3       (NV20)
[   718.204] 	GeForce 4Ti     (NV25, NV28)
[   718.204] 	GeForce FX      (NV3x)
[   718.204] 	GeForce 6       (NV4x)
[   718.205] 	GeForce 7       (G7x)
[   718.205] 	GeForce 8       (G8x)
[   718.205] 	GeForce GTX 200 (NVA0)
[   718.205] 	GeForce GTX 400 (NVC0)
[   718.205] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   718.205] (II) FBDEV: driver for framebuffer: fbdev
[   718.205] (II) VESA: driver for VESA chipsets: vesa
[   718.205] (++) using VT number 8

[   718.206] (II) Loading sub module "fb"
[   718.206] (II) LoadModule: "fb"
[   718.206] (II) Loading /usr/lib/xorg/modules/libfb.so
[   718.206] (II) Module fb: vendor="X.Org Foundation"
[   718.206] 	compiled for 1.15.1, module version = 1.0.0
[   718.206] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   718.206] (II) Loading sub module "wfb"
[   718.206] (II) LoadModule: "wfb"
[   718.206] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   718.206] (II) Module wfb: vendor="X.Org Foundation"
[   718.206] 	compiled for 1.15.1, module version = 1.0.0
[   718.206] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   718.206] (II) Loading sub module "ramdac"
[   718.206] (II) LoadModule: "ramdac"
[   718.206] (II) Module "ramdac" already built-in
[   718.206] (WW) Falling back to old probe method for modesetting
[   718.206] (EE) open /dev/dri/card0: No such file or directory
[   718.206] (WW) Falling back to old probe method for fbdev
[   718.206] (II) Loading sub module "fbdevhw"
[   718.206] (II) LoadModule: "fbdevhw"
[   718.206] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   718.207] (II) Module fbdevhw: vendor="X.Org Foundation"
[   718.207] 	compiled for 1.15.1, module version = 0.0.2
[   718.207] 	ABI class: X.Org Video Driver, version 15.0
[   718.207] (EE) open /dev/fb0: No such file or directory
[   718.207] (WW) Falling back to old probe method for vesa
[   718.207] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   718.207] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   718.207] (==) NVIDIA(0): RGB weight 888
[   718.207] (==) NVIDIA(0): Default visual is TrueColor
[   718.207] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   718.207] (**) NVIDIA(0): Enabling 2D acceleration
[   718.233] (II) NVIDIA(GPU-0): Display (HP 2159 (DFP-0)) does not support NVIDIA 3D Vision
[   718.234] (II) NVIDIA(GPU-0):     stereo.
[   718.235] (II) NVIDIA(0): NVIDIA GPU GeForce 9100 (C77) at PCI:2:0:0 (GPU-0)
[   718.235] (--) NVIDIA(0): Memory: 524288 kBytes
[   718.235] (--) NVIDIA(0): VideoBIOS: 62.77.3c.00.04
[   718.235] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   718.236] (--) NVIDIA(0): Valid display device(s) on GeForce 9100 at PCI:2:0:0
[   718.236] (--) NVIDIA(0):     CRT-0
[   718.236] (--) NVIDIA(0):     HP 2159 (DFP-0) (connected)
[   718.236] (--) NVIDIA(0): CRT-0: 300.0 MHz maximum pixel clock
[   718.236] (--) NVIDIA(0): HP 2159 (DFP-0): 165.0 MHz maximum pixel clock
[   718.236] (--) NVIDIA(0): HP 2159 (DFP-0): Internal Single Link TMDS
[   718.236] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   718.236] (**) NVIDIA(0):     device HP 2159 (DFP-0) (Using EDID frequencies has been
[   718.236] (**) NVIDIA(0):     enabled on all display devices.)
[   718.238] (==) NVIDIA(0): 
[   718.238] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   718.238] (==) NVIDIA(0):     will be used as the requested mode.
[   718.238] (==) NVIDIA(0): 
[   718.238] (II) NVIDIA(0): Validated MetaModes:
[   718.238] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[   718.238] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[   718.266] (--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
[   718.266] (--) NVIDIA(0):     option
[   718.266] (II) UnloadModule: "nouveau"
[   718.266] (II) Unloading nouveau
[   718.266] (II) UnloadModule: "modesetting"
[   718.266] (II) Unloading modesetting
[   718.266] (II) UnloadModule: "fbdev"
[   718.266] (II) Unloading fbdev
[   718.266] (II) UnloadSubModule: "fbdevhw"
[   718.266] (II) Unloading fbdevhw
[   718.266] (II) UnloadModule: "vesa"
[   718.266] (II) Unloading vesa
[   718.266] (--) Depth 24 pixmap format is 32 bpp
[   718.267] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   718.270] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[   718.306] Loading extension NV-GLX
[   718.329] (==) NVIDIA(0): Disabling shared memory pixmaps
[   718.329] (==) NVIDIA(0): Backing store enabled
[   718.329] (==) NVIDIA(0): Silken mouse enabled
[   718.330] (==) NVIDIA(0): DPMS enabled
[   718.330] Loading extension NV-CONTROL
[   718.330] Loading extension XINERAMA
[   718.330] (II) Loading sub module "dri2"
[   718.330] (II) LoadModule: "dri2"
[   718.330] (II) Module "dri2" already built-in
[   718.330] (II) NVIDIA(0): [DRI2] Setup complete
[   718.330] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   718.330] (--) RandR disabled
[   718.335] (II) SELinux: Disabled on system
[   718.336] (II) Initializing extension GLX
[   718.348] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   718.351] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   718.351] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   718.351] (II) LoadModule: "evdev"
[   718.351] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   718.351] (II) Module evdev: vendor="X.Org Foundation"
[   718.351] 	compiled for 1.15.0, module version = 2.8.2
[   718.351] 	Module class: X.Org XInput Driver
[   718.351] 	ABI class: X.Org XInput driver, version 20.0
[   718.351] (II) Using input driver 'evdev' for 'Power Button'
[   718.351] (**) Power Button: always reports core events
[   718.351] (**) evdev: Power Button: Device: "/dev/input/event1"
[   718.351] (--) evdev: Power Button: Vendor 0 Product 0x1
[   718.351] (--) evdev: Power Button: Found keys
[   718.351] (II) evdev: Power Button: Configuring as keyboard
[   718.351] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   718.351] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   718.351] (**) Option "xkb_rules" "evdev"
[   718.351] (**) Option "xkb_model" "pc105"
[   718.352] (**) Option "xkb_layout" "us"
[   718.352] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[   718.353] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[   718.354] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   718.354] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   718.354] (II) Using input driver 'evdev' for 'Video Bus'
[   718.354] (**) Video Bus: always reports core events
[   718.354] (**) evdev: Video Bus: Device: "/dev/input/event5"
[   718.354] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   718.354] (--) evdev: Video Bus: Found keys
[   718.354] (II) evdev: Video Bus: Configuring as keyboard
[   718.354] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:16/LNXVIDEO:00/input/input8/event5"
[   718.354] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   718.354] (**) Option "xkb_rules" "evdev"
[   718.354] (**) Option "xkb_model" "pc105"
[   718.354] (**) Option "xkb_layout" "us"
[   718.354] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[   718.354] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   718.354] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   718.354] (II) Using input driver 'evdev' for 'Power Button'
[   718.354] (**) Power Button: always reports core events
[   718.354] (**) evdev: Power Button: Device: "/dev/input/event0"
[   718.354] (--) evdev: Power Button: Vendor 0 Product 0x1
[   718.354] (--) evdev: Power Button: Found keys
[   718.354] (II) evdev: Power Button: Configuring as keyboard
[   718.354] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   718.354] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[   718.354] (**) Option "xkb_rules" "evdev"
[   718.354] (**) Option "xkb_model" "pc105"
[   718.354] (**) Option "xkb_layout" "us"
[   718.354] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[   718.355] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1020 (/dev/input/event2)
[   718.355] (**) Logitech Unifying Device. Wireless PID:1020: Applying InputClass "evdev pointer catchall"
[   718.355] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1020'
[   718.355] (**) Logitech Unifying Device. Wireless PID:1020: always reports core events
[   718.355] (**) evdev: Logitech Unifying Device. Wireless PID:1020: Device: "/dev/input/event2"
[   718.355] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Vendor 0x46d Product 0xc52b
[   718.355] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Found 20 mouse buttons
[   718.355] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Found scroll wheel(s)
[   718.355] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Found relative axes
[   718.355] (--) evdev: Logitech Unifying Device. Wireless PID:1020: Found x and y relative axes
[   718.355] (II) evdev: Logitech Unifying Device. Wireless PID:1020: Configuring as mouse
[   718.355] (II) evdev: Logitech Unifying Device. Wireless PID:1020: Adding scrollwheel support
[   718.355] (**) evdev: Logitech Unifying Device. Wireless PID:1020: YAxisMapping: buttons 4 and 5
[   718.355] (**) evdev: Logitech Unifying Device. Wireless PID:1020: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   718.355] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.4/3-2.4:1.2/0003:046D:C52B.0003/input/input5/event2"
[   718.355] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1020" (type: MOUSE, id 9)
[   718.355] (II) evdev: Logitech Unifying Device. Wireless PID:1020: initialized for relative axes.
[   718.355] (**) Logitech Unifying Device. Wireless PID:1020: (accel) keeping acceleration scheme 1
[   718.355] (**) Logitech Unifying Device. Wireless PID:1020: (accel) acceleration profile 0
[   718.355] (**) Logitech Unifying Device. Wireless PID:1020: (accel) acceleration factor: 2.000
[   718.355] (**) Logitech Unifying Device. Wireless PID:1020: (accel) acceleration threshold: 4
[   718.356] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1020 (/dev/input/mouse0)
[   718.356] (II) No input driver specified, ignoring this device.
[   718.356] (II) This device may have been added with another device file.
[   718.356] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4004 (/dev/input/event3)
[   718.356] (**) Logitech Unifying Device. Wireless PID:4004: Applying InputClass "evdev keyboard catchall"
[   718.356] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:4004'
[   718.356] (**) Logitech Unifying Device. Wireless PID:4004: always reports core events
[   718.356] (**) evdev: Logitech Unifying Device. Wireless PID:4004: Device: "/dev/input/event3"
[   718.356] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Vendor 0x46d Product 0xc52b
[   718.356] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found 1 mouse buttons
[   718.356] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found scroll wheel(s)
[   718.356] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found relative axes
[   718.356] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Forcing relative x/y axes to exist.
[   718.356] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found absolute axes
[   718.356] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Forcing absolute x/y axes to exist.
[   718.356] (--) evdev: Logitech Unifying Device. Wireless PID:4004: Found keys
[   718.356] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Configuring as mouse
[   718.356] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Configuring as keyboard
[   718.356] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Adding scrollwheel support
[   718.356] (**) evdev: Logitech Unifying Device. Wireless PID:4004: YAxisMapping: buttons 4 and 5
[   718.356] (**) evdev: Logitech Unifying Device. Wireless PID:4004: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   718.356] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.4/3-2.4:1.2/0003:046D:C52B.0003/input/input6/event3"
[   718.356] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:4004" (type: KEYBOARD, id 10)
[   718.356] (**) Option "xkb_rules" "evdev"
[   718.356] (**) Option "xkb_model" "pc105"
[   718.356] (**) Option "xkb_layout" "us"
[   718.356] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[   718.356] (II) evdev: Logitech Unifying Device. Wireless PID:4004: initialized for relative axes.
[   718.356] (WW) evdev: Logitech Unifying Device. Wireless PID:4004: ignoring absolute axes.
[   718.357] (**) Logitech Unifying Device. Wireless PID:4004: (accel) keeping acceleration scheme 1
[   718.357] (**) Logitech Unifying Device. Wireless PID:4004: (accel) acceleration profile 0
[   718.357] (**) Logitech Unifying Device. Wireless PID:4004: (accel) acceleration factor: 2.000
[   718.357] (**) Logitech Unifying Device. Wireless PID:4004: (accel) acceleration threshold: 4
[   718.357] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101f (/dev/input/event4)
[   718.357] (**) Logitech Unifying Device. Wireless PID:101f: Applying InputClass "evdev pointer catchall"
[   718.357] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101f'
[   718.357] (**) Logitech Unifying Device. Wireless PID:101f: always reports core events
[   718.357] (**) evdev: Logitech Unifying Device. Wireless PID:101f: Device: "/dev/input/event4"
[   718.357] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Vendor 0x46d Product 0xc52b
[   718.357] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Found 20 mouse buttons
[   718.357] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Found scroll wheel(s)
[   718.357] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Found relative axes
[   718.357] (--) evdev: Logitech Unifying Device. Wireless PID:101f: Found x and y relative axes
[   718.357] (II) evdev: Logitech Unifying Device. Wireless PID:101f: Configuring as mouse
[   718.357] (II) evdev: Logitech Unifying Device. Wireless PID:101f: Adding scrollwheel support
[   718.357] (**) evdev: Logitech Unifying Device. Wireless PID:101f: YAxisMapping: buttons 4 and 5
[   718.357] (**) evdev: Logitech Unifying Device. Wireless PID:101f: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   718.357] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2.4/3-2.4:1.2/0003:046D:C52B.0003/input/input7/event4"
[   718.357] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101f" (type: MOUSE, id 11)
[   718.357] (II) evdev: Logitech Unifying Device. Wireless PID:101f: initialized for relative axes.
[   718.357] (**) Logitech Unifying Device. Wireless PID:101f: (accel) keeping acceleration scheme 1
[   718.357] (**) Logitech Unifying Device. Wireless PID:101f: (accel) acceleration profile 0
[   718.357] (**) Logitech Unifying Device. Wireless PID:101f: (accel) acceleration factor: 2.000
[   718.357] (**) Logitech Unifying Device. Wireless PID:101f: (accel) acceleration threshold: 4
[   718.358] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101f (/dev/input/mouse1)
[   718.358] (II) No input driver specified, ignoring this device.
[   718.358] (II) This device may have been added with another device file.
[   718.358] (II) config/udev: Adding input device HDA NVidia Rear Mic (/dev/input/event12)
[   718.358] (II) No input driver specified, ignoring this device.
[   718.358] (II) This device may have been added with another device file.
[   718.358] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event11)
[   718.358] (II) No input driver specified, ignoring this device.
[   718.358] (II) This device may have been added with another device file.
[   718.358] (II) config/udev: Adding input device HDA NVidia Line Out Front (/dev/input/event10)
[   718.358] (II) No input driver specified, ignoring this device.
[   718.358] (II) This device may have been added with another device file.
[   718.358] (II) config/udev: Adding input device HDA NVidia Line Out Surround (/dev/input/event9)
[   718.358] (II) No input driver specified, ignoring this device.
[   718.358] (II) This device may have been added with another device file.
[   718.358] (II) config/udev: Adding input device HDA NVidia Line Out CLFE (/dev/input/event8)
[   718.358] (II) No input driver specified, ignoring this device.
[   718.358] (II) This device may have been added with another device file.
[   718.359] (II) config/udev: Adding input device HDA NVidia Line Out Side (/dev/input/event7)
[   718.359] (II) No input driver specified, ignoring this device.
[   718.359] (II) This device may have been added with another device file.
[   718.359] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event6)
[   718.359] (II) No input driver specified, ignoring this device.
[   718.359] (II) This device may have been added with another device file.
[   718.359] (II) config/udev: Adding input device HDA NVidia Front Mic (/dev/input/event13)
[   718.359] (II) No input driver specified, ignoring this device.
[   718.359] (II) This device may have been added with another device file.
[   719.553] (II) NVIDIA(GPU-0): Display (HP 2159 (DFP-0)) does not support NVIDIA 3D Vision
[   719.553] (II) NVIDIA(GPU-0):     stereo.
[   719.553] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   719.553] (**) NVIDIA(0):     device HP 2159 (DFP-0) (Using EDID frequencies has been
[   719.553] (**) NVIDIA(0):     enabled on all display devices.)
[   720.556] (II) NVIDIA(GPU-0): Display (HP 2159 (DFP-0)) does not support NVIDIA 3D Vision
[   720.556] (II) NVIDIA(GPU-0):     stereo.
[   720.556] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   720.556] (**) NVIDIA(0):     device HP 2159 (DFP-0) (Using EDID frequencies has been
[   720.556] (**) NVIDIA(0):     enabled on all display devices.)
[   732.700] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   735.284] (II) NVIDIA(GPU-0): Display (HP 2159 (DFP-0)) does not support NVIDIA 3D Vision
[   735.284] (II) NVIDIA(GPU-0):     stereo.
[   735.284] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   735.284] (**) NVIDIA(0):     device HP 2159 (DFP-0) (Using EDID frequencies has been
[   735.284] (**) NVIDIA(0):     enabled on all display devices.)
[   736.302] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   736.338] (II) NVIDIA(GPU-0): Display (HP 2159 (DFP-0)) does not support NVIDIA 3D Vision
[   736.338] (II) NVIDIA(GPU-0):     stereo.
[   736.338] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   736.338] (**) NVIDIA(0):     device HP 2159 (DFP-0) (Using EDID frequencies has been
[   736.338] (**) NVIDIA(0):     enabled on all display devices.)
[   736.343] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   736.349] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   736.355] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   736.420] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   736.428] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[   736.431] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[   736.449] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[   736.485] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[   737.256] (II) NVIDIA(GPU-0): Display (HP 2159 (DFP-0)) does not support NVIDIA 3D Vision
[   737.256] (II) NVIDIA(GPU-0):     stereo.
[   737.256] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   737.256] (**) NVIDIA(0):     device HP 2159 (DFP-0) (Using EDID frequencies has been
[   737.256] (**) NVIDIA(0):     enabled on all display devices.)
[   738.508] (II) XKB: reuse xkmfile /var/lib/xkb/server-1908D3BB0224FA577B58A32F49D8B4107F7BAFFD.xkm
[   746.134] (II) Server zapped. Shutting down.
[   746.402] (II) evdev: Logitech Unifying Device. Wireless PID:101f: Close
[   746.402] (II) UnloadModule: "evdev"
[   746.402] (II) evdev: Logitech Unifying Device. Wireless PID:4004: Close
[   746.402] (II) UnloadModule: "evdev"
[   746.402] (II) evdev: Logitech Unifying Device. Wireless PID:1020: Close
[   746.402] (II) UnloadModule: "evdev"
[   746.402] (II) evdev: Power Button: Close
[   746.402] (II) UnloadModule: "evdev"
[   746.402] (II) evdev: Video Bus: Close
[   746.402] (II) UnloadModule: "evdev"
[   746.403] (II) evdev: Power Button: Close
[   746.403] (II) UnloadModule: "evdev"
[   746.573] (EE) Server terminated successfully (0). Closing log file. 
```

Whaddya think?  I'm ready to just hang this up as just not worth it.  Nouveau works pretty good though but noticeably substandard to 304.  Sure would like 340 as not only does NVIDIA list it as correct for both my cards but the listed enhancements over 304 sound promising as far as overall features as well as lowering operating temp under load.

gt

---

### Post by garyt53 on 2015-10-04
Have tried all the conflicting suggested methods, even with .run file, and all end up with cycling horizhold then shortly thereafter, BSOL (black screen of limbo). ha

---

### Post by garyt53 on 2015-10-04
Oh, yeah.....didn't blacklist Nouveau and had a helluva issue with libcuda1-304 being thrashed but found a straightforward solution to that conundrum.

---

### Post by garyt53 on 2015-10-06
Have exhausted all conflicting "solutions" on the web, all resulting in the same driver failure.  I have both x-swat and xorg PPAs installed, purged both with lightdm off and tried with just xorg.....even tried to install the .run driver file and no go.  And recovery-boot options would not work.  Nor would the Additional Drivers utility.  I did get that to download the selected driver after changing my download source to Ubuntu Main, but it would not install.  But the nouveau driver works.  Checked under stress nearly as good as NVIDIA-304 actually, but the overheating issue of the integral NVIDIA 9100 cheapo GPU was worse. 

This thread goes nowhere.  So lets do everybody a favor and remove it from the portal....or label it "Not Solved", or at the very least don't label it "Solved".  I know many others have issues with NVIDIA drivers on 14.04 LTS amd64 and and I do not want to wast their time here even though I am sure almost all have just opted to reset the graphics driver on a fresh install.  Not an option for me.

gt

---

