---
title: "mythconverg_backup.pl"
date: 2015-10-16
forum: Mythbuntu
---

### Post by jim74 on 2015-10-16
When running the following script to do a database backup - mythconverg_backup.pl

Does it include the information that would be done when doing "mythconverg_backup.pl --backup_xmltvids"?

Or in other words, do I need to do both to do a complete backup?

Thanks.

---

### Post by blm-ubunet on 2015-10-16
The "--backup_xmltvids" option is just a small subset of the database backup.
It generates a small file & completes quickly so is no real burden.
I try to generate the xmltvid backup after any channel lineup changes.
You don't need to use this option to capture all database information.

AFAIU The "--backup_xmltvids" is a convenience thing for users (dvb) who have to populate these fields manually.
The mythtv-setup channel editor does have "interactive/smart" xmltvid editing using the data from the selected video-source .conf file.
In the past restoring the xmltvids, after channel scanning etc, was the most time consuming part of getting the backend setup.

---

### Post by jim74 on 2015-10-16
Thanks. You confirmed my understanding of the [COLOR=#000000]"--backup_xmltvids" option. :)

Can the backend be running during the backup?
[/COLOR]

---

### Post by blm-ubunet on 2015-10-16
Yes, people do seem to run cron jobs (of dB backup) with the backend still running.
But you do want the backend (all BEs & FEs & other clients) & dB server to be quiet.
A backup is worse than useless if it does not restore.

I only manually generate dB backups before installing a new build of mythtv or messing with the channel scanner.
In this case all/any BEs & FEs have to be stopped.

AFAIK The largest table(s) in mythtv's mythconverg schema is the seektable data & this can be regenerated. In fact it is a good idea to regenerate this for old recordings for couple reasons: inaccurate H264 keyframes & slow dB access.

There is an optimizing script available (author dekarl) that has proved to speed up seeking for some users with lots of old recordings.
Old recordings (H264) should have seektables regenerated if you see macroblocking when seeking.

---

