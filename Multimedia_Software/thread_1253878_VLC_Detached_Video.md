---
title: "VLC Detached Video"
date: 2009-08-30
forum: Multimedia Software
---

### Post by Anonymous Rain on 2009-08-30
Hey guys. Argh this is really initiating. For some reason VLC on Ubuntu has it's video window detached from the main interface. Double You Tea F? I tried checking online for solutions but all I found was all this stuff telling me to install ppa stuff. I tried my best but honestly it was all foreign to me and thus I came to no avail. Can anybody direct me to a .deb package for a version of VLC that doesn't have this issue? It's too iritating controlling two windows for one program.

---

### Post by ad_267 on 2009-08-30
I don't know of another way to do this other than using the PPA, but it's not too hard.

Go to System - Administration - Software Sources - Third Party Software.
Click on Add.
Enter:
```
deb http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
```

To authenticate the PPA you need to open a terminal and enter:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2F021AC1
```

I think the Ubuntu developers are looking at making the process of adding PPAs easier. :)

Then you just need to open the Update manager and if you check for updates there should be an update for vlc.

The problem occurs because Ubuntu has a slightly older version of VLC which has issues with embedding the video, so this feature was disabled. Using the PPA installs a more recent version where this has been fixed.

---

### Post by Anonymous Rain on 2009-08-30
Thanks ad_267, you totally simplified things for me. I entered in all the stuff you said and I'm updating my system now. It's nice to not have to completely depend on my Windows XP guest system to use my favourite programs. Strangely enough the update manager crashed specifically because of trying to update VLC. However simply trying again got around the problem. Strange.

Anyway now I have VLC in all it's single windowed glory! YAY! :popcorn:
SOLVED.
[IMG]http://i26.tinypic.com/20f4y2g.png[/IMG]

---

### Post by andrew.46 on 2009-08-30
Hi ad_267,

> **ad_267 said:**
> I think the Ubuntu developers are looking at making the process of adding PPAs easier. :)

I realise that this goes a little off topic but can I ask for any more details on this move?

Andrew

---

### Post by ad_267 on 2009-08-30
It's part of the plan for the new [AppCentre/Software Store]("https://wiki.ubuntu.com/SoftwareStore").

For October 2010:
> Establish a mechanism for establishing and conveying a trust level for software in PPAs, and for easily adding PPAs within the Store.

Further below under "you should be able to":
> * find software sources (Launchpad PPAs)

    * and know how trusted each PPA is 

I realise that's a while away though and there isn't really anything concrete yet.

---

### Post by HappyFeet on 2009-08-30
If I may add my 2 cents, I actually like the detached screen. It makes things easier when using multiple monitors. When I switch to ubuntu 9.10, is there a way to keep it detached?

---

### Post by ad_267 on 2009-08-30
Yes, it is an option under Tools - Preferences - Interface - Embed video in interface. This option is enabled by default, but didn't do anything.

---

### Post by svamppi on 2009-10-07
This has been annoying me for a while now? Any idea when it will be automatically fixed? Does 9.10 fix it?

---

### Post by ad_267 on 2009-10-08
> **svamppi said:**
> This has been annoying me for a while now? Any idea when it will be automatically fixed? Does 9.10 fix it?

Yup 9.10 fixes it, it has VLC 1.0.2. I haven't actually tested it myself though but it should definitely be gone.

---

### Post by andrew.46 on 2009-10-08
Hi svamppi,

> **svamppi said:**
> Does 9.10 fix it?

I attach a screenshot of vlc running under the Karmic beta and there is some good news there for you :).

Andrew

---

### Post by svamppi on 2009-10-14
Ok, thanks. Can't wait to ruin my ubuntu install yet again by doing a dist-upgrade :P

---

### Post by maresee on 2009-11-17
not working anymore, i try this before 2 weeks and then work, but when i try today it wont. any solution,someone

---

