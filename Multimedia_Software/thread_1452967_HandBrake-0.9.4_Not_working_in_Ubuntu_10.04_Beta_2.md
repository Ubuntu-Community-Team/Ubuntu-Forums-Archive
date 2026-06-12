---
title: "HandBrake-0.9.4 Not working in Ubuntu 10.04 Beta 2"
date: 2010-04-12
forum: Multimedia Software
---

### Post by deeptiman.panda on 2010-04-12
Hi All

I have been using Handbrake for quite sometime now and was quite happy with its performance. After I upgraded to handbrake version 0.9.4 and Ubuntu 10.04 Beta 2, it seems to have stopped working. 

The application starts fine but after I add a video file to convert, the "Start" button or the "Add to Queue" buttons remain disabled. I tried with a variety of file types and files, but the result is the same.

Finally I tried on an older version of my Ubuntu (from a live Remastersys CD) which had Handbrake 0.9.3 and it worked fine. So, I reached the conclusion that it is the problem with the Handbrake version 0.9.4 and Ubuntu 10.04. 

I did not find any information about this in Handbrake's forums. Please help me, as I cannot load any of my movies into my Ipod now.

Attached is a screenshot of Handbrake showing the disabled buttons.

Best Regards
Deeptiman

---

### Post by WinterRain on 2010-04-12
I was on the handbrake forums and was told that hanbrake will not be ready for 10.04 until after 10.04 is final. It will probably be in 3 weeks or so.

---

### Post by deeptiman.panda on 2010-04-12
Thank You.. 

So probably I would have to wait then..

---

### Post by JohnAStebbins on 2010-04-12
The handbrake snapshots work with 10.04
[http://forum.handbrake.fr/viewtopic.php?f=6&t=15901](http://forum.handbrake.fr/viewtopic.php?f=6&t=15901)

---

### Post by haydoni on 2010-04-13
But these, it claims, ONLY work for 32 bit machines...

---

### Post by JohnAStebbins on 2010-04-13
The nightly snapshot build system has limited ability to produce builds for all the various permutations of linux distributions.  A 64-bit version that works on lucid is available in an older (non-nightly) snapshot.
[http://forum.handbrake.fr/viewtopic.php?f=6&t=15452](http://forum.handbrake.fr/viewtopic.php?f=6&t=15452)

---

### Post by twisted_steel on 2010-04-15
> **JohnAStebbins said:**
> The nightly snapshot build system has limited ability to produce builds for all the various permutations of linux distributions.  A 64-bit version that works on lucid is available in an older (non-nightly) snapshot.
[http://forum.handbrake.fr/viewtopic.php?f=6&t=15452](http://forum.handbrake.fr/viewtopic.php?f=6&t=15452)

Thanks John.  This works fine on 64-bit beta 2.  I'm looking forward to the official release down the road.

---

### Post by JohnAStebbins on 2010-04-16
As of this morning, there are nightly svn snapshot builds that are also available in this PPA. [https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by PRupp89 on 2010-05-03
I'm trying to install one of the nightly builds, and I'm getting this error:

Error: Dependency is not satisfiable: libwebkit

I searched the package manager for it, and there are versions of it installed, but nothing that is just "libwebkit"... How can I fix this? I downloaded the gui version for 64

---

### Post by twisted_steel on 2010-05-03
> **PRupp89 said:**
> I'm trying to install one of the nightly builds, and I'm getting this error:

Error: Dependency is not satisfiable: libwebkit

I searched the package manager for it, and there are versions of it installed, but nothing that is just "libwebkit"... How can I fix this? I downloaded the gui version for 64

It looks like this dependency started showing up recently.  I was going to post and say that I haven't had any issues with the PPA, but the handbrake-gtk package on my system cannot be upgraded due what you mentioned above.

Output:
```

handbrake-gtk:
 Depends: libwebkit  but it is not installable
 Depends: libnotify  but it is not installable

```

Actually, I already have libwebkit 1.0.2 installed and libnotify1 0.4.5 installed.  It might be something weird going on with the package.

---

### Post by BHSPitMonkey on 2010-05-04
Here's a temporary workaround for installing the PPA build (which I can confirm works on 10.04/amd64):

[LIST=1]
[*]Uninstall handbrake-gtk
[*]Go to [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/pool/main/h/handbrake/](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/pool/main/h/handbrake/)
[*]Find the handbrake-gtk lucid .deb file for your architecture
[*]Save it into your home folder
[*]Open up a Termina
[*]Run the following command:
[/LIST]

```
sudo dpkg -i --force-all <name of downloaded handbrake-gtk file>
```

This should get you around the libwebkit and libnotify dependencies.

---

### Post by springbokmarine on 2010-05-05
Thanks! This worked perfectly. My speed also increased from about 40 fps to ~100 fps.

---

### Post by Conzo on 2010-05-06
> **BHSPitMonkey said:**
> Here's a temporary workaround for installing the PPA build (which I can confirm works on 10.04/amd64):

[LIST=1]
[*]Uninstall handbrake-gtk
[*]Go to [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/pool/main/h/handbrake/](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/pool/main/h/handbrake/)
[*]Find the handbrake-gtk lucid .deb file for your architecture
[*]Save it into your home folder
[*]Open up a Termina
[*]Run the following command:
[/LIST]

```
sudo dpkg -i --force-all <name of downloaded handbrake-gtk file>
```This should get you around the libwebkit and libnotify dependencies.


Thank you for the Info...  worked great !
Conzo

---

### Post by hursto75 on 2010-06-03
I have handbrake up and running on Ubuntu 10.04. I wrote a how to here:
[http://crackednoodle.com/2010/06/install-handbrake-on-ubuntu-10-04/](http://crackednoodle.com/2010/06/install-handbrake-on-ubuntu-10-04/)

Check it out. Easy and fast.

Thanks,

---

