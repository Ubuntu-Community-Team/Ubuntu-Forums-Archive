---
title: "Dell Inspiron 1521 with ATI Radeon x1270"
date: 2009-08-09
forum: Multimedia Software
---

### Post by tom.swartz07 on 2009-08-09
Hi all,

I have a rather simple question.

I have been using Ubuntu for several months now, and am thoroughly enjoying every minute of it. Just recently I was poking around with Blender, which I used to have on my Vista installation. For some reason of another, the window for blender is INCREDIBLY choppy and leaves artifacts all over the screen. Upon further investigation, I searched my X11 xorg.conf file and found that for some strange reason, there is no driver for my ATI card listed. It simply says:

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```I googled the problem and found that many early builds of Jaunty, 9.04 did not have any support for the ATI cards such as mine. 

My question is; does the final version of 9.04 have support for my ATI Mobility Radeon X1270 card? If so, how do I configure xorg to use it?
Ultimately, My goal is to regain use of the s-video port on the back of my computer to attach a secondary monitor. Until I figure out how to add the drivers for the card, no dice.

Any help would be greatly appreciated!
Thanks a ton!

---

### Post by tom.swartz07 on 2009-08-14
I really hate to do this, but 

bump?

I would like to get my graphics card squared away as soon as possible. Thanks!

---

### Post by tom.swartz07 on 2009-08-17
Im not looking for specifics; the only question I would like answered is; "how do I make sure the driver for my video card is installed correctly?"

Once this is done and I am certain that the card is being used, I could regain the use of s-video out.

Thanks all

---

### Post by RedSingularity on 2009-08-17
Have you looked in the System>Admin>Hardware drivers area?

---

### Post by tom.swartz07 on 2009-08-17
Yes Sir,

The only proprietary driver listed there is the one for my Broadcom Wireless card.

This is where much of the confusion comes from- every place Ive seen mentions that it should be listed there, but for some reason it isnt listed for me.

ATI's website doesnt seem to support it anymore either. Unless they renamed my card to an integrated Radeon Xpress 1200?

Im nearly at my wits end trying to get this working.

---

### Post by RedSingularity on 2009-08-17
In the package manager do you see something installed called "xorg-driver-fglrx"?

---

### Post by tom.swartz07 on 2009-08-17
Im sorry, I failed to mention previously that I have already tried fglrx, and it did not remedy the problem. 

At this moment in time, I am trying to download and install the Official ATI driver for my system. The drivers are no longer supported by ATI, and the last version is 9.3

After this finishes, hopefully it might work. Thank you for the help so far.
Ill let everyone know how it turns out.

---

### Post by tom.swartz07 on 2009-08-17
Nope, it doesnt work.

Installing it, i see
```

tom@ubuntu-laptop:~$ cd /home/tom/Desktop/
tom@ubuntu-laptop:~/Desktop$ sh ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.vDlYBY
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.28-13-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.vDlYBY
tom@ubuntu-laptop:~/Desktop$ 

```


Is there something that Im missing?

---

### Post by RedSingularity on 2009-08-17
No.....looks like you have an old card!  Wow.  How old is it?


Ps:  What is the output of "lspci | grep VGA"

---

### Post by tom.swartz07 on 2009-08-17
My card was stock included with my laptop when I purchased it 2 years ago. The card is, like I mentioned, the ATI Mobility Radeon X1270. It was released around 2007, so Im assuming that the age of the card wouldnt play too much into the fact that this doesnt work, would it?

---

### Post by RedSingularity on 2009-08-17
Hmmm no....doesnt sound old at all.  

Can you post lspci | grep VGA

---

### Post by tom.swartz07 on 2009-08-17
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

```

---

### Post by RedSingularity on 2009-08-17
> **tom.swartz07 said:**
> 

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```
Thanks a ton!


See you area under "Device", well with your fglrx drivers installed (confirm in synaptic) add a line under that that says:
```

Driver  "fglrx"
```

So your new Section will look like this:

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fglrx"
EndSection

```

See what happens if you want.

---

### Post by steefjeqv on 2009-08-18
Hi,

The fglrx driver doesn't support your card anymore.

What you can do is upgrade your xorg-ati driver, using the "xorg on the edge" ppa :

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

Before applying this upgrade, make sure you've removed all the fglrx stuff :

sudo dpkg --purge fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

Greetings,
Steven

---

### Post by arktist on 2009-09-12
Tom I have the same laptop. Similar problems.

It seems 9.3 isn't supported by Jaunty. I decided to try to install Intrepid on another partition. It recognizes the proprietary drivers however doesn't seem to want to use S-video yet. I haven't set up the xorg.conf... not sure that it is necessary? But that is my next course of action. I'll let you know what my results are.

Did you have any luck with karmic or ppa or anything for that matter?

Thanks

---

### Post by steefjeqv on 2009-09-13
Hi,

I'm using the xorgontheedge ppa on my Thinkpad T60. The graphics chipset is an X1400.

It works quite good. And this driver will be gaining more features as of kernel 2.6.32 (kernel modesetting, power management,.....).
A combination of 2.6.32, Karmic and the xorgontheedge ppa will get good performance out these ATI chipsets.

Greetings,
Steven

---

### Post by yoshiki2 on 2009-11-08
try using open ati drivers

---

### Post by pme 72 on 2009-11-09
Not that it will necessarily solve the problem but shouldn't a RS690M series ATI card be supported by the current fglrx driver? 500 series and below are legacy. 600 and 700 series should be supported.

---

### Post by JevonPenguin on 2009-11-10
I use Kubuntu 9.10 Karmic on a Gateway M-1624 series and until a moment ago had the same problems with blender that Tom had. I also have an x1270, which is a bit quirky at times, but I have finally gotten to run. I am running some generic Xorg radeon drivers found through Synaptic, and I discovered this thread:
[http://ubuntuforums.org/showthread.php?p=8283887](http://ubuntuforums.org/showthread.php?p=8283887)
You lose slight performance, but it makes blendering much easier.

---

### Post by jaypmcwilliams on 2009-12-21
NOT to single anyone specific, but some statements were made, by others on this thread, to a question. those comments were just a little too harsh. PLEASE remember, people look to us to help, NOT INSULT OR ASSUME!!!!! ATI DOES still support the xpress series & specifically x1270 IS listed & supported with Ubuntu Karmic, Intrepid, Jaunty.... However, the files it needs to complete it's installed, setup & completion were NOT included in karmic, NOR are they available. Let's see what we can do to fix this instead of making up answers for our own ignorance.

---

