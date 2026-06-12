---
title: "Help with LIRC in 10.04"
date: 2010-08-04
forum: Mythbuntu
---

### Post by bcg30506 on 2010-08-04
My remote setup was working perfectly before updating my system from 9.04 to 10.04.  Now while technically it works, meaning the remote controls it and the buttons are still mapped correctly, the performance is much worse.

The remote used to respond quickly and consistently.  Now in 10.04 it seems to "miss" a lot of button presses and sometimes it "bounces" causing one key to act like I pressed it more than once.  So if I'm trying to move the cursor down, sometimes I'll press the Down key 4 or 5 times before the cursor moves on screen.  Other times I'll press it once and the cursor will move down 2 or 3 places.  Same remote and config files as before but it never used to do this.

I'm hoping it's a simple LIRC tweak or a kernel module parameter but have no idea how to go about debugging it.  Any help?

---

### Post by ian dobson on 2010-08-06
Hi,

I had a similar problem with my remote (Serial Plug with a Hauppauge remote). I spent quite some time playing with the lirc parameters until I realised the batteries where about 3 years old and at the end of their life. After replacing them everything was back to normal.

I've noticed that the user interface is abit slower in 10.04 compared to 9.10 on my underclocked frontend (c2d e5200 running at 1200MHz), but it's not too bad.

Regards
Ian Dobson

---

### Post by nickrout on 2010-08-06
I hate to say it because it seems so obvious, but have you checked the batteries? 

Honestly I am not being facetious, I have had battery failure coincide with a system update, and beat my head against the wall until the obvious hits me...

It's like the times you think networking is seriously broken only to realise that the ethernet cable is not plugged in :)

---

### Post by bcg30506 on 2010-08-06
Okay, you two talked me into it.  I'll try it when I'm there and let you know. However, I didn't go there first because it's a universal remote and is still working good and consistently for all the other components.  So it seemed strange to me that it could be batteries when it only occurs on the myth machine.  Plus it only started once I upgraded to 10.04, so it seems too coincidental that the batteries got weak the exact time I upgraded.  Still, I'll replace them and post back the results.

---

### Post by newlinux on 2010-08-06
what kind of LIRC receiver do you have? Does it give an indication when it receives an Infrared signal? Have you added any lighting or other equipment to the room?

---

### Post by bcg30506 on 2010-08-06
> **newlinux said:**
> what kind of LIRC receiver do you have? Does it give an indication when it receives an Infrared signal? Have you added any lighting or other equipment to the room?

I have the Hauppauge receiver that came with the PVR-150 capture card.  I've added nothing to the room.  Only change was the upgrade to 10.04.

Batteries seem okay.  When I control the TV with the same remote (it's universal), I cannot get ahead of the TV.  The volume bar changes as fast as I can hit the keys for volume up/down on the remote.  In mythfrontend though, it is very sporadic.  Sometimes not reading at all, other times bouncing and causing multiple changes.  This never happened in 9.04.

I'm thinking it has to be either a kernel module parameter that is different or a subtle change to the lircd.conf file that was upgraded.  However, I don't know any more than that to be able to debug it.

---

### Post by bcg30506 on 2010-08-06
Okay I have a bit more info.  On a hunch from a web search, I ran the irw utility to watch the keypress activity in the terminal.  I pressed the VolumeUp button once and got the following immediately upon pressing & releasing:

0000000000001790 00 Vol+ Hauppauge_350
0000000000001790 00 Vol+_UP Hauppauge_350

Then I pressed the VolumeUp button 3 times quickly in a row and got this sequence after a second or two delay once I completed all 3 presses - nothing printed as I was pressing them:

0000000000001790 00 Vol+ Hauppauge_350
0000000000001790 01 Vol+ Hauppauge_350
0000000000001790 00 Vol+_UP Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350
0000000000001790 01 Vol+ Hauppauge_350
0000000000001790 00 Vol+_UP Hauppauge_350
0000000000001790 00 Vol+ Hauppauge_350
0000000000001790 00 Vol+_UP Hauppauge_350

So it does not appear to be responding with a 1-to-1 event to my action at the remote.  Does this help?

---

