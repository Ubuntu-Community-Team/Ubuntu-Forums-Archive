---
title: "Mythbuntu 9.10 won't install"
date: 2010-03-21
forum: Mythbuntu
---

### Post by meanmrmustard on 2010-03-21
After installing the Karmic version on my frontend only machine I cannot connect to the backend - schema is 30 versions behind.

So I decide to install the 9.10 version on the primary machine.
Everything goes fine until it gets to the 30% point scanning disks and the screen begins flashing and goes no further.

I use the safe graphics mode as I have for every install but Karmic doesn't seem to be working out.


The message on screen actually says
 "getting time from a network time server" repeatedly followed by an increasing percentage. 
Once it reaches 30% there is an error:

[  125.532355] end_request I/O error, dev fd0, sector 0
[  137.700362] end_request I/O error, dev fd0, sector 0
30%: Detecting file system...


Anyone recognize the problem?
As a last resort I'll just go back to Jaunty on the frontend.

---

### Post by SiHa on 2010-03-22
It looks like it's looking for a floppy drive (/dev/fd0).
Only thing that springs to mind is that you don't have a floppy, but your BIOS thinks you have, and is passing that to the installer which then fails when trying to access it.

---

### Post by meanmrmustard on 2010-03-22
> **SiHa said:**
> It looks like it's looking for a floppy drive (/dev/fd0).
Only thing that springs to mind is that you don't have a floppy, but your BIOS thinks you have, and is passing that to the installer which then fails when trying to access it.


Thanks for the input - I'll see where that leads me.

---

### Post by superm1 on 2010-03-22
> **meanmrmustard said:**
> After installing the Karmic version on my frontend only machine I cannot connect to the backend - schema is 30 versions behind.

So I decide to install the 9.10 version on the primary machine.
Everything goes fine until it gets to the 30% point scanning disks and the screen begins flashing and goes no further.

I use the safe graphics mode as I have for every install but Karmic doesn't seem to be working out.


The message on screen actually says
 "getting time from a network time server" repeatedly followed by an increasing percentage. 
Once it reaches 30% there is an error:

[  125.532355] end_request I/O error, dev fd0, sector 0
[  137.700362] end_request I/O error, dev fd0, sector 0
30%: Detecting file system...


Anyone recognize the problem?
As a last resort I'll just go back to Jaunty on the frontend.

When this happens, is the system frozen?  If not, odds are you are running into an installer bug with your particular configuration of disks.

One really common thing is having dmraid configured on the disk once, but not removing the metadata.  From the live disk menu, press F6 and choose the 'nodmraid' option.  See if that helps.

If not, please run ubiquity in debug mode from a terminal:

```
ubiquity -d
```

When it hangs, open another terminal window and type this:

```
ubuntu-bug ubiquity

```
It will file a bug with all of the appropriate logs attached to it.

---

### Post by meanmrmustard on 2010-03-23
SiHa: yes the floppy was part of the problem. I disabled the boot up floppy seek and the floppy controller and the I/O error disappeared.



> **superm1 said:**
> When this happens, is the system frozen?  If not, odds are you are running into an installer bug with your particular configuration of disks.

I was able to get to another virtual terminal but it was flashing also.
The last three lines are:
30%: Getting time from a network time server...
30%: Scanning disks...
30%: Detecting file systems...

> 
One really common thing is having dmraid configured on the disk once, but not removing the metadata.  From the live disk menu, press F6 and choose the 'nodmraid' option.  See if that helps.

If not, please run ubiquity in debug mode from a terminal:

```
ubiquity -d
```

When it hangs, open another terminal window and type this:

```
ubuntu-bug ubiquity

```
It will file a bug with all of the appropriate logs attached to it.

The disk never had any raid configuration but I tried your suggestion - no help.

The text on the screen flashes seven times - the seventh time it pauses for 2 seconds during which I was able to access another terminal Alt+F1, etc.), otherwise it would not accept keypresses at all.

Booted into live mode to run ubuquity -d, I again chose safe graphics mode, it began the flashing again, the last line reads:
Starting init crypto disks...

BTW.. md5sum verifies the disk is ok.

---

