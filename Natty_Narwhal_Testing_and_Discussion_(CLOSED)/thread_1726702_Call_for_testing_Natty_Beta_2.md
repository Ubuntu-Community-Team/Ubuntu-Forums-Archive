---
title: "Call for testing Natty Beta 2"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-04-11
This just in:

> Hi everyone!

Natty Beta 2 is due this week and the first candidates will be ready for
testing on the ISO tracker starting from Tuesday, 12. As usual we'll be
asking everyone on the QA team to participate in the image testing to
ensure we have good test coverage.

The procedures for testing ISO images and reporting results are
explained on [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

You can start syncing your ISOs so you are prepared when the Release
Team start posting images to the ISO tracker.

Test results will be tracked on [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

You may have accounts on the tracker from last time. Please register if
you are new to this.

Please let us know if you have any questions.

We will coordinate testing in #ubuntu-testing on freenode. Please, go
there often to see what others are testing or what needs to be tested.

Thank you very much for your help and happy testing!

-- Jean-Baptiste irc: jibel 

---

### Post by kansasnoob on 2011-04-11
Holy crap! I just got my iso/upgrade testing notices. I didn't expect this until tomorrow :p

---

### Post by KegHead on 2011-04-11
Hi!

Looks like fun!

KegHead

---

### Post by kansasnoob on 2011-04-11
Wow, big changes too it looks like. I tried an image yesterday so I was fairly up-to-date, but I'm zsyncing now and it shows only 76.1% complete :D

I'm feeling like a complete dummy ATM, I usually have a Maverick ready to test the Natty upgrade but I goofed :(

Actually testing is going to be somewhat more complex than ever since the live-installer will also offer an upgrade option if applicable, and they added the Wubi option if applicable.

Wow! The QA Team may even have to modify the testing instructions.

I find that as time goes along I get more and more serious about making sure everyones first impression is a good one. Now, with the introduction of Unity as default we'll hear lots of applause and boos, but I don't care that much about the DE!

IMHO there are enough DE options ATM to satisfy everyone ATM.

---

### Post by RJ12 on 2011-04-11
I'm finding Natty to be really good and Unity to be very polished, especially with these past updates :) I hope to be trying out Beta 2 when it is available :)

---

### Post by kansasnoob on 2011-04-11
One bug reported:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/758236](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/758236)

I know I whine too much sometimes but when push comes to shove I do both :D

Maybe I should change my "handle" to PushMe-PullYou :lolflag:

---

### Post by ranch hand on 2011-04-12
All I am testing is the Xubuntu Live Session and it works just great.

I have an install from last round that is just now nicely tweeked so I am not going to reinstall.

The ISO booted like a charm, every thing I could mess with in 30 minutes worked great.  All the controls and settings seemed to work.

A very slick Live CD.  Folks trying it out should love it.   

Xubuntu has come a long way in the last 18 months.

---

### Post by ELD on 2011-04-12
Downloading now to see if this one will work, downloaded yesterday's daily iso and it wouldn't boot, so hopefully this will fare a bit better :)

---

### Post by ngsupb on 2011-04-12
have to admit Natty becomes more and more stable. First time when I installed (alpah3 ) it had a lot of crashes.

I can't notice any major  issue now with the latest upgrades. Good job!

---

### Post by ELD on 2011-04-12
> **ngsupb said:**
> have to admit Natty becomes more and more stable. First time when I installed (alpah3 ) it had a lot of crashes.

I can't notice any major  issue now with the latest upgrades. Good job!

Yeah this beta cd test booted up fine and any issue i had before with Unity has gone, looks like Unity will actually work for me on release, sweeet!

---

### Post by Grendel336 on 2011-04-12
*(noob alert)*

Will Beta 1 update to Beta 2 using the update manager?

---

### Post by ngsupb on 2011-04-12
> **Grendel336 said:**
> *(noob alert)*

Will Beta 1 update to Beta 2 using the update manager?

ofc 

This question should be sticked for all releases :S

---

### Post by kansasnoob on 2011-04-12
> **ngsupb said:**
> ofc 

This question should be sticked for all releases :S

**Common Problems / Frequently Asked Questions About Testing**

[http://ubuntuforums.org/showthread.php?t=1594833](http://ubuntuforums.org/showthread.php?t=1594833)

---

### Post by KegHead on 2011-04-12
"All I am testing is the Xubuntu Live Session and it works just great.

I have an install from last round that is just now nicely tweeked so I am not going to reinstall.

The ISO booted like a charm, every thing I could mess with in 30 minutes worked great. All the controls and settings seemed to work.

A very slick Live CD. Folks trying it out should love it. 

Xubuntu has come a long way in the last 18 months."

I'm trying this today. I love Xubuntu! It's my backup distro!

KegHead

---

### Post by kansasnoob on 2011-04-12
I really put myself behind the eight ball this time :(

I usually try to be prepared for this, eg; having an existing Maverick installed, updated, and modified to use it for an upgrade test, this time I was very ill prepared.

I also probably need to contact the QA Team about possible changes needed to our test case scenario regarding the new default to Wubi if 4 primary partitions exist, and the new "upgrade" path offered if only one older Ubuntu is seen on the drive(s).

Lots of changes:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-April/000841.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-April/000841.html)

[https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1_Automatic_partitioning_o_8475526086986065](https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1_Automatic_partitioning_o_8475526086986065)

Almost mind boggling :D

One thing is for sure, we often gripe about the devs not listening, or at least I do, but when you look at docs like the latter it becomes obvious that these people really work their heinies off trying to improve things.

---

### Post by KegHead on 2011-04-12
Hi!

Downloaded and working perfectly.

KegHead

---

### Post by kansasnoob on 2011-04-12
With all of the changes to ubiquity I posted this message to all members of the Testing Team:

> I've recently been struggling with all of the changes in ubiquity, some
of which I was not totally aware of until Evan Dandrea provided this
link:

[https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1](https://docs.google.com/View?id=dfkkjjcj_101gnkrpg5v#4_5_1)

My main concern is the addition of providing a Wubi option if 4 primary
partitions exist, and also the new "installer upgrade" path as described
fairly simply here:

[https://lists.ubuntu.com/archives/ubuntu-devel-](https://lists.ubuntu.com/archives/ubuntu-devel-)
announce/2011-April/000841.html

I'm just wondering if we need to add those two specific options to the
test list?

I just performed my first "upgrade via live CD" test (which I'd really
not known how to do until Evan provided the first of those links) and it
worked perfectly, but there is no way to report success or failure.

ATM I can't conveniently create the proper scenario to try the new Wubi
offering but perhaps other testers would be able to do so.

Just food for thought, I'm very impressed with how well the whole QA and
Testing teams function. I'm often amazed.

Thanks in advance,

Lance

You'll have to copy-n-paste that second link :(

I also somehow double posted that message, so now I've reaffirmed the fact that I'm a dufus :P

---

### Post by XubuRoxMySox on 2011-04-12
> **ranch hand said:**
> 
Xubuntu has come a long way in the last 18 months.

Omygoodness, YES!! It's been a well-kept secret 'til now, but Xubuntu has seriously trimmed down! It's lean and mean and fast! Mind-bending speed; superb, elegant beauty; and a model of simplicity without sacrificing function and versatility.

Xubuntu Natty absolutely rocks the universe!

Robin

---

### Post by Wobblybob on 2011-04-12
Just Testing the Beta 2 Xubuntu now, and I agree is great and the way forward for those of us not wanting to go down the Unity path.

---

### Post by KegHead on 2011-04-12
Yes, Xubuntu is cool!

It's my backup distro if we lose gnome.

11.04b2/classic/2.6.39-999

KegHead

---

### Post by kansasnoob on 2011-04-12
Just got the "new build" message :D

Round two begins now .......................

---

### Post by kansasnoob on 2011-04-13
Test #2 died quickly due to a network configuration problem, so I moved right on to test #3 this AM.

I think it looks pretty good, not perfect, but pretty darn good :D

I know there will be those who simply love Unity, and others who truly hate it, and a lot of others that will have a gazillion questions - but IMHO it's not that bad once you spend a little time with it.

I find window management to be the biggest obstacle and I think Luke Benstead did a really good job explaining that at Ayatana:

> Hi guys,

I've been using Unity on my main desktop for a few days now, and I'm
getting incredibly frustrated with the behaviour of switching between
multiple windows of the same app. Say for example I have three windows
open, and I minimize two of them I can't find a way to get to one of
the minimized windows without restoring them all. Am I missing
something obvious?

What I'd like to happen is clicking the launcher should display all
three open windows, and when I select the one I want, those that were
minimized should remain minimized. The problem extends when you
consider that all 3 windows may be minimized, in which case clicking
the launcher restores all of them! I can't think of a single occasion
where I'd want that to happen.

Is there any chance of getting this behaviour looked at? It's making
Unity unbearable, as I'm continually re-minimizing windows I don't
need.

My recommendation would be that if you have more than 1 window open,
clicking the launcher button would display all the windows and then
all but the selected one would return to its previous state. This
would make the behaviour predictable, it took me a while to figure out
what the current logic actually was!

Thanks,

Luke.

The next biggest thing to me is the top panel. I think that should be more easily customized, including it's position and the ability to add applets like sensors-applet and inhibit-applet. Right now the top of the screen is too "busy" while nothing is going on at the bottom.

And the workspace switcher is slightly annoying, why the need to open a window to select which workspace you want?

IMHO Unity is more suitable for a tablet than a desktop so I'll be sticking with classic, but that is just my choice :D

---

### Post by KegHead on 2011-04-13
Hi!

I came to the same conclusion within minutes of working w/Unity.

It's nice, but classic is perfect for me.

KegHead

---

### Post by KegHead on 2011-04-13
Huh?

---

### Post by fjgaude on 2011-04-13
> **KegHead said:**
> Huh?

I have found that Unity is a better workflow for what I do than the classic.

I normally have four windows filled with apps. Each has it purpose and usually associated with each other in my graphic design work.

I have all the icons in the left, vertical bar. I click on the app I want and it takes my to the window where the app is.

To get the apps as icons on the vertical bar I use the Applications icon to place each in the window I wish it or they to be. I mark the icon with the left click, "Keep in Launcher".

This results in a setup that is quick, going from one window to another. I'm sold on Unity.

---

### Post by Duncan Williams on 2011-04-13
I am new to Linux and have only had limited experience.
after 20 years of dos and windows and changing to ubuntu about a month ago.
I liked maverick and was getting used to the interface for a few weeks.
Now I have been using unity for a few days.
I found it a bit hard to come to grips with.
I thought `its all there somewhere so just persevere'
After working it out and using it I think it's great.

I can't see me using windows again.

---

### Post by cariboo on 2011-04-13
If you want to discuss your experiences using Unity, please post in the Unity Mega thread in the Cafe, this thread should only be for discussing iso testing.

---

### Post by kansasnoob on 2011-04-14
> **cariboo907 said:**
> If you want to discuss your experiences using Unity, please post in the Unity Mega thread in the Cafe, this thread should only be for discussing iso testing.

Sorry, I guess I led things in that direction, albeit unintentionally.

When I do iso-testing one of the things I try to accomplish is to put my noob shoes on, that is ask myself, "If this were my first experience w/Ubuntu what would I think"?

That's what I was trying to reflect on. I started w/Gutsy after some distro-hopping and if Natty were my first I think it's slick enough I'd still have stuck around :)

I encountered no show-stopper bugs in the 3rd, and what appears to be the last, build ;)

---

### Post by Duncan Williams on 2011-04-14
I am not a tester of natty beta 2.
Sorry if my opinion was off-topic.

---

### Post by andrewabc on 2011-04-14
> **ranch hand said:**
> All I am testing is the Xubuntu Live Session and it works just great.

I have an install from last round that is just now nicely tweeked so I am not going to reinstall.

The ISO booted like a charm, every thing I could mess with in 30 minutes worked great.  All the controls and settings seemed to work.

A very slick Live CD.  Folks trying it out should love it.   

Xubuntu has come a long way in the last 18 months.

Glad to hear xubuntu working good.
Guess I should have noticed this thread earlier and tested to see if unity would work this time (will wait for final beta now). beta1 normal ubuntu would not work at all because of unity (nonstop repeating crashes/freeze once at desktop).

lubuntu beta1 worked great, although missing network icon. Hope they update beta2 today. Works great as web browsing OS.

---

### Post by sanderd17 on 2011-04-16
On my laptop, I'm not able to get past GRUB (backlight problems, tried all kinds of boot options, non worked) and on my desktop, Ubuntu doesn't find the graphical drivers so I get into fallback mode. I can use compiz without problems in ubuntu 10.10.

As a result: I can only conclude that natty still has serious bugs and I can't test unity.

---

### Post by andrewabc on 2011-04-16
With beta2 I was able to get to desktop without anything crashing, and unity works fine. Now I can test it. :)

Although oddly when I went into "proprietary drivers" it said there were none available, even though I have new ati card, and ubuntu 10.10 offers driver.

Still waiting for lubuntu beta2
[http://people.ubuntu.com/~gilir/](http://people.ubuntu.com/~gilir/)

---

### Post by Rasa1111 on 2011-04-16
I havent read all posts in the thread, Im sorry..

But Im wondering..
Is it just me..
Or did Beta 1 seem to work much nicer? quicker, snappier, smoother, etc? 

beta 2 seems quite a bit slower to me.
both run on USB drives.

---

### Post by stragierk on 2011-04-17
So... If the crash handler/reporter crashes while reporting, what do you?

Anyhow, the application responsible for refreshing Unity's list of installed applications crashed / doesn't work. The sidebar panel thingy seems to be stuck in 'show always' at the moment, can't really say there's a clear way to overlook any settings involving Unity. Is this temporarily unavailable or a non-feature?

(I would use Launchpad, but that's just too confusing on a Sunday or even Monday.)

Aside these unfortunate bugs (the reporter app crashing, the sidepanel being stuck on top and the installed application list updater crashing), it does look quite promising. The panel widgets make sense now, wireless worked instantly, soundcard was properly detected and the installation went quite well.

EDIT: Apparently launching a program from the command line and keeping it in the sidepanel (and then launching it from there) seems to bring a program into the list of installed/used applications. Even so, something must have initially gone wrong.

---

### Post by ikt on 2011-04-17
> **stragierk said:**
> (I would use Launchpad, but that's just too confusing on a Sunday or even Monday.)


I find it interesting you perceive Launchpad to be confusing to use, while leaping into the biggest desktop shake up in Ubuntu's history.

For modest bug reporting Launchpad is really (really) easy to use:

- Sign up to launchpad
- if you have any programs crash the crash reporter should automatically collect the required info
- click to submit a report
- firefox will open, login and write a brief comment about what you were doing at the time of the crash.
- click submit
- all done :D

> can't really say there's a clear way to overlook any settings involving Unity. Is this temporarily unavailable or a non-feature?

The power button in the top right > system settings > unity

---

### Post by SeijiSensei on 2011-04-17
The installer for Kubuntu 11.04b2 crashed with a video panic.  See [this thread]("http://ubuntuforums.org/showthread.php?t=1731893") for details.

---

### Post by rougered on 2011-04-17
Hi,
          just updated my sistem (hp tm2-2050) to natty beta2. 

i have severe problems in logging in since the backlight goes off on startup and i have no way of switching it back on.  command line opens (and screen lights on) if i press ctrl-alt-f2 (well also fn on this keyboard)

yesterday i performed an update but the thing got even worst and i had to reinstall. 
trying to update now to see if anything was fixed. Please not that the system has a ati mobility 5470+ intel graphic card

thank you
Riccardo

---

### Post by cariboo on 2011-04-17
Now that beta 2  has been released, I'm going to unstick this thread.

---

### Post by Rasa1111 on 2011-04-18
and Im still wondering if anyone else has found that beta 2 seems soo much slower than beta 1? :??:  lol

---

### Post by stragierk on 2011-04-18
> **Rasa1111 said:**
> and Im still wondering if anyone else has found that beta 2 seems soo much slower than beta 1? :??:  lol
I perceived a significant decrease in speed as well. Before, I had 10.04 32bit installed, now I have the second beta AMD64 installed, so I wasn't too sure at first. Just now however, I noticed that my laptop was really busy, as in full out CPU usage. A quick look at the system monitor showed me that syndaemon, I presume a program belonging to the Unity package, was claiming near 100% CPU usage. Killing it didn't seem to hurt the system. Just to make sure, I switched to Gnome (aka 'Ubuntu Classic').

[QUOTE=ikt]I find it interesting you perceive Launchpad to be confusing to use,  while leaping into the biggest desktop shake up in Ubuntu's history.[/QUOTE]
Well, I've been using Ubuntu for years now and am familiar with most desktop environments. Honestly, Unity's not *that* special. The title/taskbar thing has its spacesaving upsides taken from Apple with a native version of Docky as a sidebar.
> 
For modest bug reporting Launchpad is really (really) easy to use:

- Sign up to launchpad
- if you have any programs crash the crash reporter should automatically collect the required info
-** click to submit a report**
- firefox will open, login and write a brief comment about what you were doing at the time of the crash.
- click submit
- all done :grin:
And that's when the crash reporter crashes. Not much use in filing a report when you can't exactly say what went wrong.

> The power button in the top right > system settings > unity 	
That's not settings, that's an option. Might be that I'm not getting the full Unity experience, but the only thing I can change about Unity is whether or not I want the title/task bar of an application integrated in the upper panel. What would be welcome is a way to set the sidebar's delay in popping up or even disabling it's automatic hiding property. Having the option to put the sidebar to the right would be nice too. It's little stuff like that that makes or breaks the experience with an environment. Also, you can add and remove launchers to the sidebar, but you can't apparently change their order. That's plain stupid.

Anyhow, I'll try to get this Launchpad thing working. Maybe that'll make a difference.

---

### Post by bennachie on 2011-04-18
While I tend to agree that Unity could be seen as a somewhat restricted version of the Mac desktop. and certainly has far too few configuration options at present, I should in fairness point out that changing the order in which the icons appear in the sidebar is really easy (just as it is in the Mac). Click and hold on an application item, drag it distinctly to the right, then move it up or down to where you want it to appear. The other icons will move apart to make room.

---

### Post by Rasa1111 on 2011-04-18
> I perceived a significant decrease in speed as well. Before, I had 10.04 32bit installed, now I have the second beta AMD64 installed, so I wasn't too sure at first. Just now however, I noticed that my laptop was really busy, as in full out CPU usage. A quick look at the system monitor showed me that syndaemon, I presume a program belonging to the Unity package, was claiming near 100% CPU usage. Killing it didn't seem to hurt the system. Just to make sure, I switched to Gnome (aka 'Ubuntu Classic').


 Alright, thanks very much my friend. 
Good to know it wasnt just me.
Much appreciated.  <3

---

### Post by anaconda on 2011-04-18
11.04 beta1 kernel wont boot on my machine (Asus eee PC 1005p) It just hangs, so I wont get any data on why it wont work.

However botin with 10.10:s kernel works, and I can test unity.

Will try to upgrade to beta2 as sooon as I have some extra time.

---

### Post by bennachie on 2011-04-18
For what it's worth, I had no problems installing Natty B2 on my eeePC 701-4G with 1GB RAM (I use an 8GB SDHC card for my /home partition). The only difficulty was that Evolution didn't want to recognise that I only had a 7-inch screen, which became a bit tedious. Evolution works just fine on a 10-inch netbook, but Thunderbird is the better bet with the smaller screen.

---

### Post by stragierk on 2011-04-18
> **bennachie said:**
> While I tend to agree that Unity could be seen as a somewhat restricted version of the Mac desktop. and certainly has far too few configuration options at present, I should in fairness point out that changing the order in which the icons appear in the sidebar is really easy (just as it is in the Mac). Click and hold on an application item, drag it distinctly to the right, then move it up or down to where you want it to appear. The other icons will move apart to make room.
Ah-ha. Dunno how that didn't work before, but now it apparently does. Thank you for the information.

Anyhow, Launchpad and me didn't work out, mostly because I don't know whether I'm talking about a bug or suggesting a new feature. (Thus need to answer the question of Launchpad ticket/report or a mailing list, a concept I've never actually used and which I consider on the same level as telegraphs: I get the principle, but don't know why on earth you'd use it nowadays.)

If a Unity developer would ever happen to browse this, you never know after all, I suggest a division in the 'Installed applications' between system programs/settings and actual user applications. Less clutter, more oversight of what you have and with which applications can be used.

Also, for future beta versions, do make sure to include any libraries / programs needed to report bugs etc. People like me, who only pay half attention to these error messages, don't always understand that the bug reporter can't work because it's missing dependencies. In a beta version, it seems quite essential that this kind of stuff is present out of the (virtual) box.

Nevertheless, I do appreciate the effort that's gone into this so far.

---

### Post by ikt on 2011-04-18
> **stragierk said:**
> And that's when the crash reporter crashes. Not much use in filing a report when you can't exactly say what went wrong.

Yeah that's cool, I was talking about regular bug reporting. (when the crash reporter works :P)

> **stragierk said:**
> Anyhow, Launchpad and me didn't work out, mostly because I don't know whether I'm talking about a bug or suggesting a new feature.

tbh it doesn't really matter, just submit the bug anyway, there are people who can deal with semantics.

Specifically if you are talking about a new feature there is a status for that: [https://wiki.ubuntu.com/Bugs/Importance](https://wiki.ubuntu.com/Bugs/Importance)

> Wishlist: a request to add a new feature to one of the programs in Ubuntu.

These aren't always bugs, but can be ideas for new features which do not yet exist.
These can also be requests to have software packaged for Ubuntu.
If it is non-trivial to implement, it should rather be written as a feature specification, see FeatureSpecifications

Think of launchpad as less of a "bug" tracker and more of a "issue" tracker, if you have an issue at all, submit a bug, if it's something you're doing wrong you'll get told about it, if it's a question it'll get turned into one on the answer tracker or you'll be told to use these forums, either way not an issue.

> **stragierk said:**
> 
(Thus need to answer the question of Launchpad ticket/report or a mailing list

Launchpad report, every time, the mailing list is just for discussing various topics.

---

### Post by stragierk on 2011-04-19
All right, thanks for clearing that up.

---

### Post by recluce on 2011-04-20
On beta1 (besides the install from USB crashing for me, like all Natty releases so far), the installer tried to access partitions it was explicitly set to "do not use". Reason enough for me to STOP testing, I still need my data on those partitions. Does anybody know if this has been corrected? 

Any experience with a beta2 install from USB in a Live Session?

---

### Post by smoosh on 2011-04-24
The biggest issue I had with installing Natty Beta 2 was with Grub. I tried to install it (Natty Beta 2) to an external HD just for giggles, and the resulting install left my internal SSD unbootable! After trying to fix it for almost an hour - reading how-tos on my phone, I just installed the damn thing to the SSD, even though I wasn't ready, and knew there would be hell to pay.

SO, aside from having to re-tweak my entire system (which was to be expected) and a few processes eating my cpu sometimes (ubuntuone, xapian-index, some other things I can't remember the names of), everything is great! Oh, there are some very strange compiz behaviors if I enable or disable things is CCSM, but it had the same sort of thing in Maverick, so meh.

I guess the one thing I don't really get is why all the restricted extras had to be uninstalled... But who cares? The whole reason I switched to Ubuntu from OSX is so I could tweak the crap out of it, so while part of me likes to bitch about all the stuff I had to do to get it working right, another part of me LOVES having to do all that stuff again every six months. I guess it makes me feel needed. Thanks Ubuntu!

---

