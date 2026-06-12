---
title: "no ubuntu one and cant update on  update manager"
date: 2011-01-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by liverpoolatnight on 2011-01-13
Hi all

Today i installed 11.04 natty aph1 and it all installed great :D then though ill update on update manager. When it updated it throw some errors then carried on updating the system thinking things will improve. Anyway restarted my system and an error message come up and said i don't have the right hardware :\ hmm my pc is not that old so i booted back up again.

everything was fine but it kinda looked strange as it looks like 10.10 :S

and now i cant update because the thing dos not come up but gives me a error

tryed
sudo update-manager -d
[B][COLOR="Red"]root@nattylinuxb1:/home/francis# sudo update-manager -d
/usr/lib/pymodules/python2.7/gtk-2.0/gtk/__init__.py:40: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import gio
ImportError: could not import gio
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 81, in <module>
    from DistUpgradeFetcher import DistUpgradeFetcherGtk
  File "/usr/lib/python2.7/dist-packages/UpdateManager/DistUpgradeFetcher.py", line 26, in <module>
    from ReleaseNotesViewer import ReleaseNotesViewer
  File "/usr/lib/python2.7/dist-packages/UpdateManager/ReleaseNotesViewer.py", line 33, in <module>
    class ReleaseNotesViewer(gtk.TextView):
AttributeError: 'module' object has no attribute 'TextView'
root@nattylinuxb1:/home/francis#[/COLOR][/B]

And i cant install .deb file aswell :( 

Any helps :P 

System info
aph1 x64 (No partion's)
intel pentium 4 ht 3.00ghz
2GB DDR2 667 ram
80gb ide hard 7200rpm
pci express x16 ati radeon X1550 256mb
At this time i am downloaded the x86 to see if i have the same problems :(

---

### Post by dino99 on 2011-01-13
i suggest to read and learn a little more about how to maintain a system and using the main commands: see the links below.

For all your updates, use "synaptic" or "apt-get update", then "apt-get upgrade"

---

### Post by ronacc on 2011-01-13
and to install a .deb you already have downloaded use 
```
sudo dpkg
```   see ```
man dpkg
``` for syntax .

---

### Post by liverpoolatnight on 2011-01-13
> **dino99 said:**
> i suggest to read and learn a little more about how to maintain a system and using the main commands: see the links below.

For all your updates, use "synaptic" or "apt-get update", then "apt-get upgrade"

Cheers for the advise :D 

> **ronacc said:**
> and to install a .deb you already have downloaded use 
```
sudo dpkg
```   see ```
man dpkg
``` for syntax .

:)

---

### Post by lidex on 2011-01-13
One other small thing. You were invoking update-manager, a gui program. Anytime doing that from terminal you should prefix with gksu or gksudo (graphical sudo) or you can run into weird issues.
Reference here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by cariboo on 2011-01-14
> **lidex said:**
> One other small thing. You were invoking update-manager, a gui program. Anytime doing that from terminal you should prefix with gksu or gksudo (graphical sudo) or you can run into weird issues.
Reference here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

If you look at the op, you'll see he was running as root, using sudo when running as root, makes no sense.

---

### Post by gooeykablooey on 2011-01-14
I had a similar problem earlier, where the same error messages came up. Apparently I was running gir1.0 libraries instead of gir1.2, which does not include the __init__.py file that was being referenced.

Try running

```
sudo apt-get install gir1.2-gtk-3.0
```This package should require a number of other gir1.2 packages, and will remove the old gir1.0 packages. I have not found any problems with this yet, but I'm still not quite sure why the older gir1.0 packages were installed.

---

### Post by lidex on 2011-01-15
> **cariboo907 said:**
> If you look at the op, you'll see he was running as root, using sudo when running as root, makes no sense.
Yeah, you're right - didn't see that. Doesn't make sense.

---

