---
title: "wicd - could not connect to wicd's D-Bus Interface"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by xenou on 2010-04-18
[FONT=Verdana]Today my wicd wireless connection gave me an error after 10 months of flawless performance, with a message about dbus.  At startup Wicd asked for my root password and then it display the following messages:  "Could not connect to wicd's D-Bus interface.  Check the wicd log for error messages".

In case anyone else runs into this problem, here's what I did.

1) Check /var/log/wicd for a log file.  The last line of the log file reported this error:
[/FONT]> [FONT=Verdana]ConfigParser.[/FONT][FONT=Courier New]ParsingError: File contains parsing errors: /etc/wicd/[/FONT][FONT=Courier New]wired-settings.[/FONT][FONT=Courier New]conf  [line 23]: '[]\n'[/FONT][FONT=Verdana]
[/FONT]
[FONT=Verdana]Okay, so then I opened up the file where the error was reported:[/FONT]
> [FONT=Courier New]sudo gedit /etc/wicd/wired-settings.conf[/FONT][FONT=Verdana]
[/FONT]
[FONT=Verdana]The last line of this file contained two empty brackets.  I hit backspace a few times to delete the empty brackets - also I did not leave an empty line at the bottom but backspaced to the end of the last line of the actual configuration settings.  Saved and closed.  Reboot (probably starting wicd would have been enough).  Back in business![/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]I hope this helps someone else.[/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by Gazoo01 on 2010-05-01
Thanks--I had the same problem, and your solution got wicd working for me again.

---

### Post by Ubunthree on 2010-05-10
Helped me too, exact same problem, thanks!

---

### Post by nicktids on 2010-05-10
Thanks this helped me as well.

Happened after I went from wireless to wired for a faster file transfer.  And then back to wireless and got the error above.

---

### Post by yozgoesdigital on 2010-07-15
Thanks for posting your solution. Got this problem already for some time and never took the time to solve it (sticked to windows)
It worked perfectly!

---

### Post by convoi on 2013-01-04
useful, thank you!

---

### Post by van hanegen on 2013-08-08
Well, just the same case with 13.04. But i'm a newbie. And, may be, that's why after inserting:
[FONT=Courier New]sudo gedit /etc/wicd/wired-settings.conf
[/FONT][FONT=franklin gothic medium]all i get is the blanc document.
So any adwise of wicd right installation would be appreciated[/FONT].

---

### Post by howefield on 2013-08-08
One of the dangers in replying to 3 year old threads, probably best to start a new one.

Thread closed.

---

