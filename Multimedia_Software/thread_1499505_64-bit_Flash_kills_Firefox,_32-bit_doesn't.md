---
title: "64-bit Flash kills Firefox, 32-bit doesn't"
date: 2010-06-02
forum: Multimedia Software
---

### Post by MattP220 on 2010-06-02
This one has me at a loss and I've not found any resolution, so the last resort is a help thread. 

The issue: I installed 10.04 yesterday, and there were no issues. I originally installed the flashplugin-nonfree package to install the regular Flash package. That worked just fine in both Firefox 3.6.3 and Chrome 5.

I'd previously installed the 64-bit Flash alpha from Adobe's site on 9.10, and that works just fine. I prefer it to the 32-bit version since it seems to leave my CPU alone. The 32-bit version on the other hand eats up a lot of processor cycles, so I'd rather avoid it if at all possible.

In any case, I installed it to 10.04 and it works...unless I try to open Gmail in Firefox. It works on Youtube and every other Flash-enabled site I've gone to, and I have no problems at all in Chrome. But Gmail will crash it every time. Opening FF in a terminal gives me a segfault, but with no prior warnings - FF just starts, then after a few seconds loading Gmail, the window vanishes w/ the segfault listed in the terminal.

I upgraded FF to 3.6.5 from the daily build repo, since that's what I'd used in 9.10, and same thing - crash when you go to Gmail. At that point, I opened the error console to see what was happening, and it was spitting out a whole slew of errors when loading Gmail. Unfortunately the console dies when the browser goes, so I haven't got a copy of that available. It appeared to be Javascript errors, but I dunno. 

I should also add that I've installed this from several angles - I tried a manual install, and then I tried to install from Adobe's repository. No go on either. 

Since I need to access Gmail, I uninstalled the 64-bit Flash for now and put the original flashplugin-nonfree package back in effect. Everything works fine, so it's tolerable for now, but I'd really be interested in a fix or at least more detail if this is a bug. 

Cheers!

---

