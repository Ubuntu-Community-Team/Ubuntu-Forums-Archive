---
title: "Gutsy Gnome Problems"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by ultralame on 2007-11-18
I have had a system that I have upgraded from Dapper all the way to Gutsy.  I had Gnome working under Feisty by running the Nvidia supplied installer.  I was not able to get compiz running, but gnome was OK (std graphics, sound).

I upgraded to gutsy and enabled the restricted drivers, but was unable to get anything to work.  I installed. reconfigured, and eventually removed nvidia-glx-new and ran nvidia-glx.  This appeared to test OK.

I restarted gnome.  The splash screen came up, with the system sound.  When I logged in, the cursor arrow came up and was responsive, but the screen remained blank (ubuntu beige, no icons, no progress, etc).  I had to kill gdm from a console.

However, I am able to log in as another user- with some issues...

-The splash screen has working sound.  But when I log in as that user, the session does not find a sound card.

-I can run compiz, but there are no window title bars.  So went back to standard effects, and things are working (other than sound).

-I deleted all the .gnome and .compiz folders I could find in my original account- but now when I log in it becomes a black screen.  The only thing I can do is hit CTRL-ALT-Delete and that brings up a working login/logout/restart dialog.

So...

The nvidia driver can obviously work, but my user settings must be hosed.  How can I reset my account?  How do I configure sound for the account that is working?  How do I get window title bars on compiz?

Thanks!

---

