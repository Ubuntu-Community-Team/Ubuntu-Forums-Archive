---
title: "Flash Problems"
date: 2009-01-19
forum: Multimedia Software
---

### Post by spvo on 2009-01-19
Hi,

I am having a few problems fixing my girlfriends computer running 32 bit Ibex.  The computer had suddenly starting acting crazy (programs crashing and restarting, custom changes disappearing).  Anyway, it was caused because she had filled the hard drive and there was no room for programs to write configuration files.  After freeing up space everything seemed to be working fine.

Now, however, flash is no longer working properly.  With video (youtube and livevideo.com) the flash player will start playing the video.  Then, suddenly and after a random amount of time (usually around 5 seconds) it will stop playing.  The progress bar jumps back to the start and the cached file disappears.  This happens on every tingle youtube video.  My computer (running on the same internet connection) plays the videos perfectly.

I have tried completely removing and reinstalling the flash player through synaptic.  I deleted both the .mozilla and .macromedia folder.  The problem still persists.  Does anyone know what could cause this?

John

---

### Post by gandaran on 2009-01-19
could be the /tmp directory is full due to amount of disk space available, try rebooting the computer to clear the /tmp folder.

---

### Post by spvo on 2009-01-19
I had already tried that too.  I freed up about 6 gigs of disk space on the computer and rebooted.  But the problem is still there.  Also, I created a new user and tried watching youtube with that account, but the problem was still there.  That would mean it has to be a system wide problem rather than just a problem with her user account.  Any other ideas?

---

### Post by gandaran on 2009-01-19
do you have a separate root partition and is it full? the /tmp directory is in the root file system not the home user account.
try these commands to clean up the file system and maybe release some space
sudo apt-get clean
sudo apt-get autoclean

---

