---
title: "Flash Player Crash is Killing My System"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Tinieblas on 2009-11-01
Installed flash player the other day from the Adobe website. It was working fine and then for some reason one site said that it wasn't working properly. I went back to the Adobe site and downloaded it again and told it to reinstall. It popped up with an error and now it's killing my whole system. I have a big red error sign up by my wireless signal indicator. When I click on it, it opens the synaptic package manager and pops up this error message:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

My only option is to close the window. I tried to run the update manager and I get this error:

Package in inconsistent state
The package 'adobe-flashplugin' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.

Again, the only option is to close the window.

I found a forum that says you're supposed to install flash using this command in the terminal
sudo apt-get install flashplugin-nonfree So I tried that to see if it would fix it and it gives me this:

alan@Alan-Laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

I'm completely out of ideas... If I try to reinstall it from Adobe's site it says that the package is corrupted and can't be opened... HELP!!!

---

### Post by Tinieblas on 2009-11-01
I just tried to remove it with the computer janitor and this is what it said:

Could not clean up properly
E:Sub-process /usr/bin/dpkg returned an error code (1)

So still no luck...

---

### Post by Tinieblas on 2009-11-01
Found someone else with the same problem this is what they did and it worked!

sudo dpkg --configure -a
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin
sudo apt-get remove --purge adobe-flashplugin

---

### Post by Incendia on 2009-11-01
> **Tinieblas said:**
> Found someone else with the same problem this is what they did and it worked!

sudo dpkg --configure -a
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin
sudo apt-get remove --purge adobe-flashplugin

Glad you got it fixed. Please mark this thread as [Solved] in the prefix. :]

---

