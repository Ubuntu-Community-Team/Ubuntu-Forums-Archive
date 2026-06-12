---
title: "weekly build 0.21-21064 - 8.04 LTS no menus?"
date: 2009-08-03
forum: Mythbuntu
---

### Post by carltondhouston on 2009-08-03
I hope to become famous for asking a stupid question.  Not really.

I upgraded to the latest weekly build on 8.04 LTS mythbuntu.  Now, no matter what theme I activate, I see no menus or pictures on the display.  I can set the theme in the database manually and the new theme will come up... things are all working and whatnot, but I cannot see what I am doing.  I see the theme background, just no words or pictures or what.

If I start up and just hit enter, the tv is displayed correctly.  From there, if I bring up the menu and select the guide, I can peruse the guide and select programs to record and whatnot as if nothing were wrong.

The no display of text and graphics occurs on mythtv-setup as well.

Did I miss something, or do I just need to wait on the next build for this to go away?  Hoping for a quick fix.

I am using an ATI Radeon RV100 in this machine for some reason.

If someone can help me get this corrected, I promise not to play in the unstable code anymore.  :)

---

### Post by klc5555 on 2009-08-04
> **carltondhouston said:**
> I hope to become famous for asking a stupid question.  Not really.

I upgraded to the latest weekly build on 8.04 LTS mythbuntu.  Now, no matter what theme I activate, I see no menus or pictures on the display.  I can set the theme in the database manually and the new theme will come up... things are all working and whatnot, but I cannot see what I am doing.  I see the theme background, just no words or pictures or what.

If I start up and just hit enter, the tv is displayed correctly.  From there, if I bring up the menu and select the guide, I can peruse the guide and select programs to record and whatnot as if nothing were wrong.

The no display of text and graphics occurs on mythtv-setup as well.

Did I miss something, or do I just need to wait on the next build for this to go away?  Hoping for a quick fix.

I am using an ATI Radeon RV100 in this machine for some reason.

If someone can help me get this corrected, I promise not to play in the unstable code anymore.  :)

Congratulations! You appear to have weekly-upgraded smack into the middle of the Dreaded Radeon Bug, previously only afflicting 9.04 users.

Escape into the desktop and see whether the frontend can be started in usable form from a console with:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend

If this works for you, you can automate it for Mythbuntu startup as follows:

The simlink /usr/bin/mythfrontend should be renamed /usr/bin/mythfrontend.old

In a text editor, start a new script "mythfrontend", which will be saved as /usr/bin/mythfrontend

This new script "mythfrontend" has one line, and invokes the simlink now called "mythfrontend.old" with the correct parameters you're using to run your frontend. In my case, this is:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend.old


After this, the little script "mythfrontend" is saved to /usr/bin/mythfrontend and then it is made executable: chmod +x /usr/bin/mythfrontend

And you ought to be OK.

---

### Post by carltondhouston on 2009-08-04
Will try this when I get home tonight and report back.

Of course you know with a fix this easy and quick (thanks) I'll have to reneg on my promise to stay out of the unstable code.

---

