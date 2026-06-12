---
title: "music player that won't mess up ipod apps"
date: 2012-04-27
forum: Multimedia Software
---

### Post by ttitties on 2012-04-27
I just recently switched over from windows to ubuntu which i love so far. I miss not being able to use itunes to manage the content on my ipod touch and don't mind using another program to do so. 

My main concern is the apps that i have installed on my ipod and whether or not if they or the metadata(saves) will be affected by syncing with other programs. Usually I would just do it and find out but in this case i don't want to risk losing my apps or metadata.  I know i'll have to download apps and podcasts via my ipod touch now as opposed to itunes store but i can deal with that. 

Thanks in advance for all the help.

---

### Post by Paddy Landau on 2012-04-28
You can sync iPods, iPhones and iPads on Linux using Rhythmbox...

... in theory.

In practice, do remember that Apple does not support Linux (even though OSX is very much closer to Linux than to Windows), so if anything goes haywire, you aren't supported!

Unfortunately, if you want Apple products, you must have Mac or Windows to be sure.

You can back up everything on iTunes and try Ubuntu, and if it messes up, try to restore from iTunes; but my personal experience with iTunes is that it loves to just delete stuff without any warning.

Proceed with iPod on Ubuntu at your own risk.

---

### Post by ttitties on 2012-04-28
What if I were to run a virtual OS and install itunes on that? 

What's the best virtual machine program to run on ubuntu 12.04 and would windows xp be my best choice of a virtual OS or windows 7?

---

### Post by Paddy Landau on 2012-04-28
> **ttitties said:**
> What if I were to run a virtual OS and install itunes on that?
You have three options.

[LIST]
[*]Dual boot, which of course means having only one operating system running at a time.
[*]Use a virtual machine.
[*]Use a hypervisor such as KVM to switch between the two; but this is a complex option, so don't choose it unless you are brave and have plenty of time to research.
[/LIST]
 > **ttitties said:**
> What's the best virtual machine program to run on ubuntu 12.04[VirtualBox]("https://www.virtualbox.org/") seems to be the most popular. I have found it easy. Don't install the one from the Repository, but instead add the VB PPA (instructions on the VB Linux download page; scroll down to the Debian instructions. Unusually, the site is down at the moment, so I can't give you the link). Then install through your preferred package manager (Ubuntu Software Manager, apt-get, or Synaptic Package Manager).

You will have to also install the Extensions Pack; again, I can't give you the link, but it's there on the main download page.

> **ttitties said:**
> would windows xp be my best choice of a virtual OS or windows 7?
That depends entirely on your machine. If you have a four-core machine with 6Gb RAM or more, you'll find Windows 7 or Windows 8 runs very well. With lower specs, you'd best look at Windows XP, which uses much less RAM. (Remember that any RAM allocated to your guest will be unavailable to your host.)

Playing around with the VB settings will allow you to tweak your guest for best performance without significantly impacting your host.

---

### Post by tomatoe on 2012-04-28
I'm using my iPod with banshee and so far no problems. 
Of course you'll need iTunes to do some things you can't do in linux like restoring iPod.  But you can do that on your friend's pc, xD

---

