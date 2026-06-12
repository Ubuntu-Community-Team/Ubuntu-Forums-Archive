---
title: "Is maverick going to fix the horrible plymouth for nvidia?"
date: 2010-05-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Speed_arg on 2010-05-28
I just wanted to know if this is planned, sorry I couldn't find anywhere the to-do list.

---

### Post by dino99 on 2010-05-28
hey, plymouth is a young boy  :P

---

### Post by MacUntu on 2010-05-28
[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-grub2-boot-framebuffer](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-grub2-boot-framebuffer)

---

### Post by ranch hand on 2010-05-28
> **dino99 said:**
> hey, plymouth is a young boy  :P
Plymouth has been around for years and has never worked universally.

It works great on some, if not most, hardware.  The problem is that it just will not work on others.

As it is patched (it is more patches than anythng else) to fix some thing for one group of boxes it make things worse for others.

This does get it to work for more people.  It also completely excludes others from using it.

Those folks are not happy.

The best way to fix it is to jack it up and back something else under it.

---

### Post by Macchia on 2010-05-28
> **ranch hand said:**
> Plymouth has been around for years and has never worked universally.

It works great on some, if not most, hardware.  The problem is that it just will not work on others.

As it is patched (it is more patches than anythng else) to fix some thing for one group of boxes it make things worse for others.

This does get it to work for more people.  It also completely excludes others from using it.

Those folks are not happy.

The best way to fix it is to jack it up and back something else under it.

The best way, until fixed, should be the possibility to remove it imho.

---

### Post by ranch hand on 2010-05-28
> **Macchia said:**
> The best way, until fixed, should be the possibility to remove it imho.
I haven't had time to finish it but I have 3 installs of 9.10 (copies of each other) that I am going to;
#1>leave as 9.10
#2>upgrade to 10.04
#3>try to turn into 10.04 with out loosing usplash/xsplash and not installing plymouth et al.

I have them on a separate drive with bootchart installed.  I have the list of packages to be upgraded and the ones that you need to run dist-upgrade to get.  Those lists are separated alpha-numerically in a gedit file for me to study up on for the proposed 10.04 with xsplash.

If it works I want to see what the thing acts like.

We need some one with enough knowledge to do this right.

This is just the only thing I can think of that I can do.

---

### Post by tokyobadger on 2010-05-28
> **Speed_arg said:**
> Is maverick going to fix the horrible plymouth for nvidia?
I use a GTS 250, the nvidia drivers (195.36.24) on amd64, have a resolution of 2560x1600, and I see purple background, white text (at proportionate size and crisp definition), and a progression of white dots turning red at boot and shutdown. I understood this to be the Lucid implementation of plymouth.

Could you define the problem you're having?

---

### Post by TerminX on 2010-05-28
Unfortunately, someone had the horrible idea of making this premature piece of crap a dependency of mountall, making it impossible to properly remove.

It's really disappointing to see decent software devs focus on useless crap like a fancy bootscreen instead of stability or stuff that actually affects the desktop in a positive way.

Who knows how much time has been completely wasted tying to work out problems with the daemon that serves no purpose other than showing you an animated picture while your system boots.

---

### Post by philinux on 2010-05-28
> **tokyobadger said:**
> I use a GTS 250, the nvidia drivers (195.36.24) on amd64, have a resolution of 2560x1600, and I see purple background, white text (at proportionate size and crisp definition), and a progression of white dots turning red at boot and shutdown. I understood this to be the Lucid implementation of plymouth.

Could you define the problem you're having?

Bootup/Plymouth.
Users should experience a much faster boot however some users may experience problems with Plymouth after the nVidia graphics driver has been enabled. Users may experience plymouth using lower graphics resolution.
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013](https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013)

---

### Post by tokyobadger on 2010-05-28
We don't know from the OP what precisely his/her 'horrible plymouth for nvidia' problem is. Granted, it is likely to be what you describe, but as a member of the forums staff, surely you'd want to advocate more informative / less emotional posts. Stating anger/frustration/dissatisfaction doesn't contribute to solving problems.

---

### Post by Merovius on 2010-05-28
For me at least, on two separate machines it does not work all that well. On my laptop it seems to run as expected after a black screen with blinking cursor for 15 seconds, but the graphics are awful. (Dell D600) On my other machine with 8600GT video and an upgrade from Karmic I get a hybrid Lucid / Karmic boot and a flickery but fast shutdown.

My personal opinion is that the Karmic boot was *much* nicer.

---

### Post by philinux on 2010-05-28
> **tokyobadger said:**
> We don't know from the OP what precisely his/her 'horrible plymouth for nvidia' problem is. Granted, it is likely to be what you describe, but as a member of the forums staff, surely you'd want to advocate more informative / less emotional posts. Stating anger/frustration/dissatisfaction doesn't contribute to solving problems.

That extract above is from the General Help forum sticky re lucid.

I have the same problem and I'm frustrated with it. But I'm leaving as is to see if a fix comes through. It's not a big deal.
**nVidia 8600GT**

---

### Post by cascade9 on 2010-05-28
> **TerminX said:**
> Unfortunately, someone had the horrible idea of making this premature piece of crap a dependency of mountall, making it impossible to properly remove.

It's really disappointing to see decent software devs focus on useless crap like a fancy bootscreen instead of stability or stuff that actually affects the desktop in a positive way.

Who knows how much time has been completely wasted tying to work out problems with the daemon that serves no purpose other than showing you an animated picture while your system boots.

Well, that explains why I was having serious problems tring to remove plymouth on a friends machine :| 

I pretty much agree with your (harshly worded) assesment, but eyecandy for the masses, you know....

---

### Post by wayneericgouin on 2010-05-28
/agree 
I have Plymouth working as intended by forcing the use of a framebuffer, but should I really have to do all that just to make my bootup visuals look decent.

---

### Post by screaminj3sus on 2010-05-28
I get full resolution Plymouth with open source ati drivers, but problem is I literally see it for half a second. The whole damn boot is a blinking cursor and than Plymouth comes up for half a second and fades into the login screen. A boot slash seems pointless if it comes up so late in boot.

---

### Post by philinux on 2010-05-28
> **screaminj3sus said:**
> I get full resolution Plymouth with open source ati drivers, but problem is I literally see it for half a second. The whole damn boot is a blinking cursor and than Plymouth comes up for half a second and fades into the login screen. A boot slash seems pointless if it comes up so late in boot.

That is part of the problem defined in the General Help forum sticky. There is a work around there too.

I get the same as you but a low res blocky image.

---

### Post by Macchia on 2010-05-28
i can't even ctrl-alt-f[1-9] because i can't see the cursor.

---

### Post by ranch hand on 2010-05-28
> **tokyobadger said:**
> We don't know from the OP what precisely his/her 'horrible plymouth for nvidia' problem is. Granted, it is likely to be what you describe, but as a member of the forums staff, surely you'd want to advocate more informative / less emotional posts. Stating anger/frustration/dissatisfaction doesn't contribute to solving problems.
We are into the second release with plymouth.  It has gotten progressively worse.  I have, for instance, wonderful boot times of over a minute and shut down times (shen it will shut down at all that take several minutes.

As folks who like Ubuntu well enough to do testing you can be damned sure that we are a little emotional about having this piece of crap on here.

---

### Post by ronacc on 2010-05-28
I don't mind them trying out stuff like this I DO MIND them making it a dependency of a critical file so that it is hard/impossible to remove when it don't play nice with your rig(s) ( 4 boxes all Nvidia ).

---

### Post by dyltman on 2010-05-28
> **philinux said:**
> That is part of the problem defined in the General Help forum sticky. There is a work around there too.

I get the same as you but a low res blocky image.

this is what I get, low res blocky image and 1-2 seconds of it. The rest is the blinking thing

---

### Post by philinux on 2010-05-28
> **dyltman said:**
> this is what I get, low res blocky image and 1-2 seconds of it. The rest is the blinking thing

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by nanog on 2010-05-28
Plymouth is a project that is intended to work well with libre open source drivers. IME, it works fine with nouveau in fedora and ubuntu. Perhaps it would have been better if  xsplash was kept for blob users - but this creates necessary dependencies and significantly complicates developers work. The blob must die!

---

### Post by ranch hand on 2010-05-28
> **nanog said:**
> Plymouth is a project that is intended to work well with libre open source drivers. IME, it works fine with nouveau in fedora and ubuntu. Perhaps it would have been better if  xsplash was kept for blob users - but this creates necessary dependencies and significantly complicates developers work. The blob must die!
That is nice.

I am using the OSS ATI driver.  It does not work for that either.  Not in Ubuntu.  It does not work in Fedora either.

As a matter of fact it works much better in Ubuntu if you call a minute to boot and 3 minutes (if you are lucky) for it to shut down, always with the message;
shutting down main plymouth process with kill command                            [Fail]

What a wonderful piece of  crap.

---

### Post by ronacc on 2010-05-28
> **nanog said:**
> Plymouth is a project that is intended to work well with libre open source drivers. IME, it works fine with nouveau in fedora and ubuntu. Perhaps it would have been better if  xsplash was kept for blob users - but this creates necessary dependencies and significantly complicates developers work. The blob must die!

If they block installation of the blob like they did once before , prior to the Nouveau or some other open source driver providing ALL of the functionality of the blob, many people myself included will be very upset . I am the final arbiter of what will be installed on my system not some "holier than thou "  " true believer " .

---

### Post by ranch hand on 2010-05-28
> **ronacc said:**
> If they block installation of the blob like they did once before , prior to the Nouveau or some other open source driver providing ALL of the functionality of the blob, many people myself included will be very upset . I am the final arbiter of what will be installed on my system not some "holier than thou "  " true believer " .
Unfortunately we seem to be suffering through a period of "true believer" fan boys in development right now.

In Kubuntu anyone that wants a gui for package management has installed synaptic to "correct" that wonderful idea packagekit (properly spelled for Kubuntu it should be Kpackagekrap).

And of coarse we all get the wonders of plymouth.

Hey, come on, Fedora uses it.  Wow, I am impressed.

Truly I am impressed.  I never said it was a positive impression.

---

### Post by wayneericgouin on 2010-05-28
I wouldn't mind Plymouth so much even if it didn't work as intended as long as it didn't add an extra minute to my boot process. Not that boot time  makes a huge impact on the systems ability to function but I believe boot time was a priority for Ubuntu.

---

### Post by null_pointer_us on 2010-05-28
The mount-all dependency issue came up during Lucid testing. I removed plymouth in USC, and it took out my system including leaving me no display and grub not being able to find any kernels to boot.

IIRC, it was reported on launchpad and marked as invalid or "won't fix."

Can't you just remove the plymouth theme packages that cause problems for you?

```
aptitude search plymouth-theme
```

Then remove the theme packages. I think the text one is OK if somewhat ugly, but even that one can be removed and you see the dmesg output on startup.

It's a shame that all the nicely formatted and colored boot text from the old Fedora/Mandrake days has gone by the wayside.

---

### Post by ranch hand on 2010-05-28
That helps with the problem of the graphic side of plymouth.  The real problem is not plymouth.  The real problem is at the core and that is libplymouth2 (currently, I am sure we will get another, worse one).

---

### Post by fedexnman on 2010-05-28
plymouth needs to go sorry , ubuntu needs to get back with xsplash or usplash, if you like plymouth great, but if your coming from windows or mac and are trying ubuntu for the first time and have an ati or nvidia gpu, you will be very dissappointed. plymouth is unprofessional looking period, its an embarresment to the ubuntu distro imho.

---

### Post by soapytheclown on 2010-05-28
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

if your desperate for it now, you can do this? tbh its nice but for 5 seconds of seeing my pc turn on / off its not worth it, only thing is that guide doesnt tell you to use your res rather than their one.

---

### Post by ranch hand on 2010-05-28
> **fedexnman said:**
> plymouth needs to go sorry , ubuntu needs to get back with xsplash or usplash, if you like plymouth great, but if your coming from windows or mac and are trying ubuntu for the first time and have an ati or nvidia gpu, you will be very dissappointed. plymouth is unprofessional looking period, its an embarresment to the ubuntu distro imho.
Everything you say is just right.  The sucker is just  shameful thing to saddle an other wise wonderful OS with.

---

### Post by ronacc on 2010-05-28
Although I know Ubuntu detests the Idea of user choice , plymouth is one place where it is sorely needed . If they MUST keep it make it OPTIONAL.

---

### Post by ranch hand on 2010-05-28
> **soapytheclown said:**
> [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

if your desperate for it now, you can do this? tbh its nice but for 5 seconds of seeing my pc turn on / off its not worth it, only thing is that guide doesnt tell you to use your res rather than their one.
That is fairly old news and only of use to people that have nothing to really complain about.  Their boxes boot.

Eye candy is not what 90% of the complaints about plymouth are about.  We want the bugger to work or be replaced so that we can continue to use Ubuntu.

---

### Post by Martin Marshalek on 2010-05-28
While I personally preferred xsplash in Karmic most of all, I think I see what the Ubuntu developers will end up doing. The main problem with Plymouth by default is that, by default, it requires Kernel Mode Setting, a feature not enabled in the restricted drivers. By the time Maverick is released, the new-ish Gallium 3d Nouveau drivers will be much more stable and probably be at least in the repositories. These are open source drivers which, if most of the current bugs are worked out, will play very nicely with Plymouth.

Or Ubuntu users can do what Fedora users did for the last few releases and edit their grub configurations. Now Fedora has open source 3d so the restricted drivers aren't needed unless for games or intense 3d applications. Ubuntu will probably be at this point next release, albeit with a much more stable release of the current Gallium 3d.

---

### Post by seeker5528 on 2010-05-28
> **fedexnman said:**
> plymouth needs to go sorry , ubuntu needs to get back with xsplash or usplash, if you like plymouth great, but if your coming from windows or mac and are trying ubuntu for the first time and have an ati or nvidia gpu, you will be very dissappointed. plymouth is unprofessional looking period, its an embarresment to the ubuntu distro imho.

I would be just as happy without any of that stuff, but plymouth works fine my 3 systems with different generations of ATI cards, all using the open source driver.

I avoid Nvidia video like the plague, so I can't really say anything specific about that other than to point out the open source driver is less mature than ATI and Intel.

In a more general vein, the proprietary drivers have the same problem they have always had, they are behind the curve a bit when it comes to some of their kernel/Xorg support.

That's not to say plymouth couldn't handle some situations more gracefully, but to some extent it is a matter of blacklisting the hardware when it is able to be determined that hardware with a particular hardware ID has an excessively high number of issues.

Later, Seeker

---

### Post by ronacc on 2010-05-28
atleast at the present time plymouth will potentially give unsatisfactory results on atleast 1/2 ( in reality probably more ) of users systems ( Nvidia + ATI ) forcing them into a "no win " choice either don't use the driver of their choice or accept cruddy boot graphics and/or terrible boot/shutdown times . IMHO this is not the way to impress people favorably .

I saw today on slashdot that Intel is dropping discrete graphics chips and I believe Via has already bailed out so pretty soon that will be 100% of new systems that will potentially cause problems with plymouth .

---

### Post by Longinus00 on 2010-05-28
> **ronacc said:**
> atleast at the present time plymouth will potentially give unsatisfactory results on atleast 1/2 ( in reality probably more ) of users systems ( Nvidia + ATI ) forcing them into a "no win " choice either don't use the driver of their choice or accept cruddy boot graphics and/or terrible boot/shutdown times . IMHO this is not the way to impress people favorably .

I saw today on slashdot that Intel is dropping discrete graphics chips and I believe Via has already bailed out so pretty soon that will be 100% of new systems that will potentially cause problems with plymouth .

Intel has never made a discrete graphics chip.

---

### Post by ronacc on 2010-05-28
since I don't use anything but Nvidia I was just reporting what I saw on /.   

[http://hardware.slashdot.org/story/10/05/26/1741228/Intel-Abandons-Discrete-Graphics](http://hardware.slashdot.org/story/10/05/26/1741228/Intel-Abandons-Discrete-Graphics)

---

### Post by cariboo on 2010-05-28
I'm running Maverick on two system, both with nvidia cards, one a GT210 and the other a 9400GT, Plymouth seems to work better on both systems. The same systems running Lucid, I only see plymouth at shutdown. I did the modifications from the Softpedia page on the system running the 9400GT, I haven't checked bootchart, but it does seem to take a little longer to startup, but otherwise it works perfectly.

On my Compaq netbook with Intel 945 chipset running Lucid UNE, plymouth runs the way it should.

---

### Post by fedexnman on 2010-05-29
yeah, softpedia stuff,  i did that and it fixed it, imho  karmic xsplash looks the best, looks way better than w7 or osx.

---

### Post by BwackNinja on 2010-05-29
READ: [http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/](http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/) (especially near the end)

An SVGAlib backend to plymouth would probably be the best solution, so if someone knows how, it would probably be the best solution. Ysplash used SVGAlib as a backend, and that's why you got decent resolution with usplash but sadly not with plymouth if you weren't using a driver that had kernel mode setting. This would bring the boot graphics back to the quality from when usplash was default.

---

### Post by Longinus00 on 2010-05-29
> **ronacc said:**
> since I don't use anything but Nvidia I was just reporting what I saw on /.   

[http://hardware.slashdot.org/story/10/05/26/1741228/Intel-Abandons-Discrete-Graphics](http://hardware.slashdot.org/story/10/05/26/1741228/Intel-Abandons-Discrete-Graphics)

Like I said, they never made a discrete graphics chip. Now they never (in the foreseeable future) will.

---

### Post by Slug71 on 2010-05-29
Why does poor Plymouth get the slack for all this. Yeh its been around for a while but is still very much new. It is really the video drivers that are to blame too. Ive got Lucid on 3 boxes and have no trouble at all with it. I would be very sad to see it go as ive looked forward to it since Jaunty development. 
Blame the people responsible for the video drivers though. There should however be much improvement with Maverick and the next kernel.

---

### Post by ranch hand on 2010-05-29
> **Slug71 said:**
> Why does poor Plymouth get the slack for all this. Yeh its been around for a while but is still very much new. It is really the video drivers that are to blame too. Ive got Lucid on 3 boxes and have no trouble at all with it. I would be very sad to see it go as ive looked forward to it since Jaunty development. 
Blame the people responsible for the video drivers though. There should however be much improvement with Maverick and the next kernel.
You and most of the folks on this thread can't seem to understand that the bugger doesn't work even if you disable the graphics part of it.

The graphics are not an necessary  thing at all.  Plymouthd has not grahic function.  It is instigated by libplymouth2.

I have the graphics turned off on my installs and have "splash" removed from my menu.  This does, I will admit, improve things.  I can boot.

That you can fob off on the drivers although I see no reason that driver devs should worry about making their drivers fit one particular app.

What you can't blame on the drivers is the 50 to 75 second boot time and the 85 to 300 second shut down time that is taken up by errors from plymouth and ureadahead.

The Ubuntu devs have done a remarkable job in improving the performance of this piece of crap.  The are not going to get it to work a whole lot better.  Why?  Because what they are doing is patching.

If you have a boat made of rust, patches do not help in the long run.  They will cause the hulk to sink faster when that inevitably occurs.

I admire their determination, but not the bull headedness to not see that they have just about ruined and LTS and, it appears, this current development stage OS too.  This is not a great way to run anything.

This is an insult to all the devs that have worked hard to make a great LTS just to have it ruined by this faulty boot crap.  It is an insult to the loyal users of Ubuntu that this thing is continuing into another release.

I am sorry that you have been looking forward to this piece of crap.  I have been looking forward to a replacement for my 8.04LTS.  Gee I am glad they have their priorities straight.  Lets please the folks that want a few seconds of eye candy at the expense of those users who really want a reliable, bootable, OS capable of being shut down.

Makes no sense what so ever and I am really tired of the folks trying to blame everything else but plymouth.  Damn straight it is everything elses fault.  They ought to scrap the Linux kernel and start over with the priority being the ability to run plymouth.  Then maybe we could ave a real OS.

Bunk.  If you develop an app, it is up to you, as the developer, to make sure it is compatable with the things it runs on and the depends that you design it to use.  That includes drivers which are used by may things that have no trouble with them at all.

Plymouth obviously has a completely alien requirement from its environment than anything else.  Inflict it on MS.  Get it the hell off my box.

---

### Post by MacUntu on 2010-05-29
You having problems with plymouth doesn't make it crap. Contact the developers and help them to work on a solution. If you cannot live with the current state I suggest using Karmic or a distribution that doesn't ship with plymouth.

Besides, that's completely off-topic. The question is answered in post #3 - why do we need this pointless anti-plymouth bla bla _again_?

---

### Post by ronacc on 2010-05-29
> **MacUntu said:**
> You having problems with plymouth doesn't make it crap. Contact the developers and help them to work on a solution. If you cannot live with the current state I suggest using Karmic or a distribution that doesn't ship with plymouth.

Besides, that's completely off-topic. The question is answered in post #3 - why do we need this pointless anti-plymouth bla bla _again_?

Mabye we would like to continue using an uptodate ubuntu rather than an obsolete version . telling people to go use a different distro really helps ,someday they might just take you up on that .

---

### Post by MacUntu on 2010-05-29
> **ronacc said:**
> Mabye we would like to continue using an uptodate ubuntu rather than an obsolete version .
If one wants bugs fixed, he or she needs to do something. What kind of testing forum is this where people want something removed just because it's buggy? :confused:
> **ronacc said:**
> telling people to go use a different distro really helps
Contrary to ranting in forums that developers usually don't even follow it *really* helps. ;) And if one isn't interested in fixing Plymouth or using "obsolete" releases of Ubuntu, there's no alternative (other than hacking the system in an unsupported state).

---

### Post by Elfy on 2010-05-29
This is going nowhere fast - keep the trolling out of it please.

---

### Post by tad1073 on 2010-05-29
> **forestpiskie said:**
> This is going nowhere fast - keep the trolling out of it please.

My sentiments exactly, but I do agree with Ranch Hand. The Plymouth devs know all about the issues that Plymouth has with proprietary drivers, but so far have only offered patches and work arounds.

Maybe it is grub 2 that is the culprit. My experience with fedora 12 and plymouth was that when I installed nvidia drivers all I had to do was set the "vga=795" kernel flag instead of having to edit this file, that file and that file with grub 2.

I am not a programmer or developer so I can't say for sure.

---

### Post by seeker5528 on 2010-05-29
> **tad1073 said:**
> My sentiments exactly, but I do agree with Ranch Hand. The Plymouth devs know all about the issues that Plymouth has with proprietary drivers, but so far have only offered patches and work arounds.

If the developers sat on their assets waiting for the proprietary drivers to catch up all the time, nothing would ever get done.

And wouldn't you know it. Right after posting about how I don't have any problems, I have a problem. Doesn't seem likely that Plymouth has anything to do with the issue I am having though.

Later, Seeker

---

### Post by cascade9 on 2010-05-30
> **ranch hand said:**
>   I have been looking forward to a replacement for my 8.04LTS.  Gee I am glad they have their priorities straight.  Lets please the folks that want a few seconds of eye candy at the expense of those users who really want a reliable, bootable, OS capable of being shut down.

Personally, I've never understood why people would want eyecandy on booting. If it was pretty much bugless, it makes a bit more sense, but plymouth seems to be a trainwreck.  

> **Longinus00 said:**
> Like I said, they never made a discrete graphics chip. Now they never (in the foreseeable future) will.

Actually, intel has made a standalone video card- 

[http://en.wikipedia.org/wiki/Intel740](http://en.wikipedia.org/wiki/Intel740)

It was so bad that intel would probably rather nobody remembered it though.

---

### Post by Slug71 on 2010-05-30
> **cascade9 said:**
> Personally, I've never understood why people would want eyecandy on booting. If it was pretty much bugless, it makes a bit more sense, but plymouth seems to be a trainwreck.  


Well eyecandy on boot or any place on the desktop is important to win over new users. Believe it or not.
If you were in a airport or on a bus or in a hotel or whatever and you fire up your PC and the person sitting next to you sees awesomeness, the first thing they do is ask you 'what is that?'. You explain what it is and the benefits of it and then they wanna know how they can get it.
If its nothing intriguing they wouldnt care a less what it is.

And well, the more users we get, the more bugs get filed, possibility of new developers and more vendor support, etc..

Plymouth is far from a trainwreck.


FWIW, the desktop im using now has a nvidia Geforce 6600 256mb which i got in 2005 and Plymouth works just fine on it using the nouveau driver.

---

### Post by Reiger on 2010-05-30
Careful what you wish for. Fire up your computer without a graphical environment whatsoever and start typing away on the console. Chances are a passer-by will ask “what is that?” to be followed by a confession that boils down to “rather you than me, mate”... :P

---

### Post by Slug71 on 2010-05-30
> **Reiger said:**
> Careful what you wish for. Fire up your computer without a graphical environment whatsoever and start typing away on the console. Chances are a passer-by will ask “what is that?” to be followed by a confession that boils down to “rather you than me, mate”... :P

Well yeh they might, but yeh i bet they dont ask how they can get it. :P

---

### Post by ronacc on 2010-05-30
> **Slug71 said:**
> Well eyecandy on boot or any place on the desktop is important to win over new users. Believe it or not.
If you were in a airport or on a bus or in a hotel or whatever and you fire up your PC and the person sitting next to you sees awesomeness, the first thing they do is ask you 'what is that?'. You explain what it is and the benefits of it and then they wanna know how they can get it.
If its nothing intriguing they wouldnt care a less what it is.

And well, the more users we get, the more bugs get filed, possibility of new developers and more vendor support, etc..

Plymouth is far from a trainwreck.


FWIW, the desktop im using now has a nvidia Geforce 6600 256mb which i got in 2005 and Plymouth works just fine on it using the nouveau driver.

if they saw what plymouth looks like on my box the sure wouldn't want it .
I have an Nvidia 7600gs and use the propriatary driver because I need the 3d accel and plymouth looks UGLY . fortunately I am not having the probem ranch hand is with extended boot/shutdown , my boot is around 20 sec so plymouth isn't visible long enough to make me puke .

---

### Post by fedexnman on 2010-05-30
im sure the ubuntu and plymouth developers are aware of things, because it seems like a 50/50 chance that plymouth will boot correctly on peoples machines.  eventually im sure things will be sorted out or fixed either with plymouth or ubuntu not using plymouth( by 10.10 0r 11.04 ?), so no worries here.   i had ubuntu 9.10 installed on my 74 yr old mother in-laws toshiba laptop (amd ), i upgraded it to 10.04 and i had to tell her bout the boot process and maybe in another 6 months it might get fixed, kinda embarrassing for me here, but i downloaded frozen bubble for her, boy she likes that game and also texas holdem. so no worries here, im sure there aware of things.

---

### Post by MacUntu on 2010-05-30
> **ronacc said:**
> if they saw what plymouth looks like on my box the sure wouldn't want it .
I have an Nvidia 7600gs and use the propriatary driver because I need the 3d accel and plymouth looks UGLY .

What's holding you back from using a framebuffer? It's like:
```
echo "FRAMEBUFFER=y" | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u -k all
```
Then edit '/etc/default/grub' and add 'vga=792' (or whatever supported resolution you like) to 'GRUB_CMDLINE_LINUX_DEFAULT=...' and run 'sudo update-grub'. Done - the splash screen starts earlier and is no longer 16-bit puke.

---

### Post by amano on 2010-05-30
> **MacUntu said:**
>  the splash screen starts earlier and is no longer 16-bit puke.

Rather 16 colours than 16 bit.

---

### Post by MacUntu on 2010-05-30
> **amano said:**
> Rather 16 colours than 16 bit.

Of course. ](*,):---)

---

### Post by SevenMachines on 2010-05-30
what MacUntu describes is indeed how i have it at the moment and it works fine, be warned if you do this though, it can break suspend/resume, certainly with the nvidia card i have on this machine. I dont use that kind of power management thing here but something to watch for if you do

---

### Post by ronacc on 2010-05-30
> **MacUntu said:**
> What's holding you back from using a framebuffer? It's like:
```
echo "FRAMEBUFFER=y" | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u -k all
```
Then edit '/etc/default/grub' and add 'vga=792' (or whatever supported resolution you like) to 'GRUB_CMDLINE_LINUX_DEFAULT=...' and run 'sudo update-grub'. Done - the splash screen starts earlier and is no longer 16-bit puke.

thanks , I gave that a shot on my mangy install , It didn't work , not because of your instructions but because of the bizarre setup on my box . Mangy is on sda 3 but right now I am booting off of the mbr of sdb ( which has sabayon 5.2 ) I switch bios boot order to boot off of different drives but that only works off of the mbr and mangys grub is in a partition , later I'll try it on my lucid install on sdc since it has its own grub in that mbr . sda 1 and 2  have karmic which uses usplash .

---

### Post by ronacc on 2010-05-30
@ SevenMachines thanks for the warning , not a problem for me because I NEVER suspend or resume , not even on my netbook, off means OFF .

---

### Post by SevenMachines on 2010-05-30
> **ronacc said:**
> @ SevenMachines thanks for the warning , not a problem for me because I NEVER suspend or resume , not even on my netbook, off means OFF .
ditto, i think this was one of the reasons that it wasnt set this way as default for proprietary nvidia, understandable

---

### Post by Scotty Bones on 2010-05-30
The only issue I had with plymouth was its resolution.
I'm currently running 10.04 on a System76 Panp5 with the GeForce G 105M and the NVIDIA 195.36.24 driver. I installed the Solar theme then used Startup-manager to change the resolution from 800x600x8 to 1024x768x24. And I must say this thing looks freakin' sweet.

---

### Post by cascade9 on 2010-06-01
> **Slug71 said:**
> Well eyecandy on boot or any place on the desktop is important to win over new users. Believe it or not.

Plymouth isnt on the desktop, its bootscreen. When I showed it to a friend of mine, his 1st reaction was "where is the scroling commands on boot? this looks like a windows boot screen! can you get rid of it?" (and that was before I installed the nVidia drivers that made it look horrid). Once I told him that AFAIK, plymouth is unremovable, he said a few nasty things bout the thought process behind that ever happening, waved his arms (literally!) and said "gimmie debain". 

Eyecandy on booting might win over some users...but its also not going to impress some users. Even eyecandy on the desktop will annoy soem users...thankfully, nobody has hardwired compiz into gnome/xfce, and kiwn can be disabled. . 

> **Slug71 said:**
> If you were in a airport or on a bus or in a hotel or whatever and you fire up your PC and the person sitting next to you sees awesomeness, the first thing they do is ask you 'what is that?'. You explain what it is and the benefits of it and then they wanna know how they can get it.
If its nothing intriguing they wouldnt care a less what it is.

Fair enought hat you think that, but I place usability, stability, and customisation much higher than a bootscreen process. Also, considering that everybody else has a bootscreen, surely that is more 'intriguing' than a cookie-cutter, me-too bootscreen. 

BTW, my machine never goes anywhere- its a desktop, I dont own a laptop and have no plans to ever get one.  

> **Slug71 said:**
> Plymouth is far from a trainwreck.

FWIW, the desktop im using now has a nvidia Geforce 6600 256mb which i got in 2005 and Plymouth works just fine on it using the nouveau driver.

Which is pretty useles if installing the nVidia drivers makes it go ugly. Not everybody wants to use nouveau (I would only use it on very old nVidia cards, anything GF 6XXX or higher I'd use the nVidia driver every time)

I still think its a trainwreck.

---

### Post by Slug71 on 2010-06-01
> **cascade9 said:**
> Plymouth isnt on the desktop, its bootscreen. When I showed it to a friend of mine, his 1st reaction was "where is the scroling commands on boot? this looks like a windows boot screen! can you get rid of it?" (and that was before I installed the nVidia drivers that made it look horrid). Once I told him that AFAIK, plymouth is unremovable, he said a few nasty things bout the thought process behind that ever happening, waved his arms (literally!) and said "gimmie debain".

I know, i said 'bootscreen OR any place on the desktop. 
To each their own i guess.

> **cascade9 said:**
> Fair enought hat you think that, but I place usability, stability, and customisation much higher than a bootscreen process. Also, considering that everybody else has a bootscreen, surely that is more 'intriguing' than a cookie-cutter, me-too bootscreen. 

BTW, my machine never goes anywhere- its a desktop, I dont own a laptop and have no plans to ever get one.  

Agreed on usability, stability and customization. 
Any new users and especially those that are completely new to Linux even, will need time to adjust and get to know the new system. So something to make them happy until they get to know it is important. If they want what they saw, they dont want to spend a couple hours learning how to tweak and going onto forums to ask questions. Theyre already gonna have trouble trying to install .exe's on here. :P 

> **cascade9 said:**
> Which is pretty useles if installing the nVidia drivers makes it go ugly. Not everybody wants to use nouveau (I would only use it on very old nVidia cards, anything GF 6XXX or higher I'd use the nVidia driver every time)

I still think its a trainwreck.

Last i heard nVidia drivers dont support or have KMS enabled. If thats the case then thats the problem right there since Plymouth relies on KMS.

---

### Post by philinux on 2010-06-01
nVidia 8600GT.

This, plus the framebuffer fix, works for me. The resolution chosen should be the monitor's native resolution.
From the General Help forum sticky.

```
gksu gedit /etc/default/grub
```
and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
**GRUB_GFXPAYLOAD_LINUX=1680x1050** 

Save the file and run 
```
sudo update-grub
```

---

### Post by ratcheer on 2010-06-01
> **Slug71 said:**
> Last i heard nVidia drivers dont support or have KMS enabled. If thats the case then thats the problem right there since Plymouth relies on KMS.

Bingo! That is the entire crux of the issue.

Tim

---

### Post by SevenMachines on 2010-06-01
As i understand it its more of a problem with framebuffers and nvidia causing problems on resume/suspend, i have a very pretty splash in high resolution with nvidia binary as mentioned before, but try to suspend and pain will follow.

[EDIT] hold on, keybuk has blogged an explanation on some of this
[http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/](http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/)

---

### Post by Mr. Picklesworth on 2010-06-01
> **Slug71 said:**
> Agreed on usability, stability and customization. 

Doing graphics with a nice bit of technology has a perfectly valid impact on usability. For example, compare the highly readable fsck message in Lucid to the crazy, scary looking, scrolling madness we got with earlier releases. Being able to press Delete and instantly toggle between text output and the boot screen (without changing to a different tty) is a big help, too.

Text-based interfaces do not rule out usability, either. Plymouth has a text theme, and it's actually quite good at what it does. Nicely formatted, very readable text.


> **Slug71 said:**
> Last i heard nVidia drivers dont support or have KMS enabled. If thats the case then thats the problem right there since Plymouth relies on KMS.

Plymouth does not *rely* on KMS. It *benefits* from KMS. It looks pretty when your graphics driver supports KMS, and it looks like any other boot splash when it doesn't.

---

### Post by Slug71 on 2010-06-01
> **Mr. Picklesworth said:**
> Doing graphics with a nice bit of technology has a perfectly valid impact on usability. For example, compare the highly readable fsck message in Lucid to the crazy, scary looking, scrolling madness we got with earlier releases. Being able to press Delete and instantly toggle between text output and the boot screen (without changing to a different tty) is a big help, too.

Text-based interfaces do not rule out usability, either. Plymouth has a text theme, and it's actually quite good at what it does. Nicely formatted, very readable text.

Agreed.

> **Mr. Picklesworth said:**
> Plymouth does not *rely* on KMS. It *benefits* from KMS. It looks pretty when your graphics driver supports KMS, and it looks like any other boot splash when it doesn't.

Thanks for the clarification.

---

### Post by ronacc on 2010-06-01
> **Mr. Picklesworth said:**
> 
Plymouth does not *rely* on KMS. It *benefits* from KMS. It looks pretty when your graphics driver supports KMS, and it looks like any other boot splash when it doesn't.

I can assure you that the grainy washed out purple background with fuzzy white letters does not look nearly as good as the splash in Karmic for instance . We who are raising concerns are not anti plymouth , what we are complaining about is that when it isnot working properly on your box you have no acceptable way out . For myself I can ignore the "purple uglies " I thankfuly have a satisfactorily short boot/shutdown time but as I stated above I would hate to have to show that to a prospective convert as an example of the excelence of Ubuntu .

---

### Post by ranch hand on 2010-06-01
> **ronacc said:**
> I can assure you that the grainy washed out purple background with fuzzy white letters does not look nearly as good as the splash in Karmic for instance . We who are raising concerns are not anti plymouth , what we are complaining about is that when it isnot working properly on your box you have no acceptable way out . For myself I can ignore the "purple uglies " I thankfuly have a satisfactorily short boot/shutdown time but as I stated above I would hate to have to show that to a prospective convert as an example of the excelence of Ubuntu .
I am anti-plymouth because plymouth is not going to, ever work on my box.

10.04 is a great OS and I love it.  Wish I could use it for more than a toy.

I will continue to test Ubuntu, test ISOs and have fun with the fine folks on this forum.

I have been excitedly waiting for the new LTS to replace hardy as my serious, secure business OS.  Can't use it.  I am off to Debian land I guess.  I have to, in the nest year, find something I can actually use for more than entertainment.

Frankly wondering if it will boot and then if it will shut down is not even that entertaining.

---

### Post by ronacc on 2010-06-01
I am glad I don't have as serious a problem as you do ,a few seconds of "purple uglies " is a minor annoyance . I think though what you object to is that they integrated plymouth so tightly into things that there is no way out . Atleast with usplash we could just delete splash from the boot line . I agree that it was a very bad Idea to make a ( at least for a few people ) pretty bootup  a sine quo non of the entire system effectively they have made themselves hostages to plymouth .

---

### Post by nanog on 2010-06-01
ranch_hand,
have your tried both of the following?

nano /usr/share/doc/plymouth/README.Debian

> Disabling the splash screen
---------------------------

There are two methods to disable the splash screen.  Both have the
same effect.  Your boot will show such messages as are emitted by
the starting services, and will still be able to prompt if needs be.

 1) Remove all of the plymouth-theme-* packages from your system,
    including the text ones.  Plymouth will remain installed to
    permit boot-time prompts.

 2) Remove "splash" from the kernel command-line.  You can do this
    per-boot, or make it permanent by changing the
    GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub 			 		

---

### Post by ranch hand on 2010-06-01
> **nanog said:**
> ranch_hand,
have your tried both of the following?

nano /usr/share/doc/plymouth/README.Debian
I have done all of those things long ago.  I also do not have "splash" in my menu entries.  I have also tried the mountall that doesn't depend on plymouth so you can remove it (don't use it anymore - no real benefit)

This makes it so I can, if I wait long enough, boot.

The thing that you are not getting is that plymouthd is the problem.  That is supplied, currently by libplymouth2.

Every time that has been upgraded my performance gets worse.  Hell, now the stupid thing can't even turn itself off when I reboot.

---

### Post by tekkidd on 2010-06-01
i think it should be fixed in an update for 10.04

although fixing it yourself isn't all that hard

---

### Post by philinux on 2010-06-02
After some testing I can confirm, on my box at least, that hibernate and suspend both work fine with fixes I've done as per post #67. Boot up and shutdown look good in the correct resolutions too. Also shutdown is 4 seconds ish.

So for one lucky nvidia user I'm happy. :P

---

### Post by Slug71 on 2010-06-02
> **ranch hand said:**
> I have done all of those things long ago.  I also do not have "splash" in my menu entries.  I have also tried the mountall that doesn't depend on plymouth so you can remove it (don't use it anymore - no real benefit)

This makes it so I can, if I wait long enough, boot.

The thing that you are not getting is that plymouthd is the problem.  That is supplied, currently by libplymouth2.

Every time that has been upgraded my performance gets worse.  Hell, now the stupid thing can't even turn itself off when I reboot.

Why not use Karmic as your stable OS replacing Hardy? Karmic still has plenty of life left and then upgrade to Lucid when the fix is out.

---

### Post by ranch hand on 2010-06-02
> **Slug71 said:**
> Why not use Karmic as your stable OS replacing Hardy? Karmic still has plenty of life left and then upgrade to Lucid when the fix is out.
To do that I would have to have some faith that;
A>plymouth will be fixed

B>fixed before 04-11

C>backported to 10.04

All of these seem pretty shaky to me.  8.04 is good until 04-11.

I may stick with it until the next LTS and hope that they have a boot manager that actually will work by then.

---

### Post by ratcheer on 2010-06-02
> **philinux said:**
> After some testing I can confirm, on my box at least, that hibernate and suspend both work fine with fixes I've done as per post #67. Boot up and shutdown look good in the correct resolutions too. Also shutdown is 4 seconds ish.

So for one lucky nvidia user I'm happy. :P

This is the first of these type of suggested fixes that has worked for me, at all. However, the result looks very similar to what I was getting without the fix. The splash may or may not be clearer than what I had before. I think it is clearer, but am not sure. Certainly nowhere near as sharp and clean as the splash I get with nouveau.

Tim

---

### Post by philinux on 2010-06-02
> **ratcheer said:**
> This is the first of these type of suggested fixes that has worked for me, at all. However, the result looks very similar to what I was getting without the fix. The splash may or may not be clearer than what I had before. I think it is clearer, but am not sure. Certainly nowhere near as sharp and clean as the splash I get with nouveau.

Tim

I'm getting identical to how nouveau was. Apart from slight 1 second black screen. With the nvidia driver active before the two fixes I was getting a black screen with a flashing cursor top left for about 10 sec. Then a short duration plymouth for 3 seconds, but it was displayed pretty low res and large. Same at shutdown although it was and still is damn quick.

---

