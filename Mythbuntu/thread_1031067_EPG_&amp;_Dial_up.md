---
title: "EPG &amp; Dial up"
date: 2009-01-05
forum: Mythbuntu
---

### Post by laffinet on 2009-01-05
Hi !

I'm thinking about building a HTPC for a colleague. Problem is he's only got a dial up connection and does not really want to change to broadband. 

Question(s):

- does Ubuntu support dial up modems and if so, how well ?
- would Mythbuntu be able to download EPG information via dial-up ? The way I can see this work is schedule a cron job that establishes the dial-up connection, downloads the EPG stuff and then disconnects. Possible ? Would it take ages to download the EPG stuff ?

Thanks for any help.

---

### Post by Caysho on 2009-01-05
It's a "manual" configuration, but there are several references online.

An EPG over dialup would be no worse than email.  You would need to get an idea of the size of the files to be downloaded if you are concerned about it.

---

### Post by volkswagner on 2009-01-05
EPG data can take some time.  I have  three lineups with approx 300 channels total.  It can take several minutes to download on cable.  I never checked the speeds of schedules direct.  It seemed to me it must be slow.  My MCE2005 wakes, downloads and sleeps in approx two minutes (still uses the old Zap-to-it site).  This is what leaves me to believe the Schedules Direct is throttled or just slow.

If you can limit your database of channels and lineups your overall time should decrease.

EDIT: There is also an option to select/deselect "run EPG update next time SD recommends".  If you disable that, the guide will only update when you tell it, via your cron.

---

