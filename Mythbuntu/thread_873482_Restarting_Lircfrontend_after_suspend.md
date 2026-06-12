---
title: "Restarting Lirc/frontend after suspend"
date: 2008-07-29
forum: Mythbuntu
---

### Post by rtfm_joey on 2008-07-29
With various posts here I was able to set up a nice Mythbuntu box whilst being a Linux newbie.

I have a 1039 MCE Remote, with a USB2 receiver.

I can suspend just find; I execute a small script with irexec that kills the Mythfrontend.real end then suspends (the frontend needs te be restarted to communicate with lirc again).

What I'm now looking for is to restart irexec/mythfrontend when I resume.

I tried to add the commands to /etc/acpi/resume.sh, but two things can happen; irexec gets started, but not the frontend, or vice versa.

Then I thought te be smart so I only let the front end get started via resume.sh, and irexec via cron after 1 minute.

Irexec get's started when I resume, but nada on the frontend.

When I remove the crontab, suspend and resume, the frontend get's started, but not irexec.

Is there a proper way to do this?

What I need is when comming out of suspend to start the frontend and irexec, both at the seem time if possible.

/edit:
ah crap, the title needed to be Restarting irexec/frontend after suspend, can a mod change this?

---

