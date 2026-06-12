---
title: "Clicking maximise freezes the desktop (unity, intel GMA graphics)"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-08
Happens with: gnome-terminal, firefox, evince
Steps to reproduce: Open gnome-terminal, firefox or evince. Click the maximise button. The desktop freezes completely and the only way to restore it is to enter a virtual terminal and do service gdm restart.

EDIT: Also confirmed with banshee, shotwell and a bunch of non-packaged and manually compiled programs. In fact, the only two programs that I've observed maximising normally so far are nautilus and gedit.

---

### Post by rlklee on 2011-04-08
Did you recently update/upgrade? 

Also: if so, did you dist-upgrade, safe-upgrade or upgrade?

---

### Post by PaulW2U on 2011-04-08
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Happens with: gnome-terminal, firefox, evince
Steps to reproduce: Open gnome-terminal, firefox or evince. Click the maximise button. The desktop freezes completely and the only way to restore it is to enter a virtual terminal and do service gdm restart.
Yes. I'm getting this too but with cream, the gvim add-on. It started immediately after downloading today's updates.

---

### Post by rlklee on 2011-04-08
> **PaulW2U said:**
> Yes. I'm getting this too but with cream, the gvim add-on. It started immediately after downloading today's updates.

Did you dist-upgrade or merely upgrade?

---

### Post by PaulW2U on 2011-04-08
> **rlklee said:**
> Did you dist-upgrade or merely upgrade?

My current installation dates from last weekend and I have always used **aptitude safe-upgrade** to update/upgrade it.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-08
Same here, this installation is a couple days old and I've only used aptitude safe-upgrade.

---

### Post by rlklee on 2011-04-08
Well, same behavior here. Intel chip as well. My main culprit when maximizing is Emacs.

---

### Post by PaulW2U on 2011-04-08
Now this is a strange bug!

I was going to report that the problem had fixed itself as I could start cream, maximise it and minimise it without Unity freezing. I could even log out and back in again and maximise and minimise cream without Unity freezing. But, if I reboot, log-in, start cream and try to maximise it then Unity freezes.

[By the way I am using, AltGr-K-SysRq to force a log out]

Very odd. :confused:

---

### Post by rlklee on 2011-04-08
> **PaulW2U said:**
> Now this is a strange bug!

I was going to report that the problem had fixed itself as I could start cream, maximise it and minimise it without Unity freezing. I could even log out and back in again and maximise and minimise cream without Unity freezing. But, if I reboot, log-in, start cream and try to maximise it then Unity freezes.

[By the way I am using, AltGr-K-SysRq to force a log out]

Very odd. :confused:

I am getting very inconsistent behavior as well. The bug pops up across a range of unrelated applications without rhyme or reason. Was just emacs at first for me, but now it's elsewhere. 

I was using the unity desktop and have switched to classic to see if the problem persists here. Hopefully not.

---

### Post by rlklee on 2011-04-08
> **rlklee said:**
> I am getting very inconsistent behavior as well. The bug pops up across a range of unrelated applications without rhyme or reason. Was just emacs at first for me, but now it's elsewhere. 

I was using the unity desktop and have switched to classic to see if the problem persists here. Hopefully not.

Update to this. No maximize/freeze behavior on Classic Desktop yet. Been an hour of constant use.

---

### Post by rlklee on 2011-04-08
Any further understanding of this?

Edit: Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/754063"). Fix has apparently been committed.

Edit 2: For those wondering, the report above has been updated and claims the fix will be rolled Monday.

---

