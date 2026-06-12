---
title: "Persistent network monitoring?"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by wujj123456 on 2012-06-16
I am recently looking for some bandwidth analyzer tools, and found bandwidthd and darkstat to be very useful, especially the darkstat's graphs.  However, I can't configure either of their data to survive reboots.  A "service darkstat restart" wipes out previously recorded data.  

I've also tried using "--chroot /var/lib/darkstat --export history.db --import history.db" options for darkstat.  Despite what promised in the man page, darkstat is not importing previously recorded database.  

I'd like to know if anyone has any good luck in setting up a network analyzer similar to bandwidthd/darkstat to monitor usage across reboots.  Or is there any options I can use to save data across reboots for dartstat? 

Thanks.

---

