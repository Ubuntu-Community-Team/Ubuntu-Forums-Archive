---
title: "How do I run minidlna as a service"
date: 2010-10-28
forum: Multimedia Software
---

### Post by mikehicks on 2010-10-28
Okay, so now I've got minidlna working with my Sony TV (see previous post), can anyone tell me how to set it up as a service?

At the moment I have to go into a terminal window (command prompt) and enter "minidlna" to run it manually.

Does minidlna support running as a service?
How do I do it?

cheers
Mike

UPDATE:
For now I've got it as a startup application.
Obviously this means I have to log in as a desktop session to make minidlna start, rather than just boot up the machine.

---

### Post by rbx on 2010-10-30
I have minidlna running on a headless ubuntu server VM. I basically have it run as a start up program, but I also have a cron job setup for it to run 'minidlna -R' to scan for any new media every 6 hours.

crontab -e

#edit the file to include the following
0 */6 * * * minidlna -R

Hope this helps.

---

