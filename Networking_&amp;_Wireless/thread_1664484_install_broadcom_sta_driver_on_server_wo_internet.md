---
title: "install broadcom sta driver on server w/o internet"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by stevepoppers on 2011-01-11
I'm starting to build Ubuntu from the server install and I need to start with gaining internet access without the atrocious inconvenience of stringing a cord across the room more than a foot off the ground. I tend to play around and do a lot of reinstalls, so it really is quite annoying. It sure would be nice to have the driver on the disc and know how to just...make it happen. I've been searching for a few hours and I keep running back around to the Ubuntu documentation pages which really aren't very clear. I guess first problem is that I can't even figure out how to mount the CD in the server environment. Never tried before. O.o Usually just plug it in, but as I said...

Edits:

Ok, accessed CD with ```
sudo mount /dev/cdrom /media/cdrom
```Seems so obvious now. Am currently trying to follow instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access"). 1-11-11 2:14am EST

I have been defeated within the hour. At the first dpkg command, I am met with dependency problems I seem incapable of resolving. They almost seem to be circular. Like a package depends on itself. Fwiw, it involves gcc. Any takers? 1-11-11 2:58am EST

Ok, uncommented the server CD in /etc/apt/sources.list and removed the -server from the name so it matches the full desktop CD I put in. I can install stuff but still do not know how to install/activate the driver from only the terminal. 1-11-11 3:29am EST

My system has informed me to use apt-cdrom to add CDs as repositories, which is mighty convenient as far as that's concerned. However, I still cannot install any of the driver software. Quitting for the night. 1-11-11 4:04am EST

---

