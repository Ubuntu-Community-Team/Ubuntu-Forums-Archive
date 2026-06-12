---
title: "Maverick and Amarok 1.4:  Problems"
date: 2011-01-08
forum: Multimedia Software
---

### Post by Cleanville on 2011-01-08
I just successfully installed UBUNTU / Linux for the first time today (with some help from this forum).

The reason I did this was that I wanted to try out some scripts in Amarok 1.4 (not Amarok 2, but Amarok **1.4**).  This is turning out to be difficult to go on my 10.10 maverick installation, which seems to want amorak 2.

Would it be better for me to install and older version of UBUNTU in order to get Amarok 1.4.  Would this even work?  How far back would I have to go?

---

### Post by Chronon on 2011-01-08
It was forked a while ago as Pana.  

[http://ubuntuforums.org/showthread.php?t=1400314](http://ubuntuforums.org/showthread.php?t=1400314)

---

### Post by BicyclerBoy on 2011-01-08
There are a couple of problems getting old amarok to go with 10.04

Has a clash with later mysql5.1..

[http://www.dwasifar.com/?p=1111](http://www.dwasifar.com/?p=1111)

This ppa has lucid build it may have maverick..
[http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu)

It needs package libmysqclientl15-off   installed version  5.1.30really5.0.83-Oubuntu3
I think this has to be forced because it was a *buntu 8.10 package.

---

### Post by Cleanville on 2011-01-09
> **Chronon said:**
> It was forked a while ago as Pana.  

[http://ubuntuforums.org/showthread.php?t=1400314](http://ubuntuforums.org/showthread.php?t=1400314)

Un fortunately Pana cannot do the things (specifically scripts) that are drawing me to explore LINUX in the first place.

That is why I am thinking it would be easier to install an old version of UBUNTU where all the Amarok 1.4 dependencies and all that other stuff that is easy for you, but difficult to me, is already taken care of.    Can you switch to an earlier version of UBUNU?  How far back should I go so that Amarok 1.4 and its scripts have the maximum chance of working with as few terminal line commands as possible?

---

### Post by Cleanville on 2011-01-09
> **BicyclerBoy said:**
> There are a couple of problems getting old amarok to go with 10.04

Has a clash with later mysql5.1..

[http://www.dwasifar.com/?p=1111](http://www.dwasifar.com/?p=1111)

This ppa has lucid build it may have maverick..
[http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu)

It needs package libmysqclientl15-off   installed version  5.1.30really5.0.83-Oubuntu3
I think this has to be forced because it was a *buntu 8.10 package. 

yeah, but see this is super difficult who someone, like me who started using LINUX for the first time yesterday.

Wouldn't it be easier to just take the whole OS back in time so that RUBY and Perl and SQL and FESTIVAL and ESPEAKER (and heavens knows what else) are in correct versions for the Amarok 1.4 to run the scripts that I strongly desire to run?

Maybe taking the OS back in time is not the easiest way to do that.  If not, why not?

---

### Post by BicyclerBoy on 2011-01-09
You could use 9.10 as this works quite well & is still in common use.
(And uses Grub2 bootloader)
Going back is a complete new install or liveCD or another disk or partition.
(Dual/triple boot)

If you are after long term stable OS then the LTS version is for you.
8.04LTS 10.04LTS

There is less churn on these versions but still bug fixes..
8.04 LTS is history tho..

You could email the ppa maintainer & ask nicely for a maverick version ..

---

### Post by Cleanville on 2011-01-09
> **BicyclerBoy said:**
> You could use 9.10 as this works quite well & is still in common use.
(And uses Grub2 bootloader)
Going back is a complete new install or liveCD or another disk or partition.
(Dual/triple boot)

If you are after long term stable OS then the LTS version is for you.
8.04LTS 10.04LTS

There is less churn on these versions but still bug fixes..
8.04 LTS is history tho..

You could email the ppa maintainer & ask nicely for a maverick version ..

I think that Amarok 2 (the one I am trying to avoid) came out in 2008.  Is 8.04 LTS prior to that?

When you say that 8.04 LTS is "history" do you mean that it is impossible to get or impossible to run, o are you just saying that it is quite old?

---

### Post by mc4man on 2011-01-09
Even though 10.04 was outdated multimedia wise the day it released, it may well  serve your purposes. It's still currently supported and you can use as long as you wish, even after support ends.

What you may wish to try first is building amarok 1.4 - fairly easy and well enabled.
Whether it will run all your scripts you'd have to try and see.

Currently have 1.4 running well in 10.10 and 11.04, don't use scripts much but the script manager is there and works (installed a lyric script which works fine

This thread describes for 10.04, read thru, I mention some 10.10 stuff in various posts (10), if deciding to try and don't understand or have error(s) just post

[http://ubuntuforums.org/showthread.php?p=9753783](http://ubuntuforums.org/showthread.php?p=9753783)

---

### Post by Cleanville on 2011-01-09
> **mc4man said:**
> Even though 10.04 was outdated multimedia wise the day it released, it may well  serve your purposes. It's still currently supported and you can use as long as you wish, even after support ends.

What you may wish to try first is building amarok 1.4 - fairly easy and well enabled.
Whether it will run all your scripts you'd have to try and see.

Currently have 1.4 running well in 10.10 and 11.04, don't use scripts much but the script manager is there and works (installed a lyric script which works fine

This thread describes for 10.04, read thru, I mention some 10.10 stuff in various posts (10), if deciding to try and don't understand or have error(s) just post

[http://ubuntuforums.org/showthread.php?p=9753783](http://ubuntuforums.org/showthread.php?p=9753783)

This seemed to work.

new problem:  the amarok 1.4 indicates that the scripts I want are "already installed," but they do not show up in the "installed scripts" menu.  This may be because I may have tried to install them in Anarok 2 (which did not work of course).  This is pretty much unrelated to the problem of getting Amarok 1.4 in UBUNTU 10.10, but if you have any words of wisdom on this . . .

---

### Post by mc4man on 2011-01-09
As mentioned not really big on the amarok scripts. The one I did install (116725-ultraLyricWiki-0.4.amarokscript.tar.gz) I just put in Documents as is (not extracted) and the script manager found and installed
After that a folder was created in ~/.kde/share/apps/amarok/scripts, maybe delete the whole amarok folder itself and start fresh

Also maybe remove the ~/.kde/share/config/amarokrc file or at least ck.

---

### Post by Cleanville on 2011-01-11
well, I am not where I want to be with Amarok 1.4, but this post did solve the problem I brought up in this thd, so:

(i)  THANK YOU; 

and

(ii) marking it SOLVED.

---

### Post by mc4man on 2011-01-11
you might want to post your continuing issue(s) into the thread I linked, it's possible that at some point someone may have some workable solution(s) for you.

edit; if you have a link or two to a nonworking script post it/them up

---

### Post by Cleanville on 2011-01-11
> **mc4man said:**
> you might want to post your continuing issue(s) into the thread I linked, it's possible that at some point someone may have some workable solution(s) for you.

edit; if you have a link or two to a nonworking script post it/them up

well, the problem does not seem to be the script, but that I can't get to the script from AMAROK 1.4 because Amarok 1.4 sort of thinks it is installed (for purposes of re-installing it), but won't show it in the "installed scripts" menu.  It is not like AMAROK 1.4 is actually trying to run the script and failing at that.  Can't get AMAROK to try to run it.

---

### Post by mc4man on 2011-01-11
Did you remove the amarok conf. files as I mentioned previously?

Are you using gnome or kde? (wasn't this thread is tagged kde at some point?

---

