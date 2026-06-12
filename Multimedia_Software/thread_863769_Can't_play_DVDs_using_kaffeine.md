---
title: "Can't play DVDs using kaffeine"
date: 2008-07-18
forum: Multimedia Software
---

### Post by wandalalakers on 2008-07-18
Update: I have two DVD drives in my desktop.  

Dvd drive #2 can play DVDs while dvd drive #1 can't unless I manually change the xine engine setting but then dvd drive #2 can't anymore
Is there any way to get two DVD drives to play a DVD in the same desktop using one xine engine setting?

using xine engine setting /dev/scd0 dvd drive #1 works but dvd drive #2 does not work (encrypted dvd)
using xine engine setting /dev/scd1 dvd drive #2 works but dvd drive #1 does not work (encrypted dvd)
my initial configuration was /dev/dvd dvd drive #2 works but dvd drive #1 does not work (encrypted dvd)

so it seems using xine engine setting /dev/dvd is the same as xine engine setting /dev/scd1 at least in my desktop with two dvd drives.
Oh well, thx mc4man.
my scd1 drive is a dvd writer so I'll just keep scd0 for my xine engine setting since it's the dvd reader.
I'll just use scd1 for burning dvds only
I'm going to try something else for giggles and will post what I find out here shortly.
I just tried an unencrypted dvd in both drives but I still get the same problem as above.  
I'm going to report this bug.  thx for responding to this thread mc4man.

---

### Post by mc4man on 2008-07-19
When Kubuntu 8.04 first came out I found the exact same thing with 2 dvd drives, neither of the 2 'default ' apps, kaffeine and amarok could work with 2 drives. And to make matters worse the default device settings of both apps did not work that well with one drive. Setting them to /dev/scdx instead of the links, /dev/dvd, /dev/cdrom, ect. solved that, but using 2 drives without manual editing was and still is a mystery. (at least to me and apparently you).

I would of thought that when media was inserted, the default device setting of the app called would be dynamically changed to the device the media was inserted in. And stay that way till the same media type was inserted into the other drive, in which case it would change to it. And so on and so forth.

Now maybe there's a way to configure this, hidden away in all the config options, would love to know. But for something so basic you'd think it would work from the get go or by now.
I would find it hard to believe that no one working on  kubuntu's release didn't have 2 dvd drives, more likely considered to be of low importance.

---

