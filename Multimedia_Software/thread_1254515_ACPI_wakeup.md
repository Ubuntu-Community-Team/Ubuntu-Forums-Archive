---
title: "ACPI wakeup?"
date: 2009-08-31
forum: Multimedia Software
---

### Post by Mrazek on 2009-08-31
Hi all,

I tried to setup my testing machine with Mythbuntu (9.04) for waking up before scheduled recording and switching off after recorded. I used [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup). There is absolutely no problem to wake up using command line BUT there is a problem with MythTV. I used a setwakeup.sh script from [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) modificated by those lines:

echo I was here :-) >> /usr/bin/setwakeup.log
date >> /usr/bin/setwakeup.log

When I call setwakeup.sh from command line (for example "sudo setwakeup 12345678900") then to setwakeup.log are added those two lined from above. BUT when I schedule some recording in MythTV, switch off the PC and then switch on, no new lines in setwakeup.log are added (which means no script was called before shutdown).
I'm afraid this is a bug in MythTV? Or bug between chair and keyboard? :-)

---

### Post by comcute on 2009-09-23
You must execute mythshutdown -x to shut down the PC, not just shut it down.

---

### Post by Mrazek on 2009-10-21
OMG, it works, IT WORKS!! :)

Thank you bilion times! I used [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) solution but in "Integrate into mythTV" section is: Server halt command: sudo shutdown -h now :confused:

I spent about one year of testing. Really. Thanks once again.

---

