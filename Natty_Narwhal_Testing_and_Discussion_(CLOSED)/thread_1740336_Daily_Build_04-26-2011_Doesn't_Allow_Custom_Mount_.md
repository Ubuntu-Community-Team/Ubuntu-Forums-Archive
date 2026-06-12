---
title: "Daily Build 04-26-2011 Doesn't Allow Custom Mount Point?"
date: 2011-04-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by DevHead on 2011-04-26
With Beta 2, I could mount a partition on my hard drive to /namehere .  However, I haven't been able to do so with today's build.  I'm not sure how far back the daily builds have had this issue.

I used to be able to type in the blank field what mount point I want.  However, I can't do so now.  Is anyone experiencing this also?  TIA.

---

### Post by asasoft on 2011-04-27
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043)

---

### Post by DevHead on 2011-04-27
Thanks for the update. One day left until the official release.

---

### Post by asasoft on 2011-04-27
Workaround, copy and paste the custom mount point inside the text box works for me.

---

### Post by DevHead on 2011-04-27
Thanks.  That workaround works perfectly.

---

### Post by kansasnoob on 2011-04-27
One of you should ask at the bug report that work-around be added to the release notes.

Do you just create it in gedit and then copy-n-paste?

I'd kind of like to know :D

I did go ahead and add a bit to that bug report. Believe me, the installer-team has a dart board dedicated to me.

---

### Post by asasoft on 2011-04-27
@kansasnoob Do you just create it in gedit and then copy-n-paste?

Yes!

---

### Post by coffeecat on 2011-04-27
I don't know whether this is relevant, but there have been two daily builds of the desktop ISOs today, one set this morning (UTC) and one set timed 18:05 to 18:10. Considering that Evan Dandrea posted "fix committed" yesterday in that bug I wonder if the 18:10 ISOs include the fix.

I've just a few minutes ago zsync'ed to this afternoon's ISO but I'm too tired in this timezone to burn it to CD and try it this evening. Perhaps someone else will do the honours. :)

If not, I'll have a go in the morning.

---

### Post by kansasnoob on 2011-04-27
I opened the door for a release note:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043)

Just explain clearly how to do it :D

---

### Post by asasoft on 2011-04-27
From "Try Ubuntu" run the installer, alt+f2 run gedit , type your custom mount point , select and copy the text to paste in the installer.

From "Install Ubuntu" you can't alt+f2 or run gedit so, go to system settings type your custom mount point in the filter box, select and copy the text to paste in the installer.

I can't explain more clearly , my English bad.

---

### Post by DevHead on 2011-04-27
1. "Try Ubuntu"
2. Open gedit and type in your custom mount point /namehere
3. Highlight text /namehere using mouse
4. Install Ubuntu 11.04
5. At point of entry on the custom partition, middle click mouse button to paste what you highlighted in Step 3
6. Continue as usual with the rest of installation

That worked for me.

---

### Post by nm_geo on 2011-04-27
> **kansasnoob said:**
> One of you should ask at the bug report that work-around be added to the release notes.

Do you just create it in gedit and then copy-n-paste?

I'd kind of like to know :D

I did go ahead and add a bit to that bug report. **[COLOR=Black]Believe me, the installer-team has a dart board dedicated to me[/COLOR]**.

That is very true but we are so glad you have kept after them.. They really are too. Your efforts have made for a better product.

---

### Post by IanW on 2011-04-28
> **nm_geo said:**
> That is very true but we are so glad you have kept after them.. They really are too. Your efforts have made for a better product.

+1. If nobody filed bugs, we'd end up with Windows.

---

### Post by kansasnoob on 2011-04-28
It made the release notes:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043/comments/7](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043/comments/7)

> The manual mount point entry box in the desktop installer's partitioner does not accept keyboard input. The drop-down still works, so various standard mount points may be selected, but custom ones cannot. This was noticed too late to be corrected for 11.04. In the meantime, you can mount partitions manually later, or use the alternate install CD. (Bug:769043)

And since the bug report is linked they can also find asasoft's work-around :D

---

