---
title: "Bizarre random behaviour"
date: 2010-04-18
forum: Mythbuntu
---

### Post by sqeelurgle on 2010-04-18
I have been having bizarre behaviour with Mythbuntu as long as it has been installed.  The most annoying thing is that it will randomly "Jump Back" or "Jump Forward" when watching TV.  First I thought that it was some kind of interference with the remote, so I removed the binding between remote keys and page up and page down in the lircrc config files.  I didn't use it on the remote anyway, so it didn't matter.  Still got the random jumps, so I wondered about interference with the wireless keyboard.  I removed all the keybindings from those functions in "Edit Keys" because I don't use it anyway.  I am still getting random jumps with the "Jump Back" or "Jump Forward" on the OSD.  As far as I know, I shouldn't be getting any of those jumps, as there are no keys defined to run those functions, but it is still happening.  I also get random up arrow and down arrow movements in the menus and while watching live TV (which I don't do very much).  Any ideas what would be causing these ghost jumps?

Thanks

---

### Post by byStanderone on 2010-04-18
...well, a wild guess, am thinking of a loose connection somewhere, perhaps on the powerline itself,(ac supply). power surge and sparks can generate rf interference.

---

### Post by sqeelurgle on 2010-04-18
Thanks, I'll check that.  Should be easy enough to unplug everything and replug it just to check.

Any other ideas from anyone?

---

### Post by sqeelurgle on 2010-04-19
Actually, if I am getting RF interference, I still don't see how it could be giving me the random jumps - after all there is no key bound to the jump, so there should be nothing that could do it - unless the interference was causing bits to randomly change in memory somewhere in just the right way to cause a jump, and I think I would have noticed worse probnlems in that case.  I think it is a software or configuration issue.  Am I on the right track?

---

### Post by David Grigor on 2010-04-19
I never figured it out either. Both in 9.04 and 9.10 installs. It would randomly skip 10 miniutes forward or backward ( most times backward ) at least once per 30 minute show. 

As long as I had a LIRC configure it would happen. It didn't matter if the usb IR receiver is plugged in or not.  Problem goes away when I completely remove LIRC configs.  

As a workaround, I now just us a remote keyboard instead. Works pretty well since keyboard is big and doesn't fall between the cushions or get lost under the couch.

---

### Post by sqeelurgle on 2010-04-19
Hmmm, I wonder if an upgrade, or a different distro with mythtv would work.  I'll try an upgrade first and see what happens.  In the meantime I have found the setting for how far a jump occurs, and I have set it to 1 min, so that it's not as intrusive when it happens.  It still shouldn't be happening even with lirc given that I have removed any key from the function, but I guess there's a small bug in there somewhere.

---

### Post by David Grigor on 2010-04-21
For me, upgrading didn't fix it. Behavior followed from 9.04 to 9.10 + fixes.  I too played around with how far it would skip but finally just said the hell with it. Only way to get it to stop was to remove the lirc configs completely. Hasn't happened since.  For grins, I may try it again with 10.04 gets released. I will also point out that I got a bluetooth dongle and run the WII remote and behavior stopped. This makes sense because it doesn't use the LIRC config.

---

### Post by sqeelurgle on 2010-04-21
One thing that I have noticed, it that the behaviour seems to be worse when a nearby wireless mouse is being used.  It doesn't stop when that mouse isn't being used, and I still don't get how the function could even work when the key binding is removed, but there must be something to do with RF interference there.

---

### Post by sqeelurgle on 2010-04-27
OK, I have the likely solution.  I tried a different keyboard on this system, and the problem has gone.  There seems to be an undocumented feature with mythtv that the up and down arrows will do the jump forward and back - even when all keybindings are removed.  My keyboard was occasionally giving erroneous up and down arrow commands.  Not sure whether the keyboard has a fault of if there was RF interference, but either way, the kwyboard form the other computer works without trouble.  I'll be buying a new one.  I would guess that the same thing could occur if a remote gives the occasional up and down arrow commands by mistake.

---

