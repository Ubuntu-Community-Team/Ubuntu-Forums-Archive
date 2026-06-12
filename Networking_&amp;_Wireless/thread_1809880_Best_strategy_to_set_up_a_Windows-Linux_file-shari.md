---
title: "Best strategy to set up a Windows-Linux file-sharing network?"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by thanasis57 on 2011-07-22
Hi everyone,

I have been beating my head over how I should set up my network. It had  only Windows machines until now, but I am about to  start replacing them with Linux ones. I would like to answer some basic questions before tampering with my network. (it is already up and running for production purposes!!)

Consider the setup:
-2 Windows XP + 2 Ubuntu (10.04 because it is LTS) machines, all connected to a router
-generally, they acquire ip addresses via dhcp, but could eventually be assigned static ip's (however, there are visitor laptops that may still need dhcp connections and file-sharing access)
-not all  machines are turned on all the time, i.e. some are powered down at night.
-not all users understand the linux filesystem, mounting, etc, so I need a certain degree of automation.

So my questions on setting up my Linux machines are as follows:

1) I saw that nautilus already mounts network shares under ~.gvfs and that it can make local folders shared over the network. That's great, but creates a question: What's best? Samba or gvfs? Are the two mutually exclusive, or may I use both? 

**a) If I were to use gvfs:**
gvfs does not seem to "see" all shares automatically. I have to go  into each one (Nautilus -> Network etc) before they are mounted. On  the contrary samba sees them all, either through command line (e.g. smbtree -N) or through GUI tools (e.g. smb4k). Am I missing something, or  is it a gvfs problem?

[B]b) If I were to use samba:
[/B]On my Linux machines I can mount network folders automatically (via  samba) through /etc/fstab entries (way better than gvfs, which  appears to require manual mounts). However, wouldn't that give me errors  if one of the other machines (Linux or Windows) is powered down while  the Linux machine starts? Or if the machine is turned off and then back on?  Would it mount correctly afterwards?

2) Are static IP's a "must" for certain services (e.g. WINS), or can I keep using dhcp? Should I make a policy decision and start giving all machines static IP's?

Thanks a million!

---

