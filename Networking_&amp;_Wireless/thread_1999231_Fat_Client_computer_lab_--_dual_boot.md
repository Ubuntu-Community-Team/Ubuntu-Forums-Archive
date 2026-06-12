---
title: "Fat Client computer lab -- dual boot"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by ethanay on 2012-06-07
Hi folks,

I administer a volunteer-driven technology education program for older adults.  In order to save a lot of time and money on hardware and software administration, we'd like to transition to a fat client setup for our dual-boot Ubuntu/Windows XP machines.  I've done a lot of research and still need some help on this.

Currently, we are old-school:  We have 14 identical P4 1gb machines that we administer by tweaking an image on a master computer and distributing it to the lab computers via CloneZilla and an external HDD.  The systems all boot Ubuntu and Windows XP.  Ubuntu home profile is locked via ofris-en, and Windows XP is locked via Deep Freeze.  That way the systems are always clean for the next user, and we don't have to worry much about accidental violations of privacy.  This is an upgrade from how the lab used to work, but still time-consuming to change any hardware or software setup.

Here's what we want to do:
[LIST=1]
[*]We want someone to be able to walk to a fat client, turn it on, decide whether to use Ubuntu or XP
[*]The systems need to be left clean "as they were found" for the next user -- no saved documents, internet history on the next boot.  To say this another way, this is NOT a multi-user environment, this is a public lab.  The server should NOT be storing any of the changes that clients create as they run.  Clients should not be able to modify anything on the server.  The only way to modify the server should be by working on the server directly.
[*]If we need to add/remove or update software, or change printer setups, etc, we'd like to do that only on the fat client server.
[*]We'd like the opportunity to easily add new kiosks/workstations elsewhere in the facility without having to have a completely separate administration process (but with a countdown timer that automatically logs user out after 15 minutes)
[/LIST]

Here's our available hardware:
[LIST]
[*]14 Dell Optiplex GX280 P4 1gb clients
[*]2 P4 64-bit servers (with 2gb and 4gb RAM, respectively)
[*]1 HP ProCurve 2650 network switch
[/LIST]
The reason why I'm thinking "fat clients" is that our servers aren't powerful enough for thin clients, and our client computers are more powerful than they need to be for thin clients.

To do the above, here's what I'm thinking:
Lab computers:  4gb server running UbuntuLTSP in fat-client mode, also running Windows XP with Deep Freeze in a virtual box.  
Kiosks and CloneZilla multi-cast server (as a backup?): 2gb server running same as above with additional kiosk tweaks.

Will this work?  Any tutorials for something like this?  Should we use LTSP in fat client or DRBL?  Once we have the server up and running, do we "build" a custom client (list of packages) that get loaded onto the client computer?

Thanks!!

---

### Post by snowguy on 2012-08-07
Hi ethanay, I saw no one responded to your post. Did you end up finding a solution that works for you? If so, can you share your experience with us? 

I am interested in hearing it.

---

### Post by ethanay on 2012-08-09
Thanks for the inquiry!  Am glad someone else interested in this project has found this thread.

No, I still don't have any answers to my questions.  I've dedicated as much time as I can to research, and wasn't able to uncover any potential solution.  I am just unfamiliar with too many components of the project. 

In the mean time, we've cut down our administrative costs drastically by doing the following:
[LIST=1]
[*]Boot into Lubuntu by default as the main OS
[*]Windows is the secondary OS (only used for application-specific tasks)
[*]Automatically install updates in Lubuntu (unlike Deep Freeze, ofris does not cover administrative tasks!)
[*]Create a clonezilla server running DRBL via Lubuntu
[*]Designate the Instructors' computer as the parent computer
[*]Spend our energy doing complex manual setup tasks on that one computer
[*]Distribute the image via the CloneZilla server to the other systems
[/LIST]

Deep Freeze and Windows are still a relative pain in the @$$, but at least we've minimized a vast majority of that pain.

---

