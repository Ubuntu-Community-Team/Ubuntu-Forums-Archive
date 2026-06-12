---
title: "Mythgame not finding MAME roms"
date: 2010-12-29
forum: Mythbuntu
---

### Post by IceCap on 2010-12-29
I'm having problems with MythGame.  I installed SDLMAME and couple of roms to try on my system when running 9.10.  Later I upgraded to 10.04 and made couple of other changes/upgrades and in the mean time, MythGame stopped finding roms.
  I've cleared the game setup, checked all the paths (roms are in /var/lib/mythtv/mythgame/sdlmame/roms), checked the path in the mame.ini file, verified permissions, reinstalled MythGame, but nothing.  The game scan takes less than a second so there is something wrong there.  Which log should I look for to see what is going on?

  Thanks

  IC

---

### Post by IceCap on 2011-01-01
I figured it out.  In the setup of the game type the rom extensions can't be left blank.  They must have "zip,ZIP".

  IC

---

