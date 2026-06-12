---
title: "KDE logout issue"
date: 2011-02-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ft_ on 2011-02-19
Hi,

When I log out from Kubuntu (upgraded from Maverick), KDE often hangs roughly 5 seconds before logging out. Sometimes, no KDE log out works, and I have to sudo poweroff in konsole.

My net search showed me it seems to be a KDE-related (akonadi ? phonon ?) issue, not only a Kubuntu one.

Any solution ? Thanks !

---

### Post by ft_ on 2011-03-12
Logout issue seems to be akonadi-related. (akonadi_agent_launcher logout bug is maybe related too ?)
So I checked in ~/.xsession-errors, and I found that lancelot plasmoid use akonadi. Thus I have deleted lancelot and switched to kickoff.
Akonadi is not launched by default, lancelot was the app which called akonadi. Right now I do not get any akonadi instance launched, since I turned off lancelot.

Lag on logout seems to have vanished in kde.

---

