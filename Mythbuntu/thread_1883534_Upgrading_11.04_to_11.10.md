---
title: "Upgrading 11.04 to 11.10"
date: 2011-11-19
forum: Mythbuntu
---

### Post by jamoody on 2011-11-19
I'm new to Ubuntu and have been running Mythbuntu 11.04 with MythTV 0.24 for a month now.  I'm getting notices to upgrade to Oneiric (11.10).  Several questions:
1) is it safe to MythTV to upgrade by simply clicking on the notification panel or via Alt+F2 update-manager -d?
2) is there any significant advantage to upgrading to Ubunutu 11.10?
3) is it best practice to apply Mythbuntu fixes and Ubuntu upgrades as they come along or leave well enough alone?
 
Thanks.

---

### Post by nickrout on 2011-11-19
> **jamoody said:**
> I'm new to Ubuntu and have been running Mythbuntu 11.04 with MythTV 0.24 for a month now.  I'm getting notices to upgrade to Oneiric (11.10).  Several questions:
1) is it safe to MythTV to upgrade by simply clicking on the notification panel or via Alt+F2 update-manager -d?
2) is there any significant advantage to upgrading to Ubunutu 11.10?
3) is it best practice to apply Mythbuntu fixes and Ubuntu upgrades as they come along or leave well enough alone?
 
Thanks.

Do NOT upgrade. There are plenty of posts on here of disasters in doing so. 

It is safe to update your mythtv and general ubuntu packages within 11.04, just don't go to 11.10. Use mythbuntu-repos to stay up to date with mythtv.

---

### Post by romanyiv on 2011-11-20
I did a fresh install of mythbuntu 11.10....no gui when it booted.  After purging nvidia drivers (I also followed some other steps defined in another thread in this forum) I got my desktop back.  My system is fairly simple so not a big deal to re-configured (you should be able to import your backup of your DB).   I did this hoping that some issues  I had with LIRC would be fixed (hope springs eternal for linux users).  In my case it was sucessful (I have a HD-PVR connected to a cable settop box controlled by external IR transmitter).  

In any case get familar with clonezilla.  Great program - if you screw up you can go back to the original system.   I have 2 drives - a 320G OS and 1T for recordings - I clone only the OS drive - takes me about 15 minutes to flip back....I did this more than once - my upgraded failed (no gui).  Perhaps knowing what I do now I could have fixed it.  At the time I did not know that the system was on the nextwork and ssh was still working (console was not).  I cursed a lot - swearing I was finished with mythtv and esp. Ubuntu.  I'm still hanging on - so far the system is working pretty well...

---

### Post by jamoody on 2011-11-21
That's what it looked like to me too, but thought I'd check anyway since forums tend to show the negative side.  It's a rare post that says everything is going great :-)  Thanks for the confirmation, I'll wait.

---

### Post by romanyiv on 2011-11-21
Another comment on running 11.10.  My "office" pc is the normal ubuntu distro - I use it for pretty much all of my pc stuff (virtualbox when I have to run windows apps).  I had been running 2 versions behind (easy to do as often as ubuntu changes).  Anyway my mythfrontend client (from the normal package channels) had 2 issues that bugged me - one was I did not have an option to do a PIP - the other I prefer portrait mode - but the mythfrontend was always funky in that mode - even when having the geometry correct.   I upgraded the pc tonight - no issues - booted up normally.  The newer mythfrontend client now has the PIP button - and I can run the client with in portrait mode and the correct "letter box" format.  Very happy with the results.   One last point - I use Nvidia - running portrait always invovles making manual changes to xorg.conf - under 11.10 you can make that change from the desktop now.

---

### Post by guimaster on 2011-11-28
> **nickrout said:**
> Do NOT upgrade. There are plenty of posts on here of disasters in doing so. 

It is safe to update your mythtv and general ubuntu packages within 11.04, just don't go to 11.10. Use mythbuntu-repos to stay up to date with mythtv.

 Canonical better not show an upgrade button by default in 12.04 LTS. Nothing could be worse for a new user than to accidentally click upgrade. What is the point of an upgrade feature in every Ubuntu version, if it seldom works properly?

---

