---
title: "SiS 6296 vs. 2 versions of Ubuntu"
date: 2006-07-03
forum: Multimedia &amp; Video
---

### Post by DaveNF2G on 2006-07-03
I've spent all day on this and I still don't have any functioning version of Ubuntu.

Here's what I've done so far and the results:

1) Installed Ubuntu 5.10 from CD that came with the book, "Beginning Ubuntu Linux: From Novice to Professional" by Keir Thomas.  I set it up to dual-boot with Windows 98SE, where Windows owns the C and D drives and Linux owns what used to be the E drive.

2) Reconfigured x.org several times per instructions in the book after GUI failed to start.

3) Searched for latest drivers for SiS 6296 video card.  I have the latest drivers already.

4) Attempted to update Linux to Ubuntu 6.06.

4a) I couldn't use the built-in Linux update manager because it relies on the GUI, so I attempted to follow the directions at [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) for a manual update from the command line.  Command string starting with kdesu kate returned an error message about the command not being found or something like that.  Ditto for the string that starts gksudo "gedit.

4b) Ultimately, I ended up editing sources.list in vi (and learning a lot about using vi at the same time).

4c) Executed the command string sudo apt-get update && sudo apt-get dist-upgrade .  Lots appeared to happen on the screen - files downloading, files being extracted, files being replaced.

4d) GUI still didn't work, but when I rebooted and got the command line tty1 error message, it said I was still running version 5.10!

5)  Downloaded ISO image of version 6.06 desktop installer for the PC and burned it to CD-ROM.

6)  Removed Linux from computer and reinstated DOS/Windows partition and drive letter, restored MBR with fdisk.

7)  Booted from version 6.06 install CD.  First menu option is "Start or Install" - there is no install, only start.  It runs the live version on the CD-ROM but does not have any provision to install the distro to a hard drive.  Oh, by the way, when it tries to start up GNOME, the screen goes black and the computer freezes up solid.

As of this moment, I have NO Linux version installed on the computer at all.  I'm not willing to start over unless somebody can reassure me that Linux will eventually run.

Help!?!?!?!

---

### Post by DaveNF2G on 2006-07-06
Problem solved!

Additional research showed that I have the card that is notorious for being incompatible with Linux, so I got rid of it.  I was able to install Breezy with no problem, and upgrade to Dapper, using the video chip on the (Dell Optiplex) motherboard.

Guess I'll have to adjust my profile now.  :-)

---

