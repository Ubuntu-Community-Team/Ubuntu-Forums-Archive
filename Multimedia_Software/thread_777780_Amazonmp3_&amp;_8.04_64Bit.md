---
title: "Amazonmp3 &amp; 8.04 64Bit"
date: 2008-05-01
forum: Multimedia Software
---

### Post by bensode on 2008-05-01
Just did a fresh installation of 8.04 64bit Desktop edition going smoothly so far.  I was able to install ia32-libs, getlibs and Amazonmp3 normally.  Problem I am having is when I start the Amazonmp3 downloader with a download from Amazon I get a message that the downloader couldn't reach the internet.  I verified that there was no proxy setting getting in the way and even installed the Amazonmp3 downloader inside of a virtual machine running on this machine with a NAT connection.  I'm wondering if this is an 8.04 thing or one of the libs from getlibs that is the problem.  Internet connectivity is not the issue, though.

---

### Post by Cappy on 2008-05-03
[http://ubuntuforums.org/showthread.php?t=763576](http://ubuntuforums.org/showthread.php?t=763576)

---

### Post by BFris on 2008-05-29
Cappy, your link is quite useful. I had to follow that one and a few more to figure out how to do it just right. Here is the condensed version.

You need to disable ipv6 networking. To do this, you need to add these lines to your /etc/modules.d/blacklist file:
```
blacklist ipv6
```
Then you have to reboot. There must be a way to manually unload the necessary module, but I couldn't figure out how to do it.

Here are some of the links I followed to figure it all out:

[http://ubuntuforums.org/showthread.php?t=763576]("http://ubuntuforums.org/showthread.php?t=763576")

[http://ubuntuforums.org/showthread.php?t=772396&highlight=flock]("http://ubuntuforums.org/showthread.php?t=772396&highlight=flock")

[http://ubuntuforums.org/showthread.php?t=674401]("http://ubuntuforums.org/showthread.php?t=674401")

---

