---
title: "Ubuntu to remove and blacklist Gnome-Shell"
date: 2010-12-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2010-12-14
Wow, I just found a bug report (#690045) of the developer Micah Gersten.

He says it is not possible to build a working Gnome-Shell upgrade (2.91.*)
due to the state of Gnome3 in Natty.
He also claims that due to changed libraries, Gnome-Shell is broken at the moment.
The plan is to come back to this issue, when Gnome3 is more ready in Natty.

Here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/690045](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/690045)

---

### Post by ronacc on 2010-12-14
I wonder if we will be able to keep building it ourselves since it builds alot  of it's own libs .

---

### Post by amano on 2010-12-14
There have been a lot of last minute changes in GTK+ 3 recently. But we are close to the feature freeze: [http://blogs.gnome.org/tvb/2010/12/13/bonus-icon-view-refactor/](http://blogs.gnome.org/tvb/2010/12/13/bonus-icon-view-refactor/)

> Actually as a passing note, the GTK+ team meeting this week is potentially the last one we’re going to have before freezing GTK+ 3.0 apis. If there are glitches, problems, polishing work for GTK+ that you know is important and requires breaking API/ABI, it would be a good idea to present your issues at this meeting.

The IRC meeting is due in about 7 hours. Then we will know more ;)

---

### Post by chrisccoulson on 2010-12-14
It's not GTK3 which is the problem here. There have been quite a lot of architectural changes in the rest of the GNOME stack, which we aren't adopting in Ubuntu this cycle and are necessary to make gnome-shell work properly

---

### Post by Merk42 on 2010-12-14
> **chrisccoulson said:**
> It's not GTK3 which is the problem here. There have been quite a lot of architectural changes in the rest of the GNOME stack, which we aren't adopting in Ubuntu this cycle and are necessary to make gnome-shell work properly
Why aren't they being adopted in this cycle?

---

### Post by chrisccoulson on 2010-12-14
> **Merk42 said:**
> Why aren't they being adopted in this cycle?

Because everybody is focused on integrating Unity at the moment, and taking other disruptive changes would make the work on Unity difficult

---

### Post by Harry33 on 2010-12-14
Bug #690045
Fix released, Gnome-Shell is dropped now.
The next one to drop (naturally) is gjs, because Gnome-Shell is the only application to use it.

---

### Post by Gourgi on 2010-12-14
> **chrisccoulson said:**
> ...and taking other disruptive changes would make the work on Unity difficult..
and could potentially lead more users to the other side ... (i meant) to the other Shell :-P

obviously i'm kidding. i hope the devs 'll make Unity (Hard) rock this cyrcle!

---

### Post by Harry33 on 2010-12-14
We who run Natty and would still like to use Gnome-Shell, have yet another possibility to go (in addition to jhbuild).
And that is ricotz Testing PPA.
That one will, however install GTK+3 versions of gnome-settings-daemon and libgnomekbd. => GTK+2 theming will break, not a big isssue. Gnome-Panel will still work. GDM is odd without a background (it is black).

---

### Post by autocrosser on 2010-12-14
Hmmmm---I run both--one in each install & have removed all the Unity parts in my GS-testing install---I will keep using jhbuild to keep up to date. I must admit to liking GS better that Unity, so I will be deciding within the next couple of releases if I am staying with Ubuntu or moving on after almost 6 years......

It's a pity that we will be forced to make a choice like this.

---

### Post by ronacc on 2010-12-14
I'm with you , I just built GS in a fresh install , and I've already been censured for my diatribes against unity .

---

### Post by cariboo on 2010-12-14
I as far as I can see, the devs are only removing gnome-shell from the repositories, which was really out of date, so that they can get Unity done. They haven't said it won't ever be back.

I'm using gnome-shell from the rictoz ppa, as I don't feel like waiting 3 days+ for the download from the git repositories to finish.

---

### Post by ronacc on 2010-12-14
I built it from zero in a fresh install in less than 2 hrs including re configing dconf when the script fails there .

---

### Post by cariboo on 2010-12-14
I can't do the build, if it takes forever to download the files. :)

---

### Post by ronacc on 2010-12-14
are you dial up , dsl or dog sled ?

---

### Post by xebian on 2010-12-14
> **cariboo907 said:**
> I as far as I can see, the devs are only removing gnome-shell from the repositories, which was really out of date, so that they can get Unity done. They haven't said it won't ever be back.

I'm using gnome-shell from the rictoz ppa, as I don't feel like waiting 3 days+ for the download from the git repositories to finish.

For the curious, what would be the alternative?  Fedora? Debian?  Thanks.

---

### Post by cariboo on 2010-12-14
> **ronacc said:**
> are you dial up , dsl or dog sled ?

Cable and dogsled. :) running [mtr]("http://linux.about.com/library/cmd/blcmdl8_mtr.htm"), I can see i have a good working connection to the git repositories, it just takes for ever to download anything.

[[IMG]http://www.speedtest.net/result/1071013805.png[/IMG]](http://www.speedtest.net)

---

### Post by ronacc on 2010-12-14
your connection is faster than mine  , I wonder if the isp is slowing down that link for some reason , I know comcast my ex cable isp was messing with torrents something fierce , the were so blatant about (even legal ones like ubuntu .iso's) it they got called before congress ( U.S.) about it . As soon as DSL from the phone company became available I jumped on board

---

### Post by autocrosser on 2010-12-14
> **xebian said:**
> For the curious, what would be the alternative?  Fedora? Debian?  Thanks.

I have grown very fond of .debs---so a Debian offshoot or Debian it self would be my next choice--- I could very easily go down the Sid path......

---

### Post by tad1073 on 2010-12-14
I like neither gnome shell or unity, guess I am used to regular old gnome. If it is not an option when 11.04 final is released then I am going to Fedora 15 when it is released.

Unity looks like it should be on a phone , PDA, iPad type device but not a desktop, just my opinion though.

---

### Post by ronacc on 2010-12-14
they pretty much have to keep the standard gnome desktop around for all those systems that can't handle compiz .I doubt Ubuntu is ready to kick them to the curb .

---

### Post by Harry33 on 2010-12-15
> **cariboo907 said:**
> I as far as I can see, the devs are only removing gnome-shell from the repositories, which was really out of date, so that they can get Unity done. They haven't said it won't ever be back.
...


This exactly what was said:
"Due to the state of the GNOME3 stack in natty, we won't be able to upgrade gnome-shell to 2.91.x. In addition, due to libraries that have already changed, (Bug #685225 and Bug #677382), gnome-shell is currently broken. We also have the xulrunner-2.0 transition to consider. Due to all this, we believe it best to remove gnome-shell from natty.
The current plan is to get it built in the GNOME3 PPA and reintroduce when GNOME3 makes its way into Ubuntu."

So devs plan to add gnome-shell and its dependecies into Gnome 3 Stack.
This was then marked as "fix released".
Here:
[https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds](https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds)

So it is now very clear we will not see gnome-shell, any versions of it, in Natty.
Natty will not be ready to GTK+3, Unity is a GTK+2 plugin to GTK+2 Compiz.
Perhaps 11.10 (Ostentatious Oselot) then, who knows.

---

### Post by chrisccoulson on 2010-12-15
> **Harry33 said:**
> So it is now very clear we will not see gnome-shell, any versions of it, in Natty.
Natty will not be ready to GTK+3, Unity is a GTK+2 plugin to GTK+2 Compiz.
Perhaps 11.10 (Ostentatious Oselot) then, who knows.

Like I said earlier, it's nothing to do with GTK 3. There are already things in the archive using GTK 3 (including Apport and Jockey). The issue is that it really depends on the rest of the GNOME stack in order to work properly, and we aren't updating all of that yet in Natty.

---

### Post by Harry33 on 2010-12-15
> **chrisccoulson said:**
> Like I said earlier, it's nothing to do with GTK 3. There are already things in the archive using GTK 3 (including Apport and Jockey). The issue is that it really depends on the rest of the GNOME stack in order to work properly, and we aren't updating all of that yet in Natty.

And by that you mean packages like gnome-settings-daemon and libgnomekbd, which ought to be built against GTK+3. Then GTK+2 theming would be gone.
Plus, that G-S also needs newer clutter (1.6), that would break some other applications.

---

### Post by Merk42 on 2010-12-15
For those that want GNOME Shell, would building from source (or Ricotz PPA) still be an option come release of 11.04?

---

### Post by castrojo on 2010-12-15
> **Merk42 said:**
> For those that want GNOME Shell, would building from source (or Ricotz PPA) still be an option come release of 11.04?

Everything's being set up here: [https://launchpad.net/~gnome3-team](https://launchpad.net/~gnome3-team)

(but it's not ready yet)

---

### Post by cariboo on 2010-12-15
Thanks for the info Jorge.

---

### Post by autocrosser on 2010-12-15
Thank You Jorge!!!!!  I'm all over it......

---

### Post by ronacc on 2010-12-15
I've been watching this one for awhile ,[https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds](https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds) looks like things are moving again they were kind of stalled for awhile .

---

### Post by ktp on 2010-12-15
> **autocrosser said:**
> I have grown very fond of .debs---so a Debian offshoot or Debian it self would be my next choice--- I could very easily go down the Sid path......

sid is interesting path...one that i am considering also, but not just yet.  I think ubuntu and GS will be ok for me by next LTS.

---

### Post by rogerdean on 2010-12-16
I've just this week switched to Squeeze myself. I miss the PPA ecosystem, but otherwise all is well. I've enjoyed figuring out how to tweak more things and live without the ubuntu polish, and it all feels vaguely virtuous ;-)

---

### Post by Yellow Pasque on 2010-12-16
Sid isn't really meant for GNOME users, since a lot of parts change rapidly (though if you usually live with and work around the breakage in Ubuntu alpha releases, you may be okay). 
I run aptosid with xfce, and enjoy the rolling-release model. I find it much more stable than Ubuntu prereleases.

---

### Post by autocrosser on 2010-12-16
Hmmm--I'll be looking around if we are pushed too hard towards Unity--I'm not sure that it works for me & I've been using it for a while now....I must admit to working with GS for almost 2 years now & feel much more at home with it...

---

### Post by ronacc on 2010-12-16
I will stick around as long as the classic desktop remains available or if that is obviated by gnome3 ,that it remains possible to at least local build GS . I d/l'd the debian installer today and am preparing 2 partitions on my test box for squeeze and sid .

---

### Post by Harry33 on 2010-12-17
Yesterdays transition from gir1.0 to gir1.2 completely broke the ricotz Testing PPA Gnome-shell installation.
Right now using only Gnome-Panel with all upgrades/updates.

---

### Post by seeker5528 on 2010-12-17
> **Temüjin said:**
> Sid isn't really meant for GNOME users, since a lot of parts change rapidly (though if you usually live with and work around the breakage in Ubuntu alpha releases, you may be okay).

WHa-a-a-a-a-at?!?! :p

A lot of packages change often, that doesn't necessarily mean they change rapidly.

The things the are *really* a problem are going to be a problem whether you use Gnome or not, so I don't know why you single out Gnome users and say "Sid isn't really meant for GNOME users".

There is not that much changing at the moment anyway since Debian is in a Freeze for their next release. Hopefully they get the release out in the not too distant future, my list of things I have installed from experimental is a little bigger than I would like.

And yes Gnome is my primary UI in my Debian install on my primary machine home machine. ;)

Later, Seeker

---

### Post by Yellow Pasque on 2010-12-17
> **seeker5528 said:**
> The things the are *really* a problem are going to be a problem whether you use Gnome or not, so I don't know why you single out Gnome users and say "Sid isn't really meant for GNOME users".

This is the official policy of aptosid (formerly sidux). They don't offer GNOME iso's and they don't support GNOME

---

### Post by Harry33 on 2010-12-18
To those, who might be thinking of Debian.
See this article here on **Phoronix**:
**Debian 6.0 Kernel Will Be Free Of Closed Firmware**
[http://www.phoronix.com/scan.php?page=news_item&px=ODkyNQ](http://www.phoronix.com/scan.php?page=news_item&px=ODkyNQ)

"So what does this mean for you as a user? As an example, with Debian 6.0 not only may your network adapter might not work "out of the box", but even your ATI Radeon graphics card with the open-source driver not work by default on Debian."

---

### Post by ronacc on 2010-12-18
you just gotta love those purists , its so much fun watching them shoot their feet off:lolflag:

---

### Post by plun on 2010-12-18
> **ronacc said:**
> you just gotta love those purists , its so much fun watching them shoot their feet off:lolflag:

"Feets"... :confused: well they probably shoot something more important...
just tragic !!....:-k

---

### Post by Merk42 on 2010-12-18
They will finally be free...






...of a working system.

---

### Post by ronacc on 2010-12-18
what is the thought process that leads them to conclude that releasing a "pure" but deliberately crippled system will favorably impress people ?

---

### Post by seeker5528 on 2010-12-18
> **Harry33 said:**
> "So what does this mean for you as a user? As an example, with Debian 6.0 not only may your network adapter might not work "out of the box", but even your ATI Radeon graphics card with the open-source driver not work by default on Debian."

Most likely you will either have to make sure you download the disc that includes the firmware or you will have to install linux-firmware-nonfree or some specific firmware package after the fact. 

You already had to install some firmware packages after the fact anyway for some non-free firmware and for that hardware you may still have to install the firmware after the fact even if you get the disc the includes the firmware that was removed. 

Later, Seeker

---

### Post by Harry33 on 2010-12-18
This is not a question of free versus non-free.
No, not at all.
See, there is a difference between these two:
1) free - nonfree
2) open - closed

What Debian is doing, is to remove the closed source from kernel, even if it were free.
So they wont give a damn if an enterprise lets their code be free or not.

---

### Post by seeker5528 on 2010-12-18
> **Temüjin said:**
> This is the official policy of aptosid (formerly sidux). They don't offer GNOME iso's and they don't support GNOME

If you just say Sid I assume Debian Sid.

Aptosid is a different project with their own goals/agendas/time limitations.

Aptosid not supporting Gnome is a totally different thing than saying 'Sid isn't intended for Gnome users'.

And it looks like somebody is willing to put in some effort on Gnome in Aptosid.

[http://www.aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=408&highlight=gnome](http://www.aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=408&highlight=gnome)

Later, Seeker

---

### Post by seeker5528 on 2010-12-18
> **Harry33 said:**
> This is not a question of free versus non-free.
No, not at all.
See, there is a difference between these two:
1) free - nonfree
2) open - closed

What Debian is doing, is to remove the closed source from kernel, even if it were free.

Hmmm, black boxes the developers are not free to fix fix, verify security of, adapt to better ways of doing things.

You pay for it, just not with money.

Later, Seeker

---

### Post by sgage on 2010-12-18
> **ronacc said:**
> what is the thought process that leads them to conclude that releasing a "pure" but deliberately crippled system will favorably impress people ?

I am not an FSF guy, and cheerfully fire up the nvidia proprietary drivers first thing after an install, but I think their thought process contains these elements:

First, they're not trying to "favorably impress people" in the sense of selling product or winning market share. They're sticking to an ideal, which impresses the people that they want to impress. Though "impress" probably isn't quite the right word.

Second, they consider a system containing closed binary blobs to be deliberately crippled.

Third, I think they are thinking long-term.

I, for one, respect their views thought I'm not that "pure" myself. It is fun to poke fun at the "purists" once in a while, but if you reflect for a moment, you will realize that we have a lot to thank them for.

---

### Post by ronacc on 2010-12-18
I do respect their opinion , they are perfectly free to hold it . I do not agree with it . If some company wishes to supply " closed" software I welcome that, also and I also respect that companies desire to protect their product from the sometimes inept meddling of any keyboard jockey that thinks he can "improve" it and wants to call himself a "developer". I DO NOT mean to denigrate all those excellent and hard working developer who contribute so much to open source but it must be realized that open source is by its nature open to everyone .And it must also be noted that the result of said ineptness is often blamed on the manufacturer so I understand their desire to prevent it.

---

### Post by autocrosser on 2010-12-19
I just went to Debian's news page about this & this is what is posted:> **December 15th, 2010**
 The Debian project has been working in removing non-free firmware from the Linux kernel shipped with Debian for the past two release cycles. At the time of the releases of [Debian 4.0 Etch]("http://www.debian.org/releases/etch/") and [5.0 Lenny]("http://www.debian.org/releases/lenny/"), however, it was not yet possible to ship Linux kernels stripped of all non-free firmware bits. Back then we had to acknowledge that freedom issues concerning Linux firmware were [not completely]("http://www.debian.org/vote/2006/vote_007") [sorted out]("http://www.debian.org/vote/2008/vote_003").
 We have nonetheless kept on working on splitting away non-free bits from the Linux kernel, thanks to the work of the [Debian Kernel team]("http://wiki.debian.org/DebianKernel") and various Linux upstream developers. We are proud to announce that, to the best of our knowledge, all issues are solved and that we will be able to deliver a Linux kernel which is completely Free, according to the [Debian Free Software Guidelines (DFSG)]("http://www.debian.org/social_contract#guidelines"), with Debian Squeeze. We hereby reaffirm Free Software as one of our priorities, as documented in the [Debian Social Contract]("http://www.debian.org/social_contract").
 In accordance with the Debian Social Contract, we acknowledge that some users require the use of works that do not conform to the DFSG and that those works might include non-free firmware bits. For the time being, we have added to the non-free area of our archives alternative installation images and additional packages for Debian Squeeze, that include non-free firmware bits needed to enable specific pieces of hardware. They are not part of Debian, they should be looked for explicitly by interested users, and we cannot support them to the same extent of Free firmware as we do not have access to the corresponding source code. We encourage hardware manufacturers to release only DFSG-free firmware and we cannot accept other kind of firmware as part of Debian.


I don't see any problem with adding the stuff I need to make my system run--nvidia-drivers & maybe the Ethernet card......

---

### Post by ronacc on 2010-12-19
I think most of us here on the dev forum could manage to get a "working" system even if debian didn't provide "restricted" .debs . it will be interesting to see how this plays out .

---

### Post by cornflake000 on 2010-12-25
I have really mixed feelings about Unity.  Logically thinking, the idea of one task bar certainly removes a lot of redundancy.  I could get used to it in that respect.  Personally though, it does remind me that our friends at Apple thought of putting this idea to general use a long time ago so I feel a little sheepish... but what the **ll, I'd get over it.

On the other hand, the side bar completely eliminates any logical savings of the singular task bar.  It just sits there taking up space, making clutter.  Can someone tell me what benefit there is in this *thing*?  I remember someone with the idea of overlapping the files and folders like a drawer or something.  I wouldn't like it, but at least there could be some logical space savings.  It seems like it's there just for the sake of change rather than being there for a useful reason.  If it's just for change, then it should be a desk toy choice... not a default.

my 2 cents

---

### Post by Harry33 on 2010-12-25
Now this thread was supposed to be a discussion of the feelings people here have about Ubuntu giving up gnome-shell.
We did then proceed talking about free - non-free and open - closed applications and source.
As this is now past, mods could as well close this thread.

Anyway - than you all for this discussion.

---

### Post by cornflake000 on 2010-12-25
Inadvertently, I thought that was what I was doing.  I just didn't use the name gnome or the word shell.  There is nothing wrong with expanding an idea.  It's not off topic in my opinion.

---

### Post by ronacc on 2010-12-25
our feelings about gnome-shell include what Ubuntu intends to replace it with IMHO .

---

### Post by autocrosser on 2010-12-25
Agreed---I for one would rather use GS than Unity---as much as I try to like Unity---I don't......And yes, I've been involved with GS from the very early days--so I might be biasd towards GS---but I don't like the "perceived" forcing of Unity on users & Unity having a side-bar that intrudes in my workspace is not helping its case (yes I know it will auto-hide in the future, but I like hitting a hotspot & having multiple options--plus the Global Menu system is the one thing I disliked about Mac & I still dislike it now).

---

### Post by t1497f35 on 2010-12-25
@[autocrosser]("http://ubuntuforums.org/member.php?u=25322")
I haven't used GS at all but I tried out Unity and I like it better than the old style Gnome panels.

---

### Post by autocrosser on 2010-12-25
> **t1497f35 said:**
> @[autocrosser]("http://ubuntuforums.org/member.php?u=25322")
I haven't used GS at all but I tried out Unity and I like it better than the old style Gnome panels.

Perhaps you 'ought to build GS to see how the two compare......Similar but very different.....

---

### Post by ronacc on 2010-12-25
> **t1497f35 said:**
> @[autocrosser]("http://ubuntuforums.org/member.php?u=25322")
I haven't used GS at all but I tried out Unity and I like it better than the old style Gnome panels.

We are not telling you that you have to use Gnome-shell because we like it ,so don't tell us that we have to use unity because you like it .

---

### Post by VMC on 2010-12-25
> **autocrosser said:**
> Agreed---I for one would rather use GS than Unity---as much as I try to like Unity---I don't......And yes, I've been involved with GS from the very early days--so I might be biasd towards GS---but I don't like the "perceived" forcing of Unity on users & Unity having a side-bar that intrudes in my workspace is not helping its case (yes I know it will auto-hide in the future, but I like hitting a hotspot & having multiple options--plus the Global Menu system is the one thing I disliked about Mac & I still dislike it now).

I'm beginning to feel the same way. It appears a lot of others are too. I didn't have much success with GS, but I'm really starting to dislike Unity and that behemoth left side panel. It gets in the way. Also way should I have to install another program, namely ccsm, just to try and silence the beast!

---

### Post by Amaranth on 2010-12-25
> **VMC said:**
> Also way should I have to install another program, namely ccsm, just to try and silence the beast!

Because it's not finished yet?

---

### Post by fluteflute on 2010-12-26
I think it's sad that this has happened, because in my opinion we should have made it as easy as possible for Ubuntu users to tryout GNOME Shell.

Let's just hope that when the underlying GNOME 3 libraries are stabilised then Unity is ported to them ASAP.

---

### Post by Harry33 on 2010-12-26
So, let the discussion go on, by all means.

Here is the latest news on Gnome-Shell and its state in Ubuntu.
This is from the bug #[Bug 685225]: Broken dependencies for gnome-shell in natty.

>  gnome-shell has been removed from natty for the moment (see bug
#690045), if we can get enough of gnome3 in natty for it to build, we
can add it back, otherwise, it should come back in natty + 1.  gnome-
shell will be staged with the rest of gnome3 in a PPA for the moment:
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3), please tag any bug
reports for those PPA packages with the gnome3 tag.  Please report any
other issues you may find.

** Changed in: gnome-shell (Ubuntu)
       Status: In Progress => Invalid

** Changed in: gnome-shell (Ubuntu)
     Assignee: Micah Gersten (micahg) => (unassigned) 

And an addition to what is said in the quote:
ATM in Gnome3 Team PPA there are no gnome-shell nor dependant packages.
Only some other Gnome3 packages, of which Nautilus and Poppler are broken.

---

### Post by mc4man on 2010-12-26
I find it's a bit too early with either to make any real judgments, for the most part have no issue with unity even as partially implemented.

Can say that on the desktop would/do prefer  a 'true-hide' mode vs. intelli-hide. Atm that is a fairly simple source edit to enable, though it has been said by some of those who do have a say that the add. option may be included.

even with true-hide do find times that it's useful to keep the launcher exposed no matter what, for that a simple toogle switch as a desktop launcher and or key combo works quite well.

Ex. of switcher script (thanks to hamidaddin for basic
```
#!/bin/bash
key_value=$(gconftool --get /apps/compiz-1/plugins/unityshell/screen0/options/launcher_autohide)
echo $key_value | grep "false"
if [[ $? -eq 0 ]] ; then
	gconftool --type Boolean --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_autohide true
else
	gconftool --type Boolean --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_autohide false
fi
```

---

### Post by Harry33 on 2011-01-03
A logical step to move on the path to remove gnome-shell follows.
Now also the package gjs (libgjs0b) will be removed from Natty repos.
See the bug (wishlist) #696812
[https://bugs.launchpad.net/ubuntu/+source/gjs/+bug/696812](https://bugs.launchpad.net/ubuntu/+source/gjs/+bug/696812)

---

### Post by jennybrew on 2011-01-03
Does Ubuntu have a history of U turns if a decision is proved to be inappropriate?
I may be wrong but I dont think so.
So, those folks who dont really think Unity is the way to go might have a very long wait indeed for Gnome Shell. 
Thats a shame IMHO because I just cant seem to warm to that horrible looking thing thats taken up residence on the left side of my desktop. Maybe Ill get used to it as things improve along the development cycle. 
What will be will be ..lets just wait and see :)

---

### Post by cariboo on 2011-01-03
The only change from the blueprint that I've seen so far is that you can switch to the classic desktop without having to install anything extra. The way it was supposed to work, was that if your system is capable of 3D you'd get Unity, and if it wasn't capable of 3D it wouldn't be installed.

---

### Post by autocrosser on 2011-01-03
Well, fellow testers---reflecting on the notes from this page it now looks like time. I wish everyone well & am taking my leave from Ubuntu. I have joined the Linux Mint forums & downloaded the Linux Mint Debian Edition.......I do look fondly back on 5+ years here testing for Ubuntu & hope Ubuntu comes back to sanity sometime.

Cheers & farewell.
Autocrosser

---

### Post by ronacc on 2011-01-03
farewell old friend , may we meet again .

---

### Post by Harry33 on 2011-01-04
> **autocrosser said:**
> Well, fellow testers---reflecting on the notes from this page it now looks like time. I wish everyone well & am taking my leave from Ubuntu. I have joined the Linux Mint forums & downloaded the Linux Mint Debian Edition.......I do look fondly back on 5+ years here testing for Ubuntu & hope Ubuntu comes back to sanity sometime.
Cheers & farewell.
Autocrosser

It is always sad to lose an experienced member.
I also think Ubuntu has now done a wrong turn with Natty.
It is still promised that Gnome-shell will be back on Natty + 1 (Obedient Opussum, whatever).

---

### Post by pressureman on 2011-01-04
I also think Ubuntu has lost the plot somewhat with focusing so heavily on Unity. Whilst it might make sense for a tablet/handheld (eg. a multitouch device with no mouse), it sacrifices too much functionality on traditional notebooks/desktops with mice (some with 3 buttons or more! wow! just look what we can do if the user clicks the RIGHT or MIDDLE mouse button!).

I realize that Gnome classic desktop is still available, but I wonder for how much longer....

I'm not really a KDE fan, which rules out Kubuntu, so maybe it's time I checked out Linux Mint, or just good ol' Debian.

---

### Post by edujose on 2011-01-04
Hi autocrosser, we'll miss you around here.

Maybe you can come back next cycle (I hope Gnome Shell will be the main Ubuntu focus by then).

Meanwhile, the devs could consider using AWN or Docky in Unity as left toolbar... (just dreaming :p)

---

### Post by lucazade on 2011-01-04
> **edujose said:**
> Hi autocrosser, we'll miss you around here.

Maybe you can come back next cycle (I hope Gnome Shell will be the main Ubuntu focus by then).

Meanwhile, the devs could consider using AWN or Docky in Unity as left toolbar... (just dreaming :p)

Is GnomeShell the panacea for all problems?!
Unity devs made both AWN and Docky so it is just a matter of time :)

---

### Post by Harry33 on 2011-01-04
> **lucazade said:**
> Is GnomeShell the panacea for all problems?!
Unity devs made both AWN and Docky so it is just a matter of time :)

This is not so simple.
Me, I do not have problems with Unity Shell, if it would be an option.
But it really seems Unity has taken a lot of overall development resources and time in Natty.
Other software and issues are lagging too much.
Let's look at it this way: Natty-alfa 1 still looks quite a lot like Maverick, if we do not take into account the Unity complex.
Nothing much has happened (in Natty) with Gnome and really plain zero with Gnome-shell.

And one more thing, there will be a Feature Freeze in Natty on 24th February, not so much time to go. If we look back, we can only see that the development of Unity takes a lot of time. I do not believe there will be so many new features anymore during this cycle.

---

### Post by lucazade on 2011-01-04
> **Harry33 said:**
> This is not so simple.
Me, I do not have problems with Unity Shell, if it would be an option.
But it really seems Unity has taken a lot of overall development resources and time in Natty.
Other software and issues are lagging too much.
Let's look at it this way: Natty-alfa 1 still looks quite a lot like Maverick, if we do not take into account the Unity complex.
Nothing much has happened (in Natty) with Gnome and really plain zero with Gnome-shell.

And one more thing, there will be a Feature Freeze in Natty on 24th February, not so much time to go. If we look back, we can only see that the development of Unity takes a lot of time. I do not believe there will be so many new features anymore during this cycle.

I agree with You Unity has taken a lot of development resources and Natty seems more or less like Maverick without using Unity.

From Unity launchpad page i see Timeline 
[https://launchpad.net/unity/+series](https://launchpad.net/unity/+series)
Unity 3.8 is expected for 2011-03-31.. I'm not so sure Unity will be frozen on 24th Feb, i believe they will do an exception for Unity this time. Don't You?

---

### Post by amano on 2011-01-04
If you had followed the desktop development meetings, you would know that it isn't sure if Ubuntu can switch to GNOME/GTK+ 3 at all within this circle (most of the changes are done within PPAs currently). 

The GNOME developers landed a new theming engine for GTK+ 3 just a few days before Christmas.

This leads to one of the following options: 

a) a new theme needs to be written for the new engine. It should look similar to the current one to offer some similarity with existing GTK+ 2 programs. But Andrea Cimitan isn't able to clone Murrine a 100% within the new theming framework (the engine itself cannot be ported). Thus GTK+ 2 programs will look different than GTK+ 3 programs which isn't desireable at all (at least not in a "polished" distribution like Ubuntu)

b) all applications need to ported to GTK+ 3 in a rush before February. Some still aren't thus stability cannot be ensured with such a big porting effort at the end of the circle. 

c) GTK+ 3 adoption gets delayed until all applications within the Ubuntu stack are ported to GTK+ 3. Since GNOME Shell heavily depends on the GTK+ 3 stack now, that rules out GNOME Shell for Ubuntu 11.04.

Most probably option c) will be the one chosen. But it is understandable if the GTK+ people come out with such big changes (the new theming engine, still ongoing ports to GTK+ 3) so late in the cycle (HEY; GNOME 3 was scheduled for past September!!!).

The only real alternative that I can think of would be if GTK +3 could be patched to still use Andrea Cimitan's Murrine engine (maintaining the status quo of middle of December). But that will probably cause more breakage than what a brand new vanilla GTK+ 3 would introduce anyway and a lot of time would be wasted to maintain this code delta.

All in all: It is not Ubuntu's fault (Ubuntu is NOT as bleeding edge as Fedora risks to be). And nobody knows if Unity will end to be the default GUI for the final 11.04 release. The beta tests will show that and a default can easily be reverted, leaving the Ubuntu users with the tusted, classic GNOME panel. And I bet that Unity might be considered as "Not ready" in the end (what will probabyly be the fate of GTK+ 3 and GNOME Shell as well).

---

### Post by VMC on 2011-01-04
> **lucazade said:**
> I agree with You Unity has taken a lot of development resources and Natty seems more or less like Maverick without using Unity.

From Unity launchpad page i see Timeline 
[https://launchpad.net/unity/+series](https://launchpad.net/unity/+series)
Unity 3.8 is expected for 2011-03-31.. I'm not so sure Unity will be frozen on 24th Feb, i believe they will do an exception for Unity this time. Don't You?

If you go to [Natty changes]("https://lists.ubuntu.com/archives/natty-changes/2011-January/date.html") you'll see that more development is done on Natty Os than on Unity. that's why there's little changes right now to Unity. I'll wait until the Natty release before I jump to conclusions.

I'm more excited about the move away from X than Unity. I know that's a year or so off.

---

### Post by amano on 2011-01-04
Realistically....  much more than a year off ;)

:popcorn:

---

### Post by cariboo on 2011-01-04
Keep an eye on [The Planet]("http://planet.ubuntu.com/"), Jorge is supposed to put out a Unity progress report later today.

---

### Post by lucazade on 2011-01-04
> **VMC said:**
> If you go to [Natty changes]("https://lists.ubuntu.com/archives/natty-changes/2011-January/date.html") you'll see that more development is done on Natty Os than on Unity. that's why there's little changes right now to Unity. I'll wait until the Natty release before I jump to conclusions.

I'm more excited about the move away from X than Unity. I know that's a year or so off.

I usually follow that page you linked! I said natty seems more or like maverick without considering unity because 
most of the updates are "only" bug fixing and not brand new software.. all the other frameworks are now quite stabilized.
I'll wait Unity release before judging it..i'm not in a hurry! :)
The same applies also to GnomeShell and Wayland server.

---

### Post by cariboo on 2011-01-04
@lucazade, I remove the 3 extra posts.

---

### Post by VMC on 2011-01-04
> **cariboo907 said:**
> Keep an eye on [The Planet]("http://planet.ubuntu.com/"), Jorge is supposed to put out a Unity progress report later today.

Thanks for the link! Did you read this

[SIZE="3"]"Expect a flurry of activity this week as Unity developers spin up for the new year. Next week the Unity team will be sprinting in Dallas, Texas along with other members of the Canonical Platform team so expect a bunch of updates."[/SIZE]

Get ready folks..

---

### Post by lidex on 2011-01-05
I never warmed up to the Gnome-Shell interface, so I can't get emotional about its status. I am along for the ride - not about to jump ship - as I sense the fun part hasn't even started. If it turns out I don't like the end product with unity I'll just modify it anyway. I like the fact that canonical is breaking off.
No risk = no reward.

---

### Post by Harry33 on 2011-01-05
> **lidex said:**
> I never warmed up to the Gnome-Shell interface, so I can't get emotional about its status. I am along for the ride - not about to jump ship - as I sense the fun part hasn't even started. If it turns out I don't like the end product with unity I'll just modify it anyway. I like the fact that canonical is breaking off.
No risk = no reward.

True: no risk = no reward.
But also true: do not dump before you actually get to see what is was.
Gnome-shell was dumped way before it was (will be) ready.

---

### Post by ronacc on 2011-01-05
while it is often true that there is no reward without risk one should carefully evaluate both the risk and the POTENTIAL reward , because that reward is not guaranteed . As I see it the risk here is alienating a portion of your user base and the potential reward is a (short) head start on other distros if Unity turns out to be very popular . the reason I say short is that since this is linux and open source a  popular thing can be quickly adopted by other distros. IMHO in this case the risk is not justified by the reward . I am well aware that others may not see it this way .

---

### Post by plun on 2011-01-05
> **ronacc said:**
>  I am well aware that others may not see it this way .

Well Ubuntu Classic works with Docky or AWN.....):P

I am also rather sure that Gnome fails with Gnome3..... maybe they can do it with some paid developers !!!   Unity seems also like a disaster for the moment.

I am happy with Docky....  !!

---

### Post by ronacc on 2011-01-05
I"ve tried various docks and find that the plain "classic desktop" suits me best . I'm not even fond of OSX's dock on my MAC .

---

### Post by Merk42 on 2011-01-05
> **Harry33 said:**
> True: no risk = no reward.
But also true: do not dump before you actually get to see what is was.
Gnome-shell was dumped way before it was (will be) ready.

GNOME Shell wasn't dumped, it's just not going to be in 11.04 as a package **due to GTK+3**.

Even if Unity didn't exist it would probably be the same case.
GNOME Shell requires GTK+3, the apps in Natty won't be ready for GTK+3 in time for 11.04, therefore GNOME Shell won't be ready for 11.04.

---

### Post by xebian on 2011-01-05
I'm sorry if I don't get it but what is unity for? An Ubuntu branded uPad?  Considering Apple OS has a big headstart, a strong  Android, and perhaps HP webOS(palm pre), and of course Microsoft, who else will be using it?

IMHO the Desktop is still very large in the enterprise, SOHO, schools, and of course homes.  

I still haven't seen/experienced unity as it doesn't work in my boxes btw.

---

### Post by cariboo on 2011-01-05
Unity is a replacement for the classic two panel desktop, as gnome is moving away from it and to gnome-shell, eventually the two panel desktop will no longer be  available.

---

### Post by Harry33 on 2011-01-05
> **Merk42 said:**
> GNOME Shell wasn't dumped, it's just not going to be in 11.04 as a package **due to GTK+3**.

Even if Unity didn't exist it would probably be the same case.
GNOME Shell requires GTK+3, the apps in Natty won't be ready for GTK+3 in time for 11.04, therefore GNOME Shell won't be ready for 11.04.

First of all, if Unity did not exist, Canonical would have a lot more sources and working hours to really do something about GTK+3 in Ubuntu. Up to this date, nothing has been done for Gnome-shell. Then again, gnome.org is about to publish Gnome(2.91.5).

Are you saying Gnome3 will not be published on 6th April?
[http://live.gnome.org/TwoPointNinetyone](http://live.gnome.org/TwoPointNinetyone)

---

### Post by lidex on 2011-01-05
> **ronacc said:**
> As I see it the risk here is alienating a portion of your user base...<snip>
That can probably be said for any major change in direction.
I do think it early to come to any long term conclusions. We could very well end up with gnome-shell anyway and, 
as stated by others here, it wouldn't be ready for 11.04

---

### Post by plun on 2011-01-05
> **ronacc said:**
> I"ve tried various docks and find that the plain "classic desktop" suits me best . I'm not even fond of OSX's dock on my MAC .

Well......

[http://www.apple.com/macosx/](http://www.apple.com/macosx/)

I love an intelligent dock...... why use an "ugly" Unity ? or a total "GS-clutter"....:confused:

Nokia have no money so it is probably a severe crise for Gnome.....RMS cannot do anything.....

---

### Post by lidex on 2011-01-05
> **plun said:**
> well......

I love an intelligent dock...... Why use an "ugly" unity ? Or a total "gs-clutter"....


+1

---

### Post by cariboo on 2011-01-05
Docky 2 is now available [here]("https://launchpad.net/~docky-core/+archive/ppa"), it's getting better all the time, with removable anchor icon and workplace switcher.

This is my gnome 3 system with Debian branding, even though it came from the Ubuntu repositories.

---

### Post by Merk42 on 2011-01-05
> **Harry33 said:**
> First of all, if Unity did not exist, Canonical would have a lot more sources and working hours to really do something about GTK+3 in Ubuntu. Up to this date, nothing has been done for Gnome-shell. Then again, gnome.org is about to publish Gnome(2.91.5).I'm just saying I hope people don't think this is some super secret conspiracy to make people use Unity and not GNOME Shell
> **Harry33 said:**
> Are you saying Gnome3 will not be published on 6th April?
[http://live.gnome.org/TwoPointNinetyone](http://live.gnome.org/TwoPointNinetyone)Well GNOME Shell was already delayed twice, nonetheless something major has to be finished months in advance to be included in a release of Ubuntu.

---

### Post by ronacc on 2011-01-05
> **Merk42 said:**
> I'm just saying I hope people don't think this is some super secret conspiracy to make people use Unity and not GNOME Shell
Well GNOME Shell was already delayed twice, nonetheless something major has to be finished months in advance to be included in a release of Ubuntu.

no its a super secret conspiracy to make us use either unity OR GS instead of our old familiar WORKING desktop.

huh ? Unity is admittedly unfinished and we are less that 3 months from user interface freeze and yet they were bound and determined to include it ready or not .

---

### Post by cariboo on 2011-01-05
I have serious doubts that gnome 3/gnome-shell will be ready in April. Like has been said before, the classic 2 panel interface will eventually go away, so you have a choice  so far of Unity, Gnome-shell or the Windows 95/98 style interface of X/L/ubuntu.

---

### Post by Merk42 on 2011-01-06
> **ronacc said:**
> no its a super secret conspiracy to make us use either unity OR GS instead of our old familiar WORKING desktop.

If UIs never changed, you'd still be on GNOME 1 and wouldn't even have your beloved WORKING desktop in the first place.

---

### Post by Harry33 on 2011-01-06
> **Merk42 said:**
> If UIs never changed, you'd still be on GNOME 1 and wouldn't even have your beloved WORKING desktop in the first place.

Yes of course this is true. But no one denies that either.

As I see this, Unity as it is now, is not a true development from Gnome-Panel (Gnome2). It is merely an option. Both of those are GTK+2.0 UIs, same theme engine and themes.

And yet, Gnome-Panel can already easily be adjusted to look very much like Unity (if that is wanted), both of them can use Compiz compositing manager.

GTK+3.0 UIs can be considered true development. Gnome-Shell will be one.
Of course someone could have developed Gnome-Panel too to use GTK+3.0 and new theming engines and so on.

Perhaps what I am saying here is that Unity as a GTK+2.0 Ui is already history. It does not bring about anything so much new to brag about.
And it is somehow sad that so much time and effort is targeted for that.

Yet one more opinion, like it or not.
If Gnome3 will not be ready early enough for Natty, then why not stay with Gnome-Panel and wait. And in the meantime do something useful.
That is not what has happened.
Unity has been chosen long before anyone knew about Gnome3 possibly being late.
That is why I consider Gnome-Shell was dumped (for Natty and who knows for Natty+1).

---

### Post by Merk42 on 2011-01-06
> **Harry33 said:**
> Yes of course this is true. But no one denies that either.

As I see this, Unity as it is now, is not a true development from Gnome-Panel (Gnome2). It is merely an option. Both of those are GTK+2.0 UIs, same theme engine and themes.

And yet, Gnome-Panel can already easily be adjusted to look very much like Unity (if that is wanted), both of them can use Compiz compositing manager.

GTK+3.0 UIs can be considered true development. Gnome-Shell will be one.
Of course someone could have developed Gnome-Panel too to use GTK+3.0 and new theming engines and so on.

Perhaps what I am saying here is that Unity as a GTK+2.0 Ui is already history. It does not bring about anything so much new to brag about.
And it is somehow sad that so much time and effort is targeted for that.

Yet one more opinion, like it or not.
If Gnome3 will not be ready early enough for Natty, then why not stay with Gnome-Panel and wait. And in the meantime do something useful.
That is not what has happened.
Unity has been chosen long before anyone knew about Gnome3 possibly being late.
That is why I consider Gnome-Shell was dumped (for Natty and who knows for Natty+1).
Just because something is built with GTK+2 doesn't mean anything it accomplishes is already history. There are quite a few new things to Unity, but that's more thanks to Compiz making up for what GTK+2 lacks.

I do agree that it seems a bit silly to build Unity with GTK+2 since regardless of Ubuntu using GNOME Shell or not, GTK+2 will be discontinued.  If the compiz port of Unity were built with GTK+3 in mind it would be better in the long run and we wouldn't be in the blacklist mess to begin with.

Unity was chosen long AFTER Gnome 3 had already been delayed twice. It was originally supposed to come out spring of 2010. I don't know if that was the reasoning behind it, though.

So yeah, I think Unity should have been GTK+3, and then Shell and Unity would both be ready at the same time.

---

### Post by ronacc on 2011-01-06
> **Merk42 said:**
> If UIs never changed, you'd still be on GNOME 1 and wouldn't even have your beloved WORKING desktop in the first place.

I used GNOME 1 and somehow managed to get things done.:palso KDE when it was called K destop environment .

---

### Post by Yellow Pasque on 2011-01-06
I don't get what all the fuss is for. By the time 11.04 is out, most of you reading this will probably be using 11.10 and I'm sure that will have gtk3 and GS easily installable. The real moaning will start when GNOME classic goes away and people are forced to change if they want to stay current. 

Personally, I don't foresee myself liking GS or Unity, but I realize they're half-baked (and not in the good way ;P ), so I won't make any firm conclusions for a while. Until then, I happily use xfce on my main Debian install and GNOME classic on my Ubuntu VM's

---

### Post by Harry33 on 2011-01-06
> **Temüjin said:**
> I don't get what all the fuss is for. By the time 11.04 is out, most of you reading this will probably be using 11.10 and I'm sure that will have gtk3 and GS easily installable. The real moaning will start when GNOME classic goes away and people are forced to change if they want to stay current. 

Personally, I don't foresee myself liking GS or Unity, but I realize they're half-baked (and not in the good way ;P ), so I won't make any firm conclusions for a while. Until then, I happily use xfce on my main Debian install and GNOME classic on my Ubuntu VM's

This is kind of a selfexplanatory text, which I mostly agree, indeed.
Though, when 11.04 is out (on 28th April 2011), there is no 11.10 yet.
But of course soon after the tool chain is loaded, some of us are in.

Then, all this fuss here explains a lot too.
Not all of us accepts what is happening with Ubuntu and/or Gnome.
So let everybody have a fair chance to express their views.

---

