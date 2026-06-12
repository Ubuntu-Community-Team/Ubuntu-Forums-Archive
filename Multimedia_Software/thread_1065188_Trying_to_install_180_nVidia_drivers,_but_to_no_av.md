---
title: "Trying to install 180 nVidia drivers, but to no avail"
date: 2009-02-09
forum: Multimedia Software
---

### Post by Slacker20 on 2009-02-09
After searching through countless posts on these forums, as well as several other websites, I have yet to find a way to successfully install the nVidia 180 drivers.

My first attempt (did the whole Ctrl+Alt+F1 thing) resulted in my computer being stuck in low graphics mode and I couldn't figure out how to fix it (searched the forums for that too).  Since I had just installed Linux I didn't have too much on the hard drive, so I just reinstalled and started over.

Now I'm back to where I started, using the 177 driver, but all these screen hiccups and my AWN "gray box" issue is getting very annoying.  Is there a single good, promising method to install the 180 driver without problems?

Any help would be greatly appreciated,
~Slacker20

---

### Post by Slacker20 on 2009-02-10
bump

---

### Post by whaevr on 2009-02-10
Will EnvyNT install the 180 drivers?

I'm guessing you've tried that?

---

### Post by oldsoundguy on 2009-02-10
Envy quit!  Or at least has done nothing since 8,04.  (nothing on their blog in MONTHS!) So their install programs are only good on 8.04 or earlier.  Will not work on Intrepid.

So the work has to be done via the various threads here.  Means some work in terminal if you want to continue to use Ubuntu.

---

### Post by norwoods on 2009-02-10
i used synaptic to install nvidia driver 180.27 from

[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

and all seems good. be sure to change the

apt sources.list entries
Display sources.list entries for:

drop down list box from jaunty to intrepid and follow the instructions.

---

### Post by oldsoundguy on 2009-02-10
An interjection here.
Has ANYBODY been able to get screen rotation to work on older legacy NVidia cards using the new kernel and Intrepid?  If so, can you point me to the proper instructions (not the guesswork I see on so many threads)? Thanks!

---

### Post by Slacker20 on 2009-02-10
> **norwoods said:**
> i used synaptic to install nvidia driver 180.27 from

[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

and all seems good. be sure to change the

apt sources.list entries
Display sources.list entries for:

drop down list box from jaunty to intrepid and follow the instructions.

I'm in between classes right now at college, but I'll give this a try later tonight when I get home.  I started to read some of the directions on what to do, and so far it seems somewhat simple; I didn't read everything yet, though.

---

### Post by Slacker20 on 2009-02-11
> **norwoods said:**
> i used synaptic to install nvidia driver 180.27 from

[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

and all seems good. be sure to change the

apt sources.list entries
Display sources.list entries for:

drop down list box from jaunty to intrepid and follow the instructions.

I followed all the instructions to add PPA to the repositories and added the key.  Now when I open Synaptic I get some 180 driver stuff in my results, however, do I need to install all of these or only specific ones?

- nvidia-glx-180-dev
- nvidia-180-libvdpau
- nvidia-180-libvdpau-dev
- nvidia-180-kernal-source
- nvidia-180-modaliases
- nvidia-glx-180

Thanks in advance,
~Slacker20

---

### Post by cariboo on 2009-02-11
If you select nvidia-glx-180 it will mark the rest of the packages for installation, and yes you do need all those packages.

Jim

---

### Post by Slacker20 on 2009-02-11
Awesome, thanks a lot.  Got everything installed (very easily too), I've opened up several windows at once and haven't gotten those gray boxes on my AWN bar, full effects activated, and so far so good.

:D

---

### Post by couzin2000 on 2009-02-11
Do these repos work for Hardy Heron?
Cause I gotta say, it sound awfully tempting to install Ibex... I need those Nvidia drivers going!!!

---

### Post by Slacker20 on 2009-02-11
> **couzin2000 said:**
> Do these repos work for Hardy Heron?
Cause I gotta say, it sound awfully tempting to install Ibex... I need those Nvidia drivers going!!!

The ones from the site that was linked only show Intrepid Ibex and Jaunty, so I'm not positive but it doesn't look like they work for 8.04 and earlier.

I'd try it on my desktop (8.04) and test it, but it's an old crappy computer with an onboard graphics card.

---

### Post by Crafty Kisses on 2009-02-11
You should have just downloaded the driver from NVIDIA's website.

---

### Post by couzin2000 on 2009-02-11
> **norwoods said:**
> i used synaptic to install nvidia driver 180.27 from

[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

and all seems good. be sure to change the

apt sources.list entries
Display sources.list entries for:

drop down list box from jaunty to intrepid and follow the instructions.

Well, somehow, I thought this was really gonna help me, so I ACTUALLY went and upgraded my pc from 8.04 to 8.10, just to get this repo going. And lo and behold, I add the repo, it installs... and messes up evrything.

I can't get the driver to work, there are some things certain missing... even nvidia-xconfig wont work properly. What am I missing here?

---

### Post by Slacker20 on 2009-02-11
> **couzin2000 said:**
> Well, somehow, I thought this was really gonna help me, so I ACTUALLY went and upgraded my pc from 8.04 to 8.10, just to get this repo going. And lo and behold, I add the repo, it installs... and messes up evrything.

I can't get the driver to work, there are some things certain missing... even nvidia-xconfig wont work properly. What am I missing here?

Once you get PPA added to the repositories and add the key (go [here]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories") for instructions on that), open Synaptic (System>Administration>Synaptic Package Manager) and make sure all these have a check mark beside them:

- nvidia-glx-180-dev
- nvidia-180-libvdpau
- nvidia-180-libvdpau-dev
- nvidia-180-kernal-source
- nvidia-180-modaliases
- nvidia-glx-180

Hit apply, and everything should download and install no problem.  It didn't tell me to restart my computer, but I was still getting the gray boxes on my AWN bar so I restarted and everything is working fine now.

Hope this helps

---

### Post by couzin2000 on 2009-02-11
actually, I gt the message that the driver is not started... so I reboot X, and still, same message. I'm going to reboot entirely now... hopefully this will work.
Curious, I didn't get the libvdpau files... should I have them? are they crucially important?

---

### Post by couzin2000 on 2009-02-11
Nope.... same stuff again.
I get:
```
You do not appear to be using the NVIDIA X driver.
Please edit your X configuration file (just run 'nvidia-xconfig'
as root), and restart the X server.
```

What gives? tried that, doesn't get me anything.

---

### Post by Slacker20 on 2009-02-11
> **couzin2000 said:**
> actually, I gt the message that the driver is not started... so I reboot X, and still, same message. I'm going to reboot entirely now... hopefully this will work.
Curious, I didn't get the libvdpau files... should I have them? are they crucially important?

Not sure if they're crucially important or not, but I just went ahead and put a check mark by all those files I listed.  After I hit apply it downloaded everything and installed in just a couple minutes, and everything went smoothly for me.

---

### Post by couzin2000 on 2009-02-11
Oh dear Lord, have mercy on me.

I finally got it working.... because during one of my frequent reboots, I actually took time out to read the message on screen that said "no power to video card".

I forgot the friggin' wire.

How stupid was that! Thanks for the help (and tolerance to stupidity)

---

### Post by Slacker20 on 2009-02-11
> **couzin2000 said:**
> Oh dear Lord, have mercy on me.

I finally got it working.... because during one of my frequent reboots, I actually took time out to read the message on screen that said "no power to video card".

I forgot the friggin' wire.

How stupid was that! Thanks for the help (and tolerance to stupidity)

Haha, well at least it wasn't something worse.  Glad ya got it working

---

