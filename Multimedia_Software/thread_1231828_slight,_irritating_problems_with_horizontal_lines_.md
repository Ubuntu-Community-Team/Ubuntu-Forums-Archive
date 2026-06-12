---
title: "slight, irritating problems with horizontal lines in video"
date: 2009-08-04
forum: Multimedia Software
---

### Post by wickstopher on 2009-08-04
I've never been able to get video to look quite right on Ubuntu.  There have always been horizontal lines flashing accross the screen at semi-frequent intervals while watching video.  This is regardless of whether or not the screen is composited (i.e. compiz) or not (no compiz).  My current graphics card is an XFX nVidia 8600GTX with 256MB RAM, and the processer is a Core 2 Duo E6750 running at 2.66 GHz.  I'm using Envy-installed nVidia drivers for the card in Ubuntu.  I dual boot with Windows XP, and the problem is nonexistent on my Windows partition on the same machine.  It doesn't render anything unwatchable, but it is rather annoying once you notice it, and it is noticeable.  It may also be noteworthy that the Linux version of World of Goo (the only real game I have for Linux) also has the same problem.  Again, it is not rendered unplayable, unenjoyable or unappreciable,  but on the Windows version the graphics are as smooth as butter on the same machine.  It may also be worth noting that I've noticed similar problems on a machine that I built for a friend using a Shuttle kit with integrated Intel GMA 950 graphics and open source drivers.

I haven't seen any other mention of this problem on the forums...it's not as extreme as the "tearing" I've seen described.  So, I'm curious.

a) Has anyone else out there experienced similar issues?

b) Has anyone else out there found a solution?  if not, let your voice be heard...we need to get this fixed!

Thanks for any help!

---

### Post by wickstopher on 2009-08-05
Hmm..I think today's xkcd might be about my exact problem. :)

[http://xkcd.com/619/](http://xkcd.com/619/)

---

### Post by wickstopher on 2009-08-13
bump!

---

### Post by bobince on 2009-08-13
Screenshot? It sounds like you are talking about tearing, but then you say it's not? :confused:

---

### Post by wickstopher on 2009-08-13
I doubt if I could get a screenshot.  Like I said, it's very slight and it happens quickly.

---

### Post by mc4man on 2009-08-13
I think I've noticed the same thing, harder to describe than to notice, only 'appears' for a fraction of a sec.

It seemed less prevalent in hardy vs. intrepid and jaunty, though apparent in all.

I think it's related (here at least),  to vsync and on multiple hardware (from what were once high end p4's to recent core2duo, all with nvidia) have resolved and playback is comparable to xp, vista.

(( though have returned most installs to a modded hardy, one with intrepid till karmic is a bit further along.

While what I saw wasn't only confined to high action scenes, it was more likely to occur in them (when combined with fast camera angle changes, panning

I settled on a scene from " Quantum of Solace" for testing _ the chase scene in chapter 3 has a least 6-10 moments where 'artifacts' would occur


To resolve here
In nvidia-Xserver-settings enabled "Sync to VBlank" both in the Xvideo settings and the OpenGl settings.
In compizconfig .... general options unchecked "Unredirect Fullscreen Windows" and under the display settings tab also enabled sync to vblank and set texture filter to best
(plus set refresh rate in compiz, though probably not a factor 

No longer have any issues with any video (whether dvd's or video's from normal def. to HD

(( the hardy installs are using the 169.xx driver, the intrepid the 185.xx

Maybe the same issue you have, maybe not, if you have access to that dvd it's an excellent scene to test and or confirm 'issue'

(( or if you have a scene available via dvd or else-where mention if possible

---

### Post by wickstopher on 2009-08-14
Wow, thanks.  This seems to have worked.  As you mentioned, the problem is elusive and hard to descriptively pin down (at times I thought I was imagining it, which is why I kept putting off this post).  I had actually done everything you mentioned, as it was mentioned in a different thread, EXCEPT for the whole sync to vblank in compizconfig, and apparently that was the missing factor.  I'll wait to mark this thread as solved for a week or so, because I'm still somewhat in a state of shock and disbelief.

---

### Post by kanamor on 2010-01-22
Thank you very much mc4man!!! Now works fine!

---

### Post by sports.car.guy on 2010-01-22
> **wickstopher said:**
> Hmm..I think today's xkcd might be about my exact problem. :)

[http://xkcd.com/619/](http://xkcd.com/619/)


That flash comic you refer to has nothing to do with the Linux community and whoever wrote that comic is obviously from the Windows world blaming Linux for bad Flash playback..lol. 

If they were from the Linux world they would know Flash sucking at playback on Linux has nothing to do with it. It is all Adobe and not caring to actually make it work right.

Gnash which is developed by the open source and Linux communities, file for file puts Adobe to shame, fully supports version 7 with support for a lot of features in newer versions. It even has an AV-API interface to allow for several GPU brands to take advantage of hardware acceleration.

---

### Post by zovalik on 2010-04-21
I have the same problem on my 10.04 (also in 9.10) but I have ATI card (Dell 1555, Mobility Radeon 4500 series). I'm using fglrx. 
Anyone know how resolve this problem for my configuration? ( sory for my english...)

---

### Post by sa7ish on 2010-05-01
Thank you for the information :). I too had the same problem. After enabling sync feature in compiz i no longer get the Horizontal tearing.

---

### Post by srg84 on 2010-05-06
The Compiz solutions works, but i don´t like Desktop Effects.

¿Is there a way to fix it without activating Compiz, or at least only activating Metacity Composition manager?

gconftool-2 --type bool --set /apps/metacity/general/compositing_manager true

---

### Post by Stig1959 on 2010-08-02
Thank you , Thank you , Thank you!

You have solved a problem that has been bugging me for months. Now I no longer need a dual boot set up. 

Again, thank you for your help.

Stig1959

---

### Post by dmemt on 2010-08-30
Simply disabling Visual Effects seems to have taken care of the problem for me.

Details: 10.04. Not running Compiz. VLC. Integrated Nvidia 8200 graphics. Quad core Phenom. HP w2207h monitor @ 1680x1050.

As for 'why' desktop visual effects would affect playback in full screen mode, I have no clue. Tried lots of setting and sync type changes, but nothing helped. Stumbled across the Visual Effects solution: System > Preferences > Appearance > [Visual Effects] > (None) in a post somewhere and no more tearing!

Just thought I'd share.

Dana

---

### Post by tiosus on 2010-10-08
> **mc4man said:**
> I think I've noticed the same thing, harder to describe than to notice, only 'appears' for a fraction of a sec.

It seemed less prevalent in hardy vs. intrepid and jaunty, though apparent in all.

I think it's related (here at least),  to vsync and on multiple hardware (from what were once high end p4's to recent core2duo, all with nvidia) have resolved and playback is comparable to xp, vista.

(( though have returned most installs to a modded hardy, one with intrepid till karmic is a bit further along.

While what I saw wasn't only confined to high action scenes, it was more likely to occur in them (when combined with fast camera angle changes, panning

I settled on a scene from " Quantum of Solace" for testing _ the chase scene in chapter 3 has a least 6-10 moments where 'artifacts' would occur


To resolve here
In nvidia-Xserver-settings enabled "Sync to VBlank" both in the Xvideo settings and the OpenGl settings.
In compizconfig .... general options unchecked "Unredirect Fullscreen Windows" and under the display settings tab also enabled sync to vblank and set texture filter to best
(plus set refresh rate in compiz, though probably not a factor 

No longer have any issues with any video (whether dvd's or video's from normal def. to HD

(( the hardy installs are using the 169.xx driver, the intrepid the 185.xx

Maybe the same issue you have, maybe not, if you have access to that dvd it's an excellent scene to test and or confirm 'issue'

(( or if you have a scene available via dvd or else-where mention if possible
wooooooooooooooooooooooooooooooow
full answer work greate tanx!!!!!!!!!!!:popcorn:

---

### Post by ashfallen0 on 2010-10-10
So, either "NVIDIA" or "The Allmighty Google" has failed here.  

Symptom Backtrace:

Dell XPS M1730, Dual 9800M GTX in AFR SLI

Video output to Samsung 52" LED 120Hz@ 1920x1080

Ubuntu 10.04 Installed on Kingston 4GB USB Keydrive,

Nvidia 195.36.24 drivers

Compiz Enabled

Sync to Vblank enabled in NVIDIA, COMPIZ, VLC, 

Have tried every config tweak available off T.A.G,
and off of these forums.

Seems to be a problem with filter sort order though, as the 2:3 pulldown scanlines are appearing only on upper half of fullscreen image.

Have been trying since RedHat 5 to get video to display fullscreen properly in linux of any flavor.

This is the ONLY reason I don't swap to ubuntu full-time.  I can live with Wine Gaming, configs through terminal, and the "less than stellar" hardware adoption curve for drivers. But seriously, can't we get this knocked out, LIKE IT WAS FOR WINDOWS 95?  

off to boot back into Win7Ultx64 to watch my videos.

---

### Post by korg91 on 2010-12-27
Thank you very much mc4man, that works perfectly!

> **sports.car.guy said:**
> That flash comic you refer to has nothing to do with the Linux community and whoever wrote that comic is obviously from the Windows world blaming Linux for bad Flash playback..lol. 

If they were from the Linux world they would know Flash sucking at playback on Linux has nothing to do with it. It is all Adobe and not caring to actually make it work right.

Gnash which is developed by the open source and Linux communities, file for file puts Adobe to shame, fully supports version 7 with support for a lot of features in newer versions. It even has an AV-API interface to allow for several GPU brands to take advantage of hardware acceleration.

[OT]
@sports.car.guy

I really don't think that xkcd creator is "from the Windows world".

Maybe you (and every unix user) should take a look at this: [http://uni.xkcd.com/]("http://uni.xkcd.com/")

Anyway, it's true that Flash playback on linux sucks, even if it's Adobe's fault.

The only pc I saw with linux and decent flash playback (on a 24" 1920x1200 display) is mine, and it has a Core 2 E8500@3.17 GHz and an nVidia GTX460 :)

And note that I also had to enable video acceleration with this:

```
sudo su
mkdir /etc/adobe
echo OverrideGPUValidation=true > /etc/adobe/mms.cfg

```

[/OT]

---

### Post by dsevastakis on 2011-03-22
i've had this problem as well since ubuntu 8.10 with twinview, using nVidia drivers.. using Gnome/KDE/Gnome-shell, compiz/mutter, with/without effects, Sync to Vblank enables everywhere.. tearing still here.. i hate switching to windows to watch movies..:/

---

