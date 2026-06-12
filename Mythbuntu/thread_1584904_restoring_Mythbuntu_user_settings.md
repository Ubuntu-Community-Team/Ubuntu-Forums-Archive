---
title: "restoring Mythbuntu user settings"
date: 2010-09-29
forum: Mythbuntu
---

### Post by iaindb on 2010-09-29
Hi,

I've had myth running on different distributions before and I just installed mythbuntu a few days ago to try it out on an old gentoo laptop.  (Works great by the way!)

I was playing around with the xfce settings and X crashed after trying a few window manager decorations.  The only way to log in again was to delete my home directory.

Now however I have the more typical xfce setup with icons, task bars, etc, and I want to get back to the "as installed" mythbuntu layout.

How do I do that without manually changing the background and other settings?  I can blow away the home directory again if necessary.

thanks :)

---

### Post by LowSky on 2010-09-30
if you set up your harddrive to have a seperate /home partition. I would tell you just to reinstall mythbuntu and all will be ok.

If you dont want to do such an extreme thing you can go into synaptic and reinstall the mythbuntu-desktop package.

```
sudo apt-get install mythbuntu-desktop
```

---

### Post by iaindb on 2010-10-03
> **LowSky said:**
> if you set up your harddrive to have a seperate /home partition. I would tell you just to reinstall mythbuntu and all will be ok.
That would be the easy approach, but then I wouldn't learn anything ;)  And I would loose all my myth settings.

>  If you dont want to do such an extreme thing you can go into synaptic and reinstall the mythbuntu-desktop package.I tried that, I had to add the --force option because it told me it was already installed!  After reinstalling, there was no change to my home directory, so it didn't produce the desired result :(

Any ideas?  thanks,
Iain.

---

