---
title: "[SOLVED] Flash in firefox for other users"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by pip_134 on 2008-02-16
Hey all,
I've been using linux for a short time now and have my account pretty sorted. My housemates also use the machine and have profiles set to "user" level. 

The main question is: how do I install programs for them as well? The exact question is: how do I get flash working in firefox for them? I've trying a manual install from within their user but I am told it is all ready installed, is it a matter of telling firefox where to look?

Thanks for you time!

---

### Post by wolfen69 on 2008-02-16
try this. open up your mates account, remove flash, and install this flash file: [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)
just click to install.

---

### Post by gandaran on 2008-02-16
> **pip_134 said:**
> Hey all,
I've been using linux for a short time now and have my account pretty sorted. My housemates also use the machine and have profiles set to "user" level. 

The main question is: how do I install programs for them as well? The exact question is: how do I get flash working in firefox for them? I've trying a manual install from within their user but I am told it is all ready installed, is it a matter of telling firefox where to look?

Thanks for you time!

if flash is installed in /usr/lib/mozilla/plugins, it will work for all user's, if it's installed in your home/user/.mozilla /plugins, account it will only work for you. 
you can sort this out just by coping the plugin to the other user account or delete the plugin if it's in your home  folder or uninstall if it's on your filesystem then type on a terminal this, « sudo apt-get update » first, then  « sudo apt-get install flashplugin-nonfree »
must have the gutsy-update repository enabled.

---

### Post by pip_134 on 2008-02-16
I managed to solve the problem, then read gandaran's post. He's got it spot on: the plugin was in each users /.mozilla so I copied across the files from my account and everything worked.

Thanks again

---

