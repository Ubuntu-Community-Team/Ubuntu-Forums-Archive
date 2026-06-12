---
title: "Terminal failed to open"
date: 2010-09-03
forum: Mythbuntu
---

### Post by bcg30506 on 2010-09-03
I ran into a problem last night that I've never seen happen in 10+ years using Linux.  I lost the ability to ssh into my box.  Rather, I was able to connect via ssh but then it would immediately terminate the session with no other information.

So then I VNC'd in (this is my living room PVR that has no keyboard on it so I ssh or vnc for maintaining it) and was able to connect fine that way.  From there on the xfce desktop (running mythbuntu 10.04), I tried to open a Terminal from the Applications menu.  Nothing happened.  The screen flickered like it tried to open a window and failed then returned me to the desktop.

After Googling, it seems the failure was the shell was not able to be created.  I use Bash by default but also installed csh via synaptic and tried to create a shell with it via ssh.  That also failed.  From reading about others with similar issues, I decided to reboot.  After reboot, all is well again.  I can open a Terminal from the desktop and I can also ssh in as before.

So now I'm worried there is a time bomb on my PVR machine.  Does anyone know what may have happened to cause this?  Is there anything I need to check?  Can I do something to prevent this in the future?

Thanks!

---

