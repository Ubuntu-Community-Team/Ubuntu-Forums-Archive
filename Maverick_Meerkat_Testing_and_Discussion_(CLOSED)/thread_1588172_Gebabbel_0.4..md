---
title: "Gebabbel 0.4."
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by _sAm_ on 2010-10-04
Trying to transfer Tracks/Way-points from a Garmin GPS device with Gebabbel(version 0.4 from repo) on Maverick, but I get an error message. It worked on Lucid. 

When I copy the command from Gebabbel and run it in a terminal with "sudo" in front it works fine. I don't know why my user cant get it, only root?

---

### Post by cariboo on 2010-10-04
Could you post the error message you're getting, it would help in diagnosing the problem.

---

### Post by _sAm_ on 2010-10-05
Sure:

> A problem was detected by gpsbabel. 

The orginal error message reported by gpsbabel was:
Claim interfaced failed: could not claim interface 0: Opertation not permitted.

If I start Gebabbel from the terminal and run the "Execute" button the output (in the terminal) is: > QProcess: Destroyed while process is still running. 

In Gebabbel I go to Edit > Edit command and copy it to a terminal, enter sudo in front and run it I get the track just fine(but I have to change the Permissions(owner) from root to my user to use it).

---

### Post by cariboo on 2010-10-05
I just installed gebabbel, it starts and runs the way it should as far as I can tell with no errors, starting in a terminal doesn't display any messages.

---

### Post by _sAm_ on 2010-10-05
So you can transfer tracks from a GPS with it?

---

### Post by cariboo on 2010-10-05
Not unless I run the program as root, it seems to be a permission issue. I'm looking at [this]("http://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux") to see if I can resolve the issue.

---

