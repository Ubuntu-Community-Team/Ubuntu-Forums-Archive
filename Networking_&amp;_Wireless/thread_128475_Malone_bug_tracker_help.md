---
title: "Malone bug tracker help"
date: 2006-02-11
forum: Networking &amp; Wireless
---

### Post by mpvano on 2006-02-11
Even after creating a new account, I can't for the life of me figure out how to use "malone" the replacement for bugzilla.

If you try to do anything to do with bugs, it ends up demanding the name of a source package and you can't get any farther - I have no idea what part of the system is responsible for a bug! Isn't this a little backwards?

Bugzilla let you SEARCH for entries with related keywords.

Here's what I'm trying to report - I'd appreciate it if someone could explain exactly how to do it (I already have an account in "malone").

After endless screwing around, I have found that the reason hostap drivers for prism cards act strangely under ubuntu breezy is that the "ifrename" program incorrectly grabs and renames the "wifi0" control device created by hostap as the primary network interface - SOMETIMES. It does this seemingly randomly, and when it does, the real network interface gets an unpredictable name.

Disabling the /etc/iftab entry for the interface in question (by MAC address) completely, seems to eliminate all problems. The interface is now named what the documentation says it should be and is always correctly named regardless of whether the card comes up at boot or after resume.

In the case of hostap, the card is named wlan0, which seems to be the traditional name expected by most interfaces.

I think the problem is that hostap creates an interface with a weird MAC address that looks like the actual mac address but with many more digits. It appears that ifremap only looks at the first few digits and then sometimes grabs the hostap control interface.

I'm not convinced ifrename is ever helping anything anyway. All it seems to be doing is adding confusing behavior which breaks most wireless card documentation.

Anyway, how would I search for this bug, and if it's not known, report it.

thanks,

Mario

---

### Post by ippiraman on 2006-02-11
You can search or report bugs here:

[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

---

### Post by mpvano on 2006-02-12
Thanks, I knew about this link but it didn't seem to have any relevant entries last time I looked. I found a bug report that seemed appropriate, and added mine as a comment.

The new system makes bettersense now that there are more entries there to look at as examples....

Mario

---

