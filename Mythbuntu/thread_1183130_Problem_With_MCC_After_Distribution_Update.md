---
title: "Problem With MCC After Distribution Update"
date: 2009-06-09
forum: Mythbuntu
---

### Post by uncle hammy on 2009-06-09
There were updates available for me to install today, including a "Distribution Upgrade" to the Mythbuntu Control Center.  After installation, I have the pretty new MCC with it's new layout.  However, on my Backend/Frontend machine, when I launch the MCC I get an error dialog...

> 
Exception in captureState of plugin Plugins 

Disabling Plugin


After I click Close, the MCC opens, however as the error dialog indicates, the "Plugins" tab is not there.

I do not have this same issue on my stand alone front end machine.  

Does anybody have any idea where to begin tackling this?

---

### Post by JRoque250 on 2009-06-11
Ditto here. Booting into Mythbuntu's Xfce setup means it will slow to a crawl and eventually lock up. Loging into Gnome does not show this issue. However, MCC broke with the latest distro updates as reported above and even the icon in the program menu is gone. 

I've uninstalled and reinstalled MCC but that didn't fix it. It looks like some of it's dependencies broke.

Thanks,
JR

---

### Post by chuckheron on 2009-06-13
This fixed it for me:

sudo chmod a+rx /etc/mythtv/mythweb-digest

I'm not sure if that's a security risk or not... 
It could be masking some other configuration problem...
But now MCC comes up with the Plugins button...

---

### Post by chuckheron on 2009-06-13
I take that back, it started up MCC ok, but now the mythweb configuration is pretty well hosed up..
When I attempted to disable the Set Password for Mythweb  checkbox, it complained about this:

org.freedesktop.DBus.Python.NotImplementedError

Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/backend.py", line 485, in scriptedchanges
    plugin_instances[instance].root_scripted_changes(plugin_dictionary[plugin])
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/plugin.py", line 271, in root_scripted_changes
    self._abstract("root_scripted_changes")
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/plugin.py", line 129, in _abstract
    self.__class__.__name__, method))
NotImplementedError: plugins.MythPluginsPlugin does not implement root_scripted_changes

---

### Post by uncle hammy on 2009-06-13
I realized that I must have enabled the Testing PPA when I installed the weeklybuilds repos package.  The new MCC in question, came from there.  I ended up wiping all my machines because I didn't want anything dodgey on them....they're "production" machines.

---

### Post by JRoque250 on 2009-06-14
Hi. Thanks for the PPA tip. I am positive I did NOT enabled that option when installing the weekly updates so there must be an issue with that procedure because I too had PPA enabled. 

I removed the PPA source, uninstalled all things "mythbuntu" and reinstalled them again from the standard mythbuntu source. That fixed MCC right away. 

There's still as issue with the Mythbuntu desktop that does not happen with Gnome. Logging to the 'mythbuntu' session causes what it seems to be a loop with hundreds of defunct processes (ps -e):

xfdesktop <defunct>

That eventually settles down with the processes not dying but still in high numbers. 

How can I tell where the packages came from? Perhaps if I reinstall all that came from that PPA source I can restore the Xfce environment without having to blow everything away.

Thanks,
JR

---

### Post by JRoque250 on 2009-06-17
Ok the final issue with the desktop was resolved by following the workaround posted here: [https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/329616)

Good luck.
JR

---

