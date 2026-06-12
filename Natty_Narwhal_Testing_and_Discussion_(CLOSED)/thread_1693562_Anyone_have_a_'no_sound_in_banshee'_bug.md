---
title: "Anyone have a 'no sound in banshee' bug?"
date: 2011-02-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by SevenMachines on 2011-02-23
No sound in banshee here with lots of
```
[Warn  08:03:19.136] Caught an exception - Mono.Unix.UnixIOException: Broken pipe [EPIPE]. (in `Mono.Posix')
at Mono.Unix.UnixMarshal.ThrowExceptionForLastError () <0x00013>
at Mono.Unix.UnixStream.Write (byte[],int,int) <0x000b3>
at NDesk.DBus.Connection.WriteMessage (NDesk.DBus.Message) <0x0009c>
at NDesk.DBus.Connection.Send (NDesk.DBus.Message) <0x0003b>
at NDesk.DBus.BusObject.SendSignal (string,string,string,NDesk.DBus.MessageWriter,System.Type,System.Exception&) <0x000fb>
at (wrapper dynamic-method) NDesk.DBus.MessageWriter.HandlePropertiesChanged (NDesk.DBus.BusObject,string,System.Collections.Generic.IDictionary`2<string, object>,string[]) <0x0012a>
at Banshee.Mpris.MediaPlayer.HandlePropertiesChange (string) <0x0007c>

```

and a,
```
Service `Banshee.MediaEngine.PlayerEngineService' not initialized: Broken pipe [EPIPE].

```

Just to check if anyone else is seeing this

---

### Post by farooq23 on 2011-02-23
Me Having the same issue. 

I tried to installing banshee from dialy build ppa as well, it did fixed the issue, but once I rebooted the machine, again I don't have sound

Regards,
farooq23

---

### Post by P-I H on 2011-02-23
Yes, I have the problem since I installed daily build 21/2.

---

### Post by SevenMachines on 2011-02-23
Is there a bug open on it?

---

### Post by SevenMachines on 2011-02-23
Daily build does indeed fix it

---

### Post by mc4man on 2011-02-23
There is a fix committed on it, if using the current ubuntu package open Edit > Preferences and disable the "Show Banshee in sound menu" option
(it will still be controllable in sound menu
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/722484](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/722484)

---

### Post by gnomeuser on 2011-02-23
Fixed here. Should be in the daily ppa later today.

[http://git.gnome.org/browse/banshee/commit/?id=fe9968993aa5095cc7408cd47626aff9f01fefad](http://git.gnome.org/browse/banshee/commit/?id=fe9968993aa5095cc7408cd47626aff9f01fefad)

---

### Post by SevenMachines on 2011-02-23
> **mc4man said:**
> There is a fix committed on it, if using the current ubuntu package open Edit > Preferences and disable the "Show Banshee in sound menu" option
(it will still be controllable in sound menu
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/722484](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/722484)
Yep, that does it too. and since 'fix committed' i can ignore it too :) thanks folks

---

### Post by mc4man on 2011-02-23
There is another issue w/ banshee, though not sure if a bug
If you close banshee w/ a track playing (basically minimize to sound preferences), when reopened from sound pref.'s there will be no global menu available.
However if minimized to launcher then there is no issue w/ the gm.
May file one, may not.

---

### Post by P-I H on 2011-02-23
Yes it is working now with the "Show Banshee in sound menu" option not set.

---

### Post by farooq23 on 2011-02-25
> **mc4man said:**
> There is another issue w/ banshee, though not sure if a bug
If you close banshee w/ a track playing (basically minimize to sound preferences), when reopened from sound pref.'s there will be no global menu available.
However if minimized to launcher then there is no issue w/ the gm.
May file one, may not.

I am having the same issue. please file the bug report

---

### Post by rajeev1204 on 2011-02-26
Same here.

No sound even with latest updates.Some broken pipe error in terminal.

---

### Post by mc4man on 2011-02-26
> **rajeev1204 said:**
> Same here.

No sound even with latest updates.Some broken pipe error in terminal.

The upgrade of banshee will not disable the option 'show banshee in the sound menu', you need to do that yourself

---

### Post by rajeev1204 on 2011-02-26
> **mc4man said:**
> The upgrade of banshee will not disable the option 'show banshee in the sound menu', you need to do that yourself


I got it now, at first i was deselecting that option from edit> preferences > general tab but i found a similar option under extentions tab and now after disabling it i can hear sound.

---

### Post by mc4man on 2011-02-26
> but i found a similar option under extentions tab and now after disabling it i can hear sound.
 You should leave the _extension_ enabled, but disable the _option_ - that should allow playback and allow banshee to be 'minimized' to the sound menu (clicking the close button while track is playing
The minimize to sound menu will lose the global menu atm so it's usefulness is limited.


Edit: the update to 1.9.4 should take care of - the _'option'_ can now be enabled
(though see no purpose to it

---

### Post by farooq23 on 2011-02-26
> **mc4man said:**
> 

The minimize to sound menu will lose the global menu atm so it's usefulness is limited.




how to report this bug, it is happening to me for banshee and empathy both.

---

### Post by mc4man on 2011-02-26
> how to report this bug ..
Well you'd go in a terminal
ubuntu-bug <package name>

Not exactly sure what the GM package is in unity, indicator-appmenu enables it (indicator-applet-appmenu in gnome-panel
Or just file against each app, (banshee and empathy
Ex.
```
ubuntu-bug banshee
```

---

