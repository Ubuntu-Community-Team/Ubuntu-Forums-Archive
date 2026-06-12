---
title: "How I successfully installed Slimserver on the first try"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by m9ke on 2007-09-19
Thanks to a lot of good folks on this forum, I have my Ubuntu box up and running, after lots of upgrades and learning experiments.  Figured it was time to do some thing useful, so decided to transfer my SlimServer and all my digital music to my Ubuntu box.  I had already set up the wireless network and WPA-secured it, when I first built this out under Windows.

In my first run at it, I installed SlimServer  v. 6.3.0 via Synaptic Package Mgr.  This is a downrev version.  The install worked, but I had all kinds  of problems running the software; so many so that I went to SlimDevices forum and looked around.  Much of the advice there boiled down to "use the latest version".  There were also a number of folks who were having problems installing even the latest version from the terminal in Ubuntu.

Honestly, as a newbie, I was thinking that an install from the terminal would not go flawlessly the first time but I was willing to figure it out and make it work.  What I found was a different way of installing that i did not even know about, which was easy and worked flawlessly the first time.

Made my way to [http://wiki.slimdevices.com/index.cgi?DebianPackage](http://wiki.slimdevices.com/index.cgi?DebianPackage) where I found directions to do the following:

1. Go to this file and edit it:```
/etc/apt/sources.list 
```
I had not done this before, so it was a good thing to learn.

2.  To my sources.list, I added just one line: ```
deb http://debian.slimdevices.com stable main
```
If you are planning on following these directions, type or paste that exact string into your 
sources.list file.  Note that you could install pre-release or testing versions by substituting something else for "stable".   Directions for that are on SlimDevices wiki.

3.  The directions on SlimDevices  wiki ([http://wiki.slimdevices.com/index.cgi?DebianPackage](http://wiki.slimdevices.com/index.cgi?DebianPackage)) said:
"...And then run:

```
apt-get update
apt-get install slimserver

```

It turned out I did not need to do that!!   What happened almost immediately was that the Ubuntu Update manager popped up an "updates are ready" notice for me.

It was the SlimServer  update to version 6.5.4,  including dependencies.

After installing and copying all my music to my Ubuntu box, I rescanned my music lib in SlimServer  (trivial) and everthing just worked.  I have been listening to it all day, and it's cool to know my music in now on Ubuntu!

Disclaimers:  
1-Please note that i had already set up all the wireless networking including WPA when I first set this up in windows.  I completely got around any Ubuntu wireless issues by cabling it to my Linksys wireless router.  

2- As soon as I fired up the Squeezebox with the new software, it grabbed a firmware update.  Totally normal, but if you don't expect it you might be surprised by this.

3-There was a bit of setup on the Squeezebox, but it was trivial.  I had to put my password back into the the Squeezebox using the remote control, but it was no big deal.  Maybe it got overwritten by the firmware update.

4- You will get a couple of security warnings when you go to download the upgraded software.  I was comfortable ignoring them.  If you are not, you are stuck with the Ubuntu-supported version, until it gets updated in the repos.  YMMV.

5-I have nothing to do with SlimDevices besides being a totally happy customer, with three Squeezeboxes up and running on my wireless network.  And now on Ubuntu too!

---

### Post by CRCarl on 2007-11-08
m9ke - 
      Thanks for the info! I was considering buying the Squeezebox because of the Linux support and your post helped convince me. 

     You might want to preface your post with HOWTO:.

Thanks, 

Craig

---

