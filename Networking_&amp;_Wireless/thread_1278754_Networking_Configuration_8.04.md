---
title: "Networking Configuration 8.04"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by deck on 2009-09-29
I just loaded 8.04 as an upgrade from 7.10 on a Dell Inspiron E1505n.  The networking configuration is not retained when rebooting and there is no apparent network.  The system is being operated via wireless but both wireless and wired networking are selected.  I tried saving a location but it does not default to the last one I used.  Therefore, I must go into the Network Administrator, reset the desired configuration (wireless only) and supply the WPA Personal code.

I also noted another issue which may or may not be connected.  When I use the "User Switcher", it  works fine until I try to go back to the other user (my wife and I share this computer).  The system just presents a blank, black screen with no password entry window.

Deck

---

### Post by deck on 2009-09-30
I posted this in General yesterday but it is buried many pages back.  Since this forum is more appropriate I am reposting here with more information.

> I just loaded 8.04 as an upgrade from 7.10 on a Dell Inspiron E1505n.  The networking configuration is not retained when rebooting and there is no apparent network.  The system is being operated via wireless but both wireless and wired networking are selected.  I tried saving a location but it does not default to the last one I used.  Therefore, I must go into the Network Administrator, reset the desired configuration (wireless only) and supply the WPA Personal code.

I went into /etc/network/interfaces and commented out the setup for the wired network.  Also the setting was for "auto eth1" already which is the wireless interface.  Another thing that I noted was that when the mouse cursor was placed over the toolbar button for the network administration tool there was a grayed out label "wired networking".  The system still does not boot with the wireless working.  It takes going in and reentering the wireless security code (which is in the interfaces file). Is there anything else I can do to have the system come up with the network working?

---

### Post by t0mppa on 2009-09-30
If I understood correctly, you've got your connections configured in */etc/network/interfaces* and on the Network Manager (GUI). That's not a good idea, have to pick either one to use, as they overlap somewhat and don't work well together.

---

### Post by deck on 2009-09-30
t0mppa

That action was a last resort.  The Network Admin Tool picked up the changes.  I can always return "interfaces" back to its original configuration.  I still need to solve the problem of the system not configuring at all nor retaining the configuration.  Without having to save anything the Network Admin Tool preserved the state in 7.10.  I can't find anything in the documentation that has helped.

---

### Post by t0mppa on 2009-10-01
Ah yes, I forgot that Network Admin Tool isn't quite the same as Network Manager. I'm afraid it's been a bit too long since I've ran Hardy to be of much help with the older software.

---

### Post by bapoumba on 2009-10-02
Threads merged.

---

