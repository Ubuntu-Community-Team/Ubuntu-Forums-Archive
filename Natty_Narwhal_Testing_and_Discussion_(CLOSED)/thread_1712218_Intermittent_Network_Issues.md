---
title: "Intermittent Network Issues"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by willm.wade on 2011-03-22
I have an AMD64 server that moved to Natty.  It is having trouble intermittently with network connectivity.

I switched from the on-board to a classic 3Com NIC, but no change.
I have turned off ACPI and cleared the iptables rules, but no change.
Changed up a few network items, but no change.  Very unlikely that it is not directly related to the server.

Natty is all up to date, latest of every package.

Example of problem:

Ping any other computer and it will come in with between 5-70% packet loss.  (Extended pinging averages to 5%)

I have never had trouble pinging to the server, even when it is having trouble pinging out.

It will be able to connect one second fine, the next not then fine again.

No errors in the log except a note about CIFS unable to connect.  (However I disabled SMB and still had the issue.)

Any ideas for debugging besides compiling a kernel with debugging?

Any ideas to fix it?

Thanks,
Wil

---

### Post by lucazade on 2011-03-22
> **willm.wade said:**
> I have an AMD64 server that moved to Natty.  It is having trouble intermittently with network connectivity.

I switched from the on-board to a classic 3Com NIC, but no change.
I have turned off ACPI and cleared the iptables rules, but no change.
Changed up a few network items, but no change.  Very unlikely that it is not directly related to the server.

Natty is all up to date, latest of every package.

Example of problem:

Ping any other computer and it will come in with between 5-70% packet loss.  (Extended pinging averages to 5%)

I have never had trouble pinging to the server, even when it is having trouble pinging out.

It will be able to connect one second fine, the next not then fine again.

No errors in the log except a note about CIFS unable to connect.  (However I disabled SMB and still had the issue.)

Any ideas for debugging besides compiling a kernel with debugging?

Any ideas to fix it?

Thanks,
Wil

I would try to see what happens with wireshark, tcpdump and traceroute.
Also have you tried with older kernels?

---

### Post by willm.wade on 2011-03-22
I might give older kernels a try.  I have tried iptraf, but it did not provide any new information.

I might also have located the general source of the problem: Cron.  I am not sure yet, but it appears that disabling cron drastically improves connectivity.  I am searching though  the cron scripts now to see what I can find, and have turned on cron -L 2.

---

### Post by willm.wade on 2011-03-22
Apparently it was the /etc/cron.d/php5 script.  I am not sure why it was causing problems, but it was.  I am not using php sessions so I just moved the script out of there.

Any ideas on why this would cause issues?  Perhaps there is a bug somewhere in there?

---

