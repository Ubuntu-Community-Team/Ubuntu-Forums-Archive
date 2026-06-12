---
title: "Tuner HD3000 is off line.. ??"
date: 2008-09-30
forum: Mythbuntu
---

### Post by dvanbrunt on 2008-09-30
Just installed a new secondary backend. The only tuner I put in is an HD3000 which I have never used. The primary backend/frontend has 2 PVR-x50 cards in it.

After installing Myth on this Ubuntu box (Hardy Herron-- the primary backend is a dedicated MythBuntu install, same version), I ran the "MythTV Backend Setup" application and configured the card.

I went through the install steps carefully. I selected for the card the "DVB/DTV Capture Card (V3.x)". The pick box identified the "pcHDTV HD3000" and seemed to be happy with the card.

"Scanning" seemed to go fine, it identified local broadcast channels I know are there. 

I set up the video source, input source connected to tuner and backed out of MythTV Backend Setup. Asked if I wanted to run MythFillDatabase, I said "Yes". Note that I had already run the MythBuntu control Center, and set this as secondary backend, and in Backend Setup I did identify the IP of the primary backend and put the static IP for the secondary in the screen to identify this new "local" machine.  So when MythFillDatabase ran, it appeared to be populating the database of the primary backend box, with no errors.

Now here's the problem: When I try to watch TV or record from any frontend, the progam listings show the new digital channels in the lineup, but grayed out. Highlighting them, the info area says that the tuner is "offline" and so I can't actually watch or record anything.

I didn't see anything about this in the manual, and my searches have come up dry.

What am I missing?  I installed no other software... just added the card, installed MythTV through the "Add/Remove" menu item.

---

### Post by novellahub on 2008-10-01
Did you see my response to the same question here?

[http://ubuntuforums.org/showthread.php?t=932911](http://ubuntuforums.org/showthread.php?t=932911)

---

### Post by dvanbrunt on 2008-10-02
> **novellahub said:**
> Did you see my response to the same question here?

[http://ubuntuforums.org/showthread.php?t=932911](http://ubuntuforums.org/showthread.php?t=932911)

Sorry, I had not... and sorry for the cross-post... forgot I had already asked!  (Strange, I thought I had forum prefs set to notify me of replies... have to check that...)

anyway, I've rebooted since then, and it still is off-line. (Tried the restart anyway, though). Have reboot primary AND secondary backends, too. 

Also noted on the "Status" screen on the primary frontend/backend that it shows 2 new tuners, not one (both off line), so not sure if that's related.

---

### Post by dvanbrunt on 2008-10-04
> **dvanbrunt said:**
> Sorry, I had not... and sorry for the cross-post... forgot I had already asked!  (Strange, I thought I had forum prefs set to notify me of replies... have to check that...)

anyway, I've rebooted since then, and it still is off-line. (Tried the restart anyway, though). Have reboot primary AND secondary backends, too. 

Also noted on the "Status" screen on the primary frontend/backend that it shows 2 new tuners, not one (both off line), so not sure if that's related.

Ok, it's working now. See [http://ubuntuforums.org/showthread.php?p=5905384#post5905384](http://ubuntuforums.org/showthread.php?p=5905384#post5905384) for the details, and thanks for the help.

---

