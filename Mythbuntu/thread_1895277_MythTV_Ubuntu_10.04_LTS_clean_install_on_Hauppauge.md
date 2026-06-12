---
title: "MythTV Ubuntu 10.04 LTS clean install on Hauppauge HVR 4000"
date: 2011-12-14
forum: Mythbuntu
---

### Post by petatkinson on 2011-12-14
I'm starting a new thread after 9 reinstalls and still no working MythTV.Thanks to all who have helped but I've had so many different results from reinstalls and noticed that the system became unstable the further I progressed.

I have now reinstalled 10.04 LTS and am now asking what are the best steps to take to get a running MythTV system.From experience the least "extras" I install the better the chance I have of success.

I have to date managed to get Kaffeine scanning and storing channels so I know the steps up to that point.Is it necessary to install Medibuntu at any stage?.

Any help on the above would be greatly appreciated.

---

### Post by petatkinson on 2011-12-15
Ok so a little investigation and a few more reinstallations later I have come to the conclusion that it is the firmware from "Ubuntu firmware non free" that may be the problem.I noted from a previous post that when you set the LNB under Diseqc and escape back to the main menu and return to the Diseqc option the LNB option has returned to "unconnected".It was suggested that it was a bit flaky but to keep trying.I think that it is in fact being turned off when you exit that menu.Could anyone confirm that the current "Ubuntu firmware non free" is stable or could you suggest another source for it.There is a link to WinTV CD for Hauppauge HVR4000 drivers on MythTVTalk forum but unfortunately the link is broken.

---

### Post by nickrout on 2011-12-15
> **petatkinson said:**
> Ok so a little investigation and a few more reinstallations later I have come to the conclusion that it is the firmware from "Ubuntu firmware non free" that may be the problem.I noted from a previous post that when you set the LNB under Diseqc and escape back to the main menu and return to the Diseqc option the LNB option has returned to "unconnected".It was suggested that it was a bit flaky but to keep trying.I think that it is in fact being turned off when you exit that menu.Could anyone confirm that the current "Ubuntu firmware non free" is stable or could you suggest another source for it.There is a link to WinTV CD for Hauppauge HVR4000 drivers on MythTVTalk forum but unfortunately the link is broken.

You don't "escape", because that is the equivalant of "cancel", move to the next screen with "next" or "finish".

I know of no reason why the ubuntu package for the firmware would not be correct.

---

### Post by petatkinson on 2011-12-16
Ok so there should be no reason why MythTV shouldn't work if I download "Ubuntu firmware non free" and then do the install from Mythbuntu as "Install to a current Ubuntu Desktop". I will follow this path again for the twelveth time and see what happens.

---

### Post by nickrout on 2011-12-16
> **petatkinson said:**
> Ok so there should be no reason why MythTV shouldn't work if I download "Ubuntu firmware non free" and then do the install from Mythbuntu as "Install to a current Ubuntu Desktop". I will follow this path again for the twelveth time and see what happens.

The package is linux-firmware-nonfree.

I suspect the problem may be the way you are escaping out of the LNB setup, from what you said earlier.

And update to the latest 0.24-fixes from mythbuntu-repos right at the outset.

---

