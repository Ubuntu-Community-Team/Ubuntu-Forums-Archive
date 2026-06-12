---
title: "metacity/gnome twinview placement problem. Still a problem"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by TLE on 2006-06-17
Hi every body
I have the exact same problem which is described in [this thread]("http://ubuntuforums.org/showthread.php?t=78838&highlight=metacity+windows+placement"), but since it is a 5.10 thread i was sort of hoping something had changed in the meantime so that this could be fixed.

So anyway, just to sum up here also. I'm running a wide desktop (Xinerama) configuration which expands onto my tv. The problem is that when there is already a window open on my monitor, eg. a console and I use it to start firefox, then metacity decides that it would be better to place that on the tv because there is already one window open on the monitor (which of course would be correct if I was using the widedesktop with 2 monitors rigth next to each other), but because it is a TV I don't want it to open *anything* on the tv. I'll move whatever needs to go there my self.

So if there is a way to do this, eg. tell metacity to always open new windows on the screen where the mouse is, that would fix my problem. Does anybody have any ideas on how to fix this.

PS: In the other thread there is a link to [this site]("http://www.vislab.uq.edu.au/research/accessgrid/software/fedora/related/") where there are rpm packages where this feature is included, so it should be possible, I'd just rather not try to reinstall metacity form rpm's...

---

### Post by AskHL on 2006-06-17
Hello TLE, I did some research without having consulted the other thread you linked. Maybe devilspie can do what you want.
```

sudo apt-get install devilspie

```
This extension to the metacity window manager enables the possibility to do stuff with windows when they are opened. For example set their location if they are on the wrong screen (meaning they have too large x-coordinates  -- I assume the screens use a common coordinate system but I don't really know).

Hope it helps.

I found the program by consulting the wikipedia article on metacity and looking in the controversy section.

---

### Post by TLE on 2006-06-18
Thanks for your reply AskHL.

I've spend all of last night getting Devilspie up and running and even though it is a really cool program it does unfortunately not solve my problem. The problem seems to be that even though the desktop is one large one, Devilspie only recognises the one display it is placed on initally (and with a coordinatesystem of its own), and so it is not possible to get it to move something from display to display.

So if anybody has any other ideas, don't be shy.

---

### Post by blitzd on 2006-07-04
I've got this same problem, it's quite irritating really because I really only use my second monitor for reference material and don't want windows randomly opening on it. I did see that there was a patch here that at least adds some options to metacity which may help, but it's quite outdated:

[http://home.uchicago.edu/~chad/metacity/](http://home.uchicago.edu/~chad/metacity/)

...And unfortunately it appears from this bug thread that the metacity devs feel the current behaviour is acceptable for the majority of users:

[http://bugzilla.gnome.org/show_bug.cgi?id=151818](http://bugzilla.gnome.org/show_bug.cgi?id=151818)

However, I've found that I can beat the placement algorithm in my case (and probably yours too)... Simply open an app and maximize it on that screen - the rest of my apps open on my main screen after that.

---

### Post by RawMustard on 2006-07-05
I think this will always be a problem with Gnome.  From all that I've read on the subject over the years, I get the distinct impression the way it is, is a bit of a quick hack to avoid the complexities of proper window management.  I mean, to be able to know where and what all windows are doing or have done in the past is a huge coding job from my understanding, something that non payed developers are unwilling to undertake and the maintenance associated with it into the future would be huge.

Oh well, looks like using Gnome with large or multiple screens will be a game of BlunderbussYourScreenWithFlyingWindowsAnywhereAndEverywhereInNoLogicalManner ](*,)  Time to stock up on mouse pads, you'll wear one out a week having multiple monitors!

Oh and it would appear that compiz will work the same way :(

---

### Post by blitzd on 2006-07-07
Well, in the end window placement (and any other application specific preferences) really should be the responsibility of the applications themselves. Thats how it seems to work on any other platform I have used. I think the algorithms that Metacity uses could use some improvement though, because I honestly haven't had this problem on similar setups with Windows or Mac OS X. There should at least be an option to turn off the 'search for free space' portion of the algorithm - I would be more than happy if every window opened centered or cascading from the top left on my -main- display. But for all I know there is a way to that and I just haven't found it yet...

Anyways, it seems to be implementing a slew of odd algorithms that the devs are against - maybe they wouldn't be so against simple options to disable portions of the existing algorithm.

---

### Post by TLE on 2006-07-13
Thanks for you replies

blitzd: I know about the "open maximized window on other screen "fix"". I'm not really satisfied with it though but thanks for supplying it.

RawMustard and blitzd: It's just wierd. Somewhere in that huge bugthread one of the developers comment that he fixes it by simply changing a couple of lines of code. Now why couldn't that change be available as as option in some configuration file. Oh well, probably just a little dissapointed since I really like GNOME otherwise. But this is not good enough for me so I'll be trying something else. I just tried using E16 and that actualle does the trick, but it is IMHO slow and lacks featues, so I'll be reverting to KDE soon. It is a bit ironic though, the reason I like GNOME so much is because it is minimalistic per default and will only grow as big as you let it yourself and now I'm forced to leave it because it is lagging a feature....

PS: please let me know if you hear about a fix for this, I don't really wan't to use KDE...

---

### Post by ookami on 2006-08-05
From [this]("http://www.vislab.uq.edu.au/research/accessgrid/software/fedora/related/") link that I posted in the previous thread and that TLE included in his first post:
> The Metacity RPMs below contain a one-line patch which forces Metacity to use the current Xinerama screen for window placement.

It really can't be that hard to do a custom Metacity package that includes this patch. As I said in the previous thread, I used this in Fedora and it worked **PERFECTLY**, exactly as you would want and expect it to. Does noone with dpkg-skills have this problem?

---

### Post by TLE on 2006-08-06
ookami: No I suppose you're right. I was sort of hoping it didn't have to come to that, but I will try and investigate and see if I can figure out what the patch is and how to do a custom package. Thanks for the hint.

---

### Post by TLE on 2006-08-15
IT WORKS IT WORKS ..... !!!!!

I followed up on ookami's advice. So I found the site that contains the patched .rpm. I contacted a very friendly fellow there per e-mail and told him that I was interested in making .deb's with the same change and asked him if he knew who I could contact that could help me with that. So he sent me tha patch but also he knew of [this website]("http://www.ailis.de/~k/docs/atilinux/") where there is instruction on how to do it for Ubuntu.

So it was pretty much downhill from there. The only problem is that the patch is for the Breezy version of metacity, so I changed the patch (actually just the line number where the patch is to be applied), and then applied, compiled a new package and installed it and it works. I'm going to write a howto and supply the .deb's but I would very much appreciate if one of you guys would test them first. Please let me know as soon as possible.

---

### Post by ookami on 2006-08-17
bloody BRILLIANT!
With the instuctions and patch on that site it was a 10 minute edit-compile-install and it works perfectly. I'm bloody extatic!
We really should try and make this patch go into the official Ubuntu Metacity, I can't imagine someone actually wanting it to work in the current default manner.

Nice digging TLE, high five! ;)

---

### Post by TLE on 2006-08-17
Great. I think the first step will be a howto in the forum. With

1. A modified path and link to the instructions on that page
and/or
2. Links to precompiled packages (For those that don't want to compile it themselves)

Do you have any packaging experience ?
I'm wondering if the packages we create as a part of that guide contain the same dependencies as the original. And if so if all other could just use some of the packages we have created ?

Regarding trying to make it a part of official Ubuntu. I thought about that. I don't know, maybe someone use it the way it is, after all there must be some reason for the policy og the metacity team. But I was thinking that Ubuntu in general have those "global key" options. I don't know their exact name but some GNOME options are only available editing some kays, sort of like reg keys in windoze. Maybe it could be implemented as an option like that.

So but anyway, first things first. As soon as I'm finished with a reinstall I start a howto.

---

### Post by ookami on 2006-08-17
Sadly I have no dpkg packaging experience apart from following a few guides like the one we just used and as you pointed out I wonder if the dependancies are ok or not. We did use the official ubuntu source package including the package definition files so there is a posibility that the dependancies are fine.

As for what sould be the default behaviour, Metacitys window-placing algorithm is decidedly stupid and Havoc Pennington who initially wrote it has explained it by saying that window placement should be handeled by the applications themselves (wether he is right is an entierly different discussion and I have no particular opinion on the matter).
Anyway the current default is guaranteed to cause more problems and annoyances than the patched behaviour as the most common twinview setup without a doubt is a monitor + TV and not two monitors. Also I've seen people with two monitors go balistic over this "feature" as well. And finally the people who do indeed need/want the unpatched behaviour just have to point the cursor to the desired screen when windows are spawned and eeeeeverybody happy. ;)
I guess I should have put this rant in at bugreport instead of on the forum but oh well. ;)

---

### Post by TLE on 2006-08-17
Concerning packaging. I think there's an irc for Ubuntu developers, I'll try and find it and ask there.

> As for what sould be the default behaviour, Metacitys window-placing algorithm is decidedly stupid and Havoc Pennington who initially wrote it has explained it by saying that window placement should be handeled by the applications themselves (wether he is right is an entierly different discussion and I have no particular opinion on the matter).
Anyway the current default is guaranteed to cause more problems and annoyances than the patched behaviour as the most common twinview setup without a doubt is a monitor + TV and not two monitors. Also I've seen people with two monitors go balistic over this "feature" as well. And finally the people who do indeed need/want the unpatched behaviour just have to point the cursor to the desired screen when windows are spawned and eeeeeverybody happy.
I guess I should have put this rant in at bugreport instead of on the forum but oh well.

Oh weel, we're doing something about it now. I absolutely agree with you about how stupid the default behaivior is, and the only reason I made the "as option" suggestion is not to step on any toes, if, by some miracle, there actually are some that like it that way. Ok so there are a couple of options. We could make poll, to see if there are anybody who wants it the way it is, and then it could serve as documentation when we make the request ? Or maybe we should just write Ubuntu's maintainer of metacity and hear what he has to say about it ?

---

### Post by ookami on 2006-08-17
Doing a poll in the Edgy-forum may be a good idea. But there might not be that big of a turnout since the problem does not affect people who don't use twinview (the overwhelming majority).

---

### Post by TLE on 2006-08-24
Now the HOWTO containing the solution for this problem is ready, check it out at [http://ubuntuforums.org/showthread.php?t=242502]("http://ubuntuforums.org/showthread.php?t=242502")
Regards TLE

---

