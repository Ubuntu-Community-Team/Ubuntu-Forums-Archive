---
title: "Update Manager Offers a &quot;Partial Upgrade&quot;? Read This."
date: 2009-12-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-12-01
During the past few Ubuntu development cycles, we've been flooded with threads asking for assistance related to issues caused by careless usage of the "Partial Upgrade" feature of Update Manager, which hinted to a poor understanding of package management and the way updates happen in the development branch. 

In an effort to help with this situation, this document aims to clarify what a "Partial Upgrade" is, and why, **in most cases, you'll want to avoid it**.


[SIZE="4"]**Summary**[/SIZE]
[SIZE="1"]or **"I don't really care if I keep messing things up and wasting my and others' time with preventable problems, and you have 30 seconds to convince me to care!"**[/SIZE]

If you use Update Manager to upgrade your packages, and it offers to do a "Partial Upgrade", do not accept it without thoroughly checking what packages it offers to remove, upgrade and install. If you do, you will most likely end up removing packages that shouldn't be removed, and waste time and effort repairing your testing installation and asking for assistance. 

Most "Partial Upgrade" situations occur due to package archive inconsistencies, which will typically be resolved within a few hours. If your package manager is confused, and so are you, **simply wait** and hold off the updates until things settle down. 


[SIZE="4"]**Short Version**[/SIZE]
[SIZE="1"]or **"Hmm, so I shouldn't blindly do "Partial Upgrade"s and dist-upgrade? I didn't know that..."**[/SIZE]

Due to the fact that uploads to the repositories of the active development branch are asynchronous and uncoordinated, dependencies of certain packages may arrive later than the dependent package. This causes package management tools such as Update Manager, which are mainly meant to be used with stable releases of Ubuntu where the package archive is always consistent, to interpret the situation as requiring a dist-upgrade to install new packages and/or repair packages in a "reqreinst" (requires reinstallation) state. What Update Manager performs when doing a "Partial Upgrade" is a dist-upgrade.

When testing development releases, most of the time, a "Partial Upgrade" is undesired. The situations where it's needed are limited to new packages obsoleting old ones (as in the case of the software-center package replacing software-store) and package removals from the archive.

Do not assume that since you're running a development release, a "Partial Upgrade" is necessarily warranted.


**[SIZE="4"]Long Version[/SIZE]**
[SIZE="1"]or **"I want to be a better tester! I care! Tell me more!"**[/SIZE]

In its normal operating mode, Update Manager will not offer to remove packages. This is the equivalent of "apt-get upgrade"ing your existing packages. In "Partial Upgrade" mode, it can. Sometimes, the removal is warranted, such as when a package is obsoloted by a new one. Other times, it will not be, and a "Partial Upgrade" can offer to remove important packages due to missing dependencies.

Now, the key question: 

"**How do I know whether a package is actually meant to be replaced or removed?**"

There's more than one way:

[list][*] Check the changelog of the package in question. You can do this via "Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or by going to [packages.ubuntu.com]("http://packages.ubuntu.com") and clicking "Ubuntu changelog" for the package you're curious about, or visiting the URL 

[https://launchpad.net/ubuntu/+source/](https://launchpad.net/ubuntu/+source/)[COLOR="DarkRed"]package_name[/COLOR]/+changelog

where [COLOR="DarkRed"]package_name[/COLOR] is the name of the source package you're curious about. The most recent changelog entry will indicate the reason for the removal or replacement, if there is one.


[*] Keep an eye on the changes mailing list or RSS feed for the active development release. The current ones are the [Maverick-changes mailing list]("https://lists.ubuntu.com/mailman/listinfo/Maverick-changes"), and [its RSS counterpart]("http://feeds.ubuntu-nl.org/MaverickChanges").

For an example scenario of using the list of recent changes to determine whether a package removal and "Partial Upgrade" is safe, refer to [the next post]("http://ubuntuforums.org/showpost.php?p=8423549&postcount=2").


[*] Check the [build status information page]("https://launchpad.net/ubuntu/+builds") for Ubuntu and the [queue of new uploads to Maverick]("https://launchpad.net/ubuntu/maverick/+queue") on Launchpad to see if those mysterious missing dependencies are coming down the pipes, or there are problems preventing them from being built.


[*] Do a forum search, or [join the #ubuntu+1 channel on irc.freenode.net]("https://help.ubuntu.com/community/InternetRelayChat") and ask around to see whether other people are having problems with the same package(s).


[*] If you're still confused, simply **wait** and see if things are magically fixed within a few hours. If not, start a new thread or post to an existing one on the same issue to check with others.[/list]

A typical interaction with a package manager involves the following three steps:

[list] [*] You select some packages to be installed / removed / upgraded


[*] The package manager resolves your intention according to its package management logic, the available software sources, and the priorities you've indicated (as in APT pinning), if any, to a set of actions it has to perform, and outputs a list of those actions


[*] You check this list, confirm it if you're happy with it, or cancel it and refine your selection until you're happy with it.[/list]

If you skip the third step, assuming that simply updating your package information and hitting "Apply" or pressing "Enter" when the prompt comes up will give you the latest changes, and/or that since you're running a development release, any kind of package conflict / removal / replacement, even those that seem to intentionally remove lots of packages, are to be expected, you'll keep breaking your installation unnecessarily. **Don't do that. Review that list of changes.**

While asking for and providing assistance regarding testing is one of the main functions of this forum, learning [the basics of using development releases]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") is a prerequisite for doing useful testing, and if lots of people keep messing up their testing installations due to being unfamiliar with those basics, the forum will get flooded with duplicate threads and quicky become much less useful to everyone. 

Please take some time to learn the basics, and if you need help with that, don't hesitate to ask!

---

### Post by 23meg on 2009-12-01
Here's a typical scenario in which I figured out whether it was fine to let Synaptic remove *gstreamer0.10-schroedinger*, a package I knew nothing about previously, using one of the methods I suggested in the first post. This could have been any other package manager, such as Update Manager offering a "Partial Upgrade" to remove that package.

[list=1][*] Synaptic offered to remove the package *gstreamer0.10-schroedinger*. At this point I did not know whether Synaptic was offering to remove it due to temporary archive flux, or it was actually meant to be removed.

[[IMG]http://img16.imageshack.us/img16/2705/67492748.png[/IMG]](http://img16.imageshack.us/my.php?image=67492748.png)


[*] To figure out, I decided to check the karmic-changes mailing list **(don't be confused; this is an old example - the current one is [Maverick-changes]("https://lists.ubuntu.com/mailman/listinfo/Maverick-changes"))**. Since I'm subscribed to it, I actually did this **much faster** in my mail client, but for the sake of illustrating how it could have been done without being subscribed (by the way: **subscribing is very beneficial if you're serious about testing** - there's also [an RSS feed]("http://feeds.ubuntu-nl.org/MaverickChanges") if you don't want mail), and even only vaguely remembering the location of it, I'll pretend I browsed it at the web archives.


[*] At [https://lists.ubuntu.com/mailman/listinfo/Karmic-changes](https://lists.ubuntu.com/mailman/listinfo/Karmic-changes) (at which I may have arrived with a web search, or through [https://lists.ubuntu.com](https://lists.ubuntu.com)), I clicked the link leading to the archives.

[IMG]http://img140.imageshack.us/img140/9418/65689993.png[/IMG]


[*] I then clicked the "Date" link for the current month, since I was looking for what's probably a recent change, and I wanted the changes ordered by date.

[[IMG]http://img8.imageshack.us/img8/4152/74695720.png[/IMG]](http://img8.imageshack.us/my.php?image=74695720.png)


[*] I hit "Ctrl + F" in Firefox to search for the word "schroedinger", which is part of the package name, among the list of recent changes. I only typed the first few letters.

[[IMG]http://img12.imageshack.us/img12/2108/48677299.png[/IMG]](http://img12.imageshack.us/my.php?image=48677299.png)


[*] That highlighted what looked like a relevant change! I clicked on it to see the changelog.

[[IMG]http://img14.imageshack.us/img14/4971/85014317.png[/IMG]](http://img14.imageshack.us/my.php?image=85014317.png)


[*] I scanned through [the changelog]("https://lists.ubuntu.com/archives/karmic-changes/2009-October/010163.html") for a hint of whether this package is actually being removed. Searching the page for the words "remove", "drop" or "deprecate" was practical at this point, since I was looking to see if one of those things had happened to the suspected package.


[*] And there it was!
> debian/gstreamer0.10-schroedinger.install:
      - Dropped GStreamer plugin, it's now in gstreamer0.10-plugins-bad.


[[IMG]http://img8.imageshack.us/img8/4224/48655391.png[/IMG]](http://img8.imageshack.us/my.php?image=48655391.png)



[*] OK, it seems the GStreamer plugin for Schroedinger is being merged into the  *gstreamer0.10-plugins-bad* package, and the old package *gstreamer0.10-schroedinger* is being deprecated. So it should be fine to remove it.


[*] Just to make sure, and to satisfy my detective urge, I went back to archive page, and this time, searched for "plugins-bad", which led me to [a change entry for *gstreamer0.10-plugins-bad*]("https://lists.ubuntu.com/archives/karmic-changes/2009-October/011527.html").


[*] I looked for "schro..", and there we go:

>      + debian/gstreamer-plugins-bad.install:
       - Add new asfmux, frei0r, kate and schroedinger plugins.

[/list]

Now I know what's going on, and can comfortably let *any* package manager remove the suspected package. It's fine to accept a "Partial Upgrade" that wants to remove it.

---

### Post by MarkieB on 2010-07-28
no longer participating in ubuntuforums.org

---

### Post by Rasa1111 on 2010-09-14
CRAP!

 I just did this, after 4 days of not doing it. 
And guess what?

 BORKED! lol

 Go figure I didnt see this thread until now. 
grrrr

So, I did this "partial upgrade" , as many things were giving me errors,
broken packages, not authenticated, etc etc etc.. 

 And, It asked for a restart, So I did~
 and upon restart, 

 I only get the black screen  with 
[Maverick Meerkat Development...something....]
 and then the login prompt..

Ahmose@ahmose. login:
Password:

 So i type it all in, 
and I get nowhere but the black screen with text. 

Was the desktop removed by this "partial upgrade"

 I am booted into my Lucid now, 
but I am not sure how to remedy this DOH of mine. 

 My first big "goof" here in Ubuntu land...lol
gahh, i can be such a turd!

 this also seems to have messed up the graphics somewhat, on the boot screen.

 Anyone want/care to help?
:/

 is there a way that I can just delete it from the partition completely? and make a whole new one for it? 

 thanks. <3

---

### Post by ktp on 2010-09-14
since you have command prompt, what do you see when you login as the user?

If you are able to login, try doing what MarkieB said in comment #3.  It is hard to tell what exactly happened.  

One thing you can also try, assuming you can login even to command prompt, try to update sources and upgrade.  

> sudo apt-get update
sudo apt-get upgrade

you can also try to install the ubuntu-desktop package, which should install everything you need to get GNOME desktop.

> sudo apt-get install ubuntu-desktop

not sure this will fix your issue, but something to try.

oh and welcome to Development Release testing. =)

---

### Post by Rasa1111 on 2010-09-14
hey thanks ktp! 

Much appreciated. :)

Ill boot'er up and give it a shot. 

Thank you. =) <3

---

### Post by Rasa1111 on 2010-09-14
login successful, 
update, and upgrade didnt do much, 
and when i tried to install ubuntu-desktop, it said 
"newest version already installed"

 So it can't be that. 

hmm, 
Before i go adding a bunch of stuff to this thread,
would it be better if i just created a new thread? 

 i have some snapshots I took of the couple screens im not sure about,
I just dont want to "hijack" this thread with all my issues. lol
(unless it is preferred):?:

Well, I expected *something* may go wrong,
and ive never 'tested' a distro like this before, so im not really too surprised or disappointed.. 
(except in myself for running the "partial upgrade") lol

Might be better to name it "partial downgrade". :lol:

 Im just very happy my Lucid install is still good. 
I might go crazy(er)) if that didnt work. lol

---

### Post by ranch hand on 2010-09-14
Just don't use UM, do not run apt-get dist-upgrade unless you know what it is doing (check in synaptic) and wait a few days and everything will have caught up (probably).  Good thing s happen for those who wait.

---

### Post by Rasa1111 on 2010-09-14
Can I somehow just remove the 10.10 partition and do it over again?
I mean, I know I can, Im just not sure how and dont want to bork the entire system.

 i know (i think i do anyway) that when you remove a partition,
you must create a new NTFS partition, yay or nay?
Maybe i just got confused in my reading. I dunno.

---

### Post by ranch hand on 2010-09-14
If you just want a clean install go ahead.  Use the manual partitioning option and point it to the partition you are now using for 10.10.  That will be where it is installed.

Should not effect any thing else.

You mentioned ntfs, which is not something on my box, this usually indicates that your box is infected with MS.  If you want to keep it that way it might be a good idea to stare a copy of the MS menu entry for MS from the /boot/grub/brub.cfg file just in case it is not picked up by os-prober.

There is no reason to expect trouble in grub in this respect but if you have the bugger it won't matter.

---

### Post by Rasa1111 on 2010-09-15
ahh cool, thanks. 
Yeah I got confused by something i read earlier i guess [knew it] .lol

Nah there is no MS on this machine,
and ive never seen it on my system i dont think,
but do remember wondering why I didnt have it, when so many people talked about it on their box. lol

 I read something earlier while goggling, and someone asked how to remove an ubuntu partition, and the answer contained something about after removing it, you need to create an NTFS partition..
but now I see that is because he had a dual boot with windows. lol. *doh*

So basically, i just need to use the liveCD, 
open GParted, point to the partition with 10.10 on it,
and remove it? 
or just over write it with a fresh 10.10 install:?:

Thanks much. <3

---

### Post by ranch hand on 2010-09-15
The installer will format the partition.  If you are on two partitions just mark the / to be formatted and it will (back up still a good idea) leave your /home alone.

If you are concerned just mark the mark the partition to be formatted.

---

### Post by Rasa1111 on 2010-09-15
awesome, thanks again ranch hand. :)

Creating backup now.
Will dabble in GParted here shortly. lol :)
<3

---

### Post by jerrylamos on 2010-09-16
update, dist-upgrade HANGS UP on two pc's so far.  Things are really rolling along on update & upgrade from 2.6.35.20 level to 2.6.35-21 when the update screen stops moving.  Cursor is blinking but nothing is happening.  Any way to give it a swift boot to get going again?

If I try a sudo dpkg --configure -a it says there is another process that has a process locked.

If I kill the update, rebooting results in really wierd behavior, black screen or wrong screen size that doesn't fit the hardware or you name it.

Update manager didn't say there was a partial upgrade.  The upgrade just stopped partially done?

What do we do when upgrade is rolling along and then the messages just stop before upgrade completes?  Any graceful way to close?

What do I gather for launchpad bug?  I did bug #640059 when the reboot screwed up the screen resolution.

Thanks, Jerry

---

### Post by ranch hand on 2010-09-16
I just learned about "Ctrl+c".  Will stop what the terminal is doing in its tracks.

Did you try;
```

sudo apt-get update -f

```
?

---

### Post by jerrylamos on 2010-09-20
Apt-get hung on two of my four test pc's so I decided to try update-manager on this Thinkpad R31.  It was at level 2.6.35-19.  Update-manager insisted it would be a partial upgrade.  No thanks.

I rsync downloaded today's daily build.  Booting the CD got a kernel crash so wrote a launchpad bug.

Booting the installed 2.6.35-22 got two kernel crashes but recovered.  Wrote a launchpad bug.  Re-booted and got two more crashes.  Running anyway.....

Jerry

---

### Post by pd71sat on 2010-09-25
I too got this **update-manager** offering a "partial upgrade" and came and found this thread in my search. Still no luck in deciphering what was broken until I saw that package **wine1.2** was unchecked in the update list. Here is what I did to resolve:

1) Closed update-manager and opened up "System"-->"Administration" -->"Synaptic Package Manager". Click "Reload" just for certainty that your package list is current. In the search bar type "wine" to narrow the list pane. The list told me that both "wine" and "wine1.2" were installed. Highlighting "wine" told me this; > This package is to ease upgrades for users of older Wine packages. It can be safely removed. so I marked it for removal. Applied changes and saw that "wine1.2" was still installed. So far so good.

2) Exit "Synaptic Package Manager" and open a terminal session; "Applications"-->"Accessories"-->"Terminal" and issue;

**sudo apt-get install wine1.2**

By Jove it did the install! I was half expecting that it would say that it was already installed. Here is the console output:

> akimisty@akimisty-laptop:~$ sudo apt-get install wine1.2
[sudo] password for akimisty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  erlang-inets erlang-syntax-tools libsctp1 erlang-mnesia libcouchdb-glib-1.0-1 python-couchdb python-avahi
  erlang-xmerl libcurl3 libjson-glib-1.0-0 lksctp-tools erlang-crypto erlang-ssl erlang-runtime-tools erlang-base
  erlang-public-key
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-exe-thumbnailer icoutils imagemagick
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl transfig imagemagick-doc
Recommended packages:
  wisotool
The following packages will be REMOVED:
  ttf-tahoma-replacement
The following NEW packages will be installed:
  gnome-exe-thumbnailer icoutils imagemagick
The following packages will be upgraded:
  wine1.2
1 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 10.6MB of archives.
After this operation, 348kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) karmic/universe icoutils 0.26.0-4ubuntu1 [73.0kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main wine1.2 1.2-1ubuntu1~karmicppa1 [10.4MB]
Get:3 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) karmic/main imagemagick 7:6.5.1.0-1.1ubuntu3 [95.6kB]
Get:4 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) karmic/universe gnome-exe-thumbnailer 0.2 [9,446B]
Fetched 10.6MB in 31s (332kB/s)                                                                                        
Preconfiguring packages ...
(Reading database ... 132865 files and directories currently installed.)
Removing ttf-tahoma-replacement ...
(Reading database ... 132858 files and directories currently installed.)
Preparing to replace wine1.2 1.2-0ubuntu1~karmicppa1 (using .../wine1.2_1.2-1ubuntu1~karmicppa1_i386.deb) ...
Unpacking replacement wine1.2 ...
Selecting previously deselected package icoutils.
Unpacking icoutils (from .../icoutils_0.26.0-4ubuntu1_i386.deb) ...
Selecting previously deselected package imagemagick.
Unpacking imagemagick (from .../imagemagick_7%3a6.5.1.0-1.1ubuntu3_i386.deb) ...
Selecting previously deselected package gnome-exe-thumbnailer.
Unpacking gnome-exe-thumbnailer (from .../gnome-exe-thumbnailer_0.2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Setting up wine1.2 (1.2-1ubuntu1~karmicppa1) ...
procps stop/waiting

Setting up icoutils (0.26.0-4ubuntu1) ...
Setting up imagemagick (7:6.5.1.0-1.1ubuntu3) ...

Setting up gnome-exe-thumbnailer (0.2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
akimisty@akimisty-laptop:~$

3) Can open back "Synaptic Package Manager" and check that the wine search list is unchanged as before. Close and then open **update-manager**. No more "partial upgrade" message pop-up.


Looks like there was some inconsistency in the Ubuntu wine install and package cross reference links.

---

### Post by jerrylamos on 2010-09-25
> **jerrylamos said:**
> Apt-get hung on two of my four test pc's so I decided to try update-manager on this Thinkpad R31.  It was at level 2.6.35-19.  Update-manager insisted it would be a partial upgrade.  No thanks.

Jerry

Found the bug.  By default, CD live and initial install has 3rd party software selected and 3rd party software sources selected. 3rd party stuff is not checked, sanctioned, blessed or recommended by Ubuntu yet here Ubuntu is checking off the 3rd party repositories as selected repositories.

No wonder this is a partial upgrade!

This problem was true for the 90100920 and 90100923 CD daily builds.  Yes I wrote a launchpad bug #640733 on another test machine.

Jerry

---

### Post by Nicram on 2010-09-28
> **ktp said:**
> 

you can also try to install the ubuntu-desktop package, which should install everything you need to get GNOME desktop.


It helped!
Thanks!

---

