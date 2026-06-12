---
title: "Can't connect to router any longer."
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by mrbiggbrain on 2009-09-13
I built a UT99 server yesturday and proceeded spending the day setting it up and configureing everthing.

I installed:

ut99 server
abyssws webserver
SSH
FTP
and configured all my ports and everything.

I tested it all with DHCP, everything worked fine. then i switched it over to a static IP, and spent the next few hours testing and rebooting it, without a hitch. DId some more work on it this morning, and went to work

WHen i came home we had had a power outage, and my server wasnt connecting but on. i couldn't ping it, ssh in, or access any of the pages hosted on it, so i reset it.

I cant seem to get a connection or ping in or out, or ssh into the server. iv reconfigured it for dchp and it says its not reciving any requests. my static IP wont work either. 

Iv added IPv6 to my blacklist file (/etc/modprobe.d/blacklist)

rebooted my router, my modem, the PC.

I cant seem to get any connection at all no matter what i do.

---

### Post by mrbiggbrain on 2009-09-14
bump

Still having the same issue, Tryed removing samba as that was having issues, still nothing. id greatly appreciate some help

---

### Post by jml on 2009-09-14
Since everything worked prior to the power outage and not after, I suspect a hardware failure of some sort.  Often a power outage is associated with a voltage spike either at the time of the outage, or at the time that the power comes back on.  The spike could cause damage to one of the computer's components.

I would also suggest that you connect a computer that you know has a working network card to your internet connection to make sure that you have a functioning network connection.  Good lick.

Joe

---

