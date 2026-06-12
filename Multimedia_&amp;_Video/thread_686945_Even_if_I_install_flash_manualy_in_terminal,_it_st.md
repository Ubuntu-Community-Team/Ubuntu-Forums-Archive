---
title: "Even if I install flash manualy in terminal, it still won't work..."
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by diablo75 on 2008-02-03
I'm trying to get Flash installed on someone's computer who just started with a fresh copy of Gutsy (32-bit processor).

We've tried downloading the tar file from Adobe's website, extracting, then running the installer sudo... the only part about this I could imagine the problem cropping up is the path name, where it says something like, "Please enter the path name to your browser (e.g., /usr/lib/mozilla/)  and I would type in /usr/lib/firefox/

I recently ran across a tutorial for linux in general (not specific towards ubuntu) that said the path name should be /home/$username/.mozilla/   (Would that work??)


I've also tried doing a sudo apt-get install flashplayer-nonfree.  No good.

I've also see the automated script within firefox appear, and fail.

So, how do we install flash into firefox on Ubuntu Gutsy these days?

---

### Post by gandaran on 2008-02-04
see this [http://ubuntuforums.org/showthread.php?t=686624](http://ubuntuforums.org/showthread.php?t=686624)

---

### Post by MrClearPore on 2008-02-04
> We've tried downloading the tar file from Adobe's website, extracting, then running the installer sudo... the only part about this I could imagine the problem cropping up is the path name, where it says something like, "Please enter the path name to your browser (e.g., /usr/lib/mozilla/) and I would type in /usr/lib/firefox/

When you're running the installer, run it as a regular user, not as root.  Running as a user, the installer will pick the user's plugin directory automatically, and all the user has to do is accept the default prompts.  The Flash plugin will be copied to **~/.mozilla/plugins** unless specified otherwise by the user.

---

### Post by ellalan on 2008-03-09
I solved this problem by removing any existing" Flash plugins-nonfree" in the Synaptic Package Manager and following the instruction from this link: [www.psychocats.net/ubuntu/flashmanual](www.psychocats.net/ubuntu/flashmanual).
HTH

---

