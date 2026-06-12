---
title: "Ripping DVDs"
date: 2011-10-24
forum: Multimedia Software
---

### Post by gupti on 2011-10-24
I've been trying to rip DVDs, and nothing seems to work. I installed acidrip, but it can't find any DVD titles. I then tried to get Handbrake, but with all the PPAs, its more of a headache. I downloaded the RPM package for Fedora 15 (64 bit), and converted it with alien. I installed it, but it does nothing and now I don't know how to uninstall it. Can anyone help me?

I'm on Oneiric, and can't change my account details, so it still says Natty.

---

### Post by Paddy Landau on 2011-10-24
You'll be able to change your details after you hit 50 posts. The moderators placed that restriction in desperation to help cope with the enormous number of spammers.

Try installing [K3b]("Apt:k3b") from the repositories. I believe it will solve your problem.

---

### Post by beew on 2011-10-24
> **Paddy Landau said:**
> You'll be able to change your details after you hit 50 posts. The moderators placed that restriction in desperation to help cope with the enormous number of spammers.

Try installing [K3b]("Apt:k3b") from the repositories. I believe it will solve your problem.

Have you actually used it? Did it work?  I have tried with several dvds and it never worked at all. It may be related to this bug [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/99448](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/99448) (k3b in the repo is crippled as it is not compiled with libdvdread-dev) Don't know if it is still the case.

@Op,

I think handbrake is actually the best of the free ones I have tried. I don't understand the aversion of ppas, most multimedia apps in the Ubuntu repos are either crippled or outdated so as a rule I install them from ppas. Get the daily build ppa if you want to give handbrake another try,

The best dvd ripper by far however is makemkv, it is fast and uses very little cpu, but it is proprietary and you may need to renew something after 30 days (the beta version is always going to be free  as in beer it says) [http://www.makemkv.com/](http://www.makemkv.com/)

---

### Post by shantiq on 2011-10-25
> **gupti said:**
> I've been trying to rip DVDs, and nothing seems to work. I installed acidrip, but it can't find any DVD titles. I then tried to get Handbrake, but with all the PPAs, its more of a headache. I downloaded the RPM package for Fedora 15 (64 bit), and converted it with alien. I installed it, but it does nothing and now I don't know how to uninstall it. Can anyone help me?

I'm on Oneiric, and can't change my account details, so it still says Natty.



hi gupti i have handbrake [**here**]("http://ubuntuone.com/p/nrW/") in my ubuntuone cloud in a deb one for cli one for gui


i installed this 2 days ago on Oneiric and it installed quickly and cleanly

Help yourself  handbrake is very good a program in my experience


**also and i would say as well as** there is [k9copy ]("http://en.wikipedia.org/wiki/K9Copy")  which is in your synaptic or ```
sudo apt-get install k9copy
```

---

### Post by shantiq on 2011-10-25
> **beew said:**
> 

The best dvd ripper by far however is makemkv, it is fast and uses very little cpu, but it is proprietary and you may need to renew something after 30 days (the beta version is always going to be free  as in beer it says) [http://www.makemkv.com/](http://www.makemkv.com/)


hi there beew before i go on a wild-goose chase are u using this one under wine or with the linux version [here]("http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224")


the reason i ask is because it is from 2008 so i wonder if the dependencies are still good

Looks interesting:KS

---

### Post by satanselbow on 2011-10-25
dvdrip in the repos works fine on 11.10 ;) Used to rip main titles out of both an ISO and prop disc. :popcorn:

---

### Post by beew on 2011-10-25
> **shantiq said:**
> hi there beew before i go on a wild-goose chase are u using this one under wine or with the linux version [here]("http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224")


the reason i ask is because it is from 2008 so i wonder if the dependencies are still good

Looks interesting:KS

Hi, I use the Linux version. I think the original forum post was from 2008 but it got updated everytime there is a new version, the one you find there is v1.6.15, which is the latest (same as the Windows one on their main page) 

Never tried it on 11.10, but on 11.04 and 10.10 it installed without a hitch. It is amazing,it is so fast and the cpu usage so low that I can actually rip a full movie in a crappy laptop with only 1G of ram and 1.6 GH cpu without the thing shutting down with overheating,--with handbrake I have to put it on ice,-- but I don't know what will happen after 30 days though so I am still using handbrake as my main ripping software :)

P.S. Unfortunately k9copy is dead, the developer quited.

---

### Post by beew on 2011-10-25
> **satanselbow said:**
> dvdrip in the repos works fine on 11.10 ;) Used to rip main titles out of both an ISO and prop disc. :popcorn:
For me it is always hit and miss, there are many dvds I could rip with handbrake but with dvdrip it aborts midway with some cryptic errors or produces bad quality rip, even if it works it takes considerably longer (with handbrake ~40 mins but with dvdrip takes ~2 hours or longer) I guess mileage can be different depending on hardware and the kind of dvds, but based on my experience I wouldn't recommend it.

---

### Post by satanselbow on 2011-10-25
> **beew said:**
> For me it is always hit and miss, 

I think DVD ripping can be pretty random generally :D I did have a bit of a weird one a while ago where every ripper I used seemed to argue with transcode and DVDrip ended up coming out on top. I do like it's audio ripping by chapter as well for concert discs - a task that seems to be made stunningly difficult by some software.

As you say though different hardware/disc and a different app might be better suited ;)

Worse comes to the worse you can rip DVD from the terminal with ffmpeg :popcorn:

---

### Post by halibaitor on 2011-10-25
> **gupti said:**
> I've been trying to rip DVDs, and nothing seems to work. I installed acidrip, but it can't find any DVD titles. I then tried to get Handbrake, but with all the PPAs, its more of a headache.

What is it exactly you are trying to do with this rip?  Do you want to burn another DVD, or convert the output to another format?  The programs you use will vary depending on your intended usage.  I can give you good instructions for doing a DVD copy, but it uses WINE, since the programs are all written for Windoze.

---

### Post by gupti on 2011-10-25
Thanks for all the replies, but unfortunately I won't be able to try all of the out, as I am quite busy at them moment.:( I have downloaded handbrake, but the GTK version won't install, as it gives me this error in the software center:```
Dependency is not satisfiable: libnotify1 (>= 0.5.0)
``` What am I doing wrong?

---

### Post by beew on 2011-10-25
Where did you download handbrake from?

Did you try this ppa?
[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by alphacrucis2 on 2011-10-25
For anything to do with burning or copying DVD's I find the KDE apps k3b and k9copy work best for me. I also get rid of the debian cdrkit junk and replace with cdrtools which seems to be much more reliable.

---

### Post by beew on 2011-10-25
> **alphacrucis2 said:**
> For anything to do with burning or copying DVD's I find the KDE apps k3b and k9copy work best for me. I also get rid of the debian cdrkit junk and replace with cdrtools which seems to be much more reliable.

How do you get k3b to rip dvd?? It never does anything on my tests.

As said above k9copy is dead so it may be a bad idea to depend on it.

---

### Post by shantiq on 2011-10-25
> **beew said:**
> 

Never tried it on 11.10, but on 11.04 and 10.10 it installed without a hitch.


well thanx for that [**makemkv**]("http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224")

Installed cleanly on Oneiric and works fine
As you said quite fast but no options
Leaves you with a large mkv
Still would favour Handbrake i think zillions of options so you can design your file.

---

### Post by alphacrucis2 on 2011-10-25
> **beew said:**
> How do you get k3b to rip dvd?? It never does anything on my tests.

As said above k9copy is dead so it may be a bad idea to depend on it.


The package is in the Oneiric repos and it works so who cares if the dev has quit. It's not like it requires new features. Most trouble that arises is not with the gui front ends in any case.

---

### Post by shantiq on 2011-10-26
> **alphacrucis2 said:**
> The package is in the Oneiric repos and it works so who cares if the dev has quit. It's not like it requires new features. Most trouble that arises is not with the gui front ends in any case.



in my experience too an excellent program also k9copy   all the k's really:KS no need for improvement or new features

when something works or is designed properly to leave it alone is wisdom

i wish people who designed distros understood this :KS:KS:KS



my favourite and to my mind the most stable and well designed of all music players [XMMS]("http://ubuntuforums.org/showthread.php?t=1525072") has not been maintained for years and yet still the best to me


But for dvd rip if i may summarize


k3b   k9copy   handbrake  makemkv  dvdrip  Linux rules
no need for brilliant windows dvdshrink and dvddecrypter which always work like a dream on ubuntu under wine.....

anyway best of luck...

---

### Post by gupti on 2011-11-09
Hello everyone,
I did not have Internet for 1.5 weeks because I was switching ISPs, but thank you for your responses. I am using acidrip at the moment as it ripped the majority of my DVDs, but I have two questions:

1. I have k3b installed but I'm not sure how to rip a DVD with it. Can someone please explain this to me?

2. I have libdvdcss installed and am ripping with acid rip. However, on some DVDs, when the program loads the video source, it freezes. When I exit, lsdvd is still running in the background so I have to kill the process before it eats up all my RAM. What is the problem?

---

### Post by |{urse on 2011-11-09
[SIZE="4"]dvdstyler[/SIZE]

I think it's in the repos..

---

### Post by beew on 2011-11-09
> **gupti said:**
> 

1. I have k3b installed but I'm not sure how to rip a DVD with it. Can someone please explain this to me?



It doesn't work. The Ubuntu builds are not compiled with libdvdread so it cannot rip dvds.

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/99448](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/99448)

If you want to rip dvd with k3b you have to compile yourself. I did that with the help of mc4man
[http://ubuntuforums.org/showthread.php?t=1874644&page=3](http://ubuntuforums.org/showthread.php?t=1874644&page=3)

However I think handbrake is still the best.

---

### Post by gupti on 2011-11-09
I would be using / would have tried handbrake if I didn't have the problem I posted. (Post  #11).

---

### Post by beew on 2011-11-10
> **gupti said:**
> I would be using / would have tried handbrake if I didn't have the problem I posted. (Post  #11).

Did you install with ppa or from Ubuntu's repository? If it is the latter I am not surprised that it is broken. Don't listen to people who tell you ppas are risky, untrustworthy etc. I install almost all my multimedia stuffs from ppas (with a few compiles) because Ubuntu's offers are always outdated, often broken, crippled (k3b a case in point) or just plain don't work. What do you expect with the repo freeze? Open source never waits til perfection to release so snapshots are bound to have bugs or missing some features, with the freeze bug fixes and new features would not get to the repo during the lifespan of the release (which is 18 months for normal release and will be 5 years for LTS. Imagine no feature update and bug fixes for 5 years)

---

### Post by gupti on 2011-11-10
Unfortunately, I do not know how to add a PPA.

I also tried ripping the DVD with Thoggen, but it acts in the same way as acidrip, stalling, using up all my RAM and not being able to read the titles.

---

### Post by Marller on 2011-11-11
I would suggest for Handbrake one of those two:

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)
[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by SeijiSensei on 2011-11-11
> **gupti said:**
> Unfortunately, I do not know how to add a PPA.

[https://help.ubuntu.com/community/Repositories/CommandLine#Adding_Launchpad_PPA_Repositories](https://help.ubuntu.com/community/Repositories/CommandLine#Adding_Launchpad_PPA_Repositories)

---

### Post by tyrian on 2012-01-28
Thanks SeijiSensi, the missing link for a few of us

---

### Post by Welly Wu on 2012-01-30
I use Ubuntu 11.10 64 bit and I use K9Copy to rip my DVD-Video movies. It works for most DVD-Video movies that I used. I am new to Handbrake and I am learning how to use it in order to save a significant amount of available disk space. Handbrake will not allow you to rip encrypted DVD-Video movies unless you have installed ubuntu-restricted-extras and VLC together. I prefer lossless audio and video formats as I do not want to degrade sound or picture quality, but I am tempted to switch to lossy video formats like H.264 or MPEG-4 in order to save hundreds of gigabytes of available disk space.

---

### Post by ColdnitroX on 2012-01-30
Install a program called dvd::rip. It's in the repos, so all you have to do is ```
sudo aptitude install dvdrip
``` and you are good to go. Should work fine.

---

