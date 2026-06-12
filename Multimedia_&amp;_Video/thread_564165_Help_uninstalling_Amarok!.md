---
title: "Help uninstalling Amarok!"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by stavaroti on 2007-09-30
Hi all,

I would like to uninstall amarok primarily because it didn't work the way i thought it would.  Since i am running ubuntu, not kubuntu, the installer installed a whole bunch of dependencies that i definitely do not need, since my ubuntu installation worked just fine without them, and now i would like to remove amarok and all the dependencies it installed.

The problem is that when i open up the terminal and type sudo apt-get remove amarok it says that amarok is not installed.  If i use the add/remove feature or synaptic, it says that amarok is not installed, but amarok opens up just fine from the applications menu and runs fine.

Is there anyway that i can remove amarok and all the dependencies and kde applications that were installed?  Also before trying to uninstall amarok i 'cleaned up' ubuntu using recommendations from this forum [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Any help would be appreciated.


Thanks everybody.

Ubuntu 7.04
Dell 700m intel 1.8Ghz

---

### Post by tbroderick on 2007-09-30
How did you install amarok in the first place?

---

### Post by stavaroti on 2007-10-02
I installed it via the terminal using the following command:

sudo apt-get install amarok

---

### Post by nofrendo on 2008-01-19
Easy... Just did it

sudo apt-get remove amarok

then

sudo apt-get autoremove

I was having this problem with Synaptic and was thinking... no... it couldn't be just that simple? But it worked!

---

### Post by saheer on 2008-01-27
Thank you  :D
Your command is working.
But I have doubt ' What is the use of the command sudo apt-get autoremove ? ' :?:

---

### Post by nofrendo on 2008-02-23
when you install Amarok, it installs a lot of stuff from KDE, as Amarok uses the qt libraries.

So doing sudo apt-get remove amarok only uninstalls amarok, and not everything that was installed when you installed it.

So sudo apt-get autoremove basically looks for files that no application uses and removes them.

Just try it, when you install amarok the download is like 100mb, and when you uninstall it it only says it will free up 17 mb of space... autoremove gets rid of the rest.

---

