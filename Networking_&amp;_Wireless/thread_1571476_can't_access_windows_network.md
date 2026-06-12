---
title: "can't access windows network"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by jrevillini on 2010-09-09
on a meerkat fairly-vanilla install, i can't browse the windows network or connect to shares via SMB, but can access windows machines via terminal server client, browser (if they server web pages), and the printing manager.  i should mention that this is a guest OS with up-to-date virtualbox guest additions.  it's also important to note that i have a lucid lynx guest which works flawlessly with an identical setup in terms of resources granted to the guest OS through the VBox manager.

Typical errors are:
[INDENT]Could not display "network:///".
Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.[/INDENT]

SOMETIMES I *can* open the network, but trying to open the Windows Network item to view all computers there just maxes out the CPU on the gvfs-smb-browse until it gives up.

I've followed advice to make the following changes to the system:
* installed ntfs-config (per [http://www.uluga.ubuntuforums.org/showpost.php?p=9824941&postcount=18](http://www.uluga.ubuntuforums.org/showpost.php?p=9824941&postcount=18))
* uninstalled/reinstalled gvfs and other dependent packages (per [http://ubuntuforums.org/showthread.php?t=1278395&page=2](http://ubuntuforums.org/showthread.php?t=1278395&page=2))
* modified the /etc/nsswitch.conf and installed winbind and rebooted (per [http://ubuntuforums.org/showpost.php?p=7075850&postcount=4](http://ubuntuforums.org/showpost.php?p=7075850&postcount=4))
*installed the samba4 package (just my own personal try at getting things to work)

Other oddities:
* when I can open network (which seems to be after the computer has been up for awhile), it populates with a bunch of network printers and a single "Windows Network" icon, just as it did in lucid.

---

### Post by jrevillini on 2010-09-09
OK, this is weird ... I can't ping google.com from the network tools app, but I can do it from the command line on the Meerkat box.  On the Lucid box, it works in either, as it should.

---

### Post by jrevillini on 2010-09-10
Well, while this should be something I can correct after the fact within Ubuntu, it seems this may have to do mainly with the fact that I'd installed meerkat while using NAT as my network adapter (remember - this is a guest OS).  NAT gives the guest OS full roam of the internet and a bunch of standard network protocols, but doesn't put it in the same network as the host system is using.  I won't say this will ALWAYS mess you up in a windows network, but clearly there are some cases where it may.

Previous versions of VirtualBox would use the bridged network adapter by default.  This NAT choice seems to be something they choose as the default for new guest OS's in more recent versions.

I'm marking this solved, even though it's more of a workaround.  If anyone would like to help me troubleshoot this and figure out how to make the required changes to the network settings in Ubuntu to make it work after the fact, let me know and I'll set up the test environment to do so.

---

