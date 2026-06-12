---
title: "EPG resolution"
date: 2008-10-29
forum: Mythbuntu
---

### Post by somersetsimon on 2008-10-29
Hi,
I've managed to get Mythbuntu working reasonably well. There's one thing I want to change - the resolution on the display for the EPG. Currently I can only see about 4 channels for about 4 time slots. Where would I go to change the resolution for this? Would this mean changing the resolution for the whole of MythTV? I tried to do this, but ended up screwing up my whole environment. I was left with a tiny window to look through that didn't cover the entire usable area, so I couldn't see what I was doing to revert back to default!

---

### Post by SiHa on 2008-10-29
Go to Setup - TV Settings - EPG (I think - it's there somewhere).
In the EPG menu,you can change the number of channels displayed and the number of 1/2 hr slots.
Elsewhere in the setup menus you can change the font size as well.

---

### Post by somersetsimon on 2009-01-02
Well I'm back onto MythTV again (my new big tv is arriving soon!) and still struggling with the look of the EPG. I can change the font and the number of segments, but the area for the channel id gets squashed up. Can I allocate more space for the logo? I've attached a screenshot to demonstrate my problem...

---

### Post by SiHa on 2009-01-02
You'd probably have to edit the theme files for that. On my setup, the file that contains the EPG definition appears to be /usr/share/mythtv/themes/blootube-wide/ui.xml.

I think there's a guide to creating themes on the Mythtv wiki, maybe that can point you in the right direction?

Don't forget to backup first!

---

