---
title: "So I'm at a total loss...how to install Ardour and Jack"
date: 2007-05-14
forum: Multimedia Production
---

### Post by hurtstotalktoyou on 2007-05-14
So, I'm trying yet again to learn to use Linux.  I installed Ubuntu 6.06 (I figure support would be more developed and longer-lasting than 6.1+), and I need to start learning to do some of my most common Windows tasks in this new open-source environment.  One of the things I do most often is record multi-track audio.  For this, I've heard the only free Linux solution is Ardour, which requires Jack to work properly.  So, I need to figure out how to install these two apps.

Of course, the Ardour website is absolutely no help.  It only offers me the source code, and, I'm sorry, but building programs is out of my league at the moment, when I can barely handle package management.  I looked at Ubuntu Studio, but that's apparently an entirely different distribution, which means I'd have to re-install everything from scratch, including the OS itself.  While I may eventually be forced to do that, I'd like very much to avoid it.

I tried sudo apt-get install ardour-gtk jackd and a few variations to that effect, but nothing seems to work for me.  I always get some kind of error message, usually something like "package ardour-gtk is not available."

So, what do I do?   Is there some program other than Ardour that can record/mix/edit multitrack audio?  If so, point me to it!  And in the mean time, can anyone tell me the mysterious secret to installing Ardour and Jack on Ubuntu 6.06?

Thanks in advance!

---

### Post by Pocadotty on 2007-05-14
first off, It doesn't make sense to go back to 6.06 at this time unless you have a GOOD reason to do so.  6.10 is extremely stable and also can easily upgrade to 7.04 from the update manager, without having to reinstall everything.

You should reconsider, and at least install 6.10, because with that release you have the ability to upgrade without reinstalling. I would recommend 7.04, which makes a whole lot of thing a good deal easier. but if you want 6.06, then thats your choice.

if you had 7.04 you could upgrade to Ubuntu studio without having to do a system reinstall... I know because I did all that like 2 days ago.  There are a lot of benefits to Ubuntu Studio but in your case (because you are using 6.06) you would have to reinstall to get them... at least as far as I know.

If you dont want to upgrade then just go to Applications-->Add/Remove applications and under Sound and Video  find JACK, click the checkbox, then find Ardour and check that box... click apply and your in business.

note: that installs Ardour 1, which I found a good deal worse then Ardour 2.  The only reason why I didnt give you the instruction for Ardour 2 is I dont know how it works with 6.06.

if you cant find them in Add/Remove Programs, do a search in Synaptic Package Manager for them and mark them for install.

for simplicity sake, you may be better off using Audacity, which works without JACK, but it can only record 1 audio track at a time, but it can handle mixing as many as you want.

Unless you already have a lot of things installed and configured in 6.06, you should seriously consider upgrading to Ubuntu Studio, which has mostly everything you could want as a default application.

Best of luck

---

### Post by drosky on 2007-05-14
> **Pocadotty said:**
> first off, It doesn't make sense to go back to 6.06 at this time unless you have a GOOD reason to do so.  

I agree with Pocadotty on this, but here are a few extra comments, FWIW:

There is an upgrade path from 6.06 to 7.04, but it's a little cumbersome.  You first have to upgrade from 6.06 to 6.10, and once that's done, upgrade from 6.10 to 7.04.  This should work pretty well if you have a system where you don't have many things that weren't installed from the Ubuntu repositories.  I just did this a few weeks ago on my daughters system and it is working fine.  For more info on upgrading, look [here]("http://www.ubuntu.com/getubuntu/upgrading").  Remember, upgrading will work best the more your system consists of purely Ubuntu packages from the respositories.  Be prepared to re-install if upgrading doesn't work out, since it's not easy to back out.  Whether by upgrading or re-installing, you'll probably be happier if you move to 7.04 since packages are far more up to date, plus you can use things from Ubuntu Studio.

Also, Audacity can record more than one channel at a time.  If you have a stereo sound card as most PC's have, you can record both channels (L and R) simultaneously.  If you have multi-channel hardware that is supported in Linux, you can record more, I think the limit is either 8 or 16.

---

### Post by sunnshol on 2007-05-15
This seems like a good place for my question as well. I'm running Feisty Fawn, the 64 bit version, on an Athlon dual. I had to install Ardour itself in a roundabout way, as it was (and still is) ghosted out in the "Add/Remove Applications" wizard.

My question is simple, how do I go about installing Ardour 2? No way am I going to install a whole new distribution just to get it.

Anything obvious I'm overlooking, or any education anyone can provide, will be very appreciated.

---

### Post by Pocadotty on 2007-05-16
First thing first, before you install Ardour 2, you need to uninstall Ardour1... otherwise you will run into problems

If you have not already done so, add the Ubuntu-Studio by executing the fallowing commands in terminal
```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
``` and then ```
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Add/Remove ghosts out non-standard Ubuntu repositories.  If you cant find something in Add/Remove, search for it using Synaptic, which doesn't ghost out anything.  For instance, google earth is not in the standard repositories but it is in medibuntu, so i searched for it in Synaptic and it was there.  Same with Ardour 2.  If you cant find a package in Add/remove, search for it in Synaptic.

You can upgrade to Ubuntu studio without reinstalling, but I would hold off on that because you are running a 64bit system, and as far as I am aware the current release is just for i386(32 bit intel/AMD)... they should have the others up soon

---

### Post by ricrac on 2007-05-16
Audio and video production are some of the trickiest things to configure.
To do it optimally on a budget you'll need at least two machines.
1. machine to surf the web for help files, config help, tutorials, audio sample and video downloads, etc. and optionally to run virtual clients for testing.
2. audio workstation with 3 large harddrives, $150 = 500gb.
You'll want separate read and write drives for AV data and system
All samples and snippets are on the read drive.
All mixing/writing to the write drive.
All OS installs on the system drive.
Separate partitions for OS installs, 4gb each  (4-8gb depending on distro and apps installed) 
Separate/shared home partition   for settings retention, contains browser and desktop caches
Separate/shared home/document partition   for your important docs/data

Now install each of the following distros (if you like/need any of the features) into a 4gb partition.
jacklab
ubuntustudio
media64
dynebolic
ccrma on fedora
etc.

Each distro will have certain apps/frameworks setup and working.  Test all and decide which you want/need.  
You will invest a great deal of time getting everything working together, but you can achieve many working sets much faster.  If you need ardour2, install the best distro for ardour2, get ardour2 working, then work on getting the minimum you need to work simultaneously with your preferred system.

Audio and video are dedicated tasks.
Your email, calendar, browser, etc. are all on the surfing machine, not the audio machine.
Once your audio machine is set up.
Reboot to do dj mixing for a party
Reboot to do jack, ladspa plugin, wine vst, etc.
Need new ardour version. Copy best distro or re-install to new partition.
Reboot into new install and setup ardour2, never touching your already tuned lowlatency multi-source synced, custom kernel driver standard setup.

Hopefully very soon Xen or KVM will be able to do hardware virtualization with no performance penalty and dedicate hardware to specific virtuals.  Then you can do this all in "one" install.

More specifically to the question.
6.06 should be installed to the surf machine, you don't want to mess with this one.
7.04 should be one of the OS's installed to the audio machine, you'll want whatever kernel, config, framework, application improvements as soon as they are tested.  They will never be available as fast in a LTS system.  That's not what LTS is for, LTS is stability and security before feature creep.  
From the ardour website "Ardour's primary developer uses Fedora with Planet CCRMA", so Fedora core 6 should be installed for ardour2 testing, it "should" be the best environment since it is the developers.  This is not always the case, the author states he does not compile himself so any distro could do a more complete job of configuration and correct compiling given the preferred frameworks of said distro. 

That's why I like to use virtualization (vmware is easiest and free currently) for all my testing.
I can install and run many distros to see what comes out of the box without tying up a whole machine during installs/reboots.  Most apps will work fine on virtuals for tutorial work with web access for help and data sources.  On the real audio station you do not want a browser running.  All browsers (konquerer, firefox, opera,) will tax the system heavily, too much memory, too many file writes in cache, too much cpu overhead.  


Here is my general multiboot setups:
Surf/Private system - two os's, current and recovery, recovery used for upgrade installs.

Audio/Video/CNC system -
mythtv  - for guest usage, watch tv, videos, listen to music, surf the web, play games playable in linux, no access to anything critical
ubuntuEMC - for cnc project use
coding - for programming, compilers, IDE's, web surfing, databases, web servers, etc.
print production - scanning, printing and desktop publishing, fonts, ICC, hugin, nips, qcad, scribus, openoffice
elearning - education linux system for client projects
audio production - jack,ladspa, vst, alsa, midi, etc.
video production - kino, cinelerra, jahshaka, etc. 
Windows XP- I have to have it for some client testing and roland CNC.
Client OS's - specific installs for each client I support.
Virtual manager - runs all others as virtual clients. This is where I spend most of my time.  I'm writing this from a Ubuntu 7.04 virtual client. If I am hacked, install something broken, break my configuration, hopefully only the virtual will be compromised.

When I do production CNC, audio or video work I need to reboot into a specific realtime or low-latency kernel depending on the project to have a consistent stable platform to do constructive work upon. I wouldn't think of wasting any time trying to get EMC cnc components working with jacklab (audio) or dynebolic(video). No ROI there.

As far as waiting for the 64bit versions.  Don't.  They won't be there soon.   
CCRMA and studio64 have had 64bit versions for awhile now and still don't have all the bugs worked out. 32bit versions will be more stable and tested than 64bit versions for another year or two unless the primary developer on the project runs on a 64bit machine.

These suggestions are given with a focus on less wasted time, less effort in configuration, faster access to new upgrades. 

Virtual or multiboot credo - never break a working system, get a new virtual/multiboot working with the new app, then try and install into a copy of the working system, at all times (virtual or reboot) have the original system available for productive use.

---

### Post by Pocadotty on 2007-05-18
ricrac, your setup probably works well for you... but it seams far too complicated.

To me thats seams like a months worth of solid work to just get started.  Never mind managing all the various distros once you have it set up.

what is the purpose of this massively multi-booted machine... it seams like a whole lot of redundancy for no purpose to me.

Especially as advice for someone, who is new to linux, who just wants to install  a couple apps.

If there is a necessity for your setup and you want to let people know, start a new thread, because that much work is a massive undertaking for anyone, and an extremely daunting task for someone new to linux, therefore it is overkill and off topic.

---

### Post by ricrac on 2007-05-19
I do production work, but each type only on an occasional basis.

Until Ubuntu studio came out, Jacklab and dynebolic saved hundreds of hours of compile, config, tweak time for audio.

You could spend hundreds of hours building a realtime kernel base system with all the tweaks necessary to run EMC, or just install BDI or ubuntu emc and be routing or milling easily within an hour. I wouldn't even think of trying to configure EMC on fiesty or 64bit.  Why would I?  So the next update I would have to patch again instead of just updating the distro they (EMC) uses?
Plus I would get no support since I would no longer be running on the authors setup.

Ipcop and other distros have all firewall, spam filtering, proxy filtering, etc. setup out of the box.
I've built, tested and deployed firewalls with VPN's for distributed offices in little more than drive time. 

Until recently, Knoppix was the main player in liveCDs, invaluable in crash recovery and compatibility testing.

Each distro does it's own thing well.  Multiboot takes little effort. For power users, upgrades don't work yet and will require hours of tweaking after an upgrade.  

Consider a business view.  The business server works fine.  Next distro is released.  You build this on an alternate boot partition so if it doesn't work you can reboot into the "old" stable version.  Or course you test first on another machine, but quirks happen and you don't destroy a working system just to get new features.  If all goes well you'll never use the "old" system.  Until later that first day when app X finally get's used, you push load over 70% and start getting errors you didn't get on the old system.  If it's a critical system, you went too fast, so you back out (reboot to "old" stable) and go back to QA testing.  It might not be the "best" way but management pushes and multiboot has save me many times. 
It's not an excuse not to test.
It's usable backup.

For my friends with young children or teens who use and share only one machine, it's the only sane way to work.  For parties where you want to leave a "jukebox" for audience choice of music, it's a much more safe and secure way to go. 


It's definitely not for everyone, two machines or more are required to make the best use of install and reboot time when/if required.

---

### Post by ricrac on 2007-05-20
Here's some recent LJ posts on audio. 
The authors uses 64Studio for ardour2.
[http://64studio.com/](http://64studio.com/)
and Jacklab for ardour with vst plugins
[http://jacklab.net/](http://jacklab.net/)

Ardour2 article
[http://www.linuxjournal.com/node/1000224](http://www.linuxjournal.com/node/1000224)

other recent audio related 
[http://www.linuxjournal.com/node/1000216](http://www.linuxjournal.com/node/1000216)
[http://www.linuxjournal.com/node/1000208](http://www.linuxjournal.com/node/1000208)
[http://www.linuxjournal.com/node/1000208](http://www.linuxjournal.com/node/1000208)

---

### Post by kayosiii on 2007-05-24
Well Ubuntu studio is now out and I can reccomend it as the easiest way to get Ardour2 up and running on Ubuntu

---

