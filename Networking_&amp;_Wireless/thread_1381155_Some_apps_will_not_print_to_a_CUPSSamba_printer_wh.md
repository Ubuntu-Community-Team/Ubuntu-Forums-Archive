---
title: "Some apps will not print to a CUPS/Samba printer while others do, 9.04"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by mdlueck on 2010-01-14
Upon migrating my desktop to Ubuntu 9.04 (from Ubuntu 8.04) I noticed that some of my application will not print to my LAN printer which comes via the Samba PDC and is a HP LaserJet 4000.

For example, Thunderbird does print, Firefox does not.

I went checking on this annoying problem and discovered this thread:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/374416](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/374416)

So I went looking through the CUPS logs:
/var/log/cups/access_log
/var/log/cups/error_log

In the access_log, I see numerous successful print jobs.

In the error_log, I see:

E [14/Jan/2010:13:05:27 -0500] [Job 79] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:05:27 -0500] [Job 79] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:05:27 -0500] [Job 79] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:07:57 -0500] Print-Job: Unauthorized
E [14/Jan/2010:13:07:57 -0500] [Job 80] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:07:57 -0500] [Job 80] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:07:57 -0500] [Job 80] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:08:34 -0500] Print-Job: Unauthorized
E [14/Jan/2010:13:08:34 -0500] [Job 81] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:08:34 -0500] [Job 81] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:08:34 -0500] [Job 81] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:08:54 -0500] Print-Job: Unauthorized
E [14/Jan/2010:13:08:54 -0500] [Job 82] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:08:54 -0500] [Job 82] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:08:54 -0500] [Job 82] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:09:21 -0500] Print-Job: Unauthorized
E [14/Jan/2010:13:09:21 -0500] [Job 83] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:09:21 -0500] [Job 83] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:09:22 -0500] [Job 83] Session setup failed: NT_STATUS_LOGON_FAILURE
E [14/Jan/2010:13:15:35 -0500] Print-Job: Unauthorized
E [14/Jan/2010:13:19:50 -0500] Print-Job: Unauthorized


aaaahhhh...... A bit inconsistent considering this workstation has only one printer.

Perhaps is there some mysterious authentication which the application itself must do in order to access the printer?

I had no problems with printing when I was on Ubuntu 8.04.

Suggestions?

---

### Post by Tuomas Jäntti on 2010-09-27
Hi

You have hopefully found some solution since January. Here is a link to a solution that cleared probably the same problem for me:

[http://brainextender.blogspot.com/2009/01/ubuntu-intrepid-too-many-failed.html](http://brainextender.blogspot.com/2009/01/ubuntu-intrepid-too-many-failed.html)

Regards,

Tuomas

---

### Post by mdlueck on 2010-09-27
Thanks for the thought. Sadly that does not work either. Very odd indeed!

I am thinking to upgrade my machine to 10.04 once I can eliminate my one program which depends on 9.04.

---

