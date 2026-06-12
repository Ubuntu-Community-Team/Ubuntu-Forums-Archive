---
title: "mythwelcome not launching after upgrade"
date: 2013-02-14
forum: Mythbuntu
---

### Post by se99paj on 2013-02-14
I've just completed an upgrade on my mythbuntu setup, is been quite a few years since the last big upgrade so thought it would be a good idea.
The upgrade went fairly smoothly apart from one issue with myth welcome.
Before the  upgrade mythwelcome worked fine, but now after a restart the desktop appears but mythwelcome doesn't start, it will turn off if no recordings are going to occur and if the front end is not running.

---

### Post by JasonEde on 2013-02-16
When it starts up and although it looks like nothing has started then try pressing i on keyboard to see if the config screen appears. If it does then try just clicking on finished.

---

### Post by *drew on 2013-02-18
I've had similar problems with mythwelcome.

I found that having the mythwelcome option "Automatically Start Myth Frontend" enabled, caused mythwelcome to "vanish" after quitting the mythfrontend GUI.

uSING Alt+Tab enabled me to find it again.

This option is enabled by default in a new install (not sure about an upgrade).
It can be disabled from the 2nd mythwelcome configuration screen.
To access the 2nd configuration screen, press "i" or "info".

Also, it might be worth checking that the MYTHWELCOME line is un-commented in etc/mythtv/session-settings. It may have been overwritten in the upgrade.

---

