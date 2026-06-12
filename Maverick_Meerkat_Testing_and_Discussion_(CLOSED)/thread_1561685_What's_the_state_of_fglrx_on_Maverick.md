---
title: "What's the state of fglrx on Maverick?"
date: 2010-08-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by blazemore on 2010-08-26
Hello testers and developers,
I'd like to upgrade to Maverick tonight if possible, as I've just bought a new coffee machine.

What's the current state of xorg with regards to fglrx? Are we still at the stage of development where it doesn't work at all, or has a version been released in the maverick repository that works fully?

---

### Post by jfernyhough on 2010-08-26
[http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872)

Essentially, if you are using xorg-server 1.8 you are fine. Maverick is now xorg-server 1.9, however, so fglrx is not working (we might get lucky with Catalyst 10.9 next month).

---

### Post by SorinN on 2010-09-06
yes - I upgraded to 10.10 beta but blank screen
fglrx was not uninstaled or switched off and radeon was not activated ..how come that ?

now I will install by myself radeon or radeonhd if is possible but you should control some things there.

some script which detect ATI users and switch to radeon

---

### Post by RJ12 on 2010-09-06
Well I have an ATI graphics card in my laptop, which I am currently running Live USB of Maverick on this laptop and 3D works really good with the supplied radeon drivers

---

### Post by tanari on 2010-09-06
radeon 5750 --> fglrx not working :(, no compiz :( :( :(

---

### Post by PGHammer on 2010-09-07
> **tanari said:**
> radeon 5750 --> fglrx not working :(, no compiz :( :( :(

Change in Xorg server usually trainwrecks fglrx (it happened with 1.8 and Lucid; it took until 10.6 for it to unravel for most folks).  With 10.10 we have another change in X (to 1.9); therefore, fglrx (closed-source) is borked again.  (The difference from 10.04 is that *only* HD5xxx is affected, as everyone else can use the FOSS driver.  (Actually, the FOSS driver spits out quick 2D even for HD5xxx; it's everything else that's mucked up!)

---

### Post by djchandler on 2010-09-08
I'm using the FOSS Radeon driver with a 780V Chipset (Radeon 3100) on my laptop. Compiz, works, but video playback, particularly streaming using Flash, is slow. AMD's driver works great on this hardware running Win7. We do need that fglrx driver to work for 3D and video playback. If those things are important to you, you should probably wait until there's a fglrx driver that's compatible with the 1.9 Xorg server IMO.

---

### Post by ToxicBurn on 2010-09-08
i would love to know why the people at xorg-server dont understand how to make updates that do not break video drivers with each update they break somthing and blame it on nvidia or ati 

why not spend more time with xoorg-server and make sure they dont break things before release its like they keep putting out the same fire time after time.

as a end user i am dumbfounded how this makes for good business

whats next xorg-server 1.9a or 1.9b 2.0 all of the above break video from ATI , its ATI's fault not xorgs .

ATI changed nothing 
Xorg = BROKE ATI

why am i the only one who thinks this is stupid ?

---

### Post by The Fiddler on 2010-09-08
> **ToxicBurn said:**
> i would love to know why the people at xorg-server dont understand how to make updates that do not break video drivers with each update they break somthing and blame it on nvidia or ati 

Notice how open-source radeon and nouveau work just fine (indeed even better) after every xorg update? fglrx and nvidia are closed-source drivers that can't be fixed by xorg developers.

In other words, it falls onto AMD and Nvidia to fix their closed-source drivers to work after xorg updates in a timely manner.

---

### Post by PGHammer on 2010-09-08
> **ToxicBurn said:**
> i would love to know why the people at xorg-server dont understand how to make updates that do not break video drivers with each update they break somthing and blame it on nvidia or ati 

why not spend more time with xoorg-server and make sure they dont break things before release its like they keep putting out the same fire time after time.

as a end user i am dumbfounded how this makes for good business

whats next xorg-server 1.9a or 1.9b 2.0 all of the above break video from ATI , its ATI's fault not xorgs .

ATI changed nothing 
Xorg = BROKE ATI

why am i the only one who thinks this is stupid ?

If you rely on closed-source drivers (which should only be the case for HD5xxx in terms of AMD/ATI hardware) then you should avoid Maverick.

While I have HD5450, I don't absolutely need closed-source driver support at this point.  Also, for some rather odd reason, 2D in Maverick is faster than 2D in Lucid (FOSS/radeon server in 1.8 lacks 3D support for HD5xxx also, so that isn't it).

---

### Post by rajeev1204 on 2010-09-08
> **ToxicBurn said:**
> i would love to know why the people at xorg-server dont understand how to make updates that do not break video drivers with each update they break somthing and blame it on nvidia or ati 

why not spend more time with xoorg-server and make sure they dont break things before release its like they keep putting out the same fire time after time.

as a end user i am dumbfounded how this makes for good business

whats next xorg-server 1.9a or 1.9b 2.0 all of the above break video from ATI , its ATI's fault not xorgs .

ATI changed nothing 
Xorg = BROKE ATI

why am i the only one who thinks this is stupid ?


I agree with you completely on this one .Of course iam exempting development releases since maverick is an early beta .

But otherwise , if you use the closed vs open source logic quoted here, none of the hardware will ever work with a linux system since no hardware manufacturer except a few like realtek fully furnish the specifications .The live cd detecting and loading the drivers for a new mobo and other such stuff is a lot of reverse engineering go on, so its not like the devs dont bother .Or linux would never have scratched the desktop market.

If canonical had blamed these people for their closed source model ,we all would be sitting in front of a black CLI .Instead they try to be practical .So things work fine by the time a version of Ubuntu is out.


Luckily ubuntu works closely with the manufacturers to get working closed source drivers on their release versions like the early ATI fglrx drivers which arrive exclusively to ubuntu beta versions since the past 2 releases.



rajeev

---

### Post by Yfrwlf on 2010-09-08
> **rajeev1204 said:**
> I agree with you completely on this one .Of course iam exempting development releases since maverick is an early beta .

But otherwise , if you use the closed vs open source logic quoted here, none of the hardware will ever work with a linux system since no hardware manufacturer except a few like realtek fully furnish the specifications .The live cd detecting and loading the drivers for a new mobo and other such stuff is a lot of reverse engineering go on, so its not like the devs dont bother .Or linux would never have scratched the desktop market.

If canonical had blamed these people for their closed source model ,we all would be sitting in front of a black CLI .Instead they try to be practical .So things work fine by the time a version of Ubuntu is out.


Luckily ubuntu works closely with the manufacturers to get working closed source drivers on their release versions like the early ATI fglrx drivers which arrive exclusively to ubuntu beta versions since the past 2 releases.



rajeev

The real question being asked here is why does Xorg have to break their ABIs so badly with every release so that it causes a need for adjustments in drivers at all.  The point of ABIs/APIs is to have a common standard interface for communication, so why it is so difficult for Xorg to adopt these standards is beyond me.  I'd like to see some sort of proof as to how NOT having standardized interfaces or NOT having modules or a plugin system or whatever is beneficial to some software.  I wouldn't think implementing these standards would take too much trouble compared to actual programming.  I also would think that if done right you wouldn't have any slowdown issues due to it.

Maybe what it really all comes down to is that even though it is very possible to do and do right and maintain comparable performance and whatnot, Xorg simply wasn't designed that way, with standards in mind, and perhaps modularizing or adding standard interfaces to it would be too much trouble at this point?

Very curious.

---

### Post by Sophont on 2010-09-09
xorg is getting a lot of development.
With that come changes to the api to clean up and allow new functionality.

That is no problem with open source drivers who quickly get changed to adapt to these changes.

For most people that is not a problem to begin with - as long as you don't play games that need 3D acceleration the open drivers already cover most needs.

NVidia and ATI usually get their own drivers adapted by release.

If you want to compare Ubuntu to other platforms like Windows - then also consider that Ubuntu has a very fast update cycle of once every 6 months. Most of those releases are there to introduce cutting edge features. But nobody forces you to use those interim releases. You can stay with the LTS that come out every 2 years (roughly comparable to Windows versions plus service pack releases).

So if you need a proprietary driver for your needs - stay with Lucid and then upgrade to 12.04. Or pick an interim release that happens to have a working proprietary driver for your needs. But don't argue to hold back development in favour of proprietary drivers that hopefully will be a thing of the past soon anyway. Nvidia is the last holdout.
Intel went open ages ago. AMD(ATI) is busy doing the same.

In short - either 10.10 will have the drivers you need - or you can stay with the last version that did.
That there is trouble during alpha and sometimes into beta is normal and not a big deal.

p.s. I played games (mostly via wine) on Linux for years on a NVidia card. The proprietary NVidia drivers were updated for the Ubuntu release every single time.
ATI/AMD used to be bad news for gaming as the proprietary driver was never to to scratch - but they went open source right after AMD bought ATI. The open drivers are already in good shape and I expect them to be gaming capable in a few months (which is why I switched to AMD card with my latest computer).

---

### Post by Yfrwlf on 2010-09-10
> **Sophont said:**
> In short - either 10.10 will have the drivers you need - or you can stay with the last version that did.
That there is trouble during alpha and sometimes into beta is normal and not a big deal.

Not a big deal, but still not ideal.  You shouldn't be held captive by a distro company, or anyone.  If a user had to use a particular version of Linux, a version which didn't contain a certain driver, but found the driver someplace else, they should be able to easily install it without issues, much like Windows users enjoy for the most part.  I can give lots of examples of this scenario happening.  There may be some older version of a particular program someone wants to stick with due to the newer one being a resource hog for instance.

Ideal would be to have a standardized API/ABI so that you can easily install any driver on any Linux and Xorg, at the very least have forwards compatibility.  Newer drivers can utilize newer Xorg ABIs, but there is no reason to constantly break all of the old APIs/ABIs each time.  If you think there is, please explain why it is impossible to come up with a common language at some point in Xorg in order to provide an unchanging standardize interface.

So in short, no, I don't buy the "it's constantly evolving and has so many new features" argument.  When is it going to stop evolving?  Never, I hope.  All programs which are open source and get lots of attention evolve.  That doesn't mean it is completely impossible to have a plugin/module, API, or ABI system to have a common and standardized method for communication.

---

### Post by cariboo on 2010-09-10
We had a stable ABI when X11 was used, then everyone complained that it was never upgraded, You can have one or the other, updates, bug fixes and new features or just bug fixes and no new features. The OEM's are well are of when a new version of xserver-xorg is about to be released, Nvidia seems to be able to keep up, it's just ATI/AMD that's the problem. If you want a fairly stable version of Ubuntu stick with the LTS releases, if you want new features and new programs go with the interm releases, but wait until at least the RC before installing, unless you are willing to solve problems and report bugs.

---

### Post by Yfrwlf on 2010-09-10
> **cariboo907 said:**
> We had a stable ABI when X11 was used, then everyone complained that it was never upgraded, You can have one or the other, updates, bug fixes and new features or just bug fixes and no new features. The OEM's are well are of when a new version of xserver-xorg is about to be released, Nvidia seems to be able to keep up, it's just ATI/AMD that's the problem. If you want a fairly stable version of Ubuntu stick with the LTS releases, if you want new features and new programs go with the interm releases, but wait until at least the RC before installing, unless you are willing to solve problems and report bugs.

Okay, well I still don't understand what evidence there is to support the notion that you simply CANNOT have an X server which has a standardized driver interface AND have features at the same time.  Maybe that is the way X is made *now*, and this is impossible with X *now*, but I just seriously wonder if it is possible to have a display server have both: features and updates, and a standardized driver interface that is at least forwards-compatible.

I know what you're saying is the status quo, believe me, I'm just questioning the reasons for it.  Is anything in software truly impossible?  I don't think so.  I think there probably is a solution that would give us a display server with both features/improvements and standards.

---

### Post by cariboo on 2010-09-11
On the other hand why should the xserver devs change their development model to suit one manufacturer. ATI has a long history of not being able to keep up with new developments. They have always been a couple of steps behind. I used to use ATI exclusively, but got tired of putting up with broken drivers all the time. 

When we got the notification 4 weeks ago that there was going to be X server breakage, there was a work around from Nvidia within a day, we're still waiting for anything from ATI/AMD. 

Maybe it's time for ATI/AMD to change their development model to suit the times, notice that they have zero to very little presence on the Apple side of the equation either, as Apple uses a modified xserver too.

---

### Post by PGHammer on 2010-09-11
> **cariboo907 said:**
> On the other hand why should the xserver devs change their development model to suit one manufacturer. ATI has a long history of not being able to keep up with new developments. They have always been a couple of steps behind. I used to use ATI exclusively, but got tired of putting up with broken drivers all the time. 

When we got the notification 4 weeks ago that there was going to be X server breakage, there was a work around from Nvidia within a day, we're still waiting for anything from ATI/AMD. 

Maybe it's time for ATI/AMD to change their development model to suit the times, notice that they have zero to very little presence on the Apple side of the equation either, as Apple uses a modified xserver too.

However, nVidia has a *record* of custom and one-off driver development (they still have multiple binaries based on GPU line that are *active*, which AMD dropped this year); ATI (either before or since their acquisition by AMD) does not.

I'm referring strictly to Linux, not Windows.

---

### Post by henwyn on 2010-09-11
So if one has borked ones xorg server, either by trying to install fglrx or by upgrading from Lucid with fglrx installed, is there a formula for fixing things or are you stuck with reinstalling. I know from experience that removing fglrx and reinstalling xorg doesn't do the trick. I've got an instance of this that I'm still fiddling with but I don't have much time to put into fixing things right now and I figure we'll be getting more calls for help from this as time goes on and Maverick inches closer to release.

---

### Post by PGHammer on 2010-09-11
> **henwyn said:**
> So if one has borked ones xorg server, either by trying to install fglrx or by upgrading from Lucid with fglrx installed, is there a formula for fixing things or are you stuck with reinstalling. I know from experience that removing fglrx and reinstalling xorg doesn't do the trick. I've got an instance of this that I'm still fiddling with but I don't have much time to put into fixing things right now and I figure we'll be getting more calls for help from this as time goes on and Maverick inches closer to release.

In my case, I had done just that with Maverick (because I was unaware that Xorg 1.9 had snuck in as part of my initial updates from beta 1).  Because Ubuntu normally does not use /etc/X11/xorg.conf, I had to create one after the bork (reboot into recovery mode, then select boot into a root CLI) by re-running "X -configure" and saving the resultant /root/xorg.conf.new as /etc/X11/xorg.conf (using a CLI text-editor; in my case, I went with vi).  That let me (after rebooting) go back into GNOME; from there I removed the (apparently faulty) packages using Synaptic.

Notice that I did *not* have to reinstall xorg.

If you *have* an /etc/X11/xorg.conf already, simply edit and substitute "radeon" for "fglrx" in the Device section.

---

### Post by Yfrwlf on 2010-09-11
> **cariboo907 said:**
> On the other hand why should the xserver devs change their development model to suit one manufacturer. ATI has a long history of not being able to keep up with new developments. They have always been a couple of steps behind. I used to use ATI exclusively, but got tired of putting up with broken drivers all the time. 

When we got the notification 4 weeks ago that there was going to be X server breakage, there was a work around from Nvidia within a day, we're still waiting for anything from ATI/AMD. 

Maybe it's time for ATI/AMD to change their development model to suit the times, notice that they have zero to very little presence on the Apple side of the equation either, as Apple uses a modified xserver too.

Yes, "just following Xorg closely and continually fixing their drivers" is one solution, but is that the best solution?  Having a Xorg with a standardized driver interface would mean that wouldn't be required, and that it would take less effort by developers to support Xorg, lower the barrier to entry for Linux graphics, and allow a lot less pain for users and allow them to be more free.

But I guess Xorg just wasn't designed with that feature.  I hope it does adopt such a feature in the future though.  It's not like they'd have to worry about breaking compatibility if they did since it's already always broken :lolflag:

---

### Post by cariboo on 2010-09-11
The only place the problem shows up is in testing versions, If you want stable abi's, stick with the LTS releases.

---

### Post by Yfrwlf on 2010-09-11
> **cariboo907 said:**
> The only place the problem shows up is in testing versions, If you want stable abi's, stick with the LTS releases.

ODF is a stable API. =P

Yeah yeah a format is a poor example, okay then OpenGL.  You can still run OGLv1 and 2 programs even if you have 3 and 4 compliance, because it is forwards compatible.  Why can't a similar API scheme be used for Xorg?

---

### Post by cariboo on 2010-09-11
I guess a better place to ask your questions, would be on the mailing list, you can sign up for it [here]("http://lists.freedesktop.org/mailman/listinfo/xorg").

---

### Post by Yfrwlf on 2010-09-12
> **cariboo907 said:**
> I guess a better place to ask your questions, would be on the mailing list, you can sign up for it [here]("http://lists.freedesktop.org/mailman/listinfo/xorg").

Ask questions with actual developers who might know the answer, are you crazy?? ;)

Just kidding, thanks for the link!

---

### Post by mstrelan on 2010-09-15
Catalyst 10.9 drivers are released - does this help?

---

### Post by Noz3001 on 2010-09-15
> **mstrelan said:**
> Catalyst 10.9 drivers are released - does this help?

Downloading the BIN file from the website. Lets see what happens.

EDIT:
```
Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-21-generic:; make sure that the version is being
correctly set by --iscurrentdistro
```

=[

---

### Post by jfernyhough on 2010-09-15
That sounds like a "wrong" error to have with 10.9. Have you definitely downloaded the 10.9 .run and not 10.8? 10.9 builds fine for me on .35 (and .36 with a patch), not that it works with xorg-server 1.9.

( [http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872) )

---

### Post by Noz3001 on 2010-09-15
> **jfernyhough said:**
> That sounds like a "wrong" error to have with 10.9. Have you definitely downloaded the 10.9 .run and not 10.8? 10.9 builds fine for me on .35 (and .36 with a patch), not that it works with xorg-server 1.9.

( [http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872) )

Definitely 10.9. Guess I'll have to wait a bit more for it to work with 1.9

---

### Post by nilarimogard on 2010-09-24
An update to fglrx in Maverick brings support for xorg 1.9 and kernel 2.6.35/36. See [here]("http://www.webupd8.org/2010/09/fglrx-finally-works-with-ubuntu-1010.html").

---

### Post by ronparent on 2010-09-26
Yes, fglrx for Maverick is here. There are changes in behavior, however that have to be accommodated!

If you were operating with multiple monitors uncloned before, the ati control center willl initially come up with both monitors on a cloned desktop and will crash whenever you try to change it. You will have to change your System>Preference>Monitor setting to unclone your monitors and reset your original display resolutions before you can use the ATI control center to reset your displays. No comment if the change is for the better or not - but it is a change!

So far, I like what I see.

---

### Post by Glaucous on 2010-09-27
It seems like when installing the fglrx 780 packages I don't have working aticonfig or amdcccle, and without aticonfig I can't create a working xorg.conf.

Any ideas here?

---

### Post by thezood on 2010-09-27
> **Glaucous said:**
> It seems like when installing the fglrx 780 packages I don't have working aticonfig or amdcccle, and without aticonfig I can't create a working xorg.conf.

Any ideas here?

Did you run this?
```

sudo aticonfig --initial

```

That did the trick for me. Couldn't get HDMI output to work though...

---

### Post by Glaucous on 2010-09-27
aticonfig didn't work, because it did not exist. However I just installed Ubuntu (KDE wasn't very fast), and this time I'm not using any beta backports. :)

---

### Post by thezood on 2010-09-28
Does HDMI output and dual screen work for you guys? It doesn't even detect my HDTV when using FGLRX, works fine with the open source driver.

---

### Post by sonicb00m on 2010-09-29
HDMI does not work for me. Only get a black screen.

---

### Post by sonicb00m on 2010-09-30
aticonfig --initial fixed all for me!

---

### Post by andrek on 2010-09-30
Quick question. Does the fglrx driver work on Maverick Release Candidate installation without having to tweak much with it?

---

### Post by ktp on 2010-09-30
if you are asking if latest fglrx driver in Maverick repository support latest X, then yes.  If fglrx supports your card, then it should just work in RC.

---

### Post by tanari on 2010-10-02
after installing fglrx drivers I have white screen after logon, no menus, buttons, etc...


Ubuntu 10.10 RC
radeon 5750

---

### Post by rajeev1204 on 2010-10-02
> **tanari said:**
> after installing fglrx drivers I have white screen after logon, no menus, buttons, etc...


Ubuntu 10.10 RC
radeon 5750


Did you install from hardware drivers ? or from website ? Make sure you uninstall any old fglrx installations.

---

### Post by tanari on 2010-10-02
from hardware drivers ubuntu app

I tried to remove fglrx, now after logon monitor goes to sleep :(.

---

