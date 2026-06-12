---
title: "Compiz 0.9 rewrite coming in Meerkat?"
date: 2010-05-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by null_pointer_us on 2010-05-18
Phoronix recently [reported]("http://www.phoronix.com/scan.php?page=news_item&px=ODI1NA") that the Compiz devs have put out a call for help testing.

Background info from the article:
> The Compiz 0.9 release has been baking for quite a while as it involved [the merging of Nomad and Compiz++]("http://www.phoronix.com/scan.php?page=news_item&px=NzAzNg") ([the C++ rewrite of Compiz]("http://www.phoronix.com/scan.php?page=news_item&px=Njk1Ng")), the dropping of Compiz Fusion, and many other architectural changes after the future of Compiz was [previously called into questions]("http://www.phoronix.com/scan.php?page=news_item&px=Njk2Mg"). It's been about fifteen months since the last official release of Compiz, but again Compiz 0.9 is still on the way. 

From [smspillaz' blog]("http://smspillaz.wordpress.com/2010/05/15/bugfixing-and-a-testing/") (emphasis added):
> This means that we can finally build RPM and Debian packages. Hopefully **a PPA for Ubuntu will be coming soon**, and we might even see Compiz 0.9.2~ in Ubuntu Maverick Meerkat if we&#8217;re lucky :)

Here's what they need:
> However, what I really need now is some user input on some of the more crucial elements of this release. This includes:

    * Ensuring that compiz builds from a fresh build from the new commits that have gone into the master branches
    * Going into CCSM and disabling the &#8220;opengl&#8221; and &#8220;composite&#8221; and relaunching your window decorator and telling me if it works as expected (albeit, it&#8217;s a little slow, but I will work on this for 0.9.2)
    * If you have a screen resolution that is higher than your maximum texture size, enabling the &#8220;Copy To Texture&#8221; plugin and telling me if compiz appears to work.

As usual, you can post any quirks to this [forum thread]("http://go2.wordpress.com/?id=725X1342&site=smspillaz.wordpress.com&url=http%3A%2F%2Fforum.compiz.org%2Fviewtopic.php%3Ff%3D112%26t%3D12565&sref=http%3A%2F%2Fsmspillaz.wordpress.com%2F2010%2F05%2F15%2Fbugfixing-and-a-testing%2F") [1] and see this post by soreau for a [nice script]("http://go2.wordpress.com/?id=725X1342&site=smspillaz.wordpress.com&url=http%3A%2F%2Fforum.compiz.org%2Fviewtopic.php%3Ff%3D112%26t%3D12565%23p77557&sref=http%3A%2F%2Fsmspillaz.wordpress.com%2F2010%2F05%2F15%2Fbugfixing-and-a-testing%2F") to do everything for you

See this link for detailed instructions:
[http://smspillaz.wordpress.com/2010/05/15/bugfixing-and-a-testing/](http://smspillaz.wordpress.com/2010/05/15/bugfixing-and-a-testing/)

A PPA is coming soon! I will update this post with a link to the PPA when I hear of it.

---

### Post by plun on 2010-05-18
Yeeah....:popcorn:

The build script

[http://forum.compiz.org/viewtopic.php?f=112&t=12565#p77557](http://forum.compiz.org/viewtopic.php?f=112&t=12565#p77557)

> Try this build script which should work on karmic and lucid. By default it clones the code in ~/src/compiz/compiz++ and installs to /opt/compiz++. It also installs starter scripts for compiz and ccsm.


Installer script: [http://forum.compiz.org/viewtopic.php?f=112&t=12565#p77557](http://forum.compiz.org/viewtopic.php?f=112&t=12565#p77557)

> Don't forget to rm ~/.compiz directory if it exists.

Testing.....:)

```
Installing ccsm++ starter script to /opt/compiz++/bin/
Installing compiz++ starter script to /opt/compiz++/bin/
Would you like to start compiz++ now? y/n: y

```

---

### Post by Speed_arg on 2010-05-18
What's better about it? Is it faster than 0.8?

---

### Post by screaminj3sus on 2010-05-18
Cool cant wait for the ubuntu ppa.

---

### Post by ronacc on 2010-05-18
why wait the build script works fine , just built it on my amd64 sys .

---

### Post by screaminj3sus on 2010-05-18
So I am using the script right now. So with this script by default will the new compiz start at boot rather than .8?

---

### Post by Starks on 2010-05-18
I don't believe so. It's placed in /opt, not /usr.

---

### Post by Starks on 2010-06-04
Here's a PPA, [https://launchpad.net/~dashua/+archive/compiz-c++](https://launchpad.net/~dashua/+archive/compiz-c++)

Add as Lucid.

---

### Post by null_pointer_us on 2010-06-04
That's great news!

I'm not exactly an expert with PPAs, but it seems there are 2 failed builds (missing dependencies) and a source package. Is this normal?

If it's OK and PPA looks fine to you, I'd like to add it to the first post (with credit given) so people can find it more easily.

---

### Post by Starks on 2010-06-04
It works fine on my end (i386 with Intel graphics).

---

### Post by Vanishing on 2010-06-04
Running the build script yield some build errors on my box with the plugins..o.o

---

### Post by plun on 2010-06-06
> **Starks said:**
> Here's a PPA, [https://launchpad.net/~dashua/+archive/compiz-c++](https://launchpad.net/~dashua/+archive/compiz-c++)

Add as Lucid.

Another ppa from Amaranth, add as maverick

[https://launchpad.net/~amaranth/+archive/compiz](https://launchpad.net/~amaranth/+archive/compiz)

But just gives me error:confused:

```
plun@plun-laptop:~$ compiz --replace
compiz (core) - Error: Couldn't load plugin 'ccp'
compiz (core) - Error: Couldn't load plugin 'decoration'

```

the package compiz-gnome is also broken.

a ppa-purge and a compiz reinstall and everything is back to normal.

---

### Post by aviramof on 2010-06-06
I have just added  the ppa from [https://launchpad.net/~amaranth/+archive/compiz]("https://launchpad.net/%7Eamaranth/+archive/compiz")  as maverick and it want me to remove a lot of packages and install and upgrade a lot of packages as you can see in the attached pictures so what do you think i should do?

 it goes like this in the list first remove then install and in the end upgrade

---

### Post by plun on 2010-06-06
All those old packages must be removed and new ones installed.... in your case it seems to be a lot of packages and perhaps its better to stay away from this ppa for a while.

As I wrote I cannot start compiz with new packages. No idea whats wrong, also checked the Compiz forum thread.


Just to run these commands in case something goes wrong:
```

sudo ppa-purge ppa:amaranth/compiz

sudo apt-get install --reinstall compiz

compiz --replace
```


--

---

### Post by aviramof on 2010-06-06
Ok i tried it and i have the same problem as yours.

purged it with no problems except downloading ppa-purge manually because it's not in the main repositories.

let's hope it would work better in the future.

---

### Post by null_pointer_us on 2010-06-06
The PPAs' files are from 5/20, which is more than two weeks ago.

From some of the comments in the forum thread and my own experiences with crashes/lockups running from source, IMO it's still too early for a PPA.

Installing from source is easy and fairly safe (though very time-consuming!). [This script]("http://forum.compiz.org/viewtopic.php?f=112&t=12565#p77557") by [soreau]("http://forum.compiz.org/memberlist.php?mode=viewprofile&u=11487") makes a src folder in your home folder and installs compiz 0.9 to an opt folder, so it should not interfere with the stable, Ubuntu-provided version of compiz.

The only thing you might have to do manually is [COLOR="DarkOrange"]**mv .compiz .compiz-stable**[/COLOR] or something to keep your old settings from conflicting with the new version.

---

### Post by plun on 2010-06-06
Yup.... I am lazy for the moment so a ppa-solution is the best.

I haven't seen Amaranth for a while but maybe he is around for a comment ?

Ping....:)

---

### Post by qwertyu on 2010-06-06
Which the benefit of all this rewrite is?

---

### Post by vikrant82 on 2010-06-06
Could'nt get compiz 0.9 working, but 0.8.6 from following PPA, solved some of issues I was having with KDE and compiz. And the overall performance feels better. 

```
deb http://ppa.launchpad.net/dashua/libcompizconfig/ubuntu lucid main
```

---

### Post by Amaranth on 2010-06-06
How in the world did you find mine? That was an incomplete package I uploaded to see if a build problem was with my system or with the package. The problem was with the package. Please don't even try to use it.

---

### Post by plun on 2010-06-06
> **Amaranth said:**
> How in the world did you find mine? That was an incomplete package I uploaded to see if a build problem was with my system or with the package. The problem was with the package. Please don't even try to use it.

Hehe....:)   Thanks for answering !

Source:

Upgrade To Compiz 0.8.6 In Ubuntu 10.04 Lucid Lynx Or [B]Compiz 0.9 Beta In Ubuntu 10.10 Maverick Meerkat
[/B]
[http://www.webupd8.org/2010/06/upgrade-to-compiz-086-in-ubuntu-1004.html](http://www.webupd8.org/2010/06/upgrade-to-compiz-086-in-ubuntu-1004.html)


--

---

### Post by vikrant82 on 2010-06-06
> **Amaranth said:**
> How in the world did you find mine? That was an incomplete package I uploaded to see if a build problem was with my system or with the package. The problem was with the package. Please don't even try to use it.

:D I found it [here. ]("http://www.webupd8.org/2010/06/upgrade-to-compiz-086-in-ubuntu-1004.html")

EDIT: I Guess, we both posted at same time.. :P

---

### Post by aviramof on 2010-06-06
Basically all this mean to me that some sort of stable version or at least a ppa for Maverick should be released soon.:)

---

### Post by Speed_arg on 2010-06-06
> **qwertyu said:**
> Which the benefit of all this rewrite is?

Indeed, which is the benefit? I never knew.

---

### Post by null_pointer_us on 2010-06-08
Code cleanup/refactoring means it will be easier to fix bugs and add new features in future releases.

People are also reporting that it is much more memory efficient, e.g. Compiz 0.9.0 uses ~30% to 50% of what Compiz 0.8.4 used. I'm not aware of anyone testing this scientifically, but there will definitely be some improvements.

The above may attract new developers, too.

---

### Post by soreau on 2010-06-21
> **plun said:**
> Yeeah....:popcorn:

The build script

[http://forum.compiz.org/viewtopic.php?f=112&t=12565#p77557](http://forum.compiz.org/viewtopic.php?f=112&t=12565#p77557)




```
DO NOT REPOST THIS SCRIPTS CODE!
```



Testing.....:)

```
Installing ccsm++ starter script to /opt/compiz++/bin/
Installing compiz++ starter script to /opt/compiz++/bin/
Would you like to start compiz++ now? y/n: y

```

Please DO NOT repost the script code anywhere, only the link to it in the official 0.9 testers thread. I am constantly changing and updating this script. Thanks, on behalf of the compiz support team.

---

### Post by aviramof on 2010-06-21
A ppa for maverick would be great don't you think?

---

### Post by Starks on 2010-06-21
ppa:dashua/compiz-c++

change to lucid after adding.

---

### Post by aviramof on 2010-06-22
I added it and changed to lucid but i don't see any updates or anything new in synaptic.

---

### Post by Perfect Storm on 2010-06-22
> **soreau said:**
> Please DO NOT repost the script code anywhere, only the link to it in the official 0.9 testers thread. I am constantly changing and updating this script. Thanks, on behalf of the compiz support team.

Fixed.

---

### Post by 5735guy on 2010-06-30
Pointed Question ?

Will there ever be a Compiz 0.9 as the carrot has been dangled for a year now ?

Personally I see it as being highly unlikely it will be ready for Maverick if at all

Too many Compiz devs. pulling against each other. Come on guys work on it as a team

:mad::mad::mad:

---

### Post by xir_ on 2010-06-30
> **5735guy said:**
> Pointed Question ?

Will there ever be a Compiz 0.9 as the carrot has been dangled for a year now ?

Personally I see it as being highly unlikely it will be ready for Maverick if at all

Too many Compiz devs. pulling against each other. Come on guys work on it as a team

:mad::mad::mad:

From what i understand that is the opposite of the problem.

---

### Post by dext on 2010-06-30
from my understandings that compiz-0.9.0 has problem with GCC-4.5.0 [http://smspillaz.wordpress.com/2010/06/25/compiz-0-9-and-gcc-4-5/](http://smspillaz.wordpress.com/2010/06/25/compiz-0-9-and-gcc-4-5/) whether its a GCC bug or a compiz Bug i do not know

---

### Post by andrewabc on 2010-07-04
[Compiz 0.9.0 released](http://lists.freedesktop.org/archives/compiz/2010-July/003429.html)

I presume this will be going into 10.10? Although it is unstable release, but maybe they will have another revision by early September.

---

### Post by cb951303 on 2010-07-04
Doesn't Gnome 3.0 have its own compositing manager? If so, I find it highly unlikely that Ubuntu team will choose Compiz over the official Gnome one.

---

### Post by uBeer on 2010-07-04
Well, Gnome 3 will have the compositing manager, but Ubuntu will not enable it yet, because they choose to stick with the panels for at least one more release instead of Gnome-shell.
But I don't know if using compiz 0.9 is such a good idea, because there is no guarantee that in October there will be the stable 0.10 release. But I wouldn't mind some breakage, so if they do decide to include 0.9 I'll be happy :D

---

### Post by kahumba on 2010-07-04
Bottom line: they should just test it, if buggy - avoid it in Ubuntu, if not - include & enable.

---

### Post by Starks on 2010-07-04
We need a new Compiz.

We're still stuck on 0.8.4 instead of 0.8.6 and 0.9 just came out.

It should be stable enough for October and do remember that Maverick is not an LTS.

---

### Post by cariboo on 2010-07-04
There is a thread in the Cafe, where the author of compiz explains what is happening, from what I understand, there is only one developer, and he has a lot of other things on his plate, so development is slow.

The thread is [here]("http://ubuntuforums.org/showthread.php?t=1456511"). The dev himself chimes in at post #10.

---

### Post by Ellipsis on 2010-07-04
> **Starks said:**
> We need a new Compiz.

We're still stuck on 0.8.4 instead of 0.8.6 and 0.9 just came out.

It should be stable enough for October and do remember that Maverick is not an LTS.

There haven't been any really big additions to Compiz other than the code clean up and memory usage fixes. Both of these on their own are not going to improve user experience too much. Any big bugs on the other hand will impact users in a big way. 

So I am crossing my fingers for it to become stable by Maverick but if it isn't... I can wait.

---

### Post by x-shaney-x on 2010-07-04
Does anyone even care about compiz anymore?  (I do).
It seems everything is heading towards the horrible mutter so I fear compiz may drift away into obscurity now.

---

### Post by MacUntu on 2010-07-05
What's horrible about mutter?

---

### Post by x-shaney-x on 2010-07-05
> **MacUntu said:**
> What's horrible about mutter?
Well it's probably wrong to give it a blanket panning but it's horrible to ME at the MOMENT.
Mainly because I find it much slower than compiz or metacity.

Not only that but the window shadows are completely pointless.
To me, window shadows give a nice separation to the windows which is very useful when dealing with many open, overlapping windows and it's something I have become used to.
The mutter shadows only appear to the right and bottom of windows so the tops and left side all merge into the app below.
Not so bad if you are used to it but I have been using window shadows since the xcompmgr days.
Plus they are ugly.

Yea, shadows are a pretty minor reason to hate a window manager but it's mainly the slowness.
Things might improve.

---

### Post by Rob2687 on 2010-07-05
Slower animations or slower performance?
Performance wise I don't see it's any worse than Compiz. If anything it's a little better. The animations kinda suck right now but I'm hoping it becomes customizeable. Same goes for the shadows. There is just an offset on it. That was the default on Compiz a long time ago too.

---

### Post by x-shaney-x on 2010-07-05
Animations-wise I don't see much difference in speed/performance between mutter and compiz but the transitions are smoother with compiz.

By speed I mean the difference in general window management.
I notice it more on meerkat than lucid but opening/closing/minimizing windows is not as snappy with mutter here.
Not only that, my laptop is using much higher resources when using mutter for some reason.
Not enough to be a concern but enough to think there's something not quite right when a "lightweight" window manager is draining the comp more than the bells n whistles compiz.

Maybe it's related to my intel hardware, I dunno.

---

### Post by jpeddicord on 2010-07-05
> **x-shaney-x said:**
> Animations-wise I don't see much difference in speed/performance between mutter and compiz but the transitions are smoother with compiz.

By speed I mean the difference in general window management.
I notice it more on meerkat than lucid but opening/closing/minimizing windows is not as snappy with mutter here.
Not only that, my laptop is using much higher resources when using mutter for some reason.
Not enough to be a concern but enough to think there's something not quite right when a "lightweight" window manager is draining the comp more than the bells n whistles compiz.

Maybe it's related to my intel hardware, I dunno.

You're not alone; I noticed that too on my i915 laptop. Dragging windows was painful work.

On my desktop with an nvidia GTS 250, things are better, but the windows still seem to lag behind the pointer a little bit.

Don't experience this problem with Compiz, though that currently has issues of its own. I did give 0.9 a try and that did solve most of my gripes, though, so count me in for one who would be happy to see it. :)

---

### Post by kahumba on 2010-07-07
> **x-shaney-x said:**
> 
Mainly because I find it much slower than compiz or metacity.
....
Yea, shadows are a pretty minor reason to hate a window manager but it's mainly the slowness.

Oh no, please not yet another slow app from the gnome devs along with their existing slow "masterpieces" like gedit, nautilus and evolution. Someone teach them to create snappy apps, maybe they should consult Google.

---

### Post by GeoPirate on 2010-07-07
so, any word on a compix 0.9 ppa?

---

### Post by seeker5528 on 2010-07-08
> **x-shaney-x said:**
> Well it's probably wrong to give it a blanket panning but it's horrible to ME at the MOMENT.
Mainly because I find it much slower than compiz or metacity.

Across the range of hardware/driver combos that are able to provide OpenGL acceleration, performance will vary more with Mutter than with Compiz.

It will also on what you have running at any given time.

I have Docky running, I have a terminal window open, and I'm watching TV in Totem. If I switch to the terminal window and drag it around, it feels just as quick as on my other similar speed computer that I'm typing this from (so Firefox is open), not running Docky, has synaptic open (but idle at the moment).

The biggest difference between these computers from a performance perspective is the one running mutter has a Radeon card with an R420 chipset, the one running Metacity has a Radeon with an RV770 chipset.

Have not tried anything taxing on the RV770 lately, it did have some maturity issues, but relative to what Mutter needs, it's been performing pretty well the last few times I tried it. 

In spite of the fact the it's implemented as a Mutter plug-in, Gnome-Shell performance is an entirely different beast, much more likely to have performance issues with it than with Mutter alone (at least that's the way it seems to me on the limited range of hardware I have to test on).

Later, Seeker

---

### Post by aviramof on 2010-07-10
I want to test it again what should i do to do this?

Thanks in advance.

---

### Post by PGHammer on 2010-07-11
> **seeker5528 said:**
> Across the range of hardware/driver combos that are able to provide OpenGL acceleration, performance will vary more with Mutter than with Compiz.

It will also on what you have running at any given time.

I have Docky running, I have a terminal window open, and I'm watching TV in Totem. If I switch to the terminal window and drag it around, it feels just as quick as on my other similar speed computer that I'm typing this from (so Firefox is open), not running Docky, has synaptic open (but idle at the moment).

The biggest difference between these computers from a performance perspective is the one running mutter has a Radeon card with an R420 chipset, the one running Metacity has a Radeon with an RV770 chipset.

Have not tried anything taxing on the RV770 lately, it did have some maturity issues, but relative to what Mutter needs, it's been performing pretty well the last few times I tried it. 

In spite of the fact the it's implemented as a Mutter plug-in, Gnome-Shell performance is an entirely different beast, much more likely to have performance issues with it than with Mutter alone (at least that's the way it seems to me on the limited range of hardware I have to test on).

Later, Seeker


Are the two AMD cards running the same driver?  (Either FOSS or proprietary.)

The FOSS driver supports nothing newer than RV770 (no support for any of the Evergreen family, for example)  And even with the rest of the HD series, the two drivers have different strengths/weaknesses (just as the compositing managers do).

Even with Evergreen (my HD5450 is a prime example), which is only supported by the (patched) proprietary driver (10.5 or 10.6) there are differences in compositing-manager performance (in both Maverick and Lucid); for example, I can't enable desktop effects (compositing) in Maverick with KDE 4.5 RC1 installed (I will see if RC2 fixes this problem).

---

### Post by seeker5528 on 2010-07-12
> **PGHammer said:**
> Are the two AMD cards running the same driver?  (Either FOSS or proprietary.)

I don't think any of my cards are new enough to be supported by the proprietary driver, even if I wanted to run it.

> Even with Evergreen (my HD5450 is a prime example), which is only supported by the (patched) proprietary driver (10.5 or 10.6) there are differences in compositing-manager performance (in both Maverick and Lucid); for example, I can't enable desktop effects (compositing) in Maverick with KDE 4.5 RC1 installed (I will see if RC2 fixes this problem).

If you don't have mature drivers available, that's always going to limit what you can do. Additionally with the proprietary driver, when following the development stuff, even if the driver is mature, the support required to work with newer kernel and/or Xorg versions may not be there.

Don't know what the priorities are for the proprietary driver developers relative to the 2D versus 3D support, but on the OSS side I believe even with hardware where the 2D acceleration has to be provided through 3D functions of the hardware, getting the Xrender support working is a lot more basic than getting OpenGL support working, so typically that would come first. 

KDE has the option to use and Xrender backend for FX, so at least with an OSS driver I would expect if you can't even get the FX to work with the Xrender back-end there is a more basic support issue that needs to be addressed before even getting into the question of performance.

And just a small nitpick. While I don't doubt that compositing performance *can* be and issue, I have not read anything that makes me believe that it takes a lot, relatively speaking, to support compositing. If compositing performance *is* an issue, I expect in the vast majority of cases, it's because the driver doesn't support much beyond basic functionality to begin with for whatever reason.

How well various things perform that use compositing is an whole different question, then you are throwing in additional variables relative to what the individual software or effect you are attempting to use requires in addition to compositing support relative to the range of Xrender or OpenGL features your combination of hardware and driver provide good acceleration for.

Later, Seeker

---

### Post by JeyPeyy on 2010-07-17
I get this message: 
> Not allowed here
Sorry, you don't have permission to access this page.

You are logged in as [email]jeanphilippe.green@gmail.com[/email].

When I try to get into:
[https://launchpad.net/~dashua/+archive/compiz-c++](https://launchpad.net/~dashua/+archive/compiz-c++)

---

### Post by cariboo on 2010-07-17
It looks like the page is broken, I get the same error. Create a bug.

---

### Post by jpeddicord on 2010-07-18
Not a bug; the PPA was deleted.

---

### Post by SmSpillaz on 2010-07-22
Indeed, Amaranth did remove everything in the PPA. This was because it was just the developers trying to get one together. Unfortunately, getting a PPA together is a lot more difficult than it looks due to launchpad's load for building packages and the new buildsystem.

If you want to try it, you can just build it yourself (there are scripts around, just look on the compiz forums), or you can use a different distro. If I remember correctly, openSUSE has packages, there are packages in the works for fedora and Arch Linux has a PKGBUILD. There is even a working Compiz 0.9.0 live CD floating around somewhere on susestudio.

Just a note to the OP: try to make logical conclusions. If I say "hopefully there will be a PPA soon" it does NOT mean "there will be a PPA soon". The fact that there will be one soon is largely contingent on whether we can get one built, because it is difficult to do.

Also; to users keep in mind that 0.9.0 is kind of like KDE4.1. It is not utterly terrible, but there are still some *niche* features missing and a few bugs here and there. Our head of QA would probably put it at the level of the 0.5 version, so it is still a bit behind 0.8.x in terms of functionality. The new version doesn't necessarily mean "NEW FUNCTIONALITY OMG!", but there is a lot of *potential* for new functionality since the code is a lot easier to work with.

As for whether the rewrite is going to come to Meerkat - I doubt it. Maybe Meerkat + 1. But as you all know, FOSS software development is highly bumpy at best, and outright unpredictable in our situation. I'm not here to complain, just here to let you know not to get your hopes up.

---

