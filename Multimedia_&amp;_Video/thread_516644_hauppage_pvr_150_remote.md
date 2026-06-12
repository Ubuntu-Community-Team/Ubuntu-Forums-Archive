---
title: "hauppage pvr 150 remote"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by Naughty_Monkey on 2007-08-03
I am relatively new to Linux, but I am loving Ubuntu Feisty. I have decided to build a MythTV box with it and everything is working as it should except the remote. I believe it is the mceusb2 version. In irw I can see the remote working so I don't believe my configuration has any problems, but it will not control any programs. I have tried xine, Myth, mplayer, and none have worked. 

Since I see it in irw, and I used the recommended lircd and lircrc, made sure the button names matched, and double checked file placements, I don't kow what else it could be. I can't find anyone having the same problem as me. Most of the threads I can find it either doesn't work in irw or it produces unexpected results interacting with a program.

If anyone has any ideas or have the same problem, please let me know. 
:confused:
:mad:

---

### Post by happy-and-lost on 2007-08-03
Have you run xev to check that using the remote is generating an event?

---

### Post by tgm4883 on 2007-08-03
The hauppauge PVR-150 remote is not the MCEUSB2 remote.  So the first thing you need to do is figure out which remote you have.

Does the IR receiver plug into a USB slot or into the PVR-150 card?

The MCEUSB2 remote has a green windows button on it.

The PVR-150 remote has 4 colored buttons (Red, blue, green and yellow I think) and are either in a row or in a square.

Also I would check to see if you have a valid lircrc file for your remote when you figure out which one it is.

---

### Post by Naughty_Monkey on 2007-08-03
> **happy-and-lost said:**
> Have you run xev to check that using the remote is generating an event?

I did not know to try that, I will try that when I get home. Like I said, this is all new to me.

Thanks:)

---

### Post by Naughty_Monkey on 2007-08-03
> **tgm4883 said:**
> The hauppauge PVR-150 remote is not the MCEUSB2 remote.  So the first thing you need to do is figure out which remote you have.

Does the IR receiver plug into a USB slot or into the PVR-150 card?

The MCEUSB2 remote has a green windows button on it.

The PVR-150 remote has 4 colored buttons (Red, blue, green and yellow I think) and are either in a row or in a square.

Also I would check to see if you have a valid lircrc file for your remote when you figure out which one it is.

It has the green Windows button on it. I noticed all the lircd files out there had those listed and I removed them. The receiver plugs in through USB. So unless I am mistaken, that is the mceusb2 right? It came with my PVR-150. I also recorded my own lircd just in case I had the wrong one or my remote was a new one since none of the configs I found matched exactly.

By valid lircrc, do you mean all the buttons matching in the lircd. From what I understand, I may be wrong, the lircd interprets the key press on the remote and compare it to the lircrc to issue a keyboard command. Is that right?

---

### Post by Naughty_Monkey on 2007-08-03
This is the tuner card I have

 Hauppauge 1062 PCI Interface WinTV-PVR-150 MCE Kit Tuner Card

NewEgg Item# N82E16815116631

I also have a PVR500 in it too.

---

### Post by Naughty_Monkey on 2007-08-06
Got it working. Created a raw data lircd with irrecord and made my own lircrc. Still need to install the patch for response time though. Performance sucks.:)

---

