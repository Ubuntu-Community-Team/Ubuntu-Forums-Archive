---
title: "Amarok 2 won't detect iPod"
date: 2009-05-22
forum: Multimedia Software
---

### Post by Skerit on 2009-05-22
With every new beta I at least give the new Amarok a try, but it still can't find my iPod! I can't find any other people with the same problem so I really don't have a clue where the problem is.

There's also not a single mention of any multimedia devices in the configuration so I'm really at a total loss, here.

Does it need an extra package to detect the iPod? I have installed KDE4 and libgpod, still nothing.

---

### Post by Gobnuts on 2009-05-23
I have the same problem. 
When the ipod (6G) is mounted, it does show up in the middle-pane of Amarok2 if the "media" applet is activated". 
It has those "+" and "x" buttons next to it, but none of the buttons do anything, the ipod collection is not displayed, let alone any possibility to synch _anything_ ... 

I've been hearing that in order for this to work you need a version of libgpod which is > 0.7. However, libgpod4 is version: 0.7.0-2, yet no go. 
I've also been hearing that might be a Kubuntu-specific problem, for whatever reason.

---

### Post by raycosm on 2009-05-31
Same problem with Ubuntu 9.04 with Amarok 2.0.90 on GNOME. It baffles me, because previously I had been using OpenSUSE 11.1 with the same version of Amarok, and my 3rd generation iPod Nano worked just fine.

EDIT: Tried doing some work.

According to this thread on the Amarok forums, [http://amarok.kde.org/forum/index.php?topic=16178.0]("http://amarok.kde.org/forum/index.php?topic=16178.0"), the problem is "fixed in SVN." That's not really useful to me, and I was using 2.1 beta 1 (version 2.0.90), and it wasn't fixed. amarok.kde.org says that the latest beta is beta 2, which doesn't appear to be in the [kubuntu-experimental ppa]("https://launchpad.net/~kubuntu-experimental/+archive/ppa") that I was getting my version of Amarok for. Remembering [Project Neon]("http://amarok.kde.org/en/node/482") from the times I used Ubuntu before distro-hopping for a while, I decided to give it a try. I install amarok-nightly, start it up, build a collection, then plug in my iPod.

And it still doesn't work. How helpful. Since it worked in OpenSUSE, I'm thinking it's an Ubuntu related problem.

---

### Post by krlhc8 on 2009-06-02
I'm experiencing the same problem.

---

### Post by tarahmarie on 2009-06-10
> **krlhc8 said:**
> I'm experiencing the same problem.

Ditto.

---

### Post by cisoprogressivo on 2009-06-12
Same problem here with Amarok SVN and iPod Classic 6g.

---

### Post by PreviousN on 2009-06-12
Amarok 2 is a disappointment. I *hope* that they can improve it. BTW: It also won't detect my iPod.

---

### Post by Götz on 2009-06-13
Same problem here... it doesn't detect an ipod nano.
 This is strange, maybe it's a package bug.

---

### Post by cisoprogressivo on 2009-06-14
> **Götz said:**
> Same problem here... it doesn't detect an ipod nano.
 This is strange, maybe it's a package bug.
I don't think because I have the same problem with the PPA repository and the SVN version on 2 different computer

---

### Post by cisoprogressivo on 2009-06-14
I tried Kubuntu 9.10 with Amarok preinstalled on VirtualBox and it works fine.

---

### Post by cisoprogressivo on 2009-06-14
I opened a bug on launchpad.
Please subscribe it:
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/386931](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/386931)

---

### Post by Götz on 2009-06-14
After reading on forums and in the Amarok irc channel I know now that the media devices support in Amarok is work in progress, and is currently worked on a GSoC project.

This problem only affects me in version 2.0, but it works in version 2.1.

You can install Amarok 2.1 for Jaunty from this PPA

[https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

add 

*deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main*

in the /etc/apt/sources.list

---

### Post by cisoprogressivo on 2009-06-15
> **Götz said:**
> After reading on forums and in the Amarok irc channel I know now that the media devices support in Amarok is work in progress, and is currently worked on a GSoC project.

This problem only affects me in version 2.0, but it works in version 2.1.

You can install Amarok 2.1 for Jaunty from this PPA

[https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

add 

*deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main*

in the /etc/apt/sources.list
I cant' understand why, but this version works, but the Nightly version doesn't... :o
Thank you!

---

### Post by subsity on 2009-10-27
I have the same problem, I am using the Ipod Classic 80 gigs, The ipod mounts, but neither hippo ipod manage, banshee or amarok detects my ipod. Please help

---

### Post by PsyWolf on 2009-11-01
I'm having this problem in Amarok 2.2 in 9.10  Is anyone else still having this problem?

---

### Post by Al-Man on 2009-11-19
> **PsyWolf said:**
> I'm having this problem in Amarok 2.2 in 9.10  Is anyone else still having this problem?
Me too I have not been able to solve it. any one have any ideas?

---

### Post by ColombianGold on 2009-12-07
Hi,
Im having the same problem using amarok 2.2.1. Ubuntu 9.10 64 bit with an 80 gig ipod classic. Im searching for solutions, hope I can find one.
Being realistic Amarok will be what its supposed to be until 2.4 versions before that well just have to be patient.

---

### Post by LuisGMarine on 2009-12-07
Hello guys!

Well according to some people for some reason a lot of people are having issues having their ipods recognized in Ubuntu 9.10.  So here is a quick fix that works for me and a few people on this board.  Try it out and let me know what you guys think! :popcorn:

First, make sure that your iPod is disconnected from the computer.

Second, fire up terminal by going to **Applications > Accessories > Terminal** and typing in this code:

```
killall -9 nautilus
```

After you run that command, plug your iPod into the computer.  Wait about a minute, seriously sit there and count 60 seconds.

Third, you are going to restart nautilus.  You can do so by hitting **Alt + F2** and typing in "nautilus" (without quotations) and pressing enter.

Now if you open up amarok, banshee, songbird or whatever app you use, it should detect your iPod.

*note if this works for you, you will have to do this every time you plug in your iPod to sync it.  I recommend banshee, it has been the best program to manage my iPod.*

---

### Post by LuisGMarine on 2009-12-08
This successfully has worked with Banshee, Amarok, and Songbird. Again this is all on my system, so please let me know if it works for you guys. :popcorn:

---

### Post by Henry Flower on 2009-12-08
Worked for me in Songbird - thanks!   

However, 'sudo kill -9 nautilus' produced 'ERROR: garbage process ID "nautilus".'   

Then I tried 'sudo killall -9 nautilus', which did the trick.

---

### Post by nelsonie on 2009-12-08
type "df" in terminal, check whether the IPOD mounted directory is /media/IPOD, if not, try to mount it to this directory.

the same thing happened to me before, i tried this way to make amarok to detect my IPOD classic successfully.

Hope it would help

---

### Post by nelsonie on 2009-12-08
> **Henry Flower said:**
> Worked for me in Songbird - thanks!   

However, 'sudo kill -9 nautilus' produced 'ERROR: garbage process ID "nautilus".'   

Then I tried 'sudo killall -9 nautilus', which did the trick.

replace nautilus with its PID(process id)

---

### Post by LuisGMarine on 2009-12-08
well you weren't suppose to run that command with Sudo in front of it.  Just run it straight like I stated in the post.  Glad it worked though.

*edit* just fixed the command the way it's suppose to be ran, just killall -9 nautilus.  Sorry guys!

---

### Post by sanket_s on 2009-12-16
Alright, this does seem to work, but its a pretty crude hack. Problem is I don't see any devices option in Amarok 2.2 in general. Any solutions to that??

---

### Post by rod40cool on 2010-01-06
Well that's bizarre. That works for me too. Amarok and Banshee. I have an iPod 20G Color. Such a strange workaround though, honestly 60 seconds? :confused:

---

### Post by LuisGMarine on 2010-01-06
I was just informed of another workaround that isn't as bad but works.

First open up gconf-editor by hitting Alt + F2 and typing in "gconf-editor".  Then navigate to apps > nautilus > preferences, and un-checking the "media_automount" option.

Close out of gconf-editor and plug in your iPod.  Then open up banshee.  Once banshee is open, mount your iPod by going to your desktop and clicking on Places > "your_ipod_name" and banshee should now recognize it.

I'm not sure you have to follow the steps in the second part exactly, but you are free to experiment.  This I'm gussing might only work with the default ubuntu (gnome) install.

---

### Post by gabaS on 2010-04-04
Works like a charm, finally! Thanks a lot. I've been fighting with amarok quite a while and every once in a while it detected my iPod but i didn't know why...

---

