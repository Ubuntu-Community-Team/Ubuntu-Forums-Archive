---
title: "Unable to reinstall pidgin"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by new_to_ubun2 on 2009-07-28
I was trying to install latest version of pidgin, as I'm totally new to this ubuntu thing I did some innovative :D things, and now every thing is messed up...

sudo apt-get install pidgin

Is not working for me... need help...
thanks in advance...

---

### Post by martinbaselier on 2009-07-28
Why is it not working? Do you get a errormessages? What's the output you get when you type that command? (right mouse button to copy from terminal)

---

### Post by new_to_ubun2 on 2009-07-29
output for sudo apt-get install pidgin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
          Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1.1 is to be installed
          Depends: libpurple0 (>= 1:2.5.8-1ubuntu2~pidgin1.8.10) but it is not going to be installed
          Depends: perl (>= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is to be installed
          Depends: perlapi-5.10.0 but it is not installable
E: Broken packages

---

### Post by martinbaselier on 2009-07-29
You have a problem with your repositories. 

Have you added any third party stuff to your software sources?

You might trie to uncheck them.

---

### Post by rannable on 2009-07-29
Go to your Synaptec Package Manager and mark the program for reinstallation...

---

### Post by new_to_ubun2 on 2009-07-29
I tried this

sudo apt-get remove pidgin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pidgin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 255 not upgraded.


It's out of my system, Please suggest some solution...

---

### Post by new_to_ubun2 on 2009-07-29
When tried for reinstalltion through Synaptec Manager it gives same error as 
sudo apt-get install pidgin

I need to fix this immediately...
please help guys..

---

### Post by MichealH on 2009-07-29
Do you have a Ubuntu 9.04 CD? Ubuntu 9.04 comes with Pidgin. Try Re-installing Ubuntu or have you decided to upgrade?

---

### Post by wojox on 2009-07-29
When your in Synaptic go to Edit > Fix broken packages.

---

### Post by new_to_ubun2 on 2009-07-30
> **wojox said:**
> When your in Synaptic go to Edit > Fix broken packages.
Yes tried this too...
Nothing happens, List of broken pakages is empty....

More info:
As I said it is reinstall, First I've uninstalled pidgin using
sudo apt-get remove --purge pidgin
I geuss this is what I've done wrong

---

