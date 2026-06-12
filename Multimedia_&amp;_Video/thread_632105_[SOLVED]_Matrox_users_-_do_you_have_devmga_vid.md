---
title: "[SOLVED] Matrox users - do you have /dev/mga_vid?"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by kko1 on 2007-12-05
Hello.

In Dapper, which I've been using for a while, I don't have /dev/mga_vid for Matrox graphics, so I'm unable to use *mga* or *xmga* output with *mplayer*. If I understood the mplayer documentation right, this is because this only works with 2.4 series kernels. (See [http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#mga_vid](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#mga_vid) )

With 2.6 kernels, there's supposedly a *Work-In-Progress* project to re-implement this Matrox framebuffer implementation, but it apparently requires self-compiling the mga_vid.o kernel module, *unless it's already done and integrated with newer kernels / ubuntu distributions.*

So, is it?

kko1

PS. If it isn't, any tips on how to compile the said module (or ways to obtain a suitable one pre-compiled for Dapper) will be appreciated. I've compiled stuff before, but the project "page" (referenced in the documentation) wasn't exactly plentiful when it comes to detailing the requirements for getting the compile done...

---

### Post by clubsoda on 2007-12-07
Not sure if this helps, but anyway:-
[http://matrox.tuxx-home.at/viewtopic.php?p=1928](http://matrox.tuxx-home.at/viewtopic.php?p=1928)

A quick search at [http://packages.ubuntu.com](http://packages.ubuntu.com) doesn't turn up any package containing the mga_vid file.

---

### Post by kko1 on 2007-12-07
Thanks, clubsoda.

I've been to the matrox forums, but had missed that thread. I'll have to read it through with some thought. If nothing else, it will hopefully help me better understand the inner workings of hardware acceleration on Matrox cards. (I happen to have a *G450*, exactly as in that thread.)

Incidentally, [http://packages.ubuntu.com/](http://packages.ubuntu.com/) had crossed my mind, but I didn't do a search then. You're right, *mga_vid* wasn't to be found.
**EDIT: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) is buggy.** If you search for "mga_vid" in package descriptions, it doesn't find the packages, but they are there. I suspect it's because of the underscore. A search for "mga" works.

*

**EDIT2: I now have a working */dev/mga_vid.*** Too bad it won't work on the secondary head, which would be why I started investigating this in the first place...

Anyhow, your link pointed me to the right directions. Thanks for the help. :)

I'll post below what's needed to get it working (for the primary head).

kko1

---

### Post by kko1 on 2007-12-07
*Matrox* & *mplayer mga/xmga* output **MINI-HOWTO**.

Works at least on *Dapper*, and probably *Edgy*, at least with a *Matrox G450* card. Unfortunately only for the primary head.

Can probably be adapted (with appropriate packages, possibly working directly from the repositories) for *Feisty* and *Gutsy*.

*

*Step 0, preparations:*

To get */dev/mga_vid* and thus *mplayer*'s *-vo mga* and *-vo xmga* options working, you need to install and compile the mga_vid.ko separately.

To be able to do this, you need to have at least the following installed:
```
build-essential
debhelper
module-assistant
```

Not sure whether you need these, since we're not following the README. (I had these installed.) Try first without, and if it doesn't work, add these:
```
fakeroot
kernel-package
```

*

*Step 1:*
Install *mga-vid-common*.

"It contains some configuration files for devfs and modutils so that the module gets loaded automatically on demand and so that the device node will be created with proper permissions (if you're using devfs)."

(See */etc/devfs/conf.d/mga-vid-common* and */etc/modutils/mga-vid-common* after installing the package, if you want the details.)

It also contains the test program *mga_vid_test*.

```
sudo apt-get install mga-vid-common
```

*Step 2:*
Do *not* install *mga-vid-source* from the repositories. It does not work on *dapper* or *edgy*. It is (reportedly) fixed in *feisty*, but I can't guarantee this.

Instead, get a newer package and install it.
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/m/mga-vid/mga-vid-source_1.55-1.2_i386.deb
sudo dpgk -i mga-vid-source_1.55-1.2_i386.deb
cd /usr/src
sudo tar xzf mga-vid.tar.gz
```

(See [http://mirrors.kernel.org/ubuntu/pool/universe/m/mga-vid/](http://mirrors.kernel.org/ubuntu/pool/universe/m/mga-vid/) for packages for other architectures, or if you otherwise need an other version.)

*Step 3:*
In the previous step we will have installed a *source* package (*.tar.gz*) with documentation, and expanded the *.tar.gz*. As mentioned, we will *not* be following the README from this package.

Instead, we will use the *module-assistant* to compile and install it. It will create a *.deb* package customised for the kernel you are using, and install it. Now, remember, we have previously switched to */usr/src*. Just to make sure, be there when executing these commands.
```
sudo module-assistant update,prepare
sudo module-assistant auto-install mga-vid
sudo depmod -a
```

*Step 4:*
Test it.
```
sudo modprobe mga_vid
tail /var/log/syslog

```

**That's it!**

*

Thanks to:
- IntuitiveNipple at [http://matrox.tuxx-home.at/viewtopic.php?p=1928](http://matrox.tuxx-home.at/viewtopic.php?p=1928) for a very clear explanation of "YUV video interface for accelerated video playback", and of other things.
- Tim Miller Dyck at [https://bugs.launchpad.net/ubuntu/+source/mga-vid/+bug/64632](https://bugs.launchpad.net/ubuntu/+source/mga-vid/+bug/64632) for outlining the workaround employed here.
- mplayer documentation team at [http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#mga_vid](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#mga_vid) for guidance.
- those who created mga_vid.
- clubsoda above, for pointing me to the right direction.
- the good folks at [http://matrox.tuxx-home.at/](http://matrox.tuxx-home.at/) for general Matrox information. ;)

*

kko1

---

### Post by clubsoda on 2007-12-08
Wow, excellent follow-up post!

Thanks for the warning about [http://packages.ubuntu.com](http://packages.ubuntu.com) too; I had been relying on that flaky search engine.  It turns out that in order to find a partial filename with the **Search the contents of packages** tool you have to tick the third option: "packages that contain files or directories *whose names contain the keyword*".  Silly thing, maybe they're trying to save some CPU on regular searches...

---

### Post by kko1 on 2008-07-08
Updated guide for **Hardy**.

Do *not* install *mga-vid-source* from the repositories. It does not work on *hardy* either...

Otherwise, follow the directions for **Dapper**, but replace the filename (version) to *wget* with the following, newer version:

```
wget http://mirrors.kernel.org/ubuntu/pool/universe/m/mga-vid/mga-vid-source_2.6.24-2_i386.deb
```

(The *xmga* output comes in handy when *xv* output gives you an *X11 error: BadAlloc (insufficient resources for operation* :) )

kko1

---

