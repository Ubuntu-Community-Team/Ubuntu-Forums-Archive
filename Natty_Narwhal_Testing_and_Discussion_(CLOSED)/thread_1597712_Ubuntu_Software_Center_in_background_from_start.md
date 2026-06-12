---
title: "Ubuntu Software Center in background from start"
date: 2010-10-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Speed_arg on 2010-10-15
After realizing how slow and unhandy USC was, I thought about the following:
[LIST]
[*]USC loads at start with a delay and low niceness, like many things in Windows 7. This is for not making boot slower and laggy at the beggining.
[*]Would run completely hidden and in background
[*]Because of this, when opening a .deb or clicking in USC, it should load instantly, instead of taking 10 ridiculous seconds to load. This would make Ubuntu look a lot faster than now.
[*]When installing something, an inditator should appear in the notification bar or whatever it is called. Maybe the same spinning thing we have now at the left.
[*]When you are installing something, you can close USC and will continue installing in background. You can check installation progress in the indicator
[*]A similar system for updates would be handy
[/LIST]

---

### Post by cariboo on 2010-10-15
Why not just use the available work spaces, start up a program on one workspace, then go to an another one for something else. I normally use 4 workspaces, but there are more available if needed.

If you find the software Center slow, why not use Synaptic instead, it's still installed by default.

---

### Post by Speed_arg on 2010-10-15
> **cariboo907 said:**
> Why not just use the available work spaces, start up a program on one workspace, then go to an another one for something else. I normally use 4 workspaces, but there are more available if needed.

If you find the software Center slow, why not use Synaptic instead, it's still installed by default.

Hm i think you are not getting my point. That would be the same than minimizing. And USC is a lot better for installing programs that synaptic. Thats why USC was developed. Also USC will replace synaptic in the future.

---

### Post by cariboo on 2010-10-15
For me the Software Center doesn't do what I want when I install packages, the interface just seems to be too simplified to me. Even if Synaptic isn't installed by default, it will still be available in the repositories.

Using a Linux variant is all about what works best for me, not what a distro maker thinks will. When I do a new install, I mark all the packages I use on a regular basis for install, usually on the order of 200-250 packages, then click the apply button, and change to a different work space and do something else.

I did get your point about starting USC in the background, but I can't see the need, for a program that is only used occasionally.

---

### Post by lonniehenry on 2010-10-15
I wouldn't want USC running in the background for any reason.  It would tax low resource machines. Secondly I have had issues with it working correctly.  In Maverick when testing it didn't always work.  I like using synaptic as it tells me more about what is going to be installed.  Just my opinion.

---

### Post by david_ally on 2010-10-15
I cant launch Ubuntu Software Center. When i tried to launch USC, it indicates it is starting in the panel, but eventually just vanishes away. I was having similar problems with Printing, and other application launchers on Lucid, so i decided to install mavericks to have a trial at the release, I did a clean install, but now printing works but USC will not launch.

I already rm /var/apt/cache/.bin* but no solution.

---

### Post by cariboo on 2010-10-15
You may not have noticed, but this section is for Natty testing and discussion, so this might not be the best place to get an answer to you question.

That being said when you start USC in a terminal, what is the output? To start it, just type:

```
software-center
```

---

### Post by 23meg on 2010-10-15
I hate to be Captain Obvious, but why not determine the real and perceived performance bottlenecks, and actually fix them instead? 

If certain aspects of USC are unacceptably slow on some hardware today (which they are), that doesn't necessarily mean USC is intrinsically destined to be slow, and can only survive on ugly hacks such as overly eager preloading.

---

### Post by kahumba on 2010-10-15
I think the OP is right.
But he's proposing a painkiller instead of a cure.

Imho the 2 main issues why it is slow are:
1) The app management is not based on a real database (like mysql or so) so to do basic operations one has to use lots of files which takes a whole lot longer than if a database was used.
Imho roughy saying it contributes like 70% to the "slowness".
2) It's written in Python and no matter how much you like Python and how much you hate anyone pointing it out - it doesn't change the fact that it's an interpreted language, period. And any Python "fan" can downplay this issue as much as one wants.

---

### Post by knarf on 2010-10-16
USC is a good example of what I meant when I started the [Hog Skinner]("http://ubuntuforums.org/showthread.php?t=1595375") thread. The thing takes **more that 30** **seconds** to start on a T23 with 1.2 GHz PIII-m, 768 MB and a fairly speedy 7200rpm Hitachi Travelstar with lots of free space. While not exactly new this system should be more than capable of running a modern-ish operating system. That is, when the distributor did not decide to write one of their centerpiece programs in a language known to be a resource hog.

How to speed it up? A rewrite to some compiled language might help. That it does not have a real database back end is not really USC's fault as it it dpkg's. As to whether a 'real database' is something you should want as underpinning for the package manager is debatable as it is much easier to resurrect a børked system which is based around plain text files - think [rpm --rebuilddb]("http://www.informatimago.com/linux/rpm-rebuilddb.html") for an example of what I would rather not have to go through again.

---

### Post by plun on 2010-10-16
> **knarf said:**
> 

How to speed it up? A rewrite to some compiled language might help. 

Yup... for sure... seems to be a never ending mess with python code for the moment.

Stone dead broken for me..... but I never uses it.

---

### Post by Arla on 2010-10-16
With regard to auto-starting it.

No, no and hell no. While I appreciate for a few people who are doing random software installs day in and day out, this would be great, for a majority of users, who do a few software installs from installing the OS and are then done, this would seem a terrible waste of time and space.

---

### Post by kahumba on 2010-10-16
Imo Canonical shouldn't have taken the trade-off between a quick starting app and the ability to develop it quickly in favor of the later.
But what's done is done and it's never too late to rewrite it, especially since Vala seems pretty solid by now and has a lot of Python-like syntactic sugar (I read the Vala tutorial and I really love this language, it's well thought and sweet, Shotwell is written in it btw).

As to a DB being more difficult to restore than text files - simply not true (or a half truth at best). The backend simply has to be smart enough to take advantage of the large possibilities that a modern DB offers, the DB is ideal for this since it supports transaction unrolling, backups, etc etc, you just build on top of this technology. There are much more critical systems that run on DBs (like the NYSE) instead of using plain files. I mean common, it's the 21 century and DBs are long around and designed exactly for this type of missions (and for much more complicated ones).

---

### Post by plun on 2010-10-16
Well... hopefully this sofware will be discussed during UDS....

> 160 	New bugs
403 	Open bugs
13 	In-progress bugs
0 	Critical bugs
10 	High importance bugs 

[https://bugs.launchpad.net/ubuntu/+source/software-center](https://bugs.launchpad.net/ubuntu/+source/software-center)

Rather "unstable", IMHO.....

---

### Post by knarf on 2010-10-16
> **kahumba said:**
> As to a DB being more difficult to restore than text files - simply not true (or a half truth at best). The backend simply has to be smart enough to take advantage of the large possibilities that a modern DB offers, the DB is ideal for this since it supports transaction unrolling, backups, etc etc, you just build on top of this technology. There are much more critical systems that run on DBs (like the NYSE) instead of using plain files. I mean common, it's the 21 century and DBs are long around and designed exactly for this type of missions (and for much more complicated ones).

In a way that might be true but it is not realistic. When the **** hits the fan you usually are dropped to a root prompt with a very limited file system - no place for advanced database trickery. The most you're likely to get in the way of databases is sqlite which does not offer much (if anything) in the way of disaster recovery.

 [ hmmm, I just saw you can not say **** on this forum... What 'bout ****? ****? ]

---

### Post by cariboo on 2010-10-16
> **knarf said:**
> In a way that might be true but it is not realistic. When the **** hits the fan you usually are dropped to a root prompt with a very limited file system - no place for advanced database trickery. The most you're likely to get in the way of databases is sqlite which does not offer much (if anything) in the way of disaster recovery.

 [ hmmm, I just saw you can not say **** on this forum... What 'bout ****? ****? ]

This is a family friendly forum, I've seen members as young as 8 years old, hence the censor.

---

### Post by knarf on 2010-10-16
> **cariboo907 said:**
> This is a family friendly forum, I've seen members as young as 8 years old, hence the censor.
What´s so bad about saying ****? It's just four stars after all...

---

### Post by cariboo on 2010-10-16
This isn't the place for this, but the stars aren't a problem, it's when members try getting around the language filter, that it becomes a problem.

---

### Post by ronacc on 2010-10-16
The censor is not a bad thing , as cariboo says this is a "family" forum and language best suited to the barracks or locker room is not appropriate here ( although it catches me on occasion too ).

---

### Post by ranch hand on 2010-10-16
> **ronacc said:**
> The censor is not a bad thing , as cariboo says this is a "family" forum and language best suited to the barracks or locker room is not appropriate here ( although it catches me on occasion too ).
Yup, sometimes that "working bulls in the corral" language just comes out.

---

### Post by kahumba on 2010-10-16
> **knarf said:**
> In a way that might be true but it is not realistic........ 
It's exactly the same argument like - we should continue driving the old car because for the new and better one we would have to earn money first.
So - right now - of course it's unrealistic, you do have to make changes, to make the infrastructure work together etc etc There are many solution to the "prompt" problem you're describing later which you're treating as if was the untouchable.
If you want stuff to work quickly you can't afford pushing around (often) thousands of files, you need to change the infrastructure - and yes, it requires some work, and yes, no one is going to implement this right now, but this should be "fixed" sometime in the future. There's much more sophisticated stuff that a DB can handle, and MySQL and other DBs even have support for working with them from the command line, that's already some work done right there.
I'm not saying it's easy, but if one just keeps figuring out excuses _not_ to fix the core problems but to work around them (or not fix them at all) - that's not good.
I mean - if I were told to do this as a developer (say if I worked for Canonical and it told me to implement it) - I could tell you a thousand excuses (half-truths) why using a DB is a bad idea just to avoid working (admittedly I'm both lazy and too busy) and most people would believe me.

---

### Post by macroshaft on 2010-10-23
> **Speed_arg said:**
> Hm i think you are not getting my point. That would be the same than minimizing. And USC is a lot better for installing programs that synaptic. Thats why USC was developed. Also USC will replace synaptic in the future.

Please do clarify how USC is better than Synaptic. I often find I install a program only to find it has no graphical interface and the executable command is different from the name of the program. USC gives me no help at all with this and I often have to close it, go to Synaptic and then call up more info on what is being installed!

Also I have found packages I can't locate in USC but can easily find in Synaptic. It is simply far superior in my opinion.

---

### Post by jaymac407 on 2010-10-23
In my opinion, and seeing first hand how slow USC can be on some machines, I feel USC needs euthanized and replaced with a slim version of Synaptic.

---

### Post by MishaAct on 2010-10-23
> **jaymac407 said:**
> In my opinion, and seeing first hand how slow USC can be on some machines, I feel USC needs euthanized and replaced with a slim version of Synaptic.
I don't like both, but I'm very disappointed about gdebi-gtk was replaced with USC which takes ages to start

---

### Post by cariboo on 2010-10-23
gDebi is still in the repositories, and takes mere minutes to install and setup.

---

### Post by autocrosser on 2010-10-23
Well--I did what I ought to have done in the first place--uninstalled Software centre (accepting that ubuntu-desktop is uninstalled also). I much prefer Synaptic & Gdebi--more to the point & do what I want when I want it....As a further "throw-back"--I still use Aptitude (and like it...)

I really think that there ought to be a option (along with several others) for an "advanced" user install during system install---include Gimp & several others--plus choose to not install "fluff" like USC & things like that........

---

### Post by ronacc on 2010-10-23
> **autocrosser said:**
> 
I really think that there ought to be a option (along with several others) for an "advanced" user install during system install---include Gimp & several others--plus choose to not install "fluff" like USC & things like that........

I have been lobbying for that for several cycles , perhaps its time to turn in another brainstorm on it .

---

### Post by cariboo on 2010-10-23
+1 I would like to see the same thing.  Brainstorm really isn't the place for an idea like that, as the devs only see the ideas during UDS.  From what I understand, the Ayatana mailing list is the place to bring it up. 

kansasnoob, got a pretty good reception for his email about ubiquity on the mailing list.

---

### Post by ronacc on 2010-10-23
I'll see what I can cobble up tomorrow and I'll post here for suggestions/criticisms before I submit it .

---

### Post by VMC on 2010-10-24
> **autocrosser said:**
> Well--I did what I ought to have done in the first place--uninstalled Software centre (accepting that ubuntu-desktop is uninstalled also). ...As a further "throw-back"--I still use Aptitude (and like it...)



+2 on both counts, also did your re-install the desktop or use another one?

---

### Post by autocrosser on 2010-10-24
Well---Ubuntu-Desktop is just a meta-package (and a rather empty one at that), so I was not worried about it--My install hums along just fine without it.......```
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.
```

Personally--I think that USC should not be in that depends group.....

---

### Post by ronacc on 2010-10-24
> **autocrosser said:**
> Well---Ubuntu-Desktop is just a meta-package (and a rather empty one at that), so I was not worried about it--My install hums along just fine without it.......```
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.
```

Personally--I think that USC should not be in that depends group.....

yeah the meta-packages are a pain in the butt , I doubt we can talk them into dumping them though . On my "real" system I get rid of them and a ship :P load of other stuff and install what I darn well want , for testing though I try to keep installs on my test box atleast reasonably close to "as delivered .

---

### Post by crjackson on 2010-10-24
I don't mind the USC being there but I personally have no use for it. I know that others do but it's not for me so much. I went the other step and installed gdebi as well. I guess I just got used to a certain way of doing things.

---

### Post by autocrosser on 2010-10-24
Well--after a bit of thought I reinstalled Ubuntu-Desktop & then removed the "crud" that I didn't want that didn't remove it---I DON"T like the fact that removing USC removes ubuntu-desktop--I won't be using USC & don't think I "need" it on my system...


Ronacc---I'm ready to add info/support for the Ayatana mailing list info---lets talk about it.......

---

### Post by VMC on 2010-10-24
> **autocrosser said:**
> Well--after a bit of thought I reinstalled Ubuntu-Desktop & then removed the "crud" that I didn't want that didn't remove it---I DON"T like the fact that removing USC removes ubuntu-desktop--I won't be using USC & don't think I "need" it on my system...


Ronacc---I'm ready to add info/support for the Ayatana mailing list info---lets talk about it.......

I was under the impression that removing the desktop removed a lot more than it does. I'll have to try and see exactly what gets removed. USC is fairly quick on my system, but I would like to use gdebi & aptitude, which is easy enough to install.

---

### Post by autocrosser on 2010-10-24
Yes--if you look at it--it has as depends:

Evolution, several TTF fonts, Assisted stuff, Ubuntuone, the new music store stuff & several other things in that vein..... I reinstalled USC & then removed about 3/4 of the "fluff" without any complaints from Synaptic. I would guess that the Music store & USC are the only ones that remove Ubuntu-Desktop when deleted......HATE that.:( --I have 0% use for the Music store & USC.

---

### Post by ronacc on 2010-10-24
removing ubuntu-desktop doesn't remove anything else , it's just a meta-package with a boat load of depends but nothing depends on it . Meta-packages are just used to drag in other stuff .

---

### Post by ronacc on 2010-10-24
how the heck do I join the ayatana mailing list ? there is no join button on their LP page .

---

### Post by LiquidMeson on 2010-10-24
> **ronacc said:**
> how the heck do I join the ayatana mailing list ? there is no join button on their LP page .

[https://launchpad.net/~ayatana](https://launchpad.net/~ayatana)
Should be there, you need to log in and join the team first.

---

### Post by ronacc on 2010-10-24
> **LiquidMeson said:**
> [https://launchpad.net/~ayatana](https://launchpad.net/~ayatana)
Should be there, you need to log in and join the team first.

Thanks I was on the wrong page , launchpad.net/ayatana  ( no tilde ~ ):confused:

---

### Post by ronacc on 2010-10-24
@ autocrosser  here is what  I am proposing  to post to the ayatana list .

> With the understanding that Ubuntu always strives to make things as easy as possible for new users , there are many who have been loayal Ubuntu users for a long time that would like more control over the installation process . Can Ubiquity/Casper provide an " advanced " mode that would provide for that either as an option on the live-cd boot menu or from the live-cd desktop ?

suggestions , comments ?

---

### Post by autocrosser on 2010-10-24
Looks good to me....you might make suggestions as to what a advanced user might want with a "standard" install---Gimp, etc....And what the user might not want---USC, etc....

I found what Ubuntu-Desktop "recommends" when I reinstalled it--pulls in quite a bit of "garbage"

More thoughts: Maybe present a list of software that "could" be installed & not installed---I would guess that would only take a extra page in the installer---perhaps a checkbox list?

---

### Post by ronacc on 2010-10-24
I figured I would use the KISS principle to start with ,then if they are receptive we can fill in the details .but I'll add another sentence or 2 .

---

### Post by ronacc on 2010-10-24
ok added this to the above .

>  The ability to add and subtract specific software , for example + gimp , chromium and synaptics - Fspot ,USC and Firefox . And more control over the installation of grub  are examples of what I am suggesting for advanced users to have the option to do .

I'm a little nervous adding that right off , mentioning specific packages is sure to gore somebody's ox .

---

### Post by BwackNinja on 2010-10-24
I like this idea, but it seems to go more along the lines of how the alternate installer or a post-install wizard might work, because the desktop installer doesn't actually install everything through debs. Considering the limits on the CD size, this would just end up as a post-install chroot + apt-get, but on the dvd it would make more sense.

Somewhat ironically, but mostly unfortunately, the more you use ubuntu, the more comfortable you get with it, and the more advanced of a user you become (especially to the point where you will always just run unstable), the less the default desktop is made for you. There is the powerful ui that is synaptic for example, that is being phased out by ubuntu software center, not because synaptic is bad (y'know, other than just always running as root), but because the users that ubuntu is targeting shouldn't need it. For their extra advanced functions, they would be sent to the command line anyway.

On the note of specifically making grub easier to use for advanced users, it would be nice to be able to specify which partition has the grub that is written to the mbr, so that partition would be chroot'd into and update-grub would be run from there every time a new kernel emerged.

Also, in minorly related news, I'm planning on writing a simple reboot dialog that incorporates grub-reboot.

---

### Post by MishaAct on 2010-10-25
Power user doesn't need in synaptic &#8212; the console is enough

---

### Post by ronacc on 2010-10-25
@ BwackNinja  I don't think a text based alternative without all the fancy graphics and animations would take up all that much space and I am not saying ignore the newbes just don't ignore the users that are more experienced .

@ MishaAct   That was just an example , the point was choice , A or B or or C or none .

---

### Post by BwackNinja on 2010-10-25
@ronacc, I'm not talking about just adding an extra installer, that's not hard and doesn't take up much room. The problem is having the extra packages on the cd/dvd because otherwise it becomes something not much different than just doing the extra installation and removal after you've booted into your new install.

Advanced users are more neglected because they can address their own problems, unlike the newbies. Space is a constraint that makes it difficult to appease both parties. A new cd would be mostly redundant and also confusing to people.

How do you propose such a system would work to appease the more advanced users without confusing newbies and being significantly different than the normal post-install customization we do anyway? Would a common extra's cd work well for something like this?

---

### Post by ronacc on 2010-10-25
@BwackNinja what I basicly propose is either a boot menu entry leading to the "advanced" mode and/or an icon once the live cd desktop is up and running ( already existing " try" choice ) that leads to it . The "extra" packages don't have to reside on the cd they can be fetched from the repos, there is already an option to d/l updates in the installer that requires a network connection so an "advanced" mode that requires one is not out of character . 

Would this be significantly different from what we already do ? No not really only in that we won't have to uninstall unwanted items .

is it confusing when Windows offers ( do they still do that ? its been more than a decade since I last installed that crap ) an "express" and " advanced" mode ?

---

### Post by knarf on 2010-10-25
> **kahumba said:**
> It's exactly the same argument like - we should continue driving the old car because for the new and better one we would have to earn money first.
We're not talking about keeping the old car here, rather about keeping the toolbox used to fix both the old as well as the new version. I know I can fix a børked text file without problems - I can even generate one from scratch if needed. Doing the same to a database is not as easy. The closer to the boot loader you get, the more this counts. No matter how much the package management system is changed this will always remain true. Even if you were to use something resembling MySQL or PostgreSQL or whatnot this will remain true.
Of course there is nothing stopping anyone from creating a database using plain text files for data storage. There is no reason why such a database has to be slow either for the amount of data a package manager has to handle.

I am currently compiling [tdpkg]("http://lethalman.hostei.com/tdpkg.html") which adds an sqlite/tokyocabinet cache to dpkg by intercepting some function calls used by dpkg. If it compiles and runs I'll try to be creative in bringing the database to its knees - after making a backup of my 13999 files big /var/lib/dpkg/info directory.

[[COLOR=Blue]some minutes later[/COLOR]] tdpkg does **not** seem to work as it should on Ubuntu/Natty. It does cache the .list files in /var/lib/dpkg/info but goes on to complain loudly about nested calls and unknown file descriptors.

---

