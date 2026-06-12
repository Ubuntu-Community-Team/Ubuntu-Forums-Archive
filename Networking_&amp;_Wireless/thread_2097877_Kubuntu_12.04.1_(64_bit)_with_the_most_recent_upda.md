---
title: "Kubuntu 12.04.1 (64 bit) with the most recent updates on a HP Pavilion DV7-6135dx"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by stevewilson on 2012-12-24
My apologies if this has already been asked or addressed, but I really DID look - both here and on the web in general.

I'm running Kubuntu 12.04.1 (64 bit) with the most recent updates on a HP Pavilion DV7-6135dx laptop.  It runs absolutely great.  Video/audio/USB and wireless are all great, but EVERY TIME I put the laptop to sleep, wireless is gone as soon as it resumes.I've tried everything I could think of (or read about) and nothing seems to change it.  I'vd tried:

1.  Creating a file called 'config' in the /etc/pm/config.d directory and putting the line 'SUSPEND_MODULES="iwlwifi"' in it.

2.  Creating a file called 'unload_modules' in the /etc/pm/config.d directory and putting the line 'SUSPEND_MODULES="$SUSPEND_MODULES iwlwifi"' in it.

3. Doing a sudo /etc/init.d/networking restart .

4. Turning off and then on the wireless switch on the laptop, and

5.  Logging off and then back on after sleep.

Nothing - and I'm out of ideas.  If anyone could help, I'd be very appreciative.

Thanks in advance

Steve

---

