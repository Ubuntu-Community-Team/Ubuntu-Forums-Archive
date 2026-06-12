---
title: "[SOLVED] Preferences menu fails to disable f-spot auto photo import"
date: 2008-06-20
forum: Multimedia Software
---

### Post by Superkuh on 2008-06-20
I'm on 8.04. I have an USB mass storage device (casio exilim camera) that's auto-mounted upon connection. Under 'System: Preferences: Removable Drives and Media' (in gnome) I have unchecked under "digital camera" the "import digital photographs when connected" option. Unfortunately fspot still opens and tries asks if I wish to import the photos every time I plug in my camera (I have restarted many times). 

Is there a configuation file on disk I can edit? I found nothing in ~/.gnome2/f-spot or ~/.gconf/apps/f-spot . 

I realize this isn't likely a f-spot-import related configuration issue, but more likely lies within generalized ubuntu configuration. I don't know where to start. Any ideas on how I would go about fixing this short of completely uninstalling f-spot?

__edited many months later__
> **jimtla said:**
> There is a better solution to this problem, and it was already suggested in Superkuh's post (#6)

There was just 1 small bug in his code, 
he wrote: 
```
$ gksu gnome-volume-properties
```
and 
```
$ gksu nautilus-file-management-properties
```
To launch the two dialogs that need to be changed to disable autoload. This is exactly what needs to be done, unfortunately they were both run as root (under gksu) and as such the root preferences were changed instead of the user preferences. You just have to use:
```
$gnome-volume-properties
$nautilus-file-management-properties
```
And fix the preferences.

---

### Post by xc3RnbFO8P on 2008-06-20
Try File Management System> Preferences> File Management 
If you cant see File Management goto
System> Preferences> Main Menu
In Main Menu System> Preferences, check box File Management
In File Management Media tab Photos choose do nothing.

---

### Post by Superkuh on 2008-06-20
Thank you for the quick reply, Ringi. That solved it.

[1 day later...]
Okay, I was wrong. f-spot now only attempts to open but crashes before it can, ala:
```
An unhandled exception was thrown: F-Spot cannot find the Dbus session bus.  Make sure dbus is configured properly or start a new session for f-spot using "dbus-launch f-spot"

  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.20.0.0)
FSpot.Utils (0.0.0.0)
gdk-sharp (2.12.0.0)
gnome-vfs-sharp (2.20.0.0)
Mono.Addins (0.3.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System (2.0.0.0)
Mono.Posix (2.0.0.0)
Cms (0.0.0.0)
FSpot.Core (0.0.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins.Setup (0.3.0.0)
gnome-sharp (2.20.0.0)
glib-sharp (2.12.0.0)
f-spot (0.4.3.1)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-19-generic x86_64 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
lenny/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"
```

This is slightly better, but still annoying.

---

### Post by Superkuh on 2008-06-21
Upon advice from freenode #ubuntu and "soundray" I tried replacing 'f-spot-import' in [System:Preferences:Removable Drives and Media: Digital Camera] with 'true' and then rechecked the box. This lead to the same error as above. It's quite odd that f-spot-import would be called when there are absolutely no references to it in the configuration. :\

---

### Post by xc3RnbFO8P on 2008-06-21
Did you try **dbus-launch f-spot** in terminal

---

### Post by Superkuh on 2008-06-21
Yes. Nothing seemed out of the ordinary to me and it started fine (as it does when called in any other way). Also; **I don't want fspot being called in the first place (crashing is better than opening in my opinion)**. I would like to avoid disabling automount and browsing (via nautilus) of removable media if possible.

Thanks again for the quick reply.
```
$ dbus-launch f-spot 
Unable to create /home/superkuh/.dbus/session-bus
Starting new FSpot server
```

A clearer example of what I did to test:
```
$ gksu gnome-volume-properties
```[IMG]http://superkuh.ath.cx/users/superkuh/removabledrives_digicams.jpg[/IMG]
[COLOR="Black"]__________________________________________________________________________[/COLOR]
```
$ gksu nautilus-file-management-properties
```[IMG]http://superkuh.ath.cx/users/superkuh/filemanagment_media.jpg[/IMG]

---

### Post by xc3RnbFO8P on 2008-06-21
Do you got dbus installed in Synaptic Package Manager?
Or reinstall it again.

---

### Post by Superkuh on 2008-06-21
dbus was installed via synaptic. Just to be sure I reinstalled. The results are exactly the same. **I have now removed f-spot entirely and am having no issues**. I consider this close enough to solved. Again, thanks for the back and forth help.

---

### Post by xc3RnbFO8P on 2008-06-21
I see that you have command **true**
I got **f-spot-import**

---

### Post by Superkuh on 2008-06-21
> **Ringi said:**
> I see that you have command **true**
I got **f-spot-import**
Yes. I removed '**f-spot-import**' because I did not want f-spot-import called and the '**true**' command would not return any errors when called. Despite this, f-spot-import popped up (before I uninstalled it (see previous post)). Wierd, eh?

And yes, I did restart multiple times in between configuration changes.

---

### Post by xc3RnbFO8P on 2008-06-21
> **Superkuh said:**
> Yes. I removed '**f-spot-import**' because I did not want f-spot-import called and the '**true**' command would not return any errors when called. Despite this, f-spot-import popped up (before I uninstalled it (see previous post)). Wierd, eh?

Its a bug.
Hardy has to many bugs.

---

### Post by blindOptimist on 2008-07-03
I too have removed F-Spot. Who thought it was a good idea to make it pop up whenever I plug in a USB device?

Clearly, this behaviour was introduced by a recent update. Until a couple of weeks ago I could plug in USB devices without being troubled by F-Spot. And troubled I was, since its entirely unwanted attempts to index all photos on said USB device brought my (well specced) machine to a grinding halt.

This is the kind of heavy-handed, making-assumptions behaviour I expect from Windows, not from Ubuntu. I recommend that the default be changed back to how it was previously. In other words, please don't run F-Spot unless the user actually asks to. Autorun belongs to the world of Windows, not Ubuntu   :)

---

### Post by sim-value on 2008-07-03
Seconded **Remove any Application autostarts whatsoever!**
F-Spot always crashes my PC and i had to restart Multiple times!

---

### Post by |{urse on 2008-07-03
lol sorry i was bored

---

### Post by puikku on 2008-07-16
I'been fighting with the same problem for some time, thanks for the solution.

Not very nice that the handling of removable storage has suddenly split to nautilus preferences and to removable drives and media and these two don't seem to cooperate. I guess this should be already being worked out.

---

### Post by Midahed on 2008-07-31
> **blindOptimist said:**
> ...This is the kind of heavy-handed, making-assumptions behaviour I expect from Windows, not from Ubuntu. I recommend that the default be changed back to how it was previously. In other words, please don't run F-Spot unless the user actually asks to. Autorun belongs to the world of Windows, not Ubuntu   :)

Oh, well said!

I've been fighting this damn thing for most of the morning.  I don't like F-Spot, but it seems that the powers that be have decoded we must have it pop-up whenever a digital camera is connected to the system.

Grrrrrr  :-(

---

### Post by psyguy92 on 2008-08-19
I just removed F-Spot. I probably shouldn't be following up on this thread as it's listed as 'solved'. Removing default software doesn't really seem like an elegant solution to me, but if it fixes the -install USB drive and wait for PC to crash because it's trying to load everything into F-spot- problem, so be it. Does anyone know of any other solutions?

---

### Post by lightstream on 2008-08-28
> **Midahed said:**
> [QUOTE=blindOptimist]This is the kind of heavy-handed, making-assumptions behaviour I expect from Windows, not from Ubuntu. I recommend that the default be changed back to how it was previously. In other words, please don't run F-Spot unless the user actually asks to. Autorun belongs to the world of Windows, not Ubuntu   :)
Oh, well said!

I've been fighting this damn thing for most of the morning.  I don't like F-Spot, but it seems that the powers that be have decoded we must have it pop-up whenever a digital camera is connected to the system.

Grrrrrr  :-([/QUOTE]

Thirded! It's one of those stupid attempts to 'idiot-proof' Linux in order to attract idiots over from Windows.

Yes Windows is bad, and it's bad cos it's driven by marketing, one part of which aims to obscure the true workings of the machine and thus increase dependence on Windows (hidden file extensions being the classic example of this).

Personally, I wish they'd stop it. Let the idiots stay on Windows, that's my view.

---

### Post by jimtla on 2008-12-06
There is a better solution to this problem, and it was already suggested in Superkuh's post (#6)

There was just 1 small bug in his code, 
he wrote: 
```
$ gksu gnome-volume-properties
```
and 
```
$ gksu nautilus-file-management-properties
```
To launch the two dialogs that need to be changed to disable autoload. This is exactly what needs to be done, unfortunately they were both run as root (under gksu) and as such the root preferences were changed instead of the user preferences. You just have to use:
```
$gnome-volume-properties
$nautilus-file-management-properties
```
And fix the preferences.

---

