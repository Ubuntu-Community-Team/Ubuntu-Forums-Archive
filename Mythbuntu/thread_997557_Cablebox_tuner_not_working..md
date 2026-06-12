---
title: "Cablebox tuner not working."
date: 2008-11-29
forum: Mythbuntu
---

### Post by rschapman on 2008-11-29
I'm running Mythbuntu 8.04.1. I setup my digital cable box today with firewire. It worked fine at first but then started telling me that the signal couldn't be located despite full unencrypted signal. After working through the menus I believe I found the issue. I updated my schedules direct today but when I go to retrieve my listings for digital cable it doesn't save the information. I can select the digital cable line up and then exit but upon returning it has a completely different TX zipcode lineup. I checked twice to make sure my schedules direct lineup had been properly set and it has. What could be causing it not to save the information? Thanks for your help.

---

### Post by majoridiot on 2008-12-07
> **rschapman said:**
> I'm running Mythbuntu 8.04.1. I setup my digital cable box today with firewire. It worked fine at first but then started telling me that the signal couldn't be located despite full unencrypted signal. After working through the menus I believe I found the issue. I updated my schedules direct today but when I go to retrieve my listings for digital cable it doesn't save the information. I can select the digital cable line up and then exit but upon returning it has a completely different TX zipcode lineup. I checked twice to make sure my schedules direct lineup had been properly set and it has. What could be causing it not to save the information? Thanks for your help.

try deleting the channel line-up from backend settings.  then, re-verify the line-up on SD and save it there.
re-configure the new line-up in backend setup and re-fill the database on exit.

you may need to re-optimize and/or clean the database between the delete and new fill, to clean out
remaining residue.

---

