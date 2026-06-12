---
title: "working permanently offline"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by bugbear6502 on 2011-06-22
I would like to use my laptop at home, where I don't have internet access (don't ask, long story).

My question are two-fold; 

** How do I prevent various pieces of software trying to access the net for updates etc. I presume they are likely to hang, lock up, and generally cause trouble.

** Can anyone recommend a working practice for installing updates and/or new software, either from USB or CDROM/DVD?

I have good (legitimate!) access to assorted computer facilities at my office.

I am using 11.04

   BugBear

---

### Post by Beacon11 on 2011-06-22
In response to your first question, the Update Manager won't hang if you have no internet connection-- it'll check, see that there's no connection, and stop.

As for the second question, did you do any searching? I found this in half a second: [http://ubuntuforums.org/showthread.php?t=858705](http://ubuntuforums.org/showthread.php?t=858705)

---

### Post by bugbear6502 on 2011-06-22
> **Beacon11 said:**
> In response to your first question, the Update Manager won't hang if you have no internet connection-- it'll check, see that there's no connection, and stop.


I was more concerned about Donald Rumsfelds "unknown unknowns"; many programs silently (or obscurely) access the 'net. Spam filters update profiles, astronomy programs update satellite orbit databases, html browsers check for plugin updates, and so on.

For all I know, graphics programs update their clipart directories.

So I am keen to find a solution that would stop even the ones I didn't know about; I have no idea which of the *many* pieces of software on a default install are liable to attempt net access.

> 
As for the second question, did you do any searching? I found this in half a second: [http://ubuntuforums.org/showthread.php?t=858705](http://ubuntuforums.org/showthread.php?t=858705)Again with the Rumsfeld thing - knowing the conventional terms is of great benefit when searching. Thank you for the link.

   BugBear

---

### Post by bugbear6502 on 2011-06-23
Moving on - it appears that Keryx would be an excellent solution to my upgrade question.

But my office machine (centrally maintained) runs Fedora (13, if it matters).

Does anyone know how to install Keryx (as a downloader, not an installer) on my Fedora machine?

This is a difficult thing to google (I've tried) because you get lots of pages on wanting to use Keryx (or something like Keryx) to update Fedora (i.e. Keryx for RPMs not DEBs).

  BugBear

---

### Post by owiknowi on 2011-06-23
- you can prevent auto updates in synaptic package manager: tab updates, section automatic updates.

- you also can use the network manager to prevent from trying to connect automatically.

- if you install the simple firewall manager (the blue/white shield) from ubuntu software center,
you can pretty easily  prevent any outgoing traffic when you don't need a network.
note: you'll have to change this setting every time a network is/isn't needed, alas.

hope this is a bit useful.

---

### Post by bugbear6502 on 2011-06-23
> **bugbear6502 said:**
> Moving on - it appears that Keryx would be an excellent solution to my upgrade question.

But my office machine (centrally maintained) runs Fedora (13, if it matters).

Does anyone know how to install Keryx (as a downloader, not an installer) on my Fedora machine?

This is a difficult thing to google (I've tried) because you get lots of pages on wanting to use Keryx (or something like Keryx) to update Fedora (i.e. Keryx for RPMs not DEBs).

  BugBear

OK. I've (Ark) unpacked the Keryx deb, and hand-copied the files into place.

running keryx gives:

Traceback (most recent call last):
  File "/usr/bin/keryx", line 60, in <module>
    from keryx import AboutKeryxDialog, keryxconfig
ImportError: No module named keryx

I note that the postinst script in the .deb file contained a call to  update-python-modules, which has no (obvious to me) equivalent on fedora.

It looks like I'm one command away from running Keryx on my Fedora "host" to gather deb files for my offline Unbuntu.

Can anyone help me (I'll concede that asking how to install Python modules onto Fedora is getting a bit OT for an Ubuntu forum...)

  BugBear

---

### Post by RoflHaxBbq on 2011-06-24
Making applications not check for updates when offline isn't really necessary usually; many applications won't check when a connection isn't available and even if it does check it almost always won't cause an problems.

And about your second question ( installing software when offline ). It is really quite difficult installing software on a Linux machine when offline. As you likely already know, Windows installers will package all needed libraries with the installer, but Linux will only download parts that it needs, and not download libraries it doesn't need. This means that if you have a connection, you will have tiny download sizes, but if you don't have a  connection you will have a huge annoyance searching for dependencies etc.

One way to do it is find that program you want and all of its dependencies, then download the ones that you don't already have, copy all the debs onto a USB and install them on the target machine with

```
sudo dpkg -i NAMEOFPACKAGE
```

Hope this helps ;)

---

