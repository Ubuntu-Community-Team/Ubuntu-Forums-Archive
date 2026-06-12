---
title: "How to install all video codecs with no internet?"
date: 2008-08-09
forum: Multimedia Software
---

### Post by LaserBlade on 2008-08-09
I was looking at the comprehensive how to install codecs thread sticky at the top of the forum thread list and all the instructions required that I have an internet connection on the computer that I have XUBunuti installed to. In fact every site I've been to to install *anything* in Ubuntu assumes that I have the internet. What do I do?

For that matter I need a comprehensive guide on how to install anything at all without the internet. Finding that I have to connect to the internet just to play AVI XVID files in Ubuntu's default video player program is surprising and very disappointing considering the main page of ubuntu.com saying how many common applications are ready to use right after installation. Couldn't they have at least put a set of commonly used codecs on the installation cd itself that would automatically install?

---

### Post by NJBilly on 2008-08-09
If I may make a suggestion...

As far as not connecting to the internet to install software, good luck...

But to solve most, if not all of your Video Codec issues, just connect ONCE and open your package manger [Add / Remove Applications -or- Synaptic Package Manager] and download **VLC Media Player**.

VLC includes 99% of all video codecs from first installation, every one that I've ever heard of with the exception of Real Player codecs I believe.

Then, as you go through your video files, for each filetype (avi, mpeg, etc.) right-click on the file, go to "Open With..." and choose VLC Media Player from the list. From that point on, all video files of that type will always open using VLC.

VLC is GOD for video files, like I said, 99% OF ALL VIDEO CODECS COME STANDARD... You'll LOVE it!

To download from the internet via another computer, use Synaptic Package Manager (via the System Menu) and check the box that says "Download Packages Only" and burn them to CD. Then take that CD to your Ubuntu computer and install each of them - but be sure to begin installing the dependant files first (libraries etc - Synaptic will automatically tell you which need to be included. THEN, run the software main installer that you downloaded).

**If the other computer is NOT Ubuntu**, then the website where you are getting the file from will tell you which libraries, etc. are required to run their software, which in turn, you Google and download the dependancy files, ex: "ubuntu download libxyz", etc.

By the way, no need to be so hostile, you're among some of the most helpful, and friendliest, people on the Internet... I went from Ubuntu moron to Ubuntu GOD in a few months, thanks 120% to the Ubuntu Community, mostly from reading these forums...

Besides, how much did you pay for Ubuntu?


-WW

:popcorn:

---

### Post by LaserBlade on 2008-08-09
[QUOTE=NJBilly;5554258]If I may make a suggestion...

As far as not connecting to the internet to install software, good luck...

But to solve most, if not all of your Video Codec issues, just connect ONCE and open your package manger [Add / Remove Applications -or- Synaptic Package Manager] and download **VLC Media Player**.

I can't even connect once. I just said I have NO internet PERIOD. And if the internet is absolutely required to install anything at all...then I won't be able to use xbuntu, ubuntu or anything related to linux probably for a long, long time. Don't the devlopers realize how many people A. Had an internet connection and it went down for some reason and B. Don't have the money for an internet connection (which I hear can be insanely expensive if you go through a cable company in the U.S.). And no Dial-up doesn't even count due to how slow it is.

Forget this OS, XP works way better. I can download ONE and ONLY ONE file ONE TIME ONLY and install 90% of every program I need via an internet connection that isn't connected to the OS! Yes yes I know XP isn't as stable or reliable but for the simple things (well some of them even not so simple) I do XP gets the job done. And I didn't even NEED the OS to be connectd to the internet to do it! And ubunut DARES to call itself user friendly?! Vista is probably easier to use. At least I don't need to type 2480294 highly tricky and technical commands from a command line to install anything.

---

### Post by NJBilly on 2008-08-09
You know, if you weren't so damn rude, I, or another member, would have happily compiled VLC to your Ubuntu/Xubuntu distro (Gutsy, Hardy, etc.) and attached it to a post, but so much for that idea.

Enjoy Windows, you and Microsoft deserve each other.

---

### Post by LaserBlade on 2008-08-09
> **NJBilly said:**
> You know, if you weren't so damn rude, I, or another member, would have happily compiled VLC to your Ubuntu/Xubuntu distro (Gutsy, Hardy, etc.) and attached it to a post, but so much for that idea.

Actually that wouldn't help much because then someone would have to compile every single program I needed for me! And I'm not being rude, I'm legitimately mad that the internet is a necessity just to get anything at all done in Ubuntu. You would be pissed to if the only internet you had was at the library (and the internet at my library gets used a lot surprisingly. I guess there are many people like me who can't afford an internet connection.)

>  Enjoy Windows, you and Microsoft deserve each other.

Well enjoy Ubuntu while you can still afford an internet connection. The rest of us have-nots will happily install our windows programs using an internet connection to downlaod our programs from anywhere we can get internet instead of being limited to just the computer the OS is located on.

---

### Post by pikseli@work on 2008-08-09
Lets be friends, everyone.

I have not tested this but you can download programs as .deb files, and then move them to your compu on a usb-key or disk or cd, and install them by double clicking.

You need following on your computer: 
vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2

Go here and dl .deb files, each of whats listed above
[ftp://ftp.videolan.org/pub/videolan/ubuntu/pool/](ftp://ftp.videolan.org/pub/videolan/ubuntu/pool/)

Save on a usb-memory. Then install on your non internet compu by filebrowsing to usb-memory, doubleclicking each .deb. libdecss first, vlc, then plugins. Then see if your viddy works by starting vlc.

Sorry, but XP works better only for some things.

---

### Post by NJBilly on 2008-08-09
> **LaserBlade said:**
> Well enjoy Ubuntu while you can still afford an internet connection. The rest of us have-nots will happily install our windows programs using an internet connection to downlaod our programs from anywhere we can get internet instead of being limited to just the computer the OS is located on.

I'm not trying to fight with you... I'll start over... Hi, my name is Bill...

I'm just trying to help you understand that, yes, in some cases there are a couple extra steps to download software, but not as many as it may seem.

And after you acquire and install some software, the chances are less and less that you'll need to download any dependencies at all.

I agree, all linux software should be packaged with all necessary dependencies too begin with, but unfortunately, not all of them are. Why? I have no idea. Too many distros is the main reason, but, in my opinion, they should package for at least the most popular ones - Ubuntu being at the top of that list.

But you CAN download from your library, then bring home to install in Ubuntu, just like Windows. You just need to understand that with freedom comes a price.

As Linux matures, it is becoming more and more user friendly. It's not Ubuntu that is causing your problems, it's the software vendors not including the dependencies and packed code together in a simple to download, all inclusive, archive.

I know you're pissed off, but I'm trying to help you out by getting you past the "speed bumps" in Ubuntu with a fresh install because the end result is soooooooo worth it. You just need to understand that all the work you will put into Linux will be worth it in the end.

I have to go run off to a job, but just think about it before throwing up your arms in disgust. It really is as good as it appears.

-WW

---

