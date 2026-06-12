---
title: "Frequent freezing for no apparent reason?"
date: 2009-01-11
forum: Mythbuntu
---

### Post by gungfujoe on 2009-01-11
I just installed Mythbuntu 8.10 64-bit up and have been trying to get it working.  Today, I'm finding that it freezes quite often.  When it does so, I haven't found any way to get out of it other than hitting the power button on the computer.  Four freezes that have happened today (I decided to take a break after #4):

1 - I tried going into the Netflix setup within the MythTV front end, looking for a way to enter my email address and password, so that the Mythflix plugin would do something (anything).  The system froze.

2 & 4 - I tried running the Add/Remove tool in Ubuntu (having exited MythTV).  Half way though scanning for packages, the system freezes.  I can't move the mouse cursor, and hitting Caps/NumLock doesn't toggle the light on the keyboard, indicating that the the keyboard is totally frozen.  Since this happened twice while doing the same thing, I'm guessing this is repeatable, and the freezing isn't totally random.

3 - I was trying to figure out how to install Flash 10 alpha (the only available 64-bit version I could find), and I was resizing a terminal window.  The system froze in mid-resize.

The system isn't running hot, and it should be getting adequate power (I'm using an Antec TruePower 380W PSU that has been used long enough to show itself to be reliable.  Plus, I'd expect a PSU issue to result in a shutdown or reboot, not a freeze).

Since there's no obvious pattern and no kind of error message, I don't even know how to troubleshoot this, having very little Linux experience.  Where do I begin to look for a solution (or even to look for the cause of the problem)?

---

### Post by Nikas on 2009-01-11
> **gungfujoe said:**
> I just installed Mythbuntu 8.10 64-bit up and have been trying to get it working.  Today, I'm finding that it freezes quite often.  When it does so, I haven't found any way to get out of it other than hitting the power button on the computer.  Four freezes that have happened today (I decided to take a break after #4):

1 - I tried going into the Netflix setup within the MythTV front end, looking for a way to enter my email address and password, so that the Mythflix plugin would do something (anything).  The system froze.

2 & 4 - I tried running the Add/Remove tool in Ubuntu (having exited MythTV).  Half way though scanning for packages, the system freezes.  I can't move the mouse cursor, and hitting Caps/NumLock doesn't toggle the light on the keyboard, indicating that the the keyboard is totally frozen.  Since this happened twice while doing the same thing, I'm guessing this is repeatable, and the freezing isn't totally random.

3 - I was trying to figure out how to install Flash 10 alpha (the only available 64-bit version I could find), and I was resizing a terminal window.  The system froze in mid-resize.

The system isn't running hot, and it should be getting adequate power (I'm using an Antec TruePower 380W PSU that has been used long enough to show itself to be reliable.  Plus, I'd expect a PSU issue to result in a shutdown or reboot, not a freeze).

Since there's no obvious pattern and no kind of error message, I don't even know how to troubleshoot this, having very little Linux experience.  Where do I begin to look for a solution (or even to look for the cause of the problem)?

[B]Does it happen when you have much disk activity?
[/B]
I have the same problem with 8.04 and 8.10.
No problem with 7.10.
It has to do with the newer kernels..
I'm running 8.04 with the kernel that came with 7.10 and it works.

I think it has something to do with the hd-controller chip.... :(

---

### Post by gungfujoe on 2009-01-11
> **Nikas said:**
> [B]Does it happen when you have much disk activity?
[/B]
No, I don't believe so.  Since I haven't even gotten the system up and running for much, there should be nothing going on in the background, and resizing a terminal window is certainly not disk-intensive.  Getting to the NetFlix settings in MythTV shouldn't be, either.  I can see how getting data from the software repository might be, but still, that's minimally disk intensive.

---

### Post by Nikas on 2009-01-11
> **gungfujoe said:**
> No, I don't believe so.  Since I haven't even gotten the system up and running for much, there should be nothing going on in the background, and resizing a terminal window is certainly not disk-intensive.  Getting to the NetFlix settings in MythTV shouldn't be, either.  I can see how getting data from the software repository might be, but still, that's minimally disk intensive.

Ok. I have the same freezing and i have been able to narrow it down to the disk activity. What chipset do you have?

---

### Post by gungfujoe on 2009-01-11
> **Nikas said:**
> Ok. I have the same freezing and i have been able to narrow it down to the disk activity. What chipset do you have?
I'm using a Gigabyte GA-EP45-DS3L motherboard, which uses the Intel P45 north bridge and the ICH10 south bridge.  I've got a single WD6400AAKS (640GB hard drive) and an (empty) LG DVD drive attached to it.  The SATA controller is running in AHCI mode.

If the controller interface is the issue, might switching to legacy IDE mode do the trick?  And if I make that switch, will it kill the OS, like it does with Windows?

---

### Post by Nikas on 2009-01-11
> **gungfujoe said:**
> I'm using a Gigabyte GA-EP45-DS3L motherboard, which uses the Intel P45 north bridge and the ICH10 south bridge.  I've got a single WD6400AAKS (640GB hard drive) and an (empty) LG DVD drive attached to it.  The SATA controller is running in AHCI mode.

If the controller interface is the issue, might switching to legacy IDE mode do the trick?  And if I make that switch, will it kill the OS, like it does with Windows?

I did try do switch but the system got so slow. Not usable at all.

---

### Post by netslacker on 2009-01-12
I just resolved a similar issue.  While my solution may not help you it was aggravating nonetheless to fix.  For me, my system would randomly freeze up where it required holding the power button for a hard restart.  

The fix, as it were, was to move the box away from an area where people walked as the static electricity that was generated around it was enough to freeze the system.  Static was never a problem but now that winter is here and the humidity has dropped significanly it seems that everything in the house has a static charge.

To confirm static, all I did was walk over to the system and touch it.  A very light (insanely small) zap would occur but the system was immediately frozen solid.  Having a 4 yo running about only exacerbated the issue as everytime he touched it (which was often) the system was frozen.

At any rate, just a thought, it's not always something you're thinking of (obvious).

---

### Post by gungfujoe on 2009-01-17
> **netslacker said:**
> The fix, as it were, was to move the box away from an area where people walked as the static electricity that was generated around it was enough to freeze the system.  Static was never a problem but now that winter is here and the humidity has dropped significanly it seems that everything in the house has a static charge.

No one is near the computer when it freezes.  I'm not noticing any pattern; the crash that I mentioned above that was repeatable isn't (I've used add/remove a bunch of times now with no problem).  Some of the crashes have been when there's been no appreciable disk activity.  Watching live TV seems to cause the crashing pretty frequently, though, and that does involve disk activity.

Also, I think I can confirm that it's not the graphics drivers.  From reading around here, it seems that when people's graphics drivers cause freezing, the system still works, but the graphics do not.  I set up an SSH connection to the system from another computer, and as soon as the system crashed, the SSH connection stopped working, too.  When it crashes, the system is entirely nonresponsive.

---

### Post by gungfujoe on 2009-01-17
I think I've got a bad stick of memory.  MemTest86+ freezes part way through the test.  I'm now in the process of testing the sticks of RAM individually to determine which one is bad so I can start the RMA process.

With luck, this is the cause of my random freezing, and it'll be solved when I replace the RAM.

---

### Post by gungfujoe on 2009-02-15
I'm still not exactly sure what the problem is, but it's some combination of RAM and motherboard.  I replaced the motherboard (via RMA) after determining that the memory controller was bad, but the new one has the same problem.  It works fine with a different stick of RAM, and the "bad" RAM tests just fine in another motherboard.  Despite being on Gigabyte's list of compatible modules, it appears that these memory modules may not in fact be compatible with this motherboard.  I'm temporarily running this system with half of the RAM from my main system until I can figure out what's wrong and replace my new RAM with something that works (I'd just swap them, but my main system had 4GB, and I only bought 2GB for this machine - since it's a lower-end system serving HTPC duties, it doesn't need 4GB, but my main system does).

Regardless, this is not an Ubuntu issue, so this is more or less resolved.

---

