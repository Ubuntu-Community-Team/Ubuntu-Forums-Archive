---
title: "prevent rhythmbox plugin from activating on startup?"
date: 2008-07-24
forum: Multimedia Software
---

### Post by ranko on 2008-07-24
hi everybody,
i'm having a small annoyance with rhythmbox in xubuntu. i installed rhythmbox from synaptic and it generally works fine, but it gives me two error popups on every startup:

Plugin Error: Unable to activate plugin Magnatune Store
Plugin Error: Unable to activate plugin Jamendo

is there any way to suppress the activation of these two plugins when rhythmbox is starting?

when i go to Edit -> Plugins from the menu, the "Enabled" boxes are unchecked for these two plugins, so i'm guessing there will be some config file editing involved.

---

### Post by bensode on 2008-08-12
Bump.  I also have also found this to be annoying.  There's no obvious method to stop it from using these two plugins and apt-cache search doesn't turn up a package that can be installed to install these plugins to subsequently remove them.

---

### Post by bensode on 2008-08-12
> **bensode said:**
> Bump.  I also have also found this to be annoying.  There's no obvious method to stop it from using these two plugins and apt-cache search doesn't turn up a package that can be installed to install these plugins to subsequently remove them.

FIXED!

Trolled through the bug forums and found this gem:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/226493/comments/4](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/226493/comments/4)

Use sudo apt-get install libgnomevfs2-extra then restart Rhythmbox and the error popup goes away AND you can then manage / uncheck the plugins.

---

### Post by ranko on 2008-08-13
thank you bensode!
it works. :-)

---

