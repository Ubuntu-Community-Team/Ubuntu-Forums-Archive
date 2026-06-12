---
title: "Front End in Full Screen still runs BEHIND Desktop Panels"
date: 2009-06-23
forum: Mythbuntu
---

### Post by Mattaus on 2009-06-23
I'm having a small problem that appears to be unique...

Even though I have MythTV set to full screen, when the Front end (in fact the back end does it as well) is running, it appears to be behind the desktop panels (the top and bottom bars in Ubuntu).

It is definitely running in full screen as the done, back and next buttons in any of the mythTV back end config menus are just visible poking out of the bottom bar. So I can use them but its very hard to see them. Its also quite annoying for a HTPC been able to see these bars sitting there. When I launch XBMC from inside the MythTV Front End, it has no problems running on top of everything - its only MythTV that does this.

I have fiddled with the screen offsets to no avail. 

Has anyone else had this problem or can some one point me to or suggest a list of things I can check?

Your help would be greatly appreciated.

- Matt

---

### Post by DominicF on 2009-06-23
Hi,

I had this issue as well.  It ticked me off so much!!!

Can't remember exactly how I solved it... at the time it was a fresh install on new machine and didn't mind restarting. I started with Mythbuntu distro and saw the problem and then I wiped the hard disk and installed Ubuntu followed by the the Mythbuntu Control Centre (add/remove apps) and then it looked better.

But before you do that maybe start by checking the System -> Appearence menu from the ubuntu desktop and make sure Effects are set to None.  I noticed some time later if I had effects enable the ubuntu desktop menu would show through the Mythtv gui.

Hope that helps.

---

### Post by Mattaus on 2009-06-23
Unfortuantely I have tried all that - I really cannot figure out what the fudge is going on here...

I have however realised that I was going to try and run this all without any window managers in the final build - so losing my cool over this may not even be needed. I have a script and some instructions on how to get Ubuntu to boot and only display XBMC, so I'm going to try and modify it to run MythTV front end on start up, and when I click "Media Library" it will launch XBMC.

I have the menus edited correctly, I just need to work on the X side of things.

I'd still love to know what MythTV is doing this however, and why every normal solution out there (short of reformatting) does not solve my particular case!

---

### Post by GCFreak on 2009-06-24
Yeah, that is the fault of Compiz. Install the CompizConfig Settings Manager, go down to Utility -> Workarounds, and enable "Legacy Fullscreen Support". That will fix that issue.

---

### Post by Mattaus on 2009-06-25
So even if I right click on the desktop, and select effects (or what ever it is called) and select "none" it won't fix it? I obviously must install CompizConfig Settings Manager?

I guess it's not actually that important now that I tell ubuntu not to laod and window managers on start up...

---

### Post by GCFreak on 2009-06-26
That should fix it as well, but it obviously disables all the other Compiz effects.

---

### Post by HyRax on 2009-07-06
> **GCFreak said:**
> Yeah, that is the fault of Compiz. Install the CompizConfig Settings Manager, go down to Utility -> Workarounds, and enable "Legacy Fullscreen Support". That will fix that issue.

It's not really a fix as such, just a temporary workaround, because enabling legacy support will cause the MythTV displayed video to occasionally flicker when scrolling windows or terminals, etc.

---

