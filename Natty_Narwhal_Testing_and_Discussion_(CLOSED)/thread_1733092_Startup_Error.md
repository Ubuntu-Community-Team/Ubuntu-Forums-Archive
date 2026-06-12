---
title: "Startup Error"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MAFoElffen on 2011-04-18
After recent updates, I now get this error on startup, after grub, while loading Ubuntu 11.04beta2:  "cannot read file /etc/udev/rules.d/z80_user.rules"

z80_user.rules?  Really?  Z80?  This is a joke right?

Everything starts up just fine,  Just reading through logs and  tracking things down strays.

There is a file there with that name.  O bytes in size.  Properties says its a link to a text document... but it goes nowhere.

ANYONE-  Is this "anything?" Just an orphan from somewhere or something that got left over from updates or changes in code? It doesn't appear to be causing any problem except the read error on startup.

---

### Post by dino99 on 2011-04-19
from README:
The files in this directory are read by udev(7) and used when events
are performed by the kernel.  The udev daemon watches this directory
with inotify so that changes to these files are automatically picked
up, for this reason they must be files and not symlinks to another
location as in the case in Debian.

Packages do not generally install rules here, this directory is for
local rules.  If you want to override behaviour of package-supplied
rules, which can be found in /lib/udev/rules.d, you can do one of
two things:

 1) Write your own rules in this directory that assign the name,
    symlinks, permissions, etc. that you want.  Pick a number higher
    than the rules you want to override, and yours will be used.

 2) Copy the file from /lib/udev/rules.d and edit it here; you
    should generally only do this if you want to prevent a program
    from being run.


If the ordering of files in this directory are not important to you,
it's recommended that you simply name your files "descriptive-name.rules"
such that they are processed AFTER all numbered rules in both this
directory and /lib/udev/rules.d and thus override anything set there.

My z80-user.rules has not been read/used since 2010 jun 27th and point to a bug url.

So this is some old stuff and your system need some cleaning: use gconf-cleaner & bleachbit (as root but with care when using a setting)

---

### Post by MAFoElffen on 2011-04-19
> **dino99 said:**
> 
So this is some **[COLOR=SeaGreen]old stuff[/COLOR]** and your system need some cleaning: use gconf-cleaner & bleachbit (as root but with care when using a setting)
Thank you Dino99... I read that Readme in the directory.  I could easily clean this up on "my" box.  That is not my concern here. This is close to distribution...

My concern here is that this particular test install started out as a "*clean*" fresh install of Server Beta1 4 days ago (April 14th, after I had frag'ed it in a test, hours before beta2 was released.  There is a minimal amount of extra application's and packages installed. I think I can count less than 10 "extra" main apps if I included the main server services on this box...  Some hardware utility packages, network load and accounting packages, a network analyser package and the 3 main -desktop packages.  

That's the "*why*" it should have been somewhat easy to do accounting for/on this box...  And why anything on it, should have been in use, not extraneous.   So this sounds like a dummy fragment from something given to root, that was installed during the original install (on this box) that may come back to haunt us as an error.

Basic Simplistic Translation-- This error may have came from the install CD or from the original install/update process during the install, based on the options I selected or the packages I installed just after the install to recreate my test platform... It may have been from a stray beta1 process, that may have already been cleaned up in beta2... or not.

I guess what I need to do is to recreate my test platform again on a current snapshot of the Server Beta2 LiveCD ISO... Install again and make sure this error does not get recreated...  

If it does get recreated, **then** there is a problem somewhere.

---

