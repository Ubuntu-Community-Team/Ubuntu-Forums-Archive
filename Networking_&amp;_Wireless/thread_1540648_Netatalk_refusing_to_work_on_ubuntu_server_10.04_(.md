---
title: "Netatalk refusing to work on ubuntu server 10.04 (Lucid) - amd64"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by mauf64 on 2010-07-28
After upgrading from Karmic to Lucid Lynx I was no longer able to have the Netatalk server back on duty,
using the version distributed in repository. BTW, I am running on amd64... and this can make the difference.

I followed all the threads' instruction I found here and there but none seemed to work.

At the end I downloaded the the source ball from sourceforge (v. 2.1.3), cofigure'd with --prefix=/ + make && make install.
The /etc/init.d/netatalk script from the .deb needed some modification and I'm going to attach the patched script here.
Of course you have to run rcconf to have it started at reboot 

Hope this may help somebody!

cheers,
mauf

---

### Post by grim2 on 2011-10-16
Mauf,
I may have a similar problem.  I've got two Ubuntu machines, 1 workstation and 1 server (both 64bit and 11.10), and an iMac (OSX-Lion).  I'm trying to use my Ubuntu server as the TimeMachine share.  All was fine before Lion.

Now, I cannot access the server.  BUT, I have no problem accessing the workstation.  It's making me insane.  I've checked and rechecked versions of netatalk, config files, etc. and they are the same on the server and workstation.  For some reason, I can log into the workstation from the iMac, but the server fails every time.

Ideas?

-g2

---

### Post by mauf64 on 2011-10-17
I'll be stuck on 10.04 as long as LTS expires... just for things like this :(

However when Netatalk changed from V1 to V2 (or something like that) the share format changed and I had to reset all the shares copying the file off the netatalk control, cleaning the MAC's stuff, and reset a brand new share. I wonder if this may be a like situation...

So, you may want to try to (stop all the live shares) setup a new share and put something in, just to test it...

Then try the tar ball to install from source... (64bits is some naughty sometime) 

cheers,
mauf

---

### Post by dmovad on 2011-10-21
I've got 10.04 LTS Server-64 bit running well using this post:

[http://langit.wordpress.com/2011/09/14/share-folder-in-ubuntu-11-04-for-mac-osx-lion/#comment-84](http://langit.wordpress.com/2011/09/14/share-folder-in-ubuntu-11-04-for-mac-osx-lion/#comment-84)

Now, if someone has some insight into why every time I reboot my server I have to restart Netatalk I'd be grateful.  Even better I'd really appreciate a solution.

Thanks...
Dave

---

