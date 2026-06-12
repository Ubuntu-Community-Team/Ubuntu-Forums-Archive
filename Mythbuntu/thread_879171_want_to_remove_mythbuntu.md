---
title: "want to remove mythbuntu"
date: 2008-08-03
forum: Mythbuntu
---

### Post by Daverobb on 2008-08-03
How can I remove mythbuntu completely?  I'd rather switch back to ubuntu only as mythbuntu doesn't seem to run well on my older machine. Tried removing through synaptic and update but the backend setup and frontend icons still appear.

---

### Post by SniperKIng on 2008-08-04
Not sure if you have already tried this but you could firstly change the desktop environment to something else i think ubuntu is an option by going into the mythtv controll setup and the first tab.Then you could tell mythbuntu to not start mythtv at startup.

---

### Post by superm1 on 2008-08-04
Yeah once you turn off auto login, reboot, and then click "sessions" at the bottom.  Pick your gnome session.

---

### Post by barsofham on 2008-09-23
I was looking for the same thing you were. I just wanted it completely off my system as though I hadn't ever installed it. Keep in mind that I have very little experience in Ubuntu, so you might want to check that this is correct before you do it. What I did was use the same method of removing KDE that I had found which was to open up terminal and type ```
sudo aptitude remove kubuntu-desktop
``` except that I replaced kubuntu with mythbuntu. It removed several packages.

My next idea was to go to the synaptic package manager and search for "mythbuntu" and removed all packages that were for mythbuntu.

If you take this route, I recommend keeping a record of all packages removed so that if anything messes up you can figure out what went wrong. Everything went fine when I did it however.

Any feedback from anyone who is more adept at Ubuntu would be great.

---

