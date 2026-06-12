---
title: "Feisty Herd 4 and MythTV"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by Titus A Duxass on 2007-03-01
This is mainly for information to SuperM1.
My report on a Feisty Herd 4 + Mythtv install.

Hardware:
AMD XP1500
1gb RAM
80gb IDE HDD
BT878 based card
PC Chips Mainboard
On-Board Sound and network card

This is what I did:

1. Installed a command line system (with expert enabled to set the IP manually).
    Formatted according to the Edgy guide in the community.
    Said yes to the repositories. 
2. Installed nvidia drivers from the command line.
3. Used apt-get to install the two new meta-packages mythtv-backend-master and ubuntu-frontend-master.

Now the tricky bit:
4. Tried to run mythtv-setup - got could not start X
5. Reboot and MythTV appears as if by magic. Problem - Myth-backend is not running. Probably because mythtv-setup has not been run.
6. Exit to gdm boot screen, selected openbox session.
7. Opened terminal and ran mythtv-setup. Everythng went okay until exitting. The old Channel 3 problem came up.
8. Rebooted back into MythTV, still have the same backend problem.

Other things:
It is unclear what the password for user MythTV is, so I had to reset it with sudo passwd mythtv.

Otherwise a very simple install, just needs a couple of kinks ironing out.
Unfortunately I am about to start a three week holiday in Cyprus so will be Mythless unitl 26th March.

Cheers
Titus

---

### Post by superm1 on 2007-03-01
> **Titus A Duxass said:**
> This is mainly for information to SuperM1.
My report on a Feisty Herd 4 + Mythtv install.

Hardware:
AMD XP1500
1gb RAM
80gb IDE HDD
BT878 based card
PC Chips Mainboard
On-Board Sound and network card

This is what I did:

1. Installed a command line system (with expert enabled to set the IP manually).
    Formatted according to the Edgy guide in the community.
    Said yes to the repositories. 
2. Installed nvidia drivers from the command line.
3. Used apt-get to install the two new meta-packages mythtv-backend-master and ubuntu-frontend-master.

Now the tricky bit:
4. Tried to run mythtv-setup - got could not start X
5. Reboot and MythTV appears as if by magic. Problem - Myth-backend is not running. Probably because mythtv-setup has not been run.
6. Exit to gdm boot screen, selected openbox session.
7. Opened terminal and ran mythtv-setup. Everythng went okay until exitting. The old Channel 3 problem came up.
8. Rebooted back into MythTV, still have the same backend problem.

Other things:
It is unclear what the password for user MythTV is, so I had to reset it with sudo passwd mythtv.

Otherwise a very simple install, just needs a couple of kinks ironing out.
Unfortunately I am about to start a three week holiday in Cyprus so will be Mythless unitl 26th March.

Cheers
Titus
Titus,
3 weeks without myth!  Yikes!

Glad that for the most part this is going straightforward - I'm going to have to think about the easiest way to get around the issue of not having run mythtv-setup before restarting.  I'll get back to this thread in a day or two with what I come up with.

---

### Post by Titus A Duxass on 2007-03-29
> 3 weeks without myth! Yikes! - I have a confession! I built another MythTV Box, loaded it with 1500 ogg files and 40 DVD ISOs. 

Then I removed the TV card, then tailored the menus so that I was just left with Media Library, CD/DVD and Shutdown.

Then I took the whole thing apart, packed the components into boxes (apart from the case) and packed the whole lot into a suitcase.

I rebuilt it all in Cyprus and connected it to the TV, Viola! a perfectly working Entertainment System.

Big Brownie points from the wife!

---

### Post by superm1 on 2007-03-29
Awesome that things worked out great here :).

I've got a plan in place for this problem of being unable to do mythtv-setup for future installs, but its going to take some time to execute.  Requires some changes to ubiquity and our new install process.  Hopefully by feisty release :)

---

