---
title: "Docky Has Stopped Working"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mamamia88 on 2010-10-03
anyone have a fix?

---

### Post by cariboo on 2010-10-03
Start docky from a terminal and post the output.

---

### Post by amitso on 2010-10-03
Same. Here's my output.

$ gnome-do
Add-in could not be loaded: The required addin 'Do.Interface.Linux.Docky,1.0' is not installed.
Mono.Addins.MissingDependencyException: The required addin 'Do.Interface.Linux.Docky,1.0' is not installed.
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
[Error 12:47:47.214] [PluginManager] Encountered error loading plugin: MissingDependencyException "The required addin 'Do.Interface.Linux.Docky,1.0' is not installed."

(Do:2390): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Add-in could not be loaded: The required addin 'Do.Interface.Linux.Docky,1.0' is not installed.
Mono.Addins.MissingDependencyException: The required addin 'Do.Interface.Linux.Docky,1.0' is not installed.
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
Error while getting object for node in path '/Do/ItemSource'.
Mono.Addins.MissingDependencyException: The required addin 'Do.Interface.Linux.Docky,1.0' is not installed.
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Add-in could not be loaded: The required addin 'Do.Interface.Linux.Docky,1.0' is not installed.
Mono.Addins.MissingDependencyException: The required addin 'Do.Interface.Linux.Docky,1.0' is not installed.
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
Error while getting object for node in path '/Do/ItemSource'.
Mono.Addins.MissingDependencyException: The required addin 'Do.Interface.Linux.Docky,1.0' is not installed.
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0

---

### Post by directhex on 2010-10-04
Docky is a standalone app now, it's not integrated in gnome-do. Look at apt:docky

---

### Post by Andre-D on 2010-10-04
is that really the whole answer ?
no more gnome-do ? - the error is just supposed to be there ?

---

### Post by seeker5528 on 2010-10-04
> **Andre-D said:**
> is that really the whole answer ?

If you have some obsolete gnome-do and/or docky packages installed, that's probably it.

Later, Seeker

---

### Post by directhex on 2010-10-04
> **Andre-D said:**
> is that really the whole answer ?
no more gnome-do ? - the error is just supposed to be there ?

Gnome Do remains. The Docky theme does not.

---

### Post by sendblink23 on 2010-10-04
the regular Docky from Ubuntu Software Center works fine

I never trust doing upgrades from older/previous OS versions... fresh install is always best

---

### Post by sancho panza on 2010-10-05
This breaks my desktop workflow completely! Docky is not the same as the Gnome-Do/docky theme!!! What was the harm in leaving the theme in place??? This is so abrupt and disruptive! Does someone know how to host an alternate repo with the required packages?

---

### Post by cariboo on 2010-10-05
The two projects split about a year ago, so it isn't like there was no warning.

---

### Post by amitso on 2010-10-05
Thanks for the update. I wasn't privi to the news about Docky and Gnome-Do being split.

Stand-alone Docky works for me just fine with Gnome-Do stand-alone called when required. One noticeable difference about stand-alone Docky is that I can't automatically add programs by dragging the edge of the dock bar. Was this feature not implemented in the most recent version of Docky?

---

### Post by cariboo on 2010-10-05
I haven't been able to do that since docky became a stand-alone app. There seems to be a fix committed for this problem, but not released. For more info on docky bugs check [https://bugs.launchpad.net/docky]("https://bugs.launchpad.net/docky")

---

### Post by seeker5528 on 2010-10-06
> **amitso said:**
> One noticeable difference about stand-alone Docky is that I can't automatically add programs by dragging the edge of the dock bar.

Dragging the edge of the dock bar?

Don't know what you mean by that, since I can drag stuff from the applications menu to the dock. Don't know if it works from the menus in KDE or other environments.

If an application is running I can right click it's icon and choose to pin it to the dock, no dragging required.

Later, Seeker

---

