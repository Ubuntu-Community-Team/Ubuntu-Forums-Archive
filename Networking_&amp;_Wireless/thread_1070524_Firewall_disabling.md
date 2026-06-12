---
title: "Firewall disabling"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by NSAJEFF on 2009-02-15
Notes:

Was running Ubuntu 8.10 - problem began
Upgraded to 9.04 - problem persisted(not a clean install, just an upgrade).

I was tinkering around with GUI firewalls and installed Firestarter and UFW. I promptly removed Firestarter and noticed I couldn't get online. Figured no biggy, I'll see if UFW is being difficult and fix the rules. Got stuck tinkering and simply disabled it.

Problem solved, I could get online...but only for 10-15 minutes at a time then I would have to disable it again. Same issue with any firewall software. Removed UFW and reinstalled Firestarter and still only able to get online if I disable the firewall. Also used ipkungfu. Its gotten to the point where I set up a cron job to run ipkungfu -d every 15 minutes...

Please help.

---

### Post by NSAJEFF on 2009-02-15
Bump...running cron is not an ideal solution for me.

---

### Post by superprash2003 on 2009-02-15
remove both ufw and firestarter and flush your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

### Post by NSAJEFF on 2009-02-15
> **superprash2003 said:**
> remove both ufw and firestarter and flush your iptables [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

Thank you kindly for that! Solved the problem. I really need to sit down and read through my 'Linux Firewalls' book. Thanks again.

---

