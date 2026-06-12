---
title: "Why is my home folder (and others) opened with Rhythmbox?"
date: 2010-09-26
forum: Multimedia Software
---

### Post by dkjMusic on 2010-09-26
Just started today playing with adding PanFlute applet to my top panel. I also downloaded the Desktop Art plugin for Rhythmbox and proceeded to install per instructions given on gnome-look.org. This involves some file copying to my home folder, soooo I click Places/Home Folder and low and behold it launches Rhythmbox which proceeds to scan my home folder, for music files I assume. The same thing happens when I open Documents, Pictures, and probably others I was too aggravated to try.

Questions are: what is going on and how do I revert to opening these folders in Nautilus?

---

### Post by mc4man on 2010-09-26
see here
[http://ubuntuforums.org/showthread.php?t=1581438](http://ubuntuforums.org/showthread.php?t=1581438)

---

### Post by prshah on 2010-09-26
> **dkjMusic said:**
> what is going on and how do I revert to opening these folders in Nautilus?

This is related to a known bug. To Fix: Open "Computer" from the Places location, (or just run nautilus from the Alt+F2 "command" box). Now, navigate to your home directory, then right click any directory within it, and choose "Open With"-"Open with other application"; in the box that pops up, choose "File Browser".

From now on, it will open correctly.

Here's another way you can try; System-Preferences-File Management. If you can't find that option, press Alt+F2, and run ```
nautilus-file-management-properties
```

Then click the Behaviour tab, and select the option "Always open in browser windows", then click Close.

Now perform the earlier method again, and see if it "sticks"

If that doesn't work as well, right click any directory in your home directory, then choose Properties-Open With-File Browser-Close. If the "File Browser" option is not there, click on Add and locate "File Browser". If you still cannot find the option, at the bottom of the "Add Application" window, click on "Use a custom command" and give the command as ```
/usr/bin/nautilus
```.

---

### Post by dkjMusic on 2010-09-27
Thank you both for the speedy replies.

Your info helped me fix the problem.

---

### Post by dkjMusic on 2010-09-27
Well, I had it fixed yesterday, and it reared its ugly head again today...this time with Banshee.

BUT, I think I figured out what I was doing wrong. I was going to a music folder, right-clicking Open With..., and selecting Banshee. What I didn't notice was the box at the bottom checked to 'Remember this application for "folder" files'. See the attached screenshot of the open With dialogue. Of course, unchecking this box preserves the Open default as Nautilus. So all is hunky-dory now, except that I feel kinda stupid for not paying attention.:confused:

Oh, so this really isn't a bug after all.

---

### Post by mc4man on 2010-09-28
> checked to 'Remember this application for "folder" files'

Excellent - i seem to remember in the past if it wasn't checked then the app wouldn't show up in the open with menu where you want it.
now it does whether the button is checked or not.
They should get rid of that button altogether - it serves no purpose but to mess things up.
(at the very least it shouldn't be checked by default.

---

### Post by dkjMusic on 2010-09-28
> **mc4man said:**
> They should get rid of that button altogether - it serves no purpose but to mess things up.
(at the very least it shouldn't be checked by default.

I agree wholeheartedly.

---

