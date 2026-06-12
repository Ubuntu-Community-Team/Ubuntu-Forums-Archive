---
title: "Start frontend on TV at boot"
date: 2010-02-06
forum: Mythbuntu
---

### Post by Sctmon on 2010-02-06
I am trying to get the mythtv frontend to automatically start up on the TV rather than the monitor when the computer boots. The following command works fine when run in terminal:

DISPLAY=":0.1" mythfrontend

but if I create a script to be run at startup - 

update-rc.d my_script defaults

then when the computer boots I get the following - "You must be a member of the "mythtv" group before starting any mythtv applications. Would you like to be added to the group"

Answering yes to that or manually adding my user name to the mythtv group doesn't help.

I have also tried adding the command to Gnome startup applications but it had no effect.

Any ideas on how I can either make this work or find another method of staring it up on the TV at boot?

---

### Post by 4dognight on 2010-02-06
edit /usr/bin/mythfrontend, as follows 



if [ "$1" = "--service" ]; then
   [COLOR="Red"] DISPLAY=:0.1
    export DISPLAY[/COLOR]
    #source frontend session settings

---

### Post by Sctmon on 2010-02-06
Excellent.. Works form me.

Thanks

---

