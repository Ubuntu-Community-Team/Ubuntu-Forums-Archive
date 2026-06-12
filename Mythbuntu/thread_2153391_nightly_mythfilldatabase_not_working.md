---
title: "nightly mythfilldatabase not working"
date: 2013-06-10
forum: Mythbuntu
---

### Post by jrockinl on 2013-06-10
Two weeks ago I had installed 12.04.2 and things have been looking good until I noticed I only have two days of listings.  I check the status in MythWeb and it reports it ran at certain time at night but it did not insert any new listings.  The only way I get it to work is if I do it manually.  I imagine it is a file/directory permission problem as when doing it manually, it is as the administrator and that the nightly stuff is run as mythtv user.  What directory or files would have to have the ownership changed for the nightly listing updates to work?

---

### Post by amblinn on 2013-06-16
I had this problem for a while, too (the Information Center says it's "successful" and mythfilldatabase.log doesn't have anything useful to indicate there's a problem, but the number of days of guide data says otherwise).  For me, it turned out I'd run the mythfilldatabase manually (as "amblinn") the first time, which created a file in /tmp that then couldn't be written to by the automated job (running it as "mythtv").  You can see if this is your problem by looking at the permissions for /tmp/mythtv_ddp_data (if the file's there).  I believe a reboot is supposed to clear out /tmp, which should take care of this problem (just as long as you don't run it manually again...)... or, you can just rm the file.  If you don't have that file, then I don't have any suggestions (other than a reboot, which always seems to fix lots of weird things for me...)

---

### Post by one30nav on 2013-06-18
Had the same problem and a reboot corrected it. Thanks, amblinn.

---

### Post by flecki on 2013-06-20
I had a similar problem with only a few channels being updated and some not - manual did work though....

Turned out that the crawler crashed on some obscure channels i did not watch anyway - removing them from the EPG crawl and hiding those channels solved the issue - no error was reported in the logs.

---

### Post by larsolav on 2013-06-20
I've been having the same problem for a while myself. After reading amblinn's post, I deleted /tmp/mythtv_ddp_data (yup, it was created when I manually ran mythfilldatabase) and rebooted. It has been a couple of days and still no automatic update, although it is now a couple of days after the suggested next update time).

---

### Post by one30nav on 2013-06-20
In your case, I'd suggest deleting capture cards, deleting sources, and re-accomplish. That normally corrects everything.

---

### Post by jrockinl on 2013-06-30
The system reboot solved my problem.  Thanks!

---

### Post by klc5555 on 2013-07-01
> **larsolav said:**
> I've been having the same problem for a while myself. After reading amblinn's post, I deleted /tmp/mythtv_ddp_data (yup, it was created when I manually ran mythfilldatabase) and rebooted. It has been a couple of days and still no automatic update, although it is now a couple of days after the suggested next update time).

For a long time I have found my regular mythfilldatabase updates to be less annoying in general by taking them out of mythtv and setting mythfilldatabase as a standalone daily cron job to run in the middle of the night when not much is going on on the master backend. By composing a crontab as my regular user to run the job as my regular user, I didn't have to worry about a lot of glitches, including owner/permissions mismatches for /tmp/mythtv_ddp_data after running mythfilldatabase manually, which I do from time to time.

---

