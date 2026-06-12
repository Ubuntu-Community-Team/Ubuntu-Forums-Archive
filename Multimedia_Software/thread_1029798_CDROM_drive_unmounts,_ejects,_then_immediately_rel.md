---
title: "CDROM drive unmounts, ejects, then immediately reloads!"
date: 2009-01-03
forum: Multimedia Software
---

### Post by roachk71 on 2009-01-03
As the thread title says, when I try, in any application (including Nautilus and MythTV) to simply eject an audio CD, the system immediately closes the tray and tries to reload the disc!

Is there any way at all to disable this behavior? It creates unnecessary wear and tear on the drive.

---

### Post by mc4man on 2009-01-03
Assuming your using 8.10 that was a bug fixed awhile ago, are you updated?

If so and it still occurs you can edit a persistent rules file in udev, on 8.04 atm so can't paste in.

---

### Post by roachk71 on 2009-01-03
It would seem this bug hasn't been fixed; My computer is fully updated and the problem persists... ](*,)

I'm looking for a persistent rules file right now...

---

### Post by mc4man on 2009-01-03
The package that contained the bug fix is udev (124-9)  (intrepid updates

 ck. in synaptic to see if it's installed (orig. was udev (124-8)

---

### Post by roachk71 on 2009-01-05
The installed version is current (124-9).

I've managed to find a workaround, though; logging into a Mythbuntu session gives me a basic XFCE session, without the problem rearing its ugly head (it would appear to be a GVFS bug instead.) :-\"

---

### Post by mc4man on 2009-01-20
@ roachk71

I just installed 8.10 on my main box, during the course of updates it updated udev to 124-9 and nothing changed, still auto retracted.

If you still need/want to fix, search udev in synaptic, highlight it and in the packages tab choose 'force version' and select 124-8.

When it's done close out synaptic (you'll probably get a pop up, when you force a lower version synaptic will automark it for upgrade.)
 Choose discard changes, reboot and then upgrade udev to the 124-9 ver. It should work the second time around.

---

