---
title: "Myth not obeying Schedules direct channel lineup"
date: 2008-10-07
forum: Mythbuntu
---

### Post by gndprx on 2008-10-07
This is getting to be a very frustrating issue.

Out of the several hundred DirecTV channels, there are only about 100 that I care about.  I have gone through Schedules Direct and deactivated every channel I don't want.

Every time mythfilldatabase runs to update my schedule information, it puts back in every single channel from the entire lineup.  So I have to spend 30 minutes every time mythfilldatabase runs going through and deleting all of the channels from the myth guide.  Until I do this, the mythweb portion is all but unusable due to so many programs being displayed.

Is there a solution to this?

---

### Post by newlinux on 2008-10-07
This isn't how it behaves for me. It doesn't add back in channels that I have deleted from Schedules direct... Maybe try getting your lineup like you want it in myth and then run:

mythfilldatabase --remove-new-channels

or try running mythfilldatabase with --update option.

---

### Post by Ronno6 on 2008-10-08
Have you tried to edit your channels available at the Schedules Direct website itself? You can disable entire sections at the click of a mouse, or select one-by-one. Then save the changes. I'm pretty sure that Mythfilldatabase won't "see" them anymore.

---

### Post by gndprx on 2008-10-08
I've already done that.  I've deactivated all of the channels in my linup except those I want at the schedules direct website.

I'll try the variations on mythfilldatabase tonight.

---

