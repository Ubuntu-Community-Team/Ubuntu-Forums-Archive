---
title: "Tangerine doesn't wanna tango"
date: 2009-11-26
forum: Multimedia Software
---

### Post by SPARTAN-118 on 2009-11-26
I recently upgraded to Karmic Koala from Jaunty, and I want to share my music with my Xbox 360. However, Tangerine won't start when I click on the System->Preferences link, and trying it in Terminal results in this:

```
2009-11-26 19:02:33,674 INFO Tangerine started
[COLOR=Yellow]2009-11-26 19:02:33,730 WARN Config file '/home/matthew/.tangerine' was not found, using defaults[/COLOR]
2009-11-26 19:02:33,744 INFO Server name: matthew's Music

** (/usr/lib/tangerine/tangerine-daemon.exe:3159): WARNING **: The class Beagle.Query could not be loaded, used in Beagle, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
[COLOR=Red]2009-11-26 19:02:33,777 ERROR Failed to load 'file': Exception has been thrown by the target of an invocation.[/COLOR]
2009-11-26 19:02:33,831 INFO Loaded plugin 'session'
[COLOR=Red]2009-11-26 19:02:34,100 ERROR Failed to start server: org.freedesktop.Avahi.CollisionError: Local name collision[/COLOR]
[COLOR=Yellow]2009-11-26 19:02:34,101 WARN Shutting down[/COLOR]
```

I assume that just upgrading from 9.04 WUBI to 9.10 WUBI didn't install all the necessary files to run Tangerine. Apparently, the configuration files are missing, which might explain why the server failed to start near the end. I'll try re-installing it via Synaptic, but if it continues to do this, does anybody know how to share with 360 on Karmic? I'm currently sharing on Banshee, but the 360 doesn't see it, and, when I click "Shared Music->Matthew's music", neither does Banshee. (nothing's there)

The only "server" my 360 sees is my dad's XP computer (though it's not set up on his) and an old TwonkyMedia server that used to work but was a trial.

Thanks, 
SPARTAN-118

---

### Post by hatman on 2009-12-11
I get exactly the same fault... Have completely uninstalled it using synaptic and re-installed it but to no avail.  Anyone *any* idea as to what the problem could be? And indeed, how to sort it?  Been tearing my hair out for the last three days...

---

### Post by gnumoreno on 2010-01-20
Tangerine is not only not working but also prevents my computer from shutdown.

I killed it and executed from terminal:

```

2010-01-21 01:56:20,467 INFO Tangerine started
2010-01-21 01:56:20,485 WARN Config file '/home/mogarcia/.tangerine' was not found, using defaults
2010-01-21 01:56:20,494 INFO Server name: mogarcia's Music

** (/usr/lib/tangerine/tangerine-daemon.exe:4921): WARNING **: The following assembly referenced from /usr/lib/tangerine/plugins/Banshee.dll could not be loaded:
     Assembly:   Banshee.CollectionIndexer    (assemblyref_index=1)
     Version:    1.4.0.0
     Public Key: (none)
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tangerine/plugins/).


** (/usr/lib/tangerine/tangerine-daemon.exe:4921): WARNING **: Could not load file or assembly 'Banshee.CollectionIndexer, Version=1.4.0.0, Culture=neutral, PublicKeyToken=null' or one of its dependencies.

** (/usr/lib/tangerine/tangerine-daemon.exe:4921): WARNING **: Cannot load type 'Tangerine.Plugins.BansheePlugin'
2010-01-21 01:56:20,547 ERROR Failed to load plugin assembly '/usr/lib/tangerine/plugins/Banshee.dll': Could not load file or assembly 'Banshee.CollectionIndexer, Version=1.4.0.0, Culture=neutral, PublicKeyToken=null' or one of its dependencies.

** (/usr/lib/tangerine/tangerine-daemon.exe:4921): WARNING **: The class Beagle.Query could not be loaded, used in Beagle, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
2010-01-21 01:56:20,587 ERROR Failed to load 'file': Exception has been thrown by the target of an invocation.
2010-01-21 01:56:20,589 INFO Loaded plugin 'session'


```

I'm available to provide more info if needed.

---

### Post by maverick340 on 2010-01-31
I want to remove tangerine completely but it wont go, tangerine-daemon still lingers !

---

### Post by firefeather on 2010-02-01
> **SPARTAN-118 said:**
> I recently upgraded to Karmic Koala from Jaunty, and I want to share my music with my Xbox 360. However, Tangerine won't start when I click on the System->Preferences link...

I had the same problem; here is a post that describes how to fix it:
[http://ubuntuforums.org/showthread.php?t=1319098&p=8484358](http://ubuntuforums.org/showthread.php?t=1319098&p=8484358)

---

### Post by firefeather on 2010-02-01
> **gnumoreno said:**
> Tangerine is not only not working but also prevents my computer from shutdown.

I killed it and executed from terminal:
....

I think that might be helpful to add to [this bug]("https://bugs.edge.launchpad.net/tangerine/+bug/414988").

---

