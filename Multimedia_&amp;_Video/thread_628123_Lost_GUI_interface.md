---
title: "Lost GUI interface"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by OctopusTwo on 2007-11-30
Hello

Ubuntu 7.10 froze while I was playing a really neat game.  I then restarted only to find my dual monitors were backwards (my right one was on left and the left was on the right).  No big deal I would just change it in the configuration menu.  After many attempts of changing the displays I found they remained the same.  (backwards)

So I thought I would try and "beat the software" I disabled my default monitor.  Logged out- logged back in... and I found myself in a text based OS.  I then decided to restart to see if that would fix the issue.   Well of course it booted into a text based OS- asking for my user name and password.  All of that works fine.

I looked at the forums here and other places to see if anyone else one into this issue.  I found solutions like try typing in sudo apt-get install xserver- xorg.  Other options to install ubuntu-desktop all of which I tried restarted the machine and I still did not have a GUI.

I notieced when I start up I get this "error message" kinit: no resume images during normal boot.  I found this forum to be interesting and will pursue it if you think this is the write direction.  
[http://ubuntuforums.org/archive/index.php/t-420337.html](http://ubuntuforums.org/archive/index.php/t-420337.html) 

Thanks for any or all your help.

---

### Post by PmDematagoda on 2007-11-30
Did you try:-
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by OctopusTwo on 2007-12-01
Yes that worked.  Thank you.  What exactly does the "-phigh" part do?  Thanks once again.

---

### Post by fenian on 2007-12-01
I think -phigh stands for priority high.

---

### Post by PmDematagoda on 2007-12-01
I don't know about the meaning of -phigh, but I can safely assume that it is not high priority:).

-phigh basically reconfigures the xserver with the default values, The problem in your case must have been that your xorg.conf was corrupted by the crash and cold reboot.

Might I suggest that you use Ctrl+Alt+Backspace to restart the Xserver and if that does not work, follow this [thread]("http://ubuntuforums.org/showthread.php?t=617349") on how to restart Ubuntu safely during a freeze.

---

