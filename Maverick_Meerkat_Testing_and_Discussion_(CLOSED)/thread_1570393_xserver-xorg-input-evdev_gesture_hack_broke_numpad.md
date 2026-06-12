---
title: "xserver-xorg-input-evdev gesture hack broke numpad"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Devport on 2010-09-08
Can anybody with xserver-xorg-input-evdev-1:2.3.2-6ubuntu1 confirm that the Ubuntu gesture hack broke using the numpad for what it is intended to do : Entering numbers ?

I will then go ahead and open a bug for it.

-- This makes me think : Ubuntu devs please go the way the xorg devs suggested - do it in user space instead of hacking on such an essential part of xorg making it overly complicated and buggy --

---

### Post by oubiwann on 2010-09-09
> **Devport said:**
> Can anybody with xserver-xorg-input-evdev-1:2.3.2-6ubuntu1 confirm that the Ubuntu gesture hack broke using the numpad for what it is intended to do : Entering numbers ?

I will then go ahead and open a bug for it.

-- This makes me think : Ubuntu devs please go the way the xorg devs suggested - do it in user space instead of hacking on such an essential part of xorg making it overly complicated and buggy --

I'll have the multi-touch devs take a look at this, and reply to this thread with more info.

Thanks,

d

---

### Post by kosumi68 on 2010-09-09
Devport,

I am running that particular version of evdev together with unity, on a desktop with numpad, experiencing no such problems.

The input configuration files in /usr/share/X11/xorg.conf.d/ may have changed between lucid and maverick. Without further information about your system, I would guess the problem lies there. A bug report would be useful.

---

### Post by Devport on 2010-09-09
I didn't change any configuration file related to xorg configs. Numpad just always stays in the "cursor mode" moving the cursor no matter if Num lock is enabled or not.

I have no idea how to debug this problem at all. Any ideas are welcome.

I posted here since I don't want to open a bug if this is not a common problem.

( My system is up to date maverick - upgraded from lucid weeks ago. The problem appeared just recently, probably one of those many updates )

---

### Post by bregma on 2010-09-09
I have that exact version of evdev installed on my system and the numpad switches between cursor and numeric mode without a hitch.

Does the numlock light toggle as you toggle the numlock key?

Are you using a USB, a PS/2, or a built-in (notebook) keyboard?

There was a major change in x.org between Lucid and Maverick, but the upgrade process will not have adjusted the xorg.conf file since it's a config file.  One simple test you can do is to go to the command line and type the command "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.lucid" then restart.  See if the problem persists.

These checks are a good place to start.  If you could do them and report the results here, we can figure out the next steps to take.

---

### Post by maqifrnswa on 2010-09-10
This might be a dumb answer, excuse me if you've already tried! Have you gone to System -> Preferences -> Keyboard, then the mouse keys tab. Uncheck the box there.  The betas sometimes reset that checkbox which will disable the numpad.

---

### Post by Devport on 2010-09-10
> **maqifrnswa said:**
> This might be a dumb answer, excuse me if you've already tried! Have you gone to System -> Preferences -> Keyboard, then the mouse keys tab. Uncheck the box there.  The betas sometimes reset that checkbox which will disable the numpad.

You are the man ! This was the problem. Thank you so much.

I never wold have expected an option suddenly to be enabled by itself which never has been enabled in more than 5 years. Without you I would have suffered for a long time !

---

