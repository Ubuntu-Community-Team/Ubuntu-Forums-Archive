---
title: "mythnetvision not loading sites"
date: 2010-11-13
forum: Mythbuntu
---

### Post by iitywygms on 2010-11-13
Hi all.
Running mythbuntu .24-fixes from the autobuilds.  running on 10.04
Have everything working well except mythnetvision.
Seperate frontned backend.  
While on my frontend, I choose Browse internet video.
I then have the hulu option showing, along with The WB.
I highlight hulu, press menu and select scan/manage subscriptions.
Then I choose Update Site Maps.  It flashes "loading"  for about a second, then exits back to where I have the option of choosing hulu or The WB.
Now when I highlight hulu, and press enter nothing is available.
Not sure what I am missing, or what is wrong.  I have searched my butt off but cannot find the missing link.
I do have a RSS feed working from the discovery channel that I manually setup.
Any thoughts?

---

### Post by iitywygms on 2010-11-14
Anyone?

---

### Post by iitywygms on 2010-11-16
well I have a clue.  
my /usr/share/mythtv/mythnetvision does not contain a scripts directory!
it has a icons directory but no scripts.
How the heck I get that installed?  I tried to purge and reinstall but nothing shows up.

---

### Post by iitywygms on 2010-11-17
Today's update 11/17/2010 fixed it. :)

---

### Post by joojar on 2010-11-22
> **iitywygms said:**
> Today's update 11/17/2010 fixed it. :)

I have the same problem, but none of the updates have fixed it so far.

My installed Mythnetvision package shows up as: 1:0.24.0+fixes27315-0ubuntu0+mythbuntu1

So do I need to wait for the fixes to propagate via Mythbuntu-repo?

---

### Post by joojar on 2010-11-23
> **joojar said:**
> I have the same problem, but none of the updates have fixed it so far.

My installed Mythnetvision package shows up as: 1:0.24.0+fixes27315-0ubuntu0+mythbuntu1

So do I need to wait for the fixes to propagate via Mythbuntu-repo?

nm, my Mythnetvision scripts were installed fine (in /usr/share/mythtv/internetcontent) - the real problem was I hadn't realised the scripts were now run in the backend, and my backend wasn't running.

---

