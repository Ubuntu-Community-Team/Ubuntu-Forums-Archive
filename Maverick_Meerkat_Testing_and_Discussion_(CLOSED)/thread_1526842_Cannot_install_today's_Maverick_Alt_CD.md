---
title: "Cannot install today's Maverick Alt CD"
date: 2010-07-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-07-08
I was having several problems with my regularly updated Maverick Alpha test installation, so I decided to do a full reinstall. I downloaded the daily alternate CD image and verified the checksum. I reformatted my Maverick partition and started the installation.

The Base Installation ran up to about 80%, then failed with:

```

Unable to install the selected kernel

An error was encountered while trying to install the kernel into the target system.

Kernel package: 'linux-generic'

Check /var/log/syslog or see virtual console 4 for the details.

```Here is what I found in the syslog:

```

The following packages have unmet dependencies: linux-headers-generic: Depends: linux-headers-2.6.35-7-generic but it is not installable

```

Also, I reattempted the fresh install and the exact same thing happened, again.

Has anyone else seen this on a fresh install? Should I report a bug or just wait until tomorrow and try, again?

Thanks,
Tim

---

### Post by ratcheer on 2010-07-08
I'm going to try the Live CD - its been so long since I've tried a Live.

Tim

---

### Post by forumache on 2010-07-08
> **ratcheer said:**
> 
```

The following packages have unmet dependencies: linux-headers-generic: Depends: linux-headers-2.6.35-7-generic but it is not installable

```

Also, I reattempted the fresh install and the exact same thing happened, again.

Has anyone else seen this on a fresh install? Should I report a bug or just wait until tomorrow and try, again?

Thanks,
Tim

Wait until tomorrow. I had a similar problem when I updated today over the net (update-manager -d): Could not calculate the upgrade, something with linux generic 2.6.35.7

I waited a few hours, tried again and it worked, I'm now on Maverick.

---

### Post by ratcheer on 2010-07-08
The Live CD installation worked, but it took a *very* long time. It installed 2.6.35-6, though. I think the image was last updated yesterday (7/7 AM).

Also, the reinstall seems to have fixed all the little problems that had been creeping in to my former installation.

Tim

---

### Post by VMC on 2010-07-08
> **ratcheer said:**
> The Live CD installation worked, but it took a *very* long time. It installed 2.6.35-6, though. I think the image was last updated yesterday (7/7 AM).

Also, the reinstall seems to have fixed all the little problems that had been creeping in to my former installation.

Tim

Interesting. I had very similar experience with daily-live a week or so ago. The kernel then caused kernel panic. Once I saw the kernel move to a new release everything went smoothly.

---

