---
title: "Need help with file and printer sharing between two Ubuntu Ibex PCs"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-01-29
I have two PCs on the same LAN.  I have created a folder on each one and shared it out (auto-installing Samba along the way, granting writing capabilities and guest access on both sides for each folder).  Yet when I go into Places>Network, I see nothing from either side.  I've also installed Firestarter on both PCs and neither side registers any blocked events, so I don't think there is a firewall blocking the way.

On one PC I have a printer attached.  When I open up System>Administration>Printing, I get a small window that shows the printer represented as an icon with a little green circle/checkmark indicating it's the default printer.  When I right click on this icon, the following options appear:

Properties, Rename, Copy, Delete, Enabled (checked), Shared (checked), View Print Queue.

Along the top side of this window are the menu options:  Server, Printer, View, Help.

If I right-click on the printer and click Properties, I get a window titled Printer Properties - "HP Laserjet 6P on localhost"

It shows a description, location, device uri, make/model, and printer state.  Along the left are other categories (settings being the currently displayed, Policies, Access Control, Printer Options and Job Options being available to pick from).

If I click Policies, it shows "State" with the words Enabled, Accepting Jobs and Shared all checked off.  HOWEVER!  Just to the right of this it says "Not Published, See server settings".

Access Control shows "Allow printing for everyone except these users:" which none are listed, so it otherwise is accepting from all users.

Printer Options shows general things like media size, printout mode, media source, double sided printing, resolution/quality.

Job Options shows defaults like "Number of copies, orientation, scale to fit, pages per side, etc."

Closeing this window takes me back to the original smaller window with the icon for the printer.  Clicking on Server>Settings brings the following window up:

Several check boxes are available.

-Show Printers shared by other systems (checked)
-Publish shared printers connected to this system (checked, which seems to contradict what I read in the Properties>Policies window just a moment ago)
-Allow printing from the Internet (checked just to see if it would work/make a difference)
-Allow remote administration (checked)
-Allow users to cancel any job (checked)
-Save debugging information for troubleshooting (not checked).

So from the looks of these options, my servers settings SHOULD be publishing this printer to the network as it has been told to share itself.  Right???

So, I have two Ubuntu PCs with no firewalls throwing up any red flags that are failing to share files between them as well as send print jobs from one to the other.  What's going on?

---

### Post by diablo75 on 2009-01-29
Bump.

---

### Post by diablo75 on 2009-01-29
Bump with a comment:

I can only assume the following:

From the details I've laid out in the original post it would appear to most that I've done everything correctly as far as making sure the appropriate checks are ticked and that based on these checks, everything should be working and that nobody thus far can think of a reason why it wouldn't work.

It almost begs a mini-debate take place on just how much more difficult could/*SHOULD* file and printer sharing be between two like Ubuntu systems?  They're the same version, have all of the most recent updates applied, and all of the appropriate steps taken to get these two simple tasks to work have been taken, or so I can only assume because nobody has cared to comment or correct me on what I've done so far.

I have additional questions that might help me here:

In a Windows system, when you share a folder, and open up network places, one of the networked computers you'll find is yourself, and if you double-click on yourself, you'll see the shared folders from that PC.  And I believe the same is true in Ubuntu, right? (Please tell me).  Because if it is true, maybe the fact that both PCs fail to show themselves in Places>Network could be a clue to why this stuff isn't working.

Also, a few weeks ago, I decided to try out the webcontentcontrol package so as to review it for a fellow ubuntu user who was looking for a filter for their kid.  I had a struggle getting the software off and it screwed up a lot of my firewall settings because the author seemed to think nobody would ever try to uninstall the software and it did not backup the original settings before installing its own.  I had to use firestarter to manually allow inbound connections on 5900 so I could VNC into my own PC after finally prying the software back out of my system.  Assuming there is some sort of invisible policy in action that might be blocking communication from the other PC to my own, **what port numbers should I open up to ensure file sharing and printer sharing between two PCs doesn't fail because of a blocked port?**

Lastly, is the Networking & Wireless forum the best place for me to post this problem?  I would gladly ask a mod to relocate it for me if there is a better place for it.

---

