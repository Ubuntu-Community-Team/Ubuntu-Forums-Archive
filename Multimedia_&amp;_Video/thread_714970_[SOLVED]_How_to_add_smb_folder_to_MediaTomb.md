---
title: "[SOLVED] How to add smb folder to MediaTomb"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by kbailey on 2008-03-04
I’ve got MediaTomb up and running perfectly on one of my Ubuntu boxes with my D-Link DSM-520 (far better and faster than the MS-based software the unit ships with).

Unfortunately, I cannot seem to find a way to add my network-shared (FAT 32 network enclosure set up as smb server) media folder through the MediaTomb web-based GUI.

I’ve created “Places” bookmarks for the folders on my NAS that work perfectly as smb shares, but cannot seem to get any of these to show in the MediaTomb GUI.

They can be accessed via an ip address on my network, though adding them as a “link” in the MediaTomb GUI does not work because a “link” needs to point to a specific media file. Adding the folder to the database as a “container” does not work either because it does not allow for any scan or update options.

Is there a place in the MediaTomb GUI “PC Directory” where I can find these “bookmarked” and mounted drives? If I can add just the one folder and set it to scan recursively, I will be a very happy fellow!

Thank you in advance for your suggestions.

---

### Post by kbailey on 2008-03-05
I found the solution to this rather minor dilemma. I used Synaptic to install smbfs then edited /etc/fstab to mount the drive in my home folder on startup. Of course, the drive is now visible in the MediaTomb GUI.

Just mounting the drive using the "Connect to server" feature in "Places" did not actually mount it anywhere visible to MediaTomb.

Thanks to everybody who looked and even attempted to figure out what the heck I was talking about.

Oh yes, and thanks to dbott67 for the great how-to on mounting smb shares here:
[http://ubuntuforums.org/showthread.php?t=280473]("http://ubuntuforums.org/showthread.php?t=280473")

---

