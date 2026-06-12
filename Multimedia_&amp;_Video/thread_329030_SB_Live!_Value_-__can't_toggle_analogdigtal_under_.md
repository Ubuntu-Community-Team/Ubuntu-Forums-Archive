---
title: "SB Live! Value -  can't toggle analog/digtal under X"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by johnpipe on 2006-12-31
I've had an unsolved sound problem with the SB Live! Value (CT4832) card and have finally identified a problem area.  This card is the one with five mini-jacks:  yellow [digital out], blue [line in] ,pink [mic in], green [speaker out], black [speaker 2 out].

The problem under X is that analog/digtal switch cannot be toggled, and is set to digital output (I have conventional analog speaker system), therefore sound cannot be played.

Under X.org, lspci -v gives:

```
-----------------------

00:14.0 VGA compatible unclassified device: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4832 SBLive! Value
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at dc00 [disabled] [size=32]
        Capabilities: [dc] Power Management version 1

00:14.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at e000 [size=8]
        Capabilities: [dc] Power Management version 1
--------------------------------
```

Note disabled I/O ports.

If I open a TTY, however, lspci -v shows the ports are not disabled, alsamixer comes up with digital disabled and analog enabled, and sounds can be played with aplay. I have also tested this under Vector Linux 5.8, which also uses X.org, and get the exact same behavior.

I don't know what is specifically causing this issue, but so far it  only shows up when X.org is running.

Johnpipe

---

### Post by johnpipe on 2007-01-01
I've been searching for the solution to this SB-Live! problem for some time (I believe it was a couple months or so back when I installed Ubuntu Edgy on a newly donated box, had sound problems and posted here). It looks like it may be a problem related to the MB chipset, causing X windows some confusion, and somehow it disables the analog/digital control port. I finally located a fix with setpci:

```
johnpipe:$ sudo setpci -s 00:14.0 COMMAND=5

johnpipe:$ !332
lspci -v

-----------------------------------------

00:14.0 VGA compatible unclassified device: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4832 SBLive! Value
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

00:14.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at e000 [size=8]
        Capabilities: <access denied>

---------------------------------------------------------------------


```I found this explained in this thread at [http://forums.fedoraforum.org/showthread.php?t=110144](http://forums.fedoraforum.org/showthread.php?t=110144)  after a lot of searching with clues from a response to a bug report for ALSA  (didn't turn out to be an ALSA bug).

The upshot of this is I now have sound working! :D :D :D

HTH, johnpipe

---

### Post by handy on 2007-01-01
Can you please post your motherboard maker & model info' for future reference?

Thanks :)

---

### Post by johnpipe on 2007-01-01
> **handy said:**
> Can you please post your motherboard maker & model info' for future reference?

Thanks :)

The MB is a DFI k6bv3+/66. This mfr. and 'K6b' series seems to be common to this problem. Has VIA VT82C596B and 82C598MVP chipset, and there may be a chipset bug at the root of the issue, since lspci  calls the SB card as a "VGA compatible unclassified device: ".

HTH, Johnpipe

---

### Post by johnpipe on 2007-01-01
NOTE:  The work-around command MUST be run under 'X'. The problem only happens when 'X' is running, therefore it won't have an effect from pre-'X' initialization scripts such as rc.local. 

If I knew what script to edit for 'X' initialization, I could add the command there. At present, I have to open a terminal and run the command (requires root permission, I use sudo) each time I login to the desktop. 

Does anyone here know which 'X' file this should be added too?

Thanks, Johnpipe

---

### Post by handy on 2007-01-02
You could write a script & have it run everytime you start your desktop.

This thread's first & third posts should cover it for you:

[http://ubuntuforums.org/showthread.php?t=245618](http://ubuntuforums.org/showthread.php?t=245618)

---

### Post by johnpipe on 2007-01-02
> **handy said:**
> You could write a script & have it run everytime you start your desktop.

This thread's first & third posts should cover it for you:

[http://ubuntuforums.org/showthread.php?t=245618](http://ubuntuforums.org/showthread.php?t=245618)

Thanks, but that is not the solution I need (and doesn't readily work for this, needs debugging in this particular case). This needs to be a system-wide fix, not an individual user command for every potential user. So this needs to be a system script that executes after X starts running, and before user login; I need to find where in this process to add a system command.

John

---

### Post by johnpipe on 2007-01-06
System wide solution found; see my post here:

[http://www.ubuntuforums.org/showthread.php?t=205449&page=45](http://www.ubuntuforums.org/showthread.php?t=205449&page=45)

---

