---
title: "Songs not transfering to Creative Zen?"
date: 2009-11-30
forum: Multimedia Software
---

### Post by Xjjulix on 2009-11-30
So, it'll mount fine, I'll access the music folder, drag the mp3 file into it, and it'll even say that its transfering the song. But when I unplug my zen, I can't find the music file even though when plugged in the file showed up in the music folder on my computer.

Is this just a problem with the zen, or my computer? Is there any way to fix it? Because if not, I have to go to windows to transfer songs and it freezes up every three seconds...>_<

---

### Post by the hoplite on 2009-11-30
Yeah I had the same problem of yours. The most direct solution is to install Gnomad2, unmount the previously mounted Zen and then transfer the content. To upload the art files you'll have to use Amarok 1.4, mounting it like this:

• sudo mkdir /media/MyZen
• sudo chmod 775 /media/MyZen
• sudo mtpfs -o allow_other /media/MyZen
• sudo umount /media/MyZen (for the unmounting)

Cheers

---

### Post by Xjjulix on 2009-12-04
So, I installed Gnomad2. And when I open it, I get this.
"No jukeboxes found on USB bus"

._. Is this supposed to happen? I'm like, a super newbie when it comes to these kinds of things.

When I try opening it through sudo, I get...

usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
PDE device NULL.

And when I put in all of those commands from the above, I get

sudo: mtpfs: command not found


Gah.

---

### Post by Leighman on 2009-12-07
I'd also appreciate some help on this. Same as above post.

---

### Post by Leighman on 2009-12-07
[http://ubuntuforums.org/showthread.php?t=1307028#2](http://ubuntuforums.org/showthread.php?t=1307028#2)

This post worked for me.  Make sure you plug it in when Rhythmbox is already open.  Doesn't appear to work in Banshee.

---

### Post by Kaffeekranz on 2009-12-08
The only solution working for me came from this little german guide.

[http://physicistatwork.wordpress.com/2009/10/25/creative-zen-mit-mtpfs-unter-linux-wie-einen-usb-wechseldatentrager-einbinden/](http://physicistatwork.wordpress.com/2009/10/25/creative-zen-mit-mtpfs-unter-linux-wie-einen-usb-wechseldatentrager-einbinden/)

I'll try to translate it:

First charge your Zen, then disconnect it from your computer.
Afterwards you should do a cleanup when booting into failsafe mode.

He gives you the advice to remove lib8mtp completely to be sure that you're having all your packages updated and right where they belong.

So let's start:

```
[COLOR=#ff0000]*sudo apt-get remove libmtp8 libmtp-dev*[/COLOR]
```Confirm with yes.

Then afterwards doing an autoremove and purge type

```
[COLOR=#ff0000][I]sudo apt-get autoremove
sudo apt-get purge[/I][/COLOR]
```And now we'll install the libmtp packages again.

```
[COLOR=#ff0000]*sudo apt-get install libmtp8 libmtp-dev mtp-tools*[/COLOR]
```Next you'll need some more packages, including fuseutils, etc.

```
[COLOR=#ff0000]*sudo apt-get install libnjb5 libnjb-dev libid3tag0 libid3tag0-dev fusesmb fuse-utils fuse-convmvfs gettext gcc makedev makedepend make libmad0 libmad0-dev madplay*[/COLOR]
```The next package you need is libmtp 1.0.1.
Please dont use the repositories, but compile it yourself!

Download libmtp from [http://libmtp.sourceforge.net/download.php](http://libmtp.sourceforge.net/download.php)
Unzip the archive and cd to the folder you just unzipped to.

Next, you compile using

```
[COLOR=#ff0000]*./configure*[/COLOR]

[COLOR=#ff0000]*make*[/COLOR]

[COLOR=#ff0000]*sudo make install*[/COLOR]

```Now please connect your Zen to your computer, but as soon as the mount dialog appears unmount it. But leave it connected to your computer.

Use ```
[COLOR=Red]sudo mtp-detect[/COLOR]
``` and control whether your zen is recognized or not.

[COLOR=Black]If theres a list of information concerning your Zen and at the bottom of the page there's an "okay", then everything's fine.

Now, next you'll need the package mtpfs 0.9.
You can download it here: [/COLOR][http://www.adebenham.com/mtpfs/](http://www.adebenham.com/mtpfs/)

Unzip the archive and cd to the folder you just unzipped to.

Next, you compile using

```
[COLOR=#ff0000]*./configure*[/COLOR]
 
 [COLOR=#ff0000]*make*[/COLOR]
 
 [COLOR=#ff0000]*sudo make install*[/COLOR]
 
```That's it with compiling.

  What you're going to do next is to add a line to  /etc/ld.so.conf

```
[COLOR=#ff0000]*sudo gedit /etc/ld.so.conf*[/COLOR]
```Add the following line to the bottom

```
[COLOR=#ff0000]*include /usr/local/lib*[/COLOR]
```Next type to console

```
[COLOR=#ff0000]*sudo ldconfig*[/COLOR]
```Now we're getting to the end..

Create a mount point typing

```
[COLOR=#ff0000]*sudo mkdir /media/zen*[/COLOR]
``` (the mount point's name is up to you)

Mount it

```
[COLOR=#ff0000]*sudo mtpfs -o allow_other /media/zen*[/COLOR]
```After a short while there should a appear an icon for removable data on your desktop.
That's it. Your Zen should work perfectly fine now.

When finished transferring files you can unmount your Zen using

```
[COLOR=#ff0000]*sudo umount /media/zen*[/COLOR]
```__________________________________

Alright, that's it.
I hope you can read it without getting a headache.

Just registered only for translating this, but I was so glad when getting my Zen to run a month ago, that I had to share this.

---

### Post by Xjjulix on 2009-12-09
Just one question; when you say do a cleanup in failsafe mode, is the cleanup in the actual instructions? And...er...what's failsafe mode?
Sorry for being so newbie-ish. My knowledge of ubuntu is zip.

---

### Post by Kaffeekranz on 2009-12-09
Im talking about your Zen here, I'm sorry about the misunderstanding.
The cleanup's in the instructions, but failsafe mode wasn't quite the right word.
There's this little hole at the side of your player.. if you put something sharp like a needle in there while powering up your device, you're getting, after booting, the choice to either do a cleanup, a reformat, a normal boot, or a firmware reload.
There you should choose to do a cleanup and you're good to go.

---

### Post by eddier on 2010-01-03
Damn everything went fine until here

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for FUSE... configure: error: Package requirements (fuse >= 2.2                         glib-2.0 >= 2.6                         gthread-2.0 >= 1.2                         mad >= 0.15                         id3tag >= 0.15                         libmtp >= 0.0.9) were not met:

No package 'fuse' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables FUSE_CFLAGS
and FUSE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Not being a code junkie i,m stumped?

eddie

---

### Post by GalloGlas on 2010-01-03
> **eddier said:**
> Damn everything went fine until here

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for FUSE... configure: error: Package requirements (fuse >= 2.2                         glib-2.0 >= 2.6                         gthread-2.0 >= 1.2                         mad >= 0.15                         id3tag >= 0.15                         libmtp >= 0.0.9) were not met:

No package 'fuse' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables FUSE_CFLAGS
and FUSE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Not being a code junkie i,m stumped?

eddie

```
 sudo apt-get install fuse-utils 
```

---

### Post by eddier on 2010-01-03
Thanks but allready done-

```
sudo apt-get install libnjb5 libnjb-dev libid3tag0 libid3tag0-dev fusesmb fuse-utils fuse-convmvfs gettext gcc makedev makedepend make libmad0 libmad0-dev madplay
```

eddie

---

### Post by GalloGlas on 2010-01-04
I missed that line in his post.  Looks like he has you going through the rear to get to the belly button.  Hardcore Linux users love their terminal.  Can it be done that way?  sure.  But there are easier ways to start with.

I'd attempt to completely start over.  Remove the junk.  

Install Gnomad2 and libfuse2 from the package manager.  It should install all of its dependencies.   Thats all I had to do to make mine work.

---

### Post by labinnsw on 2010-11-13
> **Kaffeekranz said:**
> Use ```
[COLOR=Red]sudo mtp-detect[/COLOR]
``` and control whether your zen is recognized or not.

If theres a list of information concerning your Zen and at the bottom of the page there's an "okay", then everything's fine.

If everything is not fine? ```
labinnsw@UbuntuLTS-desktop:~$ sudo mtp-detect
[sudo] password for labinnsw: 
libmtp version: 1.0.1

Listing raw device(s)
   No raw devices found.
labinnsw@UbuntuLTS-desktop:~$ 

```

---

