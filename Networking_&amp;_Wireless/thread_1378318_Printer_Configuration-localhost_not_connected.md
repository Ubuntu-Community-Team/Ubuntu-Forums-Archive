---
title: "Printer Configuration-localhost not connected"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by sbrandon on 2010-01-11
Periodically after an update my connection to our network printer will disappear. I then go back to System/Administration/Printer and the New button is greyed/beiged out in the Printer Configuration-localhost dlog box and that it is "disconnected" down at the bottom of the box. I've tried 631 cups routed and there is no connection to localhost.  I was able to reconnect before but cannot remember what I found on the forum.  I would like to keep this connected so any help would be great.

---

### Post by Pavel.Niedoba on 2010-01-18
I have same problem here, thought my installation is very, keep on upgrading since 8.10, but I have same behavior here. There is absolutely nothing in log files /var/log/cups/*.log. I had no problem with printing before, don't know when this started. When I try to connect manually from ui, I get "There was an error during the CUPS operation: 'httpConnectionEncrypt failed'." Checking "require encryption" doesn't make difference.
   Ohhh, I tried "sudo /etc/init.d/cups restart" while typing this reply and it solves the problem!!
   Anybody knows how to do software clean print heads ?  from UI vould be best.

---

### Post by greatermold on 2010-07-28
sudo /etc/init.d/cups restart   --- worked for me.   Awesome quick fix.  THANKS!

---

### Post by brobry on 2011-05-15
when attempting to restart, i get [cupsd: Child exited on signal 15!                          [fail]]

what does this mean?

---

### Post by its1110 on 2011-12-25
cups restart

Yeah! WOOP De Doo.

WHY should we have to do this?!?!?

Does someone want to fix the basic problem?

---

