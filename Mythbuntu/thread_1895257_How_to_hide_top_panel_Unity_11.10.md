---
title: "How to hide top panel Unity 11.10"
date: 2011-12-14
forum: Mythbuntu
---

### Post by MickSulley on 2011-12-14
I now have Myth running successfully in Ubuntu 11.10 but I cannot get rid of the top panel.  I did manage it earlier with this info that I found - 

To get it to display without a top border
    Install CompizConfig Settings Manager
    Navigate to Utility then Workarounds
    Enable Legacy Fullscreen Support

But that no longer works!  I found a suggestion to make it transparent, but that doesn't help as the Myth window is not full screen, so I see a strip of desktop at the top instead.

Any ideas how to do this?

---

### Post by nickrout on 2011-12-14
> **MickSulley said:**
> I now have Myth running successfully in Ubuntu 11.10 but I cannot get rid of the top panel.  I did manage it earlier with this info that I found - 

To get it to display without a top border
    Install CompizConfig Settings Manager
    Navigate to Utility then Workarounds
    Enable Legacy Fullscreen Support

But that no longer works!  I found a suggestion to make it transparent, but that doesn't help as the Myth window is not full screen, so I see a strip of desktop at the top instead.

Any ideas how to do this?

did you install mythbuntu-desktop?

or get rid of compiz entirely, mythtv does not need a flash window manager.

---

### Post by MickSulley on 2011-12-15
I installed Ubuntu 11.10 clean and then installed MythTV etc on top.  I still have Unity desktop.

I did originally try Mythbuntu but had multiple problems with that, getting sound and display to work properly, it seemed that I needed to add so much stuff to get it all to work that Ubuntu made more sense.

---

### Post by nickrout on 2011-12-15
you haven't answered my question. 

I'll be clearer

```
sudo apt-get install mythbuntu-desktop
```

---

### Post by MickSulley on 2011-12-15
Sorry I misunderstood.  No I have not installed Mythbuntu desktop.  

Looking at it there are loads of other packages that need to be installed as well, is it likely to fix the problem if I install it?  Does that prevent the Unity desktop from working?

---

### Post by williammanda on 2011-12-15
The easiest way to have Mythtv and Ubuntu is to load Mythbuntu control centre. I have 11.10 and used the action you described to get rid of the top panel...I was the one who posted it.

---

### Post by nickrout on 2011-12-15
> **MickSulley said:**
> 
Looking at it there are loads of other packages that need to be installed as well, which ones?>  is it likely to fix the problem if I install it?  Does that prevent the Unity desktop from working?One would hope so, you really don't want unity on a myth box.

---

### Post by MickSulley on 2011-12-15
> **williammanda said:**
> The easiest way to have Mythtv and Ubuntu is to load Mythbuntu control centre. I have 11.10 and used the action you described to get rid of the top panel...I was the one who posted it.

I didn't have Mythbuntu control centre installed, just installed it and it makes no difference, still get the panel at the top of the screen.  I also tried disabling legacy fullscreen, then enable it again, plus reboot, still get the panel.
Have you got the latest updates?  I am pretty sure this worked until I ran updates a week or so back.

---

