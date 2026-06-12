---
title: "No Avidemux in 11.10 ??"
date: 2011-10-16
forum: Multimedia Software
---

### Post by Sharpie1 on 2011-10-16
Avidemux seems to have been deleted from the Software repository. WTH ? One of the best bits of software I had.. might have to downgrade to get it back..

Sharpie1

---

### Post by arashiko28 on 2011-10-16
This is bad!!! I hadn't realized, but I do need it!

---

### Post by mc4man on 2011-10-16
They were unable to get  package builds done. With a x264 patch a 32 bit package build would of worked but 64 bit package builds would continue to fail

If self built then there is no issue on either 32 or 64 bit - 
thread on, includes a link to open bug & patch for 2.5 source, the 2.6 source needs no patching
[http://ubuntuforums.org/showthread.php?p=11303344](http://ubuntuforums.org/showthread.php?p=11303344)

---

### Post by mc4man on 2011-10-17
There will be new avidemux packages shortly, being built for 12.04 tomorrow & then shortly afterwards for 11.10

---

### Post by gatewayasteroid on 2011-10-18
> **mc4man said:**
> There will be new avidemux packages shortly, being built for 12.04 tomorrow & then shortly afterwards for 11.10

Here's how to have a working avidemux in 2 minutes:

```
sudo gedit /etc/apt/sources.list
```

Add this line at the end:

***deb [http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu](http://ppa.launchpad.net/n-muench/programs-ppa/ubuntu) oneiric main ***

Then fire up the terminal and type:

```
sudo apt-get update
sudo apt-get install avidemux
```

Hope this helps

---

### Post by Sharpie1 on 2011-10-18
> **gatewayasteroid said:**
> Here's how to have a working avidemux in 2 minutes
Thanks a million.. works great, but FYI.. had to do "unauthenticated" install...
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6804EA8EAE0D85C

Sharpie1

---

### Post by gatewayasteroid on 2011-10-19
> **Sharpie1 said:**
> Thanks a million.. works great, but FYI.. had to do "unauthenticated" install...
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6804EA8EAE0D85C

Sharpie1

Glad it worked.
It's easy to do what you need. Remove the line you added (or comment it out) and type in the terminal:

```
sudo add-apt-repository ppa:n-muench/programs-ppa
sudo apt-get update
```

---

### Post by Sharpie1 on 2011-10-20
Thanks, +Kudos !

Sharpie1

---

### Post by gatewayasteroid on 2011-10-20
> **Sharpie1 said:**
> Thanks, +Kudos !

Sharpie1

:) Mark the thread as solved if you can :)

---

### Post by BCtom on 2011-10-22
Thank you - Saved my butt. Avidemux is by far the best tool I use for editing and transcoding HD/super sized video files with Ubuntu. I was in shock after the upgrade and it wasn't there. 

Thank you for the quick fix!

---

### Post by benplanet on 2011-10-22
life saver! thanks for compiling that for us! :popcorn:

---

