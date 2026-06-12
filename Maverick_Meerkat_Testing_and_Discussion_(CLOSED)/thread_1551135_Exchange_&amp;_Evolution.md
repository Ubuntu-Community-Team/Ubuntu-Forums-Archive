---
title: "Exchange &amp; Evolution"
date: 2010-08-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by lachild on 2010-08-11
Hey Guys,

I am having problems opening up the folders on my Exchange account Via Evolution in Maverick.  When I click on the account folder to looks like it's going to open but then quickly closes again.  I can see the folders under the account view and Folder size but I can't seem to access them.  Everything else seems to be working fine (minus Global Address list but I haven't tried to fix that one yet so it doesn't count).

This is connecting to Exchange 2003 and was working fine in Lucid just before the upgrade.


Is this known bug or anyone know a work around?


Thanks in advance,
LaChild

---

### Post by Kobalt on 2010-08-12
I'm having the same behaviour so far.

---

### Post by lachild on 2010-08-18
Kobalt,

I found a temporary work around.  If you load evolution with the --disable-eplugin everything starts working.

I tried attempting to locate the plugin that was causing the problem by unchecking all the plug-ins under the pluging setting, but this did not fix the issue, you had to use the startup flag.

So for now, to get into Exchange simply run evolution from the terminal with "evolution --disable-eplugin" or add --disable-eplugin to the launcher.

Also in case your interested I opened up [Bug #617549]("https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/617549") on this issue.  Hopfully we can get this resolved before the final release.

LaChild

---

### Post by Kobalt on 2010-08-19
Thanks for the tip, I will try that asap. I have subscribed to the bug in the meantime.

---

