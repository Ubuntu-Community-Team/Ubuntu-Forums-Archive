---
title: "Blacklist an individual application from using overlay-scrollbars"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nicocarbone on 2011-04-22
I am having problems with some programs when using overlay-scrollbars, mainly Code::Blocks and Eclipse. Is there a way to blacklist only this applications from using the new scrollbars? 

I've found several ways of disabling the overlay scrollbars completely, for all applications, but I like them and I don't want to do this. 

Thanks you.

By the way, I opened some bug reports because of this:

[https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/768730](https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/768730)
[https://bugs.launchpad.net/ubuntu/+source/codeblocks/+bug/769031](https://bugs.launchpad.net/ubuntu/+source/codeblocks/+bug/769031)

---

### Post by SevenMachines on 2011-04-22
```
$ LIBOVERLAY_SCROLLBAR=0 codeblocks
``` should work?

---

### Post by nicocarbone on 2011-04-22
> **SevenMachines said:**
> ```
$ LIBOVERLAY_SCROLLBAR=0 codeblocks
``` should work?

It works, but only from the terminal. Is there a way to set this in a way that this command is executed every time I open the application (even from the dash or the launcher)?

---

### Post by SevenMachines on 2011-04-22
i tend to have a user directory with some local programs, i also stick startup scripts in there if needed. for example, this is what i actually have for eclipse

start-eclipse.sh:
```
#!/bin/sh
LIBOVERLAY_SCROLLBAR=0 eclipse
```
then make executable, eg
```
$ chmod 755 start-eclipse.sh
```
Then use the 'menu editor' to change the eclipse program to point to the script
Maybe theres a more straightforward way, i dont know

---

### Post by nicocarbone on 2011-04-22
> **SevenMachines said:**
> i tend to have a user directory with some local programs, i also stick startup scripts in there if needed. for example, this is what i actually have for eclipse

start-eclipse.sh:
```
#!/bin/sh
LIBOVERLAY_SCROLLBAR=0 eclipse
```
then make executable, eg
```
$ chmod 755 start-eclipse.sh
```
Then use the 'menu editor' to change the eclipse program to point to the script
Maybe theres a more straightforward way, i dont know

This worked perfectly. I didn't know that changing the setting in the "Menu editor" would change the shortcut the dash uses.

---

### Post by mc4man on 2011-04-22
The script way probably is best, an update wouldn't affect. You could of also set an env in the app .desktop on the Exec= line like
Exec=env LIBOVERLAY_SCROLLBAR=0 codeblocks

As far as eclipse it is actually blacklisted in the current overlay-scrollbar, so if updated there it's likely if you purged the 2 packages (overlay-scrollbar, liboverlay-scrollbar), then re-installed with a restart it should of worked (in blacklisting

---

### Post by nicocarbone on 2011-04-22
> **mc4man said:**
> The script way probably is best, an update wouldn't affect. You could of also set an env in the app .desktop on the Exec= line like
Exec=env LIBOVERLAY_SCROLLBAR=0 codeblocks

As far as eclipse it is actually blacklisted in the current overlay-scrollbar, so if updated there it's likely if you purged the 2 packages (overlay-scrollbar, liboverlay-scrollbar), then re-installed with a restart it should of worked (in blacklisting

I already tried purging and reinstalling the scrollbar packages, but the blacklisting of eclipse is still not working. I tested this in two different PCs.

---

### Post by mc4man on 2011-04-22
> **nicocarbone said:**
> I already tried purging and reinstalling the scrollbar packages, but the blacklisting of eclipse is still not working. I tested this in two different PCs.

That is odd - the blacklist does work here. ( and overlay-scrollbar is now using the blacklist instead of the whitelist starting in 0.1.9-0ubuntu1
So if i was to remove a few things from the blacklist (synaptic, eclipse), build and install just the new liboverlay-scrollbar package, then the overlay-scrollbars show up in both of those apps
Re-installing the repo package and they go away

---

### Post by nicocarbone on 2011-04-22
> **mc4man said:**
> That is odd - the blacklist does work here. ( and overlay-scrollbar is now using the blacklist instead of the whitelist starting in 0.1.9-0ubuntu1
So if i was to remove a few things from the blacklist (synaptic, eclipse), build and install just the new liboverlay-scrollbar package, then the overlay-scrollbars show up in both of those apps
Re-installing the repo package and they go away

Have you tried Eclipse? Because the blacklist works for me, Synaptic and Update Manager, for example, do not use the overlay scrollbar. It is only Eclipse that shows the overlay scrollbar being blacklisted.

---

### Post by mc4man on 2011-04-22
> Have you tried Eclipse? 
Yeah (not that I know how to use, but can follow a tutorial)
with overlay scrollbars enabled, (not blacklisted),  there is no normal scroll area, just a very, very faint non-colored pager (in a project window, vertical only

Re-installing the current repo package and i get the normal vertical/hortizontal scrollbars

Also w/ the overlay enabled in the 'Open file' dialog box there is a visible pager, but it breaks up, again with repo package restored it is the normal one

---

