---
title: "iso and server"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by formol on 2009-02-02
hello everyone, 

I'm trying to make a domestic server.
All computer are running Ubuntu 8.04 (with last updates)

I've mount one share folder with something like
> sudo mount.smbfs //192.168.0.178/networkshare /home/formol/Videos/ISO

my goal is to put all my dvd-video in that folder and watch it from my main computer.

I've two things in this folder, an .iso and the folder of the extracted files of this iso, the video_ts.

so, when I try to open the directory in VLC, it do nothing.
when I try to mount the iso file with Gmount-iso, it says "An error occured Permission denied"

I was fully able to mount the .iso and watch it with the laptop of my flatmate (XP and deamon-tool).

did someone have a solution for me? with folder or iso file, or in any other way?

thank you

---

### Post by nixscripter on 2009-02-03
Use the Xine movie player (available in Synaptic package manager) and rather than mounting it, try providing a path to the ISO image directly:

```
xine "dvd://path/to/ISO/file.iso"
```

It will pretend to be a DVD in an imaginary player.

Hope this helps.

---

### Post by formol on 2009-02-03
nixscripter,

thank you for replying.

Someone (on the french forum of ubuntu) remember me that VLC can open iso files directly, which solved my problem.

so with VLC, I can open iso files directly from the mounted folder, and the dvd play well.

thank you again for replying.

regards,
formol

---

### Post by nixscripter on 2009-02-03
Glad to help. Please mark this thread as solved (under the Thread Tools menu).

(Oh, you did, my client was slow to update).

---

### Post by formol on 2009-02-03
I tryed to tag it "solved", it doesn't appear in the forum list
[http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")
> [ubuntu]   iso and server

---

