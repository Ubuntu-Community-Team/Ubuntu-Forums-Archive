---
title: "WARNING - System-breaking update on Karmic"
date: 2009-10-15
forum: Mythbuntu
---

### Post by igoddard on 2009-10-15
I've just installed the current updates on 9.10 beta.  Mythtv front end is not compatible with mythtv common and will not install.  If you attempt to install upgrades your front-end will be removed and not replaced.

Don't go there until someone spots it and fixes it.

---

### Post by mythding on 2009-10-15
I think there is something going on because I am still on 9.04 running trunk daily and when I tried to upgrade it told me that I could not upgrade mythfrontend, myth-backend, myth-common, etc... But the rest of myth packages where available to upgrade. I will be patient.

EDIT: it is giving me a partial update message.
EDIT 2: This might be a thread hijack so I posted in the right thread.
[http://ubuntuforums.org/showthread.php?t=1032455&page=16](http://ubuntuforums.org/showthread.php?t=1032455&page=16)

---

### Post by kadafi69 on 2009-10-15
have you upgraded to the 0.22 trunk? as you need that to upgrade to mythbuntu 9.10beta

---

### Post by superm1 on 2009-10-15
> **igoddard said:**
> I've just installed the current updates on 9.10 beta.  Mythtv front end is not compatible with mythtv common and will not install.  If you attempt to install upgrades your front-end will be removed and not replaced.

Don't go there until someone spots it and fixes it.
This is normal behavior as builds trickle through the mirrors.  i386 and amd64 build separately.  i386 provides mythtv-common for both, so if i386 builds later than amd64, you'll run into this situation.

In short, it fixes itself within a couple of hours normally.

---

### Post by igoddard on 2009-10-15
> **kadafi69 said:**
> have you upgraded to the 0.22 trunk? as you need that to upgrade to mythbuntu 9.10beta

I'm not sure whether that question was directed to me or mythding.

In may case this is a Karmic Mythbuntu install from CD so it started off as 0.22 but whether or not a particular file is trunk depends on what's in the repositories at any given time.  Not only does that seem to vary but it's the source of the problem:

apt-get install mythtv-frontend
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  mythtv-frontend: Depends: mythtv-common (= 0.22.0~trunk22413-0ubuntu1) but 0.22.0~zrc1-0ubuntu1 is to be installed
E: Broken packages

---

### Post by igoddard on 2009-10-15
> **superm1 said:**
> This is normal behavior as builds trickle through the mirrors.  i386 and amd64 build separately.  i386 provides mythtv-common for both, so if i386 builds later than amd64, you'll run into this situation.

In short, it fixes itself within a couple of hours normally.

OK, thanks for that.  I'm running 64-bit so it explains it.  I'll try later.  

It's a nuisance for me at the moment because Thursday afternoon is a time when I have the house to myself & I can try to get what works on my monitor to work on the TV but I suppose it can't be helped.

But can I suggest that stuff is built off-line and then released as a whole when it's all done so that the repositories are kept internally consistent?

---

### Post by superm1 on 2009-10-15
Try switching to the main archive mirror on.  Run this tool

```
gksudo software-properties-gtk
```

---

### Post by igoddard on 2009-10-15
Well, the updates have filtered through.

Front-end installed, back-end disappeared but could then be reinstalled OK.  

Plugins had to be reinstalled.

And guess what?  Alsa has gone back to being stupid.  Every reboot it comes up with the front channel turned down to zero.  It really is useful to have Mythbuntu come up automatically on boot without sound!

---

### Post by superm1 on 2009-10-15
> **igoddard said:**
> Well, the updates have filtered through.

Front-end installed, back-end disappeared but could then be reinstalled OK.  

Plugins had to be reinstalled.

And guess what?  Alsa has gone back to being stupid.  Every reboot it comes up with the front channel turned down to zero.  It really is useful to have Mythbuntu come up automatically on boot without sound!
Please file a bug ASAP regarding this:

[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-utils](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-utils)

Freezes are in order, so this needs to be raised.

---

### Post by slamhound on 2009-10-15
The issue of booting with the sound turned down might not be specific to this update.  I had that problem a few weeks ago (not after an update, just happened randomly).  I can't remember the exact solution (and my quick google search didn't immediately come up with the solution) but it had to do with setting the volume levels correctly and then running alsactl store.

---

### Post by superm1 on 2009-10-15
Regardless of what update caused it, if it's still happening with a fully updated current install, there's a bug, and those maintainers need to know.

---

### Post by igoddard on 2009-10-16
The solution seems to be to delete /var/lib/alsa/asound.state, set the controls and then run alsactl store. [Edit - you have to do this as root]

The mixer must be one of the few gui apps that doesn't have a Save option.

---

### Post by igoddard on 2009-10-16
> **superm1 said:**
> Regardless of what update caused it, if it's still happening with a fully updated current install, there's a bug, and those maintainers need to know.

I ran today's updates after saving with alsactl so I don't know if anything downloaded today would have fixed it.

From what I've seen through Googling & looking at what's on the box I think the real problem is deep-seated.  Alsa config files are scattered throughout the file system - /etc, /usr/share & /var/lib that I found.  Some of them have "alsa" as a name root, some have "asound".  This sort of thing is guaranteed to lead to a maintenance nightmare unless there's a unified configuration app.  The mixer could be that app - but the mixer doesn't seem to have any means of saving what it's set.

---

