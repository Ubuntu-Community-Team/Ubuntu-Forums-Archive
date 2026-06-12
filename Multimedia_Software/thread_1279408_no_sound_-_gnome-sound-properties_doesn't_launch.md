---
title: "no sound - gnome-sound-properties doesn't launch"
date: 2009-09-30
forum: Multimedia Software
---

### Post by rcopper on 2009-09-30
_**The Problem: what happened...**_

After an unexpected freeze of Ubuntu on startup - apparently while loading the apps that load on startup (and that are docked on the right side near the logout button) - volume manager, tomboy, sticky notes, tasque, mounted disks, etc - I restarted the laptop by holding the on/off button. On reboot it said something about an unclean shutdown, it did the system check, said that there are some errors that can not be fixed, suggested to log in as root and do a manual fsck.. if I got it right.. so it started fixing a bunch of errors.. smth about inodes, that had wrong numbers assigned, and so on.. (sorry if this is of no relevance.. didn't pay too much attention to this, was not expecting smth like that)


_**The Problem: symptomes..**_

at startup there is no sound/volume icon appearing in the "tray", nor can I start it from System>Preferences>Sound. When I try to do that I get an error saying that:
... it was not possible to initiate gnome-settings-daemon... and then smth about some possible problems with Bonobo... or with some non-Gnome settings manager that might be active and that conflicts with the Gnome settings 
The same happenes when trying to launch gnome-sound-properties from the command line.. 
I get the following error:
```

abcd@abcd:~$ gnome-sound-properties
E: core-util.c: Failed to stat runtime directory /home/abcd/.pulse/940448ac4b1c4d887266ce8d4960dbf4:runtime: Invalid argument
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
# the cursor keeps blinking and nothing happens until I stop it..

```The same goes for the Theme selecting manager... I entered some command, I think it was the gnome-control-center.. and it showed me that it could not initiate the gnome-sound-settings nor the theme selector... 

**So the sound doesn't work - in the main user account - everytime I launch some app that uses sound - it freezes..**

**In the same time - and this is the most important - if I switch to a guest user account evrything is perfect - the sound works!**

**_What to Do?_**
so, can anybody please help with some advice? 
I tried some things suggested on the forum with regard to simila issues, but no luck.. 
I reinstalled the gnome-control-center, I reinstalled gnome...

Thank you in advance for any help

---

### Post by Littleweseth on 2009-10-01
Maybe the troubleshooting pages here might help you (though I'm not sure if they cover the problem you're experiencing.)

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

Report back after you have a play with it. :)

- L.

---

### Post by rcopper on 2009-10-03
ok, problem solved after receiving the precious help of Starcannon, although can't say exactly what was the cause.

so I deleted all the invisible folders from the home folder of the main user, except for the mozilla firefox and thunderbird folders since I didn't want to lose all my bokmarks and mail. 

the result was working sound, however I had to manually restore several folders with some "vital" settings like the gnome menu settings, epiphany bookmarks, etc. and then I had to redo all the customizing since that was lost too. 
but the most important is that the sound works and I didn't have to reinstall the whole OS as some were suggesting.

again, enormous thanks to Starcannon, whose advice helped solve this issue.

---

