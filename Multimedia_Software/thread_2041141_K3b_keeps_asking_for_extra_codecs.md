---
title: "K3b keeps asking for extra codecs"
date: 2012-08-11
forum: Multimedia Software
---

### Post by Stonecold1995 on 2012-08-11
Every time I start up K3b, a message in the task bar pops up telling me that functionality can be improved if I install mp3 codecs.  If I agree and try to install the codecs, it says it installs, but as soon as I close K3b and restart it, I get the message again.  Plus, I don't see why K3b would need mp3 codecs anyways...  And mp3 codecs are already installed anyways.

[IMG]http://www.pictureshack.us/images/95533_k3b.png[/IMG]
[IMG]http://www.pictureshack.us/images/15839_k3b2.png[/IMG]

**How can I get K3b to shut up?  It's quite annoying...  Is anyone else having this issue?**

---

### Post by 2F4U on 2012-08-12
Have you already tried to install the package kubuntu-restricted-extras? This article suggests that it works only when installed from a terminal.

[http://ubuntuguide.org/wiki/Kubuntu_Precise_Restricted_Extras](http://ubuntuguide.org/wiki/Kubuntu_Precise_Restricted_Extras)

---

### Post by Stonecold1995 on 2012-08-12
> **2F4U said:**
> Have you already tried to install the package kubuntu-restricted-extras? This article suggests that it works only when installed from a terminal.

[http://ubuntuguide.org/wiki/Kubuntu_Precise_Restricted_Extras](http://ubuntuguide.org/wiki/Kubuntu_Precise_Restricted_Extras)

Yes, I installed that when I first began using Kubuntu.  As far as I know, I've installed all proprietary formats that I need (including everything in the kubuntu-restricted-extras package).  And no other programs complain about missing formats except for K3b.  I doubt it is a problem for DVD burning/ripping software in general, because Alcohol 120% and DVDFab both work perfectly (although those run through Wine).

---

### Post by ron999 on 2012-08-12
> **Stonecold1995 said:**
> How can I get K3b to shut up?
Hi
Install the codecs for k3b like this:-
```
sudo apt-get install libk3b6-extracodecs lame flac
```

---

### Post by Stonecold1995 on 2012-08-12
> **ron999 said:**
> Hi
Install the codecs for k3b like this:-
```
sudo apt-get install libk3b6-extracodecs lame flac
```

This is the output:

```
alex@kubuntu:~$ sudo apt-get install libk3b6-extracodecs lame flac
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flac is already the newest version.
libk3b6-extracodecs is already the newest version.
lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So yeah, they are already installed.  That's why I'm so confused... :confused:

---

### Post by cottfcfan on 2012-08-12
This is a bug.
Next time it comes up, tick the box, not to ask again, and that will be the last you see of it.

---

### Post by Stonecold1995 on 2012-08-12
I don't see where the "do not show again" box is.  All I see is install and cancel.

---

### Post by cottfcfan on 2012-08-13
Not sure, because I can't repeat it now.
But when the box 1st showed I needed extra codecs, there was also a box to say "don't ask again" or something similar, I ticked the box and that was the end of the problem.

---

### Post by rotave on 2012-08-13
To turn off the notification go to System Settings > Application and System Notifications > Other Notifications > Restricted Codec Availability

---

### Post by oldos2er on 2012-08-13
Thanks, this was bothering me too.

---

### Post by Stonecold1995 on 2012-08-13
> **rotave said:**
> To turn off the notification go to System Settings > Application and System Notifications > Other Notifications > Restricted Codec Availability

Thank you!  This worked.

---

