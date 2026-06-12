---
title: "[SOLVED] Getting a webcam to work in Ubuntu 8.10 Intrepid"
date: 2008-12-27
forum: Multimedia Software
---

### Post by mtopro on 2008-12-27
Just wanted to document and share how I got my webcam working and updated to the latest drivers in 64bit Intrepid.

First of all, the reason for this post is I went through archives and could not find a good solution to get the hardware working. Also the archives were a bit outdated and closed, thus the new post..

Installation of the Hercules Classic Silver webcam was really easy after the correct information was found at:
[http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page")

Please check at this site first to see if your device is supported under the latest builds.  If so this should hopefully work for you.

Follows is the summary of the steps:

How to build from Mercurial
From LinuxTVWiki
Jump to: navigation, search
Contents
[hide]

* 1 Check kernel version
* 2 Install Mercurial
* 3 Retrieve v4l-dvb sources
* 4 Build the Modules
* 5 Load and Unload the modules
* 6 Errata - Compilation
* 7 Errata - Compilation - Kernels before 2.6.22
* 8 Errata - Loading Modules
* 9 More Errata

Check kernel version

First of all, you need a quite recent kernel. The v4l-dvb tree is backwards compatible with recent vanilla kernels. Kernel version 2.6.10 or later is required to build the dvb modules, and version 2.6.12 or later is required to build support for hybrid devices. If you configured the kernel manually, please note that some capabilities should be enabled like EVDEV. Stock kernels usually have everything required. You also need to install the kernel-source package to have kernel headers.
Install Mercurial

V4L and DVB kernel modules are available via Mercurial.

To acquire the latest sources, you must first have mercurial installed (which requires python 2.3). Some Linux distributions already include it. In Debian, just do:
> apt-get install mercurial

If your distribution doesn't include it, you can download a binary package or retrieve the source.
Retrieve v4l-dvb sources

Now you need to pull the tree from hg.

To retrieve the v4l-dvb source tree:

> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

To update the sources later on:
> 
cd v4l-dvb
hg pull -u [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

To retrieve the dvb-apps source tree:
> 
hg clone [http://linuxtv.org/hg/dvb-apps](http://linuxtv.org/hg/dvb-apps)


**Build the Modules**

Make sure to change into the v4l-dvb directory (already there?):
> 
cd v4l-dvb


Build the modules:
> 
make

Then install the modules:
> 
sudo make install

The command above will copy *.ko module files into your /lib/modules kernel directories.


**Load and Unload the modules**

To remove (rmmod) all modules at once from the running kernel (in memory):
> 
sudo make unload

To insert (insmod) all modules at once into the running kernel, without the need to install them:
> 
sudo make load

OR..  To perform the two commands above in a single step:
> 
sudo make reload


Usually correctly installed modules will show some info in dmesg, errors will appear in dmesg also.


Although there is a method shown above to reload the kernel, it has never worked for me personally as well as simply rebooting the machine.  So I would recommend a reboot.

Hope that helps!
:guitar:

---

### Post by itix on 2008-12-28
I think it'd be best if you submitted this to the howto section ;)
Great instructions btw...

---

### Post by mtopro on 2008-12-29
Good call!  I knew there had to be a better place for this kind of thing.. Posting now.  Thanks!

---

### Post by El Viejo Lobo on 2009-02-20
It did not worked for me:(
I found the way to use skype with my Dlink C320  webcam.
It goes like this: boot/esc then chose kernel 2.6.24.xx let it fnish booting and OP'S webcam works.
A note: your [SOLVED] is relative to your very specific case, I spent hours looking for a solution that works automatically and got noting.

---

### Post by mtopro on 2009-02-23
Sorry it did not work in your specific instance.  It is strange to me that the older kernel supports your webcam but the newest does not.

Perhaps something should be added to the post.. You should look to see if your device drivers are supported on the latest build.  This proceedure should work for anyone who wants the **_latest_** drivers that are supported under Linuxtv.

Since I posted this the website has changed and I am now updating the original post to show the latest wiki locations.

---

