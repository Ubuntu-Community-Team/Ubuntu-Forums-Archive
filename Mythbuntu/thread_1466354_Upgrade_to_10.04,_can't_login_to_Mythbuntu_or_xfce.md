---
title: "Upgrade to 10.04, can't login to Mythbuntu or xfce, but can login to Gnome"
date: 2010-04-30
forum: Mythbuntu
---

### Post by Kurtosis on 2010-04-30
Hi all, Linux noob, have a problem:

I just ran the updater on my Mythbuntu 9.10 box to install all the new software in the list, including the new kernel.  I ran the normal update, not the special 'Upgrade to 10.04' option that only appears when new distro versions are released.

I restarted, and found I can't login to Mythbuntu or xfce sessions anymore, I just get returned to the login prompt.  However, I can login to xterm and Gnome sessions (the latter of which I'm posting from).

Any suggesions how to fix this?

Thanks!

---

### Post by superm1 on 2010-04-30
> **Kurtosis said:**
> Hi all, Linux noob, have a problem:

I just ran the updater on my Mythbuntu 9.10 box to install all the new software in the list, including the new kernel.  I ran the normal update, not the special 'Upgrade to 10.04' option that only appears when new distro versions are released.

I restarted, and found I can't login to Mythbuntu or xfce sessions anymore, I just get returned to the login prompt.  However, I can login to xterm and Gnome sessions (the latter of which I'm posting from).

Any suggesions how to fix this?

Thanks!
What do you mean the 'normal update'?  The regular upgrade to 10.04 is the safe route.

I'm suspecting (and scared) you might have just replaced your sources with lucid sources and ran dist-upgrade, which could have potentially disastrous results.  If you did, you will need to check and see if 'mythbuntu-desktop' is still installed.  If it's not, you'll need to install that to fix your system now.

---

### Post by Kurtosis on 2010-04-30
> **superm1 said:**
> What do you mean the 'normal update'?  The regular upgrade to 10.04 is the safe route.
Thanks super.  You know how in the Update Manager, there is the option at the top:

"New Ubuntu release '10.04 LTS' is available"  [Upgrade]

And then below that is the list of individual packages with the [Check] and [Install Updates] buttons beneath?

Well first I tried running the new release upgrade at the top, but got an error that it could not calculate the upgrade, and the upgrade was cancelled.

So then I tried the [Install Updates] below, which worked, but left me with this login problem.

> **superm1 said:**
> I'm suspecting (and scared) you might have just replaced your sources with lucid sources and ran dist-upgrade, which could have potentially disastrous results.  If you did, you will need to check and see if 'mythbuntu-desktop' is still installed.  If it's not, you'll need to install that to fix your system now.
Ok, what's the best way to check if mythbuntu-desktop is still installed, and to install it if not?  Synaptic?

---

### Post by Michael3007 on 2010-05-06
Hi Kurtosis,

have you fixed your issue in the meantime? I am facing the same problem since I have performed the update from Mythbuntu 10.4 RC to Final.

Auto-Login and MythTV are not working any more.  I have to enter my password but I cannot login to Mythbuntu / XFCE sessions anymore, I just get  returned to the login prompt (same as you).

What do I have to do to login to xterm? I can't see any boot options...

Thanks for your help, regards,

Michael

---

### Post by chipppy on 2010-05-07
ood Morning

I dont know if this helps but I have run into a similar problem on my Ubuntu desktop.  I did a normal update (not upgrade) of my Ubuntu 9.10 desktop and now WiNE kicks me out to the login screen and then I just circle the login screen after each login attempt.  
If this is similar it might point towards a fundermental problem (core applications or kernel) more then a specific Myth problem.

Cheers
chipppy

---

