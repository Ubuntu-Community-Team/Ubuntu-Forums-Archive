---
title: "How do I install MythTv? Broken"
date: 2010-04-03
forum: Mythbuntu
---

### Post by Lucky75 on 2010-04-03
Hey,

I'm running Ubuntu 9.10/Gnome, and I'm trying to install mythtv, but it doesn't seem to work. Any suggestions on how to install it?

Thanks!

```

mythtv:
 Depends: mythtv-frontend but it is not going to be installed
 Depends: mythtv-backend but it is not going to be installed

```

---

### Post by nickrout on 2010-04-03
> **Lucky75 said:**
> Hey,

I'm running Ubuntu 9.10/Gnome, and I'm trying to install mythtv, but it doesn't seem to work. Any suggestions on how to install it?

Thanks!

```

mythtv:
 Depends: mythtv-frontend but it is not going to be installed
 Depends: mythtv-backend but it is not going to be installed

```
```
sudo aptitude install mythbuntu-desktop
```

---

### Post by Lucky75 on 2010-04-03
That still didn't install mythtv, and I still get the same errors.

---

### Post by superm1 on 2010-04-03
Make sure you have universe and multiverse enabled.

If you do and that still happens, try to individually install one of those failing packages.  The error should hopefully be more informative.

---

### Post by Lucky75 on 2010-04-03
Yep, I've traced it down, and it seems to be libvdpau wanting nvidia 185 or something instead of 195. Forcing it just seems to break a whole lot of packages.

---

### Post by superm1 on 2010-04-03
Then you have the nvidia vdpau PPA activated probably.  You need to enable Mythbuntu autobuilds to get a build that works with that ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds))

---

### Post by Lucky75 on 2010-04-04
Aha! Thanks, that got it. What was the difference?

---

### Post by superm1 on 2010-04-04
> **Lucky75 said:**
> Aha! Thanks, that got it. What was the difference?

The way that VDPAU was packaged changed after 9.10 launched.  Both of those repositories have migrated over to the new way to do it for the NVIDIA packages and Myth packages.

---

### Post by Lucky75 on 2010-04-04
Ah, thanks! I've been searching for a solution for a few weeks now. Everyone keeps suggesting that I just force an install or downgrade to 185, neither of which are decent solutions ;)

---

### Post by tlimon on 2012-04-08
> **superm1 said:**
> Then you have the nvidia vdpau PPA activated probably.  You need to enable Mythbuntu autobuilds to get a build that works with that ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds))

Hello,  I'm having an issue with the mythtv-backend being installed.  I chased the dependencies down to the QuickTime libraries. qt 8.0 being called for but 8.1 is installed so the dependencies never are satisfied.  Here's the error:

"libqt4-qt3support:
 Depends: libqt4-designer but it is not going to be installed
  Depends: libqt4-network (=4:4.7.4-0ubuntu8) but 4:4.7.4-0ubuntu8.1 is to be installed
  Depends: libqt4-sql (=4:4.7.4-0ubuntu8) but 4:4.7.4-0ubuntu8.1 is to be installed
  Depends: libqt4-xml (=4:4.7.4-0ubuntu8) but 4:4.7.4-0ubuntu8.1 is to be installed
  Depends: libqtcore4 (=4:4.7.4-0ubuntu8) but 4:4.7.4-0ubuntu8.1 is to be installed
  Depends: libqtgui4 (=4:4.7.4-0ubuntu8) but 4:4.7.4-0ubuntu8.1 is to be installed"


  Can you elaborate on what you mean by the quote above?  enable where?  Thank you for the help. --Tim

---

### Post by nickrout on 2012-04-08
This thread is over 2 years old. Start a new one and tell us more info, like what version of ubunntu you have and what command you ran that produces that result.

---

### Post by tgm4883 on 2012-04-09
> **nickrout said:**
> This thread is over 2 years old. Start a new one and tell us more info, like what version of ubunntu you have and what command you ran that produces that result.

Agreed. Closing thread.

---

