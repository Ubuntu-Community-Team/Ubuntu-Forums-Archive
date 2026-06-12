---
title: "problem encountered in terminal when trying to install flash player plugin"
date: 2009-01-05
forum: Multimedia Software
---

### Post by tswann on 2009-01-05
Hi guys

I've come up against a problem trying to install Flash Player pluggin.  I downloaded it through the synaptic manager and then did the following:

I typed " sudo apt-get install flashplugin-nonfree " into the terminal, typed in my password and then the following message came up:

" E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? "

I then tried the same text but without 'sudo' at the start, was not asked for a password, and this came up:

" E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? "

If anyone has any pointers on how I can solve this problem and get the adobe flash player then I would of course be very grateful.

I look forward to hearing back.

Yours,

Thomas

---

### Post by amauk on 2009-01-05
this usually happens when you have another instance of a package manager running

make sure synaptic isn't open

---

