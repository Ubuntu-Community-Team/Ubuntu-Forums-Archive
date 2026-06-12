---
title: "Natty Beta live install error"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mjpatey on 2011-04-05
Hi, all-

I'm trying to install Ubuntu 11.04 Beta from a live session running from a USB stick.  The live session is running beautifully, in absolutely every respect (posting this question from it, it fact).  I started the installation process, got through the partitioner, created a user, files were being copied and downloaded, and then this:

> An error occurred while installing packages:

E:Sub-process /usr/bin/dpkg returned an error code (1)

The following packages are in a broken state:



This may be due to using an old installer image, or it may be due to a bug in some of the packages listed above. More details may be found in /var/log/syslog. The installer will try to continue anyway, but may fail at a later point, and will not be able to install or remove other packages (possibly including itself) from the installed system. You should first look for newer versions of your installer image, or failing that report the problem to your distributor....it didn't actually list the packages that were broken.  The recommendation it gives at the end is to check for a new version of the installer image, but I believe there's only been one release of the beta.

When I attempt to continue and reboot, no OS is installed and I'm faced with a black screen.

Any ideas how to fix this?  Thanks in advance for any light you can shed!

-Mark

---

### Post by howefield on 2011-04-05
Thread moved to "*Natty Narwhal Testing and Discussion*"

You are more likely to get appropriate help here.

---

### Post by mjpatey on 2011-04-05
Thanks, howefield!  I looked for such a forum but didn't see it.

---

### Post by r-senior on 2011-04-05
I've just had the same problem. Try again, and install from the first screen, don't go into the live session. I also thought it prudent not to download updates during the install on the basis that the less it has to do the better.

It installed the second time, I ran updates, rebooted and it seems OK.

I don't know which part of the "solution" helped.

---

### Post by mjpatey on 2011-04-05
Will try that.  Thanks!

---

### Post by mjpatey on 2011-04-05
Worked!  Posting from the new installation now.  Thanks for the suggestion, r-senior!

---

### Post by ZordidMuc on 2011-04-09
Your hint did not work for me. I have the same problem, the same error message - in German.

I did try to re-install right from the first screen, without entering the live session first. But again, same stupid message without any packages affected.

What I am supposed to do??
Please fix this error before launch of Natty!

---

### Post by mjpatey on 2011-04-09
ZordidMuc-

I believe work is continuing on the release, as I've read of several updates and enhancements, but I assume you'll have to build from source to try it.  I'm not sure what caused the error, but for some reason, choosing to install right away instead of starting a live session first (and choosing not to download updates or the codec package) worked for me.

Also, it may be helpful to note that I was not connected to a network at all during installation.  After reboot, it detected my wireless network and all was well.

Good luck!

-Mark

---

### Post by teachop on 2011-04-09
This error has happened for every Beta1 install I have tried, and in all cases if I redo, as was mentioned above, with the checkboxes unchecked about updates and 3rd party software, it works.  Then the updates can be done later.  I wonder if some people just give up at that point, would be too bad...

---

